---
title: "someone installed xubuntu on my computer, can't get it off (LONG POST)"
date: 2015-06-28
forum: New to Ubuntu
---

### Post by anna10 on 2015-06-28
[CENTER][SIZE=4]**[SIZE=1][/SIZE]**[/SIZE][LEFT]i apologize in advance for any typos, i haven't used this keyboard in a loooong time and it's missing a few letter keys

[/LEFT]
[HR][/HR][SIZE=4][B][SIZE=1]

(feel free to skip to next/last section)[/SIZE][/B][U][B]
Some Background[/B][/U][/SIZE][/CENTER]

     This won't mean much to most of you but I'm gonna explain anyway so you can understand where i'm at. i'll b 20 next month, i have (social) anxiety, depression, adhd, & body dysmorphia. so, i'm a recluse. the internet has always been my escape, it takes me away from my own thoughts and helps me forget what's going on. *i think that bit is important just to put in perspective how stressed out this whole deal is making me, and why i'm so stuck on getting this old laptop to work.* we (mom and i) haven't had a working computer for about 2 years. we're gonna be homeless (hopefully in a hotel) soon and we're trying to get everything together. 

i have this laptop my grandma bought me in 2006, it originally had windows installed (idk wha version). around 2009 i was playing online when it told me to update. during update i got a little impatient and pressed a letter key, then it shut off. i turned it back on and it was a black screen with the code running down, it would stop at the end. a friend of my mom's has a son who was working with computers at the time. after a few months he had time to look at it, and he set it back up for me. apparently when i stopped the update it deleted the windows start up function which is why it wouldn't start. he put windows vista on it and it was working fine for a few months, then it asked for another update. i started updating it and went to watch TV so i knew i wouldn't mess with it. low and behold it crashed during update and was, again, ruined.
     
     in february 2012 the same friend of my mom's gave her a desktop computer he had just refurbished. the earliest files i found on it were from 2010 i think, so it wasn't new. then in april 2013 it just completely stopped working. after a lot of googling i found out that it had succumbed to the "WINDOWS 7 BLACKSCREEN OF DEATH"! i did everything i could (something in th reboot files to restart the computer to a month earlier) but it wouldn't work. found out the only way to fix it was to buy another copy of windows for over $100 which we couldn't at all afford, plus the disk drive was stuck closed. a few months later my mom randomly turned it on to see if it would work. it was perfectly normal for about 45 minutes before the whole screen of death issue.

    last year in late 2014 a co-worker of my mom's told her he wouldn't mind fixing the laptop for her (we didn't have internet at our apartment and she was having issues looking for jobs, bc she would have to drive all the way to the library). he installed this xubuntu software on it and i have no idea how to use it. she worked 3rd shift and connected the laptop with a usb cable to the modem at her job. people wouldn't come in very often so she used that time for job searches. for a while i was allowed to go and get on the laptop and i play some browser games. now we're living with a family friend and are all on a cricket phone plan so we all have some cheap android smartphones. this way mom can still job search and sell things on craigslist. 

[HR][/HR][CENTER]

[SIZE=4]_**The Current Situation**_[/SIZE]
[U][B][SIZE=4]
[/SIZE][/B][/U][/CENTER]
     so now we've got this very old laptop with xubuntu. i am trying to finish my GED which will require some online work. the website doesn't work on mobiles and definitely not on this laptop, as it needs flash and i cannot download or update anything on this computer. for other things i try to download (basically anything at all) it always says something like "can't find appropriate application for this download", and when i sometimes have the option to search online for a program, it brings up a bunch of other errors about how i don't have the appropriate software to download that either. 

     the toolbar at the bottom doesn't even work. it just has some programs locked on at the bottom right. but it doesn't show me anything i have open. the bar just stays blank. if i minimize any windows they completely disappear. i've opened task manager to try to open them back up but they're either gone or i can't find the application on the list. i can't seem to find any customization options. i can't even get a clock on the taskbar. it's just nothing is to where i can understand how to fix it.

     i told you all that background info so you at least know i am an internet addict and know the basics of using a computer. which is just... windows. what i don't understand are systems like ubuntu and anything to do with coding. i found something online about what code to enter to take off xubuntu and go back to plain ubuntu but i couldn't find the log where you put it in. i found something called "terminal emulator" but all it says in the box is "kim@Lil-Caesar:~$ " i can't backspace it. i figured it was worth a try so i pasted the code i found anyway but it came back with an error.

[HR][/HR][CENTER][SIZE=4][U][B]
Why I'm Here

[/B][/U][/SIZE][/CENTER]
we absolutely cannot afford a new computer, even a very cheap one. i want to know how to fix this one so i can at the very least do my schoolwork and get the very basic functions working. like an actual taskbar, with a clock, being able to download a browser other than chrominum, and being able to upgrade/download programs. i want to know how to get xubuntu off of this computer! i really want to get windows back but i'm not completely sure i can do that unless i have a windows disc, which i don't. i would be fine with regular ubuntu because it might be easier for me to figure out how to use.
     i am beggiiiing here for some help. if anyone is willing to tell me what to do, i will do it. i can try to get screenshots to work, i'll tell you what programs are here, all of that. here are the specs:


[LIST]
[*]it's a **compaq** computer.
[*]it's a **Presario V6000**.
[*]there is a windows sticker at the bottom that says **"Microsoft XP Media Center Edition 2005 HP"**, it includes a product key.
[/LIST]
there are a few serial codes. i have taken the battery out once if you need to know what that says... i'm not sure what else i need to provide to make it easier to know what help i need. 

i need to emphasize that i have zero idea what i'm doing. this is like an ELI5 (explain like i'm 5). i know this will probably be quite a bit of work and patience. so if there's something that i'm supposed to do you will have to break it down into simpler terms. if i just need to copy and paste some codes, i just need to know where to go. i appreciate any and all help/advice! please bare with me, i promise to give as much info as i can :) thank you!!!!


[I][B]TL;DR read last section
[/B][/I]

---

### Post by llamabr on 2015-06-28
It sounds like xubuntu is working for you, and on an old laptop, xubuntu will be better than ubuntu.  It also sounds like this laptop will be suitable for you, if you can get flash working, right?

---

### Post by jason_gibson2 on 2015-06-28
Won't be able to find any Windows XP iso files through anything legitimate, meaning whatever you might find will be both illegal and most likely loaded with garbage.

To start, find that Terminal emulator and type this in and reply with what it says. This will tell us what version you are using and we can go from there.

```
cat /etc/issue
```

If the number is either 12.04, or 14.04 you are in luck as 12.04 is supported till 2017, 14.04 is supported till 2019. Anything else is end of life and you would need to upgrade or fresh install something current. If it isn't one of those you might as well get something started downloading. Xubuntu or Lubuntu would be my first choices as they are lightweight and should run great on old hardware like that. You can get flash ability with linux easily.

[http://xubuntu.org/](http://xubuntu.org/)
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu/LTS](https://help.ubuntu.com/community/Lubuntu/GetLubuntu/LTS)

---

### Post by wildmanne39 on 2015-06-28
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.

This is to get your wifi working hopefully, and it will let us how old of xubuntu you are using.
Thank you

---

### Post by Bucky Ball on 2015-06-29
> **jason_gibson2 said:**
> 

If the number is either 12.04, or 14.04 you are in luck as 12.04 is supported till 2017, 14.04 is supported till 2019. Anything else is end of life

??? 14.10, although only supported until next month, is still alive and so is 15.04, supported until January 2016. The LTS release would be the best place to start, but please check these things before posting. Thanks. ;)

---

### Post by sudodus on 2015-06-29
Welcome to the Ubuntu Forums :-)

Looking at the specifications of your computer model via the internet, I think that ***Lubuntu*** will work better, because it has a lighter foot-print. The engine under the hood is the same, based on Ubuntu. Standard Ubuntu needs more CPU horsepower and more RAM (memory) to work well.

 In addition, the desktop environment of Lubuntu looks more like Windows, so maybe more familiar for you.

See these links and links from them to learn more about installing a new operating system.
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

[Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")

[General tips, that may help]("http://ubuntuforums.org/showthread.php?t=2130640&p=13311591#post13311591")

Maybe you can get help again from your mother's friend/coworker, who installed Xubuntu in order to get a current operating system and also some help to run it. If there is more than 512 MB RAM (I would say 1 GB RAM), then Xubuntu might be a good option, otherwise I would recommend the lighter Lubuntu. But that is only my idea. ***If your mother's friend/coworker can make Xubuntu up to date and working well (and he likes Xubuntu better), fine!*** I hope and think that he can show you how to use Xubuntu,

- where to find different tools
- how to run the tasks you want

and if something is missing, for example flashplayer, to install it for you.

---

### Post by grahammechanical on 2015-06-29
I do not read long posts.

You should know this

a) If a version of Xubuntu/Ubuntu has reached end of life we cannot update it or install any software because the sources of the updates and software called repositories are closed. They are then put in an archive which will have a different URL to the URL stored in the operating system.

b) kim@Lil-Caesar:~$

kim = user name. Lil-Caesar = name given to the computer. Both of these names were set up during installation. ~$ = the prompt. So, that is why you cannot back space any further.

b) If you remove the Xubuntu desktop you will most definitely break the operating system unless you have first installed a replacement desktop environment and user interface. Xubuntu does not have the Ubuntu desktop installed by default. So, removing Xubuntu will leave you with an installation without a desktop environment and user interface.

c) The Ubuntu desktop is not plain. It is not fancy but it does require a graphic adapter that can do hardware accelerated 3D rendering. In other words, the 3D rendering is done by the graphic adapter's Graphics Processing Unit (GPU) and not the Central Processing Unit (CPU). In the sense of needing less powerful graphic adapters then Xubuntu and Lubuntu are better than Ubuntu.

d) Xubuntu and Lubuntu are more like Windows than Ubuntu with its Unity user interface (UI) that has completely left behind what some people called the traditional user interface metaphor. It looks very different to Windows and I like it. I shudder at the thought of using XP. I never made it past Win 98!.

e) A lot of web sites require Adobe Flash Player installed. We have a Plugin that will install Flash Player. But if this plugin was not installed when Xubuntu was installed and if Xubuntu has reached end of life you will not now be able to install that plugin.

f) When we install Xubuntu/Ubuntu we tick a box called Install third party software. That will install proprietary audio and visual codecs and, if I remember correctly, it will also install the Adobe Flash Player plugin.

Oh, one more thing. A lot of normal people are not so normal as they like to think. And they have less reason for being the way they are because they are "normal." I speak as a person who choose an image of the hulk as a representation of who he was. I do not read long posts. But I do write them. :)

Regards.

---

### Post by jason_gibson2 on 2015-06-29
> **Bucky Ball said:**
> ??? 14.10, although only supported until next month, is still alive and so is 15.04, supported until January 2016. The LTS release would be the best place to start, but please check these things before posting. Thanks. ;)

Sorry, true. I don't use or suggest to anyone to use anything other than LTS so I don't keep track of those.

---

### Post by Bucky Ball on 2015-06-29
> **jason_gibson2 said:**
> Sorry, true. I don't use or suggest to anyone to use anything other than LTS so I don't keep track of those.

All good. LTS person myself. :)

---

### Post by anna10 on 2015-07-01
Thank you everyone, I appreciate all the responses. I'd like to respond individuality but I'm on my phone. I posted the thread on the laptop but since then it's messed up again. 

After I posted the OP a message notified me that I was using an outdated version of ubuntu and offered an update. I figured updating would help make things easier, especially since I'm gonna be trying to mess with the versions I had installed. Over halfway through the update it shut off.

Found out it was because of the charger. It's a cheap one we bought a few years back when the original stopped working. It's falling apart now too- got a couple of tears in the wires. I taped it up real good today and took a while to arrange the cord in such a way it would start working. The computer won't run without being plugged in!

Aaaaanyway, of course with my luck it shut off during an update and now the files are all jacked up. On startup it shows me the different recovery options. Like which version to boot from and if I want it to boot normally. The first few versions didn't work but one of them did. When I restart it gives me error screens and I have to use the boot menu thing again.

On top of that, the laptop has a Wi-Fi switch which decided to stop working. So I can't get Wi-Fi to work. If I do anything I will have to type it out and see what happens. I'll post some pics in a minute do you can see.


EDIT: just saying my mom has since quit that job and doesn't talk to the guy who installed the software. He's a little off... So we won't be talking to him anymore

---

### Post by flocculant on 2015-07-02
Hopefully the machine shutdown after it had downloaded the updates, you can complete the update installations from recovery mode.

Reboot - at grub choose Advanced, then choose the newest kernel recovery mode.

That will boot to a small menu, choose Root Terminal

Before you do anything you have to mount as read/write

Use these commands to do that and then to finish updating the upgrades

apt-get
```
mount -o remount,rw /
```

```
apt-get install -f
```

Once it's finished and completed without error, exit and you'll be back at the menu - you can continue the boot from there

---

