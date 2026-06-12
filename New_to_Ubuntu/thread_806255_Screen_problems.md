---
title: "Screen problems"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2008-05-24
I have recently installed Ubuntu and is running fine, but I have a few minor problems.
1.My screen "flickers" (it goes blank for a microsecond and then back to normal).It doesn't do it often but I was wondering what could be the problem.
2.I have a built in bluetooth adapter and I works only one way.I can pair my phone (N 93) with my computer, but I can't send files from the phone to the computer, only the other way around:I can send files form the computer to the phone.Any ideas?

---

### Post by markbuntu on 2008-05-24
What hardware does your computer have?
Manufacturer, model number
Processor, video driver, etc. bluetooth setup.
More information is needed,

---

### Post by Troll_the_Great on 2008-05-24
It's a laptop.Asus F3T AP 008

---

### Post by markbuntu on 2008-05-24
OK, thanks. I am not familiar with the Asus laptops but I know they have some peculiar things going on that others have figured out already. Try doing a search in the search box for Asus laptop

---

### Post by Troll_the_Great on 2008-05-27
I still couldn't figure it out what the problem is... I have a Asus laptop with Nvidia Ge Force GO 7600 video adapter.Everything else is working fine...Any ideas?

---

### Post by sayakb on 2008-05-27
Regarding the bluetooth problem:
```
sudo apt-get install obexpushd
```

Sorry, doesn't work for Hardy.. I'm looking for a solution..

---

### Post by Troll_the_Great on 2008-05-27
I installed the package and it still does not work...:(. I don't know why I can send files form computer to phone but not from phone to computer....

---

### Post by sayakb on 2008-05-27
This used to work with Gutsy.. Now I don't seem to get mine to work either. I shall look up for further solutions right away..

---

### Post by sayakb on 2008-05-27
Seems like a bug in Hardy. 
Solution: [http://ubuntuforums.org/showthread.php?t=777330](http://ubuntuforums.org/showthread.php?t=777330)

---

### Post by Troll_the_Great on 2008-05-28
No ideas yet?:(:(:(:(:(

---

### Post by Troll_the_Great on 2008-06-12
My screen still does not work properly.My video adapter is a nvidia GeForce Go 7600.Can someone pls help?

---

### Post by Troll_the_Great on 2008-06-23
Hmm.... I was hoping that the  kernel upgrades to solve the problem, but no use...My screen still flickers and my bluetooth still doesn't work... Do you think is a bug in Hardy?And if yes will it ever be fixed?I am new to linux, Hardy is my first experience.I heard that because is new it still has a few bugs.From your experience, how much time needs a distro in order to become more stable? (the most annoying thing is with the screen, I would be very happy is I could fix it).

---

### Post by phidia on 2008-06-23
> **Troll_the_Great said:**
> Hmm.... I was hoping that the  kernel upgrades to solve the problem, but no use...My screen still flickers and my bluetooth still doesn't work... Do you think is a bug in Hardy?And if yes will it ever be fixed?I am new to linux, Hardy is my first experience.I heard that because is new it still has a few bugs.From your experience, how much time needs a distro in order to become more stable? (the most annoying thing is with the screen, I would be very happy is I could fix it).

Do you have the nvidia driver enabled? Click the System>Administration top menu item and select hardware drivers, enable the nvidia driver and after it installs reboot.

---

### Post by Troll_the_Great on 2008-06-23
Yes, I have the nVidia driver enabled.Compiz works wonderfull, and the other apps to, but from time to time the screen flickers...

---

