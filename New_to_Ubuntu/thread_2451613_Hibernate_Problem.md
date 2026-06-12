---
title: "Hibernate Problem"
date: 2020-10-07
forum: New to Ubuntu
---

### Post by kirk8kurtis on 2020-10-07
Can&#8217;t hibernate, can&#8217;t suspend the system. The system has swap file and it is working. Tried many treads in search of a remedy but to no avail. My last attempt was with this [post]("https://ubuntuforums.org/showthread.php?t=2432961"). Again no success. So the result from following that last post is that when I finally ran the command 'sudo hibernate' I got the display to quickly go blank and then return to what it was beforehand. I get also 'hibernate:Warning: Tuxonice binary signature file not found' and nothing else happens. I am running Asus 1201n with Lubuntu 20.04. I have also posted this issue [here ]("https://discourse.lubuntu.me/t/lubuntu-20-04-hibernation-suspend-does-not-work/1646"). Any ideas for a remedy?
Any ideas? :-k

---

### Post by GhX6GZMB on 2020-10-07
[https://ubuntuforums.org/showthread.php?t=2432961](https://ubuntuforums.org/showthread.php?t=2432961)

Also works for Lubuntu 20.04 LTS.

---

### Post by kirk8kurtis on 2020-10-07
Can’t hibernate, can’t suspend the system. The system has swap file and it is working. Tried many treads in search of a remedy but to no avail. My last attempt was with this [post]("https://ubuntuforums.org/showthread.php?t=2432961"). Again no success. So the result from following that last post is that when I finally ran the command '**sudo hibernate**' I got the display to quickly go blank and then return to what it was beforehand. I get also '**hibernate:Warning: Tuxonice binary signature file not found**' and nothing else happens. I am running Asus 1201n with Lubuntu 20.04. I have also posted this issue [here ]("https://discourse.lubuntu.me/t/lubuntu-20-04-hibernation-suspend-does-not-work/1646"). Any ideas for a remedy?

---

### Post by kirk8kurtis on 2020-10-07
Initially I have posted my question there (where your link is pointing ) but a moderator has moved it. Anyway I tried these instructions and I get that annoying message in the end and that's it. Note: I use swap file. 
 Suggestions?

---

### Post by GhX6GZMB on 2020-10-07
My link refers to systems with a swap partition. I've never been able to get hibernate to work with a swap file, sorry.

---

### Post by lysander6662 on 2020-10-07
Try this:

[https://askubuntu.com/a/1241902/684141](https://askubuntu.com/a/1241902/684141)

Hibernate does work in Linux, but you have to do some fiddling about first dependent on your distro.

---

### Post by coffeecat on 2020-10-07
Threads merged. Please do not post duplicates about the same problem.

---

### Post by CelticWarrior on 2020-10-07
> [COLOR=#000000]Can’t hibernate, can’t suspend the system.[/COLOR]
Hibernation and suspension are very different and should NOT be confused.
Suspension is fine, works flawlessly almost everywhere provided the correct graphics drivers are installed and in use. 
Hibernation is a security risk and has other issues. It was REMOVED from the default installations of any major Linux distro Windows. That must mean something, don't you think?

> [COLOR=#000000]The system has swap file and it is working[/COLOR]
For hibernation - again, SHOULDN'T be used - a swap partition is recommended instead of the now default swapfile and it must be as large, preferably slightly larger, than RAM. 

> [COLOR=#000000]I am running Asus 1201n with Lubuntu 20.04[/COLOR]
Your netbook has NVIDIA ION graphics.Have you installed Nvidia graphics driers? If so, which version?

---

### Post by kirk8kurtis on 2020-10-08
> For hibernation - again, SHOULDN'T be used - a swap partition is recommended instead of the now default swapfile and it must be as large, preferably slightly larger, than RAM. 
 
I got 3GB of RAM and 4GB of swap space.

> Your netbook has NVIDIA ION graphics.Have you installed Nvidia graphics driers? If so, which version?
No, I haven't installed any. 

Ok. I am new to linux but I am very used to hibernation function in windows so aside from security issues, can you give me pointers on how to get the Hibernate and Suspension working? You say suspension is working however I get the same results regardless of which of the two commands I ran: '**sudo systemctl suspend**' or '**sudo systemctl** **hibernate****'**. So far the display just goes OFF but the system is still ON and the disk led is not flashing so I assume no I/O. Furthermore I cant wake it from this state. The only thing left is to hold the power button to power it off and power it on again.

---

### Post by CelticWarrior on 2020-10-08
Open Additional Drivers, install Nvidia 340.

---

### Post by GhX6GZMB on 2020-10-08
Did you even read the link I sent you in post #2?
And again: hibernate needs a swap partition.

---

