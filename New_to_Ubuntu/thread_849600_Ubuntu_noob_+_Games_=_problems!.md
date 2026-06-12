---
title: "Ubuntu noob + Games = problems!"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by arashiko28 on 2008-07-04
So, I am not so much of a gamer, but do enjoy a couple of them. So, let's go for stages...

1-Runescape: Don't know much about the game, but my neighbor does and he just decided to install Linux to get away from the "viruses that were eating his computer alive" - he's 14... anyway, the game is online and java based, I installed him sun-java-jre6 and changed in the web page, the option to unsigned applet using default java. This slows down the graphics and he is not so happy about it. He wants it in high details as on windows, maybe it's not possible, but i promised to check.

2-Habbo: He also plays Habbo. For this one, I had to install him a windows version of Firefox through wine so that I could install shockwave and he could play. Again, graphics are horribles, with black boxes and a very low resolution making impossible to play.

3-Bejeweled: I installed this one for me on my computer. But at the end I get a message about being unable to create a link to popcap.com and that the game won't work if run. It doesn't, it freezes the computer and had to forcedly shut it down.

4-Course of montezuma: It installed, yet the screen fills with lines and can't play, must go to another desktop, and kill the process by terminal.

5-I want to install sauerbraten with an icon on the game menu.

5-Last but not least, I have a year now trying to fix this with no success and no support, maybe no one know what I'm talking about, it's about trying to install a program to wirelesly project data. I have now managed to run it trough terminal and got a message about mfc42.dll being missing, so I downloaded the DLL and now have this other message:
> ~/Desktop$ wine AddLogixSetup.exe 
fixme:powrprof:DllMain (0x7e300000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
err:module:map_image Could not map section .text, file probably truncated
err:module:import_dll Loading library MFC42.DLL (which is needed by L"Z:\\home\\stephanie\\Desktop\\AddLogixSetup.exe") failed (error c000007b).
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\stephanie\\Desktop\\AddLogixSetup.exe" failed, status c0000135
stephanie@stephanie-laptop:~/Desktop$ fixme:powrprof:DllMain (0x7e300000, 0, 0x1) not fully implemented
wine: Call from 0x7b844cd0 to unimplemented function rpcrt4.dll.I_RpcExceptionFilter, aborting
wine: Call from 0x7b844cd0 to unimplemented function rpcrt4.dll.I_RpcExceptionFilter, aborting


Anybody can help me? Le's make my neighbor fall in love with Ubuntu! And me to love it more!

---

### Post by jamesstansell on 2008-07-04
> **arashiko28 said:**
> 
1-Runescape: Don't know much about the game, but my neighbor does and he just decided to install Linux to get away from the "viruses that were eating his computer alive" - he's 14... anyway, the game is online and java based, I installed him sun-java-jre6 and changed in the web page, the option to unsigned applet using default java. This slows down the graphics and he is not so happy about it. He wants it in high details as on windows, maybe it's not possible, but i promised to check.


You should be able to run the signed applet for runescape.  Try this:
```
$ sudo apt-get remove icedtea-gcjwebplugin
$ sudo apt-get install sun-java6-plugin
$ sudo update-java-alternatives -s java-6-sun
```

I'm not sure about the high details part - you might try asking in the Gaming & Leisure forum.

---

### Post by chrisod on 2008-07-04
I don't think you can run Popcap games in Ubuntu - they require IE due to some Active X stuff. Maybe under wine, I've never tried though. However, Ubuntu comes with a freeware clone of bejweled called Gweled. It's in his games menu.

---

### Post by arashiko28 on 2008-07-04
I am trying to install it on Wine. And it's not even closer gweled to bejeweled 2, the graphics are like comparing an Atari to playstation 2. I have gweled installed. Now that you mention it, I'll try to install IE via wine.:)

---

### Post by arashiko28 on 2008-07-05
I'm on my neighbor's computer, this is what i get when I try the > sudo update-java-alternative -s java-6-sun
 and this is waht I get on every try:
> sudo: update-java-alternative: command not found
vicente@vicente-desktop:~$ sudo apt-get update-java-alternative -s java-6-sun
E: Operación inválida: update-java-alternative
vicente@vicente-desktop:~$ sudo apt-get update java-alternative -s java-6-sun
E: El comando de actualización no toma argumentos


The first E is invalid operation and the second one is that the update comand does no take arguments. :s

---

### Post by jamesstansell on 2008-07-05
Oops - I mistyped the update-java-alternatives command (note the missing 's' on the end)

It's not required for some people, but I have been including it because it does help some people.

---

### Post by nowshining on 2008-07-05
i'm playing bejeweled just fine on my computer. - remove the one from synaptic and install the one from winehq.org.

Then again - i'm running 7.10+ and not hardy heron.

---

### Post by arashiko28 on 2008-07-08
The bejeweled from Linux works fine, I want the one from popcap games. It can't be compared, the game it's 1,000 times more atractive, has levels, puzzles, special levels, nothing to compare to the gweled from ubuntu. and I don't want to compare it.

---

### Post by nowshining on 2008-07-10
okay i switched to hardy - it's working in wine for me just fine, and YES the one from popcap.com, if you have troubles, try manually putting in the reg. code.

if you don't have it- u should of saved the reg. code page as a backup, unless u didn't register/buy the game yet.

edit: I didn't know there was one called gweled in linux. :D

---

