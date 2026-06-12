---
title: "I screwed something up(AGAIN)..."
date: 2008-06-20
forum: New to Ubuntu
---

### Post by smith_fan on 2008-06-20
[FONT="Tahoma"]I've been getting a recurring error message when I attempt certain tasks.  I know that it stems from the failed installation of a component listed as a requirement in the fine print of something I tried to do in the past.  Now, I seem to frequently get error messages referencing msttcorefonts.  I've searched for it in Synaptic trying to undo whatever I screwed-up, but can't seem to find it.

The most-recent instance of an error message about it occurred when I attempted to update to Firefox 3.0 with ubuntuzilla.  Here is what that Terminal window message said:  
“
All done, errors in processing 1 file(s).  
dpkg: error processing msttcorefonts (--configure):
subprocess post-installation script returned exit status 1.
Setting up libnotify-bin (0.4.4-3build1) ...
Errors were encountered while processing:
 msttcorefonts
gdebi-gtk:  Fatal IO error 9 (Bad file descriptor) on X server 0:0.0.
“
Can someone please explain to me how I can fix what got messed-up with msttcorefonts?  And if more info is needed to be able to do that, please let me know.

And is there a capture tool available that I could use for similar text so that I wouldn't have to switch windows a million times because of my horrendous memory?

I really will try to figure-out any future error messages before posting about them, though! ;)

Thanks so much!,
~D~[/FONT][FONT="Tahoma"][/FONT]

---

### Post by dwhitney67 on 2008-06-20
From what I have read elsewhere, the M$ fonts aren't really needed any more under Linux, well at least not under Fedora.  The Liberation Sans and the Liberation Serif fonts should most peoples needs, being (almost?) identical to Arial or something similar.

If you are looking for a particular font, search google or the Ubuntu repositories on the web for the M$ fonts package... I would imagine it is still available.  It is sometimes easier to find a package that way on the web vs. via synaptic.  To me, synaptic is mere eye candy.

---

### Post by smith_fan on 2008-06-20
Do you have any thoughts on how I can get rid of these nagging messages?:confused:    I wish I could remember what it was that I was messing with that started them.

---

### Post by dwhitney67 on 2008-06-20
Have you tried:

```
$ sudo apt-get remove msttcorefonts
```

If this succeeds, you can always try re-installing afterwards, but as I pointed out earlier, I don't think it is necessary.

---

### Post by stinger30au on 2008-06-20
> **smith_fan said:**
> Do you have any thoughts on how I can get rid of these nagging messages?:confused:    I wish I could remember what it was that I was messing with that started them.


this may help.
click on applications , add remove programs

click show all available applications

search on

font


the first box that comes up says 

ubuntu restricted extras.

it has the ms fonts and other goodies.

i bet if you install this and restart the pc all the be good again.

also the 3rd box down as MS core fonts, just intsall that on its own and it should do the trick too

---

### Post by smith_fan on 2008-06-21
dwhitney,
All done, errors in processing 1 file(s)
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
darin@Belinda:~$

Stinger,
I feel really stupid about this, but I'm not sure how to instruct it to install those again; unchecking and then re-checking the boxes doesn't enable the 'apply changes' button.  What do I need to do?

Thank you both!,
~D~

---

### Post by gjk on 2008-06-21
Did you try it via the command line yet?
try a reinstall or a forced install. I haven't personally used these switches. The plain vanilla install has always worked for me.

apt-get install package --reinstall
apt-get -f install package

Good Luck

---

### Post by smith_fan on 2008-06-21
"
darin@Belinda:~$ sudo apt-get install package microsoftcorefonts --reinstall
[sudo] password for darin:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package package
darin@Belinda:~$ 
"
Where does a person look to find an official package name?

I'm able to remove and then reinstall Ubuntu Restricted Extras package via the Add/Remove Applications applet, but the MS core fonts one always produces an error.

Anybody have an idea for me?

Thanks!,
~D~

---

### Post by avtolle on 2008-06-21
The package name is msttcorefonts, as reflected in the error messages.

---

### Post by smith_fan on 2008-06-21
Okay, but still no luck:
"
darin@Belinda:~$ sudo apt-get install package msttcorefonts --reinstall
[sudo] password for darin:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package package
darin@Belinda:~$ 
"
Anyone know what "package package" is all about?:confused:

---

### Post by nanotube on 2008-06-21
> **smith_fan said:**
> Okay, but still no luck:
"
darin@Belinda:~$ sudo apt-get install package msttcorefonts --reinstall
[sudo] password for darin:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package package
darin@Belinda:~$ 
"
Anyone know what "package package" is all about?:confused:

yea, the command should be ```
sudo apt-get install msttcorefonts --reinstall
``` (no word "package".)
otherwise, it's looking for two packages, "package" and "msttcorefonts" which is not what you want. :)

---

### Post by gjk on 2008-06-22
Don't type the word package in the command line the word package is a placeholder for the package itself. 

As nanotube said:
sudo apt-get install msttcorefonts --reinstall

You might want to consider starting fresh by first cleaning up any partially downloaded or no longer existing package.
sudo apt-get autoclean

You can then do a sanity check for broken packages & ask the system to fix any dependency via:
sudo apt-get -f install

After you perform the above steps verify if msttcorefonts exists
sudo apt-cache pkgnames | sort > pk.txt
You can check the text file with your favorite editor or parse it from the command line. If the package is not installed follow nanotube's directions

Good Luck!

---

### Post by smith_fan on 2008-06-22
I'm almost speechless I am so embarrassed. 

Gjk, I ran nanotube's suggested command before reading your suggestions.  And, since yours were sequence-specific, I'm sure that by running them after I'd already rushed through the previous recommendation, that they didn't serve their intended purpose.  For the sake of clarity, I am just going to paste everything from the Terminal window:
"
darin@Belinda:~$ sudo apt-get install msttcorefonts --reinstall
[sudo] password for darin:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libwxgtk2.6-0 libwxbase2.6-0 python-wxversion python-wxgtk2.6
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up msttcorefonts (2.2) ...

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
darin@Belinda:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del clamav-base 0.92.1~dfsg2-1.1~gutsy2 [12.7MB]
Del clamav 0.92.1~dfsg2-1.1~gutsy2 [895kB]
Del libclamav3 0.92.1~dfsg2-1.1~gutsy2 [448kB]
Del xnest 2:1.3.0.0.dfsg-12ubuntu8.3 [1407kB]
Del openssl-blacklist 0.3.3+0.4-0ubuntu0.7.10.1 [6333kB]
Del clamav-docs 0.92.1~dfsg2-1.1~gutsy2 [1036kB]
Del clamav-docs 0.92.1~dfsg2-1.1~gutsy1 [1036kB]
Del clamav-freshclam 0.92.1~dfsg2-1.1~gutsy2 [218kB]
darin@Belinda:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libwxgtk2.6-0 libwxbase2.6-0 python-wxversion python-wxgtk2.6
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up msttcorefonts (2.2) ...

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
darin@Belinda:~$ sudo apt-cache pkgnames | sort > pk.txt
darin@Belinda:~$ 
"
Since managing to disable the sound and clearing the 'Third-party Software' tab of any repositories in Synaptic, I am wondering if I wouldn't just be better off with a fresh install of Hardy...

I've been told that if I make a copy of my Home folder and all hidden files, that I could essentially transport my *profile* to another computer.  How can I make these hidden files visible?

Thanks for your help!,
~D~

---

### Post by nanotube on 2008-06-22
> **smith_fan said:**
> 
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.


well, it looks like you have some weird proxy server settings.... do you access the net through a proxy?

> 
I've been told that if I make a copy of my Home folder and all hidden files, that I could essentially transport my *profile* to another computer.  How can I make these hidden files visible?


in nautilus: view -> show hidden files
"hidden files" are merely files with filenames that begin with a dot. nothing fancy about them.
yes, if you copy your entire home dir, you can put it right back in on a fresh install, and have all your data.

---

### Post by smith_fan on 2008-06-22
Nope--don't use a proxy.  I'm sure that I probably messed something up when trying to set-up TOR/Privoxy.  Is there a quick method of returning the default networking settings?

Thanks for the hidden files tip!:) 76 objects when showing everything versus 22 objects when not.

---

### Post by nanotube on 2008-06-22
> **smith_fan said:**
> Nope--don't use a proxy.  I'm sure that I probably messed something up when trying to set-up TOR/Privoxy.  Is there a quick method of returning the default networking settings?


i've never set those up myself, so i am not sure what exactly the process entails - and thus don't know how to undo it. 

a quick guess: check in system> preferences> network proxy

---

### Post by smith_fan on 2008-06-22
I haven't done any research on that, till now.  Now I need to fix it, cuz my bro-in-law says it's causing a problem with WGet.  He was just here trying to quickly fix some missing repositories for me.

I'm sure that there's some fairly simple way to bring back default network settings.  Thanks for your help!

~D~

---

