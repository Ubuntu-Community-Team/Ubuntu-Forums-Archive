---
title: "booting first time problem"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by agentslander on 2008-08-20
After dealing with a bunch of busy box errors, I finally got ubuntu to install without any sort of error on my computer. But, afterwards, when it restarted itself to boot up for the first time, I only get the busy cursor and no log in prompt. Does this mean I have to install it completely again? Or does it just take some time the first boot?

---

### Post by agentslander on 2008-08-20
All right, so I reinstalled twice with the same result:

Now, I'm getting a GRUB error 15 message.
Before I restarted, I was getting a pop up saying that the GNOME Setting Dameon wasn't responding.

---

### Post by Bliepo32 on 2008-08-20
You could try to boot in recovery mode to see if that works.

---

### Post by agentslander on 2008-08-20
I'd tried that with no luck, which is why I reinstalled. 

It seems that it stops installing at 79% (creating user), then unlike it did the first time it installed, it doesn't tell me anything about it being finished installing and restarting, it just starts up and gives me that GNOME error, followed by manually restarting and getting the GRUB error.

---

### Post by Bliepo32 on 2008-08-20
You could try to use SuperGrub. Just Google for it.

---

### Post by OldGrey on 2008-08-20
It reads like ubuntu did not install properly on either occasion. That could be a problem with the CD. It might be worth burning a new one, or checking the one you have for errors.

---

### Post by Bliepo32 on 2008-08-20
And try the alternate installation cd. It might solve the problem, and gives you more control.

---

### Post by agentslander on 2008-08-20
All right so I used supergrub to try and fix it and it said it was unsuccessful because of GRUB error 15. It had me reboot, still getting the GRUB error 15.

---

### Post by tarps87 on 2008-08-20
I believe error 15 means file not found, this would mean it probably can't find your kernel. Try making a new cd, I suggest using the alternative cd as it tends to work on more systems.

---

### Post by falcon61102 on 2008-08-20
Can you boot from the LiveCD?

Open up a terminal, run and post the results of:
```
sudo fdisk -l
```
-l being a lowercase L

Also, the contents of you menu.lst would be helpful too.  That can be found in the /boot folder on your internal HD.

---

### Post by agentslander on 2008-08-20
> **falcon61102 said:**
> Can you boot from the LiveCD?

Open up a terminal, run and post the results of:
```
sudo fdisk -l
```
-l being a lowercase L

Also, the contents of you menu.lst would be helpful too.  That can be found in the /boot folder on your internal HD.

I'm too new to this, so I don't know how to get to the /boot folder, or what a terminal is, unfortunately. I'm still learning.

I ran a scan on the disk and there were no errors found, so I tried another install and it got further this time to 95%, but now I'm back to the GRUB Error again. 

I'm downloading and burning another copy of the alternative version. Last time I tried it, I was still getting busybox errors, but I haven't gotten one of those in a few hours.

As for running it off liveCD, that's what it seems to do after it finishes "installing" and it works perfectly, but when I restart it, that's when the GRUB error comes up.

---

### Post by tarps87 on 2008-08-20
The terminal is in aplications -> asseccories -> terminal, if you type:```

sudo fdisk -l
```
highlight the output, copy and paste it here. You will need to use right click to copy the text.

also type:```

gedit /boot/grub/menu.lst 
```
or```

gedit grub/boot/menu.lst 
```
(it should be the firs one but if you get a blank file try the second one)
and copy and past the text to here please.

The liveCD run Ubuntu from the cd an install will run Ubuntu from the hard drive

---

### Post by MarkieB on 2008-08-20
no longer participating in ubuntuforums.org

---

### Post by falcon61102 on 2008-08-20
Ok, have you been able to get through an install successfully yet?  

I think that is the first thing we need to worry about.  If you haven't successfully installed yet then you can ignore the GRUB Error 15 because that simply is meaning that the system can't find the startup files which are the last files to be installed before the setup completes.

---

