---
title: "Can't boot into GUI on 11.10"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by cjosh on 2012-01-29
I've got an Asus UL80VT multibooting Win7 and Ubuntu 11.10, Win 7 works fine.

I was trying to get Ubuntu to register pressure sensitivity with my Wacom Intuos tablet. I did some research and apparently I had to do something with an X server which led to me to trying to update Nvidia drivers, I think. 

I'm pretty sure whatever I tried messed up and now I can't boot into GUI, I get stuck on some screen (seen in attachment). I can go into terminal but I can never reach the GUI so I'd appreciate any help.

---

### Post by cjosh on 2012-01-30
Have been trying to fix but still no luck.

---

### Post by matt2911 on 2012-01-30
> **cjosh said:**
> I've got an Asus UL80VT multibooting Win7 and Ubuntu 11.10, Win 7 works fine.

I was trying to get Ubuntu to register pressure sensitivity with my Wacom Intuos tablet. I did some research and apparently I had to do something with an X server which led to me to trying to update Nvidia drivers, I think. 

I'm pretty sure whatever I tried messed up and now I can't boot into GUI, I get stuck on some screen (seen in attachment). I can go into terminal but I can never reach the GUI so I'd appreciate any help.
This may seem simplistic but could you use your install media to reinstall your system?  I am far from a helper on this forum just so you know.

---

### Post by lolpenguin on 2012-01-31
Updating the NVIDIA drivers caused Xorg to break for me, so I restored my computer. Suggest backing up important data (it's all there, you can use duplicity being terminal-based) and reinstalling your OS, but only if you can't find another solution, though.

---

### Post by ianp5a on 2012-01-31
Or boot from a live CD to the GUI session. Then back up your data.

---

### Post by nothingspecial on 2012-01-31
It would be helpful if you could remember what you did or could provide a link to the instructions you were using.

---

### Post by grahammechanical on 2012-01-31
It is stopping Gnome Display Manager (GDM) and it is starting web server apache2. Have you converted to the server edition? Why do you have apache installed?

You will not get a GUI with GDM not working. Even then you may or may not have Ubuntu-desktop installed.

Besides which I am sure that Ubuntu 11.10 does not use GDM but LightDM. You should provide more information about your set up then just saying "11.10." It avoids giving wrong advice.

Regards.

---

### Post by cjosh on 2012-01-31
Thank you all for the replies, if it comes down to it I will have to reinstall but I'm really trying to avoid doing that.

I have a Lamp Server on my laptop which explains the Apache, I haven't got to use any of it yet so unless it does automatically I have not converted.

I'm thinking it's a video driver issue as well, seeing as that was what I was messing with before it stopped working. I can't remember the exact article I was reading though, I do know Nvidia was involved and I was trying to update my Xorg/installing wacom-tools since that was what I was trying to fix when this all started. I tried remembering some google searches and I did visit this page [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom) but that wasn't the only one.
Edit: found another page I visited [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom)

Is there any specific setup information that's needed?

---

### Post by cjosh on 2012-02-01
I had also updated from 10.04 which might be why I still have GDM. Light dm is installed as well but neither of them start. I've also removed and reinstalled nvidia-current.

I'm also getting a message "Could not write bytes broken pipe" in that same black screen.

---

