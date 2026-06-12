---
title: "HOWTO: Setup Gossip for other protocols &amp; build it from source with Tango icons"
date: 2006-06-14
forum: Outdated Tutorials &amp; Tips
---

### Post by mynimal on 2006-06-14
Basically, Gossip is a very lightweight (As in non-bloated. Believe me, it's got all the features you need) Jabber client. But don't let the word "Jabber" scare you, it can be easily set up to connect to IRC, ICQ, AIM, MSN, and Yahoo simultaneously. You can also set up Gossip to use tabbed messaging windows, play sounds when you get messages, and display notifications when any of your buddies come online. What's great about this messenger is that it doesn't cram buttons and giant text fields into every window like Gaim does. Well, I'll just attatch a screenshot for you instead of babbling on.

Alright, basically, you need to install Psi to set up your account. Gossip is still under heavy development, so hopefully you won't have to do this in the future. Psi is in the repositories, so just do this in the terminal:
```
sudo apt-get install psi
```
You may have to enable universe/multiverse.

You should be greeted with this message:
[img]http://img504.imageshack.us/img504/6100/18qg.png[/img]
Type in whatever you want for the name, and check "Register new account". Pick a server out of [this list](http://www.jabber.org/user/publicservers.shtml), with whatever protocols you want filled in. For example, if you want AIM, ICQ, MSN, IRC, and Yahoo, a good one is **im.flosoft.biz**. Since the protocols are voluntary, it doesn't matter if one has protocols you won't use. Here's what I should have if I were to register for **im.flosoft.biz**:
[img]http://img511.imageshack.us/img511/8403/21og.png[/img]

Now, click "Register" in the bottom right. You should get a message that says the account was successfully registered. Click OK. The next screen you can ignore, since most of it is just Psi settings and we aren't going to be using Psi. You can change your information by clicking the "Edit Personal Details..." button under the Details tab, but that's also optional. Click Save.

Now, for the good stuff. Change your status to Online by clicking the button in the bottom right of the buddy list window. You might be greeted with a Personal Details window, but you can either fill that in or close it. Next, click the button in the bottom left of the buddy list window and click "Service Discovery". You should have this screen:
[img]http://img375.imageshack.us/img375/5509/33jk.png[/img]

AIM Transport = AIM
ICQ Transport = ICQ
ejabberd/mod_irc = IRC
MSN Transport = MSN
? = Yahoo? (Try another server I guess. Hrm.)

Right click on whichever protocol you want and click "Register...". You're not registering for a new IM address for that protocol, you're just registering it for use with your Jabber account. Fill in the account info for the account you want to register. For example, if I were to register for AIM and my AIM username was joebob, I'd fill that in fir tge username and the AIM password for the password. It's the same for MSN and ICQ. It's probably the same for Yahoo. For IRC you just specify your username, the field at the bottom of that window is optional.

Now that I'm registered with AIM, there's something new in the contact list. You should see this:
[img]http://img509.imageshack.us/img509/9282/40bp.png[/img]

Right click on the entry next to the flashing monitor and select "Recieve Incoming Event". Click the "Add/Auth" button. Click the Next button and then click Close.

There should now be lots of your buddies in the buddy window with flashing monitors next to them. You can ignore this. Their names will be something like **theirname@im.flosoft.biz**. If you rename them here it won't do any harm, and it will go right on through to Gossip with their custom names intact (I think. It did for me anyway.).

Repeat the registration process just like you did with AIM with any other protocols you want. After you're done, you can finally close and uninstall psi like so:
```
sudo apt-get remove psi
```

And now we're on to Gossip!

[http://developer.imendio.com/wiki/Loudmouth](http://developer.imendio.com/wiki/Loudmouth) (Needed to build Gossip)
[http://www.mynimalistic.net/stuff/junk/gossip-0.11.2.tar.gz](http://www.mynimalistic.net/stuff/junk/gossip-0.11.2.tar.gz) (Tango icons)
[http://www.gnomefiles.org/app.php?soft_id=193](http://www.gnomefiles.org/app.php?soft_id=193) (Normal icons. Download link is at the bottom)

Believe me, the Tango icons look much better. Extract the .tar.gz file into your home folder, and then do this:
```
sudo apt-get install libxss-dev
cd
cd gossip*
./configure
make
sudo make install
```
Now, start up Gossip. It should be under **Applications -> Internet -> Gossip Instant Messenger**, or if you don't use gnome-panel you can just launch it by typing **gossip** into a terminal or other launcher. Since I already had Gossip installed it kept my account info, so some of this might be a little askew from what you end up with. Sorry. I'm guessing this is the first window you'll see:

[img]http://img360.imageshack.us/img360/7039/59cl.png[/img]
Select "**Yes**".

The first field should be whatever username you registered with using Psi. For example, "**yourname@im.flosoft.biz**". Fill in the password you used for registration, too. In the next window, the first field should be what you're using it on. Home is fine. Keep the rest of the fields as they are and click Forward. You can fill in whatever you want here. "Flosoft" is fine. Click Forward, and now click Apply.

You now should have Gossip set up correctly. :)

---

### Post by gamma on 2006-09-24
UPDATE: For those who don't want KDE libs on their system, try using Gajim instead of PSI to set up transports!



Just wanted to say cool guide. I'm sick of gaim's interface and Gaim-2 seems like a step in the wrong direction. Gossip with Tango icons is very pretty and simple. :D

---

### Post by Nano on 2006-09-24
Indeed, there might be a cool team behind Gaim but no one seems to be good designing GUIs...

---

### Post by Wallakoala on 2006-09-24
this is pretty cool. I think I might like gaim more but I am gonna give gossip a good try.

---

### Post by gamma on 2006-09-24
Gossip seems to have everything I need. Logging, you can see when users are typing, very simple, aliases, etc. I have no problem talking to buddies on AIM either..

---

### Post by mynimal on 2006-10-05
I've actually grown more akin to Gajim. It makes a fabulous IM client, way better than Gossip in my opinion. Plus, it supports icon themes. :D It's just as minimal and compact, if not more.

---

### Post by Nano on 2006-10-06
I wish it was even more minimal, actually. I see a lot of space (pixels) wasted for no reason. I'd love something like Miranda-IM

---

### Post by mynimal on 2006-10-06
Where do you see them wasted? After a few hacking in the advanced preferences I got it [very minimal](http://xs107.xs.to/xs107/06406/Screenshot.png).

Honestly I'm just waiting for something like Adium. Miranda IM is great but it's very unstable. MSN connectivity is, to be blunt, terrible.

---

### Post by John.Michael.Kane on 2006-10-06
The file you list **psi** is this not a kde lib?

If this is the case. Then you should let the user know they will be mixing kde with gnome...

---

### Post by stalefries on 2006-10-06
psi is an IM client, and people use it a lot to set up jabber transports, as it can do it easily. It isn't a kde lib.

---

### Post by John.Michael.Kane on 2006-10-06
psi Jabber client using Qt

Qt=trolltech=kde.. there should be a note that this howto mixes dependencies.

---

### Post by gamma on 2006-10-07
You can set up transports with Gajim.. I'll edit my upper post to note that.

---

