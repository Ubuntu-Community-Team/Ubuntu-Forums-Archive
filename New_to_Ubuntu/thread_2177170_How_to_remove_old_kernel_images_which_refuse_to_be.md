---
title: "How to remove old kernel images which refuse to be removed"
date: 2013-09-27
forum: New to Ubuntu
---

### Post by yash_pal2 on 2013-09-27
OS: Ubuntu 13.04, 64 bit for desktop as downloaded, no modifications/ no PPAs

I removed (purged) the earlier kernels and after that, again checked for the kernels remaining with the command:[SIZE=3] *[SIZE=2]dpkg --list | grep linux-image[/SIZE]*[/SIZE]
   

yashpal@yashpal-Inspiron-M5010:~$ dpkg --list | grep linux-image  

 ii [COLOR=#ff0000] linux-image[/COLOR]-3.8.0-29-generic                   3.8.0-29.42                            amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP  

 ii  [COLOR=#ff0000]linux-image[/COLOR]-3.8.0-30-generic                   3.8.0-30.44                            amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP  
 rc [COLOR=#ff3333] l[/COLOR][COLOR=#ff0000]inux-image[/COLOR]-extra-3.8.0-19-generic        3.8.0-19.30                            amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP  

 rc  [COLOR=#ff0000]linux-image[/COLOR]-extra-3.8.0-21-generic        3.8.0-21.32                            amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP  
 rc  [COLOR=#ff3333]linux-image[/COLOR]-extra-3.8.0-22-generic        3.8.0-22.33                            amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP  
 rc  [COLOR=#ff3333]linux-image[/COLOR]-extra-3.8.0-25-generic        3.8.0-25.37                            amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP  
 rc [COLOR=#ff3333] linux-imag[/COLOR][COLOR=#dc2300]e[/COLOR]-extra-3.8.0-26-generic        3.8.0-26.38                            amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP  
 ii [COLOR=#ff3333] linux-image[/COLOR]-extra-3.8.0-29-generic         3.8.0-29.42                            amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP  
 ii  [COLOR=#ff3333]linux-image[/COLOR]-extra-3.8.0-30-generic         3.8.0-30.44                            amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP  
 ii  [COLOR=#ff3333]linux-imag[/COLOR][COLOR=#dc2300]e[/COLOR]-generic                                3.8.0.30.48                            amd64        Generic Linux kernel image  
 yashpal@yashpal-Inspiron-M5010:~$  

I tried  to remove [COLOR=#ff3333] l[/COLOR][COLOR=#ff0000]inux-image[/COLOR]-extra-3.8.0-19-generic but it does not remove

   
yashpal@yashpal-Inspiron-M5010:~$ sudo apt-get purge linux-image-3.8.0-19-generic  

 [sudo] password for yashpal:  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 [SIZE=2]*Package 'linux-image-3.8.0-19-generic' is not installed, so not removed  *[/SIZE]

 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.  

 yashpal@yashpal-Inspiron-M5010:~$  

Now, if[SIZE=2] Package* 'linux-image-3.8.0-19-generic'* is not installed[/SIZE], why is it being shown in the list and if it is installed, how can it (and other redundant kernels) be removed?
Could anyone enlighten me please.
PS:
I do not have proficiency in command line; I copied and pasted commands after searching on the web; so some complicated command will be well beyond my ability.
Also, could anyone tell me how to enclose results of command line operations in a window so as to move them up and down and see them in same manner as on the right side of this post (and this page)

---

### Post by deadflowr on 2013-09-27
I believe dpkg --list shows what packages are available in the repos.
Try
```
ls /boot
```
It should show what kernels are installed.
```
apt-cache policy linux-image* | grep Installed
```
show list what kernel images are installed.(or not installed)

---

### Post by mikewhatever on 2013-09-27
Note the "rc" and "ii" in the dpkg output. 
rc - package removed, cnfig files remain
ii - package installed

---

### Post by Impavidus on 2013-09-27
> **yash_pal2 said:**
> dpkg --list | grep linux-image  
 rc [COLOR=#ff3333] l[/COLOR][COLOR=#ff0000]inux-image[/COLOR]-**extra**-3.8.0-19-generic         3.8.0-19.30                            amd64        Linux kernel  image for version 3.8.0 on 64 bit x86 SMP  

(...)

I tried  to remove [COLOR=#ff3333] l[/COLOR][COLOR=#ff0000]inux-image[/COLOR]-**extra**-3.8.0-19-generic but it does not remove

   
yashpal@yashpal-Inspiron-M5010:~$ sudo apt-get purge linux-image-3.8.0-19-generic  

 [sudo] password for yashpal:  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 [SIZE=2]*Package 'linux-image-3.8.0-19-generic' is not installed, so not removed  *[/SIZE]

You used the wrong package name. You forgot the "extra" in the name.

Unless of course you made an error copy-pasting.

---

### Post by ajgreeny on 2013-09-27
I use ```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
``` to tell me what kernels I have installed and will be in the grub menu, even if I don't usually see that menu at boot time.

To remove any unwanted kernels after an update, I always use synaptic, the best package manager available in the Linux world, in my opinion.

---

### Post by Bashing-om on 2013-09-27
yash_pal2; Hi !

In addition to all the other most excellent advise:
May I suggest that you check that the headers file has also been removed from each kernel:
```

dpkg --list | grep linux-headers

```

In respect to 'rc' .. Removed but Config files remain:
While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package with the following command.
```

dpkg -l | grep '^rc' | awk '{print $2}' | xargs dpkg --purge

```

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by deadflowr on 2013-09-27
Big +1 to using synaptic package manager.
It makes things far far far easier when removing stuff like old kernels.
I also find it harder to misspell something when it is already spelled out correctly.
I misspell  alot.

---

### Post by philinux on 2013-09-27
I use this from step 5.

I usually do the dry run first too.

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

---

### Post by yash_pal2 on 2013-09-27
Many thanks:-  '	 deadflowr', 'mikewhatever',[COLOR=#000000] 'Impavidus', '[/COLOR][COLOR=#000000]ajgreeny[/COLOR]',[COLOR=#000000]'Bashing-om',[/COLOR] 'philinux'
 
It will take me time to work through the suggestions  and report back; by the way, there was no error in copy - paste as no  site mentioned [COLOR=#ff3333]l[/COLOR][COLOR=#ff0000]inux-image[/COLOR]-'extra' , they all dealt with 'linux image' and such similar names. However, every aspect would have to be looked into.

---

### Post by yash_pal2 on 2013-09-28
Solved
[COLOR=#000000]The suggestion by 'Impavidus'[/COLOR] - "You used the wrong package name. You forgot the "extra" in the name" 
did the trick and after removing the unwanted images, 
 *dpkg --list | grep linux-image* shows only 
3.8.0-29-generic, 3.8.0-30-generic and generic                                3.8.0.30.48

I had a lot of problems with Ubuntu 12.04 and no upgrades could be installed; there were messages that boot sector was full. Only recently I realised that all the old kernels had then accumulated. So I wanted to remove the old kernels.
Many thanks once again  '	 deadflowr', 'mikewhatever',[COLOR=#000000] 'Impavidus', '[/COLOR][COLOR=#000000]ajgreeny[/COLOR]',[COLOR=#000000]'Bashing-om',[/COLOR] 'philinux' for the advice, all of which I have noted down & will come handy sooner or later.

---

