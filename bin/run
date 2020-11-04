#!/usr/bin/env node
const config = require('../config')[process.env.NODE_ENV || 'development'];

const appzip = require('appmetrics-zipkin')(config.zipkin);
require('appmetrics-prometheus').attach();
const http = require('http');


const log = config.log();
const app = require('../app')(config);

const server = http.createServer(app);

server.listen(process.env.PORT || 3000);

server.on('listening', () => {
  log.info(
    `Hi there! I'm listening on port ${server.address().port} in ${app.get('env')} mode.`,
  );
});
