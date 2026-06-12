---
title: "boot problem"
date: 2012-10-03
forum: New to Ubuntu
---

### Post by hosein685 on 2012-10-03
Dear all

When i want to boot my Ubuntu 12.04 in the GNU GRUB (version 1.99-21ubuntu3) menu i get this :
" Kernel panic -not syncing: No init found. Try passing init=option to kernel.
.
.
.

Any suggestion to fix this would be appreciated

---

### Post by 2F4U on 2012-10-03
Is that a fresh installation? Seems as if Grub is not able to find the boot image in the partition it is expecting it. Does your Grub configuration maybe point to the wrong partition?

---

### Post by hosein685 on 2012-10-03
I was upgrading using "sudo apt-get upgrade" command
after a while it stopped with error

then when i restart ubuntu it never booted again and now i just have grub command-line
grub>

---

### Post by cway00 on 2012-10-03
Based on your information 
> **hosein685 said:**
> I was upgrading using "sudo apt-get upgrade" command
after a while it stopped with error

then when i restart ubuntu it never booted again and now i just have grub command-line
grub>

**Question are you on dual boot :**

On dual boot once you update your Ubuntu OS, your Windows / Fedora will  not be listed on your grub. After installing Windows / Fedora your  Ubuntu will not boot anymore and its grub may be wiped out. To restore  it follow the steps below

**To Reinstall Grub**

You need to have Ubuntu Live CD or Live USB. Normal session can be used to repair the grub. Boot using your Ubuntu Live CD or Live USB, while booting choose Try Ubuntu.

Once booted then open a terminal, and run the following command one by one to **install** the **boot repair.**

[B]To add boot-repair to the repository
[/B]```

sudo add-apt-repository ppa:yannubuntu/boot-repair

```

[B]To Update your repository
[/B]```

sudo apt-get update

```

[B]To install boot-repair
[/B]```

sudo apt-get install -y boot-repair

```

Once Installation complete run **boot-repair** on terminal by typing the following command or select it by **System->Aministration->Boot Repair**.
```

boot-repair

```

**NOTE:** Update the Boot Repair if its newer version is available.
It  will scan the System for few seconds and will show you the options  Recommended repair and Create a BootInfo summary. By clicking the** Recommended Repair **it will start repair the grub. 

Once done **click ok** and **restart** your system, your grub should work now. If not run the boot-repair again using live cd / usb. Then follow the steps below.

Select the Advanced options, In **Main options** tab check  whether the following options are selected or not. If not select it, the  options are Reinstall Grub and unhide boot menu for 10 seconds. Check  the screen shot below

Then select the **GRUB locations** tab and check the following options are selected or not. The options are OS to boot by default and place grub into, In “**OS to boot by default**” option choose the OS which you want to be default on boot. Then select the drive where you need to reinstall the grub in “**place grub into**” option and click apply. Check the screen shots below

Click ok and restart your System. 

Hope it helps

---

### Post by hosein685 on 2012-10-03
Unfortunately didn't work:(

any suggestion?

---

### Post by cway00 on 2012-10-03
> **hosein685 said:**
> Unfortunately didn't work:(

any suggestion?

* Did you try to repair from the LiveCD 
* Which version of Ubuntu cos I am giving u an experience sample of 12.04 precise? 
*any more details provided about the cause or action that lead to the problem?

Hope to hear from u

---

### Post by hosein685 on 2012-10-03
Yes i tried to fix it with a live CD
Ubuntu 12.04 64bit

i installed a package needed for installing teamviewer7 , but i don't remember the name!
after that my hostname changed from "mechanic@modeling" to "modeling" automatically and colors lost in terminal

i tried to fix it and i used this command  " sudo apt-get upgrade"
after restarting, GRUB didn't work again.

one question: can i reinstall ubuntu but keep my home folder??

---

### Post by oldfred on 2012-10-03
From liveCD or USB post the link to BootInfo report from Boot Repair.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

If you have a separate /home, you should be able to reinstall keeping your /home using Something else to select which partitions to use & format and of course NOT formatting but using existing /home. Best to see BootInfo report first.

---

### Post by hosein685 on 2012-10-04
Thanks for your response

After boot repair finished this box appeared :

 " Boot successfully repaired.

Please write on a paper the following URL:
[http://paste.ubuntu.com/1259345/](http://paste.ubuntu.com/1259345/)

In case you still experience boot problem, indicate this URL to:
[email]boot.repair@gmail.com[/email] or to your favorite support forum.

You can now reboot your computer.


The  boot files of [Ubuntu 12.04.1 LTS] are far from the start of the disk.  Your BIOS may not detect them. You may want to retry after creating a  /boot partition (EXT4, >200MB, start of the disk). This can be  performed via tools such as gParted. Then select this partition via the  [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))  "

---

### Post by danisari on 2012-10-04
@cway00 
Thank you very much! I'm having this problem for over 48 hours and finally it is solved and thanks to you..
This is really great forum and  I wish I knew it before now..

---

### Post by YannBuntu on 2012-10-04
**@hosein:**

Hello

Were you able to boot this Ubuntu before? what did you do just before getting the error? (update? upgrade?)

Depending on your answer, the solution may be to create a separate /boot partition as advised by Boot-Repair.

---

