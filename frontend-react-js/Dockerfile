# FROM node:16.18

# ENV PORT=3000

# COPY . /frontend-react-js
# WORKDIR /frontend-react-js
# RUN npm install
# EXPOSE ${PORT}
# CMD ["npm", "start"]

# Build stage
FROM node:16.18 AS base

WORKDIR /usr/src/app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Final stage
FROM node:16.18-alpine

WORKDIR /usr/src/app
COPY package*.json ./
RUN npm install --production

COPY --from=base /usr/src/app/build ./build

EXPOSE 3000
CMD ["npm", "start"]