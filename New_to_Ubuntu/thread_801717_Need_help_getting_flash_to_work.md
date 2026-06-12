---
title: "Need help getting flash to work"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by LinuxNoob624 on 2008-05-20
Hey guys. Im new to Linux and i just cant seem to get flash to work. I tried the flash nonfree thing and it worked for like 1 day and now when i go to youtube.com all i see is a blank box. I tried installing flash by downloading it off their website. I've searched other threads for instructions and this is the problem I came accross.  


kevin@kevin-laptop:~/Desktop$ cd /home/kevin/Desktop/
kevin@kevin-laptop:~/Desktop$ tar xvfz install_flash_player_9_linux.tar.gz
install_flash_player_9_linux/
install_flash_player_9_linux/flashplayer-installer
install_flash_player_9_linux/libflashplayer.so
kevin@kevin-laptop:~/Desktop$ cd install_flash_player_9_linux/
kevin@kevin-laptop:~/Desktop/install_flash_player_9_linux$ sudo ./flashplayer-installer

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

kevin@kevin-laptop:~/Desktop/install_flash_player_9_linux$ 

Pls help me with this!!! I really like Linux but i can't keep using it if i can't even go to youtue lol.

---

### Post by beejaycee on 2008-05-20
Have you seen [THIS]("http://ubuntuforums.org/showthread.php?t=766683") post?  Scroll down and there is a bit on getting flash to work.  Good luck.

---

### Post by ezekielnin on 2008-05-20
hum I tried the step five and it doesn't work in opera .. is there any flash support for the opera browser????

The scrolling in firefox 3 is totally messed up and when playing videos it even more scruffy....

opera runs a lot smoother ... except i can't get flash to work.

Anybody knows a fix?

---

### Post by ezekielnin on 2008-05-20
Ohhh I just found this **** ...
[http://my.opera.com/remcolanting/blog/2008/04/14/opera-and-flash-on-linux](http://my.opera.com/remcolanting/blog/2008/04/14/opera-and-flash-on-linux)

I'll try it out tomorow and leave you some feedback
Good night

---

### Post by Otto-C on 2008-05-25
Ubuntu 8.04 fresh install no changes.

Followed the Adobe install instructions. All went well until it
asked for path to install it in. ie /usr/lib/mozilla.
What is the correct path.
tia
otto-c

---

### Post by sayakb on 2008-05-25
At a terminal:
```
sudo apt-get install ubuntu-restricted-extras gnash
```

This would install all of the required flash modules.

---

### Post by markbuntu on 2008-05-25
To get flash to work in Opera 9.27 which is the version available in the repository you must do the following:
First go here:

[http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266](http://kb.adobe.com/selfservice/viewContent.do?externalId=tn_14266)

which is the adobe repository for older versions of flash and download flashplayer 9 to your desktop or wherever. Unpack it. The readme will direct you to the folder with the linux version which is 9r48. Unpack that.

You need to be root for the next 2 parts

This will then create a folder called install_flash_player_9_linux. Take the file in there called libflashplayer.so and move it to /usr/lib/opera/plugins.

Then navigate over to /usr/share/opera/ini and open the pluginpath.ini file with gedit or whatever editor you use. Scroll down to the section that says ; Flash and comment out the lines 

/usr/lib/flash-plugin=1
/usr/lib/flashplugin-nonfree=1

and add the line: 

/usr/lib/opera/plugins=1

so it looks like this
; Flash
#/usr/lib/flash-plugin=1
#/usr/lib/flashplugin-nonfree=1
/usr/lib/opera/plugins=1

Save it and get out of there.

Open opera and enjoy!!

Opera 9.27 needs a version of flash 9 older than the one in the repository. Adobe changed flash 9 after Opera froze the code for 9.27 so there you go.

No need to use that buggy firefox beta anymore!

---

