---
title: "Microsoft Media Server (MMS) protocol source plugin"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-05-13
Is there a link for the Microsoft Media Server (MMS) protocol source plugin?

Thanks

---

### Post by bbandy on 2008-12-12
> **saskatchewan said:**
> Is there a link for the Microsoft Media Server (MMS) protocol source plugin?

Thanks

Despite ten mile of computer jargon babble from the propeller heads, the answer is "no" and it is ticking me off!!!!!!!!!!!!!!!!!!!!!!
Bruce

---

### Post by hosoka on 2009-02-16
Hello saskatchewan,

Googled somewhat and found the solution for your case:

[https://answers.edge.launchpad.net/ubuntu/+question/34257](https://answers.edge.launchpad.net/ubuntu/+question/34257)


Kind regards,

Horatio:)

---

### Post by jman594 on 2009-06-22
Here's what worked for me:

```
sudo apt-get install vlc mozilla-plugin-vlc
```

It wasn't really listed here or on the site linked above. 

HTH someone somewhere... 

btw, i run 9.04 jaunty

---

### Post by cmltow on 2009-07-04
> **jman594 said:**
> Here's what worked for me:

```
sudo apt-get install vlc mozilla-plugin-vlc
```It wasn't really listed here or on the site linked above. 

HTH someone somewhere... 

btw, i run 9.04 jaunty


Thank you, this worked perfectly for me!

---

### Post by aboud on 2009-07-26
it's not working on my jaunty amd64 :(

---

### Post by nutcracker53 on 2009-08-04
> **jman594 said:**
> Here's what worked for me:

```
sudo apt-get install vlc mozilla-plugin-vlc
```It wasn't really listed here or on the site linked above. 

HTH someone somewhere... 

btw, i run 9.04 jaunty

hey guys, what does this program do.

---

### Post by mompracem on 2009-08-06
> **cmltow said:**
> Thank you, this worked perfectly for me!

Worked for me also, though I have no idea of what I did... :confused: :D

---

### Post by Tibuda on 2009-08-06
> **nutcracker53 said:**
> hey guys, what does this program do.

VLC is a video player. See [http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

---

### Post by newb85 on 2009-10-14
> **aboud said:**
> it's not working on my jaunty amd64 :(

Were you unable to install the player and plug-in, or did the plug-in fail to play the content you wanted?

Vlc is in the Canonical repository.  Make sure you have that enabled if you are unable to download the packages.  You can also install it through Synaptic.

---

### Post by vinan on 2009-11-02
> **jman594 said:**
> Here's what worked for me:

```
sudo apt-get install vlc mozilla-plugin-vlc
```It wasn't really listed here or on the site linked above. 

HTH someone somewhere... 

btw, i run 9.04 jaunty


thanks i worked fine in my jaunty amd64:o

---

### Post by forkandles on 2010-01-13
With 9.04 I had already installed vlc and mozilla-plugin-vlc but my internet radio still would not work.

The answer is to go to Synaptic and install “gstreamer0.10-plugins-bad”.

Alternatively go to Terminal and type:

sudo apt-get install gstreamer0.10-plugins-bad

---

### Post by gliverman on 2010-04-02
The vlc & mozilla-plugin-vlc set workes in Lucid 10.04 beta x64.  The gstreamer one did not.

---

### Post by g.oostema on 2010-05-26
using ubuntu 10.04 lucid here and tried this fix.
however i always get this error.

giliam@giliam-laptop:~$ sudo apt-get install gstreamer0.10-plugins-bad
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libiptcdata0
The following NEW packages will be installed:
  gstreamer0.10-plugins-bad libiptcdata0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 24.0kB/1,511kB of archives.
After this operation, 4,678kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err [http://ubuntu-archive.sit.kmutt.ac.th/](http://ubuntu-archive.sit.kmutt.ac.th/)  lucid/universe libiptcdata0 1.0.3-1ubuntu1
  403  Forbidden
Failed to fetch [http://ubuntu-archive.sit.kmutt.ac.t...untu1_i386.deb]("http://ubuntu-archive.sit.kmutt.ac.th/pool/universe/libi/libiptcdata/libiptcdata0_1.0.3-1ubuntu1_i386.deb")   403  Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with  --fix-missing?

i also installed the other fix, but it does not work as well


anyone knows what I can do, i really want to listen to some radio, and  most stations here use mms protocol.

tnx for the help

---

### Post by newb85 on 2010-05-27
> **g.oostema said:**
> using ubuntu 10.04 lucid here and tried this fix.
however i always get this error.

giliam@giliam-laptop:~$ sudo apt-get install gstreamer0.10-plugins-bad
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libiptcdata0
The following NEW packages will be installed:
  gstreamer0.10-plugins-bad libiptcdata0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 24.0kB/1,511kB of archives.
After this operation, 4,678kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err [http://ubuntu-archive.sit.kmutt.ac.th/](http://ubuntu-archive.sit.kmutt.ac.th/)  lucid/universe libiptcdata0 1.0.3-1ubuntu1
  403  Forbidden
Failed to fetch [http://ubuntu-archive.sit.kmutt.ac.t...untu1_i386.deb]("http://ubuntu-archive.sit.kmutt.ac.th/pool/universe/libi/libiptcdata/libiptcdata0_1.0.3-1ubuntu1_i386.deb")   403  Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with  --fix-missing?

i also installed the other fix, but it does not work as well


anyone knows what I can do, i really want to listen to some radio, and  most stations here use mms protocol.

tnx for the help

As I understand it, 403 Forbidden means the server is not granting you read access to the files you need.  I have no idea why it's doing this, but I suggest downloading from a different server.  

Under System-Administration-Software Sources, use the Download From dropdown to select the server you want.  (Clicking Other... brings up a list of all available servers.  Select one near you for better download times.  Select Best Server will run a speed test to choose the fastest.)

---

### Post by green69 on 2010-06-06
> **forkandles said:**
> With 9.04 I had already installed vlc and mozilla-plugin-vlc but my internet radio still would not work.

The answer is to go to Synaptic and install “gstreamer0.10-plugins-bad”.

Alternatively go to Terminal and type:

sudo apt-get install gstreamer0.10-plugins-bad

For me vlc, mozilla-plugin-vlc or gstreamer0.10-plugins-bad didn't work because I wasn't still able to play my internet radio.

Finally I solved the thread installing "ubuntu-restricted-extras" from synaptics. I hope this will work for you too!

Cheers

---

### Post by dr.twinny on 2011-01-14
> **green69 said:**
> For me vlc, mozilla-plugin-vlc or gstreamer0.10-plugins-bad didn't work because I wasn't still able to play my internet radio.

Finally I solved the thread installing "ubuntu-restricted-extras" from synaptics. I hope this will work for you too!

Cheers

Booyah! Thanks a ton, your solution did the trick:D

---

### Post by dr.twinny on 2011-01-14
> **green69 said:**
> For me vlc, mozilla-plugin-vlc or gstreamer0.10-plugins-bad didn't work because I wasn't still able to play my internet radio.

Finally I solved the thread installing "ubuntu-restricted-extras" from synaptics. I hope this will work for you too!

Cheers

Booyah! Thanks a ton, your solution did the trick:D

---

### Post by Trandre on 2011-01-14
I had the same issue trying to watch movies at nrk.no. I solved it by adding this repository to software center [http://www.medibuntu.org/](http://www.medibuntu.org/) and then search for mms in software center and installed as seen on print screen

NB! I use chromium as a browser

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=181079&stc=1&d=1295032664[/IMG]

---

### Post by niccozp on 2011-02-13
> **saskatchewan said:**
> Is there a link for the Microsoft Media Server (MMS) protocol source plugin?

Thanks

if you want to play a mms, just right click and press open with movieplayer:D

---

### Post by 130s on 2011-02-19
> **green69 said:**
> 
Finally I solved the thread installing "ubuntu-restricted-extras" from synaptics. I hope this will work for you too!


This package also worked for me (to watch NASA TV). Thanks!

Just for the info., I tried the following before I tried the package above, but they didn't have an effect.

- sudo apt-get install vlc mozilla-plugin-vlc (as someone suggested)
- (all from here are installed via Synaptic Package Manager) libmms0
- xmms2-plugin-mms
- mimms

Env: Ubuntu 10.04 LTS, Firefox 3.6.13

PS. Although I'm not sure the relevance with ubuntu-restricted-extras, when I reboot the OS after I installed that package, I started to see CPU reached 100% most of which was consumed by compiz. Following this link solved the issue.
[http://ubuntuforums.org/showthread.php?t=584011](http://ubuntuforums.org/showthread.php?t=584011)

---

### Post by gerrit111 on 2011-03-31
> **green69 said:**
> For me vlc, mozilla-plugin-vlc or gstreamer0.10-plugins-bad didn't work because I wasn't still able to play my internet radio.

Finally I solved the thread installing "ubuntu-restricted-extras" from synaptics. I hope this will work for you too!

Cheers

I want to kiss you!

---

### Post by madmaxo on 2011-06-11
Running:

sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad gstreamer0.10-ffmpeg


fixed it for me. But really Ubuntu's plugin finder should have done this! This is a bug!

---

### Post by newb85 on 2011-06-11
If I'm not mistaken, the plugin finder you're referring to is actually part of Mozilla Firefox.

---

### Post by bfb on 2011-08-25
Worked for me too...
I already had VLC but it didn't work for the site I wanted ([http://www.pluzz.fr/decouverte/](http://www.pluzz.fr/decouverte/)) 
Yours did though . Thanks

---

