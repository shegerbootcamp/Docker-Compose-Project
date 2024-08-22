# Set the base image to an LTS version of Node.js
FROM node:16

# File Author / Maintainer
LABEL maintainer="cloudsheger"

# Install Node.js, build tools, and other dependencies
RUN apt-get update && \
    apt-get install -y python3 build-essential && \
    rm -rf /var/lib/apt/lists/*

# Clean npm cache
RUN npm cache clean --force

# Set the working directory
WORKDIR /src

# Copy package.json and install dependencies
COPY package.json /src/
RUN npm install --ignore-scripts

# Copy the rest of the application code
COPY . /src

# Expose the application port
EXPOSE 8080

# Run the application using nodemon
CMD ["nodemon", "/src/index.js"]