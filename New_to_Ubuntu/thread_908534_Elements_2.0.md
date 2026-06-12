---
title: "Elements 2.0"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by Cuttysark on 2008-09-02
I know it's old but I have a legal copy. I wanted to see if I could get it to install and run using Wine 1.0. The installation went without a hitch, unfortunately I can't for the life of me find it now. Any suggestions? I'm running Hardy by the way.

---

### Post by gobbles414 on 2008-09-03
In Hardy, you should be able to find it by going *Applications => Wine => Programs*. If it's not there, go *Applications => Wine => Browse C:\ Drive => Program Files*. Do either of these ideas work for you?

---

### Post by Cuttysark on 2008-09-04
I can't find anything in either of those two locations. I did browse through the various folders. I do see Notepad which I believe cam with Wine, and Gom Player which I installed a couple of days ago (and which I can open and point to a video file and shows the time count at the bottom but doesn't actually show the video, but I'm still trying to figure that one out).

I'll have another go at installing Elements over the weekend though. I actually like Gimp but I just wanted to try Wine and that disk was laying handy, but now that it's playing peekaboo with me, I don't want it to get the upper hand.

---

### Post by bubba_169 on 2008-09-04
Go to your home in nautilus, press ctrl+h to unhide all files, go to .wine/drive_c and you should be able to find the photoshop executable somewhere in 'program files'. Good luck :D

---

### Post by gobbles414 on 2008-09-04
> **Cuttysark said:**
> I can't find anything in either of those two locations. I did browse through the various folders. I do see Notepad which I believe cam with Wine, and Gom Player which I installed a couple of days ago (and which I can open and point to a video file and shows the time count at the bottom but doesn't actually show the video, but I'm still trying to figure that one out).

I'll have another go at installing Elements over the weekend though. I actually like Gimp but I just wanted to try Wine and that disk was laying handy, but now that it's playing peekaboo with me, I don't want it to get the upper hand. It seems to me like Photoshop Elements 2 didn't install correctly. Read [http://appdb.winehq.org/objectManager.php?sClass=version&iId=2415]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=2415"), then install Photoshop Elements 2 again.

---

### Post by Cuttysark on 2008-09-05
I'm pretty sure you're right when you say it may not have installed correctly. However, the nature of the problem has now changed. A digital photography course I start next month sent me, among the course work, a full free copy of Elements 6.0, so I installed that this evening, with no problems. It even placed an icon on my desktop.

The problem I have now is, when I double click to start the program, it gets as far as a screen to register with Adobe online, giving the options of Register Now, Register Later and Never Register, but regardless of which one I click, nothing happens, even choosing Never Register, it just sits like that and the only way to get rid of it is to restart.

There is a banner at the top saying it could not connect to Adobe.com and asking if I have a working connection, which I obviously have.

I'm feeling a little frustrated right now because I'm so close to having a working program.

---

### Post by gobbles414 on 2008-09-05
Cuttysark, I found a tip at [http://appdb.winehq.org/objectManager.php?sClass=version&iId=9868]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9868") that you should try. Go *Applications => Wine => Browse C:\ Drive*. Then navigate to *C:\Program Files\Adobe Photoshop Elements 6.0\*. Finally, rename the file called *adobe_registration.dll* so that it reads *adobe_registrationn.dll* (notice the extra _n_).

Does that help?

---

