---
title: "[SOLVED] Sun xVM Aborted during VDI format."
date: 2008-10-29
forum: New to Ubuntu
---

### Post by toolfan2k4 on 2008-10-29
Hello all, I installed sun xvm to ease my transition to ubuntu and because my printer will not work with linux. When I attempt to install TinyXP the installer works fine until I get to the section where you format the VDI or hard drive it then hangs for a while after you choose format and eventually the screen closes and xVM says aborted for windows XP. Oh and I am on Hardy Haron...8.04.

---

### Post by charonred on 2008-10-29
Rather than using TinyXP, try installing your standard version of XP.

I have my XP Pro installed via xVM on Ubuntu 8.04.1 and it works fine; both XP and Vista run way faster in VirtualBox than they do as a native install - and make sure you install the 'add-ons' for VirtualBox.

At the moment I still need XP to run a couple of things that won't work in Linux, so I use XP just like another application - I can have both XP & Vista open at the same time in Ubuntu without bogging the system down.

---

### Post by toolfan2k4 on 2008-10-29
> **charonred said:**
> Rather than using TinyXP, try installing your standard version of XP.

I have my XP Pro installed via xVM on Ubuntu 8.04.1 and it works fine; both XP and Vista run way faster in VirtualBox than they do as a native install - and make sure you install the 'add-ons' for VirtualBox.

At the moment I still need XP to run a couple of things that won't work in Linux, so I use XP just like another application - I can have both XP & Vista open at the same time in Ubuntu without bogging the system down.

Ok sounds good I will give it a try. How do I install the extras?

---

### Post by charonred on 2008-10-29
Sorry it's 'guest additons', not add-ons.

But from memory they are included with the xVM install; once you have installed your OS into xVM and have it running, go to the menu across top of virtual machine >devices>install guest additions. 

Apart from enabling USB support, this will allow you to move your mouse from one desktop to another without additional keystrokes to release it from the hosted OS - you also then can use 'seamless' mode which blends your hosted OS desktop with the Ubuntu desktop (very cool).

I'm using xVM 1.6.4 and just found out that Sun have a new version 2.0 available for [download]("http://dlc.sun.com/virtualbox/vboxdownload.html#linux") - previous versions are [archived here]("http://dlc.sun.com/virtualbox/"). 
Also recommend downloading the [user manual]("http://dlc.sun.com/virtualbox/UserManual.pdf")

Also; if your printer won't work with Linux, but is detected, you may find that it will work fine in XP if you install in XP as a 'network printer' instead of a 'local printer' (this seems to get around any USB setup problems).

Note: Hosted OS's see Ubuntu as a networked computer, so you may have to also setup a folder in your Ubuntu 'Home' folder and give it share permissions, this will make it easier to move docs between hosted XP and Ubuntu. Version 2.0 xVM may work better or differently than 1.6.4, so you may need to fiddle with things a bit.

---

### Post by toolfan2k4 on 2008-10-29
I tried using a regular XP cd. It still does it. I am using xVM version 2.0.4. I have attached a screenshot if it helps. Maybe I should try and older version of xVM. Anymore ideas?

---

### Post by charonred on 2008-10-29
Hmmm, don't know if this will help;

Reboot and enable virtualisation in your PCs bios, then when you get xVM running, go to the xVM settings for your XP install and enable VT-x/AMD-V

I see in your CD/DVD-ROM that xVM is still trying to install from the TinyXP.iso, so you'll need to change that to the normal XP.iso

For functionality; you could probably increase the video from 8MB to 64MB or so (that's what I set it at), and I only use 768MB of system memory (XP just doesn't use as much resources in the virtual machine as it does natively).

---

### Post by toolfan2k4 on 2008-10-30
OK I figured it out. I downgraded to 2.0.2 that did not work. Then since you said 1.6.4 worked for you I downgraded to that version and it now works fine. Thanks for the help my friend.

---

### Post by 080729jk on 2008-10-30
b&#38647;&#35834;&#23572;&#33268;&#21147;&#20110;&#21644;&#35856;[**&#21464;&#39057;&#22120;**](http://www.renle.com/)&#20225;&#19994;&#30340;&#24314;&#35774;&#65292;&#33829;&#36896;&#24555;&#20048;&#21644;&#35856;&#30340;&#24037;&#20316;&#27675;&#22260;&#65292;&#21457;&#25381;&#21592;&#24037;&#30340;&#28508;&#33021;&#65292;&#35753;&#21592;&#24037;&#19982;&#20844;&#21496;&#20849;&#21516;&#25104;&#38271;&#12290;&#20844;&#21496;&#24314;&#31435;&#20102;&#23436;&#21892;&#30340;&#20445;&#38556;&#20307;&#31995;&#21644;&#20154;&#25165;&#22521;&#35757;&#21046;&#24230;&#65292;&#24320;&#23637;&#20016;&#23500;&#30340;&#25991;&#20307;&#23089;&#20048;&#27963;&#21160;&#65292;&#25226;&#20225;&#19994;&#21150;&#25104;&#23398;&#26657;&#65292;&#25226;&#20225;&#19994;&#21150;&#25104;&#23478;&#24237;&#65292;&#23558;&#21592;&#24037;&#33258;&#36523;&#30340;&#21457;&#23637;&#21644;&#20225;&#19994;&#30340;&#21457;&#23637;&#32039;&#23494;&#32852;&#31995;&#22312;&#19968;&#36215;&#65292;&#24555;&#20048;&#21644;&#35856;&#22320;&#21019;&#36896;&#31038;&#20250;&#20215;&#20540;&#12290;&#12288;&#12288;&#20808;&#36827;&#30340;&#31649;&#29702;&#27169;&#24335;&#20351;&#38647;&#35834;&#23572;&#36328;&#19978;&#20102;&#19968;&#20010;&#26032;&#30340;&#21457;&#23637;&#39640;&#24230;&#65292;&#26410;&#26469;&#30340;&#38647;&#35834;&#23572;&#23558;&#26356;&#21152;&#21160;&#21147;&#21313;&#36275;&#65292;&#24635;&#25237;&#36164;2.5&#20159;&#20803;&#30340;&#38647;&#35834;&#23572;&#26032;&#39640;&#31185;&#25216;&#20135;&#19994;&#22253;&#21306;&#24050;&#25300;&#22320;&#32780;&#36215;&#65292;&#26631;&#24535;&#30528;&#38647;&#35834;&#23572;&#20107;&#19994;&#24320;&#21019;&#20102;&#19968;&#20010;&#26032;&#30340;[**&#21464;&#39057;&#22120;**](http://www.renle.com/)&#21457;&#23637;&#32426;&#20803;&#65292;&#26397;&#30528;&#25104;&#20026;&#8220;&#31649;&#29702;&#31185;&#23398;&#21270;&#12289;[**&#21464;&#39057;&#22120;**](http://www.renle.com/)&#20135;&#19994;&#22810;&#20803;&#21270;&#12289;[**&#21464;&#39057;&#22120;**](http://www.renle.com/)&#32463;&#33829;&#35268;&#27169;&#21270;&#12289;&#21697;&#29260;&#22269;&#38469;&#21270;&#8221;&#30340;&#30334;&#24180;&#20225;&#19994;&#30340;&#23439;&#20255;&#30446;&#26631;&#22859;&#21147;&#21069;&#36827;&#65292;&#31177;&#25215;&#24320;&#25299;&#21019;&#26032;&#30340;&#20225;&#19994;&#31934;&#31070;&#65292;&#22312;&#20840;&#29699;&#32463;&#27982;&#19968;&#20307;&#21270;&#30340;&#22823;&#28526;&#20013;&#22868;&#28044;&#21521;&#21069;&#65292;&#25104;&#20026;&#20139;&#35465;&#20840;&#29699;&#30340;[**&#21464;&#39057;&#22120;**](http://www.renle.com/)&#30005;&#27668;&#19987;&#19994;&#20379;&#24212;&#21830;&#12290;

---

