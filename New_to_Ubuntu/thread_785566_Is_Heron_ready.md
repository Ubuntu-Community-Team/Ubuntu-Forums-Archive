---
title: "Is Heron ready??"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by Roasted on 2008-05-07
I just installed it, and for some reason compiz refuses to work and k3b locks up my system hardcore whenever I use it. I'm having a ton of weird issues and plan to boot back to Gutsy for a few more weeks.

Do you folks think Heron is pretty well rounded, or is it a wise choice to chill with Gutsy for a bit longer?

---

### Post by philinux on 2008-05-07
Please post your specs.

It's running fine here.

---

### Post by Roasted on 2008-05-07
3000+ AMD 1.8ghz
2gb 400mhz RAM
Nvidia GeForce 6600 256mb PCIEx16
420w PSU
MSI K8N Neo4 Platinum 1000mhz FSB
3 hard drives
250gb 16mb SATA
250gb 16mb SATA
200gb mb IDE

I had zero problems on Gutsy. Zero. That's why I'm questioning if  Hardy is still getting kinks worked out that could be related to my issues.

Reinstalling Gutsy as we speak. :guitar:

---

### Post by bumanie on 2008-05-07
I've found hardy much less troublesome than gutsy. But if that is not the case with you, you could stay with gutsy. Could always try a fresh install just in case something minor didn't quite install properly.

---

### Post by Roasted on 2008-05-07
The problems I'm having are just stupid stuff. For example, once I install compiz, I have 2 issues. For one, "window move" is enabled. And I can't use anything in any of the open windows. However, I can move them. It's like window move is permanently attached, so it's constantly thinking I'm ready to move a window, so it blocks out my ability to click on anything within the window. If I disable window move, I get my controls and usability back. However, I can't move the window then! Even if I click and hold on the top bar, I can't move it.

Very idiotic and very frustrating.

Also, this issue with k3b is insane. Anything I do in k3b requires 5 minutes to respond. Yes, I reinstalled it.

ALSO - flash. When I play a video in youtube, it'll play with no sound for 2-3 seconds, then abruptly stop. 

Meh.

It's just looking like a not-so-smart option right now for me. I need my usability back so I can get work done.

Gutsy is 83% done. I'll give Hardy a try in another month or so.

---

### Post by Roasted on 2008-05-15
My problems keep getting worse and worse. This is by far the most troublesome distro I've used as of yet.

The sad thing is, my buddy and I have 100% identical computers. His install works fine. Mine doesn't. Yet we did the same steps to install.

Problems:

- Sound. It randomly stops working and requires a reboot to fix.
- Sound. In pidgin, sometimes when somebody logs in, the log on sound repeats really fast and won't shut off till I reboot.
- Compiz. It just simply doesn't work like it should. With compiz enabled, I can't move any windows. If I select the move window option, then I can move windows, but I can't click on anything inside the window. It's ridiculous.
- Rsync. Due to GVFS, I get errors when I rsync. Why? What's it do? Why is permission denied?

Gutsy was flawless for me. Absolutely flawless. I didn't expect to have any issues in Hardy. 

How can I fix these? I want to like Hardy. I do. But when I have to reboot my system 3 times a day to get sound to play, it gets ridiculous.

---

### Post by omns on 2008-05-15
If you and your friend have identical computers then it sounds like you may have a hardware problem that is causing you grief.

---

### Post by Roasted on 2008-05-15
Well, I figured out compiz. Somebody on another thread told me if I delete my hidden ./compiz folder from my home directory, it'll reset the settings. Except, when I reinstalled compiz, it didn't reset anything. The folder never re-appeared.

My laptop has hardy, so I just copied the folder and put it over to my desktop. I also went through every single menu and matched the settings up completely to my laptop. Now compiz (seems) to be working fine.

My question is, if I deleted my ./compiz folder, how COULD I get it back? If I go into synaptic and do a "complete removal" of advanced ccsm + simple ccsm, wouldn't that cause a new ./compiz folder to be created when I reinstall advanced ccsm + simple ccsm?

---

### Post by shae on 2008-05-16
If you remove ~/.compiz, you will have a new one generated.  However, it might be best to move it to a backup.

```
mv ~/.compiz ~/.compiz-bak
```

---

### Post by alienexplorers on 2008-05-16
The only problem I had in 8.04 was with video drivers, but that was a pretty easy fix once I used Envy.  Other problems were created by me so I can't blame 8.04 for these errors.  Other than than those few problems 8.04 has been terrific.

---

### Post by Roasted on 2008-05-18
> **shae said:**
> If you remove ~/.compiz, you will have a new one generated.  However, it might be best to move it to a backup.

```
mv ~/.compiz ~/.compiz-bak
```

Nope. A new one was not generated. I had to restore it myself since I'm an idiot and didn't create a backup. What I did was I copied the ./compiz folder from my laptop, which has Hardy running fine on it. I have no idea if this was a bad idea or not, considering my desktop is Nvidia and my laptop is ATI... however, it seemed fine.

Then I went through every menu and matched up my selected options with my desktop to match my laptop's. Everything was fine then. In doing this I found a messed up setting.

Only thing is, it's enraging me with my sound. Also, when my sound starts to fail, so do regular apps... such as my gnome image viewer. It just flat out doesn't work. Rebooting is great... it fixes it. But I'm not in the mood to reboot every day to keep my computer from having issues.

---

