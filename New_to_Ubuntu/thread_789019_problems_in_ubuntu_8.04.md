---
title: "problems in ubuntu 8.04"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by quarkhirad on 2008-05-10
Hi guys i have installed the new hardy. Its brilliant i just have a couple of problems. I have a hP pavillion dv 6767

1) I tried to play a .dat movie using  totem movie player. It said it would need to download some plugins. I allowed it to download all the plugins and it said plugins installed successfully. But when i try playing a file it says ( even after installing all the plugins it asked for) 

       An error occurred 
        
            failed to connect stream: invalid argument

But if i play the file using vlc it plays it. 

I also cannot play mp3 music files.It gives me the same error.


2) I have a 1.3M pixel inbuilt webcam. How can i use it in ubuntu.

3) I have a Dual layer DVD writer with light scribe. What software do i use to be able to use the light scribe feature in ubuntu.

4) I have installed Gsynaptics to be able to configure my synaptics touch pad. However whenever i type gsynaptics in the terminal it says

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

---

### Post by DieB on 2008-05-10
to 1:

install ubuntu-restricted-extras (solves most of the codecs) for more check:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

to 2:

install cheese

to 4:

sudo gedit /etc/X11/xorg.conf

search for that option mentioned and edit it

---

### Post by jose158 on 2008-05-10
> **quarkhirad said:**
> Hi guys i have installed the new hardy. Its brilliant i just have a couple of problems. I have a hP pavillion dv 6767

1) I tried to play a .dat movie using  totem movie player. It said it would need to download some plugins. I allowed it to download all the plugins and it said plugins installed successfully. But when i try playing a file it says ( even after installing all the plugins it asked for) 

       An error occurred 
        
            failed to connect stream: invalid argument

But if i play the file using vlc it plays it. 

I also cannot play mp3 music files.It gives me the same error.


2) I have a 1.3M pixel inbuilt webcam. How can i use it in ubuntu.

3) I have a Dual layer DVD writer with light scribe. What software do i use to be able to use the light scribe feature in ubuntu.

4) I have installed Gsynaptics to be able to configure my synaptics touch pad. However whenever i type gsynaptics in the terminal it says

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics
I got the same error "failed to connnect to stream: invalid argument". for some reason if you remove and reinstall totem it *sometimes* works fine...

---

### Post by quarkhirad on 2008-05-26
Hey hi sorry for such a late reply. I was busy i installed cheese and it works thanks a lot. However my mplayer problem still persists even after installing ubuntu restricted extras and re installing totem.

---

### Post by ichiakahoshi on 2008-05-28
i know its slightly off subject, but could some one who knows how to use cheese please message me with some simple instructions as to how to use it (or even find it) in VERY new to linux but am learning fast. thanks

---

### Post by stchman on 2008-05-28
> **quarkhirad said:**
> Hi guys i have installed the new hardy. Its brilliant i just have a couple of problems. I have a hP pavillion dv 6767

1) I tried to play a .dat movie using  totem movie player. It said it would need to download some plugins. I allowed it to download all the plugins and it said plugins installed successfully. But when i try playing a file it says ( even after installing all the plugins it asked for) 

       An error occurred 
        
            failed to connect stream: invalid argument

But if i play the file using vlc it plays it. 

I also cannot play mp3 music files.It gives me the same error.


2) I have a 1.3M pixel inbuilt webcam. How can i use it in ubuntu.

3) I have a Dual layer DVD writer with light scribe. What software do i use to be able to use the light scribe feature in ubuntu.

4) I have installed Gsynaptics to be able to configure my synaptics touch pad. However whenever i type gsynaptics in the terminal it says

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

1. Install CODECs.

```

sudo apt-get -y install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```

2.  Cheese

3.  I use K3b for CD/DVD burning duties.  As far as Lightscribe you will have to Google that.

4.  The Synaptics touchpad works OOB with Ubuntu.

---

### Post by rajaram_s on 2008-05-28
Am facing a same such problem with my synaptic software.... what do I do?

---

### Post by liamr_spencer on 2008-06-01
hi guys,

I was having the same problem as the dude above (webcam in skype not working) so i installed cheese and the webcam began to work. People can see me in skype however my mic is not working which is supposed to be intergrated with the cam.

I have a hp pavillion dv2130 laptop with a 1.3mp cam.

any help would be appreciated!

---

