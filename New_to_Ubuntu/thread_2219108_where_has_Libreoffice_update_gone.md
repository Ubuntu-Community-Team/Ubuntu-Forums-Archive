---
title: "where has Libreoffice update gone"
date: 2014-04-23
forum: New to Ubuntu
---

### Post by bobmac on 2014-04-23
Folks,
I went to update the Libreoffice version that came with version 12.4 LTS (with all the latest updates). Libreoffice said that they no longer supported this version (3.x.x) so I downloaded the latest version from the website. However, I cannot locate the new version on my system.

I'd be grateful if someone could tell me where to find it and how to install it.

Regards,

Bob

---

### Post by monkeybrain20122 on 2014-04-23
Do you mean you installed it but can't find the installed files or that you don't know where the download files have gone?

Instead of downloading from LO's site the better way would be to install from ppa, it will integrate better with the system and you will receive updates when available
[https://launchpad.net/~libreoffice/+archive/ppa](https://launchpad.net/~libreoffice/+archive/ppa)

To upgrade with the ppa, in the terminal run
```
sudo add-apt repository ppa:libreoffice/ppa
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by bobmac on 2014-04-23
I'm afraid that it seems that I'm a dimwit. I have no idea how to how to go about doing this ppa thing.
I tried the code that you kindly sent but it didn't seem to work as I still can't find the program.

Regards,

Bob

---

### Post by speartip on 2014-04-23
> **bobmac said:**
> I'm afraid that it seems that I'm a dimwit. I have no idea how to how to go about doing this ppa thing.
I tried the code that you kindly sent but it didn't seem to work as I still can't find the program.

Just open a terminal & enter the lines one by one, hitting enter after each line & putting in your password.
LO should now update to the latest version.

---

### Post by bobmac on 2014-04-26
Tried Speartip's tip. All I got after I entered the first line and my password was a message:
sudo: add-apt: command not found

regards

Bob

---

### Post by monkeybrain20122 on 2014-04-26
Sorry

should be add-apt-repository

---

### Post by bobmac on 2014-04-26
Monkeybrain 20122,

I tried your code but I get the same result.
The original code was
sudo add-apt repository ppa:libreoffice/ppa
sudo apt-get update
sudo apt-get upgrade

You also commented about the following:
Instead of downloading from LO's site the better way would be to install from ppa, it will integrate better with the system and you will receive updates when available
[https://launchpad.net/~libreoffice/+archive/ppa](https://launchpad.net/~libreoffice/+archive/ppa)

I'm afraid that I dont know what the last line means. Do I need to go to this site and do something from there?

Regards,
Bob

---

### Post by monkeybrain20122 on 2014-04-26
No, don't need to visit the site, just run those commands (change "sudo add-apt repository ppa:libreoffice/ppa" to "sudo add-apt-repository ppa:libreoffice/ppa")
The link is just the repoistory in case you want to see what is in there.

---

### Post by bobmac on 2014-04-26
Monkeybrain 20122,

Great it seemed to perform a download of lots of stuff, but I still can't find it. The icons at the LHS still point to vesion 3.

Regards,

Bob

---

### Post by monkeybrain20122 on 2014-04-26
What icon on the LHS?

---

### Post by bobmac on 2014-04-26
Monkeybrain 20122,

The original icon(s) for Libreoffice v3, that came with the 12.04 LTS version

Bob

---

### Post by bobmac on 2014-04-26
Monkeybrain 20122,

The original icon(s) for Libreoffice v3, that came with the 12.04 LTS version

Bob

---

### Post by bobmac on 2014-04-26
Monkeybrain 20122,

Please forgive my ignrance, The icons that I checked are the ones that came with the 12.04 installation (v3) Libreoffice

regards,

Bob

---

### Post by monkeybrain20122 on 2014-04-26
I don't understand what you're saying. The icons are always the same as far as I know. If you open the writer, go to Help > About Libreoffice it will tell you which version it is.

---

### Post by bobmac on 2014-04-26
Monkeybrain 20122,
When I open Writer, the screen that displays shows Libroffice 3, for a few seconds, then displays the writer page, Under Help|About Libreoffice, the version is:
Libreoffice 3.5.7.2 Build ID: 350m1(build2)

Bob

---

### Post by monkeybrain20122 on 2014-04-26
Well you said when you run those commands it downloaded and installed a lot of stuffs, what did it install?

What is the output of 
```
libreoffice --version
```

---

### Post by bobmac on 2014-04-26
Monkeybrain 20122,

LibreOffice 3.5 

Bob

---

### Post by monkeybrain20122 on 2014-04-26
Very strange. I am wondering whether you have successfully added the repository. Open the software centre, go to Edit > Preferences > Software Sources and then open the tab Other Software, do you see a line that looks like "..libreoffice/ppa/precise main"? Is the box checked?

---

### Post by speartip on 2014-04-26
Bobmac.
Best thing to do is start from scratch.
Lets delete libreoffice altogether.
```
sudo apt-get remove --purge libreoffice*
```
Then:
```
sudo apt-get autoremove
```
Then add the ppa:
```
[SIZE=2]sudo apt-add-repository **ppa:libreoffice/libreoffice-4-2**[/SIZE]
```
then:
```
sudo apt-get update
```
followed by:
```
sudo apt-get install libreoffice
```
You should now have the latest 4.2 version.

@monkeybrain20122...
I think the problem with the ppa is that it only gives the latest version for the version of Ubuntu you are using, So in Bobmacs case he still only gets the 3.5xxx version.
The ppa needs to be libreoffice-4-2, for the latest version.

---

### Post by Peter Maunder on 2014-04-26
If you are looking for LibreOffice on an Ubuntu 12.04 system, LibreOffice is installed in the "File System/opt/ libreofficex.y folder", where x.y represent the version. I.e. 4.2 for version 4.2.  This means that it is possible for multiple versions to co-exist on the same machine. For me that means a production and a testing version. 
 The user parameters are held in the  "Home/.config/libreoffice/x" folder where x is 4 for all the version 4, 3 for version 3 etc. .config is a hidden file so you need to toggle the hidden files using Ctrl h, if they are not currently showing.  I currently run Ubuntu 12.04 with 4.1 and 4.2 installed.

---

### Post by dskyracer2 on 2014-04-27
Thanks for these commands to upgrade libre office..  I just did them and they worked fine.. now have the latest in libre office... until I came here a day or so ago I had no idea libre office wasn't updating. I am using Linux Mint 13 LTS for now... very happy with it but also have a laptop with Ubuntu 12.04 so for my own good I need to refresh myself with what's going on ... haven't been back since someone hacked the forums... just returned... love all the great posts by those in the know.. Thank you again..

---

### Post by deadflowr on 2014-04-27
> **dskyracer2 said:**
> Thanks for these commands to upgrade libre office..  I just did them and they worked fine.. now have the latest in libre office... until I came here a day or so ago I had no idea libre office wasn't updating. I am using Linux Mint 13 LTS for now... very happy with it but also have a laptop with Ubuntu 12.04 so for my own good I need to refresh myself with what's going on ... haven't been back since someone hacked the forums... just returned... love all the great posts by those in the know.. Thank you again..

Two points

1)libreoffice on 12.04 still gets updates when they come, however since the developers at The Document Foundation have ended support for that version, the onus to patch it is completely on Canonical and The Ubuntu developers.

2) If you had an account on the forums, look over this please
[http://ubuntuforums.org/showthread.php?t=2164051](http://ubuntuforums.org/showthread.php?t=2164051)

---

### Post by dskyracer on 2014-04-27
Thanks for the link. I've worked at regaining my original account and here I am.. but now I think I have two accounts.. one with a hotmail address and one with a gmail address...earlier in trying to regain my account log in privledges I mistakenly used my hotmail email forgetting that my preferred email for the forums was with gmail.

 I upgraded my laptop's libre office just now too.. I'm on the laptop at the moment..works great.. I'm very grateful for the Ubuntu forums contributors, moderators, and great information which is so freely given. I've missed surfing here on the forum..didn't come back for quite a while because of the forums being hacked.. it's nice to return after so long. And again.. thanks for the commands to upgrade Libre office.. I love it and have many spread sheets with it.

---

