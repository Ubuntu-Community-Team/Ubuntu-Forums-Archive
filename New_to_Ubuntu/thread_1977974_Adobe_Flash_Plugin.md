---
title: "Adobe Flash Plugin"
date: 2012-05-11
forum: New to Ubuntu
---

### Post by 3dmatrix on 2012-05-11
I wish to install Adobe flash browser plugin on a Lubuntu comp. But i do not wish to do so through Apt or Synaptic etc. I had been facing a lot of trouble that way and Lubuntu had to be reinstalled more than 3 times and more than 5 days got wasted because of it.
(You can refer to the problem on this thread [http://ubuntuforums.org/showthread.php?t=1974136](http://ubuntuforums.org/showthread.php?t=1974136) )  Now that the entire comp is ready except the flash installation, i would not like to do any thing so that i again have to format the comp.

Rather, I have downloaded the Adobe flash file from Ubuntu's server. The file name is : 
adobe-flashplugin_11.2.202.235.orig.tar.gz  Can any one tell me how i could install flash from this file without having to go online. I tried the package installer but it said that its not a deb file.

Can any one help me with this.

---

### Post by wilee-nilee on 2012-05-11
Use the firefox addon called flash aid to install with, it will set you up best in my opinion.

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

When you have used the methods you shy away from now, were you not accepting all the updates and upgrades, that will mess you up. There are the main apps and the dependencies if you break them apart without knowing what they are you're asking for troubles.

Really what you should install is the lubuntu-restricted-extras, this loads the flash, video codecs, ms fonts and other needed stuff in general.

You also need to check if the repositories are open as well in the software sources.

After looking at the link you have in the first post I have to ask why do you need a proxy, and are you using tor?

---

### Post by idoitprone on 2012-05-11
> **3dmatrix said:**
> I wish to install Adobe flash browser plugin on a Lubuntu comp. But i do not wish to do so through Apt or Synaptic etc. I had been facing a lot of trouble that way and Lubuntu had to be reinstalled more than 3 times and more than 5 days got wasted because of it.
(You can refer to the problem on this thread [http://ubuntuforums.org/showthread.php?t=1974136](http://ubuntuforums.org/showthread.php?t=1974136) )  Now that the entire comp is ready except the flash installation, i would not like to do any thing so that i again have to format the comp.

Rather, I have downloaded the Adobe flash file from Ubuntu's server. The file name is : 
adobe-flashplugin_11.2.202.235.orig.tar.gz  Can any one tell me how i could install flash from this file without having to go online. I tried the package installer but it said that its not a deb file.

Can any one help me with this.

unpack the file so you get a file that is called something like libflashplugin.so it must have a .so ending

move the file to 
/usr/lib/mozilla/plugins 
if 32 bit
or move to
/usr/lib64/mozilla/plugins
if 64 bit ubuntu

remember to open the file manager with admin rights
type 
```
gksudo nautilus
``` to open the with admin rights

NOTE: REMEMBER TO INSTALL THE PROPER VERSION 64bit flash for 64 bit ubuntu
and 32 bit flash for 32 bit ubuntu

---

### Post by 3dmatrix on 2012-05-11
> **wilee-nilee said:**
> Use the firefox addon called flash aid to install with, it will set you up best in my opinion.

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

When you have used the methods you shy away from now, were you not accepting all the updates and upgrades, that will mess you up. There are the main apps and the dependencies if you break them apart without knowing what they are you're asking for troubles.

Really what you should install is the lubuntu-restricted-extras, this loads the flash, video codecs, ms fonts and other needed stuff in general.

You also need to check if the repositories are open as well in the software sources.

After looking at the link you have in the first post I have to ask why do you need a proxy, and are you using tor?

I am using proxy because my internet is through the University's proxy. No other option. No Tor.

.

---

### Post by wilee-nilee on 2012-05-11
> **3dmatrix said:**
> I am using proxy because my internet is through the University's proxy. No other option. No Tor.

.

Ah, I see funny mine did not have a proxy as far as I know.

---

### Post by 3dmatrix on 2012-05-11
> **idoitprone said:**
> unpack the file so you get a file that is called something like libflashplugin.so it must have a .so ending

move the file to 
/usr/lib/mozilla/plugins 
if 32 bit
or move to
/usr/lib64/mozilla/plugins
if 64 bit ubuntu

remember to open the file manager with admin rights
type 
```
gksudo nautilus
``` to open the with admin rights

NOTE: REMEMBER TO INSTALL THE PROPER VERSION 64bit flash for 64 bit ubuntu
and 32 bit flash for 32 bit ubuntu


After unpacking i get four 'so' files in it.

/adobe-flashplugin-11.2.202.235/i386/libflashplayer.so
/adobe-flashplugin-11.2.202.235/amd64/libflashplayer.so
/adobe-flashplugin-11.2.202.235/i386/usr/lib/kde4/kcm_adobe_flash_player.so
/adobe-flashplugin-11.2.202.235/amd64/usr/lib64/kde4/kcm_adobe_flash_player.so

The comp i will use it in, is an AMD comp but i have installed 32 bit Linux in it. 
So i hope i should use the first so file at : 
/adobe-flashplugin-11.2.202.235/i386/libflashplayer.so

Just for my knowledge : how do i confirm if i am using a 32 or 64 bit system :)

.

---

### Post by 3dmatrix on 2012-05-11
Is there any way I could make a deb file out of that download ? If so how ?
I am thinking abt that because it will make flash applicable system wide and not just for one or two browsers.

---

### Post by zombifier25 on 2012-05-11
To find whether your system is 32bit or 64bit:
```
uname -p
```
And then:
> **idoitprone said:**
> unpack the file so you get a file that is called something like libflashplugin.so it must have a .so ending

move the file to 
/usr/lib/mozilla/plugins 
if 32 bit
or move to
/usr/lib64/mozilla/plugins
if 64 bit ubuntu

remember to open the file manager with admin rights
type 
```
gksudo nautilus
``` to open the with admin rights

NOTE: REMEMBER TO INSTALL THE PROPER VERSION 64bit flash for 64 bit ubuntu
and 32 bit flash for 32 bit ubuntu

---

### Post by 3dmatrix on 2012-05-12
> **idoitprone said:**
> 
. . . move the file to 
/usr/lib/mozilla/plugins . . .

Thanx it worked well :)

I wish to know the following :

(1) After installing flash in this way, if in future flash player needs to be upgraded, can it do that by update manager ?

(2) I have also downloaded Adobe acrobat (AdbeRdr9.5.1-1_i486linux_enu.bin) but as it is a bin file i do not know how to install it. Installer again says its not a deb file so cannot install.

(3) Is there any way to convert such files (flash / acrobat) in to deb files ?

---

### Post by idoitprone on 2012-05-12
> **3dmatrix said:**
> Thanx it worked well :)

I wish to know the following :

(1) After installing flash in this way, if in future flash player needs to be upgraded, can it do that by update manager ?

(2) I have also downloaded Adobe acrobat (AdbeRdr9.5.1-1_i486linux_enu.bin) but as it is a bin file i do not know how to install it. Installer again says its not a deb file so cannot install.

(3) Is there any way to convert such files (flash / acrobat) in to deb files ?

1 No

2 It usually common practiace to move the file to  /opt directory for user installed programs so it does not mix with package install. This makes it easier to manage

3 Yes there is but I do not know how. Go ask someone who maintain packages, but it usually edition couple file to make a config for deb

---

### Post by 3dmatrix on 2012-05-13
> **idoitprone said:**
> 1 No

2 It usually common practiace to move the file to  /opt directory for user installed programs so it does not mix with package install. This makes it easier to manage

3 Yes there is but I do not know how. Go ask someone who maintain packages, but it usually edition couple file to make a config for deb

(2) So can we execute it directly just by placing it there ? And does the system recognizes it as an application ?

---

### Post by idoitprone on 2012-05-13
> **3dmatrix said:**
> (2) So can we execute it directly just by placing it there ? And does the system recognizes it as an application ?


If You want you just type the name of the program to run it
Usually you have to extend your class path when you manually add programs

Here is an example using java in this link
[http://harkiran-howtos.blogspot.com/2010/06/set-environment-variables-path.html](http://harkiran-howtos.blogspot.com/2010/06/set-environment-variables-path.html)

You can run it in the current directory. All you need is execute permissions on the app
```
chmod u+x applicationName
```

However, you browser must be set to look at different directories for plugins. I do not know so the other solution is to symlink to the plugin directory

```
ln -s source destination
```

---

### Post by 3dmatrix on 2012-05-13
Thanx got it done :)

---

