---
title: "Setting up server info?"
date: 2012-05-24
forum: New to Ubuntu
---

### Post by Greg Mueller on 2012-05-24
I have toyed with the idea of setting up a server at my home to host my domains. I pay for a host now on a monthly/yearly basis. I have checked and can get a static IP at my home here and at my new home when I get there.

Is there a place that has info "for the complete idiot" on setting up an Ubuntu home server?

Are the Ubuntu downloads for servers the same downloads that I use now or are they different?
Where do I get them?

I'm starting at zero so please be gentle

Thanks

---

### Post by wojox on 2012-05-24
It depends. Greg. The [Ubuntu Server]("http://www.ubuntu.com/download/server") does not come with a GUI or X for that matter. All command line. :p

You can install the Desktop version and set it up the same way.

A good guide is [Ubuntu Server Guide]("https://help.ubuntu.com/12.04/serverguide/")

---

### Post by mlentink on 2012-05-24
[http://www.ubuntu.com/download/server](http://www.ubuntu.com/download/server)
and check this out:
[https://help.ubuntu.com/12.04/serverguide/index.html](https://help.ubuntu.com/12.04/serverguide/index.html)

You might find the 'Perfect Server' Howto's over at Howtoforge useful too

---

### Post by vandorjw on 2012-05-24
Just tell us where you need help.

My suggestion is this.

1) Do not cancel your existing services yet if you depend on them. Administrating a server is more complicated than just point and click.

2) Download Ubuntu Server 12.04, or debian 6, both will be supported for a long time.

3) Use a separate computer, something that you dont need for anything else, and install the OS on it. It does not make sense to dual boot to me.

4) Reply to this thread what you would like to set up first, and we'll try to help you out with best practises as much as we can.
( Webserver [I am most familiar with apache], nameserver [bind9], etc)

---

### Post by Greg Mueller on 2012-05-24
> **cc7gir said:**
> Just tell us where you need help.

My suggestion is this.

1) Do not cancel your existing services yet if you depend on them. Administrating a server is more complicated than just point and click.

2) Download Ubuntu Server 12.04, or debian 6, both will be supported for a long time.

3) Use a separate computer, something that you dont need for anything else, and install the OS on it. It does not make sense to dual boot to me.

4) Reply to this thread what you would like to set up first, and we'll try to help you out with best practises as much as we can.
( Webserver [I am most familiar with apache], nameserver [bind9], etc)





Yep this is exactly what I want to do, since I don't know what I'm doing it may take a long time. 
First I have to get/build another computer. Trying to figure how powerful/fancy that needs to be.

I do like to tinker with stuff. If I never get done oh well. These responses are a great start



:popcorn:

---

### Post by Paqman on 2012-05-24
I'd also consider getting your toes wet by switching to a VPS instead of doing it all yourself. That way you get a fully configured machine that's ready to go and you can get used to running it on a day-to-day basis without having to spend ages tearing your hair out about initial config.

---

