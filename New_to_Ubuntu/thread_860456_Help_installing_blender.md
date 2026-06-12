---
title: "Help installing blender"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by baistaef on 2008-07-15
I tried to install Blender via synaptic it was an older version ( as all the software there ) so i downloaded it from the official site of blender and untar it but i am not being able to run it, it is executable and and i have read and wright permissions hot can i run it?
Am i gonna have a problem every time i need to install software like this? And when they update the repositories anyway???

---

### Post by rixtr66 on 2008-07-15
you can get blender 2,46 in a debian package from get deb,all you need is gdebi package installer.
rick

---

### Post by Kingsley on 2008-07-15
I found some debs here.
[http://ppa.launchpad.net/wgrant/ubuntu/pool/main/b/blender/](http://ppa.launchpad.net/wgrant/ubuntu/pool/main/b/blender/)

---

### Post by baistaef on 2008-07-15
Okay thanks guys for your help but now it is not just for blender, i don't care if i can install it from other place i want to know why the file i downloaded from the official site don't work
Anyone?

---

### Post by bumanie on 2008-07-15
You probably have not got the "C" compiler installed. > sudo apt-get install build-essential

---

### Post by baistaef on 2008-07-15
> **bumanie said:**
> You probably have not got the "C" compiler installed.

It is compiled and should be ready to work i didn't downloaded source code.

---

### Post by RomeReactor on 2008-07-15
> **baistaef said:**
> Okay thanks guys for your help but now it is not just for blender, i don't care if i can install it from other place i want to know why the file i downloaded from the official site don't work
Anyone?

Hi. Are you getting any errors? Is there a 'readme' or 'install' file? Open a terminal (Applications->Accessories->Terminal) and assuming you have the folder in the desktop, try to run it like this:
```
~Desktop/FOLDER_NAME/blender
```

EDIT: Please post the contents of the folder.

---

### Post by cotcot on 2008-07-15
Any error messages when you type 'blender' in terminal ?

---

### Post by gandaran on 2008-07-15
> **baistaef said:**
> It is compiled and should be ready to work i didn't downloaded source code.
 
can you specify what type of file it is then!

---

### Post by baistaef on 2008-07-15
> **RomeReactor said:**
> Hi. Are you getting any errors? Is there a 'readme' or 'install' file? Open a terminal (Applications->Accessories->Terminal) and assuming you have the folder in the desktop, try to run it like this:
```
~Desktop/FOLDER_NAME/blender
```

No there is no such thing there is folder and documentation for the program itself and the program ( which is executable by default by the way ).

Here is what i got from the terminal: "No such file or directory".

---

### Post by cariboo on 2008-07-15
If you install software that isn't in the repositories you will have to update it manually every time an update comes out. That is why it is recommended that you install software using Add/Remove Programs or Synaptic Package Manager. To install the program you downloaded it would be best to install it from a terminal. The best way to do this is to untar the program in  a directory in your home directory other than the desktop then navigate to that directory and install it from there. The reasoning behind this is, that if you ever want to uninstall the program you've still got the uninstall scripts in the directory that you untared the program in.

Jim

---

### Post by baistaef on 2008-07-15
> **gandaran said:**
> can you specify what type of file it is then!

That is the problem my friend there is no thing that tells me this file is .bin or .sh or .run or even .avi!!!!!!!!!!!!!!!!!

---

### Post by RomeReactor on 2008-07-15
An easier way is to just drag and drop the executable into the terminal.

---

### Post by baistaef on 2008-07-15
> **cariboo907 said:**
> If you install software that isn't in the repositories you will have to update it manually every time an update comes out. That is why it is recommended that you install software using Add/Remove Programs or Synaptic Package Manager. To install the program you downloaded it would be best to install it from a terminal. The best way to do this is to untar the program in  a directory in your home directory other than the desktop then navigate to that directory and install it from there. The reasoning behind this is, that if you ever want to uninstall the program you've still got the uninstall scripts in the directory that you untared the program in.

Jim

My friend i tried that and didn't worked, no thing works as even this a file linux does not recognize!!!!!!!!!!!!
This way i will seriously consider get back to win cause i can't install software here!!!!!!! Plus every thing needs a hell of work to do just simple stuff

---

### Post by baistaef on 2008-07-15
> **RomeReactor said:**
> An easier way is to just drag and drop the executable into the terminal.

Getting the usual message: "No such file or directory"

---

### Post by rixtr66 on 2008-07-15
there are different linux binarys for blender you have to down load the right the one,i downloaded the x86-32 w/python 25 theres one for python 24 as well you have to download the one that you have python for!you do have python??:)
rick

---

### Post by RomeReactor on 2008-07-15
> **baistaef said:**
> Getting the usual message: "No such file or directory"

That's strange; please post the contents of the folder you extracted--if possible, a screenshot. What's the name of the file you downloaded?

---

### Post by baistaef on 2008-07-15
> **rixtr66 said:**
> there are different linux binarys for blender you have to down load the right the one,i downloaded the x86-32 w/python 25 theres one for python 24 as well you have to download the one that you have python for!you do have python??:)
rick

Yes i have python and downloaded the right file still the same problem!!!!

---

### Post by Chris S. on 2008-07-15
> **baistaef said:**
> Getting the usual message: "No such file or directory"

What is the exact command that you are using in the terminal to try to run blender, and what is the exact output that appears in the terminal when it doesn't run?

---

### Post by Tatty on 2008-07-15
Interesting, i just downloaded the tar.bz2 from the blender site.  It appears to be an executable installer, but whenever I try to run it in a terminal it gives this error

```
 error while loading shared libraries: libpython2.5.so.1.0: cannot open shared object file: No such file or directory
```

Isnt python 2.5 installed in hardy by default?

---

### Post by baistaef on 2008-07-15
Thanks all for tring to help but i have had it with linux back to win when i can do the simple stuff without pain in the ***.
Thanks every body.

---

### Post by gandaran on 2008-07-15
i downloaded this file from blender site blender-2.46-linux-glibc236-py24-i386 and I think all you have to do is extract to any folder of you choice, then just click on the blender file to open blender but you need to install glibc236 which I couldn't find in synaptic for it to work.

---

### Post by gandaran on 2008-07-15
> **baistaef said:**
> Thanks all for tring to help but i have had it with linux back to win when i can do the simple stuff without pain in the ***.
Thanks every body.

why don't you get the .deb package from getdeb.

---

### Post by rixtr66 on 2008-07-15
did you down load the python 25 ver. or the 2.4 version that makes a difference,you have to download the x86 binary of the version of python you have,i had no problems with the 25 binary.
rick

---

### Post by fenian on 2008-07-15
> **rixtr66 said:**
> did you down load the python 25 ver. or the 2.4 version that makes a difference,you have to download the x86 binary of the version of python you have,i had no problems with the 25 binary.
rick

If you are using Ubuntu 8.04 (hardy) you need to download the package for python 2.5[ you can use this link]("http://download.blender.org/release/Blender2.46/blender-2.46-linux-glibc236-py25-i386.tar.bz2").

---

### Post by gandaran on 2008-07-15
> **rixtr66 said:**
> did you down load the python 25 ver. or the 2.4 version that makes a difference,you have to download the x86 binary of the version of python you have,i had no problems with the 25 binary.
rick

you are right, python 25 version works!
I like it, I'm going to remove the synaptic version and keep this one.

edit
this is just one of the many reasons I love linux, you are free to do whatever you want, there are many ways you can install software in linux, this blender package is an example, to me, handling it, is just as easy as clicking a .deb to install, I will never go back to the windows s**t.  
I have 4 application's just like this one installed in /opt (which I think  is the best place to put them) for blender, I just had to find a blender icon for the start menu entry I made for blender.

---

### Post by cheapradical on 2008-07-24
h'lo y'all.
i just happened to be looking for an answer to the same question, (re:blender install- i'm assuming we're talking about 8.04 HH?)

so, a week ago,having just installed ubuntu, (upgraded from DD6.0?), blender wasn't on the synpkmgr list, but 2 days later, there it is! so it DLed and said it installed, via synpkgmgr, (the icon's on the app. menu!) but it's nonresponsive: click the ".exe"- nothing, select from menu- nothing, and no, no "README," 

however,
i went to the folder and called the ".exe" and it gave me this:


user@user-desktop:~/Desktop/installs-howtos/blender-2.46-linux-glibc236-py25-i386$ blender
guessing 'blender-bin' == '/usr/bin/blender-bin'
Compiled with Python version 2.5.2.
Checking for installed Python... got it!
Xlib:  extension "GLX" missing on display ":0.0".
intern/ghost/intern/GHOST_WindowX11.cpp:105: X11 glxChooseVisual() failed for OpenGL, verify working openGL system!
ERROR: Unable to open Blender window
user@user-desktop:~/Desktop/installs-howtos/blender-2.46-linux-glibc236-py25-i386$ 


so, how do i verify/install opengl? (not in the synpkgmgr list! -installed or otherwise)

ps
thanks for the help!

---

### Post by cheapradical on 2008-07-24
well, worth a try, but py-2.5.2-2ubuntu4  is already installed.

is this what i hear called dependency issues?

---

### Post by RomeReactor on 2008-07-24
> **cheapradical said:**
> Xlib:  extension "GLX" missing on display ":0.0".

Hi. In your case the problem is not with Blender or Python, but with not having hardware acceleration enabled in your video card. Do you know what model is it? Please post the output of the following:
```
sudo lshw -C display
```
and:
```
glxinfo | grep rendering
```

---

### Post by cheapradical on 2008-07-24
user@user-desktop:~$ sudo lshw -C display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: NV11DDR [GeForce2 MX200]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: b2
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
       configuration: latency=64 maxlatency=1 mingnt=5
user@user-desktop:~$ glxinfo | grep rendering
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
user@user-desktop:~$ 


yeah, i should have mentioned, my computer was hand carved out of stone, (500mg p3- 500mh -intel-aargh)

not an insurmountable hurdle, we hope?

---

### Post by RomeReactor on 2008-07-24
Since Blender is an application for rendering 3D images, it needs as powerful a video card as possible. Try going to 'System->Administration->Hardware Drivers' and enable the nvidia driver there. This should enable hardware acceleration on your video card, though seeing as this is a very old card, it may not be of much help. After installing the driver, run **glxinfo | grep rendering** again; it should return a 'Yes'.

---

### Post by cheapradical on 2008-07-24
it did.

now:

user@user-desktop:~/Desktop/installs-howtos/blender-2.46-linux-glibc236-py25-i386$ ls
blender        BlenderQuickStart.pdf  plugins             release_246.txt
blender.html   copyright.txt          Python-license.txt
blenderplayer  GPL-license.txt        release_244.txt
user@user-desktop:~/Desktop/installs-howtos/blender-2.46-linux-glibc236-py25-i386$ blender
guessing 'blender-bin' == '/usr/bin/blender-bin'
Compiled with Python version 2.5.2.
Checking for installed Python... got it!
Segmentation fault
user@user-desktop:~/Desktop/installs-howtos/blender-2.46-linux-glibc236-py25-i386$ 

"segmentation fault?"
(at least the screen flashed this time!)



thanks, much appreciated.
(gotta go to sleep, now, but i look forward to reading up, tomorrow)

---

### Post by RomeReactor on 2008-07-24
The problem might be that the video card, being as old as it is, doesn't have the necessary extensions to run Blender properly. If you don't need the absolute most up-to-date Blender, you can avoid further complications by installing it from the repositories, either by looking for **blender** in Synaptic (System->Administration->Synaptic) or from the terminal:
```
sudo aptitude install blender
```
After it's installed, you can find it in 'Applications->Graphics->Blender' (there should be two entries, one for fulscreen mode and one for windowed).

Having Blender installed this way will take care of all the dependencies and let you run it without more problems--assuming the video card is up to the task. If you keep getting a segmentation fault, you can find what the problem is in the logs (System->Administration->System Logs), particularly the Xorg log.

---

### Post by cheapradical on 2008-07-28
ok, i'll use an older version, if that's what's necessary, but blend 2.46 is running on the xp partition of this box (apparently?) fine, so i'd like to keep trying for a bit.

syslog (messages) said:
"Jul 27 21:16:29 user-desktop kernel: [10509.967551] blender-bin[7283]: segfault at 00000000 eip 08543541 esp bfd8d290 error 4"

i notice that 3 of the #'s change w each attempt:
the #'s before and after "blender-bin", and the "bfd" phrase. where would i look up that error?

---

