---
title: "I can't fix a boot problem"
date: 2018-03-17
forum: New to Ubuntu
---

### Post by arepacore on 2018-03-17
I've tried a lot of things i've seen in forums for fixing a boot problem.
I used to have windows 10 and then i just install ubuntu 16.04, so ubuntu works pretty well as you might know, but windows didn't start any more, and i tried all options i read in forums for repair that startup and didn't work, i just want to recover my files i can reinstall windows if is needed. But if i can repair the windows startup better so i save all the configuration. I used boot repair in ubuntu and gave me this url [http://paste.ubuntu.com/p/MfnsMvNCpH/](http://paste.ubuntu.com/p/MfnsMvNCpH/) for posting in forums for know what happen, please if someone can help thaaank you so much!

---

### Post by T.J. on 2018-03-20
Without knowing your hardware, it is difficult to give you a single straight answer. Windows 10 is very picky about what it will accept, and has been known to mangle boot-loaders when an update takes place, because it is constantly being patched or even completely reinstalled by Microsoft Update. Generally speaking, if you want a low maintenance setup with Windows 10, and still use Linux, I recommend installing Linux in VirtualBox on Windows instead, or installing Windows 10 in a Linux KVM if you own a retail license (and understand the trade offs in graphics).

 Every time Windows 10 updates when dual-booting, you may face this issue again.

If you are up to the challenge of a little maintenance  and it does not bother you, then dual-boot is definitely a good way to learn all kinds of really cool things about Windows and Linux. I don't know your level of expertise so we would have to take this step by step.  Have you tried forcing an update of the Linux boot-loader and do you know how?

Usually, I use Debian more than Ubuntu, but Ubuntu is made from Debian, so it should work.  

Try simply opening a terminal and then "sudo update-grub".  It may be slightly different, depending on changes made by Ubuntu.  After that, reboot and try Windows.  If that does not work, come back and we will try again.

---

### Post by oldfred on 2018-03-20
Most often the issue is Windows fast start up/hibernation. It also could be your Windows needs chkdsk.
And even if you turned fast start up off, Windows may turn it back on with updates.

Since UEFI system, you should be able to directly boot Windows from UEFI boot menu.

 HP - escape + F9 for boot menu, F10 for bios setup
[http://askubuntu.com/questions/870453/live-boot-usb-install-of-16-04-fails-on-hp-pavilion-23?noredirect=1#comment1349777_870453](http://askubuntu.com/questions/870453/live-boot-usb-install-of-16-04-fails-on-hp-pavilion-23?noredirect=1#comment1349777_870453)
[http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook](http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook) 

Boot-Repair does copy shimx64.efi to bootx64.efi for the fallback/hard drive boot entry in UEFI.

 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

