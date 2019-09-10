# Set the base image to Ubuntu
FROM    ubuntu

# Install Node.js and other dependencies
RUN apt-get update && \
    apt-get -y install curl && \
   curl -sL https://deb.nodesource.com/setup_10.x |  bash - && \
    apt-get install -y python build-essential nodejs

   #curl -sL https://deb.nodesource.com/setup_6.x | bash - && \
   #apt-get install -y python build-essential nodejs && \ 
    #curl -sL https://deb.nodesource.com/setup_dev | sudo bash - && \
    #apt-get -y install python build-essential nodejs 
    #apt-get -y install npm

# Install nodemon
#RUN npm config set registry http://registry.npmjs.org/
RUN npm install -g nodemon

# Provides cached layer for node_modules
ADD package.json /tmp/package.json
RUN cd /tmp && npm install pug && npm install express && npm install redis 
RUN mkdir -p /src && cp -a /tmp/node_modules /src/

# Define working directory
WORKDIR /src
ADD . /src

# Expose port
EXPOSE  8080

# Run app using nodemon
CMD ["nodemon", "/src/index.js"]
