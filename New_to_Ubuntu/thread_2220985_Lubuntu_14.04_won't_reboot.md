---
title: "Lubuntu 14.04 won't reboot"
date: 2014-04-30
forum: New to Ubuntu
---

### Post by moltoscarso on 2014-04-30
recently upgraded my Lubuntu 13.10 to 14.04 

Online upgrade used  -   everything went ok except for system rebooting 

Any time systems goes down and try to reboot it stuck onto the lubuntu  green  up to the 2.nd of 3.rd dot

Checked the web and found several hints.   Tried modifying  /etc/default/grub  in several ways  always with no success though. 

Finally applied for Boot-repair tool - everything  worked fine besides the fact that system does not want to reboot yet.

got a reply screen asking me, if repair did not work, to post  URL:  [http://paste.ubuntu.com/7360893/](http://paste.ubuntu.com/7360893/)  to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] ,which I did meanwhile, or to post that URL to a ubuntu forum. 

That's what I'm doing now. :idea:


Thank you for any additional hint

---

### Post by LastDino on 2014-04-30
I'm shooting in the dark here but what GPU are you using?
Any other third party drivers?

---

### Post by kc1di on 2014-04-30
> **moltoscarso said:**
> recently upgraded my Lubuntu 13.10 to 14.04 

Online upgrade used  -   everything went ok except for system rebooting 

Any time systems goes down and try to reboot it stuck onto the lubuntu  green  up to the 2.nd of 3.rd dot

Checked the web and found several hints.   Tried modifying  /etc/default/grub  in several ways  always with no success though. 

Finally applied for Boot-repair tool - everything  worked fine besides the fact that system does not want to reboot yet.

got a reply screen asking me, if repair did not work, to post  URL:  [http://paste.ubuntu.com/7360893/](http://paste.ubuntu.com/7360893/)  to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] ,which I did meanwhile, or to post that URL to a ubuntu forum. 

That's what I'm doing now. :idea:


Thank you for any additional hint

Try this when ubuntu starts to boot hold down the left shift key.  then press f6 key from the menu select nomodeset hit esc and enter see if it will boot then, if it does you'll need to install the proper video driver for your video card.

---

### Post by moltoscarso on 2014-04-30
GPU shall look like:

67 [GeForce 7000M / nForce 610M]
          bridge      K8 [Athlon64/Opteron] HyperTransport Tec
          bridge      K8 [Athlon64/Opteron] Address Map
          bridge      K8 [Athlon64/Opteron] DRAM Controller
          bridge      K8 [Athlon64/Opteron] Miscellaneous Cont


according to the second suggestion  > left shift + F6   etc. etc.  got a quick and long list of commands followed by [ok]  like if pc was shutting down or reboot and lubuntu went up again as usual..

---

### Post by LastDino on 2014-04-30
Welp! You need to install stable drivers for your GPU in Ububtu.

For x32 linux OS this should probably work>
[http://www.nvidia.co.uk/download/driverResults.aspx/59843/en-uk](http://www.nvidia.co.uk/download/driverResults.aspx/59843/en-uk)

If you have x64 >
[http://www.nvidia.co.uk/download/driverResults.aspx/69443/en-uk](http://www.nvidia.co.uk/download/driverResults.aspx/69443/en-uk)

 if you've already done this and problem is still persisting, ignore me >_>

---

### Post by kc1di on 2014-04-30
if you can get to a terminal install the nvidia-304 driver.

Terminal command would look like this ```
 sudo apt-get install nvidia-304
```

---

### Post by moltoscarso on 2014-04-30
if I check in the Nvidia X Server settings I can see that the nvidia 304.117 is loaded on my laptop.  operating system:Linux-x86

---

### Post by LastDino on 2014-04-30
Yeah, but you did upgrade and I've faced similar issue with one of my clients PC who had Nvidia drivers, it is usually good practice to uninstall them before upgrade as they are 3rd party and may cause imbalance, especially since this upgrade came with upgraded kernels. Worth a shot IMO

---

### Post by moltoscarso on 2014-05-01
Are you meaning > sudo apt-get purge nvidia*
sudo apt-get install nvidia-current
sudo reboot? 

Downloded drivers from the link you posted previously though but, since I`m not that good with terminal commands I don`t want risking messing anything up..   


thanks

---

### Post by kc1di on 2014-05-01
yes do what you posted except change current to nvidia-304

---

### Post by moltoscarso on 2014-05-02
did what you suggested.

after reboot system stuck, as before, on last screen stating following:

[SIZE=3][FONT=system][COLOR=#000000]> wait-for-state stop/waiting[/COLOR][/FONT][/SIZE][COLOR=#000000][FONT=MarkerFelt-Thin][FONT=system][SIZE=3]* asking all remaining processes to terminate &#8230; [ok][/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=MarkerFelt-Thin][FONT=system][SIZE=3]* all processes ended within 1 seconds&#8230; [ok][/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=MarkerFelt-Thin][FONT=system][SIZE=3]ModemManager [611]: <info> caught signsl, shutting down[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=MarkerFelt-Thin][FONT=system][SIZE=3]ModemManager [611]: <info>ModemManager is shut down
[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=MarkerFelt-Thin][FONT=system][SIZE=3]
[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=MarkerFelt-Thin][FONT=system][SIZE=3]*deactivating swap&#8230;  [ok][/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=MarkerFelt-Thin][FONT=system][SIZE=3]*will now restart[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=MarkerFelt-Thin][FONT=system][SIZE=3]
[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=MarkerFelt-Thin][FONT=system][SIZE=3][2434.761792] reboot: restarting system[/SIZE][/FONT][/FONT][/COLOR]

---

### Post by moltoscarso on 2014-05-02
I'm afraid now I messed up anything.  System does start-up **very** slow and is accessible in recovery mode only.  Screen is black in standard mode.  Cannot reinstall all cause neither CD nor UBS stick is working.  strange enough is that windows vista on the other hand is starting correctly and **rebooting **
too!  

Any further suggestion how to bypass this new hurdle?   I wouldn't like to loose all my stuff in Lubuntu...

---

