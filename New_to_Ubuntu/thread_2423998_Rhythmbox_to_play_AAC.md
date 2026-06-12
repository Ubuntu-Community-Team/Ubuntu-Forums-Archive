---
title: "Rhythmbox to play AAC"
date: 2019-08-01
forum: New to Ubuntu
---

### Post by dynvec on 2019-08-01
I've made a search on how to get Rhythmbox to play AAC; from what I gathered, gstreamer bad plugins need to be installed. I've tried to do so in vain. Whether I was on the right path or not, please help me to have Rhythmbox play AAC. I'm especially interested in streaming AAC radio.

Thank you kindly for your help

---

### Post by Dennis N on 2019-08-01
Install **libgstreamer-plugins-bad1.0-0**
That should do it.

---

### Post by dynvec on 2019-08-01
Please note I have little knowledge of GNU/Linux. The following is what I managed to get and don't know how to get better:
> ubuntu@ubuntu:~$ sudo apt-get install libgstreamer-plugins-bad1.0-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libgstreamer-plugins-bad1.0-0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libgstreamer-plugins-good1.0-0 libgstreamer-gl1.0-0

E: Package 'libgstreamer-plugins-bad1.0-0' has no installation candidate
ubuntu@ubuntu:~$ 

---

### Post by Dennis N on 2019-08-01
What version of Ubuntu are you using? The answer I gave is based on what's available in Ubuntu 18.04. (Package name is in red in the list below.)

```
dmn@Sydney:~$ dpkg --list libgstreamer*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                      Version                   Architecture              Description
+++-=========================================-====================
ii  libgstreamer-gl1.0-0:amd64                1.14.4-1ubuntu1.1~ubuntu1 amd64                     GStreamer GL libraries
ii  [COLOR="#FF0000"]libgstreamer-plugins-bad1.0-0[/COLOR]:amd64       1.14.4-1ubuntu1~ubuntu18. amd64                     GStreamer libraries from the "bad" set
ii  libgstreamer-plugins-base1.0-0:amd64      1.14.4-1ubuntu1.1~ubuntu1 amd64                     GStreamer libraries from the "base" set
ii  libgstreamer-plugins-good1.0-0:amd64      1.14.4-1ubuntu1~ubuntu18. amd64                     GStreamer development files for libraries from the "good" set
ii  libgstreamer1.0-0:amd64                   1.14.4-1~ubuntu18.04.1    amd64                     Core GStreamer libraries and elements

```

---

### Post by dynvec on 2019-08-01
Is this ok?
> ubuntu@ubuntu:~$ cat /etc/os-release
NAME="Ubuntu"
VERSION="18.04 LTS (Bionic Beaver)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 18.04 LTS"
VERSION_ID="18.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=bionic
UBUNTU_CODENAME=bionic

---

### Post by Dennis N on 2019-08-01
You have the same version I do. I then tried the same install command here to check it. 

```
dmn@Sydney:~$ sudo apt-get install libgstreamer-plugins-bad1.0-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgstreamer-plugins-bad1.0-0 is already the newest version (1.14.4-1ubuntu1~ubuntu18.04.1).

```
I already have the latest version, so no install was done. But it also shows the package does exist. Also don't see anything wrong with your command, but you could copy and paste my command from above into your terminal and try again. Or to avoid all typing, use Synaptic Package manager instead. 

If that fails,
Try changing the server you are using for packages, and try again.
Software&Updates > Ubuntu Software > Download from:
Select another server.

Comment: Firefox will stream AAC. Can you use Firefox instead of Rhythmbox?

---

### Post by yetimon_64 on 2019-08-01
> **Dennis N said:**
> You have the same version I do. I then tried the same install command here to check it....

Note the OP's user/host names ...
> ubuntu@ubuntu 
If the OP is operating off a live image boot the universe and multiverse repositories may need adding. Would also explain why the package is missing for the OP when you have the same release 18.04.

@ OP, are you trying to install that package to a live boot environment?

---

### Post by Dennis N on 2019-08-01
> OP is operating off a live image boot...
Good observation - I didn't notice that.

---

### Post by dynvec on 2019-08-01
> **yetimon_64 said:**
> @ OP, are you trying to install that package to a live boot environment?
I don't have storage capacity other than copying things from the temporary folders provided to me after booting from a live boot (mostly to other USB sticks).
If there's a way for things to stick around from boot to boot (other than doing a full install), that would be neat, but is only optional.

---

### Post by Dennis N on 2019-08-01
Again, if you just want to listen, Firefox will stream AAC radio. Even in the live media, I would think.

---

### Post by dynvec on 2019-08-01
It doesn't seem so for me, or for that station. Looking at
[IMG]https://i.ibb.co/87mmYz0/Screenshot-from-2019-08-01-16-42-05.png[/IMG]should convey the browser doesn't handle the file itself, as it would should I put an image URL in there. The MP3 output of [SomaFM: Beat Blender: A late night blend of deep-house and downtempo chill. Commercial-free, Listener-supported Radio]("http://somafm.com/beatblender/") has a web player but the main reason I'm interested to that site is that they offer good sounding low bitrate music.

---

### Post by Dennis N on 2019-08-01
On your site, you would just click on "Tune In" and you get the site's pop-up "Soma FM player" in Firefox (screenshot). You don't have to download anything. 

I also tried the .pls file method, but I instead used Audacious to open it since it has default AAC support in Ubuntu (and I don't like Rhythmbox). It immediately started the stream. It sounds better. An advantage is you can keep the playlist file and reuse it unless it expires.

---

### Post by dynvec on 2019-08-02
I tried my best to explain in my previous post that the web player is in the MP3 section, the MP3 format has a lesser quality-size ratio and I don't have unlimited internet[SIZE=1]; and even if I had unlimited I would probably get throttled past a certain amount, so by cutting download amount where it doesn't affect quality, I'd reduce throttling[/SIZE]. Please look at the thread name/title/label, the only audio format mentioned is AAC and it's the--ONLY--format I'm interested in.
About Audacious, I instinctively put it in Ubuntu Software and only Audacity showed and I was convinced its not for listening for audio streams so I did a little search stumbling on [How to Install Audacious Audio Player on Ubuntu]("http://vitux.com/how-to-install-audacious-audio-player-on-ubuntu/") which showed to do what I did but their result
[IMG]http://vitux.com/wp-content/uploads/2019/04/word-image-1.png[/IMG]
had it. What's up with my system that it doesn't show up? Or is the article deprecated and Audacious doesn't show there any-more? Also I'm hoping whichever audio client I end up using won't require > 30 Mb d/l.

---

### Post by Dennis N on 2019-08-02
Yes, I used the .pls file that was AAC 128k. As I said, that sounded better than the "Tune In" option. If you can't get Rhythmbox to work, use Audacious for streaming the .pls file. You can install Audacious in Ubuntu's live media if you are not installing to your hard disk, and nothing extra to download. It plays AAC by default.

---

### Post by Dennis N on 2019-08-02
Audacious playing AAC audio stream - nice.
You've got it in your screenshot.

---

### Post by dynvec on 2019-08-02
> **Dennis N said:**
> Audacious playing AAC audio stream - nice.
You've got it in your screenshot.
It does not show up, it was mentioned in my last post,
> **dynvec said:**
> About Audacious, I instinctively put it in Ubuntu  Software and only Audacity showed [...] What's up with my system that  it doesn't show up?
the screenshot is theirs.
> **Dennis N said:**
> You can install Audacious in Ubuntu's live media 
If I put "live media" in in Ubuntu Software and only the following is listed

[LIST=1]
[*]Ktube Media Downloader 
[*]Plex Media Server 
[*]OBS Studio 
[*]dataclerk 
[/LIST]
 
** How can I install Audacious?**

---

### Post by #&amp;thj^% on 2019-08-02
```
sudo apt install audacious
```

---

### Post by dynvec on 2019-08-02
That doesn't work for me:
> ubuntu@ubuntu:~$ sudo apt install audacious
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package audacious

---

### Post by #&amp;thj^% on 2019-08-02
Serves me right for not reading the entire thread. ;)
> I don't have storage capacity other than copying things from the temporary folders provided to me after booting from a live boot (mostly to other USB sticks).
If there's a way for things to stick around from boot to boot (other than doing a full install), that would be neat, but is only optional. 
This is just not a proper way way to experience this OS.
When your able to install it to a real persistent machine, you will find things a more pleasurable ride.
For now try:
```
sudo apt update && sudo apt install audacious
```

---

### Post by dynvec on 2019-08-02
The system doesn't have proper storage; I'll install the OS when I get some. For now it still doesn't work:
> ubuntu@ubuntu:~$ sudo apt update && sudo apt install audacious
Ign:1 cdrom://Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426) bionic InRelease
Hit:2 cdrom://Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426) bionic Release
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [88.7 kB] 
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic InRelease [242 kB]            
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 Packages [464 kB]
Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]        
Get:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic/main amd64 DEP-11 Metadata [477 kB]           
Get:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main Translation-en [160 kB]               
Get:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 DEP-11 Metadata [22.7 kB] 
Get:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main DEP-11 48x48 Icons [10.4 kB]        
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main DEP-11 64x64 Icons [31.7 kB]   
Get:13 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic/main DEP-11 48x48 Icons [118 kB]           
Get:14 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/restricted amd64 Packages [4,296 B]              
Get:15 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/restricted Translation-en [2,192 B]          
Get:16 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic/main DEP-11 64x64 Icons [245 kB]                             
Get:17 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/main amd64 Packages [697 kB]
Get:18 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/main Translation-en [255 kB]
Get:19 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/main amd64 DEP-11 Metadata [282 kB]
Get:20 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/main DEP-11 48x48 Icons [66.7 kB]
Get:21 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/main DEP-11 64x64 Icons [134 kB]
Get:22 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/restricted amd64 Packages [6,996 B]
Get:23 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates/restricted Translation-en [3,076 B]
Fetched 3,399 kB in 2s (1,781 kB/s)                                       
Reading package lists... Done
Building dependency tree       
Reading state information... Done
757 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package audacious

---

### Post by #&amp;thj^% on 2019-08-02
Keep in mind my previous advice.
You see this:
```
757 packages can be upgraded
```
This is more or less a teaching moment now.
run:
```
sudo apt upgrade
```
after all is finished, next run:
```
sudo apt install audacious
```
But after a reboot all will be lost. (This is where I say not a proper way to enjoy this OS)
If you feel up to it see: [https://ubuntuforums.org/showthread.php?t=2213631](https://ubuntuforums.org/showthread.php?t=2213631)

---

### Post by dynvec on 2019-08-02
Thanks for that link, I plan to do it.

---

### Post by mc4man on 2019-08-02
Open up Software & Updates > enable the  universe and maybe the multiverse repos  > refresh sources 
You can then install audacious and if desired any of the gstreamer plugins for rythmbox.

---

### Post by Dennis N on 2019-08-02
Are you working with the 18.04 live media? 18.04 live media has these sources enabled:

```
xubuntu@xubuntu:~$ cat /etc/apt/sources.list | grep deb | grep -v src
deb cdrom:[Xubuntu 18.04.2 LTS _Bionic Beaver_ - Release amd64 (20190210)]/ bionic main multiverse restricted universe
deb http://archive.ubuntu.com/ubuntu/ bionic main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ bionic-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ bionic-updates main restricted universe multiverse

```
Audacious and its plugins are in universe - enabled in live media by default, so it should install. If OP is still attending to all this, check if you have the defaults above (cdrom line will be different since I used xubuntu live media). I suspect something amiss with your sources.list

Going to test the whole streaming thing with live media in VM, just to satisfy myself it will all work.

---

### Post by mc4man on 2019-08-03
> **Dennis N said:**
> Are you working with the 18.04 live media? 18.04 live media has these sources enabled:

```
xubuntu@xubuntu:~$ cat /etc/apt/sources.list | grep deb | grep -v src
deb cdrom:[Xubuntu 18.04.2 LTS _Bionic Beaver_ - Release amd64 (20190210)]/ bionic main multiverse restricted universe
deb http://archive.ubuntu.com/ubuntu/ bionic main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ bionic-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ bionic-updates main restricted universe multiverse

```
Audacious and its plugins are in universe - enabled in live media by default, so it should install. If OP is still attending to all this, check if you have the defaults above (cdrom line will be different since I used xubuntu live media). I suspect something amiss with your sources.list

Going to test the whole streaming thing with live media in VM, just to satisfy myself it will all work.
In _Ubuntu_ 18.04.x universe is not enabled by default , screen
Why they choose this is unknown to me, seems nonsensical.

---

