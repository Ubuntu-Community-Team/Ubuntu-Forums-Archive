---
title: "Doesn't connects to my Braodband Internet"
date: 2012-05-31
forum: New to Ubuntu
---

### Post by rafsuntaskin on 2012-05-31
):P hi!!! there.

I have just installed Ubuntu 12.04 in my pc today and this is the first time I am using Ubuntu.

But I am **not able** to establish any Internet connection on it. It says **Wired connection disconnected.**
I use a **Broadband **connection that requires **username **and **password **to establish **connection **(pppoe may be).

My system is:

AMD phenom II X4 965BE(3.40 Ghz)
MOBO- 890GXM-G65
Ram- 4GB


Waiting for help
:KS

---

### Post by MrBledi on 2012-05-31
if you use broadband, ADSL you don't have to use username and password thing to get connected with dial UP like once upon a time! :D

---

### Post by rafsuntaskin on 2012-05-31
> **MrBledi said:**
> if you use broadband, ADSL you don't have to use username and password thing to get connected with dial UP like once upon a time! :D
All I know is it's a broadband connection that is working perfectly on my Win 7 with Realtek Ethernet.

I need to login using the Username and Password in windows to get connected.

In cas of ubuntu what shoul I do?

---

### Post by MrBledi on 2012-05-31
someone should guide you to find your ethernet realtek drivers and then, i don't think you need for username and password login! :) 

here is a link that could help you for your drivers!
[http://www.realtek.com/Downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com/Downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false)

Scroll down to linux drivers download, install them and see the result! :) 

i'm sure that after some test you will get an positive result! :)

---

### Post by steeldriver on 2012-05-31
In my experience DSL almost always requires login / password authentication (PAP or CHAP) - you may be unaware of this if you use an external DSL modem or modem-router where the credentials are hidden in the device setup

If you are using pppoe direct (i.e. with an internal modem) then you may want to check out pppoeconf

[http://manpages.ubuntu.com/manpages/precise/man8/pppoeconf.8.html](http://manpages.ubuntu.com/manpages/precise/man8/pppoeconf.8.html)

Otherwise iirc you have to edit things manually in the 'secrets' files (but it's been a long time since I've used pppoe)

Hope this helps

---

### Post by shashanksingh on 2012-05-31
You could go to Edit connections-> DSL -> Add

Type in your username and password and the service name of the server if required.

If yours is a normal ethernet card directly connected without your own external modem, this should work I guess

---

### Post by varma1993 on 2012-05-31
I',m sure this works....
I had the same  problem...

if you are using 32 bit ubuntu, then download pppoe drivers from one of the servers listed in the following link:
[http://packages.ubuntu.com/hardy/i386/pppoe/download](http://packages.ubuntu.com/hardy/i386/pppoe/download)

if 64 bit download from
[http://packages.debian.org/squeeze/amd64/pppoe/download](http://packages.debian.org/squeeze/amd64/pppoe/download)

for installation open terminal and direct it to the file in the  downloads directory and type:
sudo dpkg -i "file name.deb" (no quotes)
while installing enter the username and password you use to login into your broadband connection.

restart system and open terminal and type :
sudo pon dsl-provider

That's it you are connected.

To disconnect type:
sudo poff
in the terminal.

---

### Post by rafsuntaskin on 2012-06-08
Thanks for your replies guys.... However I reinstalled MY ubuntu and this time it was okay :)  and I used DSL connection as it pppoe in Windows.

---

