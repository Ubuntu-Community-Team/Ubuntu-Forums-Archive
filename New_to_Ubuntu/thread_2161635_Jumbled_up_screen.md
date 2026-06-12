---
title: "Jumbled up screen"
date: 2013-07-11
forum: New to Ubuntu
---

### Post by bb94 on 2013-07-11
I was installing Ubuntu alongside Windows 7. At first everything worked, but the screen started jumbling up, showing obvious linear patterns. Now every time I try to log into Ubuntu, I get only the jumbled-up background with the linear patterns. I can log into Windows 7 fine, though.

---

### Post by dannyboy79 on 2013-07-11
what graphics cards are you using in the machine? did you install any drivers for it? if the jumbling screen is to hard to read can you at least hit ctrl-alt-f1 and then login textually? if you can, then please let me know what graphics card you have, you can find out a couple of ways.

```
lshw -class display
```

OR

```
lspci
```

look for display adapter using the second command, then come back here and tell me what graphics chip you're using.

---

### Post by bb94 on 2013-07-11
I have an nVidia GeForce 6150 SE. I think I installed the drivers for Windows, at least. I'll try your suggestion.
Also, you might want to know that Ubuntu was working fine previously, and still does up to logging in. I don't know what happened to mess the graphics up.

Edit: Ubuntu magically stopped with the jumbled-up screen. I used the terminal, and I got this:
```
kook@kook-BK149AA-ABA-s5414y:~$ lspci00:00.0 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: NVIDIA Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB controller: NVIDIA Corporation MCP61 USB 1.1 Controller (rev a3)
00:02.1 USB controller: NVIDIA Corporation MCP61 USB 2.0 Controller (rev a3)
00:04.0 PCI bridge: NVIDIA Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: NVIDIA Corporation MCP61 High Definition Audio (rev a2)
00:07.0 Bridge: NVIDIA Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: NVIDIA Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control

```

---

### Post by dannyboy79 on 2013-07-11
did you use the "Additional Drivers" to install a nvidia driver?

---

### Post by Blankanieves on 2013-07-11
I think you have a better video card but mine is also a Nvidia  video card and i have the same problem i fix it installing mint because ubuntu i cant really pass the first screen,
If you decide to do this I let you the link of the post I made in other forum because with mint i also used to have problem but now i fix them
 [http://www.linuxquestions.org/questions/showthread.php?p=4988595#post4988595](http://www.linuxquestions.org/questions/showthread.php?p=4988595#post4988595)
there is the link
and sorry for my bad English.

---

