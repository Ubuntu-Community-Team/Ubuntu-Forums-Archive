---
title: "&quot;Are you root?&quot;"
date: 2012-12-24
forum: New to Ubuntu
---

### Post by KayeNg on 2012-12-24
Hi guys. 
Typed this in Terminal:
apt-get install audacious

I got this:
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

So I typed sudo in front of "apt-get install audacious"
Everything worked fine.

But how do I become "root"?
I guess I sort of know what that means because I'm an Android phone user and I've rooted my phone countless times and I'm familiar with the advantages of root. Is this the same with Ubuntu? So how do I become root?

Also, a lot of people say Audacious media player is like Linux version of winamp.  But I don't think it even has an equalizer.  What's up with that? How is it any better than Ubuntu's default music player, Rhythm box music player? They're both very basic, as far as I can tell.

Thanks guys!!

---

### Post by deadflowr on 2012-12-24
Add the word sudo to the beginning of the command.
This will give you the elevated privileges needed.
It will prompt you for a password, use the password you made when you installed(most likely).
The password field will appear blank when typing, no worries.

sudo gives a user temporary root.(super user, or substitute user)

It is case sensitive, so use lower case.

Edit: Ubuntu comes with root locked and disabled. The reason because sudo fills this need, and being root open ended is a security risk, both from outsider and ones self.

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by arpanaut on 2012-12-24
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Should be all you need to know...
With Ubuntu it is seldom necessary to actually be at the "root" terminal.
The root account is not activated w/ Ubuntu

---

### Post by Bashing-om on 2012-12-24
Let me start my response with:
The kernel protects it's self by implementing a procedure to ensure that you know what you are doing (assumes). In order to make changes to the system, one must have the proper authority. One way to gain this authority is to use "sudo" -> super user do. This authority is all enter woven in permissions and access.

As you may surmise, at this point it is appropriate for you to learn. Reading is good !
google the term "sudo ubuntu" and let the process begin ! (google is your friend)

As to the various merits of differing players, can not advise, my needs are basic and "rhythmbox" suffices.
[INDENT][INDENT]just my humble opinion < == BDQ
   
[/INDENT][/INDENT]

---

### Post by snowpine on 2012-12-24
You can also use the Ubuntu Software Center to easily install apps with a few mouse clicks. Here's a how-to:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by andrew.46 on 2012-12-25
BTW equaliser can be found with **[COLOR="Red"]Ctrl+E[/COLOR]**. Spend a little more time with Audacious and you will find that it grows on you, a very robust and reasonably featured media player.

---

### Post by slooksterpsv on 2012-12-25
Root you'll only want to use if you're installing software or making modifications to system files. In which case you can just use sudo to open those particular items as root, but if you really really really want to use root, type in sudo su and you'll become root.

WARNING: You can highly damage your system if you use just root and not a standard user. If you want to login as root you can sudo su into root and type in passwd to change root's password. Again I highly recommend you DO NOT DO THIS cause root is only as needed. If you need access to certain files or directories e.g. web server, you can setup a symbolic link and have apache point to a directory in your home folder to for the web server - much safer.

Either way. 

As for music player, personally I like Songbird or Exaile (Exaile is my favorite)

---

### Post by maruf7 on 2012-12-25
Try this command instead:


sudo apt-get install audacios


Now you will be asked for password, enter the administrator password amd press ENTER

---

### Post by KayeNg on 2012-12-25
Thanks guys, really appreciate it.

andrew.46 , I don't mean to sound like a brat but how on earth would a new Audacious user like me know that ctrl E opens up the equalizer? Is this common for many Linux apps? I'm just curious. I won't be going back to windows any time soon unless it's absolutely necessary.  Just want to know what to expect from Linux.

By the way, are there any presets? I don't see any. You know, rock, pop, classical, room, auditorium, earphones, etc.

Thanks guys!

---

### Post by andrew.46 on 2012-12-25
> **KayeNg said:**
> andrew.46 , I don't mean to sound like a brat but how on earth would a new Audacious user like me know that ctrl E opens up the equalizer? Is this common for many Linux apps? I'm just curious. I won't be going back to windows any time soon unless it's absolutely necessary.  Just want to know what to expect from Linux.

Using the gtk interface the option can be seen under 'Output' in the top title bar, keyboard shortcut is printed next to it :)

---

### Post by KayeNg on 2012-12-26
I apologize, I didn't realize that menus of apps are displayed in the task bar at the top of the screen.  Thanks!

---

### Post by audiomick on 2012-12-26
More on sudo.

If you want to use sudo to start an application with a graphical interface, you should use gksudo. Here is why
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

It is, incidentally, worth having a general poke around at that site. There is some good info there.

Examples for gksudo might be

```
gksudo gedit
```

to get an instance of the editor gedit with root privileges. This will allow you to open, edit and save files that belong to root. Sometimes neccessary when you get a bit deeper into your system.

```
gksudo nautilus
```

gives you an instance of the file manager Nautilus with root privileges. Can be useful if file permissions get messed up.

Be careful with both of these. They both put you in a position to completely break your system by erasing something critical.

---

### Post by offgridguy on 2012-12-26
@ audiomick, this is helpful for me, thank you.

---

### Post by audiomick on 2012-12-26
You're welcome. Glad someone could use it.

---

### Post by andrew.46 on 2012-12-26
> **KayeNg said:**
> I apologize, I didn't realize that menus of apps are displayed in the task bar at the top of the screen.  Thanks!

Easy to miss, this is a feature pretty unique to the whole Unity experience. it is a lot easier to see on a non-Unity desktop :).

---

