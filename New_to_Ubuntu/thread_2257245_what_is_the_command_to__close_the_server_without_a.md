---
title: "what is the command to  close the server without a gui? exit doesn't switch off devi"
date: 2014-12-18
forum: New to Ubuntu
---

### Post by gregory10 on 2014-12-18
I am now running an apache server on ubuntu server but have no idea how to close the server down with a gui

can somebody please tell me the command for doing this please don't know where to start to look for info on that either

---

### Post by monkeybrain20122 on 2014-12-18
```
sudo service apache2 stop
```

---

### Post by lisati on 2014-12-18
This should turn the system off:
```
sudo shutdown now
```

---

### Post by gregory10 on 2014-12-19
I'm using an old netbook to get hands on experience running a webserver mainly looking towards development work but also to get an idea of what it takes for production work as well.

thanks to monkeybrain20122
and also lisati

tried 'sudo shutdown now' first and the command terminal popped out all the lists as it was shuting down then at the end had 
root@ubunto:``# 
so hit the power button and it powered down after spitting out a few messages in the terminal 

then tried 'sudo service apache2 stop' and nothing just says apache2: unrecognised service with the prompt showing my account 
apache2: unrecognised service
gregory@ubuntu:`$

I'm wondering about the 'sudo service apache2' command result??? is it maybe because apache server isn't started by default when I turn the machine on?

---

### Post by Lars Noodén on 2014-12-19
> **gregory10 said:**
> 
I'm wondering about the 'sudo service apache2' command result??? is it maybe because apache server isn't started by default when I turn the machine on?

What version of Ubuntu are you running and how did you install Apache2?  If Apache2 is from the Software Center, aka the official repositories, then the [service](http://manpages.ubuntu.com/manpages/trusty/en/man8/service.8.html) utility mentioned above will work.  If it is not from the official repositories, then some detective work is needed.  

Also, for [shutdown](http://manpages.ubuntu.com/manpages/trusty/en/man8/shutdown.8.html) to work in shutting down the whole machine, you have to tell it what to do when the time arrives.  Usually that mean -h or -HP, depending on the hardware.

---

### Post by grahammechanical on 2014-12-19
I do not run a server but I do have an install of Ubuntu which I am testing and I have to use a console or tty to update or to shutdown.

To restart I use

```
sudo shutdown -r now
```

to shut down I use

```
sudo shutdown -h now
```

Those are two useful commands for whenever the desktop user interface crashes and we cannot access the power/cog menu but we can access a console, which is what a server install uses.

Regards

---

### Post by gregory10 on 2014-12-20
thanks grahammechanical
They work fine just tested them great

On thing I need to know is: how to open or shutdowm apache2 and also how to test if it is going in some simple way.
I got it in mind to be able to configure and reconfigure do some experimentation with my app on apache.
Are there any simple commands go do that? got some I use on my laptop but with that apache2 is running on kubuntu not as a webserver as such.
I tried them and it doesn't seem to be the same result with this instalation on ubuntu server.

is there any commands to start just the apache web service and also stop it while keeping unbuntu server itself running?

---

### Post by nerdtron on 2014-12-21
sudo service apache2 start
sudo service apache2 stop

The above commands don't work? It seems apache is not installed in the standard way.
What is the output of:
```
 ps -ef | grep apache
whereis apache2
```

---

