---
title: "Difference between RedHat and Ubuntu?"
date: 2008-10-19
forum: Other OS Talk
---

### Post by 22-250 on 2008-10-19
I have a few different linux distos on cd that I can try.. don't really know anything about any of them, just kind of trying different ones to find what works best for me.
Ubuntu installed now
The Plus is that the sound works without a problem (where as on Xandros, I could not get the sound to work).
The Minuses are that it is not straightforward to download Yahoo Messenger (trying and it's a pain) or as I hear, to get limewire working (haven't tried yet myself) something about these being .exe files?? 

Anyway, I have a Red Hat 9 set of discs that I am thinking about trying.
Any idea if it would be easier to get the above .exe files installed using it? 

Thanks

---

### Post by cardinals_fan on 2008-10-19
You can't install .exe files in Linux.  WINE can let you run .exe's if absolutely necessary, but your mileage may vary.

As for Red Hat vs. Ubuntu, here are some pros/cons:

_Pros_
* Red Hat (or CentOS, its free clone) is extremely stable
* Awesome enterprise support
* Security updates for years

_Cons_
* The cost of stability is outdated software
* For a new Linux user, Ubuntu is easier

EDIT: To instant message, use the Pidgin program included with Ubuntu.  When it starts, click "add" to add a new account and select Yahoo for the protocol.  Limewire has a Linux version [here]("http://www.limewire.com/download/download.php?version=linux_deb")

---

### Post by Cochise on 2008-10-19
Try Frostwire instead of limewire, almost identical.

---

### Post by igknighted on 2008-10-19
Red Hat 9 is ancient.  I would think those disks have more value as coasters.  Using Fedora or Centos would be the modern equivalent (or RHEL, but that would be costly for a home user).

There is a linux version of Limewire, you don't need the windows EXE file.  All you need as a valid Java install, available at [www.java.com](www.java.com) (or in the repositories of many distributions).

There is a Yahoo! version for linux IIRC, but it's so old it's almost worthless.  I would look at kopete, pidgin or empathy for clients to use Yahoo! chat.  Only kopete will currently use the webcam if you need that, but if you don't any of these will do nicely.

---

### Post by 22-250 on 2008-10-19
Thanks to all so far! Maybe I try a couple more things with Ubuntu before leaving :) 


> **igknighted said:**
> 
There is a linux version of Limewire, you don't need the windows EXE file.  All you need as a valid Java install, available at [www.java.com](www.java.com) (or in the repositories of many distributions).

There is a Yahoo! version for linux IIRC, but it's so old it's almost worthless.  I would look at kopete, pidgin or empathy for clients to use Yahoo! chat.  Only kopete will currently use the webcam if you need that, but if you don't any of these will do nicely.

I want to be able to view my friend's webcam, so is this kopete you mention what I need? How do I go about installing it? I'm looking at [http://kopete.kde.org/releases.php](http://kopete.kde.org/releases.php) and not sure where to go from there. thx

---

### Post by 22-250 on 2008-10-19
and thanks for the Frostwire/limewire info/links, I'll see if I can get either to work

---

### Post by cardinals_fan on 2008-10-19
> **22-250 said:**
> 
I want to be able to view my friend's webcam, so is this kopete you mention what I need? How do I go about installing it?
Open a terminal (Accessories -> Terminal) and type the following:```
sudo apt-get install kopete
```Then look under the Network/Internet menu for it.

---

### Post by bwhite82 on 2008-10-19
Redhat is geared toward businesses (although they do have an Enterprise Desktop version which is still for businesses). It is indeed rock solid and very easy to use, you can download a 30 day trial of RHEL after which time you will no longer be able to update it with RH repos. Additionally, someone already mentioned CentOS which is a clone minus the artwork.

The key differences are package management (RPM vs. DEB), one is geared to the home user while one toward the business user.

---

### Post by 22-250 on 2008-10-19
> **cardinals_fan said:**
> Open a terminal (Accessories -> Terminal) and type the following:```
sudo apt-get install kopete
```Then look under the Network/Internet menu for it.

Wow. that was easy, thanks! I think I got it working.

Next question... how do I decide between Frostwire and Limewire?? I have never used either before.

---

### Post by cardinals_fan on 2008-10-19
> **22-250 said:**
> 
Next question... how do I decide between Frostwire and Limewire?? I have never used either before.
Neither have I.  What are you trying to accomplish?

---

### Post by 22-250 on 2008-10-19
> **igknighted said:**
> 

There is a linux version of Limewire, you don't need the windows EXE file.  All you need as a valid Java install, available at [www.java.com](www.java.com) (or in the repositories of many distributions).

How do I find out what version of Java I have -or if I even have it installed at all? and/or which of these four Linux versions should I download?
[http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com:80](http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com:80)

---

### Post by 22-250 on 2008-10-19
> **cardinals_fan said:**
> Neither have I.  What are you trying to accomplish?
I just want to be able to download a few mp3 files now and then

---

### Post by forger on 2008-10-19
careful about copyrights 22-250
Let's just leave it at that.

If you want to install frostwire:
```
sudo apt-get install frostwire sun-java6-jre
sudo update-alternatives --config java
```

Choose the number that responds to the sun java package and press enter

---

### Post by Cochise on 2008-10-20
The latest frostwire is available here in .deb format. Download the file and double click it to install.

[http://www.frostwire.com/?id=downloads](http://www.frostwire.com/?id=downloads)

---

### Post by igknighted on 2008-10-20
22-250:

Almost never in linux will you go to a website and download the program.  Most are installed as easily as Kopete was for you.  Try opening the "Add/Remove Programs" program in your Applications menu.  There are some 20,000 free to use applications there that are installed just as easily.

---

### Post by Canis familiaris on 2008-10-20
Please read the INSTALLING ANYTHING GUIDE...(link in my sig), it would give you a lot of insight on How to Install Programs in Ubuntu.

---

### Post by jseiser on 2008-10-20
instead of frost wire/lime wire you could also try gtk-gnutella

its a free, open source project that does the same things and uses the gnutella network like they do.  should be in the repo's 'apt-get install gtk-gnutella'

also, don't try and install .exe's in Linux or download the program from a website and install it until you have checked in synaptic to make sure its not already in the repo's.  You want to install the packages from the repo's so ubuntu can handle the dependencies and updating /removal of the packages.  This is with all Linux distributions.

---

### Post by MaxIBoy on 2008-10-22
I'd go for frostwire-- it can double as a bittorrent client (limewire can only handle gnutella,) and it runs a little bit lighter.

gtk-gnutella runs VERY light and fast, but the interface is confusing and a bad idea for new users.

---

