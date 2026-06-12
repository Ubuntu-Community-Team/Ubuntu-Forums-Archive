---
title: "New to Linux and Ubuntu"
date: 2024-03-16
forum: New to Ubuntu
---

### Post by pawnofthedead on 2024-03-16
I'm new to the community and the platform, so please let me know if there's a better place I should be posting my troubleshooting questions. 

I have an issue where installing the new LTS 22.04 Ubuntu has caused my network manager to disappear. I can no longer connect to the internet at all via wired or wireless connections. How can I fix?

---

### Post by yancek on 2024-03-16
What network manager?  Did you actually install Ubuntu 22.04 or did you simply try to install it?  If it is installed, did your network manager or internet connection ever work?  You might be more specific about what you mean by your network manager disappearing.  Managing a network is done by software interacting with the hardware from your OS so your statement isn't clear.  What hardware do you have?

---

### Post by pawnofthedead on 2024-03-16
I have a 12th Gen Intel(R) Core(TM) i7-12700K 3.61 GHz processor. I was running Ubuntu 20.04, and the internet was working fine. 

The computer had prompted me about the update before, but I delayed. However I needed python 3.8 to be updated, and the Ubuntu 22.04 update seemed the easiest way to do it. I let the system prompt me for the update again, I had to work through several bugs to get there, and eventually it said the upgrade was completed and 22.04 was installed. (The desktop is now a jellyfish instead of a panther.) I went to continue my python project but I got the following error: 

fatal: unable to access 'https://github.com/.........': could not resolve host: github.com
error: subprocess-exited-with-error 

It looks like it won't allow me to actually attach the image from my local desktop ... If you could see it, the image shows the Ubuntu Settings menu. It shows a bunch of menu categories: Network, Bluetooth, Background, Appearance, Applications, Sound, Power, Printers, Region & Language, Date & Time, About. The blue line is where the one for Wi-Fi used to be, and it's just gone now. Under Network, the orange bubble is where there used to be a sub-heading for Wired Connections. That's just gone now too. I'm primarily using wired connection, but both options have disappeared. 

I apologize if this is posted in the wrong place. This problem is beyond me. I'm happy to supply any additional info, I just don't know what you might need. 

[IMG]C:\Users\Michael\Desktop\Ubuntu Error.jpg[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=293500&stc=1[/IMG]

---

### Post by yancek on 2024-03-17
When you are writing your post here in the input box, there is a paperclip icon above the box.  Use that to attach an image.

>   I had to work through several bugs to get there, 

I don't suppose you made not of what those were?  No way for anyone here to know what happened.

Did you go through the steps at the link to the ubuntu documentation to troubleshoot wireless?

[https://help.ubuntu.com/stable/ubuntu-help/net-wireless-troubleshooting-initial-check.html.en](https://help.ubuntu.com/stable/ubuntu-help/net-wireless-troubleshooting-initial-check.html.en)

What exactly were you doing when you got the error about being unable to access github?  The link below gives you some commands you can use to check for connectivity problems.

[https://hostingultraso.com/help/ubuntu/troubleshooting-ubuntu-network-connectivity](https://hostingultraso.com/help/ubuntu/troubleshooting-ubuntu-network-connectivity)

---

### Post by DuckHook on 2024-03-19
Welcome to the forums, pawnofthedead,

A standard install (or upgrade) of Jammy (22.04) does not involve github. The fact that you are getting a github message tells me that you have customized your install beyond what the upgrader is designed to deal with. It doesn't take much to make the upgrader choke. The devs cannot be expected to plan for and accommodate the nearly infinite ways that people can tinker with their computer.

I rarely run into problems upgrading because I don't depart from a default install. I use only apps in the repositories and even then, I run as few apps as possible.

I'm assuming that you are new to Ubuntu and possibly even Linux (if I assume incorrectly, please advise). If you come from the proprietary OS world, the danger is that you drag in the bad habits from that world too (I'm not trying to be obnoxious—it's a very common practice). The primary bad habit is installing third party software that you download directly from the Internet. This is not only dangerous in and of itself, but will tend to break your install in exactly the way that you have now experienced.

I'll be candid: it is unlikely that we will be able to unravel what you did to break your upgrade. By the time we reconstruct your actions and unravel your bug fixes, you would be way further ahead in both time and effort to have just reinstalled.

Since you still have a working system (but no network), my recommendation would be to backup all your data, test to make sure it can all be restored, then install a fresh new system and restore the data to a virgin system.

A 12th gen i7 is more than capable of running Jammy. If the rest of the MOBO/system is similarly current, then networking should not be a problem either.

This time, I would suggest leaving the system as close to its default state as possible. If you have customizations that need to be made or special apps that are mission&#8209;critical, consider running these inside a VM. These have the advantage of easy snapshots/restores, portability and redundancy. Doing so will also allow you to keep your base system as pristine as possible and allow future upgrades to happen with dew problems.

Note that the next LTS release (Noble&#8209;24.04) is only days away and you may wish to upgrade to that in short order, so a pristine system is desirable not only for the long term, but in the very near future.

---

### Post by mrdc76 on 2024-03-22
> **pawnofthedead said:**
> I have a 12th Gen Intel(R) Core(TM) i7-12700K 3.61 GHz processor. I was running Ubuntu 20.04, and the internet was working fine. 

The computer had prompted me about the update before, but I delayed. However I needed python 3.8 to be updated, and the Ubuntu 22.04 update seemed the easiest way to do it. 


Do not update a distribution to update Python and do not use the distribution's Python for any software development project. Install Python from pyenv ([https://realpython.com/intro-to-pyenv/](https://realpython.com/intro-to-pyenv/)) or from Anaconda.

---

