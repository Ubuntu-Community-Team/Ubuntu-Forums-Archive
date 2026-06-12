---
title: "How to: Jinzora on a LAMP - Dapper"
date: 2006-10-15
forum: Outdated Tutorials &amp; Tips
---

### Post by coastdweller on 2006-10-15
Original Creation Date: 10-15-2006

**Purpose of this how-to**: This how-to is geared towards those with the desire to store their mp3 collection in a "Jinzora Stand-alone" LAMP server. This allows for easy management and streaming through a web browser.

Note: Currently the developers seem to have a problem with case sensitivity so symlinks are neccesary to get the current version working (As of the Original date above). This HOW-TO assumes you have already set up a LAMP and have access to MySQL (You know the username and password).

-- To begin: Download the jznightly

Step 1 - **:: DOWNLOADING ::**

- Open a console and move to your root web site directory:

Note: (Usually /var/www).

> mv /var/www

- Download the file

> wget [http://www.jasbone.com/jznightly.tar.gz](http://www.jasbone.com/jznightly.tar.gz)

Step 2 -  **:: EXTRACTION ::**

- To unpack the file :

> tar -zxvf jzcurrent.tar.gz

Note: If you're this far you have a folder sitting in /var/www called jinzora2

- You now can move the folder to another folder called music (This will not affect the install).

> sudo mv jinzora2 music

Step 3 - **:: INSTALLING ::**

- Move into the unpacked directory:

> mv music

- Allowing the installer to execute:

> chmod 744 ./configure.sh

Note: The installer needs certain permissions, set these by running this command:

> sh ./configure.sh

Note: If everything went well you can now proceed to the web based installer. Open a browser and go to the http location of your files. The installer will begin. The installer is pretty straight forward but note, unless you have MPD installed and configured set this up as a **streaming only** installation.

Note: You will get a security breach warning until you finish the following step:

Step 4 - ** :: FINISHING UP ::**

Note: After you've finished the web based installer move the install folder or delete it:

-moving

> mv install install.bak

-deleting

> sudo rm -rf install

Note: Now symlink the two folders with case problems:

-move into the templates directory:

> cd templates

-create the symlinks

> sudo ln -s slick Slick
> sudo ln -s slimzora Slimzora

Note: That should just about do it. This is my first how-to and I'm fairly new to the linux desktop environment - hope it works for you. I hope I haven't been too winded and inaccurate.

Ref:
- main site : [http://www.jinzora.com/](http://www.jinzora.com/)
- downloads : [http://www.jinzora.com/pages.php?pn=downloads](http://www.jinzora.com/pages.php?pn=downloads)
- forums : [http://www.jinzora.com/forums/](http://www.jinzora.com/forums/)
- faqs : [http://www.jinzorahelp.com/en/faq](http://www.jinzorahelp.com/en/faq)
- documentation : [http://www.jinzorahelp.com/en/documentation](http://www.jinzorahelp.com/en/documentation)

---

### Post by atkc on 2007-09-26
Can I mount an NFS or CIFS volume so that Jinzora will have access to it and use it for the music directory?

---

### Post by GrammatonCleric on 2007-10-23
Yup... I'm mounting my music collection via NFS under my Ubuntu Jinzora virtual machine.  The one thing I would cover in this how to is enabling ogg support in Jinzora.  

To enable ogg support select:
```

Admin Tools -> System Tools -> Settings Manager -> Main Settings -> Resampling

```Change:

```

allow_resample = false 

to true

```Correct the path to oggdec to:

```

/usr/bin/oggdec

```Also change the **default_resample** to something more to your liking.  Mine is set to 160.

One last thing remove the sample rates listed in the "**resampleRates**" that you don't want to hear your music at.
 
-GC

---

### Post by Stormspace on 2007-11-07
Need some quick help. I have Jinzora2 installed and working through apache, however it cannot see my music library. Currently my music library is on a second HDD mounted as /media/disk. I can browse to the disk, but cannot see any folders. I also have the /media/disk/music folder shared out with samba with no problems as well.

---

### Post by GrammatonCleric on 2007-11-07
> **Stormspace said:**
> Need some quick help. I have Jinzora2 installed and working through apache, however it cannot see my music library. Currently my music library is on a second HDD mounted as /media/disk. I can browse to the disk, but cannot see any folders. I also have the /media/disk/music folder shared out with samba with no problems as well.


What are the directory and file permissions set to?  Can www-data user/group view them? 

- GC

---

### Post by Stormspace on 2007-11-07
> **GrammatonCleric said:**
> What are the directory and file permissions set to?  Can www-data user/group view them? 

- GC

THX! That little hint did it.

---

### Post by coastdweller on 2008-01-28
Going to be updating this shortly. Love my jinzora server =)

---

### Post by PinkFloyd102489 on 2008-01-28
Just a little nitpicking here, but the command to change directory to /var/www is not mv, it's cd. ;-)

---

### Post by secretspicy15 on 2008-05-17
Nice walkthrough; the install is easy enough, but you make sure one does not get hung up on silly details... like running configure before trying to install...
:-D

---

### Post by stokedfish on 2008-06-08
Some of this doesn't work anymore...

An update for the newest Jinzora version would be very much appreciated!

---

