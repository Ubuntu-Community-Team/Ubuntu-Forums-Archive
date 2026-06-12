---
title: "can't install Ubuntu"
date: 2014-01-16
forum: New to Ubuntu
---

### Post by aronq on 2014-01-16
I have always been a windows user, so please tell me exactly what to do and how to do. Thank you a lot!!!!

**Problem:** 

Can't install actually any operaing system, beacuse my laptop is very slowwwwwwwwww :( I can install windows but is then very slow. Thats why i just tried ubuntu... I downloaded the newes version today, and made a bootable usb -stick from my another windows computer. In the beginning got 3 failures... 

 [28.552075 ]bug: soft lockup cpu 0 stuck for 22s! [sweepper/0:1]
 [72.552078 ]bug: soft lockup cpu 1 stuck for 22s! [sweepper/0:1]
 [100.552106 ]bug: soft lockup cpu 1 stuck for 22s! [sweepper/0:1]
ata_id[291]: HDIO_GET_IdDENTITY failed for '/dev/sdb': Invalid argument

then its loading 
 and it comes to the screen where i can choose try ubuntu or install ubuntu...

when i try ubuntu, it works good so far. it sees my wifi connection, and recognize that its a convertible laptop, and recognize at first me stylus pen, awesome!!! but everything is still very slowwwwwww... 

when I click install, it gives me failure and stops :( so what should i do now! what would you say. I just want to have a fast laptop for the school. I think something doesnt work correctly with my cpu, bios, or chipset or stuff like that. but i am not a IT man. 

[SIZE=4]THANK YOU FOR YOUR HELP!!![/SIZE]


my Laptop has the following specs: 

HP Compaq 2710p


[TABLE]
[TR="bgcolor: #FFFFFF"]
[TD]Processor[/TD]
[TD][B][SIZE=2]Intel® Core™2 Duo Processor U7600 
(2M Cache, 1.20 GHz, 533 MHz FSB) Socket P[/SIZE][/B][/TD]
[/TR]
[TR="bgcolor: #E7E7E7"]
[TD="width: 140"]Compatible Operating Systems[/TD]
[TD="width: 401"][Genuine]("http://welcome.hp-ww.com/country/ca/en/mda/genuine_landing.html") Windows Vista® Enterprise, [Genuine]("http://welcome.hp-ww.com/country/ca/en/mda/genuine_landing.html") Windows 2000, SuSe Linux Enterprise Desktop 10 (certified)[/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD="width: 140"]Chipset[/TD]
[TD="width: 401"]Mobile™ Intel® GM965[/TD]
[/TR]
[TR="bgcolor: #E7E7E7"]
[TD="width: 140"]Standard memory[/TD]
[TD="width: 401"]1024 MB (1 x 1024 MB)[COLOR=#ff0000]**I Have 4 GB!!!!!!!!!**[/COLOR][/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD="width: 140"]Memory Upgrade[/TD]
[TD="width: 401"]Upgradeable to 4096 MB maximum[/TD]
[/TR]
[TR="bgcolor: #E7E7E7"]
[TD="width: 140"]Memory slots[/TD]
[TD="width: 401"]2 SODIMM slots supporting dual channel memory[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR="class: theme"]
[TH="class: small, colspan: 2"]Graphic / Audio[/TH]
[/TR]
[TR="bgcolor: #E7E7E7"]
[TD]Graphic Subsystem Name[/TD]
[TD]Mobile Intel® Graphics Media Accelerator X3100[/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD="width: 140"]Graphic Subsystem Video Card Memory[/TD]
[TD="width: 401"]Up to 384 MB shared system memory[/TD]
[/TR]
[/TABLE]

---

### Post by joachim_altmann on 2014-01-16
Hi,
I found some posts referring the [COLOR=#0000ff]*soft lockup stuck for 22s*[/COLOR] error to a problem in the kernel
[https://bbs.archlinux.org/viewtopic.php?pid=1359951](https://bbs.archlinux.org/viewtopic.php?pid=1359951)
[http://www.linuxquestions.org/questions/linux-kernel-70/bug-soft-lockup-during-boot-902565/](http://www.linuxquestions.org/questions/linux-kernel-70/bug-soft-lockup-during-boot-902565/)
while the other one, the HDIO_GET_IDENTITY one mayhave to do with an external usb device
[http://askubuntu.com/questions/103065/why-do-i-get-hdio-get-identity-failed-message-when-booting-with-external-usb-h](http://askubuntu.com/questions/103065/why-do-i-get-hdio-get-identity-failed-message-when-booting-with-external-usb-h)

To get rid of the first one, you may try a different kernel version, i.e. a different version / earlier of ubuntu. Maybe it works. Which version of ubuntu did you try to install?

---

### Post by silvervulpus on 2014-01-16
for the specs of your hardware, ubuntu 12.4 will run, but very slowly and it will bug quite alot. i recommend the XFCE or Xubuntu flavour, or if you dont want to do that, try puppy linux, crunchbag linux, or damn small linux. all of those would be better suited to your hardware opposed to ubuntu. like i said, if you still want the ubuntu features, understand the gnome desktop will be slow and buggy on your hardware, go with Xubuntu or XFCE. now after you have chosen your distro, on your second computer where you are making the bootable flashdrive. download and install unetbootin.exe. you can get it at [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)   once its installed, run the unetbootin.exe at the top, (pictures and instructions are on download page but i will type them anyway) click the first drop down menu and select what disribution you want, then in the second drop down select what version of the distribution you want. at the bottom there is one last drop down menu to handle.make sure you select the proper drive (F: or H: or M: or T: or whatever label is on your flashdrive) then select start. it will download the distributions .isofile for you and auto extract and install it to your flashdrive for you. once all that is done, simply plug you flashdrive into the computer you want to install it on, boot the flashdrive from the bios, and install and enjoy!. hope this helps!

---

### Post by QIII on 2014-01-16
I have edited your thread title.

Please take care with all caps and exclamation points.  This is seen as yelling.  Rather than causing people to be quicker to help, it may be off-putting.

---

### Post by silvervulpus on 2014-01-16
i misread your specs slightly, i rescind the idea of it running slowly or buggy because of your processor, but i still dont know if your graphics card or GPU will handle the gnome environment, and would still recommend XFCE/Xubuntu. but dont worry about damn small linux, or puppy, or crunchbag, my bad. XFCE/Xubuntu 12.4 should work great. also make sure that your installing the 64Bit. not the 32. if you try to install 32 you will have errors. check it out. [http://ark.intel.com/products/29764/Intel-Core2-Duo-Processor-U7600-2M-Cache-1_20-GHz-533-MHz-FSB-Socket-P](http://ark.intel.com/products/29764/Intel-Core2-Duo-Processor-U7600-2M-Cache-1_20-GHz-533-MHz-FSB-Socket-P) ...... says on this link that your processor requires a 64bit instruction set!

---

### Post by aronq on 2014-01-20
Thank you very much for your help. I have installed xubuntu 12.4 and it works. I still have one problem. When i use my laptop from Battery than my CPU 8% and when i plug in AC then 50% and everything is soooooooo slow. does anybody have any idea?

---

