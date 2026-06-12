---
title: "[SOLVED] Running Yahoo in Wine ??"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by hufferd on 2008-07-26
Hi all its been awhile since I posted any questions that is a good thing I think that means things are going well and I am getting used to ubuntu LOL 

with that said I still have one of a few issues Im still trying to get around and that is.....  

I use pidgin for my messaging and it works well for what I need to do most of the time.  How ever I do have one friend that I like to share photos with from time to time and we also like to play many of the games that are built into yahoo.   The issue I have is I have not been able to get yahoo to work with wine I have been able to get it to install and it will run but thats about it I cant type anything in any of yahoo's boxes and it seems to just sit there.  I wanted to know if anyone has had any luck with getting yahoo messenger to work under wine ??? 

Thanks 
D

---

### Post by SunnyRabbiera on 2008-07-26
Eh, its hit and miss I am afraid.
This is yahoo's fault

---

### Post by rossjman1 on 2008-07-26
I believe that Yahoo has a Linux version of its messenger.

---

### Post by SunnyRabbiera on 2008-07-26
> **rossjman1 said:**
> I believe that Yahoo has a Linux version of its messenger.

Yes but its seriously behind in the times, IM clients are such a pain to get in linux...

---

### Post by loell on 2008-07-26
for  yahoo messenger photo sharing you can use

[gyachi]("http://ubuntuforums.org/showthread.php?t=773802")

but if you're also looking for yahoo games, there's no client for linux for that.

---

### Post by bushda on 2008-07-26
My wife uses the voice chat function of Yahoo Messenger quite a bit for the classes she's taking. Rather than swear at wine, I set up a Windows XP VM in VirtualBox. It works very well that way, but is definitely a more involved approach over running it in wine. 

If you've got an XP license and install media though, it's an option.

---

### Post by tye959 on 2008-07-26
I'd say delete wine and reinstall the latest version. Or just reinstall if you have the latest version. (Maybe there could be a corrupt file?) idk thats all I know

---

### Post by jimmy the saint on 2008-07-27
I second gyachi.  It can do everything that yahoo messenger does (at least all that matters) plus more.  The voice chat works, camera support, plus extra security features that you dont get with yahoo.  It would also be easier than haveing to open a virtualmachine first!

---

### Post by barbedsaber on 2008-07-27
I thought that yahoo allowed you to IM and do all that stuff from a browser?
sure, its a pain, but it's almost guaranteed to work.
(then again, I could be wrong, so don't get too excited until you give it a go

---

### Post by kansasnoob on 2008-07-27
> **barbedsaber said:**
> I thought that yahoo allowed you to IM and do all that stuff from a browser?
sure, its a pain, but it's almost guaranteed to work.
(then again, I could be wrong, so don't get too excited until you give it a go

It does! I do it! I use the Yahoo Classic theme and just IM  using Yahoo from within Firefox. No problems!

Well, setting up my Logitech webcam sucked almost as much as setting up the mic, but it works!

No need for anything fancy!

---

### Post by barbedsaber on 2008-07-27
Thats great to hear. Now, if you wouldn't mind, could you mark this thread as solved? (so that people looking for people to help know that the problem is fixed, and people looking for a solution to the same problem know that the one here works) all you have to do is click thread tools, and then mark as solved. Thanks. :)

---

### Post by lisati on 2008-07-27
> **rossjman1 said:**
> I believe that Yahoo has a Linux version of its messenger.
Pidgin can connect with Yahoo's messenger service

---

### Post by barbedsaber on 2008-07-27
> **lisati said:**
> Pidgin can connect with Yahoo's messenger service

yes, but the only functionality you get, is talking, with text. Yahoo offers a lot more than this. It is worth noting that kopete allows video talk, but not things such as games.

---

### Post by hufferd on 2008-07-27
> **loell said:**
> for  yahoo messenger photo sharing you can use

[gyachi]("http://ubuntuforums.org/showthread.php?t=773802")

but if you're also looking for yahoo games, there's no client for linux for that.


I cant seem to get this to install it is for a 32 bit system and I am running a 64 bit.......  I never have been able very weel to get 32 bit apps to work on a 64 bit system :(

---

### Post by loell on 2008-07-27
> **hufferd said:**
> I cant seem to get this to install it is for a 32 bit system and I am running a 64 bit.......  I never have been able very weel to get 32 bit apps to work on a 64 bit system :(

in your 64 bit system, install [getlibs]("http://ubuntuforums.org/showthread.php?t=474790")

then in the terminal,

force  to install,
```
sudo dpkg -i --force-all gyachi_1.1.31-1_i386.deb
```

get the 32 bit dependencies
```
sudo getlibs /usr/bin/gyachi
```

---

### Post by steveneddy on 2008-07-27
I say turn your fiends on to Skype for video and voice chat and find somewhere else to play games.

---

