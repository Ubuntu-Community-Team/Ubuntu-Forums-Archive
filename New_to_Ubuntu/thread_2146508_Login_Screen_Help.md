---
title: "Login Screen Help"
date: 2013-05-18
forum: New to Ubuntu
---

### Post by BigZ1981 on 2013-05-18
Okay, so I installed kubuntu 13.04 and customized everything.  The only problem I'm having is changing my login screen background.  Apparently kubuntu uses LightDM, and being a newbie, I don't know how that makes a difference.  Anyway, I'm stuck with a white background on my login after changing it in System Settings.  Any tips on how to resolve this?

---

### Post by rburkartjo on 2013-05-18
big try this do a google search for ubuntu tweak. look for a .deb install and install the program. then open the app and navigate to tweaks/login settings then click the unlock button on the top and set your wallpaper. good luc

---

### Post by El Tito on 2013-05-18
System->System Administration->Login Screen.Uncheck the "use themed greeter" option in the general tab, and then under the background tab, choose your login wallpaper.Hope this helps!!

---

### Post by ehsanoo on 2013-05-18
Here is a solution:
[http://askubuntu.com/questions/154430/kubuntu-12-04-change-login-screen-background](http://askubuntu.com/questions/154430/kubuntu-12-04-change-login-screen-background)

---

### Post by Bucky Ball on 2013-05-18
Grub Customizer:

[http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183)

---

### Post by BigZ1981 on 2013-05-20
> **rburkartjo said:**
> big try this do a google search for ubuntu tweak. look for a .deb install and install the program. then open the app and navigate to tweaks/login settings then click the unlock button on the top and set your wallpaper. good luc

This did nothing for me.  Still on a white background.

> **El Tito said:**
> System->System Administration->Login Screen.Uncheck the "use themed greeter" option in the general tab, and then under the background tab, choose your login wallpaper.Hope this helps!!

I don't have that option.  Is this for LightDM in kubuntu 13.04?

> **ehsanoo said:**
> Here is a solution:
[http://askubuntu.com/questions/154430/kubuntu-12-04-change-login-screen-background](http://askubuntu.com/questions/154430/kubuntu-12-04-change-login-screen-background)

Apparently kubuntu 13.04 uses LightDM for it's login screen manager.  These directions don't work for me.

> **Bucky Ball said:**
> Grub Customizer:

[http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183)

This one's a little over my head...I don't know enough about linux to know how to navigate through this program.

---

### Post by BigZ1981 on 2013-05-20
Bump.  Any other help would be appreciated.  Thanks in advance!  :)

---

### Post by Bucky Ball on 2013-05-21
> **BigZ1981 said:**
> This one's a little over my head...I don't know enough about linux to know how to navigate through this program.

? Open a terminal and paste in these lines one at a time:

```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer
```

Go to System and you'll find it there. Launch it, click the 'Appearance settings' tab. Set it up how you want; images, colours, whatever. Done.

---

### Post by BigZ1981 on 2013-05-25
> **Bucky Ball said:**
> ? Open a terminal and paste in these lines one at a time:

```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer
```

Go to System and you'll find it there. Launch it, click the 'Appearance settings' tab. Set it up how you want; images, colours, whatever. Done.

Ok.  I'll have to check this out when I get a chance.  I dropped windows & reinstalled kubuntu on the merged partitions. :)

---

