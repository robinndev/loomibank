FROM node:20 as builder

WORKDIR /app
COPY . .

RUN npm install -g nx && npm install
RUN npx nx build transactions

FROM node:20

WORKDIR /app

COPY --from=builder /app/dist/apps/transactions ./dist
COPY --from=builder /app/package*.json ./

RUN npm install --only=production

CMD ["node", "dist/main"]
