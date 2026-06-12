---
title: "Ubuntu boots into black screen installed Nividia drivers"
date: 2012-11-03
forum: New to Ubuntu
---

### Post by neewbee on 2012-11-03
I just did a clean install of Ubuntu 12.10. I installed the updates for my graphics card a Geforce GT 640 in the terminal. I did these following commands in the terminal.



sudo apt-get purge nvidia-current
sudo apt-get install linux-headers-generic
Reboot and then Install proprietary drivers via Software Sources
 


I rebooted my machine. First my machine would boot to purple and than I would get frequency errors.

Thanks for the tips and tricks guys!

---

### Post by bogan on 2012-11-03
Hi!, [B]neewbee,
[/B]
Have you tried the other drivers in Additional Drivers?.

If you can get to a terminal 'Ctrl+Alt+t', please Post the following: ```
lspci | grep -iA3 vga
sudo apt-cache policy nvidia-current
```Chao!, **bogan.**

---

### Post by neewbee on 2012-11-03
When I originally installed ubuntu it installed the additional drivers for my card automatically. I kept on getting graphics issues like it would boot to black screen on startup. I would get the frequency errors. I than went in my terminal and typed in those following commands purging the propriety drivers did a reboot and than I couldn't even access the main screen. Kept on getting frequency errors. 

Should I do a clean install again and try downloading the additional drivers on jockey. 

I am also running 12.10 alongside windows. Windows and Ubuntu are on two different drivers. Are there any good dual boot programs to take advantage of for this? 

thanks again.

---

### Post by bogan on 2012-11-03
Hi!. **neewbee**,

At this stage there are other things to try before resorting to a re-install, but without any info about your system and video card, it is not possible to sensibly advice.

I can only suggest that if you are using 12.10 & can get to a Terminal, you try running: ```
sudi apt-get install linux-headers-generic
``` before purging the video driver and re-installing it, or installing a different driver.

[COLOR=Red]Please Post the info requested[/COLOR].

Chao!, **bogan**.

---

### Post by neewbee on 2012-11-03
Here are my specs for my system.

Kingston 8gb of ram
Corsair 650 psu 
EVGA Geforce GT 640 
Asus P8-v-z77-v mobo
650 gb hardrive for linux 
256gb ssd samsung 830 for windows
i7 2600 3.40ghz sandy bridge

I am running 12.10. I just installed the updates. Before it booted to the main screen there were colour bars. Which means there is something up with my graphics. I know my card runs smoothly in windows. Also compiz keeps on crashing. Should I download drivers from Jockey?

Also when I restart my system it boots to the frequency errors. Sometimes when I restart it boots to the main screen where I can sign in and than it freezes.

---

### Post by bogan on 2012-11-04
Hi!, neewbee,

I can only repeat what is in my Posts #2 & #4

Please Post output of : 
```
lspci | grep -iA3 vga 
sudo apt-cache policy nvidia-current
``` And what messges you get from: 
```
sudi apt-get install linux-headers-generic
``` That is: does it install? or does it say: ' linux-headers-generic is already the latest version'?

Whether to install drivers from 'jockey,' or not, depends on what is installed and the above requested information.

Also does the Bios have an option to choose between the CPU integrated graphics of: [ i7 2600 3.40ghz sandy bridge ] and the nvidia card [ EVGA Geforce GT 640 ] ??

You probably need the latest nvidia driver and also Bumblebee. [ not exactly a 'newbie' project. ]

Edit: I do not know what you mean by: "frequency errors"; do you mean 'refresh rates'??

Chao!,** bogan**.

---

### Post by grahammechanical on 2012-11-04
I think that he means a messed up screen image instead of a pure screen image. This happens when the video driver does not completely flush the screen image from some memory cache as it loads a new image.

We had this during the 12.10 development cycle with both the Nvidia and the Nouveau drivers. At that time these messed up screen images cover the screen completely and made the login screen unusable and even if we got passed the login to the desktop we could not use it for the same reasons.

I am running 12.10 that is being converted (over the months) into 13.04. I am using the Nouveau driver and as the loading process switches from log in to the desktop I get a partially messed up screen image that clears once I get to the desktop. I have not tested this recently with the Nvidia drivers.

This is what I think is happening on the OP's machine. Nvidia drivers have not been up to standard for some weeks. Then we should also remember that the Xserver does not start using the video drivers until later in the boot process so that sometimes we may see what we think of as scanning issues when it is just the Xserver changing its default & basic video settings to those that are optimum for the monitor.

Regards.

P.S. If we get a Grub menu we can select the Recovery Mode and then Resume and that will-may get us to a login screen and desktop without loading the proprietary drivers. From there we can try to solve the problem.

In 12.10 we can go to System Settings>Software Sources and under the Additional Drivers tab we can choose other drivers. If we have the proprietary drivers installed we can choose from 3 versions, including experimental drivers, or to use the Nouveau driver. If we only have the Nouveau driver listed then we can activate the proprietary drivers from there.

This might be a safer method than running commands in a terminal when we are not sure of what we are doing.

---

### Post by bogan on 2012-11-04
Hi!, **grahammechanical,**

+1 your Post, fully agree; but i was wary of advising with an absence of relevant data, ginen that the OP calls him/herself: 'neewbee'.but refers to 'jockey'.

Chao!, **bogan**.

---

