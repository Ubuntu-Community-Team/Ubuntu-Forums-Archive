---
title: "Using LAMP and MEAN on 1 Machine."
date: 2014-11-08
forum: New to Ubuntu
---

### Post by khan3 on 2014-11-08
Hi,

I have a Ubuntu 14.04 installed on a virtual machine. I have been created Projects using the LAMP stack (with vhosts) so far. However, i want to get into MEAN is it possible on the same machine to use LAMP stack for 1 project and MEAN stack for another project?
If so can you explain how it works as they both use localhost?

I hope the questions make sense.

thanks.

---

### Post by Lars Noodén on 2014-11-08
You could have them listen on different ports.  Or, just a guess, you could use Apache as the front end load balancer for a name- or ip-based vhost that forwards to the other stack, running on a different port or ip, using mod_proxy.

---

### Post by khan3 on 2014-11-08
> **Lars Noodén said:**
> You could have them listen on different ports.  Or, just a guess, you could use Apache as the front end load balancer for a name- or ip-based vhost that forwards to the other stack, running on a different port or ip, using mod_proxy.

**You could have them listen on different ports.**

This is what ive read else where with ngix i think. I don't have much knowledge of this do you know a goods tutorial which will show me how?

---

### Post by nerdtron on 2014-11-08
> **khan3 said:**
> **You could have them listen on different ports.**

This is what ive read else where with ngix i think. I don't have much knowledge of this do you know a goods tutorial which will show me how?

Do you know where the nginx configuration is saved? Most programs in Linux has a "listen" keyword for port on which it will bind and accept connections.

In nginx I think the config file will contain something like:
```

server {
...
...
listen 8080;
...
...
}

```

After saving your modification you need to restart the nginx service.
To verify that nginx bind to another port,
```
 sudo netstat -tulpn
```

---

### Post by khan3 on 2014-11-08
> **nerdtron said:**
> Do you know where the nginx configuration is saved? Most programs in Linux has a "listen" keyword for port on which it will bind and accept connections.

In nginx I think the config file will contain something like:
```

server {
...
...
listen 8080;
...
...
}

```

After saving your modification you need to restart the nginx service.
To verify that nginx bind to another port,
```
 sudo netstat -tulpn
```

I dont actually have nginx, i was just reading on the topic. So don't quite understand what u mean here.

---

### Post by nerdtron on 2014-11-08
What I actually mean is that after you install nginx, it listens to a default port declared on its configuration file. So if you need to make nginx listen to another port instead you simply need to edit its config file and declare a different port number.

---

### Post by Lars Noodén on 2014-11-08
If you are changing the ports,

The directive to set in the nginx configuration file is [listen](http://nginx.org/en/docs/http/ngx_http_core_module.html#listen)

The directive to set in the Apache configuration file is also named [Listen](http://httpd.apache.org/docs/2.4/mod/mpm_common.html#listen), but keep in mind that Apache2 and nginx configurations will be very different otherwise.

---

### Post by khan3 on 2014-11-08
This sounds initially complex but is prob very easy, again do you know of a good tutorial on how to get them both working togeather, before i have a go my self?

[https://www.digitalocean.com/community/tutorials/how-to-configure-nginx-as-a-reverse-proxy-for-apache](https://www.digitalocean.com/community/tutorials/how-to-configure-nginx-as-a-reverse-proxy-for-apache)

is this what im looking for?

---

### Post by m_duck on 2014-11-08
I might have missed the point of the question, but the simple way is just using different ports (as mentioned). If you leave Apache on (presumably) port 80, you can just set Express to listen on another port, e.g. 3000, so you would access your lamp stack via **localhost **and your MEAN stack via **localhost:3000**.

```

var express = require('express')
var app = express()

app.get('/', function (req, res) {
  res.send('Hello World!')
})

var server = app.listen(**3000**, function () {

  var host = server.address().address
  var port = server.address().port

  console.log('Example app listening at http://%s:%s', host, port)

})
```

From: [http://expressjs.com/starter/hello-world.html](http://expressjs.com/starter/hello-world.html)

Express will listen on whatever port you pass to listen(). If you have a more complex app (especially a generated one), you might be setting the port in a Gruntfile or a config.js file for example.

---

### Post by khan3 on 2014-11-09
And if i wanted to create multiple mean projects i would need to install Nginx and use vhosts?

So ive installed nginx and ive kind of messed up all my apache websites. when i navigate for example to

local.mysite.com it shows the nginx defualt page instead of my laravel site for example/

---

### Post by m_duck on 2014-11-09
The easiest way would be to configure each project as above. Wherever the port is set, just change it per project (if they are all running at once). If running only one at a time, they can all use the same port.

Example a:
```
App a: ... app.listen(3000);
App b: ... app.listen(3001);
Access a via localhost:3000 and b via localhost:3001

```
Example b:
```
App a: ... app.listen(3000);
App b: ... app.listen(3001);
Access a and b via localhost:3000 but only one will run at a time

```

I assume this is just for development?

---

### Post by khan3 on 2014-11-09
Update:

localhost:3000 - Points to my MEANApp [Mean Project].

localhost:8080 - Points to my auth [Laravel Project].

I want local.auth.com to point to my auth [Laravel Project] e.g a Virtual Host.
And i want my MeanApp to use a Virtual Host also.

[SIZE=3]**I am confused, can someone simply tell me with what i want to do (See above), do i need to use nginx and apache together or separately e.g apache for php projects and nginx for mean projects. Or What can i use to setup virtual hosts for my mean project.**[/SIZE]

---

### Post by Lars Noodén on 2014-11-10
> **khan3 said:**
> do i need to use nginx and apache together or separately e.g apache for php projects and nginx for mean projects. 

You can use nginx for PHP, too, instead of Apache2 if that's what you are asking.

---

