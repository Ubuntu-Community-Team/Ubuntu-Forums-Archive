---
title: "opera not playing youtube videos"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by SILLAT on 2008-07-12
hey ya'll
i'm feeling abit adventurous today so i jus installed opera 9.27 for a test spin but when ever i got to you tube to play a video i only see a grey box an the vids wont play. i'm  a newbee to opera, ff3 will always be #1 for me
am i missing a plugin or something for opera ?? flash,Gnash & Gstreamer is already intalled and vids play at youtube well in ff3 so wat cud it be? ?
                    

thnx in advance

---

### Post by benerivo on 2008-07-13
First check that opera has detected the flash plugin. Go to Tools>Preferences>Advanced>Content, and make sure the plugin box is ticked. Click on the Plugin Options button and make sure it has detected flash (it should be listed). If not, you can enter a new path/location for it to search for plugins in, so you should enter the place where the flashplayer plugin has been installed to. Then make sure that javascript is enabled in Opera.

---

### Post by SILLAT on 2008-07-13
i see the flash an java plugins are detected there plugin path look like this:
/usr/lib/opera/plugins:/usr/lib/flashplugin-nonfree:/usr/lib/mozilla/plugins
/usr/lib/opera/plugins:/usr/lib/flashplugin-nonfree:/usr/lib/mozilla/plugins

is something wrong with the paths ? ? 
thats also the path for mplayer ans som more plugins

---

### Post by markbuntu on 2008-07-13
Which version of flash are you using? 

Opera 9.50 needs flash 10.

---

### Post by SILLAT on 2008-07-13
i am using flash 9
where can i get flash 10 ?
an how do i install that ? ?
an i jus checked my opera about an its actually:
Version
9.27 
Build
709
Platform
Linux
System
i686, 2.6.24-19-generic
Qt library
3.3.8b
Java
Java Runtime Environment installed

---

### Post by markbuntu on 2008-07-13
I could not get flash to work at all on Opera 9.27, versions 9 or 10. I had to get an even earlier version of flash from adobe and that was flaky.

Your best bet would be to get Opera9.50 from the Opera web site. There is a version for Ubuntu and it is very easy to install.

If you want to get flash 10b, there are instructions in a sticky at the top of the Multimedia and Video forum. Do not get flash10b2, it is very buggy.

---

