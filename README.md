# Gold Price API

REST API to get real-time gold futures price in USD from the Chicago Mercantile Exchange (CME). One endpoint. Clean JSON. 100 free requests/month.

## Features

- Real-time gold futures price from the CME
- One endpoint, no parameters — just call `/price`
- Clean JSON response with price and timestamp
- 99.99% uptime SLA
- 100 requests/month on free tier
- Example Response:
```json
{
  "price_usd": 5030.7,
  "updated_at": "2026-02-09T10:12:49+00:00"
}
```

## Get API Key

Create an account at [omkar.cloud](https://www.omkar.cloud/auth/sign-up?redirect=/api-key) to get your API key, and use it in requests. 100 requests are free every month.

## Quick Start

```bash
curl -X GET "https://gold-price-api.omkar.cloud/price" \
  -H "API-Key: YOUR_API_KEY"
```

```json
{
  "price_usd": 5030.7,
  "updated_at": "2026-02-09T10:12:49+00:00"
}
```

## Installation

### Python

```bash
pip install requests
```

```python
import requests

response = requests.get(
    "https://gold-price-api.omkar.cloud/price",
    headers={"API-Key": "YOUR_API_KEY"}
)

data = response.json()
print(f"Gold Price: ${data['price_usd']} USD")
```

### Node.js

```bash
npm install axios
```

```javascript
import axios from "axios";

const response = await axios.get("https://gold-price-api.omkar.cloud/price", {
    headers: { "API-Key": "YOUR_API_KEY" }
});

console.log(`Gold Price: $${response.data.price_usd} USD`);
```

## API Reference

### Endpoint

```
GET https://gold-price-api.omkar.cloud/price
```

### Headers

| Header | Required | Description |
|--------|----------|-------------|
| `API-Key` | Yes | API key from [omkar.cloud/api-key](https://www.omkar.cloud/api-key) |

### Parameters

None. Just call the endpoint with your API key.

### Response Fields

| Field | Type | Description |
|-------|------|-------------|
| `price_usd` | number | Current gold futures price in USD (e.g., 5030.7) |
| `updated_at` | string | Last updated timestamp in ISO 8601 format |

## Examples

### Get gold price in Python

```python
import requests

response = requests.get(
    "https://gold-price-api.omkar.cloud/price",
    headers={"API-Key": "YOUR_API_KEY"}
)

data = response.json()
print(f"Gold: ${data['price_usd']} (updated {data['updated_at']})")
```

### Build a price alert

```python
import requests

ALERT_THRESHOLD = 5000

response = requests.get(
    "https://gold-price-api.omkar.cloud/price",
    headers={"API-Key": "YOUR_API_KEY"}
)

price = response.json()["price_usd"]
if price > ALERT_THRESHOLD:
    print(f"Gold crossed ${ALERT_THRESHOLD}! Current: ${price}")
```

### Track gold price over time

```python
import requests
import time

prices = []
for _ in range(10):
    response = requests.get(
        "https://gold-price-api.omkar.cloud/price",
        headers={"API-Key": "YOUR_API_KEY"}
    )
    data = response.json()
    prices.append(data["price_usd"])
    print(f"${data['price_usd']} at {data['updated_at']}")
    time.sleep(60)
```

## Error Handling

```python
response = requests.get(
    "https://gold-price-api.omkar.cloud/price",
    headers={"API-Key": "YOUR_API_KEY"}
)

if response.status_code == 200:
    data = response.json()
elif response.status_code == 401:
    # Invalid API key
    pass
elif response.status_code == 429:
    # Rate limit exceeded
    pass
```

## Rate Limits

| Plan | Price | Requests/Month |
|------|-------|----------------|
| Free | $0 | 100 |
| Starter | $16 | 3,000 |
| Grow | $48 | 15,000 |
| Scale | $148 | 75,000 |

Most gold price APIs charge $99/month for unlimited access. We don't. Start free, scale cheap.

## Questions? We have answers.

Reach out anytime. We will solve your query within 1 working day.

[![Contact Us on WhatsApp about Gold Price API](https://raw.githubusercontent.com/omkarcloud/assets/master/images/whatsapp-us.png)](https://api.whatsapp.com/send?phone=918178804274&text=I%20have%20a%20question%20about%20the%20Gold%20Price%20API.)

[![Contact Us on Email about Gold Price API](https://raw.githubusercontent.com/omkarcloud/assets/master/images/ask-on-email.png)](mailto:happy.to.help@omkar.cloud?subject=Gold%20Price%20API%20Question)
