---
title: "LiveCD question"
date: 2013-01-09
forum: New to Ubuntu
---

### Post by nu2this2 on 2013-01-09
High folks,
Have downloaded the iso file for 12.04.1, checked the md5sum,burned a CD, started ubuntu from the LiveCD and here is where the troubles begin.

1. The load time takes approx 5min befor the desktop appears.
2. Takes another 2min befor the icons on the left to appear.
3. The mouse is very jerky.
4. There is no internet connection.

Is this normal when using a LiveCd?
I'm sitting in front of the screen at the moment wondering how to check check this out but really don't have a clue as to what to do next.

Any suggestions?

Thanks.

---

### Post by Impavidus on 2013-01-09
1 & 2: Booting from a live cd is slow. A total of seven minutes sound quite long to me, but, depending on your machine, it doesn't neccesarily indicate a problem.
3: There may be a problem with the drivers of your graphics card. This is a common issue. What make and model of craphics card do you have?
4: Are you trying to use a wireless connection? Wireless doesn't always work because of driver issues. This is probably the second most common problem when installing Ubuntu. Using a wired connection usually works.

Both driver problems can probably be solved. You can ask the dash (click the ubuntu logo in the upper left) for additional drivers. I think. I'm sorry, I don't use the unity interface myself. You'll need an internet connection to download and install the drivers, so it's best to get a wired connection working.

---

### Post by nu2this2 on 2013-01-09
> **Impavidus said:**
> 1 & 2: Booting from a live cd is slow. A total of seven minutes sound quite long to me, but, depending on your machine, it doesn't neccesarily indicate a problem.
3: There may be a problem with the drivers of your graphics card. This is a common issue. What make and model of craphics card do you have?
4: Are you trying to use a wireless connection? Wireless doesn't always work because of driver issues. This is probably the second most common problem when installing Ubuntu. Using a wired connection usually works.

Both driver problems can probably be solved. You can ask the dash (click the ubuntu logo in the upper left) for additional drivers. I think. I'm sorry, I don't use the unity interface myself. You'll need an internet connection to download and install the drivers, so it's best to get a wired connection working.

Thanks for the suggestion. I'm not sure what graphic card is installed, I will check though. The computer is a 10 year old Gateway Laptop. Would the fact that 12.04-1 DESKTOP mean that it won't work on a laptop?

---

### Post by ibjsb4 on 2013-01-09
> **nu2this2 said:**
> Thanks for the suggestion. I'm not sure what graphic card is installed, I will check though. The computer is a 10 year old Gateway Laptop. Would the fact that 12.04-1 DESKTOP mean that it won't work on a laptop?

```
sudo lshw -C display
```

```
sudo lshw -C display | grep driver
```

---

### Post by Impavidus on 2013-01-09
There's a choice between desktop and server, desktop edition is fine for laptops.

As your laptop is ten years old, I think the hardware is simply not up to the task. Try running one of the lighter versions of ubuntu (xubuntu, lubuntu).

---

### Post by BlinkinCat on 2013-01-09
Hi,

Copy/paste and run the following command into a terminal

```
/usr/lib/nux/unity_support_test -p
```this will show if your machine is capable of running Unity well.

Results should all indicate "yes"

Good luck - :p

I run Xubuntu 12.04 and think it is great.

---

### Post by grahammechanical on 2013-01-09
How much RAM does the machine have? The live session loads into RAM. That will make a difference to how fast the OS seems to work. Or not in your case.

Did you try to set up a wireless connection to your wireless router? It is not done automatically until we have first set up the connection.

Here is something to try.

1) At the first purple screen press Enter.
2) At the language selection screen press Enter to select English as the default. Or select your language.
3) Press F6 and scroll down to nomodeset and press Enter.
4) Press Esc to get back to the Try or Install screen and select Try Ubuntu.

See, if that makes a difference. Ubuntu will load without setting a video mode. We can install drivers (video and wireless) in a live session (Additional Drivers utility). And also set up a wireless connection. But the settings and drivers will be lost when we end the live session.

Regards.

---

### Post by nu2this2 on 2013-01-09
Thanks all, let me try some of the suggestions and I'll log back on.):P

---

### Post by TenPlus1 on 2013-01-09
Also check what speed your CD/DVD Player is, being that old a computer would mean a very slow device also...

---

### Post by drawkcab on 2013-01-09
If you have a 10 yr old Gateway I highly suggest installing lubuntu.  Xubuntu might be pushing it honestly.

I was just fussing around with my friend's computer from that era last night and even the top-of-the-line laptops from that era don't have enough snort to run unity in 2d mode.  

Precise Puppy might be an option!

Your wifi card might be a problem, but there are always solutions.  The first thing is to settle on the distribution appropriate for your hardware.  I highly doubt ubuntu will ever run smoothly on your Gateway.

---

### Post by nu2this2 on 2013-01-10
Hello again,

Well I was able to burn a LiveCd of 10.04 3LTS and it seems to have loaded on my old Gateway laptop. Now I need to understand how it works.

I can see Applications, Places, System, Firefox icon, and ? icon in the upper left corner. I would like to open the word processing function but can't see where to click. Is there a tutorial anywhere for this version?

Thanks

---

### Post by iMac71 on 2013-01-10
> **nu2this2 said:**
> Hello again,

Well I was able to burn a LiveCd of 10.04 3LTS and it seems to have loaded on my old Gateway laptop. Now I need to understand how it works.

I can see Applications, Places, System, Firefox icon, and ? icon in the upper left corner. I would like to open the word processing function but can't see where to click. Is there a tutorial anywhere for this version?

Thanksyou might give a look to the following tutorial:
[http://www.howtoforge.com/the-perfect-desktop-ubuntu-10.04-lucid-lynx](http://www.howtoforge.com/the-perfect-desktop-ubuntu-10.04-lucid-lynx)

---

### Post by nu2this2 on 2013-01-10
> **iMac71 said:**
> you might give a look to the following tutorial:
[http://www.howtoforge.com/the-perfect-desktop-ubuntu-10.04-lucid-lynx](http://www.howtoforge.com/the-perfect-desktop-ubuntu-10.04-lucid-lynx)

Thank you,

Browsed the tutorial and It looks as though this is for someone who is actually installing on the hard drive. At this moment I am only trying "Ubuntu". Is there no word processing function on the LiveCd?

---

### Post by Impavidus on 2013-01-10
Click applications->office->(libre/open)office writer or something like that. I don't know exactly what was included in the 10.04 live disk. A simple text editor should be present at applications->tools->gedit. Shouldn't be too hard.

---

