##########################
## Builder Container
##########################
FROM node:18.10.0-alpine3.15 as builder

WORKDIR /app

COPY package.json package-lock.json ./

RUN npm i --no-progress

COPY . .

RUN npm run build

##########################
## Application Container
##########################
FROM node:18.10.0-alpine3.15

WORKDIR /app

COPY --from=builder /app ./

CMD ["npm", "run", "start"]
