---
title: "Installed Ubuntu 13.04 x64"
date: 2014-01-15
forum: New to Ubuntu
---

### Post by punkboy22 on 2014-01-15
Hello everyone i have been dabbling with Ubuntu for a few years now but just recently got into it real deep.... i installed it through VMware 5.0.2  and noticed i have no GUI which i am cool with i can get into that but i have the issue where i can't seem to find the shutdown button? searched it and googled it all i could find was that 13.10 takes it away but im not there yet... any ideas?

---

### Post by grahammechanical on 2014-01-15
Try this. Ctrl+Alt+T. does that get you a terminal (command line interface)? If it does then run either of these commands.

```
sudo shutdown -r now
sudo shutdown -h now
```

You will be asked to enter your password.

The first command restarts and the second command halts (or shuts down the OS). At least you will be able to shut down while you work out what you need to do. I suggest that you restart and at the Grub menu select Advanced options for Ubuntu and then select recovery mode. At the Recovery menu select Resume. That may get you to a working desktop with a fallback video mode. From there go to System Settings (power/cog menu) and select Software and Updates and open the Additional Drivers tab and then experiment with a different video driver.

Regards

---

### Post by punkboy22 on 2014-01-15
i will have to try those commands.. i know i was using sudo shutdown -s -t 1 i think i for some reason just drew a blank but when i do it says your system will shut down in 1 minute..  rolls through some stuff and says hit any key to resume shutdown do that put in my password and back to square one

---

### Post by punkboy22 on 2014-01-16
Ok now im confused i went and turned on my Ubuntu VM and got hit with it being Xubuntu?????:confused:  any ideas? But those commands worked for me thanks.

---

### Post by monkeybrain20122 on 2014-01-16
BTw Ubuntu13.04's support ends in two weeks.

---

### Post by punkboy22 on 2014-01-16
yeah thats fine i'll go and get the new one right now just playing with it.

---

### Post by punkboy22 on 2014-01-17
Thanks for all the help grahammechanical 	 found out my Ubuntu died during my update and for some reason changed it to Xubuntu killed the system and re-did the VM and now all is good. thanks.

---

