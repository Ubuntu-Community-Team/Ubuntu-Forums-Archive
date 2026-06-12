---
title: "Sound problems."
date: 2012-06-17
forum: New to Ubuntu
---

### Post by Mortyman1 on 2012-06-17
Hi, I hope ive not posted this in the wrong place. Im totally new to Linux but im getting the hang of it slowly all except having no sound. Ive been browsing your forums for the last 3 hours trying all sorts of things to get my sound to work. 

When i type lspci i get;

00:00.0 RAM memory: NVIDIA Corporation MCP61 Host Bridge (rev a1)
00:01.0 ISA bridge: NVIDIA Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB controller: NVIDIA Corporation MCP61 USB 1.1 Controller (rev a3)
00:02.1 USB controller: NVIDIA Corporation MCP61 USB 2.0 Controller (rev a3)
00:04.0 PCI bridge: NVIDIA Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: NVIDIA Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: NVIDIA Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: NVIDIA Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
02:00.0 VGA compatible controller: NVIDIA Corporation GT216 [GeForce GT 220] (rev a2)
02:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)

So im guessing that means my sound card is recognised...

Ive checked to make sure im not muted.

Ive added a line of code at the bottom of the text editor when I did something in terminal which i saw in someones post on here

Ive tried 
sudo apt-get remove --purge alsa-base sudo apt-get remove --purge pulseaudio sudo apt-get clean && sudo apt-get autoremove sudo apt-get install alsa-base sudo apt-get install pulseaudio

just feeling pretty lost at the moment. if anyone can help im be grateful

---

### Post by NikTh on 2012-06-17
> **Mortyman1 said:**
> 
Ive added a line of code at the bottom of the text editor when I did something in terminal which i saw in someones post on here

Hi , 
can you post here , where did you wrote that line and what line is this ? 

Did you wrote it to **/etc/modprobe.d/alsa-base.conf** ? 

Try this command from terminal 
```
sudo alsa force-reload
```and see if sound works .

Also give the output of ```
cat /proc/asound/card0/codec* | grep Codec
```And please , when you post here output of commands , **Copy the entire out put and paste between [CODE] brackets by clicking on # at the top of the message pane.**
Thanks.

---

