---
title: "Disable auto logout"
date: 2021-05-10
forum: New to Ubuntu
---

### Post by jegub on 2021-05-10
Hi! i have a wierd problem. i have disabled auto logut in settings>privacy>screenlock. But it seems to auto logout after a few hours. Last time i touched my computer was before i was going to bed and when i woke up (7 hours of sleep) my user was logged out... any idea? 

I am mining on the computer so its not like it ideling either....

//Jakob

Ubuntu 20.04 Desktop

---

### Post by cmcanulty on 2021-05-10
Look at power manager settings and screensaver settings

---

### Post by grahammechanical on 2021-05-10
You are disabling automatic screen lock. That is not the same as automatic logout. I am not sure if Ubuntu Desktop has automatic logout set. Maybe Ubuntu server has automatic logout set. I do not know. The instruction guides that I have just researched refer to the Bash terminal. Which would be applicable to a server installation.

A person would need to change the tmout setting in either /etc/profile or /.bash_profile. Or, some other place. On my Ubuntu desktop I cannot find any file where the tmout setting is included. Except in some snap files.

[https://www.cyberciti.biz/faq/linux-tmout-shell-autologout-variable/](https://www.cyberciti.biz/faq/linux-tmout-shell-autologout-variable/)

I do have show hidden files checked. I have looked in /etc/profile, /home/.bashrc, /home/.bash_logout, /.profile, /etc/bash.bashrc  

I am staring to suspect that the tmout command is not used in the Ubuntu desktop system environment. At least not on my Ubuntu 20.04. But it may be used in Ubuntu server.

[https://ostechnix.com/auto-logout-inactive-users-period-time-linux/](https://ostechnix.com/auto-logout-inactive-users-period-time-linux/)

Regards

---

### Post by DeadlyOats on 2021-05-16
> **grahammechanical said:**
> You are disabling automatic screen lock. That is not the same as automatic logout. I am not sure if Ubuntu Desktop has automatic logout set. Maybe Ubuntu server has automatic logout set. I do not know. The instruction guides that I have just researched refer to the Bash terminal. Which would be applicable to a server installation.

A person would need to change the tmout setting in either /etc/profile or /.bash_profile. Or, some other place. On my Ubuntu desktop I cannot find any file where the tmout setting is included. Except in some snap files.

[https://www.cyberciti.biz/faq/linux-tmout-shell-autologout-variable/](https://www.cyberciti.biz/faq/linux-tmout-shell-autologout-variable/)

I do have show hidden files checked. I have looked in /etc/profile, /home/.bashrc, /home/.bash_logout, /.profile, /etc/bash.bashrc  

I am staring to suspect that the tmout command is not used in the Ubuntu desktop system environment. At least not on my Ubuntu 20.04. But it may be used in Ubuntu server.

[https://ostechnix.com/auto-logout-inactive-users-period-time-linux/](https://ostechnix.com/auto-logout-inactive-users-period-time-linux/)

Regards

In other words, you are saying there is no way, in the settings, to disable screen lock, after waking a sleeping computer.

We can set the system to log in without inputting the password, when powering up a computer, but when waking from sleep, we'll always have to log in....

---

### Post by cmcanulty on 2021-05-16
I don't get logged out after suspend, ever.

---

### Post by DeadlyOats on 2021-05-16
> **cmcanulty said:**
> I don't get logged out after suspend, ever.

I'm using Kubuntu 20.04.  How can I set up my system so that it does not log me out after the computer goes to sleep?

---

### Post by cmcanulty on 2021-05-17
look in screensaver settings and power manager settings

---

### Post by DeadlyOats on 2021-05-17
> **jegub said:**
> Hi! i have a wierd problem. i have disabled auto logut in settings>privacy>screenlock. But it seems to auto logout after a few hours. Last time i touched my computer was before i was going to bed and when i woke up (7 hours of sleep) my user was logged out... any idea? 

I am mining on the computer so its not like it ideling either....

//Jakob

Ubuntu 20.04 Desktop

I had asked that question in my own thread, and found your thread on the same issue.  This is the answer I got.  I hope this is helpful to you.

> **vidtek said:**
> Go to System-Settings->workspace behaviour->screen locking  look at the options and understand them.   It's one of the first things I do with a new install

Cheers Tony

---

