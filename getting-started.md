# Getting started

Install Reazy cli
```sh
$ npm install -g reazy-cli
```

Generate the app
```sh
$ reazy generate my-awesome-app
```
This will generate a very basic app with a couple of services(react-native and reazy-native-config)

Run the app
```sh
$ reazy run-ios
$ reazy run-android
```

### Installing a basic service

Let's add a new service `reazy-auth` which is available as a reazy plugin.
```sh 
$ npm install --save reazy-auth
```

Open `src/app.js`.
```js
import reazy from 'reazy';
import config from 'reazy-native-config';
import auth from 'reazy-auth';
import reactNative from './services/react-native';

const app = reazy();

app.use(config(), 'config');
app.use(auth(), 'auth');
app.use(reactNative(), 'reactNative');

export default app;
```

`app.use(service(), 'serviceName')` creates a service instance and adds it to your app instance with name `serviceName`.

The service instance can then be accessed like this:
```js
const auth = app.get('auth');
auth.setUser({name: 'User', email: 'user@reazyframework.io'});
const user = auth.getUser();
```

You can also generate your own service and use it in the same way as above.
```sh
$ reazy generate service
```

Now that we are done with the basic usage, let's dive into the details.
