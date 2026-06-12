---
title: "glChess gets crazy in 3D mode"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Dlizard on 2008-06-04
I've been trying to use glChess 2.22.1.1 (the version that came with Hardy) in 3D mode. I select "Settings", "Preferences", and "3D Chess View". The image does appear in 3D, but... When I click in a piece to move the board turns to 3D while the right bottom of the mouse is pressed. It returns to 3D when I release the bottom. After about two moves the system kind of crashes. The screen turns blue and I can see just the empty frame of the board. Often the whole screen turns black. 

Frustrating. The game works pretty decently in 2D, but I would like to have the improved visual 3D effect. Is that possible to play glChess in 3D at all?

---

### Post by Xiong Chiamiov on 2008-06-05
It might be an issue with your video card drivers.  Do you know if you have the restricted (proprietary) drivers installed?  What kind of video card do you have?

---

### Post by Dlizard on 2008-06-05
> **Xiong Chiamiov said:**
> It might be an issue with your video card drivers.  Do you know if you have the restricted (proprietary) drivers installed?  What kind of video card do you have?

Hi. I used the command lspci | grep -i pci || lspci (note: I know virtually nothing about commands, since I am new to Ubuntu; I got this command in the forum in a thread about identifying video cards) and the answer I got was "00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge". Of course it means nothing to me. Based on this information do you think my video card supports 3D on glChess?

Tx.

---

### Post by ByteJuggler on 2008-06-05
That command is wrong I think.  Try

```
lspci | grep -i vga
```

and also

```
lspci | grep -i display
```

By the way, lspci by itself lists (ls) all the pci devices in your system.  "grep" is a tool for looking for lines with specified text, so piping (|) the output from lspci to "grep", looking case insensitively (-i) for "vga" in the first command and "display" in the second.  Thus printing out only the hardware that's likely to be your display adapter.

---

### Post by jualin on 2008-06-05
I have a friend that uses a VIA Video Card similar to what you have, and according to ubuntuforums VIA Video Cards don't work too good with extensive 3d. Do you have compiz enabled?, cause if you can't enable compiz, then 3D is not going to work smoothly in your system. And if you have compiz enabled then you can try disabling it since 2 3D softwares are known too make everything slower, especially in a Video Card like yours. Good luck!

---

### Post by Dlizard on 2008-06-05
> **ByteJuggler said:**
> That command is wrong I think.  Try

```
lspci | grep -i vga
```

and also

```
lspci | grep -i display
```

By the way, lspci by itself lists (ls) all the pci devices in your system.  "grep" is a tool for looking for lines with specified text, so piping (|) the output from lspci to "grep", looking case insensitively (-i) for "vga" in the first command and "display" in the second.  Thus printing out only the hardware that's likely to be your display adapter.


The first command gave me the result: 01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
and the second: 01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
I'm on uncharted waters here. 
To the other person who replied to me: I am a total beginner. Don't even know what "compiz" mean. But appreciate your reply.

---

### Post by jualin on 2008-06-05
Ok, I am sorry about that. Compiz is the Compositing Window Manager that makes all the 3D effects for your Linux PC, something similar to the Windows Vista or Apple's Leaopard Operating Systems 3D effects. And according to your post you have a ATI Radeon 9200 Pro Video Card. This post should point you in the right direction [http://ubuntuforums.org/showthread.php?t=463791]("http://ubuntuforums.org/showthread.php?t=463791")

---

### Post by Dlizard on 2008-06-06
> **jualin said:**
> Ok, I am sorry about that. Compiz is the Compositing Window Manager that makes all the 3D effects for your Linux PC, something similar to the Windows Vista or Apple's Leaopard Operating Systems 3D effects. And according to your post you have a ATI Radeon 9200 Pro Video Card. This post should point you in the right direction [http://ubuntuforums.org/showthread.php?t=463791]("http://ubuntuforums.org/showthread.php?t=463791")


Hey, I don't know if I've done something unwise, but I opened the terminal, typed "compiz" and got the following text:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5960 (rev 01) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

Don't need to say that I didn't understand the meaning of the whole thing, much less the part about trying "to remove that value". :confused:

Can anybody interpret this message and tell me whether it clarifies anything regarding my glChess problem? In other words, does that point to any possible solution?

---

### Post by jualin on 2008-06-06
According to that you dont have Compiz enabled (3d effects) so disregard my post about disabling Compiz. However I can see that your video cards propietary drivers are not installed therefore to have GLChess with 3D you need to install them. Try following the instructions on the link that I posted before. Good luck!

---

### Post by Dlizard on 2008-06-08
> **jualin said:**
> According to that you dont have Compiz enabled (3d effects) so disregard my post about disabling Compiz. However I can see that your video cards propietary drivers are not installed therefore to have GLChess with 3D you need to install them. Try following the instructions on the link that I posted before. Good luck!

I couldn't follow thing on that link. They seem to be discussing another thing (Feisty, MacBook Pro C2D, etc...) that are difficult for me to relate to my problem.

I got some useful information in: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver). I followed the steps mentioned on this link. The result? glChess starts in 3D, I can make the first move in 3D, BUT, when the machine responds with its moves the screens got blank-blue :(

I think maybe the problem could be solved with a change of video card. Does somebody know a better card (still commercially  available) for a motherboard ASRock P4V88+?

---

### Post by Dlizard on 2008-06-24
> **Dlizard said:**
> I couldn't follow thing on that link. They seem to be discussing another thing (Feisty, MacBook Pro C2D, etc...) that are difficult for me to relate to my problem.

I got some useful information in: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver). I followed the steps mentioned on this link. The result? glChess starts in 3D, I can make the first move in 3D, BUT, when the machine responds with its moves the screens got blank-blue :(

I think maybe the problem could be solved with a change of video card. Does somebody know a better card (still commercially  available) for a motherboard ASRock P4V88+?

The problem was totally correct with the information provided on:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)


Now not only Chess but also Brutal Chess work normally in 3D. :):):)

---

### Post by jualin on 2008-06-24
Congrats mate! sorry I couldn't help you more.

---

### Post by Dlizard on 2008-06-27
> **Dlizard said:**
> The problem was totally correct with the information provided on:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)


Now not only Chess but also Brutal Chess work normally in 3D. :):):)

Hey guys. Short burst of happiness. Some hours later I tried the program again and ...the problem is back. Now it starts in 3D, I make the first move in 3D and, when it is the computer turn the chess board disappears and the whole game area turns blue. I removed the "Solved" label for this thread :(:(:(...

---

### Post by jualin on 2008-06-29
Do you have Compiz (visual effects) enable? If you do disable Visual Effects before playing the game. Also maybe after an upgrade of a kernel the driver that you compiled needs to be compiled again. Try booting up with an older kernel (select it with the GRUB Menu when your computer starts), and see if the problem persists.

---

### Post by Dlizard on 2008-06-29
> **jualin said:**
> Do you have Compiz (visual effects) enable? If you do disable Visual Effects before playing the game. Also maybe after an upgrade of a kernel the driver that you compiled needs to be compiled again. Try booting up with an older kernel (select it with the GRUB Menu when your computer starts), and see if the problem persists.

Yesterday I tried some more tricks, and after coping-pasting-runing blindly a sudo command I got on a help forum my computer got definitely kaput. First the terminal screen did not open anymore. Then I made a reboot. The screen was blank. I could still log in "in the dark". No image! After struggling the whole day with just a terminal big screen left (it came back after "rebooting-by-sound-only") I finally gave up, saved what I could with a flash-drive, and reinstalled Hardy all over.

So, basically I am back to point zero. First thing I tried with the new situation was Chess. I check the box 3D Chess View. It did not even open the initial and brief three D screen I got before the crash. What I got was the message: 

[PHP]"Unable to enable 3D mode; You are unable to play in 3D mode due to the following problems:
No Python OpenGL support
No Python GTKGLExt support

Please contact your system administrator to resolve these problems, until then you will be able to play chess in 2D mode."[/PHP]

So, I will start all over and if I get some success (which I doubt) I will post it here. 

I end this message warning the beginners like myself to be EXTREMELY CAREFUL when copying/pasting/running unknown commands on terminal. In my case the guy probably tried to help, but the outcome was total disaster.

---

### Post by jualin on 2008-06-29
The message that you are getting is that you don't have 3D acceleration yet in your computer since you are missing the video card propieteary driver. The guide that you followed before "RadeonDriver" should help you out. You can follow that guide almost "blindly" since it's check by Ubuntu Administrators. Now a trick that I found a long time ago is that whenever something graphical fails, like missing the Graphical User Interface and only having the Command Line Interface is to reconfigure Xorg (Video). Pretty much you have to run > sudo dpkg-reconfigure xserver-xorg and this will give you a nice (command line) wizard to follow which will in most of the times bring back the GUI by using Vesa Drivers or 2D drivers instead of the one that you installed.

---

