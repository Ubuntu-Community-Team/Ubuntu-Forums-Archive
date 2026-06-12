---
title: "Firefox browser sluggish, crawled to a halt not letting me scroll down the page"
date: 2013-11-22
forum: New to Ubuntu
---

### Post by neil5 on 2013-11-22
I was using Firefox in Ubuntu 13.10 to do my online shopping. It was so painful. The browser crawled to a halt not letting me scroll down the page, then the rest of the system decided to just stop! I looked up the issue using Google and was advised to disable add-ons and stuff in Firefox, but it didn't really help. The whole system still stopped, greyed out occasionally....I got so fed up I used my phone to do the rest of the shopping! Surely that can't be right?!

I used System Monitor to see what was going on but nothing obvious jumped out at me. Anyone else had this problem or know why it's doing this?

---

### Post by sudodus on 2013-11-22
There could be different reasons for your problems. We need to know more about your computer to be able to give relevant advice, so please give us the specifications of your computer, at least

- Brand name and model
- CPU
- RAM (size)
- Graphics chip/card

---

### Post by jdeca57 on 2013-11-22
As you can guess the answer is that it's not normal. ;-)

Is it a new installation and is it the first time you shop on that site? 
Are there problems with other, more simple sites like this one? Did your post come from that installation with that Firefox?
Did you reboot and what gives then?

---

### Post by neil5 on 2013-11-22
Ok my laptop is a HP with an Intel Dual Core CPU, and it's about 4 years old. It has about 1GB of RAM and (i think...or it could be 2, I'll have to check) and has only Ubuntu 13.10 installed on it. I'm posting this from work on a Windows PC. My laptop came with crappy Vista installed but ran fine, performance wise. I upgraded it to Windows 7 a year or so ago and it ran fine...not the best, but good enough. This I hope gives you an idea of it's performance capability but I couldn't tell you what on-board graphics chip-set it has without looking.

To be honest, I haven't had Ubuntu installed that long and not really done much with it, but my Mrs uses it most days to surf the net (and plan our wedding) and she says it's fine, so it could be something to do with the website I guess but wouldn't have thought it should be as it's one of the biggest supermarkets in the UK!

---

### Post by ajgreeny on 2013-11-22
Some supermarket sites use a lot of flash animations on their websites which can slow a machine down quite a bit.

Try using the flash-block add-on for FF and see if it makes any difference on those sites..

---

### Post by sudodus on 2013-11-22
> **neil5 said:**
> Ok my laptop is a HP with an Intel Dual Core CPU, and it's about 4 years old. It has about 1GB of RAM and (i think...or it could be 2, I'll have to check) and has only Ubuntu 13.10 installed on it. I'm posting this from work on a Windows PC. My laptop came with crappy Vista installed but ran fine, performance wise. I upgraded it to Windows 7 a year or so ago and it ran fine...not the best, but good enough. This I hope gives you an idea of it's performance capability but I couldn't tell you what on-board graphics chip-set it has without looking.

To be honest, I haven't had Ubuntu installed that long and not really done much with it, but my Mrs uses it most days to surf the net (and plan our wedding) and she says it's fine, so it could be something to do with the website I guess but wouldn't have thought it should be as it's one of the biggest supermarkets in the UK!

If you have only 1 GB RAM, I suggest that you use Xubuntu instead of Ubuntu. Ubuntu's Unity desktop environment needs a lot of horsepower and memory to run well. With 2 GB RAM it's up to you to decide what style of desktop enviroment that you like better. If you have problems playing video (particularly high definition video), you can also try Xubuntu.

But if the system is generally slower than it used to be (that Ubuntu suddenly became slow), we need to look for another cause (maybe a bug or some problem with the file system or the hard disk drive).

---

### Post by neil5 on 2013-11-22
Might look into Xubuntu. I have gnome desktop environment installed on Ubuntu so I could have logged into that instead and tried. Never gave it a thought! 

Yeah I think there is a lot of Flash content on this particular site, but I didn't think Windows would win out over a Linux system. A little disappointed but I'm not giving up on it. 

Thanks for the replies guys.

---

### Post by philinux on 2013-11-22
Original title amended. 
@neil5 please see this. [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by coffeecat on 2013-11-22
@neil5, where were you shopping? Did you visit the Amazon site?

I've been having problems similar to what you describe with Amazon and Firefox since near the beginning of the year. The problem is intermittent and I have not yet been able to identify an add-on that might be contributing to the problem.

---

### Post by jdeca57 on 2013-11-22
> **sudodus said:**
> If you have only 1 GB RAM, I suggest that you use Xubuntu instead of Ubuntu. Ubuntu's Unity desktop environment needs a lot of horsepower and memory to run well. 

I installed Ubuntu 13.10 under Virtualbox with 1 GB Ram and 12 MB video memory. Aside from a slow dash (But then that was also a problem on real hardware) that system works fine, and I encountered no problems surfing. Of course, I didn't try the site of the OP but then again he didn't mention it.

I posted on this site with that VM.

But of course in principle I agree with what you say: if you suspect hardware issues Xubuntu is a perfect alternative.

---

### Post by neil5 on 2013-11-26
From what I have read (but haven't tried yet), Xubuntu is not that much quicker as it seems to be getting just a bulky as Ubuntu. Is this right or wrong? 

Also, I may have made a school boy error! I hadn't got Flash Player 10 installed. I visited a different website for something and it told me I needed this installed to view the page. I didn't think this was the issue as the site still worked when shopping, just very slowly.
Anyway, I should probably look at a lighter Linux distro anyway i guess.

---

### Post by sudodus on 2013-11-26
Xubuntu is definitely quicker, when the speed is limited by RAM or CPU or graphics hardware because the desktop environment needs less memory and less computing horsepower.

The size of the iso file or when installed on the hard disk drive does not tell much about the speed.

Install flashplugin-installer manually or with the whole multimedia package

```
 sudo apt-get install xubuntu-restricted-extras
```

---

### Post by neil5 on 2013-11-26
So is this a completely new install, or am I just installing another desktop environment?

EDIT: It's okay I found this [http://askubuntu.com/questions/64241/how-do-i-switch-to-xubuntu](http://askubuntu.com/questions/64241/how-do-i-switch-to-xubuntu)

---

### Post by sudodus on 2013-11-26
You can do it either way. It will be cleaner to do a fresh install of Xubuntu, but it is more convenient to upload Xubuntu Desktop or only XFCE

```
 sudo apt-get install xubuntu-desktop
```
or 
```
 sudo apt-get install xfce4
```

depending on if you want the whole Xubuntu environment with application programs etc or only the light-weight desktop.

After reboot you select desktop environment at the log in screen. Click on the round symbol near the window for password. See the attached file.

---

### Post by heir4c on 2013-11-26
There is nothing wrong with your hardware. 
I have also problems with FF and can't always scroll, even on this forum.
And there are more people with problems with FF.
Some people say deactivate Add-on this one or an other one. But that is not an option when you don't have that Add-on. 
Even a new install (or removing the .mozilla folder) help. This is just bugs in FF version 25. With version 24 there where no problems at all.
I think the only thing we can do is wait to they solved this problems.

---

