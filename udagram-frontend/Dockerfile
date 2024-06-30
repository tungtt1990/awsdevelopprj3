# Use IONIC base image
FROM beevelop/ionic:v2021.06.1 AS ionic

# Create app directory in Docker
WORKDIR /usr/src/app

# Install app dependencies by copying
# package.json and package-lock.json
COPY package*.json ./

# Install dependencies in Docker
RUN npm install -f

# Copy app from local environment into the Docker image
COPY . .

# Build app
RUN ionic build

FROM nginx:alpine

#COPY www /usr/share/nginx/html
COPY --from=ionic  /usr/src/app/www /usr/share/nginx/html