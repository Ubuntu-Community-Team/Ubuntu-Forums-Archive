---
title: "Boot Problem &quot;Reboot and select proper boot device&quot;"
date: 2014-04-02
forum: New to Ubuntu
---

### Post by pbcrow1 on 2014-04-02
I am having trouble booting Ubuntu, which I have just installed. have an Acer desktop computer that came with Windows 8 already  installed. Before I began attempting to add Ubuntu, I disabled fast startup and secure startup. I installed  Ubuntu 13.10 from a Live USB I made (I believe it installed properly, but am unsure as I have not yet been able to access it), and I  installed it to a section of the hard drive that I partitioned away  from Windows. After installing Ubuntu, I restarted my  computer and it went straight to Windows, so I restarted again from the  Live USB and ran a program called boot repair to attempt to fix the problem. After running boot repair, when I restart  my computer, if I don't have the USB plugged in, I get a black screen  that says "Reboot and select proper boot device", and the only thing I am able to boot is the Live USB version of Ubuntu. I would like to be able to access both the Ubuntu which I think I instaleld properly and the Windows 8 that I am hoping is still installed on my system. Please let me know if you can help. Thanks.

---

### Post by oldfred on 2014-04-02
Installing Ubuntu does not reset UEFI to boot ubuntu by default. You have to go into UEFI and choose to boot ubuntu entry. You may also have one time boot key to test if booting works.

Do not run the 'buggy' UEFI fix in Boot-Repair unless your computer is one of those where the vendor has modified UEFI to only boot Windows.  If you can boot ubuntu entry you do not need that fix. And if you have to have fix then you can only boot Windows from grub menu. 

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by pbcrow1 on 2014-04-03
Since my last post, I believe I may have fixed the problem. After posting, I kept trying to use boot-repair to fix the problem by changing some of the settings. It seems that by disabling secure install inside the boot-repair options and by checking the option "use standard EFI", the problem was fixed and on my next reboot I was able to access a GRUB menu (up until then the only grub menu I could access was the one for the Live-USB which would only show up when the USB was plugged in, otherwise I would get an error screen). From that GRUB menu, I have restarted/shutdown my computer a few times, it still comes up and I am able to access both my new Ubuntu installation and my old Windows 8 from this new GRUB menu. 

My only other question right now would be, is it possible that although it appears that everything is working now and it looks like the boot function is functional and stable, that it may revert and stop booting correctly again? If so, what can I do to prevent this? I ask because I'm not entirely positive *how* I fixed the problem, only that I was able to fix it by trial and error of adjusting the settings in boot-repair.

---

### Post by oldfred on 2014-04-03
Are you able to boot ubuntu entry from UEFI?
Are you only booting Windows from grub menu?

The issue is now with Windows updates, Windows has access to UEFI and resets itself to be first in boot order which you can easily change.

But if you ran 'buggy' UEFI fix, that has renamed the Windows efi file to really be grub/shim. So UEFI thinks it boots Windows but really boots grub. And on a Windows update it will install a new Windows efi file (overwriting the shim version), so then you cannot boot grub. You would then have to rerun Boot-Repair and its buggy UEFI fix.

---

### Post by pbcrow1 on 2014-04-03
When I start up my computer I go to a GRUB menu which has several options, two of which are labeled "Ubuntu" and "Windows Boot UEFI loader", from which I am able to boot Ubuntu and Windows, respectively. So far, this is the only way I'm booting either OS. Of the other options on the menu, there are two called "Windows UEFI bootmgfw.efi" and "Windows Boot Manager (UEFI on /dev/sda2)", but I haven't tried those yet. 

Would Windows updates eventually affect this type of GRUB menu? If so, is there a way that I can prevent this from happening, either by preventing all updates or ideally just by preventing the part of the updates that would affect the EFI file? Although the boot-repair fix seemed to work for me, I would prefer to avoid re-running it if what I did is known to be buggy.

---

### Post by oldfred on 2014-04-03
Need to know if you can boot from UEFI menu, not grub menu. UEFI is before grub loads. You may have to press a key to get into UEFI.

       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

I do not know any way to prevent Windows from doing its thing.

If it says bootmgfw.efi not bkpbootmgfw.efi, it seems you are booting ubuntu entry from UEFI. 
Boot-Repairs rename adds a copy of the original Windows efi file with bkp at beginning when it renames shim to be bootmgfw.efi.  

So you have a better UEFI that has not been modified by Vendor. You then should just have to go into UEFI and reset to make ubuntu default boot whenever Windows changes it to be Windows.

---

### Post by pbcrow1 on 2014-04-03
After some testing, it appears that before grub loads I can hit F12 to get to the boot menu, but I have only one option to choose from which is "UEFI: TOSHIBA MQ01ABD100", which then takes me to the grub menu. The option seems to be the same when I hit delete to go to the BIOS Utility area. Is this what you are referring to/is it a good thing? It does say bootmgfw.efi and not bkpbootmgfw.efi. If Windows makes a change, would I still be able to reset Ubuntu and/or the grub menu as a default as I am currently only seeing the one choice of "UEFI: TOSHIBA MQ01ABD100"?

---

### Post by oldfred on 2014-04-03
Post link to BootInfo report. As in post #2, just to be sure where everything is at.

---

### Post by pbcrow1 on 2014-04-05
The following is the link BootInfo report gave me: [http://paste.ubuntu.com/7209054/](http://paste.ubuntu.com/7209054/)

---

### Post by oldfred on 2014-04-05
It looks like you should be ok. Perhaps Boot-Repair has made a minor change and now has Windows booting thru a renamed bootx64.efi and not a renamed bootmfgw.efi file.

 BootOrder: 0004,0000,0001
Boot0000  Windows Boot Manager    Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001  ubuntu    Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)
Boot0004* UEFI: TOSHIBA MQ01ABD100

But you should not just see Toshiba entry, but both 0000 & 0001, the Windows & the ubuntu entries. I believe the * has something to do with which one's are active. But do not know how to activate the others.

Found this:
[http://linux.dell.com/efibootmgr/efibootmgr-0.5.4/efibootmgr.txt](http://linux.dell.com/efibootmgr/efibootmgr-0.5.4/efibootmgr.txt)
-a | --active         sets bootnum active
sudo efibootmgr -v
 
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

---

