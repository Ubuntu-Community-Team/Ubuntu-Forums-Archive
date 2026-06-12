---
title: "Maybe its my drivers?"
date: 2012-04-11
forum: New to Ubuntu
---

### Post by benj23673 on 2012-04-11
After doing a fresh restart and entering these commands 

sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

to install all the packages I recently installed on my previous ubuntu, I got a license agreement from microsoft that I could not click ok to so I had to end all the processes running in the terminal then I restarted my computer now when logging on my mouse dose not work or my internet I need help.

---

### Post by daslinkard on 2012-04-12
When you say that your Internet does not work, are you meaning that you are unable to load a page or that you cannot find it?  Can you be a little more specific there please.

Also, are you able to utilize the Command Line at all?  If you're unfamiliar with the short cut it is as follows:

```
 CTRL+ALT+T 
```

Please let me know if you are able to access the terminal.

---

### Post by benj23673 on 2012-04-12
I can access the terminal and when I plugged in my laser mouse from my hp desktop (I am on a e520 thinkpad) The mouse worked and I clicked on the network symbol in the top right corner clicked enable but it would not let me select wireless or wired network I am currently using my windows partition of the think pad I am not a total n00b but I need help when it comes to more complex things

---

### Post by daslinkard on 2012-04-12
Have you tried logging into Recovery mode to see if your mouse and Internet work there?  Or what about utilizing the terminal to un-install the update?

---

### Post by oldfred on 2012-04-12
I recently reinstalled the ms-fonts and you have to use tab to move to accept button and enter to accept/continue. Its just a terminal window with no mouse support.

If forcing a shutdown remember the elephants.

Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

If you follow daslinkard's suggestion on recovery mode you may be able to clean up the partially installed packages.

If partition is not mounting then the unclean shutdown may require you to run e2fsck, but you have to do that from a liveCD, so the partition is not mounted.

---

### Post by critin on 2012-04-12
>  I got a license agreement from microsoft that I could not click ok 

The mouse won't work there.  Just use the TAB key to highlight OK (or whatever the word is)  Then enter or continue.

---

### Post by benj23673 on 2012-04-12
Oldfred you may want to consider changing your name to ubuntu god. I am in recovery mode typing this and I reinstalled all the applications everything went better than expected. Thank you all for your help you are all to kind and generous one day when I am a expert of ubuntu I will give back to the forums as well as you guys do.

---

### Post by daslinkard on 2012-04-12
I'm glad the recovery mode worked for you.  It's amazing how when you first start using Ubuntu and Linux the things you read about on the forum won't make sense, but then the day will come that you will sit down in front of your machine, fire it up, and you'll discover you know more than what you realize.  Good luck with your Ubuntu endeavor!

---

### Post by oldfred on 2012-04-12
Glad you got it working, but daslinkard deserves the credit.

I got started in forums looking for help on some issue and noticed a thread on something I had just solved myself. So I signed up and offered my suggestions. So it does not take a lot of knowledge to get started and I am still learning as I lurk in the new posts area and find out something new.

---

### Post by idoitprone on 2012-04-12
> **benj23673 said:**
> Oldfred you may want to consider changing your name to ubuntu god. I am in recovery mode typing this and I reinstalled all the applications everything went better than expected. Thank you all for your help you are all to kind and generous one day when I am a expert of ubuntu I will give back to the forums as well as you guys do.

+1 oldfred is too wise

---

