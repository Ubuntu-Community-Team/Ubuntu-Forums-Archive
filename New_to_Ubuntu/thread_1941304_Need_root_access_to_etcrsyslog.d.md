---
title: "Need root access to /etc/rsyslog.d"
date: 2012-03-15
forum: New to Ubuntu
---

### Post by patriot56 on 2012-03-15
I have installed Firestarter firewall and it seems there is a known bug when installing it on Ubuntu 11.10. According to the Firestarter web site, the etc/rsyslog.d needs to be edited. However I am not able to save the edited file because I don't have permission to do so.  I tried right clicking on the file to change the permissions but that didn't work. Can anyone tell me how to gain root (su) access to this file?   Thank you in advance.

---

### Post by woxuxow on 2012-03-15
there is two way to do that
the first one an easiest way is : sudo nano /etc/rsyslog.d
the second and graphical one : sudo nautilus
then go to the path and edit the file like what you did before

---

### Post by yetiman64 on 2012-03-15
> **MustafaJF said:**
> there is two way to do that
the first one an easiest way is : sudo nano 
the second and graphical one : **sudo nautilus**
then go to the path and edit the file

For graphical applications please use gksudo or gksu,  the "Graphical Sudo" section at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) has the reasons why.

OP, firestarter is very out of date last updated in about 2005, last entry here [http://www.fs-security.com/news.php](http://www.fs-security.com/news.php) is 31st July 2005. Using out of date software is not a particularly good idea. The last package on sourceforge for it was last modified 30-01-2005.

I would recommend gufw as a graphical firewall, or you can just use the code below to enable the inbuilt firewall ufw,

```
sudo ufw enable 
```gufw is a graphical front end for ufw (supplied with Ubuntu but not turned on by default - the code above switches it on)

To check if ufw is on, you can at any time use the code,
```
sudo ufw status
```Or to turn it off,
```
sudo ufw disable
``` The graphical front end for it (gufw) is far easier to use (edit: than the codes above) and just invokes these codes and more to manage ufw's set up.

---

### Post by westie457 on 2012-03-15
@ patriot56

Firestarter is out of date and does not appear to have anyone working on it since late 2010. You would be better off using the default firewall UFW - uncomplicated firewall - or GUFW - the graphical uncomplicated fiewall.

A further point here is when running a graphical application such as gedit or nautilus as root use gksudo instead of sudo. Most of the time there is no problems using sudo to run graphical applications however when it goes wrong it can do a thorough job of hosing your system.


Ninjaed by yetiman64 with a far better explanation

---

### Post by patriot56 on 2012-03-15
Thank you MusafaJF

---

### Post by garyed on 2012-03-15
I've gotten into the habit of copying files before I edit them if I need to have root priviliges to edit them in the first place.
something like this:
```

sudo cp filename filename_3_15_2012 

```  

This way if I screw up editing the original file its easy to go back to the way it was before.

---

### Post by bodhi.zazen on 2012-03-15
> **MustafaJF said:**
> there is two way to do that
the first one an easiest way is : sudo nano /etc/rsyslog.d
the second and graphical one : sudo nautilus
then go to the path and edit the file like what you did before

Both of those are inaccurate.

"easiest way" as you say is

```
sudo -e /etc/rsyslog.d
```

less typing.

When running graphical applications, such as nautilus or gedit, you should use gksu.

```
gksu nautilus
gksu gedit /etc/rsyslog.d
```

See [https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)

---

### Post by bodhi.zazen on 2012-03-15
> **garyed said:**
> I've gotten into the habit of copying files before I edit them if I need to have root priviliges to edit them in the first place.
something like this:
```

sudo cp filename filename_3_15_2012 

```  

This way if I screw up editing the original file its easy to go back to the way it was before.

That and comment your edits

```
# comments are typically started with a #
# edit bodhi.zazen date enabled foo
```

---

### Post by patriot56 on 2012-03-15
> **yetiman64 said:**
> For graphical applications please use gksudo or gksu,  the "Graphical Sudo" section at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) has the reasons why.

OP, firestarter is very out of date last updated in about 2005, last entry here [http://www.fs-security.com/news.php](http://www.fs-security.com/news.php) is 31st July 2005. Using out of date software is not a particularly good idea. The last package on sourceforge for it was last modified 30-01-2005.

I would recommend gufw as a graphical firewall, or you can just use the code below to enable the inbuilt firewall ufw,

```
sudo ufw enable 
```gufw is a graphical front end for ufw (supplied with Ubuntu but not turned on by default - the code above switches it on)

To check if ufw is on, you can at any time use the code,
```
sudo ufw status
```Or to turn it off,
```
sudo ufw disable
``` The graphical front end for it (gufw) is far easier to use (edit: than the codes above) and just invokes these codes and more to manage ufw's set up.

@ Yetiman64 - Thank you for responding to my post.  I was aware that Firestarter was outdated but I had hoped that after installing it I would be able to update it through some kind of auto-update via their web site.  (I guess that was a little naive now that I think about it.)
However after reading your post I think I will just remove it and follow your advise.  It sounds like the best option.
Thank you again for your help and advise.  It is greatly appreciated.:D

---

### Post by patriot56 on 2012-03-15
@ garyed - Getting into the habit of  copying files before editing them.  That is a GREAT idea and advise.  I am going to start doing the same. 
Thank you.

---

### Post by patriot56 on 2012-03-15
> **bodhi.zazen said:**
> Both of those are inaccurate.

"easiest way" as you say is

```
sudo -e /etc/rsyslog.d
```less typing.

When running graphical applications, such as nautilus or gedit, you should use gksu.

```
gksu nautilus
gksu gedit /etc/rsyslog.d
```See [https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)

I am still learning how to use Ubuntu (Linux in general) and when I receive this kind of advice I am very grateful.
Your knowledge and experience is very valued to someone like me who *is* still learning.
I will follow your advice.

As yetiman64 said, Firestarter is very out of date so I am going to remove it and go with his advise to use **ufw (gufw) **as this is already installed with Ubuntu.

Removing Firestarter and using something else however, doesn't change  anything about the sound advise that I have received from you (and  others) to this post.

Thank you again for your help.

This is a great Forum.\\:D/

---

### Post by patriot56 on 2012-03-15
@ Yediman64
Thank you very much for your help.
This is really good stuff. 
Information worth adding to my Linux Terminal Journal.
Because I am still learning to use Linux, I am keeping an journal of Terminal commands.
The GUI is a comfortable and familiar way to use most distributions of Linux, however, I think the CLI is still the most powerful tool to use.
It's probably not good for someone that is new to such a powerful OS like Linux, but you have to start somewhere, right?

Thanks again

---

### Post by patriot56 on 2012-03-15
@ Yediman64
Thank you for helping with this problem.

---

### Post by bodhi.zazen on 2012-03-15
> **patriot56 said:**
> Removing Firestarter and using something else however, doesn't change  anything about the sound advise that I have received from you (and  others) to this post.

Removing firestarter is not so straight forward, you need to purge it

```
sudo apt-get purge firestarter
```

Otherwise the configuration files are not removed, and they conflict with ufw.

If you have already removed firestarter, re-install it , then purge it.

---

### Post by yetiman64 on 2012-03-15
patriot56, please make sure you read and follow bodhi.zazen's post above carefully, firestarter will need to be purged correctly. 

_*Also just to clarify*_, only ufw is installed by default. Once you clean out firestarter as per bodhi.zazen's instructions above, you will then need to get gufw from the software center. 

Good luck hope it all goes smoothly for you.

---

