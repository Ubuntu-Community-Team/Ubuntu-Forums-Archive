---
title: "Boot loop on laptop probook 655 g1"
date: 2022-06-24
forum: New to Ubuntu
---

### Post by darkndskys on 2022-06-24
I installed using the installation media made by using a usb and rufus.

The os is definately there, however; i have to go into options to start the os. 

I dont know if the boot loader installed coreectly. I have to select the efi file, then select grub. Then the os will start as normal. I was wandering what I did wrong.

I am still new to linux. please help.

---

### Post by darkndskys on 2022-06-24
I would like to also add that i installed fedora previously with no issues, thsi was something that happend immidiately after ubuntu

---

### Post by yancek on 2022-06-25
Is Ubuntu the only OS on the computer?  If you another OS such as windows, which version?  Do you still have Fedora installed and if so, is it an EFI install? Generally with an EFI install, the default install option will install correctly putting Grub boot files on the EFI partition and the rest of the Grub files on the Ubuntu root partition.

---

### Post by darkndskys on 2022-07-16
No there are no other partions on the computer. I apologize about the late reply, I am a truck Driver and am out weeks at a time, and this was meant to be my learning tool on the road. Fedora, worked perfectly. This install however, i have to open the boot options and start it up as a efi file. I have reinstalled it this evening, to see if it was something i did wrong. It could still be something im doing wrong, or the hardware. I am totally confused. If i were to install ubuntu on my desktop right now, i would bet money that it would work perfectly. I have also downloaded the iso file over again to make sure it was not something as simple as corruption or the wrong iso. The last os that was on this computer was an OEM copy of Windows 7 SP 2. 

When i reinstalled i wiped it with Gparted, then installed with ubuntu.

---

### Post by yancek on 2022-07-16
What happens if you do not select Grub/Ubuntu from the EFI file option?  Was your windows 7 an EFI install?  Was Fedora?  What do you see if you access /boot/efi/EFI directory?  What folders?  Have you tried accessing the BIOS firmware rather than the boot options which is a one time boot selection?  Accessing the BIOS firmware should give you the option to make a permanent change to Grub/Ubuntu.  A default windows 7 install would not have likely been EFI but it is possible.

Who is the manufacturer of your laptop probook 655 g1?

---

### Post by darkndskys on 2022-07-16
I dont know, I put the iso on usb, loaded up fedora, it worked first time.. dont know what the technical deal was with that. As for the windows 7 I came factory with the computer, I never had to worry about a reinstall, i just used the recovery partion to set it back to factory state. If i do not go to "boot options" It does a continous loop for the hp bios splash screen. It does not stop. i have to select "Boot Options/EFI/Ubuntu" and it will run. I could take a video with a cell phone later tonight if that would help answer questions. Because I literally just wipe the drive, and run the installer. 

Could it be something to do with the medium I am using to make the live usb?

---

### Post by darkndskys on 2022-07-16
hp 
did not see your question.

---

### Post by yancek on 2022-07-17
When you downloaded Ubuntu, did you use the checksum after download to verify it?  There is an option on the download page for the checksum.

Do you have another computer you can use to try to just boot the usb to see if it works?  Rufus usually works although I've not used it myself.  Have you tried writing the Ubuntu iso to a usb more than once?  Have you tried other software such as Ventoy?

Can you access the BIOS firmware (usually the F10 key on an HP) to make a permanent change to Ubuntu?  If it is an EFI install, you should have an OS Boot Manager option under the UEFI setting to change the boot order.
If you boot the Ubuntu 'live' USB, can you mount the partition where Ubuntu as installed and access the /boot/efi/EFI partition and see if there is an ubuntu directory?

---

