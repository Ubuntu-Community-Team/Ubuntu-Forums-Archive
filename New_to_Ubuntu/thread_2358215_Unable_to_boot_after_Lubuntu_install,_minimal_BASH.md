---
title: "Unable to boot after Lubuntu install, minimal BASH only"
date: 2017-04-10
forum: New to Ubuntu
---

### Post by heema-d on 2017-04-10
[ATTACH=CONFIG]274513[/ATTACH]

I have just installed Lubuntu on my HP Stream 11 (2015) with Windows 8.1, no dual boot just Lubuntu only. When I first tried to install it I was having issues with installing GRUB. After I used Boot Repair and rebooted my laptop I get error messages and only get the minimal BASH screen. No option to boot from USB or anything.
I used to us Ubuntu, but that was years ago, so I basically feel like a noob. I have searched on the forums and google and couldn't find anything to help.

I know the image is crappy but its the best one I could take, it says:

Failed to open \EFI\Microsoft\Boot\grub64.efi -Not Found
Failed to load image \EFI\Microsoft\Boot\grub64.efi: Not Found
start_Image() returned Not Found

Thanks

---

### Post by yancek on 2017-04-11
Your machine is using UEFI which I am not very familiar with.  Since you have the boot repair software, the best thing to do it to post a link to the boot repair output or run it again if you don't have that.  This time select the option to Create BootInfo Summary and don't try any repairs.  When it finishes, it should show you a link you can post here which will make the output available here and some of the members more familiar with UEFI installs should be able to help.

From what I have read, HP does not comply with the UEFI standards and that adds some complexity to the problem.

---

### Post by heema-d on 2017-04-11
How would I go about doing that when I can't even load up any OS?

---

### Post by heema-d on 2017-04-11
Is there tutorial to show me how to boot a usb in Minimal BASH?

---

### Post by yancek on 2017-04-11
You need to change the BIOS the way you did to first boot Lubuntu from the usb.  If you are getting the grub> prompt, you are past that point.  You should see a key on boot telling you which key to tap to get into the BIOS.  If you can't get into the BIOS, that's a totally unrelated problem and has nothing to do with whatever operating system you might have.

---

### Post by heema-d on 2017-04-11
I can't get into BIOS/UEFI. 
Whenever I exit grub>prompt, I can see the BIOS for a split second then the screen goes black

---

### Post by Geoffrey_Arndt on 2017-04-12
When you first boot up the computer - - that's when you get into the BIOS/UEFI, not when you shut it down (including exiting the grub-prompt).   So, when you turn the machine on, you have a few seconds to press either F2, F10, or perhaps the Esc key).   

EDIT:   when I google for "enter bios for HP Stream 11" . . . I saw it's the F10 button.   Normally, you have to keep tapping that key (one two taps per second) until you see the BIOS.

Here's more info:   [http://h30434.www3.hp.com/t5/Notebook-Boot-and-Lockup/Linux-live-boot-up-issue-Some-distros/td-p/5397785](http://h30434.www3.hp.com/t5/Notebook-Boot-and-Lockup/Linux-live-boot-up-issue-Some-distros/td-p/5397785)

---

