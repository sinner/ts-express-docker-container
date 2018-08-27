FROM node:carbon
ARG API_DIRECTORY=project-api

# Set working dir
RUN mkdir -p /var/srv/app
WORKDIR /var/srv/app

# Set env var
ENV PATH /var/srv/app/node_modules/.bin:$PATH

# Copy dependencies files
COPY ./${API_DIRECTORY}/package*.json ./

# Create diocesan user, but now, we've got a 'node' user with UID 1000
# RUN adduser --disabled-password --uid 1000 --home "/var/srv/app" --gecos "Guest user to execute common binaries into the project" node

RUN npm install -g typescript ts-node typeorm nodemon

RUN chown -R node:node ./

COPY ./local/docker/api/files/docker-entrypoint.sh /usr/local/bin/docker-entrypoint
RUN chmod +x /usr/local/bin/docker-entrypoint

# ENTRYPOINT ["docker-entrypoint"]

# Installing modules and set correct permissions
# USER node

# RUN npm install

# RUN ls -la

# RUN ts-node ./node_modules/bin/type-orm migrations:run

CMD [ "npm", "start" ]
