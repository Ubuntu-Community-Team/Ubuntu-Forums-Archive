---
title: "New Ubunu User with No HDMI _ HELP"
date: 2022-05-31
forum: New to Ubuntu
---

### Post by stilltrying2 on 2022-05-31
No HDMI:




Here what I have:
Sound application. I show two choices for sound card, choosing digital
because that is what it is. But I have only the optical cable not the HDMI
to select. 


I want to be able to use HDMI
Here is my
```
 lshw -C video


 *-display                 
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:17 memory:de000000-deffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:c0000-dffff
```



Here is my PCI bus

```
00:1f.3 SMBus: Intel Corporation 9 Series Chipset Family SMBus Controller
02:00.0 VGA compatible controller: NVIDIA Corporation Device 2507 (rev a1)
02:00.1 Audio device: NVIDIA Corporation Device 228e (rev a1)
04:00.0 Network controller: Intel Corporation Device 2723 (rev 1a)
```


I&#8217;m using:
Ubuntu 20.04 version
kernel 5.4.0-113-generic


Here is a list of my aplay hardware


```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 11: HDMI 5 [HDMI 5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 12: HDMI 6 [HDMI 6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I&#8217;m using a Nvidia RTX 3050 8GB video card on Intel I7 4790K chip with a Asus Z97 MB with 32G of ram. Works fine on windows. I&#8217;m lost here.


My Question is How do I get the HDMI to play in Ubuntu? How do I get the Sound setting 
to see my HDMI so I can play the sound through HDMI?

---

### Post by TheFu on 2022-05-31
I suspect that HDMI only works when there's a monitor connected via HDMI.
While you can use alsa directly, if you like, most people use PulseAudio for 20.04 audio controls. **pavucontrol** is the GUI tool for this.  I've posted long steps a few times in these forums, so rather than repeat those, I'd suggest you find those posts.  They start by saying to run that command, then start in the right-most tab and enable only the specific hardware you want to use (disable all others), working left in the tabs.

For choosing sinks and sources from the CLI, [Https://ubuntuforums.org/showthread.php?t=2462882&p=14040864#post14040864](Https://ubuntuforums.org/showthread.php?t=2462882&p=14040864#post14040864) I think this doesn't use a GUI.

BTW, please edit the post above to place the terminal output inside forum 'code tags' - how?  [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code)  That way indentation and columns are aligned in the way we are used to seeing them.

---

### Post by stilltrying2 on 2022-05-31
Thank you. I had followed that link and others before. I was not successful thus I posted. I was not aware that this forum had strict rules of formatting. When I have time, I will review them. Thank you. In the mean time, maybe someone else has some suggestions?

---

### Post by TheFu on 2022-05-31
> **stilltrying2 said:**
>   I was not aware that this forum had strict rules of formatting. 

It is about making it easier for others to help.  Formatting that makes information hard to read, makes it hard for people to answer and since nobody here is paid (100% volunteers), having easy to read posts will often get the quickest answers.

---

### Post by stilltrying2 on 2022-06-15
how?

---

### Post by TheFu on 2022-06-15
> **stilltrying2 said:**
> how?

What?

---

### Post by ajgreeny on 2022-06-15
As TheFu says using **Code-Tags** for terminal output makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

I have edited you original post to add tags; see how much easier it is to decipher.

---

### Post by TheFu on 2022-06-15
And I pointed out that **pavucontrol** is the GUI program to manage audio.  It is common to see 10 audio options, so the OP will just need to try them all in that tool.  I don't know how to explain it, just start in the right-most tab and work through it, then move to the next tab to the left, work through it, then to the next tab to the left and work through it.  I think there are 5-6 tabs for controlling which audio devices are used, for which programs and the gain, then the output volume.

Basically, run the program, start in the far right tab and move to the next tab to the left, trying everything.

Of course, the audio stream sent down the HDMI cable has to be one that the monitor/receiver will understand.  If that doesn't happen, then it won't work.  I have an addon device that accepts hdmi input, then splits off the audio to a toslink 5.1 PCM stream for my receiver and sends the video to a projector about 15 ft away.  For my setup, this is the best playback option. The source for the video/audio is a raspberry pi running Linux (osmc) and sending everything out the HDMI port.  OSMC lets be choose if audio transcoding is wanted or if it should just send the stream directly for the audio receiver to handle.

In another room, I have a weenie monitor connected via HDMI. It can handle only PCM audio. No Dolby-anything. No AC3. No AAC. No MP3. No Vorbis, so playback to that monitor is purely PCM stereo audio. Nothing else.  Clearly, a 1st world problem.

---

### Post by stilltrying2 on 2022-06-15
Ty

---

### Post by grahammechanical on 2022-06-15
> I suspect that HDMI only works when there's a monitor connected via HDMI.

That is correct. If this machine is a laptop then System Settings and Audio and video applications will not show an HDMI option unless the laptop is connected to a monitor by an HDMI cable.

If this machine is a desktop with a discrete Nvidia video adapter then the adapter may have an HDMI output port. That port should be connected to the monitor with an HDMI cable. Of course, the monitor should also have an HDMI input port for all this to work.

Over the years I have have connected a machine running Ubuntu to various monitors using Video Graphic Array (VGA) ports: Digital Visual Interface (DVI) as well as High Definition Media Interface (HDMI) and getting sound output.

Regards

---

### Post by stilltrying2 on 2022-07-02
What finally worked for me was to enter this command:

[COLOR=#333333][FONT=DIN-Web-Pro]**sudo ubuntu-drivers autoinstall**[/FONT][/COLOR]

---

