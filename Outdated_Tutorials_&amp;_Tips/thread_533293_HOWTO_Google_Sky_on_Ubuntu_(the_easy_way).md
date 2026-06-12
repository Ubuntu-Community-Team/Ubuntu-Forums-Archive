---
title: "HOWTO: Google Sky on Ubuntu (the easy way)"
date: 2007-08-23
forum: Outdated Tutorials &amp; Tips
---

### Post by Pesho on 2007-08-23
[Google Sky]("http://earth.google.com/sky/index.html") is the major new feature in the [just released]("http://googleblog.blogspot.com/2007/08/view-from-sky.html") Google Earth 4.2. The proper way to install new applications on Ubuntu is using the package manager. However, Google does not provide a .deb package, so we will have to build one ourselves. Fortunately, it's very easy:

First, download and install the latest version of *googleearth-package*:

```
wget http://ftp.debian.org/debian/pool/contrib/g/googleearth-package/googleearth-package_0.3.2_all.deb
sudo dpkg -i googleearth-package_0.3.2_all.deb
sudo apt-get install -f
```Now use *googleearth-package* to automatically create a .deb package for the latest Google Earth:

```
make-googleearth-package
```Finally, install the resulting package:

```
sudo dpkg -i googleearth_4.2.180.1134+0.3.2-1_i386.deb
sudo apt-get install -f
```That's all. Start it from *Applications* -> *Internet* -> *Google Earth*. Press the *Sky* button and enjoy.


Note 1: Tested on Ubuntu Feisty 32-bit, but should work on any version of Ubuntu. On 64-bit architectures you may have to specify the *--force* option for *make-googleearth-package*.

Note 2: Source: [http://buglandia.blogspot.com/2007/08/howto-google-sky-on-ubuntu.html](http://buglandia.blogspot.com/2007/08/howto-google-sky-on-ubuntu.html)

---

### Post by larrybrazos on 2007-08-26
thanks!!

---

### Post by sandrinux on 2007-08-26
mmmh...
When i do :

make-googleearth-package

it build the version 

googleearth_4.1.7076.4458+0.3.0-1_i386.deb


so the software installed is the old version, without the "sky" button.


I tryed to search in 
[http://ftp.de.debian.org/debian/pool/contrib/g/googleearth-package/](http://ftp.de.debian.org/debian/pool/contrib/g/googleearth-package/)

and there is a newer version , the 0.3.1-1

but is just the same, no sky button.

---

### Post by larrybrazos on 2007-08-26
i can confirm it worked for me.

---

### Post by Pesho on 2007-08-26
> **sandrinux said:**
> mmmh...
When i do :

make-googleearth-package

it build the version 

googleearth_4.1.7076.4458+0.3.0-1_i386.deb


so the software installed is the old version, without the "sky" button.


You probably have an older version of GoogleEarthLinux.bin in the working directory. Delete it, and make-googleearth-package will download the new version.

---

### Post by DemoN3x on 2007-08-27
> **Pesho said:**
> [Google Sky]("http://earth.google.com/sky/index.html") is the major new feature in the [just released]("http://googleblog.blogspot.com/2007/08/view-from-sky.html") Google Earth 4.2. The proper way to install new applications on Ubuntu is using the package manager. However, Google does not provide a .deb package, so we will have to build one ourselves. Fortunately, it's very easy:

First, download and install the latest version of *googleearth-package*:

```
wget [http://ftp.debian.org/debian/pool/contrib/g/googleearth-package/googleearth-package_0.3.2_all.deb](http://ftp.debian.org/debian/pool/contrib/g/googleearth-package/googleearth-package_0.3.2_all.deb)
sudo dpkg -i googleearth-package_0.3.2_all.deb
sudo apt-get install -f
```Now use *googleearth-package* to automatically create a .deb package for the latest Google Earth:

```
make-googleearth-package
```Finally, install the resulting package:

```
sudo dpkg -i googleearth_4.2.180.1134+0.3.0-1_i386.deb
sudo apt-get install -f
```That's all. Start it from *Applications* -> *Internet* -> *Google Earth*. Press the *Sky* button and enjoy.


Note 1: Tested on Ubuntu Feisty 32-bit, but should work on any version of Ubuntu. On 64-bit architectures you may have to specify the *--force* option for *make-googleearth-package*.

Note 2: Original URL of this HOWTO: [[link]("http://buglandia.blogspot.com/2007/08/howto-google-sky-on-ubuntu.html")]

Note 3: If this how-to was useful to you, please [digg it]("http://digg.com/linux_unix/HOWTO_Google_Sky_on_Ubuntu_Debian_the_easy_way").

Worked ok for me with a couple of adjustments.  I had to install fakeroot first.

The resulting package was sudo dpkg -i googleearth_4.2.180.1134+0.3.**[COLOR=Red]2[/COLOR]**-1_i386.deb

---

### Post by Pesho on 2007-08-27
> **DemoN3x said:**
> Worked ok for me with a couple of adjustments.  I had to install fakeroot first.


'*sudo apt-get install -f*' should have taken care of that.

---

### Post by staib on 2007-08-28
> **Pesho said:**
> You probably have an older version of GoogleEarthLinux.bin in the working directory. Delete it, and make-googleearth-package will download the new version.

Hi

Thanks for this - I had been hoping that some kind soul would be around with an answer!

However - like others I have deleted Google Earth - then followed your steps - only to see the 'old beta' version back again :confused:

Please can you just advise (or tell me the commands) how to get rid of that old bin file as I'm not 100% sure what the working directory is (still being a newbie and all) - and deleting the wrong file scares me me more than wanting to see the Universe!

Thanks,

Nick

---

### Post by Pesho on 2007-08-28
> **staib said:**
> Please can you just advise (or tell me the commands) how to get rid of that old bin file as I'm not 100% sure what the working directory is (still being a newbie and all) - and deleting the wrong file scares me me more than wanting to see the Universe!

Just execute 

```
rm GoogleEarthLinux.bin
``` 

before 

```
make-googleearth-package
```

---

### Post by staib on 2007-08-28
Thanks for the prompt reply - but having just followed the steps again - removing Google Earth (using Synaptic) inserting the 'rm GoogleEarthLinux.bin' bit where appropriate - and adding that DemoN3x bit about the version number (...googleearth_4.2.180.1134+0.3.2-1_i386.deb) I am still confused!

Synaptic shows the current version of Google Earth (4.2.180.1134+0.3.2-1) as being the new one (it even refers to it as being a 3d map/planet viewer) - but launching from the Applications > Internet > Google Earth menu pulls up the old one - which I thought I had deleted...)

I think what has happened is that I had a Google Earth before via Automatix2 (which I no longer use) and the menu item is linking to that one - instead of the new one...

Any suggestions for finding the new one and then adding it to the menu?

Thanks again.

---

### Post by Pesho on 2007-08-28
When installed via the package, the Google Earth binary is placed at /usr/bin/googleearth. Try starting it directly, it should be the new version. If that's the case, just edit the menu entry to point to this location.

---

### Post by staib on 2007-08-28
Thanks again my friend...

I WISH I could say it worked...

OK I did as you suggested (I think) used Terminal to cd into /usr/lib/googleearth than just typed (again in Terminal) googleearth

but that just launched the old original version!

The only thing at /usr/lib/googleearth seems to be a 148byte 'shell script' which when opened with a double click reads:

#!/bin/bash
export LD_LIBRARY_PATH=/usr/lib/googleearth:"${LD_LIBRARY_PATH}"
cd /usr/lib/googleearth
exec /usr/lib/googleearth/googleearth-bin "$@"

I can't pretend to understand too much of this and have to get back to work now - but if you have any ideas let me know :-)

Cheers,

Nick

---

### Post by _simon_ on 2007-08-28
The title is a little wrong, this isn't the easiest way.

The easiest is to download the .bin from the google earth website.
Then from terminal sudo sh nameofinstaller.bin

That's it!

---

### Post by Pesho on 2007-08-28
> **staib said:**
> WISH I could say it worked...

OK I did as you suggested (I think) used Terminal to cd into /usr/lib/googleearth than just typed (again in Terminal) googleearth

but that just launched the old original version!...


OK, first I wrote /usr/bin..., not /usr/lib... as you did. Second, you shouldn't 'cd' there and type 'googleearth', this doesn't work as in Windows. On Ubuntu, the current directory isn't searched when running a binary, for security purposes. 

What you should do instead is simply open a terminal and type '/usr/bin/googleearth'.


> **_simon_ said:**
> The title is a little wrong, this isn't the easiest way.

The easiest is to download the .bin from the google earth website.
Then from terminal sudo sh nameofinstaller.bin


Perhaps I should rename the title to "...the proper way" then?

---

### Post by _simon_ on 2007-08-28
Not sure there is a "proper way"?

---

### Post by staib on 2007-08-30
> **Pesho said:**
> OK, first I wrote /usr/bin..., not /usr/lib... as you did. Second, you shouldn't 'cd' there and type 'googleearth', this doesn't work as in Windows. On Ubuntu, the current directory isn't searched when running a binary, for security purposes. 

What you should do instead is simply open a terminal and type '/usr/bin/googleearth'.

Finally :guitar:

Thanks Pesho - got it all working now - I appreciate your help :)

Nick

---

### Post by phyzik on 2007-09-19
How to update Google Earth installed using this this method? Do you just
```
make-googleearth-package
```
and then
```
sudo dpkg -i googleearth_4.2.xxxx_i386.deb
sudo apt-get install -f
```
or do I have to do it all over again (an perhaps even uninstall the old version first)?

thx,
damien

---

### Post by Pesho on 2007-09-19
> **damien37 said:**
> How to update Google Earth installed using this this method? Do you just...


Basically yes. You don't need to do it all over again. Just make sure to remove any old GoogleEarthLinux.bin you might have in the working directory (so that make-googleearth-package will download the newest version).

---

### Post by rfruth on 2007-09-19
This is good to know but what does doing it by hand buy me (why not just get the latest-n-greatest GE BIN file from the google earth site) :confused:

---

### Post by phyzik on 2007-09-19
> **rfruth said:**
> This is good to know but what does doing it by hand buy me (why not just get the latest-n-greatest GE BIN file from the google earth site) :confused:

Because this way it's like you installed a .deb file - definitely a better way to install applications in Ubuntu (and any other debian-based distro).

@Pesho: thanks for the quick reply :)

---

### Post by BLTicklemonster on 2007-10-31
or go here and install the latest deb


[http://ftp.debian.org/debian/pool/contrib/g/googleearth-package/](http://ftp.debian.org/debian/pool/contrib/g/googleearth-package/)

---

### Post by TheMacOne on 2007-10-31
Heya party ppl,

Just tried as the thread said and got nowhere. Got the prev poster's error about a wrong version or something.. :(

I have already installed the current version of googleearth-package through synaptics by searching for "googleearth". :D

I downloaded the current version from earth.google.com download page.
Direct link below: [HTML]http://dl.google.com/earth/client/current/GoogleEarthLinux.bin[/HTML]

So, one I d/l'd the file, I  cd into where the downloaded file was and then I tried:
```
sudo make-googleearth-package --file <file location>/GoogleEarthLinux.bin --force
```

In my case, the file location was ~/Downloads folder (yours will more than likely vary) and once I issued that command, it made (after a few minutes) a Google Earth deb pkg in my home folder.

Installed the deb using GDebi Installer in the System menu (gutsy ubuntu) and installed fine.

Works fine for basic use, haven't tried the other eye candy :)
Hope this helps someone. :)

---

### Post by Illumina on 2007-12-04
i have installed the google earth.. but everytime i start it... it got freeze... the screen turn to gray... and it can't run..... and it makes my processor works harder.... why can this happened?

i have this error message 

Xlib:  extension "XFree86-DRI" missing on display ":1.0".

---

### Post by KaYnemO on 2007-12-04
I've got Google Earth to install but it just freezes on startup... maybe it's the internet proxy, but it wouldn't even give me a config screen %(

---

### Post by glennric on 2007-12-04
googleearth is in the medibuntu repositories with the googlesky feature enabled.  Add deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free to the file /etc/apt/sources.list, then run sudo apt-get update, sudo apt-get install googleearth.  Go to [http://medibuntu.org]("http://medibuntu.org") for more information.

---

### Post by schneidexe on 2008-04-16
Hi Folks,

to bad the script does not work with the latest Google Earth 4.3. I added the --force option, but the resulting package does not work at all.

So I installed directly it with the .bin-Installer. Sure it's now not in the package manager, but it works for me (on Feisty).

Greetz

schneidexe

ATTENTION: After the Installation with sudo don't press the START button, press QUIT and start manually or you will get config-files with wrong rights!

---

