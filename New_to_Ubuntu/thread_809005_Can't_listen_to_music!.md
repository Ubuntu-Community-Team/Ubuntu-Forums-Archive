---
title: "Can't listen to music?!"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Sec Expert on 2008-05-27
hi dear guys and gals!I am an absolute beginner to Ubuntu(but not to windows)I have just installed Ubuntu when I log in to Ubuntu it has the starting sound(with no try to install the sound card)so I think it has detected my Sound Card(it's realtek on-board) but what is dissapointing is that I can't listen to music!?](*,)what can i do?:lolflag:

---

### Post by forestpixie on 2008-05-27
Have a look at this page to sort your codecs out

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by sayakb on 2008-05-27
> **Sec Expert said:**
> hi dear guys and gals!I am an absolute beginner to Ubuntu(but not to windows)I have just installed Ubuntu when I log in to Ubuntu it has the starting sound(with no try to install the sound card)so I think it has detected my Sound Card(it's realtek on-board) but what is dissapointing is that I can't listen to music!?](*,)what can i do?:lolflag:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Sec Expert on 2008-05-27
> **LinuxIsInnovation said:**
> ```
sudo apt-get install ubuntu-restricted-extras
```

ok I'm gonna try that can you explain what the code exactly does?

---

### Post by sayakb on 2008-05-27
That installs the restricted Ubuntu modules, which includes all gstreamer codecs, flash plugins, java support and a few more things you might need. GStreamer plugins would solve your music problems.

---

### Post by billgoldberg on 2008-05-27
> **Sec Expert said:**
> ok I'm gonna try that can you explain what the code exactly does?

It installs a lot of software that can't be installed by default because of copyright issues.

It includes codecs for various video and audio codecs, the flash player, open java (you should remove open java and install java6-jre), ...

If for some reason the problem isn't with the codecs, you could try this:

[http://linuxowns.wordpress.com/2008/05/07/hardy-sound-problems-2/](http://linuxowns.wordpress.com/2008/05/07/hardy-sound-problems-2/)

for further media support, I suggest you take a look at this:

[http://linuxowns.wordpress.com/2008/02/11/media-and-ubuntu/](http://linuxowns.wordpress.com/2008/02/11/media-and-ubuntu/)

---

### Post by Sec Expert on 2008-05-27
thank you guys but unfortunately I still can't listen to mp3 or avi files(I didn't try others)when I try to run an mp3 file a window comes and tells me to search for suitable codec then I press search, there's another window that I confirm (to install gstream extra plugins) but when I confirm it, It says that there's a conflict with another software but it doesn't tell me which software it is. I'm totally confused plz help meeeeeee:(:confused::mad:

---

### Post by sayakb on 2008-05-27
Do you have Synaptic or any other package manager running in the background. If so, close it and download the codecs again. 
Btw, did you install restricted modules? That should install all gstreamer codecs. Anyway, open synaptic and install gstreamer plugins from ugly, bad, good and multiverse sets.

---

### Post by forestpixie on 2008-05-27
Open synaptic and search for gstreamer - make sure that gstreamer plugins good bad and ugly have been installed if they are not install them with synaptic. If you think you might try amarok install libxine1-ffmpeg as well.

See if that gets you further along.

---

### Post by billgoldberg on 2008-05-27
Make sure the ubuntu repo's (also third party ones) are activated in synaptic "settings -> repositories"

the in a terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

then for extra media codecs install the win32 codecs, libdvdcss and non-free-codecs or vlc from the second link in my previous post.

---

### Post by Sec Expert on 2008-05-27
> **LinuxIsInnovation said:**
> Do you have Synaptic or any other package manager running in the background. If so, close it and download the codecs again. 
Btw, did you install restricted modules? That should install all gstreamer codecs. Anyway, open synaptic and install gstreamer plugins from ugly, bad, good and multiverse sets.

when I tried to install restricted modules you told me this happended:
kh@kh-power:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for kh:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras
kh@kh-power:~$ 

and now when I try to install gstreamer plugins it says it says"mark additional required changes" but then it prompts the error message:
"could not mark all packages for installation or upgrade"
you c what a shame I am:):(

---

### Post by sayakb on 2008-05-27
Do you have all your software sources enabled. Goto System->Administration->Software sources and check all ubuntu software, 3rd paty and updates from there. Then:

```
sudo apt-get install -f
sudo apt-get update
sudo apt-get install ubuntu-restricted-modules
```

---

### Post by Sec Expert on 2008-05-27
> **billgoldberg said:**
> **Make sure the ubuntu repo's (also third party ones) are activated in synaptic "settings -> repositories"**

the in a terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

then for extra media codecs install the win32 codecs, libdvdcss and non-free-codecs or vlc from the second link in my previous post.

I went there but I don't know what exactly goes on there?!](*,)

---

### Post by sayakb on 2008-05-27
My God.. Okay.. did you enable your software sources? I'm sure you don't have your repositories (software sources) enabled. Do it first, please..

---

### Post by Sec Expert on 2008-05-27
> **LinuxIsInnovation said:**
> Do you have all your software sources enabled. Goto System->Administration->Software sources and check all ubuntu software, 3rd paty and updates from there. Then:

```
sudo apt-get install -f
sudo apt-get update
sudo apt-get install ubuntu-restricted-modules
```

I did what you told me in this post and I got this:

kh@kh-power:~$ sudo apt-get install -f
E:[B] Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/B]
kh@kh-power:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US       
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US       
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Fetched 3B in 3s (1B/s)  
E: [B]Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/B]
kh@kh-power:~$ sudo apt-get install ubuntu-restricted-modules
E: [B]Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
kh@kh-power:~$ [/B]
](*,)

---

### Post by sayakb on 2008-05-27
Seems like you have a package manager running. Do me a favor, press Ctrl+Alt+Backspace. Login again and retry these three commands. Make sure that even update manager is not running.

EDIT: Or atleast try: killall synaptic. Then try again. If it still doesn't work, then login again as indicated..

---

### Post by Sec Expert on 2008-05-27
> **LinuxIsInnovation said:**
> Seems like you have a package manager running. Do me a favor, press Ctrl+Alt+Backspace. Login again and retry these three commands. Make sure that even update manager is not running.

EDIT: Or atleast try: killall synaptic. Then try again. If it still doesn't work, then login again as indicated..

I did that, well this time I had no problem with these two commands:
sudo apt-get install -f
sudo apt-get update
but when I typed the third one I got the same result as before
kh@kh-power:~$ sudo apt-get install ubuntu-restricted-modules
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-modules
kh@kh-power:~$ 
](*,)

p.s. I think you like to kill me now;)

---

### Post by sayakb on 2008-05-27
No kill me instead :D
Try: sudo apt-get-install ubuntu-restricted-extras

Sorry for the horrible typo..

---

### Post by Sec Expert on 2008-05-27
heyyyyyyyy voila!the last command didn't work but now I can listen to music it works:popcorn:just tell me one more thing WHERE IS THE THANK BUTTON?(I can't see it I'm so clumsy!) I wanna thank you man(or woman):lolflag:

may ubuntu be with you!

---

### Post by sayakb on 2008-05-27
Man it is.. ;)
No probs.. Enjoy your music :D

---

