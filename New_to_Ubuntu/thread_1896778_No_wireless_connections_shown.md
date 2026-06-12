---
title: "No wireless connections shown"
date: 2011-12-17
forum: New to Ubuntu
---

### Post by Sirfloatsalot1 on 2011-12-17
I co-installed Ubuntu 11.04 (yesterday) with my Windows XP Pro SP3.  No problems seeing my wireless or connecting to the Internet with XP, but with Ubuntu, nothing shows up on the wireless screen.  I read one of the forum posts and they though 10.04 might be more reliable, so I tried that too - no wireless locations. Wireless is enabled. Any suggestions?  Thanks!

---

### Post by LinuxFan999 on 2011-12-17
What are the specifications of your computer?

---

### Post by wildmanne39 on 2011-12-17
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Sirfloatsalot1 on 2011-12-19
Sorry, but it took me a while to figure out the "cut and paste", but here's the responses in a line-by-line format.

gx520@gx520-OptiPlex-GX520:~$ cat /etc/lsb-release; uname -a  
 DISTRIB_ID=Ubuntu  
 DISTRIB_RELEASE=11.10  
 DISTRIB_CODENAME=oneiric  
 DISTRIB_DESCRIPTION="Ubuntu 11.10" 
 Linux gx520-OptiPlex-GX520 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux  
 

gx520@gx520-OptiPlex-GX520:~$ lspci -nnk | grep -iA2 net 

(no apparent response to this command)

 

gx520@gx520-OptiPlex-GX520:~$ iwconfig  
 lo        no wireless extensions.  
 

gx520@gx520-OptiPlex-GX520:~$ rfkill list all  
 0: hci0: Bluetooth  
 	Soft blocked: no  
 	Hard blocked: no  
 

gx520@gx520-OptiPlex-GX520:~$ lsmod  
 Module                  Size  Used by  
 nls_iso8859_1          12617  1  
 nls_cp437              12751  1  
 vfat                   17308  1  
 fat                    55577  1 vfat  
 bnep                   17923  2  
 rfcomm                 38408  8  
 ppdev                  12849  0  
 snd_intel8x0           33318  2  
 snd_ac97_codec        106082  1 snd_intel8x0  
 ac97_bus               12642  1 snd_ac97_codec  
 dcdbas                 14098  0  
 snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec  
 snd_seq_midi           13132  0  
 snd_rawmidi            25241  1 snd_seq_midi  
 

Makes perfect sense to me!

---

### Post by joelgeez on 2011-12-19
I just had a similar experience. I spent all day diagnosing, going to forums, screaming at the computer.
 
Turns out I had accidentally turned off the wireless switch. Not saying you would do that. Just saying that's what happened to me.
J

---

### Post by wildmanne39 on 2011-12-19
Hi, is your card an internal card? that command should have produced some out.

Also the lsmod information is very short are you sure that is all of it?
Thanks

---

### Post by Sirfloatsalot1 on 2011-12-19
Here's the whole lsmod - sorry about that.  As far as a card, I don't know what that means.  I use a USB "antenna" to get the signal from my wireless.  There's no expansion card for it.  


gx520@gx520-OptiPlex-GX520:~$ lsmod  
 Module                  Size  Used by  
 nls_iso8859_1          12617  1  
 nls_cp437              12751  1  
 vfat                   17308  1  
 fat                    55577  1 vfat  
 bnep                   17923  2  
 rfcomm                 38408  8  
 ppdev                  12849  0  
 snd_intel8x0           33318  2  
 snd_ac97_codec        106082  1 snd_intel8x0  
 ac97_bus               12642  1 snd_ac97_codec  
 dcdbas                 14098  0  
 snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec  
 snd_seq_midi           13132  0  
 snd_rawmidi            25241  1 snd_seq_midi  
 snd_seq_midi_event     14475  1 snd_seq_midi  
 snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event  
 i915                  505108  3  
 snd_timer              28932  2 snd_pcm,snd_seq  
 btusb                  18160  2  
 snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq  
 bluetooth             148839  23 bnep,rfcomm,btusb  
 snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 psmouse                73673  0  
 serio_raw              12990  0  
 drm_kms_helper         32889  1 i915  
 drm                   192226  4 i915,drm_kms_helper  
 soundcore              12600  1 snd  
 binfmt_misc            17292  1  
 parport_pc             32114  1  
 snd_page_alloc         14115  2 snd_intel8x0,snd_pcm  
 i2c_algo_bit           13199  1 i915  
 video                  18908  1 i915  
 lp                     17455  0  
 parport                40930  3 ppdev,parport_pc,lp  
 usb_storage            44173  1  
 uas                    17699  0  
 usbhid                 41905  0  
 hid                    77367  1 usbhid

---

### Post by wildmanne39 on 2011-12-19
Hi, please post the results of:
```
lsusb
```
Thanks

---

### Post by Sirfloatsalot1 on 2011-12-20
gx520@gx520-OptiPlex-GX520:~$ lsusb  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 002: ID 090c:1000 Feiya Technology Corp. Flash Drive  
 Bus 001 Device 005: ID 13b1:002f Linksys AE1000 v1 802.11n [Ralink RT2870]  
 Bus 002 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)  
 Bus 003 Device 002: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard  
 Bus 004 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse  
 Bus 002 Device 003: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)  
 Bus 002 Device 004: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)  
 Bus 002 Device 005: ID 0a5c:2148 Broadcom Corp.  
 gx520@gx520-OptiPlex-GX520:~$

---

### Post by mavenuparker on 2011-12-20
did you install all the drivers shown in 'Additional Drivers'?

Im not a pro but check once in case you forgot to install the wireless drivers 

Good luck

---

### Post by Sirfloatsalot1 on 2011-12-20
The wireless works fine with my "current" OS (Win XP SP3), but not when I boot with the "dual-installed" Ubuntu.  I boot in Windows to get to this forum.

---

### Post by Sirfloatsalot1 on 2011-12-20
The wireless works fine with my "current" OS (Win XP SP3), but not when I boot with the "dual-installed" Ubuntu.  I boot in Windows to get to this forum.

---

### Post by wildmanne39 on 2011-12-20
Hi, you need to go to the following link:
[http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)
Now download RT3572USB driver and follow the directions on this page very carefully.
[http://ubuntuforums.org/showthread.php?t=1630358](http://ubuntuforums.org/showthread.php?t=1630358)
Thanks

---

### Post by Sirfloatsalot1 on 2011-12-25
Went to the site and downloaded the file.  Extracted it using 7-Zip to get the 2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO folder.  But when I tried to edit the \os\linix\config.mk file, "command prompt" showed that it was empty.  Under Windows Explorer, it shows:

config.mk   20 KB  MK File    4/26/2011  6:22 PM


Am I at least in the right place?

Why is this so difficult?  Is my wireless missing a driver?  

I am not a computer ace, so all of this seems waaaaay to difficult.  Maybe I'm not cut out for Linix, because this is confusing as .....!? :confused: (But I do appreciate your time with me on this)!

---

### Post by wildmanne39 on 2011-12-25
Hi, yes your wireless is missing a driver that is what you are trying to install.

When you extract it follow the directions to right click and extract here.

Did you do this inside ubuntu? the reason I ask is you said > "command prompt" showed that it was empty. Under Windows Explorer, it shows:

config.mk 20 KB MK File 4/26/2011 6:22 PMthere is no windows explorer in ubuntu and you do all this in the ubuntu terminal which can be opened by hitting ctrl+alt+t.
Thanks

---

### Post by Sirfloatsalot1 on 2011-12-28
OK, so I did this in Ubuntu Terminal this time and I should be right here, according to your directions.
  "By default, downloads go to a directory called Downloads. Open it and 
right-click the file and select 'Extract here.' Open the 
2010_0915_RT3572_Linux_STA_v2.4.0.2 folder and then navigate to 
os/linux/config.mk and change 'HAS_WPA_SUPPLICANT=y' and 
'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. Change them from =n to =y. 
Proofread, save and close the text editor."   SUCCESSFUL WITH THIS PORTION - modified and saved the two files.


"Next, edit /include/os/linux_rt.h to change the two functions 
usb_buffer_alloc and usb_buffer_free to be renamed to usb_alloc_coherent
and usb_free_coherent, respectively. DO NOT replace the instances 
of rausb_buffer_alloc and rausb_free_coherent. Proofread, save and 
close the text editor." 
MY VERSION (the only one available from the website to download - 
2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO) doesn't have a file 
named /include/os/linux_rt.h.  It has the following: rt_drv.h rt_linux.h rt_linux_cmm.h rt_os.h  The closest file - rt_linux.h does not have either of the usb_buffer 
functions (alloc and free).  Ideas?  Onward through the fog!

---

### Post by wildmanne39 on 2011-12-28
Hi, here is a link to the driver it is the third one down 3572usb.
[http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)

You got to get rid of the driver you tried to install like this go into the directory of the driver and run these commands please:
```
make clean
make
sudo make uninstall
sudo depmod -a
sudo update-initramfs -u
```
Here is a link start at post 74 it is dealing with the new driver for the newer version of ubuntu.
[http://ubuntuforums.org/showthread.php?t=1630358&page=8](http://ubuntuforums.org/showthread.php?t=1630358&page=8)
Thanks

---

### Post by Sirfloatsalot1 on 2011-12-29
"Go to the directory of the driver" - what does this mean?  I assume I'm in Ubuntu Terminal - then what?

(Can you tell I'm a newbie)?

Also, am I going to have to do this for all of my peripherals (printer, external DVD, ....).  Is there a generic driver download area for Ubuntu and how do I know if I'm going to have to do this for something else?

---

### Post by wildmanne39 on 2011-12-29
Hi, yes you go into the directory of the driver you tried to install in the terminal, then you run the commands one line at a time in my previous post to get rid of that driver and follow the rest of the directions.
Thanks

---

### Post by Sirfloatsalot1 on 2011-12-30
I got down to step 4 with no problem, then:
 [SIZE=3]4.)[/SIZE]
 [INDENT]Navigate to: 
[COLOR=#c0c0c0]yourname[/COLOR]/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO/common/os

And open:
[COLOR=#0000ff]rt_linux.h[/COLOR][/INDENT] [INDENT][B]

No such file in \common\os, but found it in \include\os.  Made the changes and saved it.

[/B]
[/INDENT]  [INDENT] Step 6.[/INDENT] I get to :  [email]gx520@gx520-OptiPlex-GX520:~/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO[/email]$   [INDENT] I run “make” and it crunches a bunch of stuff, but when I try to do suco make install, it asks for a password. I don't have a password!?
[/INDENT]  [INDENT] [email]gx520@gx520-OptiPlex-GX520:~/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO[/email]$ sudo make install  [/INDENT] [INDENT] [sudo] password for gx520:  [/INDENT] [INDENT] Sorry, try again.  [/INDENT] [INDENT] [sudo] password for gx520:  [/INDENT] [INDENT] Sorry, try again.  [/INDENT] [INDENT] [sudo] password for gx520:  [/INDENT] [INDENT] Sorry, try again.  [/INDENT] [INDENT] sudo: 3 incorrect password attempts  [/INDENT] [INDENT] [email]gx520@gx520-OptiPlex-GX520:~/Downloads/2011_0427_RT3572_Linux_STA_v2.5.0.0.DPO[/email]$[/INDENT]  [INDENT] I don't use a password to get into Ubuntu and it won't let me type anything in (keyboard entries don't show up on the screen).  I just hit the Enter key when the screen comes up (but Terminal doesn't like that – it lists 3 incorrect password attempts and boots me back to   [EMAIL="gx520@gx520-OptiPlex"]gx520@gx520-OptiPlex[/EMAIL][/INDENT] [INDENT] Next?[/INDENT]

---

### Post by wildmanne39 on 2011-12-30
Hi, you do not have a user password? if not you will have to make one, here is a link.
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
Thanks

---

### Post by chipbuster on 2011-12-30
Just so you know, when you're in command prompt, any passwords you type will not show up on the screen, even as stars (*) or dots. This is a security feature in most UNIX systems.

---

### Post by Sirfloatsalot1 on 2011-12-31
Seemed to be going well up to entering the new password twice and typing exit.  The message came back :   Authentication Token manipulation error

---

### Post by wildmanne39 on 2011-12-31
Hi, I googled this there is many sites about this message it is caused by a few things, I suspect you may have entered the second password wrong.
[http://mohammednv.wordpress.com/2008/01/08/authentication-token-manipulation-error-when-changing-user-passwords-in-linux/](http://mohammednv.wordpress.com/2008/01/08/authentication-token-manipulation-error-when-changing-user-passwords-in-linux/)
If you need more help google the error message. Also you can start a thread with that issue as the title.
Thanks

---

### Post by Sirfloatsalot1 on 2012-01-02
I Googled it too and tried a couple of things, but nothing seemed to work.  This is the third time I've tried to get Ubuntu working over the past two years.  Obviously, I'm not a techie, but this is just waaaaay too hard.  Guess it's back to Microsoft (rats)!

I DO thank you for your time and effort, and wish you well in 2012!  Thanks again.

---

### Post by wildmanne39 on 2012-01-02
Hi, your welcome! we will be here when you are ready to try again.
Thanks

---

