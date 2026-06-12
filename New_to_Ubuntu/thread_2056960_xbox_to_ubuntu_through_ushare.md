---
title: "xbox to ubuntu through ushare"
date: 2012-09-12
forum: New to Ubuntu
---

### Post by kabukiM0n0 on 2012-09-12
Hey there, 

I'm trying to link up my xbox to my system, ubuntu 12.04 using Ushare. but I am having a few minor errors which my brain can't quite  get round. 

this is my config file
```
# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=uShare

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=eth1

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49200

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/home/km

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=

# Enable Web interface (yes/no)
USHARE_ENABLE_WEB=yes

# Enable Telnet control interface (yes/no)
USHARE_ENABLE_TELNET=no

# Use XboX 360 compatibility mode (yes/no)
USHARE_ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
USHARE_ENABLE_DLNA=no

```

and this is the response I get after typing ```
ushare --x
```

```
Interface eth1 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 192.168.1.40:49153
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /home/km
Found 23550 files and subdirectories.

```

The console is connected to a router and I am on the same connection though wireless. 

Thanks in advance.

---

### Post by kabukiM0n0 on 2012-09-12
Not entirely sure how, but I got it working ...

---

### Post by crparis on 2012-09-14
This needs updating as the updates to the Xbox's dashboard have implemented new "features":

I'm trying to get this working as well, but having some problems with the Xbox itself.  Specifically, the Xbox requires you to setup the Media Center PC.  After seeing it on the network (ushare is working fine!) the Xbox gives me an 8-character "setup key" that I am supposed to put in to the Windowns Media Center to "protect" my content.  There's some info from MS at:

[www.xbox.com/pcsetup](www.xbox.com/pcsetup)

So I've got ushare setup fine, the xbox sees it, but I don't know the ushare/linux version of entering the setup key to allow my media server to be used.

See also: [http://ubuntuforums.org/showthread.php?t=1438813](http://ubuntuforums.org/showthread.php?t=1438813)

Thanks for any help that can be lent!

---

### Post by megamister on 2012-09-14
So using ushare, you can stream music and movies etc to the Xbox and PS3, and it works ok eh? I have been thinking about that for a couple days now.

---

### Post by kabukiM0n0 on 2012-09-16
You can't use media center unless you run it in a virtual box. 
If the config files are set up properly 
```
sudo gedit /etc/ushare.conf
```
there you set up you're configuration - I can paste mine if you still can't get it working. 
Then go into videos/music on your xbox and your computer name should appear - not all formats work on xbox, but for me the majority do. 
Remember you have to type **yes** in the option that allows to connect to xbox or ps3 in the conf. files. 

Also realize that you cannot plug your pc directly into the xbox. It has to go through a router, switch, etc.

---

### Post by walkeraj on 2012-09-16
> **kabukiM0n0 said:**
> Then go into videos/music on your xbox and your computer name should appear

Have you read the rest of this post?  There is a new "setup key" that you need; ushare does not provide any method to input it.  Read before you respond, please.

In other words, to everyone that might be reading: No, ushare does not currently seem to work, and judging from their website that says that development has been discontinued, it's not likely to work any time soon.  We will need to find another solution.

---

### Post by kabukiM0n0 on 2012-09-19
> **walkeraj said:**
> Have you read the rest of this post?  There is a new "setup key" that you need; ushare does not provide any method to input it.  Read before you respond, please.

In other words, to everyone that might be reading: No, ushare does not currently seem to work, and judging from their website that says that development has been discontinued, it's not likely to work any time soon.  We will need to find another solution.

You think I might have read the post .. I created it. 

For your information. you don't need any set-up key ... as that's to go through Windows Media Centre, which would completely defy the point of using Ushare - I already explained this ... above your comment.
> You can't use media center unless you run it in a virtual box
Pay more attention before you throw sarky comments around, please.

---

### Post by maravingian on 2012-10-23
At last, I`ve finally read something that makes sense why Geexbox & Ushare haven`t been working since the upgrade to Precise.  Thankyou :)

Now, the million dollar question is...Does anyone have any ideas on an alternative to sdtream from Computer to Xbox??

So far I haven`t found anything that fits...

---

### Post by maravingian on 2012-10-23
At last, I`ve finally read something that makes sense why Geexbox & Ushare haven`t been working since the upgrade to Quantal.  Thankyou :)

Now, the million dollar question is...Does anyone have any ideas on an alternative to sdtream from Computer to Xbox??

So far I haven`t found anything that fits...

---

### Post by d.vanheeckeren on 2012-11-21
I set up ushare on my server box here at the house, named the server,  and enabled xbox support, then started it up.  Worked FLAWLESSLY for  playing music, which is what I wanted to do!

I have one little  issue though...No matter what I've tried, the xbox never shows more than  1000 items.   Artists, Albums, and songs.  Is that an xbox limitation  or a ushare limitation?

Thanks in advance for any ideas.   :)

---

