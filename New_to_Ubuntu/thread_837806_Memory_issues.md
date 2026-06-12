---
title: "Memory issues???"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by ross_m on 2008-06-22
Blender is locking up on me because the cpu is maxing out when I have shitloads of ram available. Is there a blender or ubuntu tweak that might help. Pleeease!!!

ps. posted something similar recently but it seems to have disappeared! Apologies if I'm harping,

Ross

---

### Post by pablolie on 2008-06-22
> **ross_m said:**
> Blender is locking up on me because the cpu is maxing out when I have shitloads of ram available. Is there a blender or ubuntu tweak that might help. Pleeease!!!

ps. posted something similar recently but it seems to have disappeared! Apologies if I'm harping,

Ross

I also run Ubuntu on an old super-portable Sony C1 with 380k of memeory and a Transmeta Crusoe processor that runs at 50% without any apps open and maxes out at 98-100%... and it is never an issue, it runs slowly, but very stable. The problem may be the proces that is causing out the CPU to max out, rather than the fact the CPU is maxed out...?

---

### Post by randy78 on 2008-06-22
> **ross_m said:**
> Blender is locking up on me because the cpu is maxing out when I have shitloads of ram available. Is there a blender or ubuntu tweak that might help. Pleeease!!!

ps. posted something similar recently but it seems to have disappeared! Apologies if I'm harping,

Ross

Not to harp, but maybe it was deleted because of the language...

(Think family friendly)

CPU and RAM are two different beasts, and if something is causing a very high CPU load, all the ram in the world can't help out.

Post your system specs please

---

### Post by ross_m on 2008-06-22
Ubuntu 8.04 (hardy)
kernel 2.6.24-19-generic
Gnome 2.22.2

memory 2.4 GiB
processor amd athlon 64 3500+

---

### Post by randy78 on 2008-06-22
> **ross_m said:**
> Ubuntu 8.04 (hardy)
kernel 2.6.24-19-generic
Gnome 2.22.2

memory 2.4 GiB
processor amd athlon 64 3500+

Are you using the 64 bit version of Hardy or 32 bit?

---

### Post by ross_m on 2008-06-22
64 bit
I think

---

### Post by randy78 on 2008-06-22
> **ross_m said:**
> 64 bit
I think

Double check to make sure...

Are you running Compiz while trying to use Blender?

Compiz is heavy on the video card and should be disabled before using any graphics-intensive apps.

Also, is all of your memory the same speed?
This can be a source of trouble and should be checked :)

---

### Post by ross_m on 2008-06-23
I did check - with 'uname -a' in the terminal which gives this result:
"Linux Rangi 2.6.24-19-generic #1 SMP Wed Jun 4 15:10:52 UTC 2008 x86_64 GNU/Linux"
I'm assuming the "x86_64 GNU/Linux" means it is.

I have disabled Compiz. That is - I have disabled all desktop effects.

Is all my memory the same speed? How would I find that out?

I do know that when Blender freezes, and it eventually does, the blender terminal seems to get locked up trying to sort out the GL libraries, then when I reboot I get an error message something about the gnome daemon unable to get settings. Is this at all related?

ps. I really appreciate your help in this

---

### Post by sdennie on 2008-06-23
You might be able to see the speed of all your memory with:

```

sudo dmidecode --type memory

```

---

### Post by ross_m on 2008-06-23
> **vor said:**
> You might be able to see the speed of all your memory with:

```

sudo dmidecode --type memory

```
Thanks for the hint vor. I did that and get this:

> # dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0006, DMI type 5, 20 bytes
Memory Controller Information
	Error Detecting Method: 64-bit ECC
	Error Correcting Capabilities:
		None
	Supported Interleave: One-way Interleave
	Current Interleave: One-way Interleave
	Maximum Memory Module Size: 1024 MB
	Maximum Total Memory Size: 2048 MB
	Supported Speeds:
		70 ns
		60 ns
	Supported Memory Types:
		Standard
		EDO
	Memory Module Voltage: 3.3 V
	Associated Memory Slots: 2
		0x0007
		0x0008
	Enabled Error Correcting Capabilities:
		None

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A0
	Bank Connections: 1
	Current Speed: 89 ns
	Type: Other Unknown EDO
	Installed Size: 512 MB (Single-bank Connection)
	Enabled Size: 512 MB (Single-bank Connection)
	Error Status: OK

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A1
	Bank Connections: 2
	Current Speed: 89 ns
	Type: Other Unknown EDO
	Installed Size: 2048 MB (Double-bank Connection)
	Enabled Size: 2048 MB (Double-bank Connection)
	Error Status: OK

Handle 0x0019, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 1 GB
	Error Information Handle: Not Provided
	Number Of Devices: 2

Handle 0x001A, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0019
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 512 MB
	Form Factor: DIMM
	Set: None
	Locator: A0
	Bank Locator: Bank0/1
	Type: Unknown
	Type Detail: None
	Speed: 400 MHz (2.5 ns)
	Manufacturer:  
	Serial Number:  
	Asset Tag:  
	Part Number:  

Handle 0x001B, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0019
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: A1
	Bank Locator: Bank2/3
	Type: Unknown
	Type Detail: None
	Speed: 400 MHz (2.5 ns)
	Manufacturer:  
	Serial Number:  
	Asset Tag:  
	Part Number:  


Sorry but this is all a bit eye-watering for me. Any clues as to whether all of this is a Good Thing or not

---

### Post by sdennie on 2008-06-23
That's some odd output.  It says that the largest memory module you can use is 1G and that the most memory you support on your system is 2G.  This isn't my area of expertise but, I would try pulling the 512M memory module and see if you still have the same problems.

---

### Post by ross_m on 2008-06-23
Thanks I'll give it a try tomorrow.

---

### Post by ross_m on 2008-06-23
Ok, I've (finally) removed the 512 M memory stick the readout now says this:

# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0006, DMI type 5, 20 bytes
Memory Controller Information
	Error Detecting Method: 64-bit ECC
	Error Correcting Capabilities:
		None
	Supported Interleave: One-way Interleave
	Current Interleave: One-way Interleave
	Maximum Memory Module Size: 1024 MB
	Maximum Total Memory Size: 2048 MB
	Supported Speeds:
		70 ns
		60 ns
	Supported Memory Types:
		Standard
		EDO
	Memory Module Voltage: 3.3 V
	Associated Memory Slots: 2
		0x0007
		0x0008
	Enabled Error Correcting Capabilities:
		None

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A0
	Bank Connections: 1
	Current Speed: 195 ns
	Type: Other Unknown EDO
	Installed Size: 2048 MB (Double-bank Connection)
	Enabled Size: 2048 MB (Double-bank Connection)
	Error Status: OK

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A1
	Bank Connections: 2
	Current Speed: 195 ns
	Type: Other Unknown EDO
	Installed Size: Not Installed
	Enabled Size: Not Installed
	Error Status: OK

Handle 0x0019, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 1 GB
	Error Information Handle: Not Provided
	Number Of Devices: 2

Handle 0x001A, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0019
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: A0
	Bank Locator: Bank0/1
	Type: Unknown
	Type Detail: None
	Speed: 400 MHz (2.5 ns)
	Manufacturer:  
	Serial Number:  
	Asset Tag:  
	Part Number:  

Handle 0x001B, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0019
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: A1
	Bank Locator: Bank2/3
	Type: Unknown
	Type Detail: None
	Speed: 400 MHz (2.5 ns)
	Manufacturer:  
	Serial Number:  
	Asset Tag:  
	Part Number:  


ps. how do I get all this into one of those gnarly scrolling text boxes???

pps. It still means little to me but it seems to be saying the same thing - minus the ram from the removed card of course. So, to recap Ive been trying to get ubuntu working for 2 weeks now. This is NOT fun. I need to use Blender but it maxes out cpu use while leaving all the installed ram largely untouched. The result is it crawls maddeningly, then eventually freezes. Anyone? Any ideas?

---

### Post by lemuriaX on 2008-06-24
Hey ross_m

to put the code in a code box choose New Reply and then select the text and choose the # button in the HTML editor, to wrap code tags around the selected text.

Sorry can't offer any real help on the Blender issue.

A couple ideas would be:

Try posting in the Multimedia Production forum. 

A search there for "blender" could possibly help:

[http://ubuntuforums.org/search.php?searchid=43515438](http://ubuntuforums.org/search.php?searchid=43515438)


Perhaps could try Ubuntu Studio - the kernel is optimized for multimedia production in that version. 

Could see if Gutsy has the same issue or it;'s unique to Hardy.

Good luck - hang in there.

---

### Post by sdennie on 2008-06-24
What is the output of the following commands:

```

lspci

```

```

glxinfo | grep direct

```

```

ps aux | grep compiz

```

---

### Post by issih on 2008-06-24
Why are you messing around with ram if the process is slow because its cpu intensive?

Ram is memory, its is not directly related to cpu cycles at all.

You can have all the ram in the world, but if you put all your cpus into an infinite loop on a thread that doesn't give up priority your machine will be utterly unusable. Having dual cpus helps as one cpu is potentially still free to respond if the other is busy, but if both are busy you are still going to have to wait.

This doesn't, to me, look like anything necessarily to do with ram at all. 

Blender is a 3d modelling program right? unless it is able to use the video card to do some of its projections/3D matrix modelling it is going to be very hard on CPU usage. Chances are thats just how much its hammering your cpu, and if thats the case your only option is to buy another faster pc, or go make a cup of tea.

If you have some actual reason to think its not just needing that much cpu, what is it?

If you are convinced that it should be better, I'd look at your video card drivers before the ram.

---

### Post by ross_m on 2008-06-24
> **vor said:**
> What is the output of the following commands:

```

lspci

```

```

glxinfo | grep direct

```

```

ps aux | grep compiz

```


Hi vor, I've been offline. Hope you're stiull around :)

```

 lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 400 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

 glxinfo | grep direct
direct rendering: Yes

$ ps aux | grep compiz
rmunro    6071  0.0  0.0   5164   840 pts/0    R+   09:22   0:00 grep compiz
```

---

### Post by ross_m on 2008-06-24
> **issih said:**
> Why are you messing around with ram if the process is slow because its cpu intensive?

not messing with anything brother, just trying to get this thing working.

> **issih said:**
> Blender is a 3d modelling program right? unless it is able to use the video card to do some of its projections/3D matrix modelling it is going to be very hard on CPU usage. Chances are thats just how much its hammering your cpu, and if thats the case your only option is to buy another faster pc, or go make a cup of tea.

If you have some actual reason to think its not just needing that much cpu, what is it?

The actual reason is that it worked fine on XP, no major demands on cpu at all.

> **issih said:**
> If you are convinced that it should be better, I'd look at your video card drivers before the ram.

And one look at the thousands of threads involved in getting video card drivers working under Hardy indicates you're probably right. It's NVidia 6100. Any ideas??

---

### Post by lemuriaX on 2008-06-25
Noticed this thread today, some other folks having similar issues - [http://ubuntuforums.org/showthread.php?t=788964](http://ubuntuforums.org/showthread.php?t=788964)

---

