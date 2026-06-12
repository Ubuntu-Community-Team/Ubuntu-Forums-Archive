---
title: "Which Zoom download is best for new users: Ubuntu or Debian?"
date: 2024-10-22
forum: New to Ubuntu
---

### Post by mavengarlick on 2024-10-22
Hi! First post here! I recently installed Ubuntu 24.04.1 LTS and am a very, very new user.

Zoom gives me multiple distro choices and the Ubuntu option seems natural, but duckduckgo's AI chat is advising me to install the debian version. I'm assuming this is due to issues with snap packages and zoom? I've learned the chat is quite a good linux adviser, but I thought I would ask here since it's a subjective question. I'm seeking opinions from experienced users to verify it's advice. 

I'm sure I could probably install either but I'm a _**B**eginner_ with a large, capital _**B**_ and need whatever will work the easiest for me. 

I'm using a modded Thinkpad that is 64 bit. I can post the results of inxi -Fxzzr if needed. I apologize if I have left out needed information. Please let me know and I will rectify that. Thank you!

---

### Post by deadflowr on 2024-10-23
On Ubuntu use Ubuntu versions.

---

### Post by mavengarlick on 2024-10-23
Thank you deadflowr! I installed it successfully and got a meeting started. Everything is functional except for video background. I get an immediate change when setting appearance filter and making other changes to meeting status, so I'm not sure why the background isn't being set. I'm able to do that on my W10 machine and my android phone.

---

### Post by yancek on 2024-10-23
Did you read the post at the link below or something similar and try those instructions?

[https://community.zoom.com/t5/Zoom-Rooms-and-Workspaces/Turning-on-virtual-backgrounds-in-Linux/td-p/159655](https://community.zoom.com/t5/Zoom-Rooms-and-Workspaces/Turning-on-virtual-backgrounds-in-Linux/td-p/159655)

Not sure that will work, rarely use Zoom myself but the post at the link below indicates this has been ongoing and was a problem with earlier versions of Ubuntu.  Maybe it will work with 24.04.

[https://ubuntuforums.org/showthread.php?t=2496060](https://ubuntuforums.org/showthread.php?t=2496060)

---

### Post by Norm24 on 2024-10-23
I downloaded the Ubuntu .deb right from the Zoom website.No issues,works perfectly.

[https://zoom.us/download?os=linux](https://zoom.us/download?os=linux)

---

### Post by mavengarlick on 2024-10-23
yancek, Thank you for this! No I didn't find it in my searches on this issues. I need to work on my google skills! It sounds like it would resolve my issue, but following this instruction:

"   	 	 	 	   [B]    2. Locate & Edit the ZoomMedia.ini File (if needed): 
        &#9702; If the previous option wasn't there, here's how to edit the ZoomMedia.ini file: 
            &#9642; Find the file: Use the command sudo find / -name ZoomMedia.ini. If not found, please also check ~/.config/zoomus.conf.[/B]"I get this result:
'find: &#8216;/run/user/1000/doc&#8217;: Permission denied
 find: &#8216;/run/user/1000/gvfs&#8217;: Permission denied'

Now I'm working through the next bits of instruction with duck.ai, but so far I can't find the ZoomMedia.ini file. The chat is starting to tell me Zoom might not be installed correctly, but is still giving me some options to try.

---

### Post by mavengarlick on 2024-10-23
> **Norm24 said:**
> I downloaded the Ubuntu .deb right from the Zoom website.No issues,works perfectly.

[https://zoom.us/download?os=linux](https://zoom.us/download?os=linux)

Thank you, I might just try this link if I need to reinstall Zoom.
ETA: Yes, this is the same link I used to download zoom originally. I'll try to reinstall once more.

---

### Post by mavengarlick on 2024-10-23
Per the second link in your reply, it appears I need 8 cores to run zoom backgrounds. I know nothing about hardware, but this might be my issue as I have a core i7 from 2018.
When I run inxi I think this is the relevant bit:
CPU:
  Info: dual core model: Intel Core i7-2640M bits: 64 type: MT MCP
    arch: Sandy Bridge rev: 7 cache: L1: 128 KiB L2: 512 KiB L3: 4 MiB

Is it even possible to add the blur background with my setup?

---

### Post by yancek on 2024-10-23
You can find the number of cores with different commands, the simplest probably the one below:

```
sudo cat /proc/cpuinfo | grep "processor"
 
```

---

### Post by mavengarlick on 2024-10-23
That command gives me this result:
processor    : 0
processor    : 1
processor    : 2
processor    : 3

It looks like I'll have to clean my office once W10 goes away on my main laptop. ;) 

Though, if I can manage to keep Ubuntu working well on this one, maybe I can try it on my more robust Thinkpad too. I'll have to look into zoom's W10 requirements vs linux, as my main laptop's CPU only has 4 cores, not 8.

Thanks again for your help!

---

### Post by grahammechanical on 2024-10-23
> but so far I can't find the ZoomMedia.ini file

That sounds suspiciously like some configuration file that would be in a Microsoft Windows application. Linux does not use ini configuration files. 

> The name of these configuration files comes from the filename extension *INI*, short for initialization, used in the MS-DOS operating system which popularized this method of software configuration

[https://en.wikipedia.org/wiki/INI_file](https://en.wikipedia.org/wiki/INI_file)

Regards

---

### Post by grahammechanical on 2024-10-23
I quote

[https://community.zoom.com/t5/Zoom-Rooms-and-Workspaces/Turning-on-virtual-backgrounds-in-Linux/td-p/159655](https://community.zoom.com/t5/Zoom-Rooms-and-Workspaces/Turning-on-virtual-backgrounds-in-Linux/td-p/159655)

> 
[LIST=1]
[*]**Check In-App Settings:**
[LIST]
[*]Even though it's not officially supported, see if the virtual background option is available:
[LIST]
[*]Go to Settings > In Meeting (Advanced) > Virtual Background. 
[*]If you see it, switch it on and see if this will allow the VB to start working 
[/LIST]
    
[/LIST]
    
[/LIST]
 
[LIST=1]
[*]** Locate & Edit the ZoomMedia.ini File (if needed): **
[LIST]
[*]If the previous option wasn't there, here's how to edit the **ZoomMedia.ini** file: 
[/LIST]
    
[/LIST]
 
[LIST=1]
[*]
[LIST]
[*]
[LIST]
[*]Find the file: Use the command **sudo find / -name ZoomMedia.ini**. If not found, please also check **~/.config/zoomus.conf**. 
[*]Open it: Use a text editor (e.g., sudo nano ZoomMedia.ini). 
[*]Add a line: Find the **[FEATURE]** section and add **SMARTVB=1**. 
[*]Save and restart Zoom. 
[/LIST]
    
[/LIST]
    
[/LIST]
 
[LIST=1]
[*]**If Unable to Locate, then Create ZoomMedia.ini (if necessary):**
[LIST]
[*]If the file doesn't exist, create a new text file named **ZoomMedia.ini** in one of these locations: 
[/LIST]
    
[/LIST]
 
[LIST=1]
[*]
[LIST]
[*]
[LIST]
[*]~/.zoom 
[*]/etc/zoomvdi 
[*]~/.config/zoomus.conf 
[/LIST]
    
[/LIST]
    
[/LIST]
 
[LIST]
[*]Add this content:
[LIST]
[*][B][FEATURE]
SMARTVB=1[/B] 
[*]Save and restart Zoom. 
[/LIST]
    
[/LIST]



Ignore references to ZoomMedia.ini file. It will not work in Linux/Ubuntu. You will need to load the file manager (FILES) and turn on Show Hidden files. Click on the hamburger icon (three horizontal lines) and tick show hidden files. 

 In Linux if a file or folder has a dot ( . ) in front of it then it is hidden from the file manager and also from us. So, turn on show hidden files and look for zoomus.conf. I cannot tell you where to find it as I am not using the Debian (deb) packaged version of zoom-client (workplace) but the snap packaged version and the files are in the .snap hidden folder which you may have but it will not have any files for zoom.

Regards

---

### Post by mavengarlick on 2024-10-23
Thank you for telling me about this, you're absolutely right, it did nothing to add it.
I found the zoomus.conf file and opened it with Nano:  

[zoom_new_im]
SMARTVB=1
VirtualBackgroundEnabled=1
is_landscape_mode=true
main_frame_pixel_pos_narrow="376,770"
main_frame_pixel_pos_wide="1280,770"

I looks like there's not much more to do, as VirtualBackground is already enabled. I wish there was a way to at least blur my background.

---

### Post by iamjiwjr on 2024-10-24
For me, the deb is the gold standard. Quality, reliability, "features," it's subjective, but I like the deb better.

---

### Post by Autodave on 2024-10-24
I was running Mint and it ran fine....everything worked.  Moved back to Xubuntu 24.04 and the backgrounds or the blur do not work......they just lock the video.  Audio keeps working.  I have a zoom license.  I have a 12 core with an RTX 3080 and 32G RAM.  I have no idea why mine doesn't do what it used to be able of doing on Mint.

---

