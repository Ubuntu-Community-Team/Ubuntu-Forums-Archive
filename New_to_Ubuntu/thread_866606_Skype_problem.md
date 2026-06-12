---
title: "Skype problem"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by CommanderOne on 2008-07-21
Hey,

I installed Ubuntu a few weeks ago, and have been throughly enjoying it, but I have been having some problems with the Linux version of Skype.

I can download and install it, but as soon as I go go run it I can log in, but thats about as far as I get. As soon as that happens it will log me in for a few seconds, but seems to lose the connection and goes from a green active icon, to a loggin in rotating gray one.

I as wondering if anyone had any ideas how to fix it.

Thanks in advance.

---

### Post by jamesrfla on 2008-07-21
Skype login servers seems to be working so that isn't the problem. Try rebooting.

---

### Post by komputes on 2008-07-22
Log into skype.com with the same username and password, if that fails do the password recovery by filling out your details and clicking "Get Password"

[https://secure.skype.com/store/member/login?message=login_required](https://secure.skype.com/store/member/login?message=login_required)

---

### Post by CommanderOne on 2008-07-22
Hey,

Thanks for the help.

I can actually login to skype, and skype.com, the problem I am having is when I have logged into the skype client on my computer, I get signed into skype, can see people online etc, but then it seems to log me out, or I lose the connection, and it goes back to siging me in.

---

### Post by hyper_ch on 2008-07-22
use skype from the medibuntu repos. That works for sure.

---

### Post by komputes on 2008-07-22
Is this using a cabled or wireless connection? When skype is grey, are you able to access the web via firefox?

---

### Post by CommanderOne on 2008-07-23
> **komputes said:**
> Is this using a cabled or wireless connection? When skype is grey, are you able to access the web via firefox?

Hey,

This is using a wireless connection, and when skype starts I can connect to the net fine, but as soon as it gors into that 'loading' stage firefox packs a spat as well and wont let me through either. But this happens every time I try to use Skype, and has to be because of it.

I tried sudo apt-get install skype, and that has the same problem :/

Thanks,

---

### Post by komputes on 2008-07-23
If this does not happed on a wired connection, I would blame the wireless connection or wireless driver (or the router but I doubt it). It has nothing to do with skype or firefox and everything to do with the network. I had the same issue using a broadcom and a d-link wireless controller using a windows driver under NDISwrapper.

---

