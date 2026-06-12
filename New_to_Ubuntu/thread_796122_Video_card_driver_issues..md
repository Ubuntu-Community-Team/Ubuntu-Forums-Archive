---
title: "Video card driver issues."
date: 2008-05-16
forum: New to Ubuntu
---

### Post by tactx on 2008-05-16
Before I get into my problem, I'd like to say thanks to those who spend any time even contemplating helping me here. After contemplating the ramifications of open source technology and deciding that it is something I would like to pursue and maybe, someday, contribute to, I decide to try to transition from Windows to Ubuntu. Thought its probably needless to say that while I am still committed to learning/using Linux, I am somewhat overwhelmed. Though I've found a few links that seem to at least partially address my problems, I don't know enough to be able to follow the recommendations, and I am unsure if what I am trying to achieve is currently posssible.

The Problem: I have two graphics cards running three monitors horizontally arranged . Specifically, I am running two NVIDIA GeForce 8800 GTS 512k cards...(not in SLI Mode). Each has two DVI outputs. They are driving three 20" Widescreen LCD monitors. Currently, cloned video appears on the first two monitors and there is no video on the third monitor. I would like to be able to use the center monitor as my main window and extend the desktop to the side monitors.

What I have done: I installed the NVIDIA 3D Accelerated Restricted Driver and this caused my video to be isolated to the first monitor (far left)
Unable to make the proper adjustments. I added the "Screen and Graphics"
application under "other" on the applications menu. It shows two listings for "screen 1" one marked default, and the other as disabled.Changing the status of one disables the other. On the Graphics Card tab it shows my two NVIDIA Graphics Card where I selected the appropriate 8000 series driver on both of them. The Video Memory setting appears to be set at automatic, but is greyed out. Trying to undo what I had done pending further research, I unchecked the "enabled box on the NVIDIA Restricted driver. It appeared to be uninstalling but threw an Error#2 ???

I rebooted the computer and the configuration reverted to showing the cloned window on the first two monitors. Ive seen a couple of posts concerning "twinview" but was unsure if they would address my needs and too confused to be confident about trying to "edit" x conf without more detailed help. I went to the the Nvidia website and searched for the appropriate driver and think I found it but then linked to [http://www.nvnews.net/vbulletin/showthread.php?t=72490]("http://www.nvnews.net/vbulletin/showthread.php?t=72490")...and knew I was in too deep to figure things out without help.

Any usefull guidance will be appreciated.

---

### Post by balagosa on 2008-05-16
hmmm...i read your post and would liek to help.

but i just dont know anything related to Nvidia, since my graphics card is Intel built-in.

i am sure many here can help you though.

---

### Post by hermes0710 on 2008-05-16
You may run "gksudo nvidia-settings" and there is an interface there for configuring your screens. Other than that, if old driver is the issue here, you may use envyng (sudo apt-get install envyng-gtk) in order to obtain the latest nvidia driver

---

### Post by tactx on 2008-05-16
Wow that was fast...LOL:D No problem, thanks for reading..Im itching to try and folow the instruction in the link to load the NVIDA driver, but im unsure about the edits...and i dont know how ito the get the aps it says you need to have installed previously...:o...or if it will fix my problem..

---

### Post by tactx on 2008-05-16
I ran the "gksudo nvidia-settings" command in the terminal at the "~$" prompt ...it asked for my password then returned to the prompt....Now,what?

---

### Post by hermes0710 on 2008-05-16
Didn't you have any application appeared? Or any error?

---

### Post by tactx on 2008-05-16
Not that I can see/discern...

---

### Post by tactx on 2008-05-16
I should probably mention that I re-enabled the NVIDIA restricted driver first...

---

### Post by shifty_powers on 2008-05-16
try system>administration>nvidia x server settings

---

### Post by tactx on 2008-05-16
system>administration>nvidia x server settings 

I do not have an "nvidia x server settings" selection...

---

### Post by hermes0710 on 2008-05-16
"sudo apt-get install nvidia-settings"

---

### Post by shifty_powers on 2008-05-16
heh ok

```
sudo apt-get install nvidia-settings
```

that will either install it for you or tell you that it is installed.

if it installs it for you, then look where i said. if not then get back to us ;)

---

### Post by tactx on 2008-05-16
OK, I ran the sudo apt-get install envyng-gtk
to install the envyng app
ran the app ...uninstalled the nvidia driver ...rebooted, ran it again to install the "latest" driver and was showing the NVIDIA driver as enabled.
Then when I ran the gksudo nvidia-settings command..said app appeared.
I set each monitor to run as a seperate x-window saved the config file rebooted....and now have video on all three monitors! It appears to be three desktops....however...I am unable to move my mouse to the third destop and cannot use it.

Also...how can I add the gksudo nvidia-settings command to a menu selection so I can launch the app without needing to type it into a terminal window each time?

PS...Thank you so much! :D ~Almost there...

---

### Post by shifty_powers on 2008-05-16
is it not in the system>admin menu?

as for third desktop, not sure on that one.

as to adding nvidia settings to your menu, just right click on applications and click on edit menu, shoudl be farily easy from there. the comman for the launcher will be gksudo nvidia-settings again ;)

---

### Post by hermes0710 on 2008-05-16
For the menu question: System>Preferences>Main Menu and locate the entry for the nvidia-settings app. Append gksudo in the begining and that's all (I think, try it out)

---

### Post by tactx on 2008-05-16
Um...Duh...there it is...LOL...Sorry :D

Im gonna keep playing with the settings ...if I cant get the mouse to work on the third desktop...should I open another thread to address that?

/ty :D

---

### Post by shifty_powers on 2008-05-16
heh we all have moments like that.

glad to help ;)

---

### Post by hermes0710 on 2008-05-16
I think that nvidia-settings from the  menu does not run with root priveleges and so you must have to edit the entry manually (appending the gksudo)

---

### Post by tactx on 2008-05-16
Thank you all so much!!!! This has been fixed!
I appended the gksudo command in the launcher properties for nvidia-settings and played with the settings. I have set with the first two monitors set to 1680 x 1050, and the third set to auto. Each configured as a seperate x-window, with Xinerama enabled. it took a couple of reboots to apply all the changes,...
... but I now have three monitors acting as a single seamless desktop. Special Thanks to _hermes0710_ & shifty_powers

I would like to find out more about the EnvyNG script that I ran, any links to the source code and descriptions would be appreciated.

---

### Post by hermes0710 on 2008-05-16
Glad i helped :)

Info: [https://wiki.ubuntu.com/EnvyNG]("https://wiki.ubuntu.com/EnvyNG")
Developer's Website: [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

---

