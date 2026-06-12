---
title: "Help setting up Hardy Heron Intranet"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by gotguts on 2008-08-22
Hi ya'll,

.     This is my first post as I've been searching heavily through existing threads for too long.  So please forgive my newbieness.
.     Trying to set up an intranet within my small business.  We have several projects for which we have websites.  So far they have all been created with MS FrontPage and shared via simple windows file sharing in an XP environment.
.     Hardy Heron up and running as a MyHost.  Tweaks made with GUI Webmin 1.4 (command line gets too confusing if I screw up but I don't mind using the terminal mode if I have to).  Samba seems OK with some users setup and I can view the shared directories from other PCs on the network.  Created a folder for "MySite" in /var/www/ and transferred a website to the /var/www/mysite/ folder.  I can type in the static IP address in another PC on the LAN and successfully get to the default web page in /var/www/ (get the "It Works!" page popping up).  I almost can see MySite too, typed in [http://*hostip](http://*hostip)*/mysite and got directed to the home page of MySite. 
.     BUT, none of the images show up! :confused: I know they're there and can seem them properly in the page if I navigate via \\MyHost\MySite\index.html
.     OK, so I really don't know what I'm doing but really want to learn this powerful cool tool, Ubuntu Linux, that is.  I just am not sure how to setup Apache, the DNS, BIND, or the rest of it.  And I think part of the problem is that there's not alot out there on a GUI setup of Hardy Heron.

Thanks In Advance!

[www.sequelspecial.com](www.sequelspecial.com)

---

### Post by motang on 2008-08-22
So does **mysite** have the same create and delete permission?  Right click on the folder (*var/www/mysite*) in Nautilus and see if you can make it so that you, your group have create and delete permission and for others access only.  That should do the trick, I had to do that for all of my own.

---

### Post by decoherence on 2008-08-22
Hi there!

Say you have an image that isn't showing up and it's in /var/www/MySite/images/MyImage.jpg

What kind of error does it give you if you browse to [http://hostip/MySite/images/MyImage.jpg?](http://hostip/MySite/images/MyImage.jpg?)

Also, I believe Webmin has the facility to view log files. See if you can find Apache's access.log or error.log and see if there is anything that refers to your images.

If I were to guess right now, I'd say the permissions on them are too restrictive, but that's just wild speculation.

Webmin is a good start for people who want to set up Apache, BIND/DNS (BIND is the DNS server) without having to quest around the filesystem for config files (half the challenge for new users!) Just remember to read the very fine manuals so you eventually get an idea of what Webmin is doing! (man apache2, man bind, etc)

---

### Post by gotguts on 2008-08-22
Thanks Motang.  I checked the permissions, as you suggested, and all seems good (777 for now so I should be OK).

Decoherence, I think you might be on to something.  If I click on a hyperlink to a JPG image I get "webpage cannot be found.  But, if i navigate there through the folders the JPG image shows up fine.

---

### Post by gotguts on 2008-08-22
Oh, something else I just noticed.  None of the webpage themes are showing up.  Its as though my browser doesn't know where to look.

Do I need to set up a virtual server or something?

---

