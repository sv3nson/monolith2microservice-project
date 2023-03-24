## Build
FROM node:18.14.0-alpine AS ionic
#FROM beevelop/ionic:latest AS ionic
# Create app directory
WORKDIR /usr/src/app
# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
COPY package*.json ./
RUN npm install -g ionic
RUN npm install --force
# Bundle app source
COPY . .
RUN ionic build
## Run 
FROM nginx:alpine
RUN rm -rf /usr/share/nginx/html/*

COPY --from=ionic  /usr/src/app/www /usr/share/nginx/html