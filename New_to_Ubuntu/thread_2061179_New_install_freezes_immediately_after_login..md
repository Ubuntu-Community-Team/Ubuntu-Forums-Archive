---
title: "New install freezes immediately after login."
date: 2012-09-21
forum: New to Ubuntu
---

### Post by ManudaNZ on 2012-09-21
Never used Linux before.

Have old computer not used for 5 years with win2000. Want kids to use it.

80gb drive. Athlon +3700 1.2Ghz.
Foxconn NF4K8AB motherboard.
Nividia Gefore 6600GT graphic driver.
1Gb 333 DDR Ram

I tried the 32 bit.iso file first. But had EDD: errors when loading disk. So I downloaded the AMD_alternative.iso file.
Installed Ubantu 64 bit from CD burned from my normal computer. And it doesn't work. The comp starts fine. I can log in fine. But Desktop starts and looks great. But the second I click on anything my screen freezes and I cant do anything. Ctrl+ALT+F1 does nothing. nothing works.

I see this may be caused by NiVidia Cards but there seems to be no definitive guide on how to fix..

How do I fix.

TY for your replies.

PS. Community always seems to assume I know wat sodu means or grub or Open your Terminal? I'm like wtf is that! there seems to be no explanations on the internet of what these things are.Or on the website.

---

### Post by Luigi2012SM64DS on 2012-09-21
try lubuntu if you have a slow machine or don't care about visuals.
also download the 32bit version. i don't think a win2000 computer should be 64 bit.
also 1MB RAM...?
and btw Terminal is the linux form of command in windows.
apt-get is just what you typw inside to download ans install things.

---

### Post by ManudaNZ on 2012-09-21
that should have said 1GB ram..

As far as I can tell this more than meets the specs for ubantu.

---

### Post by NikTh on 2012-09-21
> **ManudaNZ said:**
> 
Installed Ubantu 64 bit from CD burned from my normal computer. And it doesn't work. The comp starts fine. I can log in fine. But Desktop starts and looks great. But the second I click on anything my screen freezes and I cant do anything. Ctrl+ALT+F1 does nothing. nothing works.

Hi , 

I am standing on above. 

Open a terminal with Ctrl+alt+t keys combo. Copy-paste from here bellow commands, one at time  and press Enter. Post back here the results 

```
lspci -nnk | grep -iA2 vga
free -m
df -Th
```Thanks

---

### Post by ManudaNZ on 2012-09-22
OK I have tried a few things. Notably.. I have re-installed Ubuntu using the i386 alternative.iso file. I wiped the partitions and just installed it clean..

Now I get a blank screen when I start up.

ctrl+Alt_F1 works  So I can log-in using console.


Results from screen..

lspci -nnk | grep -iA2 vga

05.00 VGA VGA compatible controller [0300]: NVIDIA Corporation MV43 [Geforce 6600 GT] [10de:0140] (rev a2)
Kernal Driver in use: nouveau
Kernal Modules:nouveau, nvidiafb

fee -m

mem;  total 1001, free 946, shared 0 buffers 0 cached 21
+/_ buffers/cache:  22    978
Swap:  1022  0  1022

df -Th

Filesystem  --etc..(headers)
/dev/sda1   type: ext4  Size:74G  Used:1.7G Avail:69G  User%:3% Mounted on:/
udev   type: devtmps Size: 494M  Used:4.0K Avail: 494M    :1%   /dev
tmpfs  tmpfs    :201M Used:256K  Avail: 200M  :1%  .run
none   tmpfs  :5.0M  :0 :5.0M :0%  /run/lock
none   tmpfs  :501M  :0  :501M  0%  : /run/shm


( I found another thread that said I should uninstall Nvidia and install nouveau.)

but it froze when i tried installing nouveau. And I had to reboot machine as it was unresponsive.

---

### Post by ManudaNZ on 2012-09-22
OK. My machine even freezes in Console mode randomly.. It takes anything from 30 secs to  about 5 mins and then the computer becomes unresponsive. Just stops working.. Hard drive stops spinning.

---

### Post by mörgæs on 2012-09-22
Are you sure about 3700+ and 1.2 GHz?

Try a memory test from the boot menu. Might need to run a couple of hours.

If the memory works, I would go for a fresh install of X/Lubuntu. 

Stick to the open-source graphics drivers, at least in the beginning

---

### Post by ManudaNZ on 2012-09-22
It is definately 3700+ AMD processor. It says it when the computer start up..
Funily enough I had tried the memory test previously in my stuffing around wit it and it came up fine.. But now I can't get the Grub loader anyhow.

I tried downloading Xubuntu desktop i386 (the 4th iso file i've now downloaded). but the when it tries to boot from CD the screen goes blank for a few seconds.. the CD starts stuttering and then the computer will reboot automatically.


I will now be inserting disk into my Xp computer.. and reformatting disk and installing Win2000 back on. And then my reviews of Linux will be a positve..don't ever touch as it isn't a very good system,...

---

### Post by ManudaNZ on 2012-09-22
OK. I think I may have found my problem...

I have noticed that my Bios resets itself after I have unplugged the computer.. and sometimes when Ubuntu just freezes and I hit the reboot button.

I am now suspecting my motherboard battery has gone dead. I suppose the computer is about 8years old after all so no surprise about the battery.
Interestingly this doesn't seen to be affecting Windows 2000 as much as Ubuntu.
I am currently re-installing Win2000 and I will now have to go and buy a new computer..(which I was trying to avoid)

I am still keen to try Linux.. I will have to see if I can convince my wife to give up her laptop with that crappy Vista (shivers down spine.. yuck).. lol.

---

### Post by Luigi2012SM64DS on 2012-09-22
forget xubuntu
try lubuntu
last try.

---

### Post by NikTh on 2012-09-23
> **ManudaNZ said:**
> 
```
lspci -nnk | grep -iA2 vga
05.00 VGA VGA compatible controller [0300]: NVIDIA Corporation MV43 [Geforce 6600 GT] [10de:0140] (rev a2)
Kernal Driver in use: nouveau
Kernal Modules:nouveau, nvidiafb
``` 

Try to install nvidia driver with this command 
```
sudo apt-get install nvidia-173
```Then give this command ```
sudo nvidia-xconfig
```and reboot your PC . 
> **ManudaNZ said:**
> fee -m
```
mem;  total 1001, free 946, shared 0 buffers 0 cached 21
+/_ buffers/cache:  22    978
Swap:  1022  0  1022
```

Here it seems that you have low physical mem. 1GB. 
So try to use ubuntu-2d session. Select the session from login screen. Click Ubuntu Icon in login box and select **ubuntu-2d**



> **ManudaNZ said:**
> ( I found another thread that said I should uninstall Nvidia and install nouveau.)
but it froze when i tried installing nouveau. And I had to reboot machine as it was unresponsive.
Nouveau is pre-installed . You don't need to install anything if you installed Ubuntu (fresh installation). 

You must try nvidia-173 driver and not nvidia-current , maybe supports your card (GT6600) better. 

Thanks

---

### Post by mörgæs on 2012-09-23
> **ManudaNZ said:**
> 
I am currently re-installing Win2000 and I will now have to go and buy a new computer..(which I was trying to avoid)


A new computer is likely to come with Windows 7 pre-installed in a way that makes dual booting with Ubuntu difficult. 

I would go for a 4-5 years old used computer. You should be able to get it for a very modest price.

An even more modest price is a new BIOS battery for the motherboard. The most common type (CR2032) should cost you less than 10 US $.

---

