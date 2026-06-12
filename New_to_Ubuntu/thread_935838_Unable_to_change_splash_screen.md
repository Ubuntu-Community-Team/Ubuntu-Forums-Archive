---
title: "Unable to change splash screen"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by jpanoff on 2008-10-02
Dear Linux users;

I have been using linux for a month so far. It has been a very fun trip thus far...
Here is my problem: 
I can't set up my splash screen. 
Here is what I 've done:

I have downloaded GDM Themes from [gnome-look.org]("http://www.gnome-look.org") and also some splash screens from the same site.
After finish downloading them I get a tar.gz file which I drag to my login window preferences under the local tab. 
I try to select it but under no circumstances it allows me. I have also tried to install it through start-up manager under the appearance tab but no luck. 

I would appreciate your help, 
and looking forward to your replies. 
Best regards
Jpanoff

---

### Post by nothingspecial on 2008-10-02
you need to untar it. Just click on it a choose where to extract it to.

---

### Post by jpanoff on 2008-10-02
One more thing guys and girls;
I cannot change any of my login window preferences. 
For instance I wanted to set up auto login but my changes do not get saved.
I really wander what my problem is...

---

### Post by jpanoff on 2008-10-02
Dear Nothingspecial; 

Thank you very much for your reply. I did as you suggested. However; when I untar the file and dragged it to the to the login window preferences/local an error message comes up and tells me the folder is not an theme archive not a tar.gz or tar archive. 

Here is the twist though. When I drag the tar files there, I am able to install them and everything looks just fine. But when I log out and log in it tells the splash screen remains the same. 

So I've done a couple more things. I reinstall the login window from synaptics and deleted the Human splash screen that comes default with ubuntu. 

Then again I did the same procedure, changed the theme and everything looks just fine. but when I log out log in again an error message pops back before the splash screen. saying it can not locate /usr/share/gdm/theme/home/xml...

Once again thank you for your earlier reply and please let me know what you think?

Best regards
Julio

---

### Post by danking12 on 2008-10-02
Maybe you have to sudo somehow while doing these changes. I am not really sure.

What you could do is just replace the Human splash screen that you deleted earlier. Just rename the splash screen to whatever the human splash screen is called and it will open that file. Not really an ideal solution but may be a work around.

---

### Post by drs305 on 2008-10-02
> **jpanoff said:**
> One more thing guys and girls;
I cannot change any of my login window preferences. 
For instance I wanted to set up auto login but my changes do not get saved.
I really wander what my problem is...

You can use a gui app called StartUp-Manager to tweak the boot settings, including the boot splash screen, default OS, menu timeout, etc. To change grub's menu.lst options, you do need root privileges, which is why you have to enter your password when starting this app.

Install StartUp-Manager:
```
sudo apt-get install startupmanager
```

To run:
System > Admin > StartUp-Manager

The 'Appearance' tab lets you select your splash screen.

For full information, look at:
[StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

Bootloader images are usually stored in /boot/grub/splashimages/ and have extensions of .xpm.gz  You can manage them from StartUp-Manager once you have downloaded them to your computer. Splash themes have .so extensions and you will have to point to their location to install them.

---

### Post by jpanoff on 2008-10-02
Danking;
I thought that was a great idea, I did that, changed all the names as if the splash screen is called home/home.xml. But it didn't work... bummer, was worth the try though. 

Drs305; 
Did as you said. Got the startup manager. It seems that is up and running but then when I get to appearance, Usplash Theme, manage splash themes, add
I need to add an .so file
but all of the splash themese that I downloaded from gnome-look.org do not have such a file. 
What do you think would that be?

Once again thanks for your suggestions.

---

### Post by jpanoff on 2008-10-02
Hi; 
Don't think I am an as% if I take too long to reply to you guys but I will be going on a short trip ans will be back on Sunday. 
Hopefully we will be able to find a solution to this problem. 
Looking forward to reading your suggestions

---

### Post by drs305 on 2008-10-02
I am going to defer to those with experience doing what you want. I imagine you have downloaded a tar.gz file with .png images within.

Here is a link to the ubuntu wiki on usplash customizations. I have not used it and hopefully someone will post some links which they have used successfully.
[USplashCustomizationHowto]("https://help.ubuntu.com/community/USplashCustomizationHowto")

---

