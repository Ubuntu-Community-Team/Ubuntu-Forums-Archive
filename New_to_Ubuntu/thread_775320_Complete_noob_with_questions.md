---
title: "Complete noob with questions"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by zeththedarkmage on 2008-04-30
Basic Windows user here and I've been sick of using it for a while and I have really been wanting to try out 8.04 LTS but I am a bit worried about making the switch. There are not many programs that I use on my computer, the main ones are VLC media player with the cccp codec pack, stepmania, and a couple other basic programs that I am worried about being compatible with WINE. Also I have an nvidia video card that I don't know if I have the driver disc for and I use an LPT port with a program that allows me to configure the inputs through it since I use it for hooking a playstation controller to my computer. So I was wondering if someone on here could kinda of tell me the best way of going about making sure these couple of programs can make the jump I would love to be able to switch over to Linux.

Thanks in advance.

---

### Post by swoll1980 on 2008-04-30
Ubuntu has vlc and full nvidia support

---

### Post by zeththedarkmage on 2008-04-30
Thank you for that information, do you know if it will be able to recognize my lpt card?

---

### Post by Mogurijin on 2008-04-30
The best thing to do would be to find equivalents in Linux to avoid using WINE if you can. However, for compatibility, you can check [The AppDB]("appdb.winehq.com"). And as mentioned earlier, VLC has a Linux version, and you won't need your Windows nVidia drivers, there are Linux ones. But do you have a wireless adapter? And why do you need cccp if you have VLC?

PS
Throw in a LiveCD and test things out. Also, if you search the name of your lpt card on these forums, something will probably come up. Or you can try google.

---

### Post by sujoy on 2008-04-30
and as for the lpt card try using the live cd first

---

### Post by swoll1980 on 2008-04-30
I know that lpt cards work in Ubuntu not sure how or to what extent( i don't have one)

---

### Post by zeththedarkmage on 2008-04-30
Thanks for the useful information. As far as I knew I thought I had to have cccp to play mkv files I had downloaded but I didn't know for sure. As far as the livecd goes do I just put it in there and it then it will let me test compatibility with the lpt card?

---

### Post by Mogurijin on 2008-04-30
I have played .mkv files through VLC, works great. It can handle the multiple audio and stuff just fine ;).

---

### Post by swoll1980 on 2008-04-30
> **zeththedarkmage said:**
> Thanks for the useful information. As far as I knew I thought I had to have cccp to play mkv files I had downloaded but I didn't know for sure. As far as the livecd goes do I just put it in there and it then it will let me test compatibility with the lpt card?

correct

---

### Post by oskar2000 on 2008-04-30
What programs do you need?
The app-db is a good place to start:
[http://appdb.winehq.org/](http://appdb.winehq.org/)
Search field is on the bottom left.
If you scroll down on the application page you will often find workarounds for common issues.

If you have problems with wine and you don't mind paying a little for support, you can give Crossover or Cedega a try.

You can also run windows in a virtual machine - try virtual box.

But many programs have equivalent open source applications. You should try those first.

Which programs do you need to get running / replacements for?

---

### Post by Mogurijin on 2008-04-30
Stepmania has a Linux version:
[http://www.stepmania.com/wiki/Downloads]("http://www.stepmania.com/wiki/Downloads")

So you're set there too. That knocks out VLC, cccp, and Stepmania. What are your other "basic programs"? Maybe we can help you up with those too.

---

### Post by zeththedarkmage on 2008-04-30
The main programs are a program that is pretty much a ripped version of the game in the groove (very similar to dance dance revolution) that is a .exe and has all of my custom songs in it, I could use stepmania if I had to but I would prefer to not have to. Also the only other real program I am concerned about would be the program that allows me to configure the lpt card input to use my playstation controller through the lpt port.

---

### Post by Mogurijin on 2008-04-30
What playstation controller are we talking about? 1, 2 or 3? And what is the name of this game?

---

### Post by zeththedarkmage on 2008-04-30
I guess techinically it is a basic playstation 1 controller since it can be used for both. Also the program is MDawG's ITG2PC program that can be located [here]("http://www.stepmania.naota3k.com/index.php?dir=")

---

### Post by Mogurijin on 2008-04-30
Looks like you might have issues with Wine, but you can still give it a shot. Don't know about the card/controller.

---

### Post by zeththedarkmage on 2008-04-30
Ok, thanks. I'm testing the cd integrity right now and once it is done I will check some of the things with the livecd. If I choose to fully install will I need to back up all of my important files and reformat or uninstall windows or something that will cause all of my files to dissappear, because I have no idea what exactly is going to happen. Also while running the livecd how do I check to see if the lpt card is being registered and if it is working.

---

### Post by park8b156 on 2008-04-30
Search Google for "13 things Ubuntu" follow the blog to the T it helped ma alot.  Also try searching your computer brand and # with Ubuntu after it and see if any of those pages help you.

---

### Post by Mogurijin on 2008-04-30
You don't have to kill Windows. Ubuntu (more specifically gparted) can resize partitions. However, it is still a good idea to backup your data and to defrag Windows a few times.

---

