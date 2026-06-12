---
title: "Screen Resolution - Simple Fix"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by iaculallad on 2008-05-25
Problem on Screen Resolution

You can use this newbie simple guide to fix your Screen Resolution when you are stucked on using <= 800x600. 
(Assuming that you had the correct video adapter driver installed, and still resolution is stucked).

*First thing to do is backup your /etc/X11/xorg.conf file.

**Code:**

> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak*After the backup, We will edit/replace some text on xorg.conf.

**Code:**

> sudo gedit /etc/X11/xorg.confWhich will pop the gedit windows with the xorg.conf file loaded and ready to be editted. 
Locate ONLY the "Screen" and "Monitor" section on your xorg.conf and replace some of the text inside the section. 

[COLOR="Blue"]Blue color text[/COLOR] are comments
[COLOR="Red"]Red color text[/COLOR] the the line of code to insert


**#------------For the "Monitor" section----------**
Section "Monitor" [COLOR="Blue"]#<-This remains [/COLOR]              
Identifier "Configured Monitor" [COLOR="Blue"]#<-This remains[/COLOR]
[COLOR="Red"]HorizSync 30-110[/COLOR] [COLOR="Blue"]#<-This is the text to insert on this section[/COLOR]
[COLOR="Red"]VertRefresh 50-160[/COLOR] [COLOR="Blue"]#<-This is the text to insert on this section[/COLOR]
[COLOR="Blue"]#<-Or if you already have the HorizSyc and VertRefresh, ignore this and 
#directly proceed to your "Screen" section[/COLOR]
EndSection
**#------------Snip-Snip-------------------**
[B]

#------------For the "Screen" section----------[/B]
Section "Screen" [COLOR="Blue"]#<-This remains [/COLOR]   
Identifier "Default Screen" [COLOR="Blue"]#<-This remains, for any configured Default Screen[/COLOR]
Monitor    "Configured Monitor" [COLOR="Blue"]#<-This remains, for any configured Monitor[/COLOR]
Device "Configured Video Device" [COLOR="Blue"]#<-This remains, for any configured Video Device[/COLOR]
[COLOR="Red"]DefaultDepth 24[/COLOR] [COLOR="Blue"]#<-Insert this if you do not have in in on this Section, Red text only[/COLOR]
[COLOR="Red"]SubSection "Display"[/COLOR] [COLOR="Blue"]#<-This is the text to insert on this section, Red text only[/COLOR]
[COLOR="Red"]Depth 24[/COLOR] [COLOR="Blue"]#<-This is the text to insert on this section, Red text only[/COLOR]
[COLOR="Red"]Modes "1280x1024"[/COLOR] [COLOR="Blue"]#<-This is the text to insert on this section, Red text only[/COLOR]
[COLOR="Red"]EndSubSection[/COLOR] [COLOR="Blue"]#<-This is the text to insert on this section, Red text only[/COLOR]
[COLOR="Blue"]#<------You can delete any text that follows below this line.[/COLOR]
EndSection
**#------------Snip-Snip-------------------**

---

### Post by diablo75 on 2008-05-25
Snip snip, indeed.  Great guide!

---

### Post by br3nd6n on 2009-04-20
For any other newbies wondering, I just tried this fix and it worked beautifully. After rebooting I had loads more resolution options. Brilliant.

Thank you very much iaculallad!!!!!! :D

---

### Post by MIKE SILVA on 2009-09-07
Hi,

Thanks for the post, but i still have a 640 x 480 resolution.

my xorg.conf is:

Section "Device"
Identifier "Configured Device"
Driver "vesa"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
HorizSync 30-110 
VertRefresh 50-160
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 16
SubSection "Display"
Depth 16
Modes "1024x768"
EndSubSection
EndSection 

(depth 24) is not possible.

My main problem is i want to use this computer without monitor.
If I have a monitor connected I don't need "vesa" and it works fine.

I have an intel 82845G/GL system.

Any ideias?

Thanks

---

