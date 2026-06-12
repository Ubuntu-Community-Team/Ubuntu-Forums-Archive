---
title: "External monitor not showing video and mouse pointer messed up"
date: 2012-08-14
forum: New to Ubuntu
---

### Post by Herby Pepper on 2012-08-14
Pointer looks and work fine on laptop but when I connect external monitor it appears there as a shaking, square shape. Videos are not showing either.

my laptop hp 2133: 
Graphic card: VIA Technologies, Inc. CN896/VN896/P4M900, Chrome 9 HC. 
System: Lubuntu 12.04

I think it is graphic problem but can't find drivers for my card and system. I do have xserver-xorg-video-openchrome and disper installed.
I did not have that problem with Lubuntu 11.10.

Any ideas? thanks

---

### Post by Herby Pepper on 2012-09-17
I was able to get a nice pointer:
 

 Since now Lubuntu/Ubuntu does not have xorg.conf file I generated it (1) and then modify it to look like the one from Debian website (2) ([http://wiki.debian.org/InstallingDebianOn/HP/HP2133](http://wiki.debian.org/InstallingDebianOn/HP/HP2133) )
 

 1) generate xorg.conf:
 

 press Ctrl+Alt+F1   (to switch to text terminal)
 

 Login
 

 sudo service lightdm stop  (to stop desktop environment)
 

 sudo xorg -configure  (to configure xorg.conf, it will put the file in your home direction)  
 

 sudo cp home/username/xorg.conf.new /etc/X11/xorg.conf (in username put your user name)  (to copy created file to the location that system will recognise and use it)
 

 sudo service lightdm start   (to start desktop environment)
 

 

 2) modify xorg.conf:
 

 go to [http://wiki.debian.org/InstallingDebianOn/HP/HP2133](http://wiki.debian.org/InstallingDebianOn/HP/HP2133) in section Resources Attachments there is xorg.conf file contents, select and copy it. (Ctrl+C copy selected)
 

 Open terminal  
 

 sudo leafpad /etc/X11/xorg.conf    (to open xorg.conf for modification)
 

 Ctrl+A  (to select all)
 

 Delate   (to delele selected)
 

 Ctrl+V    (to past copied earlier file)
 

 Save and close file.
 

 Restart computer.

---

### Post by impula on 2012-11-08
> **Herby Pepper said:**
> Pointer looks and work fine on laptop but when I connect external monitor it appears there as a shaking, square shape. Videos are not showing either.

my laptop hp 2133: 
Graphic card: VIA Technologies, Inc. CN896/VN896/P4M900, Chrome 9 HC. 
System: Lubuntu 12.04

I think it is graphic problem but can't find drivers for my card and system. I do have xserver-xorg-video-openchrome and disper installed.
I did not have that problem with Lubuntu 11.10.

Any ideas? thanks

Hello! I have just installed lubuntu 11.10, I'm glad to hear that you managed to get it work with external monitor! My problem is, that it doenst show external monitor at all in monitor settings ( ( monitor is eizo 2331). it doesnt show it monitor settins (LXrandR 0.1.2) when i plug in.monitor is also not responding in any way. and monitor works perfect on pc.  Could you please help me how to do it? i have hp 2133. I am new to this ubuntu, so could you please be specific in your answer? I know how to open terminal, but thats all. So step by step instructions if possible! Thank you very much, i would really appreciate any help! :) Have a nice day! -impula

---

