---
title: "Bluez programming: where to find examples?"
date: 2007-08-07
forum: Programming Talk
---

### Post by MrJavalava on 2007-08-07
Hi there.

I'm programming with PyBluez, where i'm having a bit of a struggle finding examples for Bluetooth programming. Though I've found [http://people.csail.mit.edu/albert/bluez-intro/](http://people.csail.mit.edu/albert/bluez-intro/) as a starter, the examples are very basic.
What I want to do, is to develop a server application which can send messages through bluetooth to other bluetooth devices (mobiles, pda, etc).

However, since I have no clue howto send messages with the bluetooth interface, I'm sorta stuck. I've used the allmighty Google, but it just points back to the mentioned url. There seems like there are no good tutorials nor documentations for how you can send sms, pictures or any other kind of data from a pc to a bluetooth device.

What I've found out so far by using the documentation that is linked, is that I can detect other bluetooth devices and get to know what services the devices provides. Other than that, I'm making any progress.
 
I've also skimmed through a book called "Bluetooth 1.1 Connect without Cables", but it's more technical rather than applied software development. I think [www.bluetooth.org](www.bluetooth.org) (or was it SIG..) might have something, but I can't access whatever documents they have.

I know this is all about network programming, I've read like many others the [Beejs guide to networking](http://people.csail.mit.edu/albert/bluez-intro/). However, I like to know more about how you can program directly against a bluetooth device. There must be standards to communicate with them.... However I can't spot them through the technical documents.

So, are there any opensource programs out there, developed with Bluez, that I've not spotted? 

For those that are interested, I can add the code I've made so far. However, the code I've written so far is made from the examples in the documentation I've found.

---

### Post by pmasiar on 2007-08-07
It is not obvious what level of help you need: are you experienced Python programmer, skilled in socket programming and stuff, or is it your first serios project?

---

### Post by joe_bruin on 2007-08-07
As you probably already know, Bluez just implements little more than a serial link (like a network socket).  On top of that, there are several Bluetooth "profiles" defined for classes of devices.  These are implemented at the application level.  So if you want to do something like transferring images to a phone, you're probably going to have to implement some sort of object exchange protocol that the phone expects over Bluetooth.  The details of these I am not knowledgeable about, but you won't find much information without reading very technical documents.  You may be able to find libraries that implement these already, otherwise you may have a lot of work to do.

---

### Post by MrJavalava on 2007-08-08
Meh I thought I had avoided most of the "STFW" things.. seems not. I am experienced with Python programming and know about socketprogramming, so that's not really an issue.

The problem is more of finding out how I can access relevant services, as you said, on the application level. I know I have alot of work to do, just hoped someone would pity me and show me the way.. Loads of documents and stuff out there, but not much usefull.

Took me a while to realize about OBEX, didn't really notice what it was, till about 30 mins ago... anyhu. There is an open library called OpenObex, perhaps it can give me a clue. It's clear so far that I need more than just Bluez:

The libraries that I seem to use at the moment are:
1. Network: Bluez
2. Application, OBEX objects: OpenObex

By doing a service search I can easily find out what protocol and port the Obex service on a bluetooth device are. Now, to just figure out how to interface with the devices..

edit:
The purpose is to develop a server app that can commmunicate with BT devices (that has the required services) without installing anything. I want to use the sms and/or mms capability of the BT device. However, I have to figure out the protocol first though. At the moment I've only found server - client examples, and that's not what I'm looking for.

---

### Post by MrJavalava on 2007-08-14
This has taken a while, still no progression.

While I figured out how to send data through the obex push port by using ussp-push, it didn't give me a clue how to do it directly through python. I'm trying to avoid the sys(<put command here>) way you can do in Python. 

I'm wondering wheter people has tried the python-obexftp from Fedora? Going to try it now, hope it can save me some time, creating bindings from header files can be annoying.

The title is starting to be misleading, perhaps i should change it.....

---

### Post by MrJavalava on 2007-08-14
Just linking the obexftp thingy [http://ubuntuforums.org/showthread.php?t=525321&highlight=obexftp](http://ubuntuforums.org/showthread.php?t=525321&highlight=obexftp) which i've created on the forum...

---

### Post by RickSeymour on 2007-09-25
One of the programmes you might be interested in looking into is btms written by an Italian (not sure if its currently maintained), written in C that uses a sqlite database to record and send out files to bluetooth devices.

So with that programme in mind I've decided to write a python programme to do the same. (i've dabbled with PHP programming so python is very new to me)

So far I've got the programme to search the local area for B/T devices, find out if they can receive files (using bluetooth.find_service(name="OBEX Object Push",address=addr)) record that in a sqlite db then use obexftp to send out the file
The plan is to use mainloop to loop the programme so that it constantly searches for new devices and sends out the file....

---

### Post by pmasiar on 2007-09-25
and the question is...?

---

### Post by gralizem on 2008-05-15
Hy

I'm trying to established a bluetooth communication betwwen two embedded system.
At this time i would like to send sound between this two system, so someone could have some docs about that because i'v didn't found anything on the web.

Thanks
(sorry for the english :) )

---

### Post by anjelika on 2008-06-27
Hey,
I need to do exactly the same application!!
Any progress with that, found any interesting info?
I found out that for Linux, there's a library called bluez which can be used with C which implements the bluetooth stack.
```
http://people.csail.mit.edu/albert/bluez-intro/index.html
```
Let me know if you found something useful and maybe we can help each other;)
Thanks

---

### Post by edup_pt on 2010-01-18
Hello anjelika,

Any news?

I want to write an application that sends a file to new bluetooth phones/devices in the bluetooth area. 

The problem is that when sending the file via obex > obexftp_put_file(cli, filepath, filename);

the phone is requiring the passphrase key.


Thanks.

Eduardo

---

