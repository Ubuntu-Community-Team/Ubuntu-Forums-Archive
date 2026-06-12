---
title: "30 inch monitor with Nvidia quadro fx 4600 on 11.10"
date: 2012-04-18
forum: New to Ubuntu
---

### Post by hktrout on 2012-04-18
I have 30 inch monitor and have quadro fx 4600 graphic card in my machine. When I connect my computer to the 30 inch monitor after I installed 11.10, It just gives me pink screen in the monitor.I thought that I needed to install nvidia driver.So I installed driver with below code. But after I installed the driver and connected to my 30 inch monitor, the screen froze all the time that I couldn't even mouse my mouse.. So I had to uninstall this driver and now I am using 19 inch monitor. 

    sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
    sudo apt-get update
    sudo apt-get install nvidia-current 

Could you please help me What I need to do in order for me to use my 30 inch monitor in Ubuntu 11.10 ? 

Thanks.

---

### Post by papibe on 2012-04-19
Hi hktrout. Welcome to the forums!

Pressing Alt+Ctrl+F1 should take you to a text mode screen. Login there and run this command:
```
sudo nvidia-xconfig
```
Then restart your machine:
```
sudo reboot
```
If that gets you to a black screen again, please paste the file:
```
/var/log/Xorg.0.log
```
here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and post back the link so we can take a look.

BTW, what kind of connection are you using? DVI, HDMI? lately we've seen a lot of problems with new monitors (and TVs) connected through VGA.

Regards.

---

### Post by hktrout on 2012-04-19
> **papibe said:**
> Hi hktrout. Welcome to the forums!

Pressing Alt+Ctrl+F1 should take you to a text mode screen. Login there and run this command:
```
sudo nvidia-xconfig
```
Then restart your machine:
```
sudo reboot
```
If that gets you to a black screen again, please paste the file:
```
/var/log/Xorg.0.log
```
here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and post back the link so we can take a look.

BTW, what kind of connection are you using? DVI, HDMI? lately we've seen a lot of problems with new monitors (and TVs) connected through VGA.

Regards.

Thank you so much for you reply.

I just typed sudo nvidia x-config but it gave me " sudo: nvidia-xconfig: command not found " 

And I am using VDI cable. Thank you

---

### Post by NikTh on 2012-04-19
See if driver installed correctly. 
```
apt-cache policy nvidia-current
```Also see if an xorg.conf file exist.
```
ls /etc/X11
```

Also give the output of ```
lspci -nn| grep VGA
```

---

### Post by hktrout on 2012-04-19
> **NikTh said:**
> See if driver installed correctly. 
```
apt-cache policy nvidia-current
```Also see if an xorg.conf file exist.
```
ls /etc/X11
```

Also give the output of ```
lspci -nn| grep VGA
```

Hi,

I get this after I typed apt-cache policy nvidia-current
```
 nvidia-current:
  Installed: (none)
  Candidate: 295.40-0ubuntu1~oneiric~xup1
  Version table:
     295.40-0ubuntu1~oneiric~xup1 0
        500 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ oneiric/main amd64 Packages
        100 /var/lib/dpkg/status
     280.13-0ubuntu6.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/restricted amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ oneiric-security/restricted amd64 Packages
     280.13-0ubuntu6 0
        500 http://us.archive.ubuntu.com/ubuntu/ oneiric/restricted amd64 Packages

```

Get this after I typed ls /etc/X11

```

ls: cannot access /etc/x11: No such file or directory

```

lspci -nn |grep VGA

```
 01:00.0 VGA compatible controller [0300]: nVidia Corporation G80 [Quadro FX 4600] [10de:019e] (rev a2)
02:00.0 VGA compatible controller [0300]: nVidia Corporation G80 [Quadro FX 4600] [10de:019e] (rev a2)

```

Thanks

---

### Post by NikTh on 2012-04-19
> **hktrout said:**
> 
```
 nvidia-current:
  Installed: (none)
  Candidate: 295.40-0ubuntu1~oneiric~xup1
  
```

You have not installed your drivers correctly. Try again 
```
sudo apt-get install nvidia-current
``` if any errors occurred post here . 

Or 
another installation method 

```
jockey-gtk
```This command will open a window with additional drivers. Enable the [Recommended] one.
After the installation you must reboot for driver take place.

**Be Careful now **
I see that you have G80 chip. Read here --> [http://www.phoronix.com/scan.php?page=news_item&px=MTA4ODc](http://www.phoronix.com/scan.php?page=news_item&px=MTA4ODc) because the 295.40 driver has problems with your chip. 
Maybe it is a good idea for you to install an older driver until Nvidia fix the problem.

You can install the Nvidia driver that 11.10 version provides. I think its older than 295.40. 
Just remove the** ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu**(from Update manager --> settings --> other software) and then go to terminal and
```
sudo apt-get update 
sudo apt-get install nvidia-current
```

---

### Post by hktrout on 2012-04-19
>  This command will open a window with additional drivers. Enable the [Recommended] one.
After the installation you must reboot for driver take place.

I installed " sudo apt-get install nvidia-current " 
I don't get a window with additional drivers.. 

What shall I do ? Thank you.

---

### Post by papibe on 2012-04-19
Now restart your machine and try again the steps of post.#2.

Regards.

---

### Post by hktrout on 2012-04-19
> Just remove the** ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu**(from Update manager --> settings --> other software) and then go to terminal and


Hi,

I have two choices to remove, the one with source code and the one without.. Which one do I need to uncheck mark  ? please refer to the picture.. Thanks.

---

### Post by NikTh on 2012-04-19
> **hktrout said:**
> Hi,

I have two choices to remove, the one with source code and the one without.. Which one do I need to uncheck mark  ? please refer to the picture.. Thanks.

Both.

---

### Post by hktrout on 2012-04-19
1) I installed sudo apt-get install nvidia-current
2) removed the ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu
3) restarted machine

now,My computer freezes that i cannot even type.
could you tell me what to do? thanks

---

### Post by NikTh on 2012-04-19
> **hktrout said:**
> 1) I installed sudo apt-get install nvidia-current
2) removed the ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu
3) restarted machine

now,My computer freezes that i cannot even type.
could you tell me what to do? thanks

Wrong order . Now you probably are "victim" of Nvidia's bug that we mentioned before. 
Right order is
1)remove the ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu
2) sudo apt-get update (from terminal)
3) Install nvidia drivers
4) reboot 

Now you must remove your driver . Do as follow 
From terminal 
```
sudo apt-get purge nvidia-current
sudo reboot
``` 

When system reboots open a terminal and 
```
sudo apt-cache policy nvidia-current
``` and lets see the output once again.

---

### Post by hktrout on 2012-04-19
> **NikTh said:**
> 
Now you must remove your driver . Do as follow 
From terminal 
```
sudo apt-get purge nvidia-current
sudo reboot
``` 


Hi,after i typed above code, the screen is black now. So, I can't do next step. thanks

---

### Post by NikTh on 2012-04-19
> **hktrout said:**
> Hi,after i typed above code, the screen is black now. So, I can't do next step. thanks


Screen is black ? weird. Before you haven't nvidia drivers installed but worked.. 

Ok. 

Try the combination of Ctrl+Atl+F1 then give your username and password and then 
```
sudo apt-get update 
sudo apt-get install nvidia-current
sudo reboot
```

---

### Post by hktrout on 2012-04-19
> **NikTh said:**
> Screen is black ? weird. Before you haven't nvidia drivers installed but worked.. 

Ok. 

Try the combination of Ctrl+Atl+F1 then give your username and password and then 
```
sudo apt-get update 
sudo apt-get install nvidia-current
sudo reboot
```


Hi, i tried ctrl+atl+f1 but it doesn't change.. It still stays at black color screen.

---

### Post by NikTh on 2012-04-19
Do you have a grub menu with options ? 
Try to boot to "Recovery mode" and then "Dpkg - Repair broken packages" . Then reboot again. 

If nothing happen boot again to "recovery mode" and try "FailSafeX" option . 
When you get to the system open terminal and give the output of 
```
apt-cache policy nvidia-current
```

sorry for the mess , i didn't expect such behavior..

---

### Post by hktrout on 2012-04-19
> **NikTh said:**
> Do you have a grub menu with options ? 
Try to boot to "Recovery mode" and then "Dpkg - Repair broken packages" . Then reboot again. 

If nothing happen boot again to "recovery mode" and try "FailSafeX" option . 
When you get to the system open terminal and give the output of 
```
apt-cache policy nvidia-current
```

> sorry for the mess , i didn't expect such behavior 
That's fine. you was trying to help me.. iI really appreciate

[QUOTE]Do you have a grub menu with options ? "
Where can i find it?

How can i go to recovery mode ?

---

### Post by Ghil on 2012-04-19
when you boot, when you first see the purple color, hit shift. it will give you the grub menu. from there, you can edit the launch options by pressing "E" instead of enter on the default ubuntu entry.

now search for the linux /boot line. press END on your keyboard to go to the end of the line, and add "nomodeset" (without the "") at the end of it. Then press control + X to boot. It should resolves the black screen if I'm right.

---

### Post by NikTh on 2012-04-19
If you don't have a grub menu then enable it with shift key hold. 
When reboot hold down shift and wait for grub to show up. Then go to recovery mode.

---

### Post by hktrout on 2012-04-19
hi, somehow, i got into terminal.please tell me what to do next..

---

### Post by hktrout on 2012-04-19
Hi, I got the output after I typed apt-cache policy nvidia-current.please tell me what to do. thanks

---

### Post by NikTh on 2012-04-19
```
sudo apt-get install nvidia-current
sudo nvidia-xconfig
sudo reboot
```

---

### Post by hktrout on 2012-04-19
> **NikTh said:**
> ```
sudo apt-get install nvidia-current
sudo nvidia-xconfig
sudo reboot
```
Hi,It still freezes.. Thanks

---

### Post by NikTh on 2012-04-19
> **hktrout said:**
> Hi,It still freezes.. Thanks

Ok , but at least you have now your system work again. 
Open a terminal and lets see one more time ```
apt-cache policy nvidia-current
```

---

### Post by hktrout on 2012-04-19
> **NikTh said:**
> Ok , but at least you have now your system work again. 
Open a terminal and lets see one more time ```
apt-cache policy nvidia-current
```

Hi, I typed it ,got this.

---

### Post by hktrout on 2012-04-19
Hi,

Thank you so much for your help, NikTh. We have been struggling with this issue for more than 3 hrs now.. I am not sue if we can solve this problem... I will just re-install my computer and just go back to 19 inch monitor...  
I guess Ubuntu 11.10 cannot support nvidia..

Thank you so much.

---

### Post by NikTh on 2012-04-20
> **hktrout said:**
> Hi,

Thank you so much for your help, NikTh. We have been struggling with this issue for more than 3 hrs now.. I am not sue if we can solve this problem... I will just re-install my computer and just go back to 19 inch monitor...  
I guess Ubuntu 11.10 cannot support nvidia..

Thank you so much.

To late for me last night. Sorry. ha 

Your guess is wrong. I have ubuntu 11.10 on 37 inch monitor , nvidia gt210 (more powerless than yours i think) ,  and works perfect. Your problem its something else. 
Hardware or software ? i am not sure. 
We(you) can try again . 
Here (in this forum) exists  more experienced users than me and you. Just leave your thread open and wait . 
Bump sometimes if you see no answers it helps.
Thanks for your patience.

---

### Post by Jurjen de Vries on 2012-05-06
I also have a Nvidia quadro fx 4600, and this post helps me a lot with my current problem (100% CPU usage at Compiz and Gnome3) since last week. Did'nt know about the NVIDIA linux driver problem, after uninstall the nvidia driver my desktop have a good response.
I am adding this to this post because maybe more people have the same problem with this videocard and 100% CPU usage.
Thanks to NikTh for pointing to the NVIDIA problems.

Now I am going to search how to upgrade NVIDIA driver by shell, I found out that they release a new version 3 May with bugfix for this problem. [http://www.nvidia.com/object/linux-display-ia32-295.49-driver.html](http://www.nvidia.com/object/linux-display-ia32-295.49-driver.html)

Edit: It was a little hard to update to the latest drivers, [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual) documentation was written for Ubuntu 11.04 and lower to stop X server. I found out by Google that you can stop X server with lightdm, so added it to the documentation as well.

---

