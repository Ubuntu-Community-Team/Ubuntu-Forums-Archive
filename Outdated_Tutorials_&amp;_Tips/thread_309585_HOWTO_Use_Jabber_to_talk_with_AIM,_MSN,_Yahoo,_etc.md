---
title: "HOWTO: Use Jabber to talk with AIM, MSN, Yahoo, etc"
date: 2006-11-29
forum: Outdated Tutorials &amp; Tips
---

### Post by zombie_killer on 2006-11-29
Taken from [Thad Hopkins' apologetics site]("http://othello.alma.edu/~07tmhopk/ubuntuhowto.html#gaimcommunicate").

This guide will present a process using Psi Jabber, Gaim, an AIM account, and a gTalk account, with the user running Ubuntu. However, any Jabber account and client will work, and the process will also work for Yahoo! and MSN protocols. Psi Jabber is required, however, to get things going. After that, Psi Jabber can be removed.

[B]Grab the tools
[/B]
Required for this tutorial, Psi Jabber is an open source and cross-platform Jabber client. The qca-tls package is required for Psi Jabber to work with gTalk. To install these on Ubuntu, first check your repositories to make sure "Universe" is enabled. Then:

```

sudo apt-get install psi
sudo apt-get install qca-tls
```

To install Gaim 2.0.0 Beta 3, [download the file]("http://othello.alma.edu/~07tmhopk/files/gaim-2.0.0beta3_2.0.0beta3-1_i386.deb").

Right click > Open with "GDebi Package Installer"

**Setup Psi Jabber for gTalk**

   1. Open Psi Jabber, and add a new account. Name the account whatever you'd like (this will be your gTalk account).
   2. For your Jabber ID, enter your entire e-mail address (username@gmail.com).

[IMG]http://othello.alma.edu/~07tmhopk/graphics/psi1.png[/IMG]

   3. In the Connection tab, check Use SSL encryption (to server), Ignore SSL warnings, Allow Plaintext Login (don't worry, the SSL layer will keep you safe), Send "Keep-alive" packets (for NAT timeouts), and then Manually Specify Server Host/Port:. That's every box on the tab.
   4. Enter "talk.google.com" in the Host: dialog box, and the port should be set to 5223.

[IMG]http://othello.alma.edu/~07tmhopk/graphics/psi2.png[/IMG]

   5. Connect to gTalk.
[B]
Setup the transport[/B]

   1. Go to Service Discovery and input one of the servers from [this site]("http://www.jabber.org/network/oldnetwork.shtml") into the Address: box. Make sure the server you're using supports the protocol you'd like to use. This might take a few tries to find a server that works. As of this posting, the server jabber.3gnt.org seems to work just fine.
   2. Click Browse.
   3. Right-click on the protocol you'd like to use, and click Register. If Register isn't available, either wait a moment to see if it shows up, or find another server. Enter the information for whatever account you'd like to use.

[IMG]http://othello.alma.edu/~07tmhopk/graphics/psi3.png[/IMG]

   4. After registering the account, you'll begin to receive what might be hundreds of notifications on Psi Jabber. These will be all of your buddies on the account you registered asking to be on your buddy list. You'll have to go through every single one and authorize them. When you're all done with that, you can close out Psi Jabber, uninstall it if you'd like (sudo apt-get remove psi), and boot up your favorite Jabber client (I recommend Gaim). After you connect, your buddy list will soon populate with all of the buddies you just authorized.

---

### Post by bodhi.zazen on 2006-12-03
Nice How-to 



This thread has been added to the UDSF wiki.

[Jabber](http://doc.gwos.org/index.php/Jabber)


If you do a major update to your how-to please send me a PM. Either I can teach you how to add to the wiki or I can try to maintain the wiki myself (as time allows), thank you.

Peace be with you,


[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by Ptero-4 on 2007-02-10
How do I do this on Gaim? Are there transports for Yahoo and M$N in Gaim? Do I need to have a hotmail account to use the M$N transport?

---

### Post by pay on 2007-02-12
> **Ptero-4 said:**
> How do I do this on Gaim? Are there transports for Yahoo and M$N in Gaim? Do I need to have a hotmail account to use the M$N transport?For gaim, do it as it says and then fire up gaim with jabber and the users should be there. Yes msn and yahoo are supported in gaim. No you don't need a hotmail account. I use a gmail account with it, but you have to register it somehow with microsoft ( i forget how).

---

### Post by marko_4454 on 2007-03-05
For those interested...for gaim to work as an MSN live ID. You need to first register here:

[https://accountservices.passport.net/ppnetworkhome.srf?vv=450&lc=1033](https://accountservices.passport.net/ppnetworkhome.srf?vv=450&lc=1033)

---

### Post by Ptero-4 on 2007-03-26
Thanks I registered there. Now Do I put my gmail address and LiveID passowrd as M$N in gaim?

---

### Post by sabme on 2007-04-04
Thanks for the How 2!

I didn't allow some of my buddies to authorize how can I get them back?

Sab

---

