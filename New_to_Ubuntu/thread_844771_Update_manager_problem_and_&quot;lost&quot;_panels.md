---
title: "Update manager problem and &quot;lost&quot; panels"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by troutusa on 2008-06-29
I've installed Xubuntu onto a 266MHz P3 Dell latitude laptop with just 64Mb memory and a 2G HD. (I previously used Windows XP Pro which ran very VERY slow. Hence my interest in Linux/Xubuntu.)

I've been unable to use the Update Manager. It loads, shows there are 125 (or more) updates available. All updates are pre-checked and I click on "Install". Everything appears to be working, but even after leaving the computer run for several days, then having to reboot because the Update Manager won't respond, when I start the Update Manager again the same updates are still needed.

I found a post describing how to install updates using a terminal window. I ran those commands and I believe sucessfully installed quite a few updates. (I've run the Update Manager since and noticed the updates are different.) Further attempts to use the Update Manager have failed in the same manner as before.

Any comments on what the problem and solution might be would be greatly appreciated.

Missing Panels: The first few times I booted up Xubuntu I had both top and bottom panels. Either during one of the update sessions or while going through the settings I've managed to "lose" both panels. If I open up the Settings application, and try to click on the "Panels" button, the computer indicates it is trying to read from the hard drive (loading a program) but nothing ever happens. 

How can I get these panels back?

Any help will be greatly appreciated.

---

### Post by tjwoosta on 2008-07-02
to update try finishing the updates from the terminal first then restart

do 
```
sudo apt-get update
```
then when thats finished do
```
sudo apt-get upgrade
```
when thats finished restart
after restarting do the process over 
(some updates i think dont show up untill you have prerequisite updates installed)

after all updated and restarted the update manager should work again (hopefully)

(by the way the updade manager should have all the same updates that the terminal has, the update manager is simply a front end for the same thing)

---

### Post by troutusa on 2008-07-03
> **tjwoosta said:**
> to update try finishing the updates from the terminal first then restart

do 
```
sudo apt-get update
```
then when thats finished do
```
sudo apt-get upgrade
```
when thats finished restart
after restarting do the process over 
(some updates i think dont show up untill you have prerequisite updates installed)

after all updated and restarted the update manager should work again (hopefully)

(by the way the updade manager should have all the same updates that the terminal has, the update manager is simply a front end for the same thing)
THanks for your comments. I found similar suggestions in other threads and was able to get the updates. I'm still trying to solve the missing panels. I found commands for restoring the panels through a terminal.

Is there a way to boot to the terminal so that programs can be started manually? I want to use the xfce programs without loading the desktop GUI. My computer only has 64Mb of RAM.

---

