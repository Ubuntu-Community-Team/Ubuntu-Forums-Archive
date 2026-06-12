---
title: "Question about a wireless router setup..."
date: 2012-01-28
forum: New to Ubuntu
---

### Post by ryanryanryan on 2012-01-28
... First, thanks for taking the time to read this post.

I'm new to Linux. About 4 days. 

I have a Belkin Wireless G adaptor - F5D7050B.

Simply put, do I need to install the software that came with the router? Or do I just need to use the command terminal to look for/install drivers?

Thanks.

---

### Post by _0R10N on 2012-01-28
Hi! Follow this links and see if it works for you

[http://www.linuxant.com/driverloader/](http://www.linuxant.com/driverloader/)
[http://opensource.bureau-cornavin.com/belkin/index.html](http://opensource.bureau-cornavin.com/belkin/index.html)

Regards!

---

### Post by oldfred on 2012-01-28
Most of the software is just to automate the setup. You can usually login to the router and do the setup from Firefox or whatever browser you use.

It should tell you default userid & password, which are the first things you want to change, but make sure you save/record/remember them.

Then you just need to choose your wi-fi security wpa2 and give that the site name & pw you need to use wi-fi.

---

### Post by ryanryanryan on 2012-01-28
Great information. just what i was looking for. Will let you know how it goes! (crossing my fingers)

---

### Post by oldfred on 2012-01-28
If you did not get a written set of instructions, you may be able to get them from the CD. I recently bought a low-cost router and went to their site for the manual. But later I found it on the CD as a pdf.

Default router ip is often this which I bookmarked:

[http://192.168.0.1/main.html](http://192.168.0.1/main.html)

But it may vary by vendor.

---

### Post by ryanryanryan on 2012-01-28
Oldfred - Yup, I checked out the PDF on the installation CD and dug up some info...

However, setting up the wireless was as simple as plugging it in and unplugging the ethernet connection.

I also ran a few commands to see if the hardware was detected, and sure enough it was. 

Thanks for the the help.

---

### Post by oldfred on 2012-01-29
While it may work out of the box, you really need to reset passwords from default. Otherwise your neighbors and anyone driving by can use your wi-fi. And a default login password allows them to totally reset system.

---

### Post by mcduck on 2012-01-29
> **oldfred said:**
> While it may work out of the box, you really need to reset passwords from default. Otherwise your neighbors and anyone driving by can use your wi-fi. And a default login password allows them to totally reset system.

...or do even worse things, like configure a custom DNS address on the router, redirecting all the network traffic to some completely different location or though a server that monitors the traffic and steals passwords and other information.

---

### Post by anewguy on 2012-01-29
a BIG +1 !!  Almost every router, or at least routers of the same brand, use the same default userid and password. Without changing it, you are leaving yourself wide open.  This userid/password combination is not something you have to enter each time you want to connect to the net via the router - it is like the root userid/password for your system, except it's for the router.  You most definitely need to change this to something specific to you (and remember it - perhaps writing it down somewhere).  This userid/password is to protect your router from being modified by others - not just being used to connect to the net - but actually modifying the setup of the router.

In addition, if you did not go through the router setup, you have an open network, meaning any and every body can connect to your network.  Again, as already mentioned, change this to WPA2.

Both of these things are changed via the router setup, which you access by logically connecting to the control port for the router.  Usually this is something like [http://192.168.0.0](http://192.168.0.0) or [http://192.168.0.1](http://192.168.0.1) entered in your browser address line.  This should bring a up a login screen from your router.  This is where you need to know what the default is so you can log in.  Once logged in, change the administrator userid or at least the administrator password.  Next change the encryption to WPA2 and supply a password/passphrase.  If you are not sure on this, read the documentation or search the web for ideas on creating an appropriate password.  You probably have to do a "save" on each of these updates, which will usually reset the router.

So, if you change the administrator stuff first and the router resets, you will probably need to use the new administrator userid/password to get back in to change the encryption.

Once you have changed the encryption, the first time you try to connect the router will ask you for a password - this is not your login password but is the WPA2 password/passphrase/key you entered into the router.

Dave ;)

---

