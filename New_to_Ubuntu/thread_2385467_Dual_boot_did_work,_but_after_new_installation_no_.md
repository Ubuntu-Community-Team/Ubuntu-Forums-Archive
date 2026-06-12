---
title: "Dual boot did work, but after new installation no moore"
date: 2018-02-20
forum: New to Ubuntu
---

### Post by roggan99 on 2018-02-20
I have Ubuntu 16.04 and win 10. Dual boot disapered on my second intallation, i did move partitions and reinstall ubuntu becouse i like it use my hdd better. 
Among other changes I moved my /boot-partition to another partion (the first partition on hdd and format to ext4) 

What is wrong? Now starts ubuntu direkt without any question. I took a screen picture showiing my partiions.


Anyone have a solution, I am new in Linux-world so thanks for an easy to understand solv.....

Best regard Roger

---

### Post by ajgreeny on 2018-02-20
See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.

**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by roggan99 on 2018-02-21
Here is my Pastebin link : [http://paste.ubuntu.com/p/TX6D8CkVnB](http://paste.ubuntu.com/p/TX6D8CkVnB)

BR Roger

---

### Post by roggan99 on 2018-02-24
Aha! You are not going to advice me more? I understand that you come back to me and say to me  what I should do!? 
Ok i am glad for your first responce... Wery glad! But I waiting for answer 3-4 days now? Maybe thats normal sometimes? How can I know?

Acording to the repair disc, i can try that first option. 

/Roger

---

### Post by coffeecat on 2018-02-24
> **roggan99 said:**
> Aha! You are not going to advice me more? I understand that you come back to me and say to me  what I should do!? 
Ok i am glad for your first responce... Wery glad! But I waiting for answer 3-4 days now? Maybe thats normal sometimes? How can I know?

@roggan99, if you do not get a reply in 12-24 hours, simply bump your thread to bring it up to the top again by posting the single word "bump". You left this thread to sink down for 3 days. 

Also, please do not assume that anyone asking you for information is necessarily going to provide a solution. A forum is where any member may choose to contribute to a thread - you do not get individual attention. Many forum members here, especially forum staff, will get the ball rolling by asking for further information so that you can help others to help you.

Good luck with finding a solution.

---

### Post by oldfred on 2018-02-24
It looks like you overwrote your Windows boot partition which must be NTFS and unusually is first partition on BIOS/MBR systems.

The Windows boot partition has bootmgr & /boot/BCD Windows boot files.
You can install Windows without boot partition but then boot flag must be on the partition with the Windows boot files or in your case sda2, not sda1.
And you need to recreate the BCD using your Windows repair flash drive or Windows third party tools. You cannot create BCD using Linux tools.

Grub looks for bootmgr & BCD to know which Windows partition to boot from. It does not use boot flag.
But with Windows 10, you must have fast start up off which is just hibernation or grub will not boot Windows.
And Windows updates often turn fast start up back on. 
If grub does not boot Window you may need to use your Windows repair disk or repair console in installer. Or temporarily reinstall Windows boot loader to directly boot Windows, repair Windows & then restore grub boot loader.

Boot-Repair can restore boot loaders, but cannot do other Windows fixes.
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System) 

      
 f8 to get to repair install screen, if you can start to boot
[URL="http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html"]http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html

[/URL]
 [http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive](http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive) 

[URL="http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html"]
[/URL]

---

### Post by roggan99 on 2018-02-25
Solved! New windows install and then windows booted nomaly. Then I booted with my **Boot-Repair **disc.. I did not run any paticular repair, just like to put a new pastebin, but when I started after this was made dual boot was OK

Thanks for helping!

---

