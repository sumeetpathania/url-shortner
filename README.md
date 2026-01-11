# URL Shortener

A backend service that generates short URLs and redirects users to long URLs.

## Features
- Generate short URLs using Base62 encoding
- Redirect short URLs to original URLs
- PostgreSQL-backed persistence
- Expiration support

## Architecture
- Controller → Service → Repository
- Stateless redirect service
- SQL as source of truth

## Hot Path
GET /{shortCode}
- Indexed lookup by short_code
- Minimal logic for low latency

## Cold Path
POST /shorten
- Validation
- ID generation
- Persistence
