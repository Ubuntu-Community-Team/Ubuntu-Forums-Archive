---
title: "nvidia driver problem"
date: 2012-11-09
forum: New to Ubuntu
---

### Post by bigal1932flying on 2012-11-09
Soon after the release of 12.10 I did a fresh install to a new ssd. I have been happy with using Quantal Quetzal but seemed to have a very slight problem which I thought may have been caused by the Nvidia Driver. I went to "Additional Drivers" and changed from 2nd. on list to the ist, as soon as I rebooted I found that I had lost my Unity Desktop.
Following some advice on the Internet (which I accessed in another OS) I tried opening a Terminal and typing:
"sudo apt-add-repository ppa:xorg-edges/ppa"
I then received a message saying that "could not make internet connection" so I tried:
"sudo apt-add-repository ppa:ubuntu-x-swat/x-updates" followed by
"sudo apt-get update"
"sudo apt-get install-current nvidia-settings"
After reboot I still had no Unity, so I tried:
"sudo apt-get purge nvidia-current nvidia-current updates nvidia-experimental-304"
"sudo apt-get install linux-source"
"sudo apt-get install linux-headers-generic"
"sudo apt-get install nvidia-current-updates"
After reboot I still do not have Unity.
Any suggestions?

---

### Post by squakie on 2012-11-09
It also makes a difference which nVidia chipset you have.  Post back the output of 

lspci | grep VGA

It may require a different driver from those listed.

When you say you have lost Unity, is it just the menu of the left, or do you mean you've lost the GUI entirely.  If you've lost the GUI, I'm sure we can do something to get it back.  If you still have the GUI, have you tried going back into additional drivers and going back to the  2nd, or even the 3rd drivers listed?  If the 1st on the list resulted in  no unity it obviously is not the driver of choice.  If you are unable to get to Additional Drivers, let us know and we can fix that as well.

---

### Post by NikTh on 2012-11-09
> **bigal1932flying said:**
> 
Any suggestions?

Hi, 

why you want the additional - restricted Nvidia driver ? Do you have any specific problem with the open source - pre-installed nouveau ? 

If you don't have any particular problem , then leave the pre-installed nouveau driver. For me it works very good with Ubuntu 12.10 .
Nouveau is not a basic driver (like Windows) , is a driver developed by Linux programmers and tested by Ubuntu developers. 

If you really have a problem with nouveau and want the additional driver , remove the X-swat repository , remove any nvidia driver and install the experimental 304 to see if works better. 

Remove repository
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:ubuntu-x-swat/x-updates
sudo apt-get update ; sudo apt-get upgrade
``` 

Un-install nvidia completely.
```
sudo apt-get remove --purge nvidia-*
sudo rm /etc/X11/xorg.conf
```


[LIST]
[*]If you want the **nouveau driver** continue like this
[/LIST]
```
sudo apt-get install nvidia-common
sudo apt-get install --reinstall xserver-xorg-video-nouveau
sudo dpkg-reconfigure xserver-xorg
echo 'nouveau' | sudo tee -a /etc/modules
```


[LIST]
[*]If you want to test the **nvidia-experimental** continue like this.
[/LIST]
```
sudo apt-get install nvidia-experimental-304
sudo nvidia-xconfig
```

In any case , after installation finish , reboot .

Thanks

---

### Post by bigal1932flying on 2012-11-10
Many thanks, that has fixed the problem.
What a relief THANKS.

---

### Post by HiImTye on 2012-11-10
it's likely because the nvidia drivers don't install the headers they need to compile. if you want nvidia accelerated graphics, then do this:
```
sudo apt-get install linux-headers-generic nvidia-current
```if you already have the nvidia drivers installed, do this instead:
```
sudo apt-get install linux-headers-generic; sudo apt-get install --reinstall nvidia-current
```then reboot, you should have working nvidia drivers

edit: I would remove the PPA you added, because it isn't necessary and it will cause you problems if you decide to upgrade instead of doing a fresh install of the next version of ubuntu

```
sudo apt-get install ppa-purge; sudo ppa-purge ppa:ubuntu-x-swat/x-updates; sudo apt-get update
```

---

### Post by NikTh on 2012-11-10
> **bigal1932flying said:**
> Many thanks, that has fixed the problem.
What a relief THANKS.

Glad you solved it. 

If you want (for future - help - others) give the results of bellow commands 

```
lspci -nnk | grep -iA2 vga
dpkg -l | grep -i nvidia
``` 

so we can see what is the graphics card and what driver you use. 

Thanks

---

