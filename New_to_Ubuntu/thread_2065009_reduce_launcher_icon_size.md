---
title: "reduce launcher icon size?"
date: 2012-09-30
forum: New to Ubuntu
---

### Post by jonabark on 2012-09-30
I got a new acer aspire-one 10 inch for my wife and we are trying to learn ubuntu. I  apparently downloaded the 64 bit version of ub instead of the 32 bit version I intended to use.  it mostly works fine and the processor for the machine is 64 bit so it seems like it should work fine, but ????
Anway. 
I want to reduce the icon size
Help says go to settings: appearance and there is a slider for the icon size but there is no such slider on either tab as many others have also found. It was suggested on one thread that MyUnity would enable this adjustment so I installed from Ub software but when I try to use MyUnity  it says my ubuntu 12.04 is running in 2D mode and many features won't work which turns out to include the icon size slider.

How do I either a) move to 3D mode or b) step by step otherwise fix the problem and does anyone get why this feature doesn't appear in appearances?

---

### Post by Gone fishing on 2012-09-30
You could install [http://ubuntu-tweak.com/downloads/](http://ubuntu-tweak.com/downloads/) this allows you to change various things in Ubuntu including icon size

---

### Post by DogMatix on 2012-09-30
That's very odd there definitely should be a launcher icon size slider at the bottom of the 'look' tab. Is there a bug report in Launchpad relating to this? You shouldn't need MyUnity to remedy this.

EDIT: Ah! may have overlooked the Unity 2D bit in your post. Which I have no experience with. Sorry.

---

### Post by mikewhatever on 2012-09-30
Unity2d is a fallback mode, used when the hardware can't handle Unity well. Unity uses Compiz as window manager, and quite a few graphics chips aren't up to the job. To check if yours can handle Unity, run the following in a terminal window:

```
 /usr/lib/nux/unity_support_test -p
```

You should get an ouput similar to this:

```
~$  /usr/lib/nux/unity_support_test -p  
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)
OpenGL version string:  2.1 Mesa 8.0.2

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

```

So, if the hardware can run Unity, logout, click the cogwheel (next to the username feild), select Ubuntu, and login. That should load Unity, which has the lancher resize feature under Appearence.
If not, and you are stuck with Unity2d, the only way is to manually edit config files as root.
[http://www.dedoimedo.com/computers/ubuntu-unity-2d-resize-launcher.html](http://www.dedoimedo.com/computers/ubuntu-unity-2d-resize-launcher.html)

---

### Post by jonabark on 2012-09-30
So MikeW,
 are you saying that Gone Fishing's solution will not work without the  Unity 3D or should I try that. I am not a gamer and don't need 3D? I am embarrassed to admit that I am reluctant to use the terminal window since it is very foreign territory to me and I'm afraid I will screw something up. But if I need to I guess I will review the guidelins at the top of the Beginner forum and wade in.

---

### Post by jonabark on 2012-09-30
Gone Fishing,
Does this program work without Unity 3D?

---

### Post by mikewhatever on 2012-09-30
I haven't the slightest idea what Gone Fishing is. If Unity (same as Unity3d) works, you shouldn't need any external stuff to modify the launcher size. If not, and CLI is the problem, try this:
[http://www.omgubuntu.co.uk/2012/04/how-to-change-unity-2d-launcher-icon-size-with-a-script](http://www.omgubuntu.co.uk/2012/04/how-to-change-unity-2d-launcher-icon-size-with-a-script)

The download link no longer works, but you can still get the script from the forum thread (bottom of the first post).

The default launcher size is pretty huge for a 10 inch screen.

PS: 32 is the least size that still looks good. Shrinking it more will make the Desktop Switcher icon pop out, as it doesn't resize.

---

### Post by jonabark on 2012-09-30
mikewhatever
Gone Fishing is one of the people who posted a response. His solution was to install ubuntu tweak? So I was just asking if that will work in 2D mode?

---

### Post by mikewhatever on 2012-09-30
> **jonabark said:**
> mikewhatever
Gone Fishing is one of the people who posted a response. His solution was to install ubuntu tweak? So I was just asking if that will work in 2D mode?

Got it, sorry Gone Fishing. :)

...and no, Ubuntu Tweak will not resize the Unity2d launcher. That said, it provides other interesting options - no harm installing it.

---

### Post by deadflowr on 2012-09-30
Hey, follow mikewhatever's command to help figure out what might be the problem.
Also, run the command here:

```
lspci | grep VGA
```

So we can see what card you're running.
Hopefully, the card is capable to run full unity, and the drivers need tweaking.

---

### Post by jonabark on 2012-09-30
I opened terminal, typed in the command( can't copy /paste because I'm reading the forum from my mac.) got no such file or directory
tried deadflower's command and got no such command. How am I screwing up? OK looked in settings/details and have a VESA: Intel XX Graphics card

---

### Post by deadflowr on 2012-09-30
try the command 
```
lspci -v
```

and look for the VGA line.

---

### Post by jonabark on 2012-09-30
Ok here is what I did step by step: opened terminal from the searcher at the top of the launcher, typed exactly and more than once the suggested commands next to the $ sign
got bash: /usr/lib/nux/unity_support_test-p: No such file or directory
WhadIdowrong?
Also is the VESA Intel XX insufficient as a description of the graphics card?

---

### Post by mikewhatever on 2012-09-30
> **jonabark said:**
> Ok here is what I did step by step: opened terminal from the searcher at the top of the launcher, typed exactly and more than once the suggested commands next to the $ sign
got bash: /usr/lib/nux/unity_support_test-p: No such file or directory
WhadIdowrong?
Also is the VESA Intel XX insufficient as a description of the graphics card?

You'd better copy/paste, because you've missed the space between "...test" and "-p".

WhadIdowrong? <-- no spaces, that's wrong.

---

### Post by jonabark on 2012-09-30
I thought I had tried it both ways- with and without  a space since I wasn't sure, but apparently I didn't. 
ANYWAY
I typed it in again and it worked and I got exactly the readout you described with the final line being Unity 3D supported: no   So I guess I have to go the other route you suggested which I will now try. Sorry for the screw-ups I really appreciate your help here.

---

### Post by mikewhatever on 2012-09-30
Don't feel bad. Screwups are OK, they are part of the learning process we've all gone through one way or another. Sometimes,  the curve might be a bit too steep, so people are here to help when needed. 
Anyway, if you want to practice, try **lspci | grep VGA**, and watch both the spaces and capitalization. That should print out some info about the grapgics chip, though with a netbook, there isn't much of a choice beyond Intel's gma3150 or something similar.
PS On the second thought, gma3150 shold be able to run Unity, so you probably have something else.

---

### Post by jonabark on 2012-09-30
OK Mike Here is what I got: 
VGA compatible controller: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller (rev 09)

---

### Post by jonabark on 2012-09-30
So what now Mike?
I went to the site you mentioned and tried the first backup command and got this message: Priscilla@ubuntu:~$ tar cvfz ~/Documents/unity-2d-shell-backup.tar.gz/usr/share/unity-2d/shell/*
tar: Cowardly refusing to create an empty archive
Try `tar --help' or `tar --usage' for more information.

---

### Post by mikewhatever on 2012-09-30
Bingo, and that is Intel's [Cedar Trail platform]("http://www.xbitlabs.com/articles/cpu/display/atom-cedartrtail.html") with gma3xxx graphics. It's rather new, and the driver support is shaky. I am surprized you haven't had problems installing Ubuntu on it.

How about the output of **lspci -nnk | grep -A3 VGA** ? That will also show the driver it uses.

---

### Post by jonabark on 2012-09-30
00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller [8086:0be1] (rev 09)
    Subsystem: Acer Incorporated [ALI] Device [1025:061f]
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:061f]

This is a very inexpensive computer but I think it should serve the demands of the user. I'm just trying to make the desktop environment as user friendly as possible.

---

### Post by mikewhatever on 2012-09-30
> **jonabark said:**
> So what now Mike?
I went to the site you mentioned and tried the first backup command and got this message:priscilla@ubuntu:~$ tar cvfz ~/Documents/unity-2d-shell-backup.tar.gz/usr/share/unity-2d/shell/*
tar: Cowardly refusing to create an empty archive
Try `tar --help' or `tar --usage' for more information.

That one is probably an overkill for now. Why don't we go with the script solution. It's much simpler, and works just as well. I am going to try and attach it to this post. When downloaded, move it from the Downloads folder out to home, and then in a terminal:

```
sudo python ./script.py 32
```

You'll be asked for the password, just type it and hit Enter (no output will show), then logout/login, and the launcher should look much more presentable.

---

### Post by mikewhatever on 2012-09-30
> **jonabark said:**
> 00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller [8086:0be1] (rev 09)
    Subsystem: Acer Incorporated [ALI] Device [1025:061f]
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:061f]

I am afraid you forgot the -k option there, so no driver is shown:
```
lspci -nnk | grep A2 VGA
```

It should look similar to this:
```
~$ lspci -nnk | grep -A3 VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller [8086:8108] (rev 07)
	Subsystem: Dell Device [1028:02c6]
	Kernel driver in use: gma500
	Kernel modules: psb_gfx
```

---

### Post by jonabark on 2012-09-30
OK I have some questions on this: After I download it and save it to my home folder as a script.py file do I do something else with that scrip or do I just enter the sudo line into terminal and logout /login


"That one is  probably an overkill for now. Why don't we go with the script solution.  It's much simpler, and works just as well. I am going to try and attach  it to this post. When downloaded, move it from the Downloads folder out  to home, and then in a terminal:

 	Code:
 	sudo python ./script.py 32 
Then logout/login, and the launcher should look more presentable. 		                   		 		 			  			  			  			  			 				 					Attached Files 					 					 	[IMG]http://ubuntuforums.org/images/attach/py.gif[/IMG] 	[script.py]("http://ubuntuforums.org/attachment.php?attachmentid=224903&d=1349062158") (2.0 KB, 0 views)

---

### Post by mikewhatever on 2012-10-01
Nope, nothing else. Moving it out of the Downloads folder is needed so that the Terminal can find it. It's possible to skip that too, and use '... ./Downloads/script.py 32' instead.

---

### Post by jonabark on 2012-10-01
Awesome! Complete success. That leaves more room and I learned a thing or 2. Thank you so much. Can I send you a pair of home-made glass earrings for a lady friend as a small token. Color?  I work with glass. ( [www.brooksideglassworks.com](www.brooksideglassworks.com) ) Thanks

---

### Post by mikewhatever on 2012-10-01
You are most welcome, glad it worked for you.
I'll have to consult the lady about the earrings, regardless, your success is the ultimate reward.

---

### Post by aimwin on 2013-01-20
> **jonabark said:**
> Awesome! Complete success. That leaves more room and I learned a thing or 2. Thank you so much. Can I send you a pair of home-made glass earrings for a lady friend as a small token. Color?  I work with glass. ( [www.brooksideglassworks.com](www.brooksideglassworks.com) ) Thanks

It works for me too,
 
***_so I would like to join jonabark to thanks mikewhatever_***

I found also that I can do 
[B][I]sudo python ./script.py 25

AND GET EVEN SMALLER ICON SIZES IN THE LAUNCHER.[/I][/B]

-----------------
I have these.
carolyne@aim:~$ ps -ef | grep unity
carolyne  4907  4824  1 07:37 ?        00:00:05 unity-2d-panel
carolyne  4908  4824  1 07:37 ?        00:00:05 unity-2d-shell
carolyne  5099     1  5 07:37 ?        00:00:24 /usr/lib/unity/unity-panel-service
carolyne  5193     1  0 07:37 ?        00:00:00 /usr/lib/unity-lens-applications/unity-applications-daemon
carolyne  5195     1  0 07:37 ?        00:00:00 /usr/lib/unity-lens-files/unity-files-daemon
carolyne  5197     1  0 07:37 ?        00:00:00 /usr/lib/unity-lens-music/unity-music-daemon
carolyne  5199     1  0 07:37 ?        00:00:00 /usr/bin/python /usr/lib/unity-lens-video/unity-lens-video
carolyne  5257     1  0 07:37 ?        00:00:00 /usr/bin/python /usr/lib/unity-scope-video-remote/unity-scope-video-remote
carolyne  5259     1  0 07:37 ?        00:00:00 /usr/lib/unity-lens-music/unity-musicstore-daemon
carolyne  5492  5430  0 07:44 pts/1    00:00:00 grep --color=auto unity
carolyne@aim:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Whistler XT [AMD Radeon HD 6700M Series]
carolyne@aim:~$ /usr/lib/nux/unity_support_test -p
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  22
  Current serial number in output stream:  22
carolyne@aim:~$

---

