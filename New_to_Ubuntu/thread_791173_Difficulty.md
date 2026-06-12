---
title: "Difficulty"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by donaldshelton on 2008-05-11
I installed Ubuntu thinking that I'd have fun with the open source programs.  So far, though, I have had nothing but frustrations.

I can't go back to Windows as I formatted the whole drive and can't find the rescue disks.  Oh whoa is me!!!

I downloaded the Linux version of Google Earth.  The instructions say to navigate to the location of the file then install it using the terminal.  According to the properties of the program, it is located at /home/donaldshelton/desktop/  When I type this in the terminal I am told that the file or directory doesn't exist.

Any help is appreciated.  I just might go out and get a copy of windows to reinstall, but I want to give this a try first.!

Don

---

### Post by tacutu on 2008-05-11
you have to go to that directory first:
```
cd /home/donaldshelton/desktop/
```
and then execute the binary you downloaded:
```
./Google<whatever>.bin
```

---

### Post by Monicker on 2008-05-11
Desktop should be capitalized.

```
cd /home/donaldshelton/Desktop/
```


Remember, Linux is case sensitive.

---

### Post by SunnyRabbiera on 2008-05-11
well there is a better way to get google earth, by adding the medibuntu repositories.
In linux we do things be a system of repositories as opposed to a hodgepoge of websites that may or may not contain malicious software.
First is to learn how to use the package managers in ubuntu, package managers are graphical ways to see repositories.
[use this guide here to get started]("http://monkeyblog.org/ubuntu/installing/")

after that follow instructions on this page to get the medibuntu repository working:
[here]("https://help.ubuntu.com/community/Medibuntu")

give us time and we can give you answers.

---

### Post by RequinB4 on 2008-05-11
Hi!  Welcome to ubuntu.

Kind of stinks you used the whole drive, but it seems like you're getting aquainted more than having a serious problem with the system.  Linux =/= windows, for BETTER or worse.

There are hundreds of places to go to get started.  If you're the kind of person who learns by reading over doing, here are some links that should help.

First, to solve your problems navigating the terminal, go here - [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Second, linux is not windows, some good stuff: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Third, the ubuntu beginner's guide(far from comprehensive): [https://help.ubuntu.com/community/Beginners/Guide](https://help.ubuntu.com/community/Beginners/Guide)

Fourth, as to installing software, SunnyRabbiera has posted a great guide.

---

### Post by ugm6hr on 2008-05-12
> **SunnyRabbiera said:**
> well there is a better way to get google earth, by adding the medibuntu repositories.

Indeed - here is a specifc How-To:
[http://ubuntuforums.org/showthread.php?t=787571](http://ubuntuforums.org/showthread.php?t=787571)

---

### Post by SlappyPappy on 2008-05-12
Yo Don, tell us what has you so frustrated. Lots of people here with good answers might help you feel better about what you're trying to do!  :)

---

### Post by donaldshelton on 2008-10-09
Thanks to all who have replied.

I have since gotten rid of the original machine, and have started again with a new one.

I was able to install ubuntu with vista, and now have a dual boot system  yippee!!!

Again, thanks to everyone.

---

### Post by donaldshelton on 2008-10-13
> **SlappyPappy said:**
> Yo Don, tell us what has you so frustrated. Lots of people here with good answers might help you feel better about what you're trying to do!  :)


I can't get any sound from any source on the internet.  I go to youtube, and I can't hear any sound.

When the computer boots, I hear the jingle really well.  The volume is on max, the volume on the video player in youtube is on max.  I have downloaded the ALSA mixer and the ALSA player.  I tried to get the RealPlayer, but had difficulty installing it.

I sound a lot like a complainer, but I am actually having fun trying to figure out all the bugs.

Any help is really appreciated!!!!

Don

---

