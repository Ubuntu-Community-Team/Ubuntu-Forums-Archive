---
title: "No choice, only windows on boot"
date: 2012-07-02
forum: New to Ubuntu
---

### Post by Subcomfreak on 2012-07-02
Here we go. After finally being able to install unbuntu with the excellent help on these forums I need to actually have a choice of booting to it on start up.

Sense I had a special case, I need to manually partition out the linux install. My whole computer now looks like this:

C: (sdd) has windows 2000 on it (ntsf)
E: (sda 1?) ntsf, part of a 320gb hard drive. Has my windows stuff on it
F: (sda 2?) Same as above
sdb 1 (what was H: is an ext4 "/" that is 25gb
sdb 2 (again, H: is swap 2gb
sdb 3 (H: is what is left over of a 320gb hard drive in ext4 format as /home
J: (sdc) a USB flash drive with live on it.

Do note that I am not one hundred percent familiar with the linux drive naming conventions. SO I'm not sure if those sdxs are correct...

During the install I selected for the bootloader to go in just plane old sdb. No not sdbx or anything like that. I'm sure that linux itself installed correctly because I no longer have an H:/ drive under windows. 

My problem is that I can't select to boot one of the two. It only boots to windows. This is a problem. I know you guys have the solution;)

I can boot from live usb, and I have the "plop boot manager" on CD. SO I can get into linux if needed.

Thanks in advance.

---

### Post by anewguy on 2012-07-02
The problem is that the installation process, by default, installs the boot loader to the drive you are installing Ubuntu to unless you tell it otherwise.  So what you have now is the same default Windows on the 1 drive, and if you change to the 2nd
 drive and boot then Ubuntu will boot.

Boot up using the LiveCD, then run update-grub being sure to point it to the Windows drive, or just reinstall Ubuntu paying attention to where the boot loader is going.

---

### Post by Subcomfreak on 2012-07-02
someone suggested that I should use the boot-repair-disk. Will it fix the problem? If it doesn't I will use your method.

---

### Post by oldfred on 2012-07-02
If BIOS is so old that it does not let you select boot drive then you have to install grub2's boot loader to sda. Must be an old IDE system.

All BIOS that support SATA drives and many with newer IDE that had cable select systems should let you choose boot drive. Some BIOS hide the which drive settings as a sub menu under boot device hard drive setting and others may have a choose boot drive somewhere else even a different page of the BIOS. Many systems also have a one time boot key, f12 on my system.

---

### Post by mkstallings1 on 2012-07-02
I replied to your other thread before I saw this new one.  I used to get very annoyed with grub problems before I found Boot Repair.  The problem seems to be that you are not booting from the hdd that has grub installed to it.  To me, the easiest possible thing for now and in the future would be to burn Boot Repair to a disc, boot from it, and follow the onscreen prompts.  I'm pretty sure you can install it from synaptic too, but then you couldn't use it on any other distros you might mess up the bootloader on.

---

### Post by Subcomfreak on 2012-07-02
> **mkstallings1 said:**
> I replied to your other thread before I saw this new one.  I used to get very annoyed with grub problems before I found Boot Repair.  The problem seems to be that you are not booting from the hdd that has grub installed to it.  To me, the easiest possible thing for now and in the future would be to burn Boot Repair to a disc, boot from it, and follow the onscreen prompts.  I'm pretty sure you can install it from synaptic too, but then you couldn't use it on any other distros you might mess up the bootloader on.
tried to on a USB but no prompts. Probably due to me going through Plop. Going to burn a disc tomorrow. Too tired right now :p

THANKS FOR ALL THE QUICK RESPONSES!

---

### Post by Subcomfreak on 2012-07-03
Okay, I installed boot repair and ran the recommended. When I rebooted I got a black screen and nothing happened. I'm going to generate a report and the try again.
 [http://paste.ubuntu.com/1073016/](http://paste.ubuntu.com/1073016/)

[COLOR=#000]
     [/COLOR]
   Once it finished the first time, it said that I must boot from sdb in my bios, but my bios simply can not do that. I _think_ I can only boot from my scsi drive (C: in windows) which, via Gparted, is sdd.

But right now, I can't boot to windows or unbuntu except via live disc.

EDIT: Seeing as I have nothing to lose (I do have back ups by the way.) I'm going to throw grub in sdd.

---

### Post by flemur13013 on 2012-07-03
If you have Windows and Linux on separate physical disks, it's far better to select the OS to boot via BIOS, and to avoid having Windows depend on grub.   Besides being more robust, it's also much easier and simpler then messing with grub. 
(Hook up your windows disk - only - and make windows boot.  Then hook up your linux disk - only - and make linux work. Then hook up both disks and select the one to boot via BIOS).

---

### Post by Subcomfreak on 2012-07-03
Interesting. I was able to boot to unbuntu from my hard drive. A black screen came up with "can not display from this video mode. I just hit enter and It boot to unbuntu. So probably it worked, it is just my side of the equation that is screwed up. I'll try pressing the down arrow key to see if I can boot to windows.

---

### Post by Subcomfreak on 2012-07-03
I actually can't boot to windows now. Some may consider this a blessing, others, like me don't (yet).

Apparently my monitor doesn't want to display this menue, but from trial and error I found that the menu is something like this:

Ubuntu
Ubuntu recovery
Weird diagnostic

flemur, while I know that you suggestion WOULD work under "normal" circumstances, it will not work if I can only boot from drive C: (which is my windows).

So right now I really don't know what to do... I can all ways restore my C: (sdd) drive and that would probably get me back to normal windows MBR.

But what should I do now?

---

### Post by mkstallings1 on 2012-07-03
While in Ubuntu, did you "sudo update-grub"?  I have no idea how to fix your boot screen not showing,  but it may at least add Windows to your "invisible" list.

---

### Post by Subcomfreak on 2012-07-03
I did that and now I am able to boot into windows. Menu is still invisible, but this is what it is:

Ubuntu
Ubuntu recovery
memtest86+
memtest86+ (twice apparently)
Windows 2000

the top four are located in /boot, memtest is located in /boot/memtest86+

I guess I should go do some googling around to see more grub specific solutions. I'm pretty sure its a graphical problem, because my monitor is not picking up an output.

---

### Post by cryptotheslow on 2012-07-03
Have a look at the /etc/default/grub file using

```
gksu gedit /etc/default/grub
```

Particularly this section:
[i]# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480[/i]

Set that to a lowish resolution you know your monitor supports then save the file and run "sudo update-grub" again.

Once you can actually see the GRUB display you can use the vbeinfo command to get a list of all supported modes which you can then use to re-edit the /etc/default/grub file with a higher resolution if need be.

---

### Post by Subcomfreak on 2012-07-03
I was about to post in here saying that I tweaked that exact file and it worked. Problem solved!

---

### Post by YannBuntu on 2012-07-04
Hello
> **Subcomfreak said:**
> A black screen came up with "can not display from this video mode. I just hit enter and It boot to unbuntu.

For information, another way to solve this is via the "out-of-range" option of Boot-Repair (Advanced options -> GRUB options tab). This sets the GFXMODE to 640x480 and updates GRUB. Then a higher resolution can be tested as suggested by cryptotheslow.

---

