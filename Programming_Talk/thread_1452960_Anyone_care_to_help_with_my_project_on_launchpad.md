---
title: "Anyone care to help with my project on launchpad ?"
date: 2010-04-12
forum: Programming Talk
---

### Post by heikaman on 2010-04-12
Hi, I started a bluetooth file server project on launchpad called [bluekiosk]("https://code.launchpad.net/bluekiosk") it's written in c, bluez and it works :)

I finished the basic stuff, but I think it needs more work, I need some help in testing, I don't have a bluetooth device now, releasing, no public releases yet, and any new features are welcomed.

Please let me know if you are interested.

---

### Post by f1r3flie on 2010-04-13
I'm interested in getting involved in some sort of project. I can program in C++ and to an extent gtkmm. Can you give any more information on what you're trying to do and if it sounds like I can help?

---

### Post by heikaman on 2010-04-13
Hi

Thanks for your reply, the project is a bluetooth file server that continuously scans the area for bluetooth devices and then attempts to push files to those devices using obex, those files can be anything picture, text etc, it's written in c and uses bluez and obex.

I made it to be used for location-based advertisment, information broadcasts or for keeping tabs on people :D

As far as I know there are **commercial** apps like this for Window$, but nothing free for linux.

I need help with:

* creating a release, no public release yet and this is the highest priority.

* I need to know if I can use multiple bluetooth devices simultaneously, one for scanning, the other for sending.

* the server should eventually run as a daemon

* I would like to save information about the devices the server finds in a database, bdaddr, name, model, no of times seen etc..

* currently there are some cmd args but I think a config file in /etc would be nice

* maybe a GUI front-end in gtk

* changing the name

* changing the licence to LGPL maybe?

* I need someone to test

* I have some new ideas that can be implemented in the future


I don't know what you can do, but if you think you can help with anything you're welcome to join.

---

### Post by f1r3flie on 2010-04-13
I think I can help with this.

I can make it a distributable application with Makefiles etc. that anyone can run and use. I could make a GUI frontend for it. I also believe but am not certain that I could make the database.

How much of this have you already made? I'm not sure if it can be made as part-C++, part C, although i don't think it's too hard to translate between the two programming languages, as they are quite similar.

I don't have a bluetooth device, although I may have one soon and I know others who do. Are you expecting it to have an application installed on the client device (also are you thinking computers or mobile devices?).

Is it a program targeted at advertising to strangers or to deliver information to colleagues etc?

Finally, is there a link to a project site for this and is anyone else also working on it?

---

### Post by heikaman on 2010-04-14
> **f1r3flie said:**
> I think I can help with this.

I can make it a distributable application with Makefiles etc. 

I used autotools already for that, I was talking about a public release, that is something you can download and install, not every one would like to checkout the src and compile, I'm thinking a deb package would be nice.

> **f1r3flie said:**
> 
I could make a GUI frontend for it. I also believe but am not certain that I could make the database.


That would be nice. Although the GUI is not for the server, because the server will run as a daemon, it could be, however, for configuring/monitoring the server.

> **f1r3flie said:**
> 
How much of this have you already made? I'm not sure if it can be made as part-C++, part C, although i don't think it's too hard to translate between the two programming languages, as they are quite similar.


I made some nice progress, like I said I covered all the basic stuff.

If you know c++ then you know c and you can call c code from c++ code.

> **f1r3flie said:**
> 
Are you expecting it to have an application installed on the client device (also are you thinking computers or mobile devices?).


It works with any "device" that supports obex, basically all devices, and does not need any clients on the device.

> **f1r3flie said:**
> 
Is it a program targeted at advertising to strangers or to deliver information to colleagues etc?


It can be used for distributing files, keeping track of devices how many times a device was seen ? when was the last time a device was seen ? and where? etc...

> **f1r3flie said:**
> 
Finally, is there a link to a project site for this and is anyone else also working on it?

I'm working alone, this the link:

[https://code.launchpad.net/bluekiosk]("https://code.launchpad.net/bluekiosk")

And you can checkout the src and test:

[PHP]bzr branch lp:bluekiosk[/PHP]

---

