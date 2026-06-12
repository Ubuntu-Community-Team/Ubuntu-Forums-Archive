---
title: "Ubuntu 12.04 and No Display Variable Set error"
date: 2012-08-02
forum: New to Ubuntu
---

### Post by lykenstrife on 2012-08-02
I, do apologize, if this has been posted before, but I'm having an issue.. I just recently finished installing Ubuntu 12.04 on my Toshiba Qosmio x505. It has an Nvidia GTX 360m video card on it.. some how, I was able to get to the login screen and everything after the installation, but now after doing all the updates and driver downloads, I can't get back to the Log In Screen. It promptly takes me to the the terminal and asks me to login through the terminal. I did and typed in the "startx" command to boot up to the GUI, but I got this error: Fatal: Couldn't Open Display" and "No Display variable set... 

So I poked around a littled bit and tried a few commands, sudo lightdm, sudo startx, and sudo gdm.. because according to Google I should be able to remedy the problem using those commands, but it was all to no avail. I am wondering what I should do.. I know my computer meets the basic system requirement above and beyond the call of duty, but I can't seem to get this up and running.. is there any that you guys could suggest that could help me get this up and running? I would like a bit of an explanation of how it works and such, but please don't make it too complicated I'm still VERY new to Ubuntu, and only just started messing around with some of the terminal commands and such on a Netbook I had..

---

### Post by pqwoerituytrueiwoq on 2012-08-03
try installing the gpu driver
```
sudo apt-get install nvidia-current
```
run this 1st to get the latest driver
```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates;sudo apt-get update
```
if it still does not work you can try the open source driver
```
sudo apt-get purge nvidia-current
```

---

### Post by lykenstrife on 2012-08-03
when I tried sudo apt-get install nvidia-current I got Failure to match Toshiba with Lenovo..

I was also told on the support chat to try display=:'0.0&& startx' to which I got: Fatal Server Error: No Screens Found.

the sudo apt-add-repository ppa:ubuntu-x-swat/x-updates;sudo apt-get update command gave me the same error as startx Fatal: Couldn't Open Display

---

### Post by lykenstrife on 2012-08-03
bump..

---

### Post by lykenstrife on 2012-08-03
bump....

---

### Post by lykenstrife on 2012-08-03
Bump.....

---

### Post by wilix on 2013-03-25
thanks, this helped me to solve my problem.

---

### Post by alexandru-apostol on 2013-11-01
I don't get it really. My frustration level is at it's maximum right now. For a week I'm trying to install Ubuntu (first 13.10, then 12.04 LTS) and I'm not seeing the light anymore. I can make the "jerk" meme with Ubuntu in which I'll write: "Works flawlessly from USB stick during installation/ Freezes at restart due to graphics driver failure". The best i get after each installation is the text login mode... amongst crashes, errors and other stuff. So I login, type startx, watch it fail and read countless lines of forum threads... But I can't understand one thing... why can it work from a stick??? Why can't it work after installation??? Ok, there's a graphic card issue, but then it shouldn't start at installation. What's the excuse for the GUI not to load after installation?

---

### Post by vgerris on 2014-01-23
You might have this issue because another driver is loaded when booting than during installation, or a different X config.
When you get in safe mode and have a terminal you can troubleshoot the issue.
I would call it a bug, feel free to report it : [https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs) .
When installing th proprietary driver, sometimes things go wrong.
Check the forums for driver realted issues.

---

