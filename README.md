version: '3.8'

services:
  db:
    image: mongo:6.0
    ports:
      - '27017:27017'
    volumes:
      - mongodb_data:/data/db
    healthcheck:
      test: ["CMD", "mongosh", "--eval", "db.adminCommand('ping')"]
      interval: 10s
      timeout: 5s
      retries: 5
      start_period: 10s

  mailhog:
    image: mailhog/mailhog:v1.0.1
    ports:
      - '1025:1025'
      - '8025:8025'

volumes:
  mongodb_data: