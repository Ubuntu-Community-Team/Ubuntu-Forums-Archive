---
title: "Brunch - config.server.port: expected: number, got: string (3000)"
date: 2016-07-01
forum: Programming Talk
---

### Post by Crafty Kisses on 2016-07-01
I'm trying to run a test-run with Brunch using Nitrous as the container for dependencies, I'm using the node package manager to install it via

```
npm install -g brunch
```

My **brunch-config.js** looks good, here's the content of my brunch-config file, I opted for JavaScript instead of CoffeeScript

```
 module.exports = {
  files: {
    javascripts: {joinTo: 'app.js'},
    stylesheets: {joinTo: 'app.css'},
  },

  server: {
   hostname: '0.0.0.0',
   port: '3000'
  }
};

```

So I want to run the application on port 3000 obviously, but when I run

```
brunch build 
```

I get the following error output

```
01 Jul 05:56:40 - error: config.server.port: expected: number, got: string (3000)
01 Jul 05:56:40 - error: Initialization error -  config is not valid
Stack trace was suppressed. Run with `LOGGY_STACKS=true` to see the trace.
```

This is also true when I run

```
brunch build --production

```

I have browsed around GitHub, the official documentation for Brunch - but yet to find a solution, this isn't a container issue either (I thought it might be) but tried to run it on a local machine - same thing. Any support would be highly appreciated.

---

### Post by spjackson on 2016-07-01
I would try removing the quotes from around '3000'.

---

### Post by Crafty Kisses on 2016-07-01
Yeah, I did that same error, ended up fixing it switching to an older version of brunch - thanks for the input!

---

