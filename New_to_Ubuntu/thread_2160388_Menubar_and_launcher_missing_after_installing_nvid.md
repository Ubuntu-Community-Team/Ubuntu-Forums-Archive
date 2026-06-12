---
title: "Menubar and launcher missing after installing nvidia drivers"
date: 2013-07-06
forum: New to Ubuntu
---

### Post by easyrocketscience on 2013-07-06
I installed Ubuntu 13.04 on my Lenovo Y410P today (alongside Windows 8) and everything worked fine.

I installed Steam and downloaded Team Fortress 2. The TF2 menu was laggy and the audio was stuttering. I discovered that I needed to install the nvidia drivers.

I did a sudo apt-get install nvidia-current and rebooted. After that the menubar and launcher did not show up. I proceeded to try a number of solutions to this problem that I found online, such as installing linux-headers-generic, reinstalling ubuntu-desktop, reinstalling nvidia-current, and uninstalling nvidia-current. None of these fixes have worked for me. All I can see after I log in is my desktop picture and the icons on my desktop.

Is there anything I can do short of reinstalling Ubuntu?

---

### Post by Double.J on 2013-07-06
Hi there, welcome to the forums!

just wondering how you went about uninstalling the driver?

in the mean time, you can try resetting unity. it could be after all that some changes were made to unity/compiz during the same session in which you installed the driver there's a good guide [here]("http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html")

---

### Post by easyrocketscience on 2013-07-06
I uninstalled the driver with sudo apt-get remove nvidia-current.

I think I tried resetting Unity, but there was always an error with those commands.

---

### Post by easyrocketscience on 2013-07-06
Update: I installed gnome fallback, so I can at least access my computer. I still would like to be able to use Unity.

---

### Post by stinkeye on 2013-07-07
What is your output for the terminals command...
```
/usr/lib/nux/unity_support_test -p
```
and
```
lspci -k | grep -A3 VGA
```

Eg
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **/usr/lib/nux/unity_support_test -p**
OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NVCF
OpenGL version string:  3.0 Mesa 9.1.3

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

[COLOR="#008000"]glen@Raring:~$[/COLOR] **lspci -k | grep -A3 VGA**
01:00.0 VGA compatible controller: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] (rev a1)
	Subsystem: Gigabyte Technology Co., Ltd Device 351a
	Kernel driver in use: nouveau
01:00.1 Audio device: NVIDIA Corporation GF116 High Definition Audio Controller (rev a1)
```

---

### Post by deadflowr on 2013-07-07
The two methods [here]("http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html") may or may not help you reset unity.

If it works and you want to try reinstalling the nvidia drivers, try using the additional drivers program to do so.

---

### Post by easyrocketscience on 2013-07-07
@stinkeye:

/usr/lib/nux/unity_support_test -p

```
Error: unable to open display
```

lspci -k | grep -A3 VGA

```
00:02.0 VGA Controller : Intel Corporation Haswell Integrated Graphics Controller (rev 06)
                                          Subsystem: Lenovo Device 3801
00:03.0 Audio Device: Intel Corporation HD Audio Controller (rev 6)
                                          Subsystem: Lenovo Device 3978

--

01:00.0 VGA Compatible Controller: NVIDIA Corporation GK107M [GeForce 750M] (rev a1)
                                          Subsystem: Lenovo Device 3801
                                          Kernel driver in use: nvidia
08:00.0 Ethernet Controller: Qualcomm Atheros QCA8171 Gigabit Ethernet (rev10)
```

---

### Post by stinkeye on 2013-07-07
> **easyrocketscience said:**
> @stinkeye:

/usr/lib/nux/unity_support_test -p

```
Error: unable to open display
```

lspci -k | grep -A3 VGA

```
00:02.0 VGA Controller : Intel Corporation Haswell Integrated Graphics Controller (rev 06)
                                          Subsystem: Lenovo Device 3801
00:03.0 Audio Device: Intel Corporation HD Audio Controller (rev 6)
                                          Subsystem: Lenovo Device 3978

--

01:00.0 VGA Compatible Controller: NVIDIA Corporation GK107M [GeForce 750M] (rev a1)
                                          Subsystem: Lenovo Device 3801
                                          Kernel driver in use: nvidia
08:00.0 Ethernet Controller: Qualcomm Atheros QCA8171 Gigabit Ethernet (rev10)
```
Was **/usr/lib/nux/unity_support_test -p** run from within your fallback session? Needs a graphical enviroment.

Can you open a terminal with ctrl+alt+t from your Ubuntu session and
do you have ccsm installed.

---

### Post by easyrocketscience on 2013-07-07
@stinkeye

I tried installing GNOME 3 to get a better desktop than GNOME fallback, but that somehow broke GNOME (none of the icons or menu items showed up). I installed XFCE, which works fine, and I reran /usr/lib/nux/unity_support_test_ -p:

```
Xlib: extension "GLX missing on display ":0.0"
Error: GLX is not avaliable on the system
```

And no, I don't know what ccsm is.

---

### Post by easyrocketscience on 2013-07-07
Okay, I just found CCSM. Everything in there seems to be disabled. Should I enable Unity Plugin, OpenGL, etc?

---

### Post by easyrocketscience on 2013-07-07
Bump. I enabled some things in CSSM.

---

### Post by stinkeye on 2013-07-07
> **easyrocketscience said:**
> Bump. I enabled some things in CSSM.
Ok, I don't use the nvidia driver as the nouveau driver works fine for my uses.
I had installed nvidia before on this 13.04 install just to compare with nouveau.
I can't remember if I installed through the terminal or enabled in software sources.

I just tried installing in terminal with
```
sudo apt-get install nvidia-current
```
and encountered the same problem as you.
Tried to enable plugins in ccsm but they wouldn't stick.

Tried to set compiz/unity back to defaults and reloaded compiz/unity...didn't work.
```
dconf reset -f /org/compiz/ && setsid unity
```
[COLOR="#FF0000"]_EDIT_[/COLOR]: I played around with unistalling and reinstalling nvidia drivers and found 
sometimes just a reboot seemed to reload the driver properly (still blank desktop though)  and the reset and reload commands worked to show the unity desktop.

So I purged the nvidia driver (if rebooting fails as in above edit)
```
sudo apt-get purge nvidia*
```
At this stage just check the nouveau drivers are installed...
```
apt-cache policy xserver-xorg-video-nouveau
```
> [COLOR="#008000"]glen@Raring:~$[/COLOR] **apt-cache policy xserver-xorg-video-nouveau**
xserver-xorg-video-nouveau:
  [COLOR="#FF0000"]Installed: 1:1.0.7-0ubuntu1[/COLOR]
  Candidate: 1:1.0.7-0ubuntu1
  Version table:
 *** 1:1.0.7-0ubuntu1 0
        500 [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) raring/main amd64 Packages
        100 /var/lib/dpkg/status


Rebooted into ubuntu session where nouveau drivers were loaded.
Check driver...
```
lspci -k | grep -A3 VGA
```
> [COLOR="#008000"]glen@Raring:~$[/COLOR] lspci -k | grep -A3 VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] (rev a1)
	Subsystem: Gigabyte Technology Co., Ltd Device 351a
	Kernel driver in use: [COLOR="#FF0000"]nouveau[/COLOR]

Set compiz/unity back to defaults and reloaded compiz/unity.
If you can't run this command from within the Ubuntu session just run the **dconf reset -f /org/compiz/** command
and then try logging into the ubuntu session.
```
dconf reset -f /org/compiz/ && setsid unity
```

Now I'm back to where I started with unity running using nouveau drivers.

This time tried installing nvidia drivers through software sources > Additional Drivers (see pic)
Chose nvidia-313-updates and applied changes. On completion rebooted.
All good....
> [COLOR="#008000"]glen@Raring:~$[/COLOR] **/usr/lib/nux/unity_support_test -p**
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTX 550 Ti/PCIe/SSE2
OpenGL version string:  4.3.0 [COLOR="#FF0000"]NVIDIA 313.30[/COLOR]

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

[COLOR="#008000"]glen@Raring:~$ [/COLOR]**lspci -k | grep -A3 VGA**
01:00.0 VGA compatible controller: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] (rev a1)
	Subsystem: Gigabyte Technology Co., Ltd Device 351a
	Kernel driver in use: [COLOR="#FF0000"]nvidia[/COLOR]

I don't know if you need to use a particular nvidia driver version with steam.
Nvidia is all too much of a headache for me. #-o


The other issue is when you say "I tried installing GNOME 3" What did you install? Did you add a ppa?

---

