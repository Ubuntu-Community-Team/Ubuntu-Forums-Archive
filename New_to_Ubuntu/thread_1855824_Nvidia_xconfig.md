---
title: "Nvidia xconfig"
date: 2011-10-07
forum: New to Ubuntu
---

### Post by Moose62 on 2011-10-07
Just updated to natty. On first boot unity was working. Now it is not and when I go to system/admin/nvidia x server setting I get a dialog box that says
You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

Ok, how do I do this?

---

### Post by wackawacka on 2011-10-07
> **Moose62 said:**
> Just updated to natty. On first boot unity was working. Now it is not and when I go to system/admin/nvidia x server setting I get a dialog box that says
You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

Ok, how do I do this?

i had this problem.  i opened a terminal and typed this:  

sudo nvidia-xconfig

the "sudo" means you run as root

it'll ask you to type a password, then you either restartX or restart your computer, either way it'll revert to using nvidia.

---

### Post by Moose62 on 2011-10-07
I tried that and this is the message I get:

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'


And since I have no idea what that means, I'm still lost.

---

### Post by Gone fishing on 2011-10-07
Just rename the file

sudo mv /etc/X11/xorg.conf  /etc/X11/xorg.conf.backup  or you could do this graphically gksu nautilus

Then run the command wackawacka gave you

---

### Post by Moose62 on 2011-10-07
Followed the steps wackawacka gave me. On restart my resolution was too large, and could not be reduced. I removed the driver and restarted. I have normal resolution now. But can't use the unity desktop. 

I've gone through this twice with the same results. Any suggestions? I was thinking of deleting the xconfig file and starting over. But not sure how to do this.

---

### Post by Gone fishing on 2011-10-07
> On restart my resolution was too large, and could not be reduced. I removed the driver and restarted. I have normal resolution now. 

How did you try and change the resolution? Have you got nvidia-settings installed? What do you mean resolution too large the font is too big i.e resolution low or resolution too great and font too small?

---

### Post by Moose62 on 2011-10-07
Everything was too large for the screen. I tried going into the nvidia setting but it only had 2 options.  Large & larger. My normal resolution is something like 1280x800 or something like that. I didn't have this problem until upgrading to natty. I'm running a nvidia geoforce 7100 graphics card.

My current settings are1024x768 and everything looks right on the screen.

---

### Post by anewguy on 2011-10-07
While I look for other things on the net, try this:

sudo gedit /etc/X11/xorg.conf

Look for a section that says something about video device and if it says "Driver" followed by anything, change that to "Driver    "nvidia"  ".

If it doesn't list a driver at all, add:

Driver "nvidia"  in that section


Save the file.

Reboot and see if it's any better.

Dave ;)

EDIT:  As per Gone fishing's post, did you install nvidia-settings?  Go through synaptic to do so if you can, otherwise just use sudo apt-get install nvidia-settings in the command line.  When it finishes, reboot and look for it I believe in system/administration

EDIT-EDIT:  Could also be missing glx, etc., so please:

Post back attaching the /var/log/Xorg.0.log file for us to review

---

### Post by Moose62 on 2011-10-07
I followed those steps and got a blank file? There was nothing there.

---

### Post by anewguy on 2011-10-07
If it's not in /etc/X11, see if there is one in your home folder.

Also, see the edit additions on my last post.

Dave ;)

---

### Post by Gone fishing on 2011-10-07
I would be tempted to install the nvidia settings manager 

sudo apt-get install nvidia-settings

---

### Post by Moose62 on 2011-10-07
tom@tom-EX307AA-ABA-SR1907CL-NA630:~$ /var/log/Xorg.0.log
bash: /var/log/Xorg.0.log: Permission denied
 
Gee, it's my computer and it denies me permission? I'm thinking it doesnt like me. 

Not finding the file in my home folder. I have the Nvidia settings again. But I'm getting the original message

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

So I will try that again and see what happens this time.

---

### Post by Moose62 on 2011-10-07
I did that again, and on restart nvidia has my resolution at 640x480 again. This isnt working. So I am removing the driver again

---

### Post by anewguy on 2011-10-07
> **Moose62 said:**
> tom@tom-EX307AA-ABA-SR1907CL-NA630:~$ /var/log/Xorg.0.log
bash: /var/log/Xorg.0.log: Permission denied
 
Gee, it's my computer and it denies me permission? I'm thinking it doesnt like me. 

Not finding the file in my home folder. I have the Nvidia settings again. But I'm getting the original message

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

So I will try that again and see what happens this time.

Just typing in /var/log/Xorg.0.log won't do anything - it's a log file, not a command.  Just do:

less /var/log/Xorg.0.log

This will allow you to scroll up and down in the output.

Dave ;)

---

### Post by anewguy on 2011-10-07
> **Moose62 said:**
> I did that again, and on restart nvidia has my resolution at 640x480 again. This isnt working. So I am removing the driver again

I don't have a nVidia card, but isn't there some option in nvidia settings manager to Save the settings?  If you're not doing this, it would explain it resetting on reboot.  And of course I'm sure you have to have the nVidia driver installed before you can use the settings manager.

Dave ;)

---

### Post by Gone fishing on 2011-10-07
> I don't have a nVidia card, but isn't there some option in nvidia settings manager to Save the settings? If you're not doing this, it would explain it resetting on reboot. And of course I'm sure you have to have the nVidia driver installed before you can use the settings manager.

To save the settings you need to run settings manager as root so gksu nvidia-settings

---

### Post by anewguy on 2011-10-07
Thanks, Gone fishing!  Hopefully that will solve the OP's problem.

Dave ;)

---

### Post by wackawacka on 2011-10-08
> **Moose62 said:**
> I did that again, and on restart nvidia has my resolution at 640x480 again. This isnt working. So I am removing the driver again

since you're in the mood, just try this one more time in this order:

1.  delete all xorg.conf, xorg.conf.backup, whatever is there, kill it all.  

2.  reboot

3.  you'll end up in a terminal and type:  startx

4.  you should be in a fresh copy of xorg.conf

5.  goto nvidia.com, look for your video card and download the latest copy.  i have an 8400gs and i had two choices of installs, i chose the lower number assuming more stability, you may have to come back and try the next driver if you get a choice.  

6.  sudo apt-get --purge remove nvidia-settings

7.  install new driver

8.  sudo apt-get install --reinstall nvidia-settings 


the last step i said --reinstall, i'm assuming after the driver install, you have it.  if not, remove the --reinstall

i know this is extended, but i would argue that this is thorough.  if through these procedures you can't get it working, the issue is advanced and if you're not at that level yet, you might want to consider investing in a new card.  i spent a couple of bucks on new cards before i could understand how to keep the money in my pocket, or don't give up.  

gl!

---

### Post by Moose62 on 2011-10-08
I have tried to delete the xorg.conf files. Permission denied. I am seriously considering doing a clean install and starting over.

---

### Post by Moose62 on 2011-10-08
Did the clean install. On reboot it was using the Nvidia 173 driver. removed it, installed recommended driver. rebooted & everything was just groovy. Saved it to the xconfig file. So I hope we are good now.

Thanks to everyone for their help.

---

### Post by wackawacka on 2011-10-08
> **Moose62 said:**
> Did the clean install. On reboot it was using the Nvidia 173 driver. removed it, installed recommended driver. rebooted & everything was just groovy. Saved it to the xconfig file. So I hope we are good now.

Thanks to everyone for their help.

good job.  next time, you can boot into safe mode and remove 'permission denied' files that way... and if it stills give you problems, you might need to chmod 755 and do some taking over.  

take care

---

