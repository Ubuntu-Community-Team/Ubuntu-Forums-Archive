---
title: "root privileges"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by totalnewb4ever on 2008-08-19
How do I give myself root privileges.  I know there are a number of ways of acting as root, but I want my username to be just as good as root when it comes to all read/write privileges.  I'm sick of getting the message that I don't have permission to do things -- it's my computer.  Thanks for any help.

---

### Post by kellemes on 2008-08-19
All your questions are answered here.. [https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

---

### Post by snowpine on 2008-08-19
> **totalnewb4ever said:**
> How do I give myself root privileges.  I know there are a number of ways of acting as root, but I want my username to be just as good as root when it comes to all read/write privileges.  I'm sick of getting the message that I don't have permission to do things -- it's my computer.  Thanks for any help.

Hi TotalNewb, if you look around on the internet, you can probably find the answer to your question... however, you will not find the answer here on ubuntuforums because the official board policy is that It's Not A Good Idea. :)

Check out the link from Kellemes for some good info.

---

### Post by linuxguymarshall on 2008-08-19
Its not good to do this but run this : 

```
gksudo nautilus
```

---

### Post by fuhrysteve on 2008-08-19
> **linuxguymarshall said:**
> Its not good to do this but run this : 

```
gksudo nautilus
```

That will work, but a better solution is to do this:

```
sudo apt-get install nautilus-gksu nautilus-image-converter nautilus-open-terminal
```

That will let you do a lot of fun stuff, including open a folder as an administrator.

I hear you when it comes to the "it's my computer" stuff in Gnome. I'm always amazed at some of the stuff you can do on the command line though.

source: [http://lifehacker.com/394538/enable-advanced-permissions-dialog-in-nautilus](http://lifehacker.com/394538/enable-advanced-permissions-dialog-in-nautilus)

---

### Post by Vivaldi Gloria on 2008-08-19
[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by totalnewb4ever on 2008-08-19
Thanks everyone.  The main reason I got fed up with the root privileges thing is because the sudo command didn't always work.  In fact, I often found myself frustrated at the lack of times it worked.  I understand it's not the safest thing, but that nautilus seems to do the trick when I need it.  I'll be sure to be extra safe about the whole process, though.  Thanks all.

---

### Post by kellemes on 2008-08-20
> **totalnewb4ever said:**
> Thanks everyone.  The main reason I got fed up with the root privileges thing is because the sudo command didn't always work.  In fact, I often found myself frustrated at the lack of times it worked.  I understand it's not the safest thing, but that nautilus seems to do the trick when I need it.  I'll be sure to be extra safe about the whole process, though.  Thanks all.

Sudo works, you need to try to understand it instead of bypassing it. Sooner or later you have to.

---

### Post by pmsumner on 2008-08-20
> **totalnewb4ever said:**
> Thanks everyone.  The main reason I got fed up with the root privileges thing is because the sudo command didn't always work.  In fact, I often found myself frustrated at the lack of times it worked.  I understand it's not the safest thing, but that nautilus seems to do the trick when I need it.  I'll be sure to be extra safe about the whole process, though.  Thanks all.

Can you advise what exactly didn't work with sudo?

It's all very well being "extra-safe" working as root but the fact remains that you can easily destroy an installation working as root without trying at all.

---

### Post by t0p on 2008-08-20
> **linuxguymarshall said:**
> Its not good to do this but run this : 

```
gksudo nautilus
```

What do you mean it isn't good to do this?! **sudo** and **gksudo** *are* good!  It's logging in as root that's bad around here!!

---

### Post by t0p on 2008-08-20
> **pmsumner said:**
> Can you advise what exactly didn't work with sudo?

It's all very well being "extra-safe" working as root but the fact remains that you can easily destroy an installation working as root without trying at all.

Don't worry!  The OP isn't talking about working as root!  He mentioned "nautilus" - he means either the command **gksudo nautilus** or the nautilus-gksu extension, both of which are just graphical forms of sudo.

Also, it's pretty easy to brick your computer using sudo!

---

### Post by totalnewb4ever on 2008-08-20
> **pmsumner said:**
> Can you advise what exactly didn't work with sudo?

It's all very well being "extra-safe" working as root but the fact remains that you can easily destroy an installation working as root without trying at all.

I don't remember exactly what I was doing, but really anything involving creating a folder/file in the filesystem or altering a file resulted in a "no permission" message, even when using sudo.  One specific example is when I was trying to change a file in the X11 folder (xorg or something like that) so my pen tablet would work properly, and I couldn't until I found out how to do it via signing in as root in recovery mode.  I got it to work and everything is glorious now.  My most recent problem was creating a folder to store cache for a game (runescape).  I couldn't get permission to do that, either, until I used the nautilus way of doing it.  Again, now I accomplished what I needed to and everything is working great.

Thanks for everyone's concern and I understand now that having root privileges 24/7 is not the most brilliant thing.  Ubuntu is taking some getting used to, but I still love it (recently switched over from Windows).  Peace.

---

