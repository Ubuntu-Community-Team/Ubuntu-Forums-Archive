---
title: "new install / possible graphics issues"
date: 2012-10-14
forum: New to Ubuntu
---

### Post by Dwarvenking on 2012-10-14
Hi all, hope some one can help!

Ive just moved my old hp pavillion that i run my cnc mill with over to ubuntu having been convinced emc is a better way to go):P
However im having issues lol I burnt the boot disc, installed it ok (no other operating systems full reformat!) and the first time i booted up everything was fine. Switched it off and later decided to have a play. Everything goes ok until the desktop appears and satys blank? (tool bar and icons gone etc) It still responds to commands and having seen another post with the same problem i tried alt and f4 then unity-reset and compiz-replace but get a message back saying the location doesnt exist.
I also get a weird grid pattern on the desktop sometimes like the graphics are struggling but i had no problem first time round and windows never had any graphics issues.

Can anyone suggest anything?
the hard drive while small (about to be replace) still has 2 gig free and ive made no system changes and tried re installing! 
Almost forgot to mention its **Ubuntu 10.04 "Lucid Lynx" LTS  that comes pre bundled with linuxcnc**

Thanks for your time
Harry

---

### Post by Dwarvenking on 2012-10-14
Just a quick update, i booted up right clicked and created some new empty folder, restarted and the folders were still there so its not graphics (i think anyway!!) If it is of any relation i opened linuxcnc config using alt f4 and saved a demo set up but when i try to launch linuxcnc its self i get a linux cnc error page the last line of which is loading real time os, RTAPI and HAL_LIB modules.

May be 2 completely unrelated issues though!

Thanks again

---

### Post by NikTh on 2012-10-14
Ubuntu 10.04 LTS still supported , but is an old version (2 years almost) and will EOL in a few months. 

Can you try the newest LTS version Ubuntu 12.04 ? 

Download it from here : [http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/) . Goto Desktop CD section and download the appropriate architecture (32bit or 64bit). 

If you managed to install the Ubuntu 10.04 , you will figure it out on how to install 12.04 (same way :p) 

Thanks

---

### Post by homecomputer@on.aibn.com on 2012-10-14
I had this happen once. I did  .....  ctrl alt f1 to get to the terminal. Then I did  ..... ctrl alt f7 to get back to the desktop. .... and all was there .... was video driver glitch.
I then  in 10.04  I used the additional hardware to get the ati driver.

---

### Post by Dwarvenking on 2012-10-15
Hi all, unfortunately i cant update as the sole purpose of the install is to run emc and its specifically bundled with that version and a warning not to upgrade for proper operation. were do i find an ati driver? im electronics based but not operating systems:p

Thanks 
harry

---

### Post by squakie on 2012-10-15
If you search the linuxcnc website, it makes it sound like it only works with your release.  If you go to the source code git you'll notice a reference to a change to the makefile so it works with 12.04.  So, you might be better off going that way.  I had never heard of linuxcnc prior to this, but I'd be willing to genea-pig the source code installation and make on my 12.04 system to be able to give you information on what you need to do.  That would probably take me a day or 2 if you can wait that long.

The instructions for 11.x and 12.04 can be found here:

[http://wiki.linuxcnc.org/cgi-bin/wiki.pl?Build_A_Simulator_Manually](http://wiki.linuxcnc.org/cgi-bin/wiki.pl?Build_A_Simulator_Manually)

---

### Post by squakie on 2012-10-16
Let me know if you want me to guinea pig that in 12.04 so I can help you to install it 12.04 and have a current install running emc.

---

