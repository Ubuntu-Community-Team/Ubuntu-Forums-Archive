---
title: "Having problems loading Ubuntu on old laptop"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by texastrey1836 on 2008-05-30
Have an Averatec 3250 with AMD (yes it's old). I've tried all sorts of different installs to install Ubuntu on the computer with no joy. Have done installs previously on other computers and have flown right through it, but not this time.
I've tried a bunch of different ways and this time I keep coming up with a quick screen that I can't read fast enough and then some disclaimer from Ubuntu about how it's free and there's no warranty, then it tells you about how "To run a command as administrator..." I've never seen this before and don't know what to do.
Any help? There shouldn't be a problem with size of HD or RAM (60 GB, 512 RAM).
I've posted elsewhere but am a bit frustrated and putting it where it's more likely to be seen.

---

### Post by Aearenda on 2008-05-30
It sounds as though the video driver is not starting, and so you get dropped back to the comand line login.

You can use this to login with the username and password you selected during installation, and then do ```
more < /var/log/Xorg.0.log
```

This should give you some clues about what is happening.

---

### Post by overdrank on 2008-05-30
> **texastrey1836 said:**
> Have an Averatec 3250 with AMD (yes it's old). I've tried all sorts of different installs to install Ubuntu on the computer with no joy. Have done installs previously on other computers and have flown right through it, but not this time.
I've tried a bunch of different ways and this time I keep coming up with a quick screen that I can't read fast enough and then some disclaimer from Ubuntu about how it's free and there's no warranty, then it tells you about how "To run a command as administrator..." I've never seen this before and don't know what to do.
Any help? There shouldn't be a problem with size of HD or RAM (60 GB, 512 RAM).
I've posted elsewhere but am a bit frustrated and putting it where it's more likely to be seen.

HI and if you have checked the cd for errors and the MD5SUM on the iso then it maybe an issue with the drive. Can you see the start or install screen from the live cd?

---

### Post by texastrey1836 on 2008-05-30
Am currently still trying to run it but now it gets stuck on this part where it just says
starting deferred execution scheduler atd
starting periodic command scheduler crond
checking battery state
running local boot scripts 
and then doesn't do anything else. cd stops working
about to scream and wife is getting mad at me for working on this at 1.15 a.m. adhd kicking in bad.

---

### Post by Aearenda on 2008-05-30
Then go to bed - didn't you know that all computers have a built in human stress sensor that causes them to go weird when you can least cope with it?
:-D

---

### Post by lisati on 2008-05-30
> **Aearenda said:**
> Then go to bed - didn't you know that all computers have a built in human stress sensor that causes them to go weird when you can least cope with it?
:-D

:)

texastrey1836: The way I originally installed Ubuntu on my laptop (it's currently about 2 years old) was with the "alternate" install disk. It doesn't have the "live CD" portion that lets you give Ubuntu a test drive before installation, but can sometimes be helpful if other installation methods grind to a halt.

---

### Post by texastrey1836 on 2008-05-30
Hey all:
Am trying the alternate text-based installer and that's working great-- until it comes to detect disk, and then it won't recognize my hard drive. I've slept since I started working on this and it's still kicking my a**. I don't blame Ubuntu, as I've had good success with them on other machines, but no joy here on the averatec.

---

### Post by texastrey1836 on 2008-05-30
No joy: can't find the hard disk. Have trolled the threads on here and have seen some things to try, but can't get to them. I tried something else with xserver and that didn't work. About to toss the computer and yell at Ubuntu, Averatec, and Windows for putting me in this miserable place. Argh!:mad:

---

### Post by sweeneytodd on 2008-05-30
sounds to me like a bios problem, i'd try updating it and maybe changing the battery and resetting it, in the reverse order that i stated, if not i'd still put it down to the motherboard,

---

### Post by ubume2 on 2008-05-30
Hang in there.  Sounds like the initiation rite I went through when I first installed linux.

---

### Post by sweeneytodd on 2008-05-30
maybe u could share ur wisedom and enlighten us with your diagnoses then, how did u solve ur problem that sounded so similar

---

### Post by texastrey1836 on 2008-05-30
Just wondering how I update my BIOS. I sound like a royal idiot; I'm just a n00b.
Trey

---

### Post by Aearenda on 2008-05-30
Never update your BIOS unless you absolutely have to. Too many systems turn into bricks that way!

I would try booting with the all_generic_ide parameter, and if that doesn't work, irqpoll, or both together. See [http://ubuntuforums.org/showpost.php?p=4799028&postcount=15](http://ubuntuforums.org/showpost.php?p=4799028&postcount=15) for how to try it.

Or if you're booting from the CD, press F6 at the first screen after choosing the language and add the parameters 'all_generic_ide irqpoll' to the end of the line, after the '--' marker (without the quote marks, of course).

Sorry this is cryptic, I've got to go out.

---

### Post by Confused Vorlon on 2008-08-18
I have an averatec 3200 and had a similar issue with hanging installation.

I went with a rather random route. I had a 6.02lts disk kicking around and that installed fine. Then I was able to update to 8.04.

Still haven't got any network connections (though they did work on 6.02). Hopefully the good folks here will help me with that.

nonetheless - it is a step along the line!

---

### Post by banned bandit on 2008-08-19
I managed to get my display working by installing 7.10 first.  Make sure when you install 7.10 you press F4 and choose 1024X768 when your in the CD boot menu.  After your done installing, you can upgrade to 8.04LTS.  You will need a active internet connection.  I still havent been able to get my onboard WIFI card working.  I had to use an old linksys wireless B PCMCIA card.

---

