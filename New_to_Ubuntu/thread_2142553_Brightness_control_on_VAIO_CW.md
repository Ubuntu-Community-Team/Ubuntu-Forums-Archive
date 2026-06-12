---
title: "Brightness control on VAIO CW"
date: 2013-05-06
forum: New to Ubuntu
---

### Post by yylongsony on 2013-05-06
[COLOR=#000000]Hi,Everyone, 

I just installed ubuntu13.04 on my vaio laptop and I'm new to ubuntu. I have a problem with the screen brightness. After I install the Nvidia driver (proprietary,tested) from Software&Updates, 

I can no longer adjust the screen brightness. And the brightness bar in the Brightness and Lockscreen disappeared. How can I fix it ?

Any help is much appreciated.

Thank you for your time and attention !

[/COLOR]

---

### Post by sbnwl on 2013-05-06
Try the other options also. It's quite likely that one of them, except 'nouveau' would solve the issue.

---

### Post by yylongsony on 2013-05-06
It doesn't work.And I also tried to manually install the driver downloaded from the Nvidia website. None of them worked.

---

### Post by coffeecat on 2013-05-06
Have a look at this post:

[http://ubuntuforums.org/showthread.php?t=1907928&p=11613896#post11613896](http://ubuntuforums.org/showthread.php?t=1907928&p=11613896#post11613896)

I suggest you try the first fix for now and see if it helps. This will involve editing a system file from the terminal which is not a very friendly introduction to Ubuntu - sorry about that!. To be able to edit a system file in a user-friendly GUI text editor in 13.04, you would need to install a package and adjust a setting first, so I'll show you how to do this edit in a basic terminal editor. (Note to others helping - gksu is not installed by default in 13.04. If you are going to tell the OP to "gksu gedit" you must tell them how to install gksu **and** set sudo mode.)

Press ctrl-alt-T to open a terminal. Now:

```
sudo nano -w /etc/X11/xorg.conf
```

You will be prompted for your password. You will not see it echoed to the screen as you type - that is normal. 

In the text file that opens look for the section that begins and ends:

```
Section "Device"
...
...
...
EndSection
```

There will be a few lines between Section and EndSection. Insert this line anywhere within that section as a separate line:

```

       Option "RegistryDwords" "EnableBrightnessControl=1"
```

Double-check and triple-check that you have typed it in correctly. That's a numeric one at the end of the line, not a lower-case L. Now press ctrl-O to save the edited file and then ctrl-X to exit the text editor. Reboot and see if the brightness control is now working.

---

### Post by yylongsony on 2013-05-06
Hi,coffecat.  

Thank you for your patience and your detailed guidance. I followed your steps and reboot the computer. But it still remains unsolved. 

I also referred to some posts of the others, and I found that after installing the Nvidia driver, all the contents in  /sys/class/backlight/ was gone.  It seems to have something in the folder before I install 

the driver.

---

### Post by coffeecat on 2013-05-06
The problem with Sony is that they have several different ways of handling screen brightness, but I must admit I'm vague on the details. The fix I posted - borrowed from the linked post - worked on my Vaio with the proprietary nvidia driver but it's not going to work on all Vaios with nvidia graphics. 

Have a look at the boot parameters in the link - there is a link in that describing how you test them. See if any of those help. Also, I suggest you post the exact model number of the Vaio that you are using - with luck someone on the forum has the same model. You could edit your post title to include the model number too - that might help. Edit your first post and use the advanced editor to change the title.

---

### Post by yylongsony on 2013-05-06
Well,I'll take your advice. Again, Thank you so much for your attention.

---

### Post by Lfekey2 on 2013-05-06
You can try  [https://github.com/guillaumezin/nvidiabl](https://github.com/guillaumezin/nvidiabl)

---

### Post by yylongsony on 2013-05-09
[SIZE=2][FONT=arial][COLOR=#333333]Thanks Lfekey2 for an excellent guide. I installed the nvidiabl module,  it worked perfectly for me on my VAIO CW running  ubuntu 13.04.  And the Raring Ringtail detects the FN keys.  

Now I can adjust screen brightness whenever I want , no need to endure the maximum brightness all the time. Great ![/COLOR][/FONT][/SIZE]

---

### Post by saggiyogesh on 2013-07-06
> **yylongsony said:**
> [SIZE=2][FONT=arial][COLOR=#333333]Thanks Lfekey2 for an excellent guide. I installed the nvidiabl module,  it worked perfectly for me on my VAIO CW running  ubuntu 13.04.  And the Raring Ringtail detects the FN keys.  

Now I can adjust screen brightness whenever I want , no need to endure the maximum brightness all the time. Great ![/COLOR][/FONT][/SIZE]

I am not able to control the brightness, followed the above mentioned steps: updated nvidia driver version to 310 and also installed nvidiabl-dkms_0.80_all.deb file. 
Can you pls share nvidia card number, driver version and nvidiabl version you have installed.
pls help.

---

### Post by forevertheuni2 on 2014-01-07
It's not an X problem it's gnome/ubuntu. Kde/Kubuntu works. and you can also do it with xbacklight app from the terminal

---

