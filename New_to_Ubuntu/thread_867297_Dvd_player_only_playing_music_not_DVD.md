---
title: "Dvd player only playing music not DVD"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by Peterfc on 2008-07-22
Hi All

I have installed Mythbuntu 8.4 and have fitted a brand new out of the box DVD player Pioneer Dvr-115dbk. While running Ubuntu 8.4 i can only run music cd's. When i run Mplayer i get "No media opened".

When using Mythbuntu. Import Dvd i get a message "No Jobs. Checking and/or wainting for DVD. I was able to import cd's music but trying to import Dvd Fails.

Going to Places/ Computer the Dvd drive is found  Cd-Rw/Dvd+_RW "Dvd +and _ but could not should how it's listed"

Thanks for reading this post.

Dell Dimension 2400 series 1gb ram 80gb hard drive split 50-50 Ubuntu amd Mythbuntu.

---

### Post by paul101 on 2008-07-22
are the codecs installed. . . ?

---

### Post by Peterfc on 2008-07-22
Hi Paul

Sorry but where would i find the codecs? I have install Mplayer, Gnome player and Helix. 

Thanks for your reply

---

### Post by frank002 on 2008-07-22
Open Synaptic and search for      libdvdcss. This might be what you are missing.

---

### Post by LowSky on 2008-07-22
you need to add the medibuntu repos
in terminal type the commands one after the other in order

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

```
sudo apt-get install libdvdcss2
```
for a 32 bit install
```
sudo apt-get install w32codecs
```
or if 64 bit is installed dont install unless  your running 64 bit!!!
```
sudo apt-get install w64codecs
```

---

### Post by ramjet_1953 on 2008-07-22
Do it the easy way, if you are not comfortable with the command line.

Navigate to [COLOR="Blue"]Applications>Add/Remove[/COLOR]

When the window opens, make sure that you change the dropdown menu Show, to [COLOR="Blue"]All Available Applications[/COLOR].

Next click on the [COLOR="Blue"]Other[/COLOR] item in the left pane.

Scroll down to the [COLOR="Blue"]Ubuntu Restricted Extra[/COLOR]s item and choose it.

Click on the [COLOR="Blue"]Apply Changes[/COLOR] button in the bottom right-hand corner.

Depending upon your Internet speed, this may take some time as it will also load-up quite a few extras, such as flash, Java, Microsoft fonts, as well as audio and video codecs.

There are two more packages that you also need.

         [B] libdvdnav4
          libdvdread3[/B]

You can use Synaptic package manager to install them.

Unfortunately, to enable libdvdcss2, there is one command line thing that you will need to do.

Copy and paste this command into a terminal window:

[COLOR="Red"]sudo /usr/share/doc/libdvdread3/install-css.sh[/COLOR]

If you do all of this, your system will play virtually and audio, or video file.

Regards,
Roger :cool:

---

### Post by styfle on 2008-07-23
Thanks a lot ramjet_1953. The only problem I had was some corruption when downloading/installing the restricted stuff. I think it had to do with java.

Also when I ran that command, I got this:
> `/tmp/dvdcss-OS5629/libdvdcss.deb'
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.30.198
Connecting to [www.dtek.chalmers.se|129.16.30.198|:80](www.dtek.chalmers.se|129.16.30.198|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 25,178 (25K) [text/plain]

100%[====================================>] 25,178         5.67K/s    ETA 00:00

10:01:11 (776.97 B/s) - `/tmp/dvdcss-OS5629/libdvdcss.deb' saved [25178/25178]

Selecting previously deselected package libdvdcss2.
(Reading database ... 104829 files and directories currently installed.)
Unpacking libdvdcss2 (from .../dvdcss-OS5629/libdvdcss.deb) ...
Setting up libdvdcss2 (1.2.5-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

It sounds good but I wanna double check to see if that is right.
And I still can't play DVDs :(

PS I am a complete noob to linux

---

### Post by LowSky on 2008-07-23
dont forget to reboot ubuntu

---

### Post by Jon Monreal on 2008-07-23
> **styfle said:**
> Thanks a lot ramjet_1953. The only problem I had was some corruption when downloading/installing the restricted stuff. I think it had to do with java.

Also when I ran that command, I got this:

It sounds good but I wanna double check to see if that is right.
And I still can't play DVDs :(

PS I am a complete noob to linux

That should have installed the codecs. Did you try rebooting as LowSky Suggested? Otherwise, what happens when you insert (or, for that matter, try to play) a DVD? Do you get an error? Or does Ubuntu not recognize (mount) the DVD at all?

---

### Post by styfle on 2008-07-23
Ok I downloaded Movie Player Xine and that seems to work great. DVD menus, the fast forward works, and it just works.
The audio seemed to be a bit off after about 30 minutes but then I paused it and it seemed to correct itself.

---

### Post by Jon Monreal on 2008-07-24
> **styfle said:**
> Ok I downloaded Movie Player Xine and that seems to work great. DVD menus, the fast forward works, and it just works.
The audio seemed to be a bit off after about 30 minutes but then I paused it and it seemed to correct itself.

Sounds like everything is good then. Are you interested in seeing if any of the other players will work?

---

### Post by alohadiaz on 2008-10-29
Hey All. 

I jst added on the codecs but now my screen flickers while watching movie and the movie player takes priority over any open web page now allowing me tp see the portion of the web page the movie player is located behind, I was having the same problem when I was using Ubuntu UE 1.9. Just went back to 8.4 and having the same issue. I think it has to do with my ATI drivers not sure.

---

