---
title: "Dual system but directly boot into windows"
date: 2016-06-18
forum: New to Ubuntu
---

### Post by qq52184962 on 2016-06-18
Hello, I have a Sony vaio pro 13 computer. And I made a partition of my disk for ubuntu installation. However, it seems that my computer ignore GRUB and directly boot in Windows 10. I have already tried **boot repair**, and it didn't work. I installed both windows and ubuntu in **UEFI** mode. And I did some research and found some people suggested to do BCDedit in windows like this: [B][COLOR=#000000][FONT=&amp]bcdedit /set "{bootmgr}" path \EFI\ubuntu\shimx64.efi
[/FONT][/COLOR][/B]And the result was a tragedy. I can't boot into both ubuntu and windows. And after that I spent much time recovering my windows system and reinstalling my ubuntu. But still I can't boot with GRUB. Is there any help for me to boot with GRUB? Please give me a guide with detail since I am really new to ubuntu. I appreciate for helps.
BTW, openBSD wouldn't help because it only work with legacy mode.

---

### Post by ajgreeny on 2016-06-18
Run boot-repair again but this time do not use the default repair but run the Boot-info-script.  That will give you a report with a pastebin link which we can use to read the report and hopefully see what went wrong.

---

### Post by qq52184962 on 2016-06-19
[http://paste2.org/XXhKy9Hh](http://paste2.org/XXhKy9Hh)
Here is a link of my boot status after using boot repair.

---

### Post by Karl_Hungus on 2016-06-21
Change the boot-order in the bios, that should solve your issue. What bootloader are you using? anything at all or just hittin it raw dog?

---

### Post by qq52184962 on 2016-06-21
The problem is for Sony, the BIOS have only few changeable options. In terms of boot order, I can only choose either internal storage or external storage. I use Linux GRUB, but the prob is it never executes. My laptop just bypass GRUB and directly go into windows boot loader.

---

### Post by oldfred on 2016-06-21
Sony is hard coded in UEFI to only boot by description and only valid description is "Window Boot Loader". That is not allowed per UEFI. But since now others also do it, I assume Microsoft gives a discount if you make it difficult for anything other than Windows.

All systems do boot a fallback or hard drive boot entry or /EFI/Boot/bootx64.efi. That is how all external drives/installers work, but you can use that on internal drive also. You probably never will be able to actually boot the ubuntu entry in UEFI.

       
 Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI.
'Use the standard EFI file' in advanced options. 

You can see if Boot-Repair did this already if bootx64.efi file size matches shimx64.efi or Windows's bootmgfw.efi.

You do not now show a UEFI: hard drive or similar entry in UEFI. But you may want to turn off Secure Boot.

       Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair) 
    
              Sony Vaio Pro 13 - To get into  UEFI press this "Assist" button BEFORE starting
[http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio](http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio)
[URL="http://askubuntu.com/questions/644901/booting-a-sony-vaio-computer-running-windows-8-1-in-ubuntu-from-a-usb-drive"]http://askubuntu.com/questions/644901/booting-a-sony-vaio-computer-running-windows-8-1-in-ubuntu-from-a-usb-drive
[/URL]
 One Sony user, dual booting, and boot hard drive UEFI entry, not ubuntu
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi ) 

[URL="http://askubuntu.com/questions/644901/booting-a-sony-vaio-computer-running-windows-8-1-in-ubuntu-from-a-usb-drive"]
[/URL]

---

### Post by qq52184962 on 2016-06-23
I copy [COLOR=#000000][I]shimx64.efi to \EFI\Boot\ folder and change its name to bootx64.efi (Replace the original file). But still it directly go into windows 10. And also I change the boot order create a hard drive boot but still didn't work. 
[/I][/COLOR][IMG]https://scontent-tpe1-1.xx.fbcdn.net/v/t34.0-12/13535896_1047666298647335_1435573832_n.jpg?oh=54435c88a6b015837359b43f3a362ea4&oe=576E5075[/IMG]

---

### Post by qq52184962 on 2016-06-23
And also, my laptop seems have a magic that can change boot order automatically back after reboot. SO i still can only boot into Windows 10.
[IMG]https://scontent-tpe1-1.xx.fbcdn.net/v/t35.0-12/13524060_1047671101980188_1260252387_o.jpg?oh=901bb1b2ae01eb091b1bd541e7236362&oe=576E1A9F[/IMG]

---

### Post by oldfred on 2016-06-23
Please copy & paste terminal output, do not use screen shots. If longer terminal output or text files, use code tags.  You can easily add code tags with Forum's advanced editor and the # icon.
Also if attaching screenshots using the paperclip icon. Do not post in line as not everyone has high speed Internet.

That magic could be Windows.

It is my understanding that Windows does some sync between UEFI's NVRAM and Windows BCD. It then may be changing things.
But I also thought it only did that when you did maintenance or updates in Windows. 
But I do not have Windows that is use as dual boot regularly, so now sure of details.

---

