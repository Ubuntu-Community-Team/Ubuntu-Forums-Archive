---
title: "Installing PLONE 3.0 on Dapper Drake 6.06"
date: 2007-11-02
forum: Outdated Tutorials &amp; Tips
---

### Post by mahalie on 2007-11-02
*[SIZE="1"]Note to moderators: There's already a Plone From Scratch HOWTO, however it is for a previous version of Plone (2.0.5) and uses the apt-get method which I've noticed a lot of people in the forums having trouble with. Also, I do not provide 'undo/uninstall' instructions, other than, whip up a a LAMP on VMware and test it first or backup your system. I would welcome uninstall directions if someone who knows what they are doing could provide them.[/SIZE]*

**(Plone 3.0.2 on an 32-bit Ubuntu 6.06 LTS 'Dapper Drake' LAMP)**

**What is Plone? **- [Plone]("http://plone.org") is a pretty cool content management system (CMS) that can be used to manage a website or intranet. Well, I think it's cool based on some videos and documentation on their site. After comparing a lot of CMS options I'm trying out Plone because a) open source is cool. b) Google people are smart, c) it supports LDAP/Kerberos which I need for my all-M$ work enviro, d) there's training/conferences/books available and d) I've read some great reviews and CMS comparisons that rated it #1.

**Doesn't Plone provide installation instructions?** Well, yes. But when I started to read them I got real nervous. What the heck is gcc? libssl? TLS? etc. Those poor geeks at Plone don't realize how noob noob can be! I tried to find better instructions (for me) in the forums and instead I found a lot of people having problems trying to install Plone via Synaptic or apt-get instead of using Plone's instructions, particularly with Dapper Drake.

Please let me know in comments what corrections and improvement I could make. This is my first HowTo for the Ubuntu community and I have a LOT to learn.

You should already have gcc, g++, make and tar installed by default, but if you want to be anal do this:

```
sudo apt-get update
sudo apt-get install gcc g++ make tar
```

[INDENT]Sidetrack > (Possibly totally unnecessary step!) If you're a fair server noob like me you have no idea what libssl and readline libraries and development headers are and what the heck is TLS? Google suggests it has something to do with mail encryption. I read some confusing stuff on Ubuntu Forums about RPM and a program called Alien that converts RPMs to DEB packages seemed probably unrelated but like a handy utility to have and so:

```
sudo apt-get install alien
```[/INDENT]

Download the Plone Installer Package. I saved it in my home folder - it doesn't really matter where you put it so long as you can find it.

```
wget -c http://plone.googlecode.com/files/Plone-3.0.2-UnifiedInstaller-Rev2.tar.gz
tar zxf Plone-3.0.2-UnifiedInstaller-Rev2.tar.gz
cd Plone-3.0.2-UnifiedInstaller
```

Here's where you have to pay attention. You can do a ZEO or Stand-Alone install. "WTF?" you say? Yeah, well just pick your poison after [reading all about it]("http://plone.org/documentation/tutorial/installing-plone-3-with-the-unified-installer"). I'm doing a Stand-Alone as root install.

According to the README.TXT in the installation package my choice of standalone instance installed as root will result in Plone being installed to /opt/Plone-3.0.2 and libz and libjpeg libraries getting built in /user/local. A "plone" user will be added and Zope will be configured to run under that user id. You need to start Zope as root user (via sudo).

```
sudo ./install.sh standalone
```

Then a whole bunch of stuff happens. Lots of gcc (compiling) and checking for things (lots of yes and a few no-s in my case). Just wait, this is a good time to read about checking your installation and [next steps here]("http://plone.org/documentation/tutorial/installing-plone-3-with-the-unified-installer/running-the-unified-installer"). Or just catch up on your RSS feeds and I'll walk you through it.

If you're real lucky, this is what you'll see when it's all said and done:

> ```
#####################################################################
######################  Installation Complete  ######################
Use the account information below to log into the Zope Management Interface
The account has full 'Manager' privileges.

  Username: admin
  Password: xxxxxxxx

Before you start Plone, you should review the settings in:
 /opt/Plone-3.0.2/zinstance/etc/zope.conf

Adjust the ports Plone uses before starting the site, if necessary
To start Plone, issue the following command in a Terminal window:

 sudo /opt/Plone-3.0.2/zinstance/bin/zopectl start

To stop Plone, issue the following command in a Terminal window:
 sudo /opt/Plone-3.0.2/zinstance/bin/zopectl stop

Plone successfully installed at /opt/Plone-3.0.2
See /opt/Plone-3.0.2/zinstance/adminPassword.txt
for password and startup instructions

Ask for help on plone-users list or #plone
Submit feedback and report errors at http://dev.plone.org/plone

This installer was created by Kamal Gill (kamalgill at mac.com)
Maintainers for Plone 3 are Kamal Gill and Steve McMahon (steve at dcn.org)
```


First, write down your admin password!! Then, check zope.conf to 'review settings'. I'm not familiar with them, so I just scanned for the port. Found it on line 969 (YMMV), set to the default Zope/Plone standalone install grabs, port 8080.

```
sudo vi /opt/Plone-3.0.2/zinstance/etc/zope.conf
use :q! to quit vi without messing anything up
```

Use netcat to see what ports you have open already. (Netcat comes with Ubuntu install)

```
nc -z -v -w2 localhost 1-65535
```

After confirming that 8080 is avail (or changing it in zope.conf if it is not available) continue following directions.

```
sudo /opt/Plone-3.0.2/zinstance/bin/zopectl start
```
  #that last part is an L not a 1, took me a while...

Then go to: [http://localhost:8080](http://localhost:8080) (or sub servername for localhost to test from other computer). If you're lucky AGAIN you'll see the Zope Quick Start page!! Wahoo! Hii Fiiiiveh to self! Then look at the example site: [http://localhost:8080/Plone](http://localhost:8080/Plone), and then check out the management interface at [http://localhost:8080/manage](http://localhost:8080/manage). Have fun. I hope it was as good for you as it was for me!

BTW: I suggest the Ubuntu Support Forum and [Plone Support Forum]("http://www.nabble.com/Plone-f6741.html") for help. I am noob, I prolly shouldn't even publish this and I definitely can't support anyone. (Will happily update and improve this based on suggestions though.)

---

