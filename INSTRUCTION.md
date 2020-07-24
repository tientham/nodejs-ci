For using this project, you need to create new folder.

mkdir config
touch config/dev.js
vi config/dev.js
module.exports = {
googleClientID: '70265989829-0t7m7ce5crs6scqd3t0t6g7pv83ncaii.apps.googleusercontent.com',
googleClientSecret: '8mkniDQOqacXtlRD3gA4n2az',
mongoURI:
'<your_mongo_url>',
cookieKey: '123123123',
};

## Start Redis

tientham$ brew services start redis
tientham$ redis-cli ping

### Redis get/set

TienTham-2:project tientham\$ node
Welcome to Node.js v12.14.1.
Type ".help" for more information.

> const redis = require('redis')
> undefined
> const redisUrl = 'redis://127.0.0.1:6379'
> undefined
> const client = redis.createClient(redisUrl)
> undefined
> client

### Redis hashes

> client.hset('german', 'ret', 'rot')
> true
> client.hget('german', 'ret', console.log)
> true
> null rot

### Redis storing plain Json object

> client.set('colors', JSON.stringify({red: 'rojo'}))
> true
> client.get('colors', console.log)
> true
> null {"red":"rojo"}

> client.get('colors', (err, val) => console.log(JSON.parse(val)))
> true
> { red: 'rojo' }

### Redis expiration

> client.set('color', 'red', 'EX', 5)
> true
> client.get('color', console.log)
> true
> null red
> client.get('color', console.log)
> true
> null null
