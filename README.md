# AI Stocks Analyzer

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)

An intelligent stock market analysis tool powered by AI that leverages machine learning and natural language processing to provide insights and predictions for stock trading decisions.

## Table of Contents

- [Features](#features)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Configuration](#configuration)
- [API Reference](#api-reference)
- [Examples](#examples)
- [Contributing](#contributing)
- [License](#license)
- [Support](#support)

## Features

- 📊 **Real-time Stock Data Analysis** - Fetch and analyze current market data
- 🤖 **AI-Powered Predictions** - Machine learning models for stock price forecasting
- 📈 **Technical Analysis** - Comprehensive technical indicators and patterns
- 💬 **Natural Language Processing** - Analyze financial news and sentiment
- 📉 **Portfolio Management** - Track and optimize your investment portfolio
- 🔔 **Alerts & Notifications** - Real-time alerts for price movements and opportunities
- 📊 **Visualization** - Interactive charts and dashboards
- 💾 **Historical Data** - Access to historical stock prices and trends

## Requirements

- Python 3.8 or higher
- pip (Python package manager)
- 4GB RAM (minimum)
- Internet connection for live data fetching

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/shukrirashid/ai-stocks-analyzer.git
cd ai-stocks-analyzer
```

### 2. Create Virtual Environment

```bash
# On macOS/Linux
python3 -m venv venv
source venv/bin/activate

# On Windows
python -m venv venv
venv\Scripts\activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure API Keys

Create a `.env` file in the project root:

```bash
cp .env.example .env
```

Edit `.env` and add your API keys:

```
ALPHA_VANTAGE_API_KEY=your_api_key_here
NEWS_API_KEY=your_api_key_here
POLYGON_API_KEY=your_api_key_here
```

Get your API keys:
- [Alpha Vantage](https://www.alphavantage.co/api/) - Stock data
- [News API](https://newsapi.org/) - Financial news
- [Polygon.io](https://polygon.io/) - Market data

## Usage

### Quick Start

```python
from ai_stocks_analyzer import StockAnalyzer

# Initialize analyzer
analyzer = StockAnalyzer()

# Analyze a stock
analysis = analyzer.analyze('AAPL')
print(analysis)

# Get predictions
predictions = analyzer.predict('AAPL', days=30)
print(predictions)
```

### Command Line Interface

```bash
# Analyze a single stock
python -m ai_stocks_analyzer analyze AAPL

# Get 30-day forecast
python -m ai_stocks_analyzer predict AAPL --days 30

# Compare multiple stocks
python -m ai_stocks_analyzer compare AAPL GOOGL MSFT

# Generate portfolio report
python -m ai_stocks_analyzer portfolio --symbols AAPL GOOGL MSFT
```

### Web Dashboard

```bash
# Start the web server
python app.py

# Access the dashboard at http://localhost:5000
```

## Project Structure

```
ai-stocks-analyzer/
├── README.md                      # This file
├── LICENSE                        # MIT License
├── requirements.txt               # Python dependencies
├── .env.example                   # Environment variables template
├── setup.py                       # Package setup configuration
│
├── src/                           # Source code
│   ├── __init__.py
│   ├── main.py                    # Entry point
│   ├── config.py                  # Configuration management
│   ├── stock_analyzer.py          # Main analyzer class
│   │
│   ├── data/                      # Data handling modules
│   │   ├── __init__.py
│   │   ├── data_fetcher.py        # Fetch stock data from APIs
│   │   ├── data_processor.py      # Process and clean data
│   │   └── cache.py               # Caching mechanism
│   │
│   ├── ml/                        # Machine learning models
│   │   ├── __init__.py
│   │   ├── models.py              # ML model definitions
│   │   ├── predictor.py           # Price prediction
│   │   └── sentiment_analyzer.py  # NLP sentiment analysis
│   │
│   ├── technical/                 # Technical analysis
│   │   ├── __init__.py
│   │   ├── indicators.py          # Technical indicators
│   │   ├── patterns.py            # Chart patterns detection
│   │   └── signals.py             # Trading signals
│   │
│   ├── utils/                     # Utility functions
│   │   ├── __init__.py
│   │   ├── logger.py              # Logging configuration
│   │   ├── helpers.py             # Helper functions
│   │   └── constants.py           # Constants and enums
│   │
│   └── api/                       # REST API
│       ├── __init__.py
│       ├── routes.py              # API endpoints
│       └── models.py              # API models
│
├── tests/                         # Unit and integration tests
│   ├── __init__.py
│   ├── test_analyzer.py
│   ├── test_data_fetcher.py
│   ├── test_ml_models.py
│   └── test_technical_analysis.py
│
├── notebooks/                     # Jupyter notebooks
│   └── analysis_examples.ipynb
│
└── docs/                          # Documentation
    ├── API.md                     # API documentation
    ├── CONTRIBUTING.md            # Contributing guidelines
    └── MODELS.md                  # ML models documentation
```

## Configuration

### Environment Variables

Create a `.env` file with the following variables:

```
# API Keys
ALPHA_VANTAGE_API_KEY=your_key
NEWS_API_KEY=your_key
POLYGON_API_KEY=your_key

# Database
DATABASE_URL=sqlite:///stocks.db

# Logging
LOG_LEVEL=INFO
LOG_FILE=logs/app.log

# Cache
CACHE_ENABLED=true
CACHE_TTL=3600

# Application
DEBUG=false
PORT=5000
HOST=0.0.0.0
```

### Configuration File

Edit `src/config.py` to customize:

```python
class Config:
    # Model settings
    PREDICTION_DAYS = 30
    LOOKBACK_WINDOW = 60
    
    # Technical analysis
    MA_PERIODS = [20, 50, 200]
    RSI_PERIOD = 14
    
    # Update frequency
    DATA_UPDATE_INTERVAL = 300  # seconds
```

## API Reference

### StockAnalyzer Class

#### `analyze(symbol: str) -> Dict`
Performs comprehensive analysis on a stock.

```python
analysis = analyzer.analyze('AAPL')
# Returns: {
#   'symbol': 'AAPL',
#   'current_price': 150.25,
#   'sentiment': 'positive',
#   'technical_signals': {...},
#   'moving_averages': {...}
# }
```

#### `predict(symbol: str, days: int = 30) -> Dict`
Generates price predictions for specified days.

```python
forecast = analyzer.predict('AAPL', days=30)
# Returns predicted prices with confidence intervals
```

#### `get_signals(symbol: str) -> List[str]`
Generates buy/sell trading signals.

```python
signals = analyzer.get_signals('AAPL')
# Returns: ['BUY', 'HOLD', 'SELL']
```

#### `compare(symbols: List[str]) -> DataFrame`
Compares multiple stocks side by side.

```python
comparison = analyzer.compare(['AAPL', 'GOOGL', 'MSFT'])
# Returns DataFrame with comparison metrics
```

### REST API Endpoints

```
GET  /api/stocks/{symbol}           - Get stock analysis
GET  /api/stocks/{symbol}/predict   - Get price predictions
GET  /api/stocks/{symbol}/signals   - Get trading signals
GET  /api/portfolio                 - Get portfolio analysis
POST /api/portfolio                 - Create new portfolio
```

## Examples

### Example 1: Basic Stock Analysis

```python
from ai_stocks_analyzer import StockAnalyzer

analyzer = StockAnalyzer()

# Analyze Apple stock
result = analyzer.analyze('AAPL')

print(f"Current Price: ${result['current_price']}")
print(f"Sentiment: {result['sentiment']}")
print(f"Recommendation: {result['recommendation']}")
```

### Example 2: Price Prediction

```python
# Get 30-day forecast
forecast = analyzer.predict('AAPL', days=30)

import pandas as pd
df = pd.DataFrame(forecast)
df.to_csv('aapl_forecast.csv', index=False)

# Visualize
import matplotlib.pyplot as plt
plt.plot(df['date'], df['predicted_price'])
plt.title('AAPL 30-Day Price Forecast')
plt.show()
```

### Example 3: Portfolio Analysis

```python
# Analyze portfolio
portfolio = analyzer.create_portfolio([
    {'symbol': 'AAPL', 'shares': 10},
    {'symbol': 'GOOGL', 'shares': 5},
    {'symbol': 'MSFT', 'shares': 8}
])

print(f"Total Value: ${portfolio['total_value']}")
print(f"Expected Return: {portfolio['expected_return']}%")
print(f"Risk Level: {portfolio['risk_level']}")
```

## Testing

Run the test suite:

```bash
# Run all tests
pytest

# Run with coverage
pytest --cov=src tests/

# Run specific test file
pytest tests/test_analyzer.py -v
```

## Contributing

We welcome contributions! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

Please see [CONTRIBUTING.md](docs/CONTRIBUTING.md) for more details.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support

- 📖 [Documentation](docs/)
- 🐛 [Issue Tracker](https://github.com/shukrirashid/ai-stocks-analyzer/issues)
- 💬 [Discussions](https://github.com/shukrirashid/ai-stocks-analyzer/discussions)
- 📧 Email: shukrirashidtrader@gmail.com

## Disclaimer

This tool is for educational and informational purposes only. It should not be considered as financial advice. Always conduct your own research and consult with a financial advisor before making investment decisions.

## Acknowledgments

- Alpha Vantage for stock data API
- News API for financial news data
- Polygon.io for market data
- Open source community for libraries and tools

---

**Last Updated:** December 30, 2025

For the latest updates, visit [GitHub Repository](https://github.com/shukrirashid/ai-stocks-analyzer)
