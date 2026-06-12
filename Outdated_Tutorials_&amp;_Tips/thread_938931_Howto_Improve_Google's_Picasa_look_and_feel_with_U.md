---
title: "Howto: Improve Google's Picasa look and feel with Ubuntu"
date: 2008-10-05
forum: Outdated Tutorials &amp; Tips
---

### Post by azza85 on 2008-10-05
Hi all!

I have no idea whether this will help anyone or not, but I have decided to write a very short howto because I feel like my little tip may improve some peoples experience with Picasa on Ubuntu. I wrote this because I was not happy with the default look of Picasa, some parts of the program were very pretty and other parts like the menu bar are very ugly in my opinion.  This howto will show you how to fix that so your menu goes from the default (left) to the image on the right :)

[IMG]http://i287.photobucket.com/albums/ll146/arandall85/menu.png[/IMG]

First of all, if you are interested in trying out Picasa for linux, download the beta version of Picasa in .deb form here...

i386 users: [http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_i386.deb]("http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_i386.deb")
amd64 users: [http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_amd64.deb]("http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_amd64.deb")


Once installed, run Picasa (I found it in "Applications"->"Other"->"Picasa").

You will see the menu bar looks different to the rest of your Ubuntu theme.  To fix this, do the following:

1. Close any running instances of Picasa

2. Press alt+F2 to get a run command, and type "gedit ~/.google/picasa/3.0/user.reg"

3. In the text file, look for the line starting with "[Control Panel\\Colors]"... it should be about 4 lines down.  Underneath this line, copy and paste the following:

"ActiveBorder"="234 229 224"
"ActiveTitle"="188 121 79"
"AppWorkspace"="128 128 128"
"Background"="85 56 40"
"ButtonAlternateFace"="181 181 181"
"ButtonDkShadow"="92 92 92"
"ButtonFace"="239 235 231"
"ButtonHilight"="252 251 250"
"ButtonLight"="241 239 226"
"ButtonShadow"="219 211 203"
"ButtonText"="0 0 0"
"GradientActiveTitle"="188 121 79"
"GradientInActiveTitle"="239 235 231"
"GrayText"="181 179 172"
"Hilight"="246 198 125"
"HilightText"="0 0 2"
"HotTrackingColor"="201 127 85"
"InActiveBorder"="212 208 200"
"InActiveTitle"="239 235 231"
"InActiveTitleText"="83 82 80"
"InfoText"="0 0 0"
"InfoWindow"="255 241 190"
"Menu"="232 232 232"
"MenuBar"="188 121 79"
"MenuHilight"="230 223 217"
"MenuText"="0 0 0"
"Scrollbar"="212 208 200"
"TitleText"="255 255 255"
"Window"="255 255 255"
"WindowFrame"="0 0 0"
"WindowText"="0 0 0"

4. Now save and close this file.

5. Go to "Applications"->"Other"->"Picasa Font Settings".  Select the "Menu Font" tab.  Change the Menu Font to "Bitstream Vera Sans", and the menu Font Size to "12".  Click "Ok".

Now when you open Picasa, you should see that the menu bar is much prettier!

I hope this helps someone :)

---

### Post by w00dsy on 2008-11-10
terrific tip, thanks. One thing, my fonts on the right side, the screensaver, web albums, sign out etc are barely readable. Any idea on how to adjust that part?

---

### Post by edmondt on 2008-11-10
YAY! Looking so pretty :)

---

### Post by binbash on 2008-11-10
good one!!

---

### Post by azza85 on 2008-11-10
Hi W00dsy,

No unfortunately I haven't found a setting to change the annoying little URL's...

Maybe someone with more experience in Wine will be able to help us.

Regards

---

### Post by pasti on 2008-11-13
thankyou very much azza85

those default fonts have been bugging me since I installed intrepid, a week ago

Cheers:KS

---

### Post by unique on 2008-11-13
Great work! looks much better!  Thanks alot man!

---

### Post by ericesque on 2008-11-13
very nice!  Too bad Google hasn't allowed us to select the gtk look-n-feel.  I thought Picasa was java based-- and java will let you do that.  I'll wait for someone to correct me though.

---

### Post by binbash on 2008-11-14
> **ericesque said:**
> very nice!  Too bad Google hasn't allowed us to select the gtk look-n-feel.  I thought Picasa was java based-- and java will let you do that.  I'll wait for someone to correct me though.

It is using wine.Yah it is not native.

---

### Post by Tom.Servo on 2008-11-14
Great info! Thanks!

---

### Post by Vadi on 2008-11-22
This hasn't quite worked for me. Picasa window did not appear this time (nor in the system tray). It is scanning everything however...

---

### Post by Martje_001 on 2008-11-22
Also add a link for us, AMD64 users:

[http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_amd64.deb](http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_amd64.deb)

Very good job nevertheless!

---

### Post by azza85 on 2008-11-23
Done! :)

---

### Post by azza85 on 2008-11-23
Vadi you still having trouble?  I'm not sure I understand quite what the issue is... did Picasa use to show and now after following my instructions doesn't?  Or has it never displayed?

Maybe after the initial scan is complete the Picasa window will show.  Let me know how it goes.

Regards

---

### Post by Vadi on 2008-11-23
Ah I found it. It decided to run away to another cube edget after starting...

---

### Post by Arup on 2009-01-09
Thank you, a nice tip for Picasa users which includes myself.

---

### Post by J0nD33 on 2009-01-12
The edits indicated by azza85 fixed most of the font problems, but there are several places where the default fonts were still scrambled.  For example, the choices at the upper right where the sign in/out choice appears were trashed.  Likewise, the fonts used by sub-menus were all hamburger was well.  Worse, the display in Picasa Font Settings was also a mess.  The cure here is to open the "user.reg" as indicated by azza85 and make the edits suggested.  THEN search for a line near the end of the file which reads "[Software\\Wine\\Fonts\\Replacements] 1212988404", below that are three font equivalence assignments.  You want to edit the line that reads "Tahoma"="DejaVu Sans" to ""Tahoma"="Bitstream Vera Sans".  This should unscramble the remaining problem font problems, or at least it did for me.  Ironically, it also straightened the problems in the Picasa Font Settings display as well.

Good luck

---

### Post by bootch42 on 2009-05-09
Hope someone can help I'm a newb with ubuntu. 
  After opening the run command then i type "gedit ~/.google/picasa/3.0/user.reg" into it. It only comes up with a blank text editor. I know its supposed to edit the settings of picasa but its not. I don't know what the problem could be. I tried substituting 2.7 for 3.0 because i dont have 3.0, that didn't help. Any help would be greatly appreciated.

---

### Post by azza85 on 2009-05-09
> **bootch42 said:**
> Hope someone can help I'm a newb with ubuntu. 
  After opening the run command then i type "gedit ~/.google/picasa/3.0/user.reg" into it. It only comes up with a blank text editor. I know its supposed to edit the settings of picasa but its not. I don't know what the problem could be. I tried substituting 2.7 for 3.0 because i dont have 3.0, that didn't help. Any help would be greatly appreciated.

Hi Bootch42,

I'm not on my Ubuntu laptop at the mo, but I'll do my best to help you.

Find the "Terminal" application in the Gnome menu (or type 'gnome-terminal' in the run command).

Now enter in the terminal "ls ~/.google/picasa/" and come back to me with the output of that command.

Azza :)

---

### Post by maxadamo on 2010-04-24
Thanks. Great job.
Anyway, I think now I am missing the tray-icon... I suspect it was there before doing this trick.
Am I wrong?

---

### Post by azza85 on 2010-06-04
Hi Maxadamo,

I've just upgraded to Ubuntu 10.04, I will do a clean install of Picasa and let you know whether the system tray appears before applying the changes.

Azza

---

