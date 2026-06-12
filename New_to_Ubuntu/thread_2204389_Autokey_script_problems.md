---
title: "Autokey script problems"
date: 2014-02-08
forum: New to Ubuntu
---

### Post by kaspin2 on 2014-02-08
[FONT=comic sans ms][COLOR=#000080]I've been trying to write a script in Autokey which will 1: open a terminal, and 2: enter some information to change my display.

[/COLOR][/FONT]
[FONT=comic sans ms][COLOR=#000080]     <ctrl>+<alt>+<f2>  (or t) doesn't open a terminal, either in a phrase or script. (What should I put?)

[/COLOR][/FONT]
[FONT=comic sans ms][COLOR=#000080]    Although a phrase will accept quotes within a line (e.g. xrandr --newmode "1304x768_60.00"   81.50  1304 1376 1504 1704  768 771 781 798 -hsync +vsync), I have to delete the quotes for the line to be accepted in a script - as a consequence of which the instruction doesn't work. (How can I retain the quotes within a script?)

[/COLOR][/FONT]
[FONT=comic sans ms][COLOR=#000080]I've tried using the Record keyboard/mouse facility but can't find where the results are stored in Ubuntu 12.04.[/COLOR][/FONT]
[FONT=comic sans ms][COLOR=#000080]Sorry if I'm missing something obvious, but any help would be much appreciated.    Kaspin[/COLOR][/FONT]

---

### Post by TheFu on 2014-02-08
Trying to control GUI programs is hard. Fortunately for you, almost every program in Linux has a CLI version that can control almost everything - including GUI programs.  If you explain what you are trying to accomplish clearly, someone can probably help.  

Using your xrandr example, create a text file and put this inside:
```
#!/bin/bash
/usr/bin/xrandr  --newmode "1304x768_60.00" 81.50 1304 1376 1504 1704 768 771 781 798 -hsync +vsync
```

I did NOT validate that these options do anything desirable or non-dangerous.
Now place that "script" somewhere in your path - ~/bin/ is a good place for personal scripts.  /usr/local/bin/ is a good place for system-level scripts.  Next make the file "executable" using **chmod**.  chmod +x /path/to/script/file

From this point on, run the script you created.

---

### Post by kaspin2 on 2014-02-08
[FONT=comic sans ms][COLOR=#000080]   [/COLOR][/FONT][FONT=comic sans ms][COLOR=#000080]Thank you for your quick reply, TheFu.  [/COLOR][/FONT]
[FONT=comic sans ms][COLOR=#000080] [/COLOR][/FONT][FONT=comic sans ms][COLOR=#000080]  [/COLOR][/FONT]
[FONT=comic sans ms][COLOR=#000080] [/COLOR][/FONT][FONT=comic sans ms][COLOR=#000080]I'm sorry if my question wasn't clear &#8211; I was trying to keep it as concise as possible. What I am trying to do is to alter the screen resolution in Ubuntu 12.04 to fit my 22&#8221; TV, which I use as a monitor, and to make soccer balls look round rather than like rugby balls.[/COLOR][/FONT]
[FONT=comic sans ms][COLOR=#000080] [/COLOR][/FONT][FONT=comic sans ms][COLOR=#000080]
[/COLOR][/FONT]
[FONT=comic sans ms][COLOR=#000080] [/COLOR][/FONT][FONT=comic sans ms][COLOR=#000080]Using randr I found that 1304x768 (3:2) was the best resolution, but I couldn't find a way of keeping it from one boot to another. So, each time I boot up I have to change the resolution by inputting through a terminal:[/COLOR][/FONT]
[FONT=comic sans ms][COLOR=#000080] [/COLOR][/FONT][FONT=comic sans ms][COLOR=#000080]   [/COLOR][/FONT]
[FONT=comic sans ms][COLOR=#000080] [/COLOR][/FONT][FONT=comic sans ms][COLOR=#000080]xrandr --newmode "1304x768_60.00"   81.50  1304 1376 1504 1704  768 771 781 798 -hsync +vsync[/COLOR][/FONT]
[FONT=comic sans ms][COLOR=#000080] [/COLOR][/FONT][FONT=comic sans ms][COLOR=#000080]
[/COLOR][/FONT]
[FONT=comic sans ms][COLOR=#000080] [/COLOR][/FONT][FONT=comic sans ms][COLOR=#000080](the modeline parameters above result from &#8220;sudo cvt&#8221;), and then:[/COLOR][/FONT]
[FONT=comic sans ms][COLOR=#000080] [/COLOR][/FONT][FONT=comic sans ms][COLOR=#000080]
[/COLOR][/FONT]
[FONT=comic sans ms][COLOR=#000080] [/COLOR][/FONT][FONT=comic sans ms][COLOR=#000080]xrandr --addmode VGA1 "1304x768_60.00"[/COLOR][/FONT]
[FONT=comic sans ms][COLOR=#000080] [/COLOR][/FONT][FONT=comic sans ms][COLOR=#000080]
[/COLOR][/FONT]
[FONT=comic sans ms][COLOR=#000080] [/COLOR][/FONT][FONT=comic sans ms][COLOR=#000080]I can store these 2 lines as 2 _**phrases**_ in Autokey. Afterwards , I can open a terminal and put in each line using my 2 Autokey abbreviations. It's quick and easy, but I thought it should be possible to create a _**script**_ in Autokey which would open a terminal and then enter the 2 lines of input. As stated in my original question, the first problem is inputting the equivalent of ctrl+alt+t, and the second is inputting lines containing inverted commas.[/COLOR][/FONT]
[FONT=comic sans ms][COLOR=#000080] [/COLOR][/FONT][FONT=comic sans ms][COLOR=#000080]
[/COLOR][/FONT]
[FONT=comic sans ms][COLOR=#000080] [/COLOR][/FONT][FONT=comic sans ms][COLOR=#000080]I hope to have the possibility of trying your suggestion tomorrow, but if someone can come up with a purely Autokey solution that would interest me too.  Thanks again,  Kaspin
[/COLOR][/FONT]

---

### Post by TheFu on 2014-02-08
Understood. 
I've used xrandr in this way - for a similar purpose. A script will work. There just isn't any need to open a terminal and type 2 lines. The script will do the command, alter the monitor output and be done. Perhaps 10x more efficient.  Anything you type in a terminal can be scripted - ANYTHING.

My script to change the output resolution was actually 
**sudo /usr/bin/xrandr --output DFP2 --mode 1280x720**
I needed the script because it was a laptop and the VGA output usually was not connected to a TV. Sometimes it was using the built-in screen, 1024x600, other times it is connected to a projector, 1280x8, or it could be connected to a 720p TV. I found having 3 scripts to be the easiest way to switch.  BTW, placing a link to that script on your desktop means a double-click would run it. Done and done.

For the newmode, I would modify the /etc/X11/xorg.conf to add the mode for the alternate monitor.  Making it a default there will solve the issue for good. No scripting necessary, but this is still worth knowing (both the script version AND the autokey solution).

I've been on UNIX and Linux systems for a very long time and have needed something like autokey about 3 times, usually when a complex GUI program didn't support command line options. All the other times, I've used scripts - some tiny like this and other times long and complex.  Most of those scripts have been less than 10 lines.

---

### Post by kaspin2 on 2014-02-08
[COLOR=#000080][FONT=comic sans ms]That's amazing &#8211; sounds like a whole new world is out there for me to discover. As a rather ancient OAP it will take me a little while to get my head around it, but I'll get there in the end. Can't wait &#8211; thanks a bundle, TheFu.
[/FONT][/COLOR]
[COLOR=#000080][FONT=comic sans ms] [/FONT][/COLOR][COLOR=#000080][FONT=comic sans ms]Kaspin  [/FONT][/COLOR]

---

### Post by kaspin2 on 2014-02-09
[FONT=comic sans ms][COLOR=#000080]Problem solved, thanks to TheFu. For the moment I've put the xrandr parameters in an .sh file, and "chmoded" it. Then I added it to the start-up applications, so on boot-up I automatically get the desired resolution. Will now play around with more scripts, until I screw up my computer entirely.... Kaspin[/COLOR][/FONT]

---

### Post by cjhabs on 2014-02-09
In that case your next script should be to backup your computer .......

---

