---
title: "Screen Resolution"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by Steve Lyne on 2008-05-22
I am an absolute beginner with Ubuntu, I do have quite a good understanding of Windows.
I have installed Ubuntu but I am unable to adjust the screen resolution above 640x480. I have searched through the postings and have seen reference to various solutions, however the advice given does not make sense to me (excuse my ignorance).
The advice to run commands from the terminal in most cases doesn't work, presumably because I am doing something wrong.
I need some real basic info to adjust the resolution.
I have an MSI motherboard and an Nvidia GeForce Fx 5200 graphics card. Both of these work perfectly with Windows. The Ubuntu install was on a new hard disc with nothing else on it.
Thanks in anticipation, Steve

---

### Post by cdtech on 2008-05-22
See this post...

[[COLOR="DarkRed"]Screen resolution[/COLOR]]("http://ubuntuforums.org/showthread.php?t=83973")

Hope this helps.....

---

### Post by Steve Lyne on 2008-05-23
> **cdtech said:**
> See this post...

[[COLOR="DarkRed"]Screen resolution[/COLOR]]("http://ubuntuforums.org/showthread.php?t=83973")

Hope this helps.....

Thanks for your help, unfortunately nothing I try works.I must admit that I am still struggling with the advice given and in particular the way the information is presented. I'm sure that all the info is given with the best intentions but reqesting that I go to monitor mode or some other strange command means very little to me. I am not a complete novice when it comes to programming but being a complete novice with Ubuntu means that I require very basic info. I have now been trying to adjust my screen resolution for nearly 4 days and I think the time has come to go back to windows. Once again thanks to everyone who has tried to help but I know when to admit defeat.
Steve

---

### Post by iaculallad on 2008-05-23
What about doing this one:

-Create a backup of your xorg.conf file first
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

-Edit the file
sudo gedit /etc/X11/xorg.conf

- And try to copy and paste the line of words which does not contain any asterisk to your "Monitor" and "Screen" section.

*Section "Monitor"
*        Identifier      "Configured Monitor"
        HorizSync 30-110
        VertRefresh 50-160
*EndSection

*Section "Screen"
*        Identifier      "Default Screen"
*        Monitor         "Configured Monitor"
*        Device          "Configured Video Device"
        DefaultDepth 24
                SubSection "Display"
                Depth 24
                Modes "1280x1024"
        EndSubSection
*EndSection

---

### Post by Steve Lyne on 2008-05-23
Since I input the various suggestions I am unable to load Ubuntu.
My system works ok with Windows but will not load Ubuntu.
I think there must be some corruption on the hard drive.
It looks like it's goodbye to Ubunto and all the peculiar names.
Thanks anyway,
Steve Lyne

---

