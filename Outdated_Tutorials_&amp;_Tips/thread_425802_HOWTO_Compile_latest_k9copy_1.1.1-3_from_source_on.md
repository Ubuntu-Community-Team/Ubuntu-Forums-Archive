---
title: "HOWTO: Compile latest k9copy 1.1.1-3 from source on Feisty"
date: 2007-04-27
forum: Outdated Tutorials &amp; Tips
---

### Post by kpkeerthi on 2007-04-27
1. Install the dependencies for the k9copy binary
```

sudo aptitude install dvdauthor libdvdread3 mencoder mplayer libhal1 libdbus0 libdbus-qt-1-1

```

2. Install the dependencies for the build
```
sudo aptitude install libdvdread3-dev libqt3-headers libqt3-mt-dev kdebase-dev kdelibs4-dev libqt3-mt-dev qt3-dev-tools libqt3-headers libjpeg62-dev build-essential checkinstall libhal-dev libdbus-qt-1-dev libhal-storage-dev
```

3.  Download the source from [http://k9copy.sourceforge.net/index.php](http://k9copy.sourceforge.net/index.php) ([[COLOR="Blue"]**Direct link**[/COLOR]]("http://downloads.sourceforge.net/k9copy/k9copy-1.1.1-3.tar.gz"))

4. Extract the tar. On my setup, the files are in  $HOME/dev/k9copy-1.1.1-3 

5. Open terminal and navigate to ~/dev/k9copy-1.1.1-3
```

:> cd dev/k9copy-1.1.1-3

```

6. Configure &  build
[INDENT]   6.a[/INDENT]
```

:> ./configure

```
[INDENT]   6.b[/INDENT]  
```

:> make

```

7. Build the deb file
```

:> sudo checkinstall --install=no

```
**Note:** --install=no option will only build the deb which you may install later.

8. Install the deb
```

:> sudo dpkg -i  k9copy-1.1.1_3-1_i386.deb

```

9. k9copy should now be installed. A little quirk is that it gets installed to /usr/local/kde/bin/k9copy which is not in the $PATH. You may want to symlink that to /usr/bin/k9copy.
```

sudo ln -s /usr/local/kde/bin/k9copy /usr/bin/k9copy

```

10. Lets create a Menu shortcut under Applications -> Sound & Video
[INDENT]9.a[/INDENT]
[INDENT]```
gksudo gedit /usr/share/applications/k9copy.desktop
```[/INDENT]
[INDENT]9.b[/INDENT]
[INDENT]Copy & paste the below content into the file[/INDENT]
[INDENT]```

[Desktop Entry]
Name=k9copy
Comment=DVD ripper
Exec=k9copy
Icon=/usr/local/kde/share/icons/hicolor/48x48/apps/k9copy.png
Type=Application
Categories=Application;AudioVideo;

```
Save and Exit.[/INDENT]

=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
I have also uploaded the deb here for those who may be interested.
**[COLOR="Red"]http://rapidshare.com/files/28307457/k9copy-1.1.1_3-1_i386.deb.html[/COLOR]**
=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=

Rock on :guitar: 
Suggestions and feedback welcome!

---

### Post by kpkeerthi on 2007-04-28
Attached screenshot

---

### Post by kpkeerthi on 2007-05-03
Did anyone find this useful? Works? Did not work? Come one guys.. I need some motivation! :)

---

### Post by laberer on 2007-05-11
Thanks for the package!

I had to remove the old version with synaptic manually.
Otherwise the old version started everytime i called k9yopy

---

### Post by enjoy_freestyle on 2007-05-12
thank's for this guide!

it was very usefull, because i noticed some problems with the package included in ubuntu feisty...
now i try my fresh compiled k9copy!!

bye

Diego:)

---

### Post by derekguy on 2007-05-13
Followed the instructions from source and got this error:

```
$ sudo dpkg -i k9copy-1.1.1_3-1_i386.deb 
(Reading database ... 186836 files and directories currently installed.)
Unpacking k9copy-1.1.1 (from k9copy-1.1.1_3-1_i386.deb) ...
dpkg: error processing k9copy-1.1.1_3-1_i386.deb (--install):
 trying to overwrite `/usr/local/kde/bin/k9copy', which is also in package k9copy-1.1.0-beta1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 k9copy-1.1.1_3-1_i386.deb
```

I'm just a n00b so not quite sure what broken pipe means, perhaps a dependancy? Cheers for any help.

I got the same error using your .deb file

---

### Post by enjoy_freestyle on 2007-05-14
maybe you had already installed k9copy from apt...

try

sudo apt-get remove k9copy 

before running dpkg -i ...

I'm not so happy aboout this new package...
it hangs a lot of times...

bye

---

### Post by Useff on 2007-05-14
Thanks for the package.

---

### Post by derekguy on 2007-05-15
Cheers, yes I had the beta1 package installed and it was not removing via apt-get but synaptic worked a treat. I will try it out to see if it hangs for me too.

Derek

---

### Post by kpkeerthi on 2007-05-16
k9copy does not hang for me. May be you should try compiling for yourself. Just a thought.

---

### Post by Foxmike on 2007-05-27
Thanks kpkeerthi!  That worked well for me!  I have put your how-to in [_UDSF_]("http://doc.gwos.org/index.php/K9copy").

If you have any comment/modifications, please tell me it will be my pleasure to correct it!:)

Regards,

-FM

---

### Post by bennyj on 2007-05-28
> **kpkeerthi said:**
> Did anyone find this useful? Works? Did not work? Come one guys.. I need some motivation! :)

Worked like a charm...thanks for the how to and good job:D

---

### Post by borovy3488 on 2007-08-12
just so you know, that was awesome...

:guitar:

---

### Post by joris1977 on 2007-09-09
thanks!

Great howto:

I was struggling with this howto in the community docs: [https://help.ubuntu.com/community/BuildingK9CopyfromSource](https://help.ubuntu.com/community/BuildingK9CopyfromSource)

maybe someone should update it... 

I feel like i'm still too new too ubuntu to edit wikis

---

### Post by 61811 on 2007-09-10
Install for 1.1.3 went without any hitch. Thanks for the great set of instructions. 

Now, wish that someone would do the same for DVD95 (1.2p0 > 1.2p1) for us Gnome users.

---

### Post by genbuntu on 2007-09-11
> **kpkeerthi said:**
> Did anyone find this useful? Works? Did not work? Come one guys.. I need some motivation! :)

Thanks kpkeerthi. Worked well for me. Had to change the name in step though.

---

### Post by lusephur on 2007-09-30
worked like a charm, thank you very much :o)

---

### Post by ktvps on 2007-10-01
I am using Feisty on my 64-bit computer and I have followed the steps to install K9copy1.1.1-3 but i got this message:


Installing with make install...

========================= Installation results ===========================
make: *** No rule to make target `configure.in.in', needed by `configure.in'. Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

Any ideas what I can do?
I have been using other versions of K9copy but they all make my computer hang.  I don't have a clue what I'm doing so any help would be appreciated!

---

