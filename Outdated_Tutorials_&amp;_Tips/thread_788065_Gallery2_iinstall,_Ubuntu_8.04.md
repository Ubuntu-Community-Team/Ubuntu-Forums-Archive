---
title: "Gallery2 iinstall, Ubuntu 8.04"
date: 2008-05-09
forum: Outdated Tutorials &amp; Tips
---

### Post by oraldlight on 2008-05-09
Ubuntu 8.04 + Gallery2.

+ I had a web server configured and working for over a year. Out of sight - out of mind. I failed to log all the pertinent information of how I made it happen. Upgrading from 6.06 was my downfall. Ill prepared, ill planned, I trashed my web server. Everything was gone because something happened to the database and I had no idea how to recover. Configurations got stomped upon by Apache update. I lost the whole site, in effect.

+ Back to square one. I am using a 64bit OS because I can, not that I need to. Attempts to use a desktop OS were not successful because I failed to understand the MySQL root+password difference from OS user+password from Gallery2 user+password. This how-to may work on Desktop versions, but the LAMP option in Server OS versions saved me time and sanity, so I stuck with it.


How-to for the impatient:

1) Install Server version of OS. During install, select "OpenSSH" and "LAMP", to facilitate remote access, and for Apache2, MySQL and PHP to be installed and pre-configured. This saves time and sanity for Gallery2 requirements. During install, MySQL will ask for a root user and password - BE SURE TO SAVE THIS INFORMATION FOR LATER!

Once the OS is installed verify webserver is working by browsing to http://<serverIP> or [http://localhost](http://localhost). You should see an "**It works!**" message. This confirms the server is operational.

2) Install the following Gallery2 helper files before Gallery2 to make Gallery's setup easier later on:
	dcraw	      - RAW file manipulation
	ffmpeg        - multimedia manipulation
 	imagemagick   - graphics manipulation
 	zip	      - compression manipulation
 	libgd2-xpm    - GD graphics library
 	jhead         - EXIF manipulation
 	libjpeg-progs - JPEG manipulation
 	
 The following line should be run to simulate the install, to see if any dependencies or conflicts exist:
  $ sudo apt-get install -s dcraw ffmpeg imagemagick zip libgd2-xpm jhead libjpeg-progs

Remove the "-s" and rerun to install for real:
  $ sudo apt-get install dcraw ffmpeg imagemagick zip libgd2-xpm jhead libjpeg-progs

Test install Gallery2 for any dependencies or conflicts:
  $ sudo apt-get install -s gallery2

If all is good, install Gallery2:
  $ sudo apt-get install gallery2

  Make an edit to a Gallery config file to point an alias to the install directory:
  $ sudo nano /etc/apache2/conf.d/gallery2
    Uncomment - #Alias /gallery2 /usr/share/gallery2 by deleting the "#".  Save and close. 
 
  After Gallery2 installs, verify it is working by pointing your browser to http://<serverIP>/gallery2 or [http://localhost/gallery2](http://localhost/gallery2). You should see a configuration/welcome page. STOP!! Do not continue! That's right, close the browser and prepare for the Gallery2 configuration process.
	
  I found it advantageous to prepare a Gallery image store prior to the install. A requirement of this is for the folder to be owned and writeable by the group 'www-data' which is what Gallery2 operates under.
  $ sudo mkdir <path_and_name of_folder>
  $ sudo chgrp www-data <path_and_name of_folder>
  $ chmod 770 <path_and_name of_folder>
	
  One more edit that I still do not fully understand why I need to do. I had to edit a php.ini file to doulbe a memory allocation. Without this, configuration would halt with an error.
  $ sudo nano /etc/php5/apache2/php.ini
    Find and change the line that says 
				"memory_limit" and change from 16m to 32m
		Save and exit
		Now restart Apapche to make changes effective.
		$ sudo /etc/init.d/apache2 restart
		
	Now you can go back and begin the Gallery2 initial configuration. Browse to http://<serverIP>/gallery2 or [http://localhost/gallery2](http://localhost/gallery2) and follow instructions.  Create/save the authentication login.txt file, point to the image store folder created above, use the MySQL root user+password from prior, and you should complete the install successfully. You now should have a functional Galelry2 install ready for use. There are plenty of more detailed walk-throughs on this specific task on the web, should you need assistance. 
	
	Not being a Web guru, I was stumped with the final detail -  how to make Gallery2 the default "home page"	for visitors. I recognized that two issues needed to be combined. Apache2 was using the /var/www/index.html as the default starting point. That may be O.K. if I was a web-head and wanted to write pages, but not my intent. Gallery was using the default install path, /etc/usr/gallery, properly. I needed to 'bridge' the two together. 
	
  The answer was finally found by altering an Apache config file.
  $ sudo nano /etc/apache2/sites-available/default 
    Find the folowing:
        DocumentRoot /var/www/default
    and change it to
	DocumentRoot /usr/share/gallery2
    Now restart apache
  $ sudo /etc/init.d/apache2 reload

  Now users will arrive at Gallery2 home page upon entering my url. I printed these instructions and made comments of users/passowrds/applications and paths, and placed inside the server(resides in my home, so security is not a major concern). Hoepfully I can read my own handwriting next time I need this info.
  
Yet to do:
   Learn how to back up MySQL and Gallery2 image store folders. Just in case...

---

### Post by skydive814 on 2008-06-21
I was following your tutorial (kudos), but found this typo that really drove me nuts: 

this: *libjpeg-prog *
needs to be: *libjpeg-prog**[COLOR="Red"]s[/COLOR]***

and

this: *[http://localhost/gallery](http://localhost/gallery)*
needs to be: *[http://localhost/gallery](http://localhost/gallery)**[COLOR="Red"]2[/COLOR]***
-sky

---

### Post by csmith23 on 2008-06-22
nice catch :)

---

### Post by oraldlight on 2008-06-23
Sky - typos fixed, thanks.

As for the "http://localhost/gallery2"  I never thought of that....

---

### Post by gwolfman on 2008-07-11
Thanks for the tutorial.  I'm going to be setting this up (hopefully) this weekend and I'll follow you simple guide.  I'll let you know how it goes. :)

Btw, anyone know how to configure the server so that [http://pix.domain.com](http://pix.domain.com) goes to gallery2?  My Apache skillz are close to nonexistent.  Thanks!

---

### Post by gwolfman on 2008-07-11
Actually, I found some time tonight, lucky me :)

you wrote:
> $ sudo chgrp www-data <path_and_name of_folder>
$ chmod 770 <path_and_name of_folder>

but when I was installing gallery2, it recommended doing this (essentially changing the owner and group together with different permissions)

> $ sudo chown www-data:www-data <path_and_name of_folder>
$ chmod 755 <path_and_name of_folder>

Looks like it's all working.  I installed gallery2 before I added the packages and noticed that I didn't have imagemagick installed, so I installed imagemagick, removed gallery2, then reinstalled it (just to be sure) and everything went perfectly smooth.

Thanks!

Though my question about pix.domain.com still stands.  Any help would be greatly appreciated! :)

---

### Post by graphius on 2008-08-29
> anyone know how to configure the server so that [http://pix.domain.com](http://pix.domain.com) goes to gallery2

You could just make the default index.htm page into a redirect....:)

no apache required

---

### Post by technicalmajor on 2009-01-17
Okay guys 

Really sorry for this, I think I am being very dim, I have followed the install guide but I am unable to navigate to 

[http://localhost/gallery2](http://localhost/gallery2)

error 404 (page not found)

I have reloaded apache config, do any of you know how to check where it's installed it??

---

### Post by 3L33T on 2009-05-17
OralDlight:  THANKS for this nice how-to.  I have used menalto gallery when it was still version 1.0.X on Redhat Enterprise LInux.  I have since replaced that RHEL server with an Ubuntu 8.04 server but could not get the darn thing working on Ubuntu following menalto's install.  I will definitely give it a shot again and hopefully be able to host my galleries again online.

Cheers!

---

### Post by 3L33T on 2009-06-11
OK, so finally had the chance to try this nice DIY install (thanks guys!).  I followed it EXACTLY and had no issues...until I wanted to view the Gallery page.  I'm getting a blank white page and nothing else.  I tried restarting apache and mysql but still getting blank screen.  Any ideas what went wrong?

---

### Post by graphius on 2009-06-14
> **3L33T said:**
> OK, so finally had the chance to try this nice DIY install (thanks guys!).  I followed it EXACTLY and had no issues...until I wanted to view the Gallery page.  I'm getting a blank white page and nothing else.  I tried restarting apache and mysql but still getting blank screen.  Any ideas what went wrong?

Check your permissions. Make sure all the appropriate directories are writable by the webserver.

sudo chown -r www-data:www-data images  (where images is your gallery directory)

I could be wrong, but this has tripped me up. My site works fine on my home server. ([http://klughammer.dnsalias.com/kg/gallery2](http://klughammer.dnsalias.com/kg/gallery2))

---

### Post by theworldhadteeth on 2009-07-22
Need a little help. I followed this through and it says it is successful. Then it says, "Enter the URL in your browser for main.php in your gallery2 directory." But when I do this, it takes me back to the beginning of the graphical installer instead of to my new gallery. Any ideas what I might have missed or done wrong? 
Ubuntu Server 8.04
Virtual Hosting... if that helps.
Thanks,
-theworldhadteeth

---

### Post by oraldlight on 2009-08-29
I revisited this and found the instructions could use some additional notations (now tested upon 9.04-32bit):

After initially installing gallery2, trying to verify by accessing "http://<localhost>/gallery2/" I would get a blank page. Not until I set user/permissions of the folder, made Apache edits and restarted Apache, would I get to the installer page.

---

