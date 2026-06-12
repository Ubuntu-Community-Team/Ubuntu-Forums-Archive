---
title: "Strange trouble in LiberOffice Writer with Ubuntu 15.04"
date: 2015-05-09
forum: New to Ubuntu
---

### Post by mla2 on 2015-05-09
_Dual boot Ubuntu 15.04 /  windows 7_
      
When I select  a bloc text in _Writer _using  _mouse_ or _shift+__arrow keys_  the entire OS freezes completely, and I have to shut down computer with power button or keys Atl+SysRq+B.

Then, I tried with a LiveCd 15.04 and same error ocurred when I selected text in Writer.
So, I check the same type “select text” in LibreOffice Writer in Windows and it works fine.
 What is the problem in Ubuntu?

Wired USB optical mouse and Keyboard

   New user Ubuntu

Thank you in advance

---

### Post by neu5eeCh on 2015-05-09
That sounds very strange. What version of LibreOffice are you using?

The following assumes the problem is with Libreoffice:

1.) Check the integrity of your LiveCD/Install Disk.
2.) If that checks out. Try reinstalling libreoffice. 

> sudo apt-get install --reinstall libreoffice

3.) Try installing the LibreOffice PPA for a later version (if you don't already have the latest version):

> sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update
sudo apt-get upgrade

If none of these work, then it's equally possible your problem doesn't originate with Libreoffice. Does selecting text cause a crash in any other application?

That said, I found similar issues reported here:

[http://askubuntu.com/questions/618276/ubuntu-15-04-libreoffice-crash](http://askubuntu.com/questions/618276/ubuntu-15-04-libreoffice-crash)
[http://askubuntu.com/questions/617829/libreoffice-doesnt-work-since-update-to-ubuntu-15-04](http://askubuntu.com/questions/617829/libreoffice-doesnt-work-since-update-to-ubuntu-15-04)
[http://askubuntu.com/questions/619829/libreoffice-crashes-on-startup-after-upgrade-to-ubuntu-15-04](http://askubuntu.com/questions/619829/libreoffice-crashes-on-startup-after-upgrade-to-ubuntu-15-04)

If it's a bug, then you're between a rock and a hard place. Is there a reason you want to use 15.04 rather than 14.04, for instance? If you can't think of a good reason, then use the LTS release.

---

### Post by grahammechanical on 2015-05-10
What video driver are you using? proprietary or open source?

I was using 15.04 all through its 26 week development period and part the way through I experienced the same problem. The next time it happens if you press Ctrl+Alt+F1 you might see some error messages about GPU lockup.

I found that I had to stop using Nouveau the open source video driver and use the proprietary video driver (Nvidia) instead.

Regards.

---

### Post by mla2 on 2015-05-10
Hi all
 
 
 Thank you
 
I reinstalled LibreOffice as you recommended.


libreoffice:


Instalado: 1:4.4.3~rc2-0ubuntu1~vivid1
 Candidato: 1:4.4.3~rc2-0ubuntu1~vivid1
 
 
 I checked with a new LiveCD/Install Disk 15.04  and the same error (entire OS freezes completely when I select text in Writer). Only in Writer this strange trouble occurred. Calc, Impress it's all ok.   
 Then I checked with a new LiveCD/Install Disk 14.04  and it works fine.
 
 
 In Windows, with LibreOffice version 4.4.3.2, all works ok.

---

### Post by mla2 on 2015-05-10
[COLOR=#000000]Hi [/COLOR] 
  [COLOR=#000000]**grahammechanical** [/COLOR] 
 
 
 [COLOR=#000000]I changed the defaut Ubuntu [/COLOR]**open source** video driver 
(Using[COLOR=#000000]X.Org X server &#8211; Nouveau display driver de xserver-xorg-video-nouveau[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000](open source)[/COLOR][COLOR=#000000] [/COLOR] 

 [COLOR=#000000]by this: [/COLOR] 
 [COLOR=#000000]([/COLOR][COLOR=#000000]Using NVIDIA binary driver &#8211; version 304.125 from nvidia-304 updates (proprietary)[/COLOR]

 [COLOR=#000000]And the &#8220;[/COLOR]_[COLOR=#000000]select [/COLOR]_[COLOR=#000000]_bug_&#8221; [/COLOR][COLOR=#000000]in Writer [/COLOR][COLOR=#000000]stoped, [/COLOR][COLOR=#000000]but  Boot login screen turned black instead violet.[/COLOR]

 [COLOR=#000000]
I have 5 options and don't know wich one is the correct i have to select. [/COLOR] 

 
[LIST]
[*] [COLOR=#000000]Using 	NVIDIA binary driver &#8211; version 340.76 from nvidia-340 	(proprietary, tested)[/COLOR]


[*] [COLOR=#000000]Using 	NVIDIA legacy binary driver &#8211; version 304.125 from nvidia-304 	(proprietary)[/COLOR]


[*] [COLOR=#000000]Using 	NVIDIA legacy binary driver &#8211; version 304.125 from nvidia-304 updates 	(proprietary)[/COLOR]


[*] [COLOR=#000000]Using 	NVIDIA binary driver &#8211; version 340.76 from nvidia-340 updates 	(proprietary)[/COLOR]

[*] [COLOR=#000000]Using 	[/COLOR][COLOR=#000000]X.Org 	X server &#8211; Nouveau display driver de xserver-xorg-video-nouveau[/COLOR][COLOR=#000000] 	[/COLOR][COLOR=#000000](open 	source)[/COLOR]
[/LIST]
 [COLOR=#000000]And [/COLOR] 

 [COLOR=#000000]Unknow:Unknow[/COLOR]

 
[LIST]
[*]  	[COLOR=#000000]Using 	Processor microcode firmware for AMD CPUs from amd-64 microcode 	(proprietary)[/COLOR]

[*] [COLOR=#000000]Do 	not use the device[/COLOR]
[/LIST]
 [U][COLOR=#000000]
Graphics:  GeForce 210/PCIe/SSE2[/COLOR][/U]

 [COLOR=#000000]
Thank you[/COLOR]

---

### Post by chinzudev on 2015-07-30
Hello ! 

Did you find the final solution with this problem? I have the same on all machines where I Installed 15.04 @ work.

---

### Post by jonathannb1973 on 2015-09-29
Hi thanks for your help
I used the following and it solved my problem:

[COLOR=#000000]Using NVIDIA binary driver – version 340.93 from nvidia-340 (proprietary, tested)[/COLOR]

---

### Post by Bucky Ball on 2015-09-29
> **chinzudev said:**
> Hello ! 

Did you find the final solution with this problem? I have the same on all machines where I Installed 15.04 @ work.

Welcome. The solution is in the posts above and below you! So the answer to your question is yes. Change from the open-source video driver.

If it doesn't work for you, to improve you chances of support, start a new thread with a descriptive title, please, rather than waking up this sleeping one. Thanks.

---

### Post by Rugaru345 on 2015-09-29
> **grahammechanical said:**
> What video driver are you using? proprietary or open source?

I was using 15.04 all through its 26 week development period and part the way through I experienced the same problem. The next time it happens if you press Ctrl+Alt+F1 you might see some error messages about GPU lockup.

I found that I had to stop using Nouveau the open source video driver and use the proprietary video driver (Nvidia) instead.

Regards.

I'm also having some random system hangs and odd graphics related issues with Ubuntu 15.04.  I'm assuming it's related to my graphics card which is an [COLOR=#000000]AMD Radeon R9 290 (rev 80) ). i'm using the proprietary AMD graphics accelerators from fglrx-updates and have a dual monitor setup on ubuntu 15.04. I tried this suggestion and when I did, both of my monitors went completely dark and I was unable to recover without a system reboot.

Thoughts?

Thanks! 
[/COLOR]

---

### Post by Bucky Ball on 2015-09-29
> **Rugaru345 said:**
> I'm also having some random system hangs and odd graphics related issues with Ubuntu 15.04.  I'm assuming it's related to my graphics card which is an [COLOR=#000000]AMD Radeon R9 290 (rev 80) ). i'm using the proprietary AMD graphics accelerators from fglrx-updates and have a dual monitor setup on ubuntu 15.04. I tried this suggestion and when I did, both of my monitors went completely dark and I was unable to recover without a system reboot.

Thoughts?

Thanks! 
[/COLOR]

Welcome. Please start a new thread. This one was firstly awoken from its slumber and is now getting off-topic, so 

*Thread closed.*

As this thread title and subject has nothing to do with your support request, to increase your chances of support, please start a new one with a descriptive title. Good luck. :)

---

