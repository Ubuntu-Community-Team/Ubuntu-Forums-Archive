---
title: "Additional Drivers?"
date: 2012-10-04
forum: New to Ubuntu
---

### Post by BuzzStPoint on 2012-10-04
The system runs fine, 
Some online videos and Wow are fine, but can get jumpy. I was wondering if video drivers are the issue. All Runs normal and smooth Win7 so I know my hardware can handle it. 

In my additional Drivers There are 4 entires:
Nvidia Accelerated Graphics Drivers (Current, 173, Version current-updates and version 173-updates) 
The last 2 post relese.

Should I update or not?

---

### Post by NikTh on 2012-10-04
Hi , 

can you open a terminal [Ctrl]+[Alt]+[t] and give the results of these commands ? 
```
jockey-text --list
lspci -nnk | grep -iA2 vga
```Thanks

---

### Post by robtygart on 2012-10-04
> **BuzzStPoint said:**
> The system runs fine, 
Some online videos and Wow are fine, but can get jumpy. I was wondering if video drivers are the issue. All Runs normal and smooth Win7 so I know my hardware can handle it. 

In my additional Drivers There are 4 entires:
Nvidia Accelerated Graphics Drivers (Current, 173, Version current-updates and version 173-updates) 
The last 2 post relese.

Should I update or not?

You need to install nvidia-current.

---

### Post by BuzzStPoint on 2012-10-04
NikTh

```

buzz@Mobile-Horse:~$ jockey-text --list
ERROR:root:Could not find any typelib for AppIndicator3
xorg:nvidia_173 - NVIDIA accelerated graphics driver (Proprietary, Disabled, Not in use)
xorg:nvidia_173_updates - NVIDIA accelerated graphics driver (post-release updates) (Proprietary, Disabled, Not in use)
xorg:nvidia_current - NVIDIA accelerated graphics driver (Proprietary, Disabled, Not in use)
xorg:nvidia_current_updates - NVIDIA accelerated graphics driver (post-release updates) (Proprietary, Disabled, Not in use)
buzz@Mobile-Horse:~$ 

```

```

buzz@Mobile-Horse:~$ lspci -nnk | grep -iA2 vga
02:00.0 VGA compatible controller [0300]: NVIDIA Corporation C77 [GeForce 8200M G] [10de:0845] (rev a2)
        Subsystem: Hewlett-Packard Company Device [103c:360a]
        Kernel driver in use: nouveau

```

---

### Post by NikTh on 2012-10-04
Try these commands 

```
sudo apt-get install nvidia-173
``` 

```
sudo nvidia-xconfig
``` 

Reboot your PC and let me know if your problem solved. 

Thanks

---

### Post by BuzzStPoint on 2012-10-04
Kubuntu is not usable. (booted to Win7)

It boots and comes to the desktop. 
Then it's stalled/super slow, Clicking on the app launcher will take 30+ seconds, a couple of minutes to load browser then you can't do anything. 

It simply hated what I did. 

How can it be rolled back?

---

### Post by NikTh on 2012-10-04
> **BuzzStPoint said:**
> Kubuntu is not usable. (booted to Win7)

It boots and comes to the desktop. 
Then it's stalled/super slow, Clicking on the app launcher will take 30+ seconds, a couple of minutes to load browser then you can't do anything. 

It simply hated what I did. 

**How can it be rolled back?**

Of course , If you couldn't I wouldn't give the commands . 

Open a terminal (konsole) and give these commands now 

```
sudo apt-get purge nvidia-173
``````
sudo rm /etc/X11/xorg.conf
```and reboot. 

You can try another driver if you want , [s]this driver is not listed by jockey (additional drivers) . [/s] It is the driver that [robtygart]("http://ubuntuforums.org/member.php?u=58062") said . nvidia-current. 

If you want to give it a shot , then give these commands
```
sudo apt-get install nvidia-current
sudo nvidia-xconfig
```Reboot
Thanks

---

### Post by BuzzStPoint on 2012-10-04
That took a bit to remove. Heh.

Here's the last one out asked.
```

nvidia-current:
  Installed: (none)
  Candidate: 295.40-0ubuntu1.1
  Version table:
     295.40-0ubuntu1.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/restricted amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/restricted amd64 Packages
     295.40-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages

```

---

### Post by NikTh on 2012-10-05
Hi , 

I edited my post , thought you will see it . 

Yes , I know that nvidia-current exists , Of course I don't know if it will work with your hardware , but you can test it like before. 

```
sudo apt-get install nvidia-current
``````
sudo nvidia-xconfig
```reboot your PC and see if working better. 

IF NOT , you know the commands now , to remove (purge) the driver. 

Thanks

---

### Post by BuzzStPoint on 2012-10-05
Current runs better then 173, But it seems to have more jumps and lags then out of the box. 

Not sure if there are tweaks that will help the drivers.

---

### Post by robtygart on 2012-10-05
You could also try nvidia-current-updates and see if that makes any difference. Looks like your card should be supported.

---

### Post by NikTh on 2012-10-05
> **BuzzStPoint said:**
> Current runs better then 173, But it seems to have more jumps and lags then out of the box. 

Not sure if there are tweaks that will help the drivers.

I don't know for tweaks , but take a look in nvidia-settings. 

Also make sure that correct driver been loaded. 

```
lspci -nnk | grep -iA2 vga | grep use
``` 

Thanks

---

### Post by BuzzStPoint on 2012-10-05
The Lspci shows Nvidia. 

If I wanted to try the -updates. 
Do I install the updates ontop of current. Or Purge the current then install the updates.

---

### Post by NikTh on 2012-10-06
> **BuzzStPoint said:**
> The Lspci shows Nvidia. 

If I wanted to try the -updates. 
Do I install the updates ontop of current. Or Purge the current then install the updates.

My opinion is , better to purge first.

---

### Post by robtygart on 2012-10-06
> **NikTh said:**
> My opinion is , better to purge first.

+1
Thats what I do too.

---

### Post by BuzzStPoint on 2012-10-06
Well I got it all narrowed down. 
Jumpiness and choppiness has been fixed. 

I installed the nvidia-current-updates.
Then while playing around in the desktop effects:
I unchecked "enable desktop effects at startup", Improved window management, various animations. And While browsing the net I found that some people had issued with the Blur effect. So I unchecked that as well. 

A quick reboot, I tested online video and World of Warcraft, and it runs great. Real smooth. 

Thank for all your help guys.

---

