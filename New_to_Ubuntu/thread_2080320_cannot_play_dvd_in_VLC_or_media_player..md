---
title: "cannot play dvd in VLC or media player."
date: 2012-11-03
forum: New to Ubuntu
---

### Post by Jackalyn on 2012-11-03
_Just for clarification._ The DVD is Upstairs Downstairs, (BBC the one you buy for 5.99 fromn Debenhams.

I have Ubuntu 12.4 on Acer 6930g

I have been to Ubuntu but have no idea what packages to download but have done all the other stuff you are meant to do according to the youtube video I watched, IE

I have done: 
```
sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```and
sudo```
 apt-get install app-install-data-
medibuntu apport-hooks-medibuntu

```and ```
apt get update
```However now I am stuck as the message I get is '  p, li { white-space: pre-wrap; }  [COLOR=#ff0000]Playback failure:[/COLOR]
 [COLOR=#000000]DVDRead could not open the disc "/dev/dvd".[/COLOR]
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/dvd'. Check the log for details.' on VLC and media player tells me  a dvd decryption library is not installed-but when I looked at the info on here it looked like it was illegal to install it?[/COLOR]

I have restricted extras and that did not solve anything.

I went online to search for what would open it and dowloaded all sorts.

Just tried this:  

#jacky@jacky-Aspire-6930G:~$ sudo apt-get install libdvdread4
[sudo] password for jacky: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 96 not upgraded.
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
jacky@jacky-Aspire-6930G:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
jacky@jacky-Aspire-6930G:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
--2012-11-03 21:09:11--  [http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages)
Resolving packages.medibuntu.org (packages.medibuntu.org)... 88.191.127.22
Connecting to packages.medibuntu.org (packages.medibuntu.org)|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7942 (7.8K) [application/octet-stream]
Saving to: `/tmp/dvdcss-uSHXrP/Packages'

100%[======================================>] 7,942       31.1K/s   in 0.2s    

2012-11-03 21:09:14 (31.1 KB/s) - `/tmp/dvdcss-uSHXrP/Packages' saved [7942/7942]

--2012-11-03 21:09:14--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.12-0.0medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.12-0.0medibuntu1_i386.deb)
Resolving packages.medibuntu.org (packages.medibuntu.org)... 88.191.127.22
Connecting to packages.medibuntu.org (packages.medibuntu.org)|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 39684 (39K) [application/octet-stream]
Saving to: `/tmp/dvdcss-uSHXrP/libdvdcss.deb'

100%[======================================>] 39,684      40.0K/s   in 1.0s    

2012-11-03 21:09:16 (40.0 KB/s) - `/tmp/dvdcss-uSHXrP/libdvdcss.deb' saved [39684/39684]

Selecting previously unselected package libdvdcss2.
(Reading database ... 323355 files and directories currently installed.)
Unpacking libdvdcss2 (from .../dvdcss-uSHXrP/libdvdcss.deb) ...
Setting up libdvdcss2 (1.2.12-0.0medibuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
jacky@jacky-Aspire-6930G:~$ ^C
jacky@jacky-Aspire-6930G:~$ #

OOOO OPENED IN WINDOWS BUT NOT VLC AND EVERTHING IS TINGED WITH GREEN? It works but fairly interesting with the green faces. Soo how do I change that and which bit of what I did solved the problem?


[COLOR=#000000]Thanks J
[/COLOR]

---

### Post by nothingspecial on 2012-11-03
Hi, see this 

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

basically, you need to do

```

sudo apt-get install libdvdread4
```

then

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

You may need to restart.

---

### Post by cwsnyder on 2012-11-03
Most of the packages are installed if you install the package **ubuntu-restricted-extras**, I believe from the 'Universe' repositories.

---

### Post by monkeybrain2012 on 2012-11-03
> **cwsnyder said:**
> Most of the packages are installed if you install the package **ubuntu-restricted-extras**, I believe from the 'Universe' repositories.


You need libdvdcss2 for watching dvds and it is not in ubuntu-restricted-extras. You need to install it from medibuntu.

Instructions to add the medibuntu repository

[http://www.unixmen.com/medibuntu-repositories-available-for-ubuntu-12-04-lts-precise-pangolin-ppa/](http://www.unixmen.com/medibuntu-repositories-available-for-ubuntu-12-04-lts-precise-pangolin-ppa/)

---

### Post by qamelian on 2012-11-03
> **monkeybrain2012 said:**
> You need libdvdcss2 for watching dvds and it is not in ubuntu-restricted-extras. You need to install it from medibuntu.

Instructions to add the medibuntu repository

[http://www.unixmen.com/medibuntu-repositories-available-for-ubuntu-12-04-lts-precise-pangolin-ppa/](http://www.unixmen.com/medibuntu-repositories-available-for-ubuntu-12-04-lts-precise-pangolin-ppa/)
But you don't need to actually add medibuntu to get the DVD working. The instructions provided above by nothingspecial are sufficient. The second command that was provided retrieves libdvdcss2 from medibuntu without needing to add the medibuntu repos.

---

### Post by AllenGG on 2012-11-05
Thanks Gamelian, and thanks to ¨nothing Special´ Worked quickly .

---

### Post by Jackalyn on 2012-11-05
> **nothingspecial said:**
> Hi, see this 

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

basically, you need to do

```

sudo apt-get install libdvdread4
```then

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```You may need to restart.


This is what made it work. I think - I did go to all the instructions on  Ubuntu but somewhere read it was illegal to download this? I then found other discussions that said it was not. My confusion was that I assumed restricted extras would take care of the problem as I had also read that but I don't think it did or the files did not download correctly. Thanks all. J

---

### Post by Linux_junkie on 2012-11-05
Glad to read that your problem has been resolved. In answer to your question regarding legality of DVD playback, in some countries US being one of them, they have software patents which restrict the use of software and as a result of this most Linux distributions do not include the DVD playback software as standard. 

If you live in such a country that prevents you using software like this without payment it is the end users responsibility to download and install not the Linux distributors.

If you live in the UK or Europe you don't need to worry about software patents because they don't apply here.

Now that it is resolved, can you mark the thread "SOLVED" by selecting it from the 'thread tools' drop down menu.

---

