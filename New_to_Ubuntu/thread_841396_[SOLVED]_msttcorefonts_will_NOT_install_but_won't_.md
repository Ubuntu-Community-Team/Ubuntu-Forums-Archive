---
title: "[SOLVED] msttcorefonts will NOT install but won't uninstall"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by Eric Qel-Droma on 2008-06-26
Okay, so I go System --> Admin --> Synaptic and I search for msttcorefonts.  Now, I think this was already supposed to be installed by something in the Add/Remove Applications menu, but it didn't work, and every time anything tries to install on my system now, I get the same error message.  I'm duplicating the process for you here.

I follow the path above and search.  I "Mark for Reinstallation" just to get the original error message.  And... this is what it says to me:

E: msttcorefonts: subprocess post-installation script returned error exit status 1

So now I'm going to try to remove the package completely to get rid of my error message.  I follow the path, I search, I "Mark for Complete Removal" and I get:

E: msttcorefonts: subprocess pre-removal script returned error exit status 1

This is beyond my three-days-of-Ubuntu experience level.  Please help.

Bonus question:  I can't manually install fonts to my usr/share/fonts directory because it's "owned by root" and I don't know how to get around that.  Please help again.

Thanks.

---

### Post by mikeyphi on 2008-06-26
Open a terminal and enter:

sudo dpkg --configure -a

enter your password when prompted

reboot and post the results!

---

### Post by Eric Qel-Droma on 2008-06-26
I did what you said, but I don't see anything different on my system.  Should I try reinstalling the package?

BTW, the MS fonts are not currently showing up in OO.org.

Thanks.

---

### Post by Eric Qel-Droma on 2008-06-26
I tried reinstalling but got the same error message.

---

### Post by Afkpuz on 2008-06-26
just keep installing msttcorefonts until it works.  It took me about 5 times to get it to stick.  It might take you more, but just keep trying to install it with the command 
```
sudo apt-get install msttcorefonts
```

It will eventually work, it's just that something is weird with source forge.  



If you don't want to wait around to keep pasting in the command, you could write a script that will install it over and over until it finally sticks.  It you wanted to do that, follow these instructions.

```
gedit install.sh
```

Paste this into the empty file
```

#!/bin/bash/
sudo apt-get -y install msttcorefonts
sudo apt-get -y install msttcorefonts
sudo apt-get -y install msttcorefonts
sudo apt-get -y install msttcorefonts
sudo apt-get -y install msttcorefonts
sudo apt-get -y install msttcorefonts
sudo apt-get -y install msttcorefonts
sudo apt-get -y install msttcorefonts
sudo apt-get -y install msttcorefonts

```

Then, run this to make the file executable
```

sudo chmod 777 install.sh

```

Finally, execute with this command
```
sudo sh install.sh
```


Basically, that will try install msttcorefonts 10 times without prompting you for the "are you sure (y/n)?"  Once it finally gets completely installed, it will just output a message that you've already installed it!  Just run that program until it gets installed.  If you want to make it run more than 10 times, just add another "sudo apt-get -y install msttcorefonts" to the file.

---

### Post by Eric Qel-Droma on 2008-06-26
BTW, this is the stuff that came up in terminal after I tried the apt-get command you suggested:

eric@eric-laptop:~$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
msttcorefonts is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up msttcorefonts (2.4) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
eric@eric-laptop:~$ 


Is that what you expected when you said something was weird with sourceforge?  Also, I don't know how to do those cool "code" boxes that everyone uses, so that's what you get!  :-)

Thanks.

---

### Post by Eric Qel-Droma on 2008-06-26
Tried sudo apt-get install msttcorefonts at least 15 times and got the exact same (previously posted) message each time.

---

### Post by Afkpuz on 2008-06-26
I don't remember the specific errors I got, but I had to try to install several times to get it to work.  From what I understand, the individual fonts are stored in sourceforge and msttcorefonts downloads them and makes them usable, or something similar.  The only problem is that sourceforge has moved the location of the fonts, so msttcorefonts has to look for them.  Just try several times to install it and see if the message changes or the install process makes it any further than the last time.  If it does, the solution is to keep trying to install until msttcorefonts downloads and installs all of the fonts.  And you can use that script that I gave you to automatically install 10 times until it works.




As for the code boxes, when writing your post, it's the "#" button up above.  Then, whatever you paste in between the code  and   /code  will be in a box.


*EDIT* if 15 times doesn't yield any different error message, then reinstalling over and over is not the answer.

---

### Post by Eric Qel-Droma on 2008-06-26
Thanks, but at what point do I give up?

...Apparently after running install.sh three more times with no change in results.  Thanks, though.

---

### Post by avtolle on 2008-06-26
IIRC, these fonts are installed also through ubuntu-restricted-extras. Is this what you tried to install initially throught Add/Remove?

---

### Post by Eric Qel-Droma on 2008-06-26
Yes.

---

### Post by bumanie on 2008-06-26
In terminal try > sudo aptitude remove msttcorefontsthat should, in theory, remove all traces of msttcorefonts, then you can try to reinstall.

---

### Post by Eric Qel-Droma on 2008-06-26
Here's what happened:

```
eric@eric-laptop:~$ sudo aptitude remove msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages will be REMOVED:
  msttcorefonts 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 201kB will be freed.
Writing extended state information... Done
(Reading database ... 115326 files and directories currently installed.)
Removing msttcorefonts ...
W: /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Andale_Mono.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Webdings.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Black.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Impact.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Italic.ttf: not registered.
dpkg: error processing msttcorefonts (--remove):
 subprocess pre-removal script returned error exit status 1

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
```

---

### Post by PatrickMoore on 2008-06-26
> **Eric Qel-Droma said:**
> Here's what happened:

```
eric@eric-laptop:~$ sudo aptitude remove msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages will be REMOVED:
  msttcorefonts 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 201kB will be freed.
Writing extended state information... Done
(Reading database ... 115326 files and directories currently installed.)
Removing msttcorefonts ...
W: /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Andale_Mono.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Webdings.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Black.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Impact.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Italic.ttf: not registered.
dpkg: error processing msttcorefonts (--remove):
 subprocess pre-removal script returned error exit status 1

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
```

im following along too because im having the exact same issue

---

### Post by bumanie on 2008-06-26
May be you could try a different server. Also look at this link, its a bit old, but may be helpful to you. [http://www.linuxquestions.org/questions/debian-26/sub-process-usrbindpkg-returned-an-error-code-1-171107/](http://www.linuxquestions.org/questions/debian-26/sub-process-usrbindpkg-returned-an-error-code-1-171107/)

---

### Post by unutbu on 2008-06-26
I think the pre-removal script fails because it can't find the files it is supposed to remove. The files don't exist because the installation failed. Let's see if we can trick the pre-removal script by giving it something to chew on:

```
#!/bin/sh
sudo touch /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf
sudo touch /usr/share/fonts/truetype/msttcorefonts/Arial_Italic.ttf
sudo touch /usr/share/fonts/truetype/msttcorefonts/Arial.ttf
sudo touch /usr/share/fonts/truetype/msttcorefonts/Arial_Bold_Italic.ttf
sudo touch /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS_Bold.ttf
sudo touch /usr/share/fonts/truetype/msttcorefonts/Andale_Mono.ttf
sudo touch /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold.ttf
sudo touch /usr/share/fonts/truetype/msttcorefonts/Georgia.ttf
sudo touch /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold.ttf
sudo touch /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold_Italic.ttf
sudo touch /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Italic.ttf
sudo touch /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS.ttf
sudo touch /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Italic.ttf
sudo touch /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman.ttf
sudo touch /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS.ttf
sudo touch /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold.ttf
sudo touch /usr/share/fonts/truetype/msttcorefonts/Verdana_Italic.ttf
sudo touch /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf
sudo touch /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold_Italic.ttf
sudo touch /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold_Italic.ttf
sudo touch /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold_Italic.ttf
sudo touch /usr/share/fonts/truetype/msttcorefonts/Courier_New.ttf
sudo touch /usr/share/fonts/truetype/msttcorefonts/Webdings.ttf
sudo touch /usr/share/fonts/truetype/msttcorefonts/Arial_Black.ttf
sudo touch /usr/share/fonts/truetype/msttcorefonts/Courier_New_Italic.ttf
sudo touch /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold_Italic.ttf
sudo touch /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold.ttf
sudo touch /usr/share/fonts/truetype/msttcorefonts/Impact.ttf
sudo touch /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold.ttf
sudo touch /usr/share/fonts/truetype/msttcorefonts/Georgia_Italic.ttf
fc-cache -f -v

sudo  apt-get remove msttcorefonts
```

To save some typing, save that to a file called test.sh

Make it executable:

```
chmod 755 test.sh
```

Run it:
```

./test.sh
```

---

### Post by PatrickMoore on 2008-06-26
```
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Verdana.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Arial_Italic.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Arial.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Arial_Bold_Italic.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS_Bold.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Andale_Mono.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Georgia.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold_Italic.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Italic.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Italic.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Times_New_Roman.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Georgia_Bold.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Verdana_Italic.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold_Italic.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Georgia_Bold_Italic.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Verdana_Bold_Italic.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Courier_New.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Webdings.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Arial_Black.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Courier_New_Italic.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold_Italic.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Impact.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Verdana_Bold.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Georgia_Italic.ttf': No such file or directory
/usr/share/fonts: caching, new cache contents: 0 fonts, 3 dirs
/usr/share/fonts/X11: caching, new cache contents: 0 fonts, 6 dirs
/usr/share/fonts/X11/100dpi: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/75dpi: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/Type1: caching, new cache contents: 8 fonts, 0 dirs
/usr/share/fonts/X11/encodings: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/util: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/truetype: caching, new cache contents: 0 fonts, 14 dirs
/usr/share/fonts/truetype/arphic: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/truetype/freefont: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/kochi: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/truetype/openoffice: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/thai: caching, new cache contents: 35 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-arabeyes: caching, new cache contents: 39 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-bitstream-vera: caching, new cache contents: 10 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-dejavu: caching, new cache contents: 21 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-indic-fonts-core: caching, new cache contents: 11 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-lao: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-malayalam-fonts: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-sil-andika: caching, new cache contents: 7 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-sil-doulos: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/unfonts: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/type1: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/type1/gsfonts: caching, new cache contents: 35 fonts, 0 dirs
/usr/share/X11/fonts: skipping, no such directory
/usr/local/share/fonts: caching, new cache contents: 0 fonts, 0 dirs
/home/patrick/.fonts: skipping, no such directory
/var/cache/fontconfig: not cleaning unwritable cache directory
/home/patrick/.fontconfig: cleaning cache directory
fc-cache: succeeded
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  msttcorefonts
0 upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
1 not fully installed or removed.
After this operation, 201kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 196907 files and directories currently installed.)
Removing msttcorefonts ...
W: /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Andale_Mono.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Webdings.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Black.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Impact.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Italic.ttf: not registered.
dpkg: error processing msttcorefonts (--remove):
 subprocess pre-removal script returned error exit status 1

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
does this help any

---

### Post by PatrickMoore on 2008-06-26
ive tried termianl and synaptec but i cannot  remove msttcorefonts... is going on

---

### Post by philinux on 2008-06-26
Try this

sudo apt-get update && sudo apt-get upgrade

then

sudo dpkg --configure -a

---

### Post by PatrickMoore on 2008-06-26
> **philinux said:**
> Try this

sudo apt-get update && sudo apt-get upgrade

then

sudo dpkg --configure -a

it still looks like im having  msttcore font errors still

:lolflag:

```
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423) hardy/restricted Translation-en_US
Get:1 http://security.ubuntu.com hardy-security Release.gpg [189B]             
Ign http://security.ubuntu.com hardy-security/main Translation-en_US           
Ign http://repository.cairo-dock.org hardy Release.gpg                         
Ign http://repository.cairo-dock.org hardy/cairo-dock Translation-en_US        
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Get:2 http://security.ubuntu.com hardy-security Release [58.5kB]               
Ign http://repository.cairo-dock.org hardy Release                             
Ign http://repository.cairo-dock.org hardy/cairo-dock Packages                 
Hit http://repository.cairo-dock.org hardy/cairo-dock Packages     
Get:3 http://security.ubuntu.com hardy-security/main Packages [25.8kB]
Get:4 http://security.ubuntu.com hardy-security/restricted Packages [6022B]    
Get:5 http://security.ubuntu.com hardy-security/main Sources [7280B]           
Get:6 http://security.ubuntu.com hardy-security/restricted Sources [906B]      
Get:7 http://security.ubuntu.com hardy-security/universe Packages [17.5kB]
Get:8 http://security.ubuntu.com hardy-security/universe Sources [2787B]       
Get:9 http://security.ubuntu.com hardy-security/multiverse Packages [3457B]    
Get:10 http://security.ubuntu.com hardy-security/multiverse Sources [14B]      
Hit http://us.archive.ubuntu.com hardy Release.gpg                   
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Get:11 http://us.archive.ubuntu.com hardy-updates Release.gpg [189B]
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release
Get:12 http://us.archive.ubuntu.com hardy-updates Release [58.5kB]
Hit http://us.archive.ubuntu.com hardy/main Packages                           
Hit http://us.archive.ubuntu.com hardy/restricted Packages                     
Hit http://us.archive.ubuntu.com hardy/main Sources                            
Hit http://us.archive.ubuntu.com hardy/restricted Sources                      
Hit http://us.archive.ubuntu.com hardy/universe Packages                       
Hit http://us.archive.ubuntu.com hardy/universe Sources                        
Hit http://us.archive.ubuntu.com hardy/multiverse Packages                     
Hit http://us.archive.ubuntu.com hardy/multiverse Sources                      
Get:13 http://us.archive.ubuntu.com hardy-updates/main Packages [256kB]        
Get:14 http://us.archive.ubuntu.com hardy-updates/restricted Packages [6458B]  
Get:15 http://us.archive.ubuntu.com hardy-updates/main Sources [76.1kB]        
Get:16 http://us.archive.ubuntu.com hardy-updates/restricted Sources [910B]    
Get:17 http://us.archive.ubuntu.com hardy-updates/universe Packages [57.3kB]   
Get:18 http://us.archive.ubuntu.com hardy-updates/universe Sources [12.9kB]    
Get:19 http://us.archive.ubuntu.com hardy-updates/multiverse Packages [12.0kB] 
Get:20 http://us.archive.ubuntu.com hardy-updates/multiverse Sources [1943B]   
Fetched 605kB in 8s (68.1kB/s)                                                 
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  evolution evolution-common evolution-plugins libglib2.0-0 libglib2.0-dev
  libssl0.9.8 openssl vino
8 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 22.0MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://security.ubuntu.com hardy-security/main libssl0.9.8 0.9.8g-4ubuntu3.3 [931kB]
Get:2 http://us.archive.ubuntu.com hardy-updates/main evolution 2.22.2-0ubuntu2 [2904kB]
Get:3 http://security.ubuntu.com hardy-security/main openssl 0.9.8g-4ubuntu3.3 [391kB]
Get:4 http://us.archive.ubuntu.com hardy-updates/main evolution-common 2.22.2-0ubuntu2 [15.7MB]
Get:5 http://us.archive.ubuntu.com hardy-updates/main libglib2.0-dev 2.16.3-1ubuntu3 [981kB]
Get:6 http://us.archive.ubuntu.com hardy-updates/main libglib2.0-0 2.16.3-1ubuntu3 [817kB]
Get:7 http://us.archive.ubuntu.com hardy-updates/main evolution-plugins 2.22.2-0ubuntu2 [85.2kB]
Get:8 http://us.archive.ubuntu.com hardy-updates/main vino 2.22.2-0ubuntu1 [210kB]
Fetched 22.0MB in 1min51s (199kB/s)                                            
Preconfiguring packages ...
(Reading database ... 196908 files and directories currently installed.)
Preparing to replace libssl0.9.8 0.9.8g-4ubuntu3.1 (using .../libssl0.9.8_0.9.8g-4ubuntu3.3_amd64.deb) ...
Unpacking replacement libssl0.9.8 ...
Preparing to replace evolution 2.22.2-0ubuntu1.3 (using .../evolution_2.22.2-0ubuntu2_amd64.deb) ...
Unpacking replacement evolution ...
Preparing to replace evolution-common 2.22.2-0ubuntu1.3 (using .../evolution-common_2.22.2-0ubuntu2_all.deb) ...
Unpacking replacement evolution-common ...
Preparing to replace libglib2.0-dev 2.16.3-1ubuntu2 (using .../libglib2.0-dev_2.16.3-1ubuntu3_amd64.deb) ...
Unpacking replacement libglib2.0-dev ...
Preparing to replace libglib2.0-0 2.16.3-1ubuntu2 (using .../libglib2.0-0_2.16.3-1ubuntu3_amd64.deb) ...
Unpacking replacement libglib2.0-0 ...
Preparing to replace evolution-plugins 2.22.2-0ubuntu1.3 (using .../evolution-plugins_2.22.2-0ubuntu2_amd64.deb) ...
Unpacking replacement evolution-plugins ...
Preparing to replace openssl 0.9.8g-4ubuntu3.1 (using .../openssl_0.9.8g-4ubuntu3.3_amd64.deb) ...
Unpacking replacement openssl ...
Preparing to replace vino 2.22.1-1 (using .../vino_2.22.2-0ubuntu1_amd64.deb) ...
Unpacking replacement vino ...
Setting up msttcorefonts (2.4) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libssl0.9.8 (0.9.8g-4ubuntu3.3) ...

Setting up evolution-common (2.22.2-0ubuntu2) ...

Setting up libglib2.0-0 (2.16.3-1ubuntu3) ...

Setting up evolution (2.22.2-0ubuntu2) ...

Setting up libglib2.0-dev (2.16.3-1ubuntu3) ...
Setting up evolution-plugins (2.22.2-0ubuntu2) ...
Setting up openssl (0.9.8g-4ubuntu3.3) ...

Setting up vino (2.22.2-0ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by philinux on 2008-06-26
Do a search on your system for andale32.exe

[edit] ignore this post.

---

### Post by philinux on 2008-06-26
[https://answers.launchpad.net/ubuntu/+question/35678](https://answers.launchpad.net/ubuntu/+question/35678)

---

### Post by Eric Qel-Droma on 2008-06-26
No help.  Here's what happened:

```
eric@eric-laptop:~$ gedit test.sh
eric@eric-laptop:~$ chmod 755 test.sh
eric@eric-laptop:~$ ./test.sh
[sudo] password for eric: 
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Verdana.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Arial_Italic.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Arial.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Arial_Bold_Italic.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS_Bold.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Andale_Mono.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Georgia.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold_Italic.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Italic.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Italic.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Times_New_Roman.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Georgia_Bold.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Verdana_Italic.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold_Italic.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Georgia_Bold_Italic.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Verdana_Bold_Italic.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Courier_New.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Webdings.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Arial_Black.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Courier_New_Italic.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold_Italic.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Impact.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Verdana_Bold.ttf': No such file or directory
touch: cannot touch `/usr/share/fonts/truetype/msttcorefonts/Georgia_Italic.ttf': No such file or directory
/usr/share/fonts: caching, new cache contents: 0 fonts, 3 dirs
/usr/share/fonts/X11: caching, new cache contents: 0 fonts, 6 dirs
/usr/share/fonts/X11/100dpi: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/75dpi: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/Type1: caching, new cache contents: 8 fonts, 0 dirs
/usr/share/fonts/X11/encodings: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/util: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/truetype: caching, new cache contents: 0 fonts, 12 dirs
/usr/share/fonts/truetype/arphic: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/truetype/freefont: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/kochi: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/truetype/openoffice: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/thai: caching, new cache contents: 35 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-arabeyes: caching, new cache contents: 39 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-bitstream-vera: caching, new cache contents: 10 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-dejavu: caching, new cache contents: 6 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-indic-fonts-core: caching, new cache contents: 11 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-lao: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-malayalam-fonts: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/unfonts: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/type1: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/type1/gsfonts: caching, new cache contents: 35 fonts, 0 dirs
/usr/share/X11/fonts: skipping, no such directory
/usr/local/share/fonts: caching, new cache contents: 0 fonts, 0 dirs
/home/eric/.fonts: skipping, no such directory
/var/cache/fontconfig: not cleaning unwritable cache directory
/home/eric/.fontconfig: cleaning cache directory
fc-cache: succeeded
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages will be REMOVED:
  msttcorefonts
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 201kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 115326 files and directories currently installed.)
Removing msttcorefonts ...
W: /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Andale_Mono.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Webdings.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Black.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Impact.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Italic.ttf: not registered.
dpkg: error processing msttcorefonts (--remove):
 subprocess pre-removal script returned error exit status 1

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
eric@eric-laptop:~$ sudo apt-get update && sudo apt-get upgrade
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Translation-en_US
Hit http://security.ubuntu.com hardy-security Release.gpg                      
Ign http://security.ubuntu.com hardy-security/main Translation-en_US          
Hit http://us.archive.ubuntu.com hardy Release.gpg
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release
Hit http://security.ubuntu.com hardy-security/main Packages         
Hit http://us.archive.ubuntu.com hardy-updates Release              
Hit http://security.ubuntu.com hardy-security/restricted Packages   
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up msttcorefonts (2.4) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
eric@eric-laptop:~$ sudo dpkg --configure -a
eric@eric-laptop:~$ 

```

---

### Post by Eric Qel-Droma on 2008-06-26
> **philinux said:**
> [https://answers.launchpad.net/ubuntu/+question/35678](https://answers.launchpad.net/ubuntu/+question/35678)

I don't know how to get to /var/lib/dpkg/info/msttcorefonts.postinst - or I would try what they did.

No, wait.  I found it, but I don't have the "permissions" to edit the file.

---

### Post by philinux on 2008-06-26
use gksudo gedit

---

### Post by Eric Qel-Droma on 2008-06-26
> **philinux said:**
> Do a search on your system for andale32.exe

[edit] ignore this post.

I'm glad you said that, because I wouldn't have known how.

---

### Post by Eric Qel-Droma on 2008-06-26
Okay, so I commented those two lines out in msttcorefonts.postinst and then did this:

```
eric@eric-laptop:~$ gksudo gedit
eric@eric-laptop:~$ sudo apt-get remove --purge msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  msttcorefonts*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 201kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 115326 files and directories currently installed.)
Removing msttcorefonts ...
W: /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Andale_Mono.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Webdings.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Black.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Impact.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Italic.ttf: not registered.
dpkg: error processing msttcorefonts (--purge):
 subprocess pre-removal script returned error exit status 1

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Grr!  (Not your fault.  I'm just tired of this error.)

---

### Post by Eric Qel-Droma on 2008-06-26
BTW, here's the altered file with the commented lines:

```
#!/bin/sh
set -e

. /usr/share/debconf/confmodule

db_get msttcorefonts/dldir
LOCALCOPY=$RET

db_get msttcorefonts/savedir
SAVEDIR=$RET

db_get msttcorefonts/dlurl
URLOVERRIDE=$RET

#db_get msttcorefonts/http_proxy
#http_proxy=$RET

if [ -e /usr/share/fonts/truetype/ms-fonts ] ; then
  cp -p /usr/share/fonts/truetype/ms-fonts /var/lib/msttcorefonts/ms-fonts
  rm -f /usr/share/fonts/truetype/ms-fonts
fi

## Content of update-ms-fonts will be concatenated below

#!/bin/sh
# Download and install the Microsoft Core Fonts for the Web
#
# (C) 2000,2001 Eric Sharkey.
# You may freely distribute this file under the terms of the GNU General
# Public License, version 2 or later.

#abort if anything goes wrong
#set -e

FONTDIR=/usr/share/fonts/truetype/msttcorefonts

#if [ `id -u` != 0 ] ; then
#  echo "update-ms-fonts can only be run as root."
#  exit -1
#fi
#
#for opt in "$@"; do
#    case "$opt" in
#        -q) QUIET_MODE=1 ;;
#        -c) CHECK_ONLY=1 ;;
#        -s*) SAVEDIR=${opt#-s} ;;
#        -u*) URLOVERRIDE=${opt#-u} ;;
#        *) LOCALCOPY=$opt ;;
#    esac
#done
if [ "`echo $LOCALCOPY | tr '[:upper:]' '[:lower:]'`" = "none" ] ; then
  exit 0
fi

EXITCODE=0

export http_proxy

# Base URL for Microsoft fonts
##URLROOT="http://unc.dl.sourceforge.net/sourceforge/corefonts/"

URLROOTS="http://surfnet.dl.sourceforge.net/sourceforge/corefonts/
         http://internap.dl.sourceforge.net/sourceforge/corefonts/
         http://puzzle.dl.sourceforge.net/sourceforge/corefonts/
         http://heanet.dl.sourceforge.net/sourceforge/corefonts/
         http://superb-west.dl.sourceforge.net/sourceforge/corefonts/
         http://superb-east.dl.sourceforge.net/sourceforge/corefonts/
         http://easynews.dl.sourceforge.net/sourceforge/corefonts/
         http://jaist.dl.sourceforge.net/sourceforge/corefonts/
         http://mesh.dl.sourceforge.net/sourceforge/corefonts/
         http://nchc.dl.sourceforge.net/sourceforge/corefonts/
         http://kent.dl.sourceforge.net/sourceforge/corefonts/
         http://umn.dl.sourceforge.net/sourceforge/corefonts/
         http://switch.dl.sourceforge.net/sourceforge/corefonts/"

if [ "$URLOVERRIDE" ] ; then
  URLROOTS="$URLOVERRIDE"
fi

if [ -z "$QUIET_MODE" ] ; then
    cat <<EOF

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

EOF
fi

SCRATCHDIR=`mktemp -t -d msttcorefonts.XXXXXX`
chmod 0755 $SCRATCHDIR
cd $SCRATCHDIR

cat <<EOF > msfonts.info
663974c9fe3ba55b228724fd4d4e445f  Andale_Mono.ttf                 andale32.exe andalemo.ttf
3e7043e8125f1c8998347310f2c315bc  Arial_Black.ttf                 arialb32.exe ariblk.ttf
f11c0317db527bdd80fa0afa04703441  Arial.ttf                       arial32.exe  arial.ttf
34cd8fd9e4fae9f075d4c9a2c971d065  Arial_Bold.ttf                  arial32.exe  arialbd.ttf
a2b3bcdb39097b6aed17a766652b92b2  Arial_Bold_Italic.ttf           arial32.exe  arialbi.ttf
25633f73d92a0646e733e50cf2cc3b07  Arial_Italic.ttf                arial32.exe  ariali.ttf
a50f9c96a76356e3d01013e0b042989f  Comic_Sans_MS.ttf               comic32.exe  comic.ttf
81d64ec3675c4adc14e9ad2c5c8103a7  Comic_Sans_MS_Bold.ttf          comic32.exe  comicbd.ttf
20f23317e90516cbb7d38bd53b3d1c5b  Courier_New.ttf                 courie32.exe cour.ttf
7d94f95bf383769b51379d095139f2d7  Courier_New_Bold.ttf            courie32.exe courbd.ttf
167e27add66e9e8eb0d28a1235dd3bda  Courier_New_Italic.ttf          courie32.exe couri.ttf
da414c01f951b020bb09a4165d3fb5fa  Courier_New_Bold_Italic.ttf     courie32.exe courbi.ttf
f4b306eed95aa7d274840533be635532  Georgia.ttf                     georgi32.exe georgia.ttf
c61b355a5811e56ed3d7cea5d67c900e  Georgia_Bold.ttf                georgi32.exe georgiab.ttf
1e4e5d1975bdf4a5c648afbf8872fa13  Georgia_Italic.ttf              georgi32.exe georgiai.ttf
e5d52bbfff45e1044381bacb7fc8e300  Georgia_Bold_Italic.ttf         georgi32.exe georgiaz.ttf
8fc622c3a2e2d992ec059cca61e3dfc0  Impact.ttf                      impact32.exe impact.ttf
4f97f4d6ba74767259ccfb242ce0e3f7  Times_New_Roman.ttf             times32.exe  times.ttf
ed6e29caf3843142d739232aa8642158  Times_New_Roman_Bold.ttf        times32.exe  timesbd.ttf
6d2bd425ff00a79dd02e4c95f689861b  Times_New_Roman_Bold_Italic.ttf times32.exe  timesbi.ttf
957dd4f17296522dead302ab4fcdfa8d  Times_New_Roman_Italic.ttf      times32.exe  timesi.ttf
70e7be8567bc05f771b59abd9d696407  Trebuchet_MS.ttf                trebuc32.exe trebuc.ttf
055460df9ab3c8aadd3330bd30805f11  Trebuchet_MS_Bold.ttf           trebuc32.exe trebucbd.ttf
8f308fe77b584e20b246aa1f8403d2e9  Trebuchet_MS_Italic.ttf         trebuc32.exe trebucit.ttf
fb5d68cb58c6ad7e88249d65f6900740  Trebuchet_MS_Bold_Italic.ttf    trebuc32.exe trebucbi.ttf
3ba52ab1fa0cd726e7868e9c6673902c  Verdana.ttf                     verdan32.exe verdana.ttf
a2b4dc9afc18e76cfcaa0071fa7cd0da  Verdana_Bold.ttf                verdan32.exe verdanab.ttf
24b3a293c865a2c265280f017fb24ba5  Verdana_Italic.ttf              verdan32.exe verdanai.ttf
f7310c29df0070530c48a47f2dca9014  Verdana_Bold_Italic.ttf         verdan32.exe verdanaz.ttf
1a56b45a66b07b4c576d5ead048ed992  Webdings.ttf                    webdin32.exe webdings.ttf
EOF

for ttf in `awk '{print $2}' msfonts.info` ; do
    if [ ! -e $FONTDIR/$ttf ] || \
        [ `md5sum $FONTDIR/$ttf | awk '{print $1}'` != `awk "/$ttf/ {print \\$1 }" msfonts.info` ]
        then
        THISFILE=`grep $ttf msfonts.info | awk '{print $3}'`
        if ! echo $FONTFILES | grep -q $THISFILE ; then
            FONTFILES="$FONTFILES $THISFILE"
        fi
    fi
done
if [ -n "$CHECK_ONLY" ] ; then
    if [ -n "$FONTFILES" ] ; then
        EXITCODE=1
    fi
elif [ -n "$FONTFILES" ] ; then 
    if [ -n "$QUIET_MODE" ] ; then
        QUIET_ARG="--quiet"
    else
        QUIET_ARG=""
    fi
    for URLROOT in $URLROOTS ; do
        for ff in $FONTFILES; do
            if [ ! -e $ff.done ] || [ ! -e $ff ] ; then
                if [ -z "$LOCALCOPY" ] ; then
                    if ! wget --continue --tries=1 --dns-timeout=10 --connect-timeout=5 --read-timeout=300 $QUIET_ARG --directory-prefix . --no-directories --no-background $URLROOT$ff ; then
                        continue 2
                    fi
                else
                    cp $LOCALCOPY/$ff .
                fi
                touch $ff.done
            fi
        done
    done
    if [ -n "$SAVEDIR" ] ; then
        mkdir -p "$SAVEDIR"
    fi
    for ff in $FONTFILES; do
        cabextract $ff 1>&2
        if [ -n "$SAVEDIR" ] ; then
            cp $ff "$SAVEDIR"
        fi
        rm $ff
    done
  #Add some level of predictability by folding everything to lower case
    for x in *; do
        y=`echo $x | tr '[A-Z]' '[a-z]'`
        if [ "$x" != "$y" ]; then
            mv "$x" "$y"
        fi
    done
    
    chmod 644 *
    
  # Give sane names. These are nearly the same names MS uses for the
  # Macintosh versions
    
    mkdir -p /usr/share/doc/msttcorefonts $FONTDIR
    if [ -e licen.txt ] ; then
        mv licen.txt '/usr/share/doc/msttcorefonts/READ_ME!'
        gzip -f '/usr/share/doc/msttcorefonts/READ_ME!'
    fi
    for ff in $FONTFILES; do
        for ttf in `grep $ff msfonts.info | awk '{print $4}'`; do
            longname=`awk "/$ttf/ { print \\$2 }" msfonts.info`
            mv $ttf $FONTDIR/$longname
            ln -sf $longname $FONTDIR/$ttf
        done
    done
    
  # Make a note of what we installed so we can uninstall it later
    mkdir -p /var/lib/msttcorefonts
    awk '{print $2}' msfonts.info > /var/lib/msttcorefonts/ms-fonts
    awk '{print $4}' msfonts.info >> /var/lib/msttcorefonts/ms-fonts
fi

cd /
rm -rf $SCRATCHDIR

if [ -z "$QUIETMODE" ] ; then
    if [ $EXITCODE = 0 ] ; then
        echo "All fonts downloaded and installed."
    else
        echo "Fonts need to be updated."
    fi
fi

# Automatically added by dh_installdefoma
FILE='/etc/defoma/hints/msttcorefonts.hints'
if [ "$1" = configure ]; then
	test -x /usr/bin/defoma-font && /usr/bin/defoma-font reregister-all $FILE
fi
# End automatically added section


exit $EXITCODE
```

---

### Post by philinux on 2008-06-26
gksudo gedit /var/lib/dpkg/info/msttcorefonts.postinst

copy and paste into terminal

---

### Post by unutbu on 2008-06-26
Run
```
sudo mkdir /usr/share/fonts/
sudo mkdir /usr/share/fonts/truetype/
sudo mkdir /usr/share/fonts/truetype/msttcorefonts/
test.sh

```
Don't worry if 
```
sudo mkdir /usr/share/fonts/
```
returns
```
mkdir: cannot create directory `/usr/share/fonts/': File exists
```

---

### Post by Eric Qel-Droma on 2008-06-26
> **bumanie said:**
> May be you could try a different server. Also look at this link, its a bit old, but may be helpful to you. [http://www.linuxquestions.org/questions/debian-26/sub-process-usrbindpkg-returned-an-error-code-1-171107/](http://www.linuxquestions.org/questions/debian-26/sub-process-usrbindpkg-returned-an-error-code-1-171107/)

I tried this in terminal (had to add "sudo" in front of everything) but it did nothing, and I don't see the point of going "back and forth" as the post suggests.

---

### Post by Eric Qel-Droma on 2008-06-26
> **philinux said:**
> gksudo gedit /var/lib/dpkg/info/msttcorefonts.postinst

copy and paste into terminal

What would this do that doing "gksudo gedit" and then opening the path in the GUI not do?

---

### Post by philinux on 2008-06-26
Sorry this allows you to edit the file, I see you've already done it.

---

### Post by Eric Qel-Droma on 2008-06-26
> **unutbu said:**
> Run
```
sudo mkdir /usr/share/fonts/
sudo mkdir /usr/share/fonts/truetype/
sudo mkdir /usr/share/fonts/truetype/msttcorefonts/
test.sh

```
Don't worry if 
```
sudo mkdir /usr/share/fonts/
```
returns
```
mkdir: cannot create directory `/usr/share/fonts/': File exists
```

Here's what I did (sorry for the lines of typo code):

```
eric@eric-laptop:~$ sudo mkdir /usr/share/fonts/
mkdir: cannot create directory `/usr/share/fonts/': File exists
eric@eric-laptop:~$ sudo mkdir /usr/share/fonts/truetype
mkdir: cannot create directory `/usr/share/fonts/truetype': File exists
eric@eric-laptop:~$ sudo mkdir /sur/share/fonts/truetype/msttcorefonts
mkdir: cannot create directory `/sur/share/fonts/truetype/msttcorefonts': No such file or directory
eric@eric-laptop:~$ sudo mkdir /usr/share/fonts/truetype/msttcorefonts/
eric@eric-laptop:~$ test.sh
bash: test.sh: command not found

```

Stuck now.

---

### Post by Eric Qel-Droma on 2008-06-26
> **philinux said:**
> Sorry this allows you to edit the file, I see you've already done it.

No problem.  Good to know the command line can take commands like that (for when I'm a Linux God and can remember long pathnames like that).

---

### Post by unutbu on 2008-06-26
> **Eric Qel-Droma said:**
> 

```
eric@eric-laptop:~$ sudo mkdir /usr/share/fonts/truetype/msttcorefonts/
```

No complaint means that msttcorefonts directory was created. Good.

> 
```
eric@eric-laptop:~$ test.sh
bash: test.sh: command not found
```

My mistake. Run test.sh like this:

```

./test.sh

```

---

### Post by Eric Qel-Droma on 2008-06-26
No luck.  Here's what I got:

```
eric@eric-laptop:~$ ./test.sh
/usr/share/fonts: caching, new cache contents: 0 fonts, 3 dirs
/usr/share/fonts/X11: caching, new cache contents: 0 fonts, 6 dirs
/usr/share/fonts/X11/100dpi: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/75dpi: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/Type1: caching, new cache contents: 8 fonts, 0 dirs
/usr/share/fonts/X11/encodings: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/util: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/truetype: caching, new cache contents: 0 fonts, 13 dirs
/usr/share/fonts/truetype/arphic: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/truetype/freefont: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/kochi: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/truetype/msttcorefonts: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/truetype/openoffice: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/thai: caching, new cache contents: 35 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-arabeyes: caching, new cache contents: 39 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-bitstream-vera: caching, new cache contents: 10 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-dejavu: caching, new cache contents: 6 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-indic-fonts-core: caching, new cache contents: 11 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-lao: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-malayalam-fonts: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/unfonts: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/type1: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/type1/gsfonts: caching, new cache contents: 35 fonts, 0 dirs
/usr/share/X11/fonts: skipping, no such directory
/usr/local/share/fonts: caching, new cache contents: 0 fonts, 0 dirs
/home/eric/.fonts: skipping, no such directory
/var/cache/fontconfig: not cleaning unwritable cache directory
/home/eric/.fontconfig: cleaning cache directory
fc-cache: succeeded
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  msttcorefonts
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 201kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 115326 files and directories currently installed.)
Removing msttcorefonts ...
W: /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Andale_Mono.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Webdings.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Black.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Impact.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Italic.ttf: not registered.
dpkg: error processing msttcorefonts (--remove):
 subprocess pre-removal script returned error exit status 1

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
eric@eric-laptop:~$ 

```

---

### Post by philinux on 2008-06-26
What have you got selected under

System>Prefs>Network Proxy

---

### Post by unutbu on 2008-06-26
Perhaps try temcat's solution: [http://ubuntuforums.org/showthread.php?p=4768010](http://ubuntuforums.org/showthread.php?p=4768010)
```

sudo /usr/bin/defoma-font register-all /etc/defoma/hints/msttcorefonts.hints
sudo apt-get -f update
sudo apt-get --purge remove msttcorefonts
```

---

### Post by Eric Qel-Droma on 2008-06-26
Ah ha!  I'd had a manual proxy configuration, but when I switched to Direct Connection and ran Synaptic, everything went swimmingly and the fonts are now on my system! 

Thanks to everyone for sticking with me through all of this!

Eric

---

