---
title: "Davinci Resolve refuses to work"
date: 2024-08-07
forum: New to Ubuntu
---

### Post by dorian0604 on 2024-08-07
I've been using ubuntu for 3 weeks now (recently switched from widnows) and been experimenting with tools and performance. Now.. I need Davinci resolve for content creation but whenever I try to install it it throws me back the "Missing or outdated system packages detected. Please install the following missing packages: libapr1 libaprutil1 libasound2 libglib2.0-0 libxcb-cursor0" error. Whenever I try installing them I either get back the error "no such repositories found" or it installs half way but doesnt get recognised. Last time libasound2 was installed it crashed out the system. Can anyone help me with it? Would be much appriciated!

---

### Post by #&amp;thj^% on 2024-08-07
Would you please include what Version of Ubuntu, and Desktop is being used...
```
inxi -Fxz
```
Will tell us, details matter.

---

### Post by grahammechanical on 2024-08-07
You will not find Davinci Resolve in the Ubuntu software repositories. The libraries it needs may not be in the Ubuntu repositories either.  You might get better help from the Blackmagic forum.

[https://forum.blackmagicdesign.com/viewtopic.php?f=21&t=194581](https://forum.blackmagicdesign.com/viewtopic.php?f=21&t=194581)

Another thing. When you installed Ubuntu did you tick to install non-free third party software? Doing that will bring in additional audio and video codecs which might help.

I have also found that installing VLC will also bring in a collection of audio and video codecs.

Regards

---

### Post by #&amp;thj^% on 2024-08-07
The OP has the Zip file from Blackmagic  site, just needs help installing it.

But I need the version they are on:
```
Installing Application icons

Updating icon cache

gtk-update-icon-cache: Cache file created successfully.

Installing udev rules

Setting up dvpanels
lib/
lib/libc++abi.so.1
lib/libavahi-client.so.3
lib/libavahi-common.so.3
lib/libdns_sd.so.1
lib/libc++.so.1
lib/libusb-1.0.so.0
lib/libgcc_s.so.1
libDaVinciPanelAPI.so
libFairlightPanelAPI.so
Creating Common Data Dir : /var/BlackmagicDesign/DaVinci Resolve
DaVinci Resolve installed to /opt/resolve

Done
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>

```

---

### Post by dorian0604 on 2024-08-08
latest ubuntu 24.04 LTS and its a ryzen 5, rtx 3070 build. so there should be no reason for it to not work.

---

### Post by dorian0604 on 2024-08-08
how do I use this? (I'm sorry if Im stupid I need time to learn terminal)

---

### Post by #&amp;thj^% on 2024-08-08
> **dorian0604 said:**
> latest ubuntu 24.04 LTS and its a ryzen 5, rtx 3070 build. so there should be no reason for it to not work.

Your almost the same specs as mine.

> **dorian0604 said:**
> how do I use this? (I'm sorry if Im stupid I need time to learn terminal)
Your not stupid, just new to linux, So I was kind of vague for a new user, for what I wanted to see open a terminal and enter this:
```
inxi -Fxz
```
But now I don't need that, I have enough info to try to help you now.

1.Where are you as far as the install process goes?

2.Can you show the steps you have taken now? (this is where I need good information it is important)

---

### Post by dorian0604 on 2024-08-08
I cant post pictures unfortunately but I download the package, unzip it with the pdf guide, run the installation code and I get the said package errors back. No matter how I try to download them from terminal, github etc.

---

### Post by #&amp;thj^% on 2024-08-08
I don't need or want pictures, I need the information from the terminal . Do you know how to copy from the terminal?
For now please run this in a terminal:
```
cd Downloads && ls
```
Paste that back here, and please use Code Tags it helps keep the correct format.
[noparse]```
your paste here
```[/noparse]

---

### Post by dorian0604 on 2024-08-08
I got back the list of my downloads folder.
```
archcraft-2024.07.01-x86_64.iso       NoiseTorch_x64_v0.12.2.tgz balenaEtcher-linux-x64-1.19.21        OneDrive-2024-07-30
 balenaEtcher-linux-x64-1.19.21.zip    OneDrive-2024-07-30.zip
'balenaEtcher-linux-x64-1.19 (2).21'   themes_und_custom
 DaVinci_Resolve_18.6.6_Linux.run      thunderbird.tmp
 DaVinci_Resolve_18.6.6_Linux.zip     'Untitled Project.jpg'
 holy2.jpg                            'WAR THUNDER'
 holy2_munkas.jpg                      wt_launcher_linux_1.0.3.15.tar.gz
 Linux_Installation_Instructions.pdf
```
I just hope I did it right

---

### Post by #&amp;thj^% on 2024-08-08
Perfect. :)
First, I really need to say is this 1st command is so not a good practice and should be avoided as a general rule but they (Black magic) only support CentsOS
so I had to get creative, now that should right there put a little fear in you....LOL
Anyway I've ran it a good spell yesterday and today and things look to be normal on my end YMMV.
```

sudo SKIP_PACKAGE_CHECK=1 ./DaVinci_Resolve_18.6.6_Linux.run -i
```
That should get you installed but broken, due to the missing packages problem.
So now we run a few more commands:
```
sudo cp /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0 /opt/resolve/libs/

```
Now we need to somehow link the missing together.

Pleas run these one line at a time, don't paste this whole code box in the terminal:
```
 cd /opt/resolve/libs
    sudo mkdir not_used
    sudo mv libgio* not_used
    sudo mv libgmodule* not_used

```
Here is what should be close to your speeds as seen in the screen shot
EDIT: You should reboot before running resolve.

---

### Post by dorian0604 on 2024-08-09
Brother in Christ thank you so much for your help!! It works now(well I dont get the icon on the taskbar but not a deadly problem-would be cool however to fix it-). Thanks for the help a lot

---

### Post by dorian0604 on 2024-08-09
I can now open it and start a project but for some reason I cant put mp4 videos on the timeline.. why?

---

### Post by #&amp;thj^% on 2024-08-09
> **dorian0604 said:**
> I can now open it and start a project but for some reason I cant put mp4 videos on the timeline.. why?

I had a similar issue (unable to drag from Media Pool to the timeline, just in one project - I could still drag Titles, but not clips from the media pool!), and the resolution was to notice that none of the video tracks had the "red box" selected. Once I clicked a video track title (V1), then I could resume dragging clips from the media pool.

As badly as I hate sending anyone to google (youtube) this may help: [https://www.youtube.com/watch?v=cYgGil8-j8k](https://www.youtube.com/watch?v=cYgGil8-j8k)

---

### Post by dorian0604 on 2024-08-11
Good it works now (sorry for late response). Only I cant import images bc I get the media offline error.. why is that?

---

### Post by #&amp;thj^% on 2024-08-11
Resolve is kind of a feel your way around type learning. (As most Media editing suites can be)

Media offline issues in DaVinci Resolve are often caused by one of 3 main issues: unlinked clips, unsupported codecs, or missing clips. To fix media offline, you'll want to start by first identifying the possible root cause of the issue:
[list]
    [*]Check File Paths: Hover over the clip in the Media Pool to see if the file path is correct. If the file path isn't correct, your issue is likely unlinked clips.
    [*]Question Mark on Timeline: If you see a question mark on the clip in the timeline, it's usually an indicator that the clip is missing from the Media Pool.
    [*]Playback Issues: If the video doesn't play but the audio does, or if you see a warning about unsupported formats, it's most likely a codec issue.[/list]

By quickly running through this checklist, you can hopefully pinpoint the root cause and get started with the best solution.

To relink the unlinked clips, navigate to the Media Pool under either the "Edit" or "Media" page. Select all the clips showing as offline, then right-click on one of them and choose "Relink Selected Clips."

A dialog box will appear, prompting you to locate the folder containing the original source footage. Once you've selected the correct folder, click "Ok" to complete the relinking process.

Sometimes, the "Media Offline" error could be related to GPU issues, especially if you're working with high-resolution or complex timelines. Ensure your GPU drivers are up-to-date and consider allocating more GPU memory for DaVinci Resolve in the software's preferences. You can also switch between CUDA, OpenCL, or Metal in the settings to see if one performs better than the others.

---

### Post by dorian0604 on 2024-08-11
sadly none worked. I've seen this kind of issue on davinci forums but I couldnt figure out the cause let alone the solution

---

