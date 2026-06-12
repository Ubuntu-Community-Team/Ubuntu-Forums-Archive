---
title: "boot problems"
date: 2014-01-27
forum: New to Ubuntu
---

### Post by Johanna_Matthiesen on 2014-01-27
Hello
I installed ubuntu 12.04 today and have it as a second OS to Windows7. Everything worked fine, but then it showed me to install 300+ updates, which I did. But after rebooting, I come to the screen to choose between windows and ubuntu. I choose ubuntu and then there is a black screen with some texts, I can only see "ERROR prefix not set". After that, I get to a purple screen which stays there forever. I look in the internet for help but couldn't find anything that would help me. 
Since I'm not talented with computer stuff, I would be happy, to give more information if needed. 
Thank you!

---

### Post by squakie on 2014-01-27
At that purple screen, try pressing ctrl/alt/F1 and see if it brings up a text screen with a login prompt.  If it does, enter in your normal userid, and when prompted enter in your normal password.  The password is not echoed, so it won't look like anything is happening, but it is accepting your keystrokes.

After logging in you should get a text prompt something like: <your userid>@<your computers name in ubuntu>:~$ 

At this prompt, type:

 lspci | grep VGA <press enter>

Copy the result that shows and post it back here.  I'm going off the idea that it is a video things, since I learned earlier today that one of the updates in 12.04xx updates the xserver and could therefore affect your graphics.  Since it stays at that purple screen, and if you can get to the terminal and login, I would be inclined to think it's a video "thing".

---

### Post by Johanna_Matthiesen on 2014-01-28
Thank you very much for your help!
I tried it but it didn't work. There was still the purple screen. Do you have any other idea to fix the problem?

---

### Post by steeldriver on 2014-01-28
If you can't get to a non-GUI virtual terminal by pressing the Ctrl-Alt-F1 key combo (that's all 3 keys together btw - not one after the other) then you can interrupt the boot sequence by holding the SHIFT key right after the Bios screen, and selecting Advanced Options / Recovery Mode --> Drop to root shell

Another option is to interrupt the boot sequence using SHIFT as above and then selecting a previous kernel from the list

---

### Post by Johanna_Matthiesen on 2014-01-28
okay, I now got to the recovery mode, but what do I do next? It shows me a lot of text and the I get following:

BusyBox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu4.1) built-in shell (ash)
(initramfs)

What do I do now?

---

### Post by squakie on 2014-01-28
You don't get a "menu" like screen with several options like "Continue with normal boot" and other "repair" options, including "Drop to root shell" ?

---

### Post by R_King_III on 2014-01-28
It sounds as if your graphics card did not like a certain driver/update. I would first ask which kind of graphics card you're using, so that we may be able to attempt to update the driver via terminal in recovery mode. You can see which graphics hardware you have using: 
lspci -nnk | grep VGA -A1

---

### Post by squakie on 2014-01-28
> **R_King_III said:**
> It sounds as if your graphics card did not like a certain driver/update. I would first ask which kind of graphics card you're using, so that we may be able to attempt to update the driver via terminal in recovery mode. You can see which graphics hardware you have using: 
lspci -nnk | grep VGA -A1

Did you read any of this thread?  This was discussed from the very first reply and the request for the information was made in the very first reply.  Please don't duplicate information as it just needlessly muddles up a thread.

---

### Post by squakie on 2014-01-28
OP - since you don't seem to be able to get to any command line, what happens if you boot using the install media (DVD?) and just select "Try Ubuntu"?  If you can get that to boot to either a desktop or a command line then you can get the information we're looking for.   Also, since you are running Windows 7 also, we can gleen the information from there as well.  I don't remember if the system info says the video chipset or adapter, but I know it can be gotten from the PCI codes in device manager details for the video.  I know it can be gotten from the device manager line for the video adapter - I just need to double check on how to get there in Windows as I haven't used it in a while.  I'll post back when I have that information, but someone else with that knowledge might post back before then and help you as well.

I would first try:

- boot into Windows 7
- *if* there is a "System" icon on your desktop, right-click on it and click on "Properties".[COLOR=#b22222][/COLOR][COLOR=#800080] EDIT:  if "system" is not on the desktop, click on the "start" button, go to the left part of that menu and "My Computer" (I think) should show there - right-click on it and select "Properties"[/COLOR]
- When the new window opens there will be several tabs to select from.  Click on the one that says "Hardware" 
- this should open a screen listing some of the hardware on your PC.  Look for Video Adap[ters - if there is one listed please copy down the line.  If there is not one listed, try left clicking on the line to see if it expands out so you can see the line.  It will *hopefully * have something like "nVidia" or "ATI" or "AMD" or some other name in it.  Post back that line here so we can check it.  

If we need more information than that, we'll post back and you have get the PCI codes from that same part of the screens.

---

