---
title: "How To: Get Flash Working in Opera9.27"
date: 2008-05-25
forum: Outdated Tutorials &amp; Tips
---

### Post by markbuntu on 2008-05-25
The current version of Flash 9.0.115.0 does not work with the current version of Opera 9.27. but Opera9.27 does work with Flash 9.0.48.0. This is how to get that working without making trouble for firefox or later versions of Opera that are coming and will work with Flash 9.0.115.0

To get flash to work in Opera 9.27 which is the version available in the repository you must do the following:


First go here:

[http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266](http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266)

which is the adobe repository for older versions of flash and download flashplayer 9 to your desktop or wherever. Unpack it. The readme will direct you to the folder with the linux version which is 9r48. Unpack that.

You can use archive manager which is in Applications/ Accessories to do this part. If you can't see it there go to System/Preferences/Main Menu and check the box to make it visible.

This will then create a folder called install_flash_player_9_linux. Take the file in there called libflashplayer.so and move it to /usr/lib/opera/plugins.

I don't know all those tricky command line terminal things so I just typed sudo nautlius in a terminal and used two nautilus windows to go to the right locations and did a drag and drop.

DANGER!!! Do not use nautlius like this unless you are absolutely sure about what you are doing and be sure to close it right away when you are finished. It is easily possible to put your system in an unrecoverable state by moving random files around as root.

Then navigate over to /usr/share/opera/ini and open the pluginpath.ini file. Scroll down to the section that says ; Flash and comment out the lines: 

/usr/lib/flash-plugin=1
/usr/lib/flashplugin-nonfree=1

and add the line: 

/usr/lib/opera/plugins=1

so it looks like this:

; Flash
#/usr/lib/flash-plugin=1
#/usr/lib/flashplugin-nonfree=1
/usr/lib/opera/plugins=1

Save it and get out of there.

Open opera and enjoy!!

****Adobe changed flash 9 after Opera froze the code for 9.27 so there you go.

When you get Opera 9.5 you can just remove the comment marks and the line you added in /usr/share/opera/ini/pluginpath.ini and just put the old flash in the trash.

Thanks to ezekleinin for finding Remco Lanting's blog on Opera and Flash which is here:

[http://my.opera.com/remcolanting/blog/2008/04/14/opera-and-flash-on-linux](http://my.opera.com/remcolanting/blog/2008/04/14/opera-and-flash-on-linux)

And a big thanks to Remco for pointing the way!!!

---

