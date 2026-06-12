---
title: "Boot loader install failed"
date: 2017-03-27
forum: New to Ubuntu
---

### Post by seaharrier on 2017-03-27
Hello 
I am trying to install Ubuntu on a Vaio VGN-Z with a USB pen. At a certain point there is message that says: " Sorry an error occurred and it was not possible to install the boot loader at the specific location". 
Then it gives 3 options but whatever you chose the system does not go ahead. 
Anybody can help?

---

### Post by westie457 on 2017-03-27
Hello seaharrier, welcome to UF.

The boot loader is usually installed to one of two locations. The location is decided by the Hard Drive partitioning scheme (MS-DOS/MBR or GPT) so where were you trying to install the boot loader to?

Probably best to see more details in a Boot-info report.

Boot using the Live USB to Try-mode, connect an ethernet cable and open a web browser eg - Firefox.

Go here [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) You will want the 2nd option, follow the instructions as shown.
When the Boot Repair app starts do not try any repairs just go to the 'Create Report' button.
Post the generated link here, then we can see where it might have gone wrong.

---

### Post by seaharrier on 2017-03-27
thank you 

here is the generated link 
ubuntu@ubuntu:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair
 Simple tool to repair frequent boot problems.

Website: [https://sourceforge.net/p/boot-repair/home](https://sourceforge.net/p/boot-repair/home)
 More info: [https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair](https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair)
Press [ENTER] to continue or ctrl-c to cancel adding it
sudo apt-get update
gpg: keybox '/tmp/tmpp0y2t3zt/pubring.gpg' created
gpg: /tmp/tmpp0y2t3zt/trustdb.gpg: trustdb created
gpg: key 32B18A1260D8DA0B: public key "Launchpad PPA for YannUbuntu" imported
gpg: Total number processed: 1
gpg:               imported: 1
OK
ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair && boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package boot-repair
ubuntu@ubuntu:~$

---

### Post by yancek on 2017-03-27
You need to actually run the boot repair software you installed from the Menu, a terminal or the Dash (ubuntu icon in the upper left of the Desktop) and select the Create Boot Info Summary option as shown on the boot repair download page.  When you run it on your computer selecting that option, you will be given a link when it finishes.  Post that link here.

---

### Post by seaharrier on 2017-03-27
i tried but like you see it is unable to locate the boot -repair 
should I do something different?

---

### Post by oldfred on 2017-03-27
What version of Ubuntu?

Boot-Repair only has current versions of Ubuntu as install candidates.

---

### Post by seaharrier on 2017-03-27
version is 16.0

---

### Post by oldfred on 2017-03-27
If you run this separately from launch of app, do you get error messages?
sudo apt-get install -y boot-repair
Then can you run boot-repair or still get error?
boot-repair

What are specs of system? What video card/chip?
Older BIOS based or newer UEFI based system?

Did you verify that downloaded ISO was correct?
       [URL="https://help.ubuntu.com/community/HowToMD5SUM"]https://help.ubuntu.com/community/HowToMD5SUM


[/URL]

---

### Post by seaharrier on 2017-03-27
older BIOS
NVIDIA - geforce video card 
is a Vaio VGN-Z 
the ISO download was correct

---

### Post by yancek on 2017-03-27
There are two ways to use boot repair described on the page.  The first option is to download the iso file and either burn it to a CD or put it on a flash drive with the tools recommended.  Did you do that or did you use the second option to install it on the Ubuntu media you are using to try to install Ubuntu?  With the second option, you should be able to access it either from the Dash or a terminal.

---

### Post by seaharrier on 2017-03-27
I used the second option and this is what I  got [COLOR=#000000]ubuntu@ubuntu:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair[/COLOR]
[COLOR=#000000]Simple tool to repair frequent boot problems.[/COLOR]

[COLOR=#000000]Website: [/COLOR][https://sourceforge.net/p/boot-repair/home](https://sourceforge.net/p/boot-repair/home)
[COLOR=#000000]More info: [/COLOR][https://launchpad.net/~yannubuntu/+a...tu/boot-repair]("https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair")
[COLOR=#000000]Press [ENTER] to continue or ctrl-c to cancel adding it[/COLOR]
[COLOR=#000000]sudo apt-get update[/COLOR]
[COLOR=#000000]gpg: keybox '/tmp/tmpp0y2t3zt/pubring.gpg' created[/COLOR]
[COLOR=#000000]gpg: /tmp/tmpp0y2t3zt/trustdb.gpg: trustdb created[/COLOR]
[COLOR=#000000]gpg: key 32B18A1260D8DA0B: public key "Launchpad PPA for YannUbuntu" imported[/COLOR]
[COLOR=#000000]gpg: Total number processed: 1[/COLOR]
[COLOR=#000000]gpg: imported: 1[/COLOR]
[COLOR=#000000]OK[/COLOR]
[COLOR=#000000]ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair && boot-repair[/COLOR]
[COLOR=#000000]Reading package lists... Done[/COLOR]
[COLOR=#000000]Building dependency tree  [/COLOR]
[COLOR=#000000]Reading state information... Done[/COLOR]
[COLOR=#000000]E: Unable to locate package boot-repair[/COLOR]
[COLOR=#000000]ubuntu@ubuntu:~$[/COLOR]

---

### Post by kyknos12 on 2017-03-27
Does When you install ubuntu from usb flash was in ntfs; The ntfs has been subject to installation grub,Make It fat32

---

### Post by seaharrier on 2017-03-27
> **kyknos12 said:**
> Does When you install ubuntu from usb flash was in ntfs; The ntfs has been subject to installation grub,Make It fat32

I need to change the partition from BIOS?

---

### Post by kyknos12 on 2017-03-27
No you did not understand, I said if the usb was in ntfs changed in the filesystem to fat32 (format) and make new bootable live usb from iso ubuntu and retry new clean install from this

---

### Post by seaharrier on 2017-03-27
ah ok and how can i change the usb ? could you please explain?

---

### Post by kyknos12 on 2017-03-27
connect usb in a system windows, my computer right click format as fat32 or in linux system
```
sudo umount /dev/sdb1
```
```
sudo mkfs.vfat -F 32 -n /dev/sdb1
``` and make bootable usb from iso

---

### Post by seaharrier on 2017-03-27
> **kyknos12 said:**
> connect usb in a system windows, my computer right click format as fat32 or in linux system
```
sudo umount /dev/sdb1
```
```
sudo mkfs.vfat -F 32 -n /dev/sdb1
``` and make bootable usb from iso


ok I will try

---

### Post by westie457 on 2017-03-27
@seaharrier

You forgot to run the 2nd command 'sudo apt update', that is why boot-repair was not found.

---

