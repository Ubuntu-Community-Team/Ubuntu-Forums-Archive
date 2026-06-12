---
title: "Screen Resolution"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by daniel.j on 2008-11-27
Is there a way to increase my screen resolution beyond 800X600 to take full advantage of my monitor?

I don't like having to scroll all over the place :(

---

### Post by Kareeser on 2008-11-27
Have you installed drivers for your graphics card?

If so, and the problem persists, you may need to alter your xorg.conf file :(

We'll guide you along. Stay put. :)

---

### Post by eternalnewbee on 2008-11-27
> Is there a way to increase my screen resolution beyond 800X600 to take full advantage of my monitor?

I don't like having to scroll all over the place
> Have you installed drivers for your graphics card?

If so, and the problem persists, you may need to alter your xorg.conf file

We'll guide you along. Stay put
Also, have you tried changing your screen resolution in: **Main Menu > Administration > Preferences > Screen Resolution**?

---

### Post by Kareeser on 2008-11-27
> **eternalnewbee said:**
> Also, have you tried changing your screen resolution in: **Main Menu > Administration > Preferences > Screen Resolution**?

Ah yes, Occam's razor... forgot to ask the most obvious question :)

Thanks eternalnewbie

---

### Post by eternalnewbee on 2008-11-27
> Ah yes, Occam's razor... forgot to ask the most obvious question
Nobody's perfect: My name is Nobody:)

---

### Post by mudmakerman on 2008-11-27
In my experience with linux, it is not the graphic card as much as your monitor not being recognized.  If your monitor is not recognized, pick a generic monitor to the resolution you wish to have. Just make sur that your monitor supports the resolution you pick.

---

### Post by daniel.j on 2008-11-27
> Have you installed drivers for your graphics card?

It says, when I click on "Hardware Drivers" from the System Administration tasks that no proprietary drivers are in use but the Nvidia shows up and the box is ticked.

If I try to untick the box it states that it will not work.

I didn't install the drivers and I'm not sure how to or if it was done automatically.

---

### Post by mudmakerman on 2008-11-27
go to SYSTEM > Administation > Screen and Graphic and click "Model" to select your monitor. 

chances are your monitor is not recognized and you will have to select a generic one to the resolution you wish to have

---

### Post by daniel.j on 2008-11-27
I do not have a 'Screen and Graphic' option in Admin tab.

---

### Post by mudmakerman on 2008-11-27
I am googling trying to find a solution. What version of linux{ubuntu} are you running?

---

### Post by mudmakerman on 2008-11-27
Do you have an option that just says graphics? My graphic card has an option for 2 monitors, so maybe just graphics is listed if your card doesn't support this.

---

### Post by abrax on 2008-11-27
Hello

I had the same problem once, why don't you try this? 



```
sudo dpkg-reconfigure xserver-xorg
```



hope it helps =)

---

### Post by daniel.j on 2008-11-27
I still think it might have something to do with the drivers. It says that the nvidia driver is 'not in use' despite being "enabled."

I'm going to do a fresh install as I'm also having some additional problems.

---

