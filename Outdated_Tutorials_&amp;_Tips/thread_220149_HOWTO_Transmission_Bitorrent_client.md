---
title: "HOWTO: Transmission Bitorrent client"
date: 2006-07-21
forum: Outdated Tutorials &amp; Tips
---

### Post by no1wantdthisname on 2006-07-21
Homepage: [http://transmission.m0k.org/](http://transmission.m0k.org/)

UPDATE: It seems that Transmission is banned from some private trackers.  You can check the forums for the details but apparently it updates from the tracker too much.  However, I've only seen one torrent out of 100+ that was banned.  It looks like it'll be fixed soon anyway.
Applecrow has a repo up for those who are lazy: [http://www.ubuntuforums.org/showpost.php?p=1323194&postcount=22](http://www.ubuntuforums.org/showpost.php?p=1323194&postcount=22)



I've used most of the bittorrent clients but this client takes the least amount of cpu/ram for a GUI.  
Transmission idles around 2-5% cpu load with a max of maybe 15% load.  This is with 3+ torrents going.  
Azureus on the same computer idles around 10% and I've seen it jump to 100% load using the official sun java.  
I see the same thing with the official client and some others.  Again, this is with 3+ torrents.  The official client seems to have the worst cpu usage for me (30-40% cpu when idle and 0 torrents going).  

I prefer the simple interface as well (See attached screenshot). 
Note: there's no upnp/encryption support so stick to Azureus if you need that.

Anyway, you can either download the current version (0.6.1 atm) from the front page or get it via subversion.  


Regardless of which you want:
```
sudo apt-get install libgtk2.0-dev libssl-dev build-essential
```

I've been using subversion and there haven't been any problems so far.
If you want to try it:
```
sudo apt-get install subversion
cd ~/
svn co svn://svn.m0k.org/Transmission/trunk Transmission
```

When you want to update the source just go into the directory and
```
svn update
```

Transmission currently doesn't have a application icon so it uses the default window icon.
I noticed that it only requires one line to add to the code if you want an icon so:
```
gedit ~/Transmission/gtk/main.c
```
Find this line (It's around line 214):
```
mainwind = gtk_window_new(GTK_WINDOW_TOPLEVEL);
```
and add under it:
```
 gtk_window_set_icon_from_file(GTK_WINDOW(mainwind),"/opt/transmission/transmission_icon.png",NULL);
```
Attached at bottom is an icon I got/altered from this page: [http://iconaholic.com/downloads.html#transmission](http://iconaholic.com/downloads.html#transmission)
```
sudo mkdir /opt/transmission
sudo mv transmission_gtk.png /opt/transmission/
```

Now to configure/install.
The prefix=/opt/transmission is installing in /opt for easy removal.
```
cd Transmission
./configure --prefix=/opt/transmission
make
sudo make install
sudo ln -s /opt/transmission/bin/transmission-gtk /usr/local/bin/transmission-gtk
sudo ln -s /opt/transmission/bin/transmissioncli /usr/local/bin/transmissioncli

```

And you're done.  See screenshot.
```
transmission-gtk
``` to start it

If you want to remove transmission just
```
sudo rm /opt/transmission -R
sudo rm /usr/local/bin/transmission*
```

---

### Post by congafx on 2006-07-24
awesome, thanks alot for this! it worked flawlessly for me!

---

### Post by Tiftof on 2006-07-25
Great Howto. But while I was searching for more info about this great program I stumbled upon this: [http://gir.deefa.com/debian/transmission/](http://gir.deefa.com/debian/transmission/) Nice debian package for transmission that worked great for me on Dapper.

---

### Post by TheSeal on 2006-07-25
Im not good at this in didnt get it to work.

when i sould do:
```
sudo ln -s /opt/transmission/bin/transmission-gtk /usr/local/bin/transmission-gtk
sudo ln -s /opt/transmission/bin/transmissioncli /usr/local/bin/transmissioncli
```
i got:
"/usr/local/bin/transmission-gtk file or folder doesnt exist" or something like that (i got it in swedish and dont know the english expression)


(yes im new to ubuntu) :P

---

### Post by no1wantdthisname on 2006-07-25
Do
```
sudo mkdir -p /usr/local/bin 
```
before that command then.

---

### Post by bionnaki on 2006-07-25
just to note, transmission is banned on [removed name of filesharing site]

---

### Post by saracen on 2006-07-26
@no1wantdthisname: what's that dock that you're using?  And the GTK theme?

@tiftof: I get a dependency not satisfied error when I try to install the deb from the site you gave.  The dependency is for libc6... but i have that installed...

---

### Post by no1wantdthisname on 2006-07-27
The libc6 error is probably because debian has a more updated version.  You would have to unpack the deb and change the version requirements.  

If you really want to then you would have to:
```
mkdir blah
dpkg-deb -x (the .deb file) blah
mkdir blah/DEBIAN
dpkg-deb -e (the .deb file) blah/DEBIAN
gedit blah/DEBIAN/control
```
remove the version requirements for libc6 and finally
```
dpkg-deb -b blah blah.deb
sudo dpkg -i blah.deb
```
It's not really worth the trouble for the 3 files that transmission installs.   

The dock is kiba-dock.
The original: [http://people.freedesktop.org/~krh/akamaru.git/](http://people.freedesktop.org/~krh/akamaru.git/) 
Another version: [http://www.compiz.net/viewtopic.php?id=1972](http://www.compiz.net/viewtopic.php?id=1972)

It seems the second one is updated more frequently and has more options like text support.
EDIT: Forgot to mention that kiba-dock doesn't seem to work without compiz.  Using metacity results in black boxes.

---

### Post by zenwhen on 2006-07-27
Awesome! I will switch to this once I have properly seeded  the torrents I am on now.

---

### Post by mustang on 2006-07-28
Thank you for the guide. Unfortunately, I'm stuck at the first step:

```

manish@ubuntu:~$ sudo apt-get install libgtk2.0-dev libssl-dev build-essential
Password:
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
                 Depends: libcairo2-dev but it is not going to be installed
                 Depends: libxcursor-dev but it is not going to be installed
                 Depends: libxfixes-dev but it is not going to be installed
E: Broken packages

```

---

### Post by no1wantdthisname on 2006-07-28
Does your /etc/apt/sources.list look something like this?

```

deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

```

---

### Post by mustang on 2006-07-28
> **no1wantdthisname said:**
> Does your /etc/apt/sources.list look something like this?

```

deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

```

I'm using the US mirrors but otherwise yes, it's similar. Just to check, I cleared my sources.list and pasted what you posted and did an update. I get the same error.

---

### Post by lzfy on 2006-07-30
When I do "sudo ln -s /opt/transmission/bin/transmissioncli /usr/local/bin/transmissioncli" I'm getting an error. But the app works fine :)

Oh, I would like to create a deb file of this so that I can install it on other machines without compiling, is there an easy way to do this?

Another question, can I remove the Transmission folder from my home dir?

thanks for the howto :p

---

### Post by kpolice on 2006-07-31
If you don't care about the icon just compile it and copy the transmission-gtk file to /usr/bin and create a shortcut in your desktop or anywhere you want. 

To uninstall it just remove the file and yes you can remove the folder with the sources once you have moved or copied the transmission-gtk binary.

EDIT
Actually it's easier :P 

1. ./configure
2. make
3. make install

And it will install it, well it just copies the binary to /usr/bin

---

### Post by mustang on 2006-07-31
Yes, a deb would be most appreciated for those of us (ok ok, me) who are having problems with the compilation.

---

### Post by kpolice on 2006-07-31
Not a deb but just copy it to /usr/bin and add a launcher :P

---

### Post by bugzor on 2006-07-31
[http://koti.mbnet.fi/laurie/deb/transmission_20060710-1_i386.deb](http://koti.mbnet.fi/laurie/deb/transmission_20060710-1_i386.deb)
compiled from svn (10.7.2006)
and packed with checkinstall it should work fine 
i cant quarantee that it works for you

---

### Post by lzfy on 2006-07-31
> When you want to update the source just go into the directory and

svn update

Can you explain me what this part means? Can I update the source and then recompile?

sorry for the noob questions :rolleyes:

---

### Post by kpolice on 2006-07-31
you execute svn update when you want to update the sources to the latest version and then you have to recompile again.

---

### Post by lzfy on 2006-07-31
> **kpolice said:**
> you execute svn update when you want to update the sources to the latest version and then you have to recompile again.

Do you have to remove the old version first? the one in /usr/bin. Or is it all automated.

---

### Post by kpolice on 2006-07-31
It will be replaced with the new version so the steps are:

1. svn update
2. ./configure
3. make
4. sudo make install

You will have an updated transmission.It's what I do every week.

---

### Post by AppleCrow on 2006-07-31
If somebody is interested by transmission's package, I've uploaded some here:
[http://acorbeaux.free.fr/packages]("http://acorbeaux.free.fr/packages")

Tomorrow I will upload the build from the SVN snapshot 706.

---

### Post by lzfy on 2006-08-01
> **kpolice said:**
> It will be replaced with the new version so the steps are:

1. svn update
2. ./configure
3. make
4. sudo make install

You will have an updated transmission.It's what I do every week.

Thanks :) I'll do this too.

---

### Post by mikedpirone on 2006-08-01
I followed your how-to to the T and got it installed and working. Only thing is it seems that downloads move extremely slow compared to Azureus. I downloaded the same file with both and finished the dl in Azureus in nearly 1/4 the time it took Transmission. Is there something I did wrong?

---

### Post by no1wantdthisname on 2006-08-01
I wouldn't know why you're getting slow speeds.  The only thing I can think of is a closed port.

I seem to be getting the same speeds if not faster than Azureus.  Then again, I tend to leave Transmission alone for hours at a time.

---

### Post by lzfy on 2006-08-01
Is there a way to minimize the app to the tray?

---

### Post by lazyd2 on 2006-08-01
> **lzfy said:**
> Is there a way to minimize the app to the tray?None that I know of...

*edit* you could try something like "Alltray"...

---

### Post by lazyd2 on 2006-08-01
> **AppleCrow said:**
> If somebody is interested by transmission's package, I've uploaded some here:
[http://acorbeaux.free.fr/packages](http://acorbeaux.free.fr/packages)

Tomorrow I will upload the build from the SVN snapshot 706.Fantastic! :)
Thanks.

---

