---
title: "HOWTO: Warcraft III with wine"
date: 2005-06-30
forum: Outdated Tutorials &amp; Tips
---

### Post by holomorph on 2005-06-30
Hi, 
I was considering getting a Cedega subscription, since they claim that Warcraft III works well, and then was reading around on the net and saw it mentioned that it actually works under wine just as well.  So I thought I'd give it a shot first; it worked well for me, so I thought I'd share my procedure with other Ubuntu users.  Here's what to do:
[list=1]
[*] Add the wine repository to your sources list:
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
either via Synaptic or just add the line to /etc/apt/sources.list

[*]Refresh your package list:
sudo apt-get update (or click update in Synaptic)

[*] Install winetools (this will install wine also):
sudo apt-get install winetools
or in synaptic search for winetools and install

[*] In a terminal, run 'winetools', it should give you a message about wine not having been configured yet, if it doesn't then you probably have a .wine/ directory in your home folder and you might want to delete that to make sure you're starting from scratch here.
Click QK until you get to the "WineTools" screen.  Select the Base setup and press ok.  From the Base Setup, Create a fake windows drive; make sure to select the correct mount point for your cdrom drive (probably /media/cdrom0). Next install TrueType Font Arial. Finally, install DCOM98.

[*] Exit winetools and open the wine config file that was created in a text editor (eg nano .wine/config).  Look 
for '[Version]' and under that where it says:
"Windows" = "win98"
change it to:
"Windows" = "winxp"
then save the file and exit.

[*] Now it is time to install Warcraft. Put your cd in the drive and type:
wine /media/cdrom0/install.exe
(asssuming that's where your cdrom is mounted)
install as you usually would (I changed the path to C:\Games\Warcraft III, but that's just a personal preference). Exit the installer when you are finished.

[*] Unfortunately wine will not play the movies (though apparently you can watch them in xine or something) so it's best to move them so the game can not find them:
cd .wine/fake_windows/Games/Warcraft\ III/
mv Movies/ Moviez/

[*] Then you can start warcraft with:

wine "Warcraft III.exe" -opengl
[/list]
Note: after upgrading to 1.18 warcraft would not run until I turn on '"HardwareAcceleration" = "Emulation"'	in the [dsound] section of my wine config file; there was an error and message telling me to do so in my terminal when it failed to run.

Let me know if any of this is unclear, I hope it helps.

Bjorn

---

### Post by frodon on 2005-06-30
Isn't it easier to use cedega ?

---

### Post by Heliode on 2005-06-30
[QUOTE=frodon]Isn't it easier to use cedega ?[/QUOTE]

Might be ;) but cedega costs money. I, for one, am glad to see that you can use regular WINE to play games with! 

I might give this a try sometime soon. I'll let you know how it went.

---

### Post by frodon on 2005-06-30
[QUOTE=Heliode]Might be ;) but cedega costs money. I, for one, am glad to see that you can use regular WINE to play games with! 

I might give this a try sometime soon. I'll let you know how it went.[/QUOTE]

can you post here how warcraft III work with wine .. slower, faster, same as window just for comparaison between cedega and wine. I have warcraft III running with cedega but I'm curious to compare with wine,  so as soon as i have time i will try to compare it.

---

### Post by holomorph on 2005-06-30
[QUOTE=frodon]Isn't it easier to use cedega ?[/QUOTE]

From what I was reading,  no, it didn't look any easier with cedega (although maybe the point-to-play thing makes configuration a bit simpler, I donno).  Also wine is free, cedega is not (I did try grabbing the winex cvs and building and installing that, but this was definately easier, and worked better).

As far as speed, I didn't notice a difference from when I played it in windows, but then, it's been a while since I played in windows, I have a fairly fast computer, and I haven't actually played for any length of time under wine, so that's just a basic first impression.

---

### Post by bored2k on 2005-06-30
[QUOTE=frodon]Isn't it easier to use cedega ?[/QUOTE]
 In my experience, YES. I inserted my disc on my computer and typed "cedega Setup.exe", went through the installation, and that was it. 

I found performance to be a lot slower on Linux (unplayable slower), but this is probably because I don't own a high end graphics card that Linux would be friends with (heck, I don't even own one). But still, on Linux I'm not able to play anything 3D other than Counter-Strike on Software mode, but on Windows I have played Half-Life 2 and more recently, Unreal Tournament 2004.

Results may vary.

---

### Post by holomorph on 2005-06-30
Are you running with the -opengl flag?  What I have read indicates that directX is very slow under wine/cedega.  I'm assuming you're getting decent performance in windows on the same machine here. . .

---

### Post by bored2k on 2005-06-30
[QUOTE=holomorph]Are you running with the -opengl flag?  What I have read indicates that directX is very slow under wine/cedega.  I'm assuming you're getting decent performance in windows on the same machine here. . .[/QUOTE]
 Although this was months ago, I'm sure I pretty much ran cedega WarcrapIII.exe with no flag. And yes, my gaming experience in Windows is Ok (I run UT2K4.. of course i can play warcraft :P).

---

### Post by Fexx on 2005-06-30
Got a few errors.

This is installing font.
Choice is Base setup
Choice is TrueType Font Arial with checked=F
arial32.exe
regedit: Can't export. Registry key 'HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall' does not exist!
Success

grep: /home/vinh/.wine/installed.reg: No such file or directory
grep: /home/vinh/.wine/installed.reg: No such file or directory
rm: cannot remove `/home/vinh/.wine/installed.reg': No such file or directory
software installation verified by /home/vinh/.wine/winetools.log
arial32.exe = installed at 01.07.2005 04:23:19
554208


And this is trying to run install.
[email]vinh@SkyNet:~/.wine[/email]$ wine /media/cdrom0/install.exe
err:module:import_dll Library ole32.dll (which is needed by L"D:\\install.exe") not found
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system\\shlwapi.dll") not found
err:module:import_dll Library shlwapi.dll (which is needed by L"c:\\windows\\system\\shell32.dll") not found
err:module:import_dll Library SHELL32.dll (which is needed by L"D:\\install.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"D:\\install.exe" failed, status c0000135

:(


Edit: to get pass that, i had to change back to win98, install dcom and exporer6.1.

---

### Post by gil-galad on 2005-06-30
I run have run warcraft III over both wine and cedega so I can give you a quick advantages of each

Cedega:
- You can run it with directx, but that give no real advantage over -opengl
- The movies work ( you can also just play them with a movie player )
- The brightness toggle does not work in wine
- The sound stutters in wine

Wine:
- Alt-tab actually works with wine, not cedega
- Its free and open source
- You can install it with apt-get

Personally, I don't want to pay for cedega or compile the cvs version, so I am using wine

---

### Post by bigcletus on 2005-06-30
Thanks for the howto.  Works great!  Just can't change the brightness.

---

### Post by Teroedni on 2005-07-03
fixme:actctx:Cr eateActCtxW stub!
wine: Unhandled exception (thread 0027), starting debugger...
WineDbg starting on pid 0x25
Unhandled exception: page fault on read access to 0x7d9bc604 in 32-bit code (0x7 6c58307).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:76c58307 ESP:7d9ae158 EBP:7d9ae178 EFLAGS:00010206(   - 00      - RIP1)
 EAX:0000e314 EBX:76ce1020 ECX:7d9ae2f0 EDX:7d9bc604
 ESI:0000e314 EDI:00000000
Stack dump:
0x7d9ae158:  7d9adef8 77c8b9f0 00000000 7d9ae190
0x7d9ae168:  76de1bd0 77c852a8 76ce1020 7d9ae2f0
0x7d9ae178:  7d9ae1a4 76c5722e 7d9ae2f0 00000003
0x7d9ae188:  7d9ae19c 76d9ed58 00020042 fffffff0
0x7d9ae198:  7d9ae2f0 77c852b8 00000000 7d9ae1c0
0x7d9ae1a8:  7103601a 7d9ae2f0 77c852b8 00000001
Backtrace:
=>1 0x76c58307 ILGetSize in shell32 (0x7d9ae178)
  2 0x76c5722e ILClone in shell32 (0x7d9ae1a4)
fixme:dbghelp:sffip_cb NIY on 'C:\Lego\opt\SHDOCVW.pdb'
  3 0x7103601a in shdocvw (+0x3601a) (0x7d9ae1c0)
  4 0x7108e5d5 in shdocvw (+0x8e5d5) (0x7d9ae1dc)
  5 0x7108bb85 in shdocvw (+0x8bb85) (0x7d9ae26c)
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file MFC42.dbg ("MFC42.dbg")

---

### Post by Teroedni on 2005-07-03
6 0x5f42c582 2242 in mfc42 (0x7d9ae2f0)
  7 0x5f42c01b 424 in mfc42 (0x7d9ae314)
  8 0x5f42b32b 424 in mfc42 (0x7d9ae368)
  9 0x5f42ac23 2143 in mfc42 (0x7d9ae434)
  10 0x5f42a891 451 in mfc42 (0x7d9ae47c)
  11 0x5f42a79e 451 in mfc42 (0x7d9ae4a0)
  12 0x5f41f3e6 in mfc42 (+0x1f3e6) (0x7d9ae538)
  13 0x5f40230b 290 in mfc42 (0x7d9ae558)
  14 0x5f402294 290 in mfc42 (0x7d9ae5b8)
  15 0x5f40221f 290 in mfc42 (0x7d9ae5d4)
  16 0x5f4021d6 290 in mfc42 (0x7d9ae600)
  17 0x76da4a4f WINPROC_wrapper in user32 (0x7d9ae624)
  18 0x76da4db6 WINPROC_wrapper in user32 (0x7d9ae65c)
  19 0x76dab567 in user32 (+0xab567) (0x7d9ae69c)
  20 0x76dabed7 CallWindowProcW in user32 (0x7d9ae6d0)
  21 0x76d76310 in user32 (+0x76310) (0x7d9ae72c)
  22 0x76d781a1 SendMessageTimeoutW in user32 (0x7d9ae790)
  23 0x76d78471 SendMessageW in user32 (0x7d9ae7bc)
  24 0x76d45ec5 in user32 (+0x45ec5) (0x7d9ae884)
  25 0x76d465a0 CreateDialogIndirectParamAorW in user32 (0x7d9ae8a8)

---

### Post by Prudentissimus on 2005-07-03
How did you fix your problem....

---

### Post by Prudentissimus on 2005-07-03
[QUOTE=Fexx]Got a few errors.

This is installing font.
Choice is Base setup
Choice is TrueType Font Arial with checked=F
arial32.exe
regedit: Can't export. Registry key 'HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall' does not exist!
Success

grep: /home/vinh/.wine/installed.reg: No such file or directory
grep: /home/vinh/.wine/installed.reg: No such file or directory
rm: cannot remove `/home/vinh/.wine/installed.reg': No such file or directory
software installation verified by /home/vinh/.wine/winetools.log
arial32.exe = installed at 01.07.2005 04:23:19
554208


And this is trying to run install.
[email]vinh@SkyNet:~/.wine[/email]$ wine /media/cdrom0/install.exe
err:module:import_dll Library ole32.dll (which is needed by L"D:\\install.exe") not found
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system\\shlwapi.dll") not found
err:module:import_dll Library shlwapi.dll (which is needed by L"c:\\windows\\system\\shell32.dll") not found
err:module:import_dll Library SHELL32.dll (which is needed by L"D:\\install.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"D:\\install.exe" failed, status c0000135

:(


Edit: to get pass that, i had to change back to win98, install dcom and exporer6.1.[/QUOTE]
 How did you fix your problem

---

### Post by Prudentissimus on 2005-07-03
[QUOTE=Prudentissimus]How did you fix your problem[/QUOTE]
 When I try to use wine /media/cdrom0/install.exe

it gives me: "No program start menu found."

... What do I do.


Here's what I got in debug:
```

dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"x11drv.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"x11drv.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"x11drv.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/t:
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/z:/mnt/windows/youxi/Warcraft III/user32.dll
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"gdi32.dll" not found in /home/tomz/.wine/dosdevices/t:
warn:file:wine_nt_to_unix_file_name L"gdi32.dll" not found in /home/tomz/.wine/dosdevices/z:/mnt/windows/youxi/Warcraft III/gdi32.dll
warn:file:wine_nt_to_unix_file_name L"gdi32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"gdi32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"gdi32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"gdi32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"advapi32.dll" not found in /home/tomz/.wine/dosdevices/t:
warn:file:wine_nt_to_unix_file_name L"advapi32.dll" not found in /home/tomz/.wine/dosdevices/z:/mnt/windows/youxi/Warcraft III/advapi32.dll
warn:file:wine_nt_to_unix_file_name L"advapi32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"advapi32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"advapi32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"advapi32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/t:
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/z:/mnt/windows/youxi/Warcraft III/kernel32.dll
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"ntdll.dll" not found in /home/tomz/.wine/dosdevices/t:
warn:file:wine_nt_to_unix_file_name L"ntdll.dll" not found in /home/tomz/.wine/dosdevices/z:/mnt/windows/youxi/Warcraft III/ntdll.dll
warn:file:wine_nt_to_unix_file_name L"ntdll.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"ntdll.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"ntdll.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"ntdll.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /home/tomz/.wine/dosdevices/t:
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /home/tomz/.wine/dosdevices/z:/mnt/windows/youxi/Warcraft III/imm32.dll
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"imm32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/t:
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/z:/mnt/windows/youxi/Warcraft III/user32.dll
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"gdi32.dll" not found in /home/tomz/.wine/dosdevices/t:
warn:file:wine_nt_to_unix_file_name L"gdi32.dll" not found in /home/tomz/.wine/dosdevices/z:/mnt/windows/youxi/Warcraft III/gdi32.dll
warn:file:wine_nt_to_unix_file_name L"gdi32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"gdi32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"gdi32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"gdi32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/t:
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/z:/mnt/windows/youxi/Warcraft III/kernel32.dll
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"ntdll.dll" not found in /home/tomz/.wine/dosdevices/t:
warn:file:wine_nt_to_unix_file_name L"ntdll.dll" not found in /home/tomz/.wine/dosdevices/z:/mnt/windows/youxi/Warcraft III/ntdll.dll
warn:file:wine_nt_to_unix_file_name L"ntdll.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"ntdll.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"ntdll.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"ntdll.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:imm:ImmAssociateContext ((nil), 0x77c482b8): semi-stub
warn:keyboard:X11DRV_KEYBOARD_DetectLayout 6 keysyms per keycode not supported, set to 4
warn:file:wine_nt_to_unix_file_name L"x11drv.dll" not found in /home/tomz/.wine/dosdevices/t:
warn:file:wine_nt_to_unix_file_name L"x11drv.dll" not found in /home/tomz/.wine/dosdevices/z:/mnt/windows/youxi/Warcraft III/x11drv.dll
warn:file:wine_nt_to_unix_file_name L"x11drv.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"x11drv.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"x11drv.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"x11drv.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:msvcrt:msvcrt_init_console :Console handle Initialisation FAILED!
warn:file:wine_nt_to_unix_file_name L"wineoss.drv" not found in /home/tomz/.wine/dosdevices/t:
warn:file:wine_nt_to_unix_file_name L"wineoss.drv" not found in /home/tomz/.wine/dosdevices/z:/mnt/windows/youxi/Warcraft III/wineoss.drv
warn:file:wine_nt_to_unix_file_name L"wineoss.drv" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"wineoss.drv" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"wineoss.drv" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"wineoss.drv" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"winmm.dll" not found in /home/tomz/.wine/dosdevices/t:
warn:file:wine_nt_to_unix_file_name L"winmm.dll" not found in /home/tomz/.wine/dosdevices/z:/mnt/windows/youxi/Warcraft III/winmm.dll
warn:file:wine_nt_to_unix_file_name L"winmm.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"winmm.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"winmm.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"winmm.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/t:
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/z:/mnt/windows/youxi/Warcraft III/user32.dll
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/t:
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/z:/mnt/windows/youxi/Warcraft III/kernel32.dll
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:wave:OSS_RawOpenDevice Couldn't open /dev/dsp (Device or resource busy)
warn:wave:OSS_RawOpenDevice Couldn't open /dev/dsp (Device or resource busy)
warn:midi:midiOpenSeq Can't open MIDI device '/dev/sequencer' ! (No such file or directory). If your program needs this (probably not): create it ! ("man MAKEDEV" ?)
warn:mixer:MIX_Open The sound card doesn't support rec level
warn:mixer:MIX_Init couldn't open /dev/mixer1
warn:mixer:MIX_Init couldn't open /dev/mixer2
warn:mixer:MIX_Init couldn't open /dev/mixer3
warn:mixer:MIX_Init couldn't open /dev/mixer4
warn:mixer:MIX_Init couldn't open /dev/mixer5
warn:file:wine_nt_to_unix_file_name L"msacm.drv" not found in /home/tomz/.wine/dosdevices/t:
warn:file:wine_nt_to_unix_file_name L"msacm.drv" not found in /home/tomz/.wine/dosdevices/z:/mnt/windows/youxi/Warcraft III/msacm.drv
warn:file:wine_nt_to_unix_file_name L"msacm.drv" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"msacm.drv" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"msacm.drv" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"msacm.drv" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"msacm32.dll" not found in /home/tomz/.wine/dosdevices/t:
warn:file:wine_nt_to_unix_file_name L"msacm32.dll" not found in /home/tomz/.wine/dosdevices/z:/mnt/windows/youxi/Warcraft III/msacm32.dll
warn:file:wine_nt_to_unix_file_name L"msacm32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"msacm32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"msacm32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"msacm32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"winmm.dll" not found in /home/tomz/.wine/dosdevices/t:
warn:file:wine_nt_to_unix_file_name L"winmm.dll" not found in /home/tomz/.wine/dosdevices/z:/mnt/windows/youxi/Warcraft III/winmm.dll
warn:file:wine_nt_to_unix_file_name L"winmm.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"winmm.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"winmm.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"winmm.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/t:
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/z:/mnt/windows/youxi/Warcraft III/user32.dll
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"advapi32.dll" not found in /home/tomz/.wine/dosdevices/t:
warn:file:wine_nt_to_unix_file_name L"advapi32.dll" not found in /home/tomz/.wine/dosdevices/z:/mnt/windows/youxi/Warcraft III/advapi32.dll
warn:file:wine_nt_to_unix_file_name L"advapi32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"advapi32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"advapi32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"advapi32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/t:
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/z:/mnt/windows/youxi/Warcraft III/kernel32.dll
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"ntdll.dll" not found in /home/tomz/.wine/dosdevices/t:
warn:file:wine_nt_to_unix_file_name L"ntdll.dll" not found in /home/tomz/.wine/dosdevices/z:/mnt/windows/youxi/Warcraft III/ntdll.dll
warn:file:wine_nt_to_unix_file_name L"ntdll.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"ntdll.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"ntdll.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"ntdll.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"winmm.dll" not found in /home/tomz/.wine/dosdevices/t:
warn:file:wine_nt_to_unix_file_name L"winmm.dll" not found in /home/tomz/.wine/dosdevices/z:/mnt/windows/youxi/Warcraft III/winmm.dll
warn:file:wine_nt_to_unix_file_name L"winmm.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"winmm.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"winmm.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"winmm.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/t:
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/z:/mnt/windows/youxi/Warcraft III/user32.dll
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/t:
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/z:/mnt/windows/youxi/Warcraft III/kernel32.dll
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"midimap.drv" not found in /home/tomz/.wine/dosdevices/t:
warn:file:wine_nt_to_unix_file_name L"midimap.drv" not found in /home/tomz/.wine/dosdevices/z:/mnt/windows/youxi/Warcraft III/midimap.drv
warn:file:wine_nt_to_unix_file_name L"midimap.drv" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"midimap.drv" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"midimap.drv" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"midimap.drv" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"winmm.dll" not found in /home/tomz/.wine/dosdevices/t:
warn:file:wine_nt_to_unix_file_name L"winmm.dll" not found in /home/tomz/.wine/dosdevices/z:/mnt/windows/youxi/Warcraft III/winmm.dll
warn:file:wine_nt_to_unix_file_name L"winmm.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"winmm.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"winmm.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"winmm.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/t:
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/z:/mnt/windows/youxi/Warcraft III/user32.dll
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"user32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"advapi32.dll" not found in /home/tomz/.wine/dosdevices/t:
warn:file:wine_nt_to_unix_file_name L"advapi32.dll" not found in /home/tomz/.wine/dosdevices/z:/mnt/windows/youxi/Warcraft III/advapi32.dll
warn:file:wine_nt_to_unix_file_name L"advapi32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"advapi32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"advapi32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"advapi32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/t:
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/z:/mnt/windows/youxi/Warcraft III/kernel32.dll
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows
warn:file:wine_nt_to_unix_file_name L"kernel32.dll" not found in /home/tomz/.wine/dosdevices/c:/windows/system
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:file:wine_nt_to_unix_file_name L"ole32.dll" not found in /home/tomz/.wine/dosdevices/t:
warn:file:wine_nt_to_unix_file_name L"ole32.dll" not found in /home/tomz/.wine/dosdevices/z:/mnt/windows/youxi/Warcraft III/ole32.dll
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle 0x218
warn:gdi:GDI_GetObjPtr Invalid handle 0x218
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:file:CreateFileW Unable to create file L"\\\\.\\Z:" (status c0000022)
warn:x11drv:SWP_DoOwnedPopups (0x10024) hInsertAfter = (nil)
warn:gdi:GDI_GetObjPtr Invalid handle (nil)
warn:x11drv:SWP_DoOwnedPopups (0x10024) hInsertAfter = (nil)
warn:driver:CloseDriver Failed to close driver
warn:driver:CloseDriver Failed to close driver
warn:driver:CloseDriver Failed to close driver
warn:driver:CloseDriver Failed to close driver
warn:driver:CloseDriver Failed to close driver
warn:heap:HeapDestroy attempt to destroy system heap, returning TRUE!
Wine failed with return code 101
/usr/bin/wine: line 123: 11159 Terminated              $XMESSAGE -timeout 30 -buttons "    Dismiss    ":0," Never display this message again ":3 -title "Wine Launch Window" "Invoking $WINEBIN/$WINE_BIN_NAME $@ ...

```

---

### Post by holomorph on 2005-07-04
I think the errors about the missing dll's are from not having installed dcom98.  I know I had similar troubles when I hadn't installed that (was trying to see the minumim that I needed).  Things work fine without IE installed.   Just be sure to switch win98 in the config file back to winxp (or some other NT supposedly works too) or you're likely to have trouble when you try to play about not being able to find your CD.

[QUOTE=Fexx]Got a few errors.
And this is trying to run install.
[email]vinh@SkyNet:~/.wine[/email]$ wine /media/cdrom0/install.exe
err:module:import_dll Library ole32.dll (which is needed by L"D:\\install.exe") not found
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system\\shlwapi.dll") not found
err:module:import_dll Library shlwapi.dll (which is needed by L"c:\\windows\\system\\shell32.dll") not found
err:module:import_dll Library SHELL32.dll (which is needed by L"D:\\install.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"D:\\install.exe" failed, status c0000135

:(


Edit: to get pass that, i had to change back to win98, install dcom and exporer6.1.[/QUOTE]

---

### Post by Prudentissimus on 2005-07-04
[QUOTE=holomorph]I think the errors about the missing dll's are from not having installed dcom98.  I know I had similar troubles when I hadn't installed that (was trying to see the minumim that I needed).  Things work fine without IE installed.   Just be sure to switch win98 in the config file back to winxp (or some other NT supposedly works too) or you're likely to have trouble when you try to play about not being able to find your CD.[/QUOTE]
 what version of wine are you guys using...

---

### Post by Prudentissimus on 2005-07-04
[QUOTE=Prudentissimus]what version of wine are you guys using...[/QUOTE]
 sigh, I just reinstalled Wine 200503... still..... "No Start Menu found" when I try to run...

---

### Post by Prudentissimus on 2005-07-04
well, good news, 

after I install WC3... i tried to run with:

wine W3.exe -opengl

it gave me this:

```

Invoking /usr/lib/wine/wine.bin Warcraft III.exe -opengl ...
fixme:opengl:query_function_pbuffer gl_version is: "1.5.3 NVIDIA 71.74"
fixme:opengl:query_function_pbuffer glx_exts is: "GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_ARB_multisample GLX_NV_float_buffer GLX_ARB_get_proc_address "
fixme:opengl:query_function_pbuffer gl_version is: "1.5.3 NVIDIA 71.74"
fixme:opengl:query_function_pbuffer glx_exts is: "GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_ARB_multisample GLX_NV_float_buffer GLX_ARB_get_proc_address "
fixme:user:EnumDisplayDevicesA ((nil),0,0x7794f86c,0x00000000), stub!
fixme:user:EnumDisplayDevicesA ((nil),0,0x7794f8a4,0x00000000), stub!
fixme:user:EnumDisplayDevicesA ((nil),0,0x7794e56c,0x00000000), stub!
err:x11settings:X11DRV_ChangeDisplaySettingsExW No matching mode found! (NoRes)
epoll_ctl: Operation not permitted
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {860bb310-5d01-11d0-bd3b-00a0c911ce86} not found
fixme:msvcrt:_XcptFilter (-1073741676,0x7794ef2c)semi-stub
err:dbghelp_msc:codeview_process_info Unknown CODEVIEW signature C63A16CD in module war3
Wine failed with return code 1
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset

```

---

### Post by gil-galad on 2005-07-04
Get the latest version of wine by following these instructions [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Then install wine and winetools and run winetools.

---

### Post by Prudentissimus on 2005-07-04
[QUOTE=gil-galad]Get the latest version of wine by following these instructions [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Then install wine and winetools and run winetools.[/QUOTE]
 Can someone show me where I can download the WORKING wine in a *.DEB file? Rather than a SOURCE... I dunno how to compile correctly.

---

### Post by Fexx on 2005-07-05
Yeah, I fixed my problem by just what was under my fist post with a Edit: comment. Seems like holomorph explained it in bit more detail. Cheers.

---

### Post by Zhukov on 2005-07-07
Ok, lets just make a point of the situation:

- Is it playable? I have a GeForce FX5200 (128 MB) and an Intel i855 (64 MB shared), one is good, the other bad, will it be *playable* in any of them?

- Does the sound work or not?

- I also assume it will work flawlessly with LANs...

If anyone could answer me these questions three...

:)

---

### Post by Prudentissimus on 2005-07-07
[QUOTE=Zhukov]Ok, lets just make a point of the situation:

- Is it playable? I have a GeForce FX5200 (128 MB) and an Intel i855 (64 MB shared), one is good, the other bad, will it be *playable* in any of them?

- Does the sound work or not?

- I also assume it will work flawlessly with LANs...

If anyone could answer me these questions three...

:)[/QUOTE]
 Neither of which, the three, works.

Warcraft III doesn't work on Linux with Wine 200503/ Winetools... This sucks.

---

### Post by bigcletus on 2005-07-07
> Ok, lets just make a point of the situation:

- Is it playable? I have a GeForce FX5200 (128 MB) and an Intel i855 (64 MB shared), one is good, the other bad, will it be *playable* in any of them?

Plays just like it is in Windows...seems to run at native speeds without any glitches.  Only problem is brightness cannot be adjusted inside the game :(
> 
- Does the sound work or not?

Yep.
> 
- I also assume it will work flawlessly with LANs...


I haven't played it on a LAN so I can't answer that one.

---

### Post by Nego on 2005-07-30
I have the latest wine cvs (altho I tried this with the wine on synaptic as well). I have DCOM98. I start up warcraft with 
```

wine /home/nego/.wine/drive_c/Program\ Files/Warcraft\ III/Frozen\ Throne.exe -opengl

```
and all I get in output:
```

fixme:ole:ITypeInfo_fnRelease destroy child objects

```
I don't get any errors, except that it cannot find my CD in drive!  :mad:  I tried to install it with wine, and drag it from my windows partition (1.18 patch and tested to work on windows xp).

Here are my wine devices:

```
nego@ubuntu:~$ ls -l ~/.wine/dosdevices/ total 0
lrwxrwxrwx  1 nego nego 24 2005-07-30 17:21 c: -> /home/nego/.wine/drive_c
lrwxrwxrwx  1 nego nego  6 2005-07-30 17:21 d: -> /cdrom
lrwxrwxrwx  1 nego nego 10 2005-07-30 18:20 e: -> /dev/cdrom
lrwxrwxrwx  1 nego nego 20 2005-07-30 17:32 f: -> /home/nego/winetools
lrwxrwxrwx  1 nego nego 13 2005-07-30 18:19 g: -> /media/cdrom0
lrwxrwxrwx  1 nego nego 13 2005-07-30 18:19 h: -> /media/cdrom1
lrwxrwxrwx  1 nego nego 14 2005-07-30 18:19 i: -> /media/floppy0
lrwxrwxrwx  1 nego nego 10 2005-07-30 18:19 j: -> /home/nego
lrwxrwxrwx  1 nego nego  1 2005-07-30 17:21 z: -> /

```

---

### Post by holomorph on 2005-08-01
[QUOTE=Zhukov]Ok, lets just make a point of the situation:

- Is it playable? I have a GeForce FX5200 (128 MB) and an Intel i855 (64 MB shared), one is good, the other bad, will it be *playable* in any of them?

- Does the sound work or not?

- I also assume it will work flawlessly with LANs...

If anyone could answer me these questions three...

:)[/QUOTE]

I got it running on my PIII 450 w/ I think a 64MB Geforce 4 (I think, mb it was 32MB); though I ran in an openbox session to get rid of gnome overhead; seemed to work fine though I didn't play for any significant length of time, just tested it.  For actually playing I use my newer laptop (though the video card is only 32MB); sound works fine on both machines.  I played a game of Frozen Throne on battlenet with no trouble, so I would assume regular LAN would work fine as well.

---

### Post by holomorph on 2005-08-01
[QUOTE=Nego]I have the latest wine cvs (altho I tried this with the wine on synaptic as well). I have DCOM98. I start up warcraft with 
```

wine /home/nego/.wine/drive_c/Program\ Files/Warcraft\ III/Frozen\ Throne.exe -opengl

```
and all I get in output:
```

fixme:ole:ITypeInfo_fnRelease destroy child objects

```
I don't get any errors, except that it cannot find my CD in drive!  :mad:  I tried to install it with wine, and drag it from my windows partition (1.18 patch and tested to work on windows xp).

Here are my wine devices:

```
nego@ubuntu:~$ ls -l ~/.wine/dosdevices/ total 0
lrwxrwxrwx  1 nego nego 24 2005-07-30 17:21 c: -> /home/nego/.wine/drive_c
lrwxrwxrwx  1 nego nego  6 2005-07-30 17:21 d: -> /cdrom
lrwxrwxrwx  1 nego nego 10 2005-07-30 18:20 e: -> /dev/cdrom
lrwxrwxrwx  1 nego nego 20 2005-07-30 17:32 f: -> /home/nego/winetools
lrwxrwxrwx  1 nego nego 13 2005-07-30 18:19 g: -> /media/cdrom0
lrwxrwxrwx  1 nego nego 13 2005-07-30 18:19 h: -> /media/cdrom1
lrwxrwxrwx  1 nego nego 14 2005-07-30 18:19 i: -> /media/floppy0
lrwxrwxrwx  1 nego nego 10 2005-07-30 18:19 j: -> /home/nego
lrwxrwxrwx  1 nego nego  1 2005-07-30 17:21 z: -> /

```[/QUOTE]


well, since it obviously lists your cdrom in your wine devices, my only suggestion is to check your .wine/config file and make sure you have: 
"Windows" = "winxp"
and not 
"Windows" = "win98"

other NT versions of windows are rumored to work here as well, but with 98 it will not find the cdrom drive, even though you have it mapped in your wine devices.

---

### Post by fekimoki on 2005-08-02
W: Failed to fetch [http://wine.sourceforge.net/apt/binary/old/winetools_2.1.1-1_all.deb](http://wine.sourceforge.net/apt/binary/old/winetools_2.1.1-1_all.deb)
  404 Not Found

:(

---

### Post by holomorph on 2005-08-02
[QUOTE=fekimoki]W: Failed to fetch [http://wine.sourceforge.net/apt/binary/old/winetools_2.1.1-1_all.deb](http://wine.sourceforge.net/apt/binary/old/winetools_2.1.1-1_all.deb)
  404 Not Found

:([/QUOTE]
 indeed, it seems to be not there; you might try getting winetools (and possibly wine) from backports:
[http://ubuntuforums.org/showthread.php?t=40291](http://ubuntuforums.org/showthread.php?t=40291)

post and let us know if that works for you.

---

### Post by Nego on 2005-08-02
Well, I reinstalled the game with a different version of wine (off the ubuntu repositories). I switched the windows versions to winxp, when in the latest cvs that wouldnt change anything, now when the game starts up I can hear the CD drive humming away, but I get an error and then a window pops up saying cannot find the cd.

```
nego@ubuntu:~$ wine /home/nego/.wine/fake_windows/Program\ Files/Warcraft\ III/Warcraft\ III.exe -opengl
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6c69006c
fixme:user:SetSystemCursor (0x127e,00007f00),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6c69006c
fixme:user:SetSystemCursor (0x1286,00007f8a),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6c69006c
fixme:user:SetSystemCursor (0x128e,00007f03),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6c69006c
fixme:user:SetSystemCursor (0x1296,00007f01),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6c69006c
fixme:user:SetSystemCursor (0x129e,00007f88),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6c69006c
fixme:user:SetSystemCursor (0x12a6,00007f86),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6c69006c
fixme:user:SetSystemCursor (0x12ae,00007f83),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6c69006c
fixme:user:SetSystemCursor (0x12b6,00007f82),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6c69006c
fixme:user:SetSystemCursor (0x12be,00007f84),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6c69006c
fixme:user:SetSystemCursor (0x12c6,00007f04),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6c69006c
fixme:user:SetSystemCursor (0x12ce,00007f02),stub!
fixme:cdrom:CDROM_DeviceIoControl Unsupported IOCTL 2d1400 (type=2d access=0 func=500 meth=0)
fixme:ntdll:FILE_GetNtStatus Converting errno 16 to STATUS_UNSUCCESSFUL
fixme:user:SetSystemCursor (0x11d6,00007f8a),stub!
fixme:user:SetSystemCursor (0x11de,00007f00),stub!
fixme:user:SetSystemCursor (0x11ee,00007f03),stub!
fixme:user:SetSystemCursor (0x11f6,00007f01),stub!
fixme:user:SetSystemCursor (0x1206,00007f88),stub!
fixme:user:SetSystemCursor (0x1216,00007f86),stub!
fixme:user:SetSystemCursor (0x1226,00007f83),stub!
fixme:user:SetSystemCursor (0x1236,00007f85),stub!
fixme:user:SetSystemCursor (0x1246,00007f82),stub!
fixme:user:SetSystemCursor (0x1256,00007f84),stub!
fixme:user:SetSystemCursor (0x1266,00007f04),stub!
fixme:user:SetSystemCursor (0x1276,00007f02),stub!
err:module:import_dll Library OPENGL32.dll (which is needed by L"C:\\Program Files\\Warcraft III\\Game.dll") not found
Wine exited with a successful status

```

I did notice something however. When I do not have a cd in the drive it will tell me "No disc inserted", but when I do have the disc in there it will tell me "Wrong disc inserted". I've tried it with 2 different cd drives.

---

### Post by maegget on 2005-08-03
[QUOTE=Prudentissimus]sigh, I just reinstalled Wine 200503... still..... "No Start Menu found" when I try to run...[/QUOTE]
Hi, I've been trying to get Warcraft III running with 5.04 and I get this same message when I use the latest version of Wine. I found a page in the winhq site that mentions this problem:
> Warcraft III's install fails with dialog message saying "No program start menu
Adding
 
[Software\\Microsoft\\Windows\\CurrentVersion\\Explorer\\Shell
Folders\\]"Programs"="c:\\windows\\Start Menu\\Programs"
 
to users.reg file in ~/.wine/ fixes the problem.
 
[http://www.winehq.org/hypermail/wine-bugs/2005/02/0300.html](http://www.winehq.org/hypermail/wine-bugs/2005/02/0300.html)

I tried this but to no avail.

Has anyone else had this problem and managed to figure out what to do?

---

### Post by stephen_lau on 2005-08-03
[QUOTE=maegget]Hi, I've been trying to get Warcraft III running with 5.04 and I get this same message when I use the latest version of Wine. I found a page in the winhq site that mentions this problem:
 
[http://www.winehq.org/hypermail/wine-bugs/2005/02/0300.html](http://www.winehq.org/hypermail/wine-bugs/2005/02/0300.html)

I tried this but to no avail.

Has anyone else had this problem and managed to figure out what to do?[/QUOTE]

Just fixed this problem up: make sure you type it in properly - ie. if you just copied and paste from the link, it would give you a line break where it shouldn't be. That is, just add (copy and paste) this line to your user.reg> 
[Software\\Microsoft\\Windows\\CurrentVersion\\Explorer\\Shell Folders]
"Programs"="c:\\windows\\Start Menu\\Programs"

---

### Post by fekimoki on 2005-08-03
> **holomorph]indeed, it seems to be not there said:**
> http://ubuntuforums.org/showthread.php?t=40291[/url]

post and let us know if that works for you.

i managed to get the winetools BP and the wine from apt-get
apt-get says: 'installation success' but they won't replace my 'manualy previous built wine'.. 
what's the best method to uninstall all the wine from this ubuntu machine, bckoz i want to fresh install the wine.

i tried delete every wine folders and files. but still no luck.

after apt-get wine & winetools. what have to do? recompile or ? i ran wine, and it says no ntdll something

---

### Post by holomorph on 2005-08-03
[QUOTE=fekimoki]i managed to get the winetools BP and the wine from apt-get
apt-get says: 'installation success' but they won't replace my 'manualy previous built wine'.. 
what's the best method to uninstall all the wine from this ubuntu machine, bckoz i want to fresh install the wine.

i tried delete every wine folders and files. but still no luck.

after apt-get wine & winetools. what have to do? recompile or ? i ran wine, and it says no ntdll something[/QUOTE]
 This is a good page to read:
[http://www.winehq.org/site/howto](http://www.winehq.org/site/howto)

The first sentance directs you to instructions on removing previous wine versions.  It's definately a good idea to start clean.  Don't forget to delete your .wine directory in your home folder to eliminate any left over configurations.

---

### Post by holomorph on 2005-08-03
[QUOTE=Nego]Well, I reinstalled the game with a different version of wine (off the ubuntu repositories). I switched the windows versions to winxp, when in the latest cvs that wouldnt change anything, now when the game starts up I can hear the CD drive humming away, but I get an error and then a window pops up saying cannot find the cd.

```
nego@ubuntu:~$ wine /home/nego/.wine/fake_windows/Program\ Files/Warcraft\ III/Warcraft\ III.exe -opengl
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6c69006c
fixme:user:SetSystemCursor (0x127e,00007f00),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6c69006c
fixme:user:SetSystemCursor (0x1286,00007f8a),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6c69006c
fixme:user:SetSystemCursor (0x128e,00007f03),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6c69006c
fixme:user:SetSystemCursor (0x1296,00007f01),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6c69006c
fixme:user:SetSystemCursor (0x129e,00007f88),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6c69006c
fixme:user:SetSystemCursor (0x12a6,00007f86),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6c69006c
fixme:user:SetSystemCursor (0x12ae,00007f83),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6c69006c
fixme:user:SetSystemCursor (0x12b6,00007f82),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6c69006c
fixme:user:SetSystemCursor (0x12be,00007f84),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6c69006c
fixme:user:SetSystemCursor (0x12c6,00007f04),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x6c690000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x6c69006c
fixme:user:SetSystemCursor (0x12ce,00007f02),stub!
fixme:cdrom:CDROM_DeviceIoControl Unsupported IOCTL 2d1400 (type=2d access=0 func=500 meth=0)
fixme:ntdll:FILE_GetNtStatus Converting errno 16 to STATUS_UNSUCCESSFUL
fixme:user:SetSystemCursor (0x11d6,00007f8a),stub!
fixme:user:SetSystemCursor (0x11de,00007f00),stub!
fixme:user:SetSystemCursor (0x11ee,00007f03),stub!
fixme:user:SetSystemCursor (0x11f6,00007f01),stub!
fixme:user:SetSystemCursor (0x1206,00007f88),stub!
fixme:user:SetSystemCursor (0x1216,00007f86),stub!
fixme:user:SetSystemCursor (0x1226,00007f83),stub!
fixme:user:SetSystemCursor (0x1236,00007f85),stub!
fixme:user:SetSystemCursor (0x1246,00007f82),stub!
fixme:user:SetSystemCursor (0x1256,00007f84),stub!
fixme:user:SetSystemCursor (0x1266,00007f04),stub!
fixme:user:SetSystemCursor (0x1276,00007f02),stub!
err:module:import_dll Library OPENGL32.dll (which is needed by L"C:\\Program Files\\Warcraft III\\Game.dll") not found
Wine exited with a successful status

```

I did notice something however. When I do not have a cd in the drive it will tell me "No disc inserted", but when I do have the disc in there it will tell me "Wrong disc inserted". I've tried it with 2 different cd drives.[/QUOTE]
 This is probably a silly question, but are you using a real disk? or did you burn a copy or something? And does this disk work when run on a windows machine?  I'm just asking to be sure it's definately a wine issue and not something wrong with the disk itsself.

Otherwise this behaviour seems rather odd to me.  I'll try to remember to post my config file next time I'm at home.

---

### Post by Nego on 2005-08-03
[QUOTE=holomorph]This is probably a silly question, but are you using a real disk? or did you burn a copy or something? And does this disk work when run on a windows machine?  I'm just asking to be sure it's definately a wine issue and not something wrong with the disk itsself.

Otherwise this behaviour seems rather odd to me.  I'll try to remember to post my config file next time I'm at home.[/QUOTE]

Im using a realy Warcraft III CD and it works on Windows. Could you also post the output your getting when you run WC3?

---

### Post by holomorph on 2005-08-04
[QUOTE=Nego]Im using a realy Warcraft III CD and it works on Windows. Could you also post the output your getting when you run WC3?[/QUOTE]


my .wine/config:
```

WINE REGISTRY Version 2
;; inspired by Sidenet (http://sidenet.ddo.jp/winetips/)
;; continued for winetools by Joachim v. Thadden (http://vonthadden.de)
;; Version 2.1.1jo

;; All keys relative to \\Machine\\Software\\Wine\\Wine\\Config

;; If you think it is necessary to show others your complete config for a
;; bug report, filter out empty lines and comments with
;; grep -v "^;" ~/.wine/config | grep '.'

[wine]
"GraphicsDriver" = "x11drv"; (x11drv, ttydrv)
"ShowDotFiles" = "1"
"ShowDirSymlinks" = "1"
"Path" = "c:\\windows;c:\\windows\\system"
"Windows" = "c:\\windows"
"System" = "c:\\windows\\system"
"Temp" = "t:\\"
"Profile" = "c:\\windows\\Profiles\\Administrator"

# [wineconf]

[Version]
; Windows version to imitate (win95,win98,winme,nt351,nt40,win2k,winxp,win2k3,win20,win30,win31)
; Set version to win98 is recommended.
"Windows" = "winxp"
; DOS version to imitate
; Only effect when "Windows" = "win31"
;"DOS" = "6.22"

; Be careful here, wrong DllOverrides settings have the potential
; to pretty much kill your setup.

[DllOverrides]
; Some native dlls won't work, so leave these builtin.
; Do not modify these lines.
"advapi32"     = "builtin";Native version won't work
"avicap32"     = "builtin";Hardware related
"capi2032"     = "builtin";Completely implemented
"comctl32"     = "builtin";Native version cause bugs.
"comdlg32"     = "builtin";thunk
"crtdll"       = "builtin";Completely implemented
"ctl3d32"      = "builtin";thunk
"d3d8"         = "builtin";Hardware related
"d3d9"         = "builtin";Hardware related
"dbghelp"      = "builtin";Native version won't work
"ddeml"        = "builtin";
"ddraw"        = "builtin";Hardware related
"ddrawex"      = "builtin";Hardware related
"dinput"       = "builtin";
"dinput8"      = "builtin";Hardware related
"dispdib"      = "builtin";Completely implemented
"display.drv"  = "builtin";Hardware related
"dmusic32"     = "builtin";thunk
"dplay"        = "builtin";
"dplayx"       = "builtin";
"dpnet"        = "builtin";
"dsound"       = "builtin";Hardware related
"dswave"       = "builtin";Hardware related
"dxdiagn"      = "builtin";
"gdi.exe"      = "builtin";Hardware related
"gdi32"        = "builtin";Hardware related
"glu32"        = "builtin";Hardware related
"gult32"       = "builtin";Hardware related
"icmp"         = "builtin";Hardware related
"ifsmgr.vxd"   = "builtin";Completely implemented
"imaadp32.acm" = "builtin";Completely implemented
"imm"          = "builtin";Special hack needed
"imm32"        = "builtin";Special hack needed
"iphlpapi"     = "builtin";Hardware related
"joystick.drv" = "builtin";Hardware related
"kernel32"     = "builtin";Hardware related
"keyboard.drv" = "builtin";Hardware related
"krnl386.exe"  = "builtin";Hardware related
"lz32"         = "builtin";Completely implemented
"lzexpand"     = "builtin";Completely implemented
"mcianim.drv"  = "builtin";Completely implemented
"mciavi.drv"   = "builtin";Completely implemented
"mcicda.drv"   = "builtin";Completely implemented
"mciseq.drv"   = "builtin";Completely implemented
"mciwave.drv"  = "builtin";Completely implemented
"midimap.drv"  = "builtin";Completely implemented
"mmsystem"     = "builtin";Hardware related
"mouse.drv"    = "builtin";Hardware related
"mpr"          = "builtin";thunk
"msacm.drv"    = "builtin";Completely implemented
"msacm32"      = "builtin";thunk
"msadp32.acm"  = "builtin";Completely implemented
"msvfw32"      = "builtin";Hardware related
"msvidc32"     = "builtin";Completely implemented
"mswsock"      = "builtin";Hardware related
"newdev"       = "builtin";Hardware related
"ntdll"        = "builtin";Hardware related
"opengl32"     = "builtin";Hardware related
"psapi"        = "builtin";Hardware related
"rasapi16"     = "builtin";Hardware related
"rasapi32"     = "builtin";Hardware related
"serialui"     = "builtin";Hardware related
"setupapi"     = "builtin";thunk
"shell"        = "builtin";Special hack needed
"shell32"      = "builtin";Special hack needed
"snmpapi"      = "builtin";Hardware related
"sound"        = "builtin";Hardware related
"sti"          = "builtin";Hardware related
"system.drv"   = "builtin";Hardware related
"tapi32"       = "builtin";Hardware related
"toolhelp"     = "builtin";Hardware related
"twain"        = "builtin";Hardware related
"twain_32"     = "builtin";Hardware related
"user.exe"     = "builtin";Hardware related
"user32"       = "builtin";Hardware related
"ver"          = "builtin";Special hack needed
"version"      = "builtin";Special hack needed
"vnbt.vxd"     = "builtin";
"vtdapi.vxd"   = "builtin";
"vwin32.vxd"   = "builtin";Hardware related
"w32skrnl"     = "builtin";Hardware related
"w32sys"       = "builtin";Hardware related
"win32s16"     = "builtin";Hardware related
"win87em"      = "builtin";Hardware related
"winaspi"      = "builtin";Hardware related
"wing"         = "builtin";Hardware related
"winmm"        = "builtin";Hardware related
"winnls32"     = "builtin";thunk
"winsock"      = "builtin";Hardware related
"wintab"       = "builtin";Hardware related
"wintab32"     = "builtin";Hardware related
"wnaspi32"     = "builtin";Hardware related
"wow32"        = "builtin";
"wprocs"       = "builtin";Hardware related
"ws2_32"       = "builtin";Hardware related
"wsock32"      = "builtin";Hardware related

;Windows Installer
; Install InstMsiA.exe if you get some errors.
"msi"         = "native"

; DCOM 98
; If you'd like to go without DCOM98, remove this line.
"ole32"        = "native"

; Windows ODBC
; If you'd like to use UNIX ODBC, remove this line.
"odbc32"       = "native, builtin"

; AcroReader 6 ActiveX plugin
; must be disabled because it crashes IE6
"pdf.ocx" = "builtin"

; you can specify applications too
; this one will apply for all notepad.exe
;"*notepad.exe" = "native, builtin"
; this one will apply only for a particular file
;"C:\\windows\\regedit.exe" = "native, builtin"

; some spy or definitely not working programs we don't like to be started
"*autorun.exe" = "native,builtin"
"*ctfmon.exe" = "builtin"
"*ddhelp.exe" = "builtin"
"eMusicClient.exe" = "builtin"
"*findfast.exe" = "builtin"
"icwconn1.exe" = "builtin"      ;Prevent from loading ICW even if registry key was changed
"*maildoff.exe" = "builtin"
"*mdm.exe" = "builtin"
"*mosearch.exe" = "builtin"
;"*pstores.exe" = "builtin"     ; needed for IE installation
"qttask.exe" = "builtin"
"realsched.exe" = "builtin"
"winampa.exe" = "builtin"
"AGENTSVR.EXE" = "builtin"

; default for all other dlls and executables
"*" = "native, builtin"
;"*" = "builtin, native"

[x11drv]
; Number of colors to allocate from the system palette
"AllocSystemColors" = "100"
; Use a private color map
"PrivateColorMap" = "N"
; Favor correctness over speed in some graphics operations
"PerfectGraphics" = "N"
; Color depth to use on multi-depth screens
;;"ScreenDepth" = "16"
; Allow the window manager to manage created windows
"Managed" = "Y"
; Use a desktop window of 640x480 for Wine
;"Desktop" = "1024x768"
; Use XFree86 DGA extension if present
; (make sure /dev/mem is accessible by you !)
"UseDGA" = "N"
; Use XVidMode extension if present
"UseXVidMode" = "Y"
; Use XRandR extension if present
"UseXRandR" = "N"
; Use the take focus protocol
"UseTakeFocus" = "Y"
; Enable DirectX mouse grab
"DXGrab" = "Y"
; Create the desktop window with a double-buffered visual
; (useful to play OpenGL games)
"DesktopDoubleBuffered" = "Y"
; Run in synchronous mode (useful for debugging X11 problems)
;;"Synchronous" = "Y"
;
; Use the Render extension to render client side fonts (default "Y")
;;"ClientSideWithRender" = "Y"
; Fallback on X core requests to render client side fonts (default "Y")
;;"ClientSideWithCore" = "Y"
; Set both of the previous two to "N" in order to force X11 server side fonts
;
; Anti-alias fonts if using the Render extension (default "Y")
;;"ClientSideAntiAliasWithRender" = "Y"
; Anti-alias fonts if using core requests fallback (default "Y")
;;"ClientSideAntiAliasWithCore" = "Y"
;
; Use the X Input Method (default "Y")
;;"UseXIM" = "Y"
; XIM Input Style (onthespot, offthespot, overthespot ,root)
;;"InputStyle" = "onthespot"
;
; Codepage for clipboard (0 for ANSI, 20932 for euc-jp)
"TextCP" = "0"

;[ppdev]
;; key:  io-base of the emulated port
;; value : parport-device{,timeout}
;; timeout for auto closing an open device ( not yet implemented)
;"378" = "/dev/parport0"
;"278" = "/dev/parport1"
;"3bc" = "/dev/parport2"

;[spooler]
;;Wine detects CUPS configuration automaticly.
;"FILE:" = "tmp.ps"
;"LPT1:" = "|lpr"
;"LPT2:" = "|gs -sDEVICE=bj200 -sOutputFile=/tmp/fred -q -"
;"LPT3:" = "/dev/lp3"

;[ports]
;"read"  = "0x779,0x379,0x280-0x2a0"
;"write" = "0x779,0x379,0x280-0x2a0"

;[Debug]
;"RelayExclude" = "RtlEnterCriticalSection;RtlLeaveCriticalSection"
;"RelayInclude" = "user32.CreateWindowA"
;"RelayFromExclude" = "user32;x11drv"
;"RelayFromInclude" = "sol.exe"
;"SnoopExclude" = "RtlEnterCriticalSection;RtlLeaveCriticalSection"
;"SpyExclude" = "WM_SIZE;WM_TIMER;"

[registry]
;These are all booleans.  Y/y/T/t/1 are true, N/n/F/f/0 are false.
;Defaults are read all, write to Home
; Where to find the global registries
;"GlobalRegistryDir" = "/etc";
; Global registries (stored in /etc)
"LoadGlobalRegistryFiles" = "Y"
; Load Windows registries from the Windows directory
"LoadWindowsRegistryFiles" = "Y"
; Registry periodic save timeout in seconds
; "PeriodicSave" = "600"
; Save only modified keys
"SaveOnlyUpdatedKeys" = "Y"

[Clipboard]
"ClearAllSelections" = "0"
"PersistentSelection" = "1"
"UsePrimary" = "0"

; List of all directories directly contain .AFM files
;[afmdirs]
;"1" = "/usr/share/ghostscript/fonts"
;"2" = "/usr/share/a2ps/afm"
;"3" = "/usr/share/enscript"
;"4" = "/usr/X11R6/lib/X11/fonts/Type1"

[WinMM]
; Uncomment the "Drivers" line matching your sound setting.

"Drivers" = "wineoss.drv"      ; default for most common configurations
;"Drivers" = "winearts.drv"    ; for KDE
;"Drivers" = "winealsa.drv"    ; for ALSA users
;"Drivers" = "winejack.drv"    ; for Jack sound server
;"Drivers" = "winenas.drv"     ; for NAS sound system
;"Drivers" = "wineaudioio.drv" ; for Solaris machines
;"Drivers" = ""                ; to disable sound
"WaveMapper" = "msacm.drv"
"MidiMapper" = "midimap.drv"

[dsound]
;; HEL only: Number of waveOut fragments ahead to mix in new buffers.
;"HELmargin" = "5"
;; HEL only: Number of waveOut fragments ahead to queue to driver.
;"HELqueue" = "5"
;; Max number of fragments to prebuffer
;"SndQueueMax" = "28"
;; Min number of fragments to prebuffer
;"SndQueueMin" = "12"
;; Forces emulation mode (using wave api)
"HardwareAcceleration" = "Emulation"
;; Sets default playback device (0 - number of devices - 1)
;"DefaultPlayback" = "0"        ; use first device (/dev/dsp)
;"DefaultPlayback" = "1"        ; use second device (/dev/dsp1)
;"DefaultPlayback" = "2"        ; use third device (/dev/dsp2)
;; Sets default capture device (0 - number of devices - 1)
;"DefaultCapture" = "0"         ; use first device (/dev/dsp)
;"DefaultCapture" = "1"         ; use second device (/dev/dsp1)
;"DefaultCapture" = "2"         ; use third device (/dev/dsp2)

[Network]
;; Use the DNS (Unix) host name always as NetBIOS "ComputerName" (boolean, default "Y").
;; Set to N if you need a persistent NetBIOS ComputerName that possibly differs
;; from the Unix host name. You'll need to set ComputerName in
;; HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\ComputerName\ComputerName, too.
;"UseDnsComputerName" = "N"

;; Application specific configuration

; 3 InstallShield versions who like to put their full screen window in front,
; without any chance to switch to another X11 application.
; So just catch them in a desktop window.
; Note: KDE handles this correctry.
;
;[AppDefaults\\_INS0432._MP\\x11drv]
;"Desktop" = "640x480"
;
;[AppDefaults\\_INS0466._MP\\x11drv]
;"Desktop" = "640x480"
;
;[AppDefaults\\_INS0576._MP\\x11drv]
;"Desktop" = "640x480"
;
;[AppDefaults\\_INS5176._MP\\x11drv]
;"Desktop" = "640x480"
;
;[AppDefaults\\_INS5576._MP\\x11drv]
;"Desktop" = "800x600"


;Disable window management for some apps.
;
;Densi denwachou 2003
[AppDefaults\\Blarea8.exe\\x11drv]
"Managed" = "N"
;
;Half Life Demo
[AppDefaults\\hldemo.exe\\x11drv]
"Managed" = "N"
;
;Real Player 10
[AppDefaults\\realplay.exe\\x11drv]
"Managed" = "N"
;
;Winamp
[AppDefaults\\winamp.exe\\x11drv]
"Managed" = "N"


;;Some apps work better with native comctl32
;;NOTE: May cause side effects
;
;;Winamp
;[AppDefaults\\winamp.exe\\DllOverrides]
;"comctl32" = "native"
;
;;WinnyP
;[AppDefaults\\winnyp.exe\\DllOverrides]
;"comctl32" = "native"
;
;;Lunascape
;[AppDefaults\\Luna.exe\\DllOverrides]
;"comctl32" = "native"
;
;;Mame file 2
;[AppDefaults\\mame2.exe\\DllOverrides]
;"comctl32" = "native"


;OpenJane_IE sppedup hack
[AppDefaults\\Jane2ch.exe\\DllOverrides]
"mlang" = "builtin, native"
;"comctl32" = "native"
;;Internet Explorer
;[AppDefaults\\iexplore.exe\\DllOverrides]
;"mlang" = "builtin, native"

;IE4,5,6 Installer
[AppDefaults\\acmsetup.exe\\DllOverrides]
"*comctl32" = "builtin"
[AppDefaults\\grpconv.exe\\DllOverrides]
"*comctl32" = "builtin"
[AppDefaults\\iebatch.exe\\DllOverrides]
"*comctl32" = "builtin"
[AppDefaults\\updcrl.exe\\DllOverrides]
"*comctl32" = "builtin"

;;Windows Media Player 9 Installer
;;WARNING: Windows Media Player 9 Installer may brake your setup!
;[AppDefaults\\setup_wm.exe\\Version]
;"Windows" = "winme"
;[AppDefaults\\setup_wm.exe\\DllOverrides]
;"msvcrt" = "builtin"


;;Example: Catch setup.exe in a desktop window.
;[AppDefaults\\setup.exe\\x11drv]
;"Desktop" = "800x600"

;;Example: Catch full screen games in a desktop window.
;;Half Life Demo
;[AppDefaults\\hldemo.exe\\x11drv]
;"Desktop" = "640x480"

;;Example: XIM Input Style
;[AppDefaults\\notepad.exe\\x11drv]
;"InputStyle" = "offthespot"

;;Example: Windows version
;[AppDefaults\\sol.exe\\Version]
;"Windows" = "nt40"

;; You can add an AppDefault entry like this for such cases.
;[AppDefaults\\pickygame.exe\\dsound]
;"EmulDriver" = "N"

;[AppDefaults\\control.exe\\DllOverrides]
;"ole32"   = "builtin"
;"shlwapi" = "builtin"
;"shell32" = "builtin"
;"*" = "builtin, native"

[AppDefaults\\QuickTimePlayer.exe\\x11drv]
"Managed" = "N"
"Desktop" = "1024x768"

;[AppDefaults\\QuickTimePlayer.exe\\DllOverrides]
;"ddraw" = ""

[AppDefaults\\wmplayer2.exe\\DllOverrides]
"ddraw" = ""

;AcroReader 6
[AppDefaults\\AcroRd32.exe\\Version]
"Windows" = "win2k"

;Real Player 10
[AppDefaults\\realplay.exe\\x11drv]
"Managed" = "N"
"Desktop" = "1024x768"

[AppDefaults\\realplay.exe\\DllOverrides]
"ddraw" = ""

; Awasu RSS Feed Reader
[AppDefaults\\awasu.exe\\Version]
"Windows" = "win2k"

; Bottler XDCC Bott Interface
[AppDefaults\\Bottler.exe\\Version]
"Windows" = "win2k"

; PowBallDX
[AppDefaults\\PowBallDX.exe\\x11drv]
"Desktop" = "640x480"
"Managed" = "Y"
"PerfectGraphics" = "Y"

[AppDefaults\\PowBallDX.exe\\DllOverrides]
"ddraw" = ""

; Miranda IM
[AppDefaults\\miranda32.exe\\Version]
"Windows" = "winxp"

; Wegweiser (Agenda)
[AppDefaults\\WEGWEISER.EXE\\x11drv]
"Desktop" = ""360x500""
"Managed" = "N"

; TVgenial
[AppDefaults\\TVgenial.exe\\x11drv]
"Desktop" = "1024x768"
"Managed" = "N"

; PhotoFiltre
[AppDefaults\\PhotoFiltre.exe\\DllOverrides]
"twain_32" = ""

; KLV 4
[AppDefaults\\klv.exe\\x11drv]
"Desktop" = "1024x768"
"Managed" = "Y"

; MailWasher Pro
[AppDefaults\\MailWasher.exe\\DllOverrides]
"comctl32" = "native"

# [/wineconf]

``` 

and the output when I start warcraft:
```

bjorn@shiver:~ $  wine /home/bjorn/.wine/drive_c/Games/Warcraft\ III/Warcraft\ III.exe -opengl
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x75130000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x75130000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x7513006c
fixme:user:SetSystemCursor (0x1286,00007f00),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x75130000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x75130000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x7513006c
fixme:user:SetSystemCursor (0x128e,00007f8a),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x75130000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x75130000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x7513006c
fixme:user:SetSystemCursor (0x1296,00007f03),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x75130000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x75130000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x7513006c
fixme:user:SetSystemCursor (0x129e,00007f01),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x75130000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x75130000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x7513006c
fixme:user:SetSystemCursor (0x12a6,00007f88),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x75130000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x75130000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x7513006c
fixme:user:SetSystemCursor (0x12ae,00007f86),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x75130000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x75130000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x7513006c
fixme:user:SetSystemCursor (0x12b6,00007f83),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x75130000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x75130000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x7513006c
fixme:user:SetSystemCursor (0x12be,00007f82),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x75130000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x75130000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x7513006c
fixme:user:SetSystemCursor (0x12c6,00007f84),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x75130000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x75130000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x7513006c
fixme:user:SetSystemCursor (0x12ce,00007f04),stub!
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW Animated icons not correctly implemented! 0x75130000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon entry found! 0x75130000
fixme:cursor:CURSORICON_SimulateLoadingFromResourceW icon size ok. offset=0x7513006c
fixme:user:SetSystemCursor (0x12d6,00007f02),stub!
fixme:ntdll:FILE_GetNtStatus Converting errno 16 to STATUS_UNSUCCESSFUL
fixme:user:SetSystemCursor (0x11de,00007f8a),stub!
fixme:user:SetSystemCursor (0x11e6,00007f00),stub!
fixme:user:SetSystemCursor (0x11f6,00007f03),stub!
fixme:user:SetSystemCursor (0x11fe,00007f01),stub!
fixme:user:SetSystemCursor (0x120e,00007f88),stub!
fixme:user:SetSystemCursor (0x121e,00007f86),stub!
fixme:user:SetSystemCursor (0x122e,00007f83),stub!
fixme:user:SetSystemCursor (0x123e,00007f85),stub!
fixme:user:SetSystemCursor (0x124e,00007f82),stub!
fixme:user:SetSystemCursor (0x125e,00007f84),stub!
fixme:user:SetSystemCursor (0x126e,00007f04),stub!
fixme:user:SetSystemCursor (0x127e,00007f02),stub!
fixme:opengl:query_function_pbuffer gl_version is: "1.5.3 NVIDIA 71.74"
fixme:opengl:query_function_pbuffer glx_exts is: "GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_ARB_multisample GLX_NV_float_buffer GLX_ARB_get_proc_address "
fixme:opengl:query_function_pbuffer gl_version is: "1.5.3 NVIDIA 71.74"
fixme:opengl:query_function_pbuffer glx_exts is: "GLX_EXT_visual_info GLX_EXT_visual_rating GLX_SGIX_fbconfig GLX_SGIX_pbuffer GLX_SGI_video_sync GLX_SGI_swap_control GLX_ARB_multisample GLX_NV_float_buffer GLX_ARB_get_proc_address "
fixme:advapi:SetSecurityInfo stub
fixme:user:EnumDisplayDevicesA ((nil),0,0x7796f0e8,0x00000000), stub!
fixme:user:EnumDisplayDevicesA ((nil),0,0x7796f118,0x00000000), stub!
bjorn@shiver:~ $ fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:imm:ImmAssociateContextEx (0x20026, (nil), 16): stub

```

---

### Post by holomorph on 2005-08-05
I just discovered something interesting.  The launcher I created for running warcraft runs the command:

```

wine /home/bjorn/.wine/drive_c/Games/Warcraft\ III/Warcraft\ III.exe -opengl

```

which also of course works fine on the command line.  I can also run
```

$ wine Warcraft\ III.exe -opengl

```

from the directory in wich i have installed warcraft ( /home/bjorn/.wine/drive_c/Games/Warcraft\ III/) and it works as expected.

if however I run
```

$ wine .wine/drive_c/Games/Warcraft\ III/Warcraft\ III.exe -opengl

```

from my home directory, it attempts to start warcraft, but then pops up a dialogue that says:
> 
Warcraft III was unamle to dind a CD Key.  Please reinstall the game from the Warcraft III CD.
I press ok and then another dialogue pops up that says> 
Please Verify that your Warcraft III disc is in your CD-ROM drive, then click on 'Retry'.

So it appears that you must either be in the installation directory, or specify the full path.

---

### Post by Nego on 2005-08-06
[QUOTE=holomorph]I just discovered something interesting.  The launcher I created for running warcraft runs the command:

```

wine /home/bjorn/.wine/drive_c/Games/Warcraft\ III/Warcraft\ III.exe -opengl

```

which also of course works fine on the command line.  I can also run
```

$ wine Warcraft\ III.exe -opengl

```

from the directory in wich i have installed warcraft ( /home/bjorn/.wine/drive_c/Games/Warcraft\ III/) and it works as expected.

if however I run
```

$ wine .wine/drive_c/Games/Warcraft\ III/Warcraft\ III.exe -opengl

```

from my home directory, it attempts to start warcraft, but then pops up a dialogue that says:

I press ok and then another dialogue pops up that says

So it appears that you must either be in the installation directory, or specify the full path.[/QUOTE]


THANK YOU!!!!!!! Finally it is up and running! Running it from my wine directory did the trick! Why is that though?

---

### Post by Kanbeki on 2005-08-09
Argh Help, it worked for a little while but now it refuses to do anything, am I missing a library or something I am using a retail cd from RoC that works fine in windows
here is my output from running with wine
```

$  wine .wine/drive_c/war3/Warcraft\ III.exe -opengl
err:module:import_dll Library OPENGL32.dll (which is needed by L"H:\\.wine\\drive_c\\war3\\Game.dll") not found
Wine exited with a successful status

```

---

### Post by fekimoki on 2005-08-09
[QUOTE=Nego]THANK YOU!!!!!!! Finally it is up and running! Running it from my wine directory did the trick! Why is that though?[/QUOTE]
 :( still cant get it work, even though i using your .wine/config
it always asking to insert the warcraft cd that has been always inserted in my cdrom drive.

---

### Post by Coid on 2005-08-16
Couldn't install TrueType Font Arial, seems like it can't find that file.
Installed 'Warcraft RoC' and 'Warcraft TFT' without problems.

But when I'm trying to start Frozen Throne I get this error
```

err:module:import_dll Library OPENGL32.dll (which is needed by L"C:\\Warcraft III\\Game.dll") not found

```
Followed by a MsgBox *"Couldn't open Game.dll"* and another MsgBox *"Please verify that your Warcraft III disc is in your CD-ROM drive, then click on 'Retry'."*
But the CD is in the CD-ROM drive, and I'm using a real Warcraft CD aswell, working on windows. I've also copied Game.dll (from the windows install) into the Warcraft III dir.

I've tried to start the game as a normal user but also with sudo.
graphic (nvidia) installed and working
sound installed and working

---

### Post by Nego on 2005-08-27
[QUOTE=Coid]Couldn't install TrueType Font Arial, seems like it can't find that file.
Installed 'Warcraft RoC' and 'Warcraft TFT' without problems.

But when I'm trying to start Frozen Throne I get this error
```

err:module:import_dll Library OPENGL32.dll (which is needed by L"C:\\Warcraft III\\Game.dll") not found

```
Followed by a MsgBox *"Couldn't open Game.dll"* and another MsgBox *"Please verify that your Warcraft III disc is in your CD-ROM drive, then click on 'Retry'."*
But the CD is in the CD-ROM drive, and I'm using a real Warcraft CD aswell, working on windows. I've also copied Game.dll (from the windows install) into the Warcraft III dir.

I've tried to start the game as a normal user but also with sudo.
graphic (nvidia) installed and working
sound installed and working[/QUOTE]


I got rid of the Opengl error by looking up gl with synaptic and installing a ton of packages, I don't know which did the trick. As for the CD detection, run the winetools configuration and make sure you put in the correct paths. I have to run these commands every time I start WC3:

```
cd /home/nego/.wine/fake_windows/Program\ Files/Warcraft\ III/
wine Frozen\ Throne.exe -opengl
```

If I don't cd to the directory first it wont detect the CD in the drive, Im not sure why.

---

### Post by CHUCKYCHUCK on 2005-09-08
i have the same problem as Coid ... :s

---

### Post by holomorph on 2005-09-08
Last time I tried playing I had a problem too and as far as I know I hadn't changed anything; I think there may have been a wine update that broke something, but I haven't had time to investigate.  I'd be curious to find out if it is still working for some people?

---

### Post by holomorph on 2005-09-27
Well, at appears that using a noCD crack does the trick; I'm going to play around a bit more and see if I can figure out how to make it work w/o the crack though.

Edit:
Well, seeing as how even battlenet works when I upgraded to 19b and applied a nocd crack (megagames.com) I guess there's really no point in messing with it more; I'd rather not have to put the CD in to play anyway.

---

### Post by ironail on 2005-10-06
have sucessfully installed warcraft3 TFT but when i run the game it says it fails to initialize opengl. i already updated my nvidia video card but im not really sure if i did the update right. my video card is 32mb nvidia TNT2 model 64. thanks in advance for any help and replies.

---

### Post by holomorph on 2005-10-06
[QUOTE=ironail]have sucessfully installed warcraft3 TFT but when i run the game it says it fails to initialize opengl. i already updated my nvidia video card but im not really sure if i did the update right. my video card is 32mb nvidia TNT2 model 64. thanks in advance for any help and replies.[/QUOTE]

You can test that you have hardware acceleration working for your card by running 'glxgears' on the command line.  Also 'glxinfo' is sometimes a useful app (look for direct rendering).  Anyway, if glxgears works for you then it's probably an issue with warcraft; otherwise it's an issue with your opengl setup.

---

### Post by Viorus on 2006-05-16
is there any way to fix the "cd not found" problem? i dont like to use a nocd cuz it gives problems later while trying to connect to battlenet (as i know from before).

I am still a wine-nub and i really could need some good tips (i tried the site [http://appdb.winehq.org/appview.php?versionId=1177]("http://appdb.winehq.org/appview.php?versionId=1177")) but to be honest it didnt help me much

what ive done so far is browsing the playdisk and then typing
```
$ wine "Warcraft III.exe" -opengl
```
I also edited the HKEY_CURRENT_USER\Software\Blizzard Entertainment\Warcraft III as they told in the other tutorial.
after the install i tried to run the game by typing
```
$ wine Warcraft\ III.exe
``` will in the map where i installed the game. and as i said above it tells me to inset the disk

---

### Post by holomorph on 2006-05-16
there might be a way to get it to recognise you have the disk in, but I think it's kinda spotty and highly dependant on your wine version.  I reccommend the nocd crack, it's never caused me any trouble connecting to battle.net (however, a generated cd key will certainly cause problems).

run w/ the -opengl flag, otherwise it'll try to use directx, which will make things very slow.

---

### Post by Viorus on 2006-05-18
[QUOTE=holomorph]there might be a way to get it to recognise you have the disk in, but I think it's kinda spotty and highly dependant on your wine version.  I reccommend the nocd crack, it's never caused me any trouble connecting to battle.net (however, a generated cd key will certainly cause problems).

run w/ the -opengl flag, otherwise it'll try to use directx, which will make things very slow.[/QUOTE]


guess ive been unlucky with the right nocds then...
may i ask for a good site where you got your nocds from? :D 
the site ive used most is megagames.com maybe not the best choice >_<

---

### Post by JeronimoGe on 2006-05-18
I have question!

I've install WC III TFT with 1.20C update, runs great, but I need to add a local server, in windows i only to have run a *.reg file and the server is added. In LINUX i have a great problem,

AnyOne Help me pls, if you can?:) 


Thanks you... :)

---

### Post by holomorph on 2006-05-18
Megagames is the only place I know for CD cracks; haven't bothered to look anywhere else.

---

### Post by Viorus on 2006-05-18
[IMG]http://i3.photobucket.com/albums/y73/Viorus/93298234.jpg[/IMG]


>_< anyone knows what this and why i get this error :confused:

---

### Post by MillDaKill on 2006-05-19
OK I just got this all working but now I can't get that font to install.  How do I install TrueType Font Arial ?


To anyone having any problems... Here are somethings I had to do to get it to work online.
1. download all of the wc3 updates from blizzards webpage and install them by hand.
2. find a cd crack that is for the most recent version or else you wont be able to go onto blizzards servers.

---

### Post by JeronimoGe on 2006-05-20
[QUOTE=MillDaKill]OK I just got this all working but now I can't get that font to install.  How do I install TrueType Font Arial ?


To anyone having any problems... Here are somethings I had to do to get it to work online.
1. download all of the wc3 updates from blizzards webpage and install them by hand.
2. find a cd crack that is for the most recent version or else you wont be able to go onto blizzards servers.[/QUOTE]
 copy your font to, .wine/drive_c find there fonts :) and paste there!

---

### Post by hyapadi on 2006-05-21
[QUOTE=Viorus][IMG]http://i3.photobucket.com/albums/y73/Viorus/93298234.jpg[/IMG]


>_< anyone knows what this and why i get this error :confused:[/QUOTE]

I don't think it's linux specific problem as it appears also in windows.

Anyway does anybody had success playing warcraft 3 exp @ pvpgn server?

---

### Post by JeronimoGe on 2006-05-23
[QUOTE=hyapadi]I don't think it's linux specific problem as it appears also in windows.

Anyway does anybody had success playing warcraft 3 exp @ pvpgn server?[/QUOTE]

[QUOTE=MillDaKill]OK I just got this all working but now I can't get that font to install.  How do I install TrueType Font Arial ?


To anyone having any problems... Here are somethings I had to do to get it to work online.
1. download all of the wc3 updates from blizzards webpage and install them by hand.
2. find a cd crack that is for the most recent version or else you wont be able to go onto blizzards servers.[/QUOTE]


I've played on official servers and some non-official servers with my Warcraft III TFT game with all updates :)

---

### Post by hyapadi on 2006-05-23
[QUOTE=JeronimoGe]I've played on official servers and some non-official servers with my Warcraft III TFT game with all updates :)[/QUOTE]

Well then, I guess I get less and less reason to stay with my window box. I'm coming linux!! :>

---

### Post by Patrick-Ruff on 2006-05-26
best place I've found for No CD cracks is [www.gameburnworld.com](www.gameburnworld.com).   I intend to test this when dapper releases. 1st of next month. ATI cards are supposidly much more supported in dapper. so, I'll get back to you guys in a few weeks.


gl

---

### Post by Lord Illidan on 2006-06-04
Hi...
I've got a problem with Warcraft 3. Graphics work fine with the -opengl switch. Almost as fast as Windows, very playable.

However, sound is the problem. It works, but stutters a lot. How do I fix it?

---

### Post by Andenium on 2006-06-11
okok so im new with this ubuntu stuff so i need to know step by step how to do this any1 think u can help me plz!?!?

---

### Post by Andenium on 2006-06-11
i do  wine "Warcraft III.exe" -opengl
and it gives me an error it says it didnt find cdRom/DVDrom and then another error that says it cant find my warcraft cd what should i do help me plz i have been trying for the past 2 days

---

### Post by Iesos on 2006-06-12
I had the nocd - problem with other Blizzard games before. My problem was an old version of wine and/or an old kernel (said the guy at winehq). I just added 

> deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/


Into my /etc/apt/sources.list and installed wine (that is, removed all previous installed versions of wine. (try for example to delete the .wine folder (If you don't got anything important in it!!!))). 

That worked fine for me. At least with Starcraft and Diablo 2. Warcraft 3 on the other hand is not playable. I can start it up (without the -opengl flag), but one cant play (lags). So I tought, maybe I'll try this -opengl flag. Then I got this error:

> fixme:win:EnumDisplayDevicesW ((null),0,0x55ddef50,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x55ddef88,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  29 ()
  Serial number of failed request:  574
  Current serial number in output stream:  574

So, does anyone recognize this problem? And whats the solution?

---

### Post by etotehpii on 2006-09-15
Anybody getting the error "Unable to validate game version.  Please reconnect to Battle.net, or apply the current game patch manually."

I have the lastest patch and my game was running fine online 2 days ago.  I was using the nocd fix so I can play online and I heard that Blizzard did this to stop bots from spamming, which is understandable.  Anybody know where to find a new nocd fix?  Or better yet how about just running the game off the cd like you do it windows?  When I try to run it off the cd it doesn't like game.dll(It says it can't open it).  I looked on the war3 cd but I couldn't find this game.dll it speaks of.

Anybody else run into this problem and find a solution?

Thanks

---

### Post by clarke.rainey on 2006-10-08
> **Viorus said:**
> [IMG]http://i3.photobucket.com/albums/y73/Viorus/93298234.jpg[/IMG]


>_< anyone knows what this and why i get this error :confused:

I am also getting this exact same message... and spent the last two hours reinstalling and such to try and fix it...

---

### Post by hyapadi on 2006-10-09
Sometimes I get such kind of error in windows. I think it's the game, not the linux problem.

---

### Post by methane on 2006-10-18
So, I finally got WarCraft III working under wine last night.
It always installed easily, but I kept getting the "cannot find CD problem."
I'm not entirely sure which of the things I tried was what fixed it, but this was the final outcome:
I'd gone through the "howto setup wine" guide on this site, and upgraded to the latest version of wine via the links in that guide using the budgetdedicated archive.  That's when I started getting the CD error.  I tried uninstalling wine and using the universe repository version (never removing the ~/.wine directory through all of this) and that didn't work either.  Still CD error.  Long story short, I went flipped back and forth through a few different versions of wine, ending up with the universe repository version.  At this point, I decided to go to the Blizzard site and grab the patch to the latest version of WCIII.  I think this is what fixed the problem.  Two starts later and the game worked, no CD error.
I may check tonight to see if the patch is the key.

As for sound: my sound is stuttery when I used on-baord sound.  I've got an nVidia chipset based Athlon XP board, so it's not the fastest thing.  And I'm using on-board video and sound.  When I switched the sount to my soundblatster card, all the stuttering went away, but there is now a half-second delay before the sounds play.  e.g., order the hero to move, and about half a second later he says his phrase.  It should be instant.  This is also noticable in the dialogue sequences.  I'm trying to figure this one out, if anyone has any ideas....

The Memory access violation: I got this error once, after trying to connect on-line, switching to Single Player, and then attemping to start the Human Campaign.  I restarted the game, went directly to the Prologue Campaign, played that, and have since been playing the Human campaign.  I have seen the error again.  I tend to agree that this is probably a game fault.

Battle.net: I can connect, but the game seems stuck when it gets to "Downloadin data files."  I don't know if the is a problem with Bnet, my Internet connection, or wine.  If anyone knows anything about this, I'd love to hear it!  I frankly don't know what it would be trying to download.

Good luck!

---

### Post by holomorph on 2006-10-18
hmm, seems like 'downloading data files' might indicate you don't actually have the latst version, and it's trying to patch (but I could be wrong).  I'm not sure how well the patching through battlenet works w/ wine.

---

### Post by methane on 2006-10-18
Yeah, I thought that too, but I did just apply the latest patch last night from the file download.  I'm going to take my router out of the equation and see if that helps.  I don't think wine is having any trouble connecting, but I also need to double-check this.  I'll try IE when I get home and make sure it can grab pages.

---

### Post by methane on 2006-10-20
So, IE in my current installation is broken, all I get is a blank screen in the IE window, no buttons or anything.  So I can't verify that wine is correctly connecting to the internet.  As for the sound problem, it seems I'm not the only one who has it and I will be trying the solution in this thread:
[http://ubuntuforums.org/showthread.php?t=187666&highlight=sound+delay](http://ubuntuforums.org/showthread.php?t=187666&highlight=sound+delay)

---

### Post by Vexed Arcanist on 2006-11-10
> **holomorph said:**
> 

[*] Then you can start warcraft with:

wine "Warcraft III.exe" -opengl
[/list]

Hahaha...I actually found this thread while searching google with "How to uninstall Warcraft III ubuntu"

Over a year ago (back when this thread probably started, ney, even before) I had TFT/WCIII running in FC4 with no problem.  However recently I got back on the linux warwagon with Ubuntu 6.10 Edgy and installed the game and had one glitch, stuttering pile of...so I was about to remove it then I added this "-opengl" line to the desktop Icon launcher command and viola!  :KS

---

### Post by MeduZa on 2006-11-11
I'm using Warcraft 3 TFT from the windows installation, I just copied the folder to my wine "program files" and the game runs perfectly with all my configs, I used a lot of programs from windows installation without needing to install it first, I just copied and pasted.
Macromedia DW needs to be installed in order to work, other app too, but fist try to copy & paste ;) If that doesn't work or you still have problems try installing it.

Somebody know some kind of "Warcraft 3 Ban list" that work on linux?, the windows one uses a special driver that doesn't work on WINE and is really a useful program

PD: Warcraft 3 runs FASTER on WINE also has better grafics using OpenGL

ej:

---

### Post by LordFiodor on 2006-11-13
Hi all, I'm quite new to Ubuntu, but was using Mac OS X for years before. Thanks to a friend I Managed to get familiar with the System quite well.
Now i also want to play Warcraft, but it doesn't work.
In Detail, I was able to install it without any Problems (I followed a German HowTo at [www.holarse-linuxgaming.de](www.holarse-linuxgaming.de)), but when I try to run the game, I can see the 'Warcraft is being started' - Window showing the Orc. Then the Screen Resolution switches to 800x600 and the X-Server freezes, I can't even reset it using ctrl+alt+backspace.

if anyone could tell me how to write the output to file, i could post the error message, ```
wine warcraft.exe -opengl > warerror.txt
``` doesn't work, I get an empty file.

Here my Soft- and Hardware Specs:
Ubuntu 6.10
Wine 0.9.24 from synaptic

Pentium M 1.73 Ghz
Intel GMA 915

I'd be glad if anyone helped me.

---

### Post by pertheusual on 2006-11-22
So Strange. I get the same problem also. The resolution changes and  then locks. 

I have to reboot the get the system running again.


HELP!

:)

Thanks

---

### Post by LordFiodor on 2006-11-23
I now managed to run the Game via Cedega, RoC works, but if you want to play TFT the CD can't be found, with a Crack it works, but then you can't play online :-(

---

### Post by d2sbydt2 on 2006-11-25
i manage to run tft on wine 0.9.25 but for some reason...
1. game movies dont play
2. game occasionally freezes or crashes.
- when it crash, it shows an error screen then the program dies
- when it freeze, the game freezes.  if i check the status of the program using system monitor, it will say warcraft 3 is "Sleeping" under the status.  if i end the process, it will become a zombie, and i can not start warcraft again until after restart.  if i kill the process, then the program ends but i can start warcraft again without restart.

anyone know wats going on?

---

### Post by IMELucky on 2006-12-03
How do I get wine to detect the CD?
(It's mounted, and it installed from the cd. Still complains about not having the CD in the drive.)

---

### Post by LordFiodor on 2006-12-04
> **IMELucky said:**
> How do I get wine to detect the CD?
(It's mounted, and it installed from the cd. Still complains about not having the CD in the drive.)

Usually you only have to set the emulated Windows Version to a version above win 98. just type 
```
winecfg
```
into your terminal, then a window opens where you can find a tab called "applications" or so where you can set the version of windoze.

---

### Post by IMELucky on 2006-12-04
Thanks for the help, I actually found the solution myself yesterday.

Here it is
Set version about win98, (like posted above, I set mine to XP)
Go to drives, and change the CDROM from Automatic to CDROM

---

### Post by adriano on 2006-12-08
> **LordFiodor said:**
> 
if anyone could tell me how to write the output to file, i could post the error message, ```
wine warcraft.exe -opengl > warerror.txt
``` doesn't work, I get an empty file.

Here my Soft- and Hardware Specs:
Ubuntu 6.10
Wine 0.9.24 from synaptic

Pentium M 1.73 Ghz
Intel GMA 915

I'd be glad if anyone helped me.

I think (partly because I just installed it and ran into a similar problem) that you need to rename the Movies folder to something else, as said here:
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Warcraft3](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Warcraft3)
Everything else seems to work.

---

### Post by KoRnholio on 2006-12-26
A note to those who can't get Warcraft III working:

Upon starting it with OpenGL, I got these errors:
> fixme:cdrom:CDROM_DeviceIoControl Unsopported IOCTL 2d1400 (type=2d access=0 func=500 meth=0)
fixme:cursor:SetSystemCursor (0x111e,00007f8a),stub!
err:ole:CoCreateInstance apartment not initialised
fixme:win:EnumDisplayDevicesW ((null),0,0x34ef50,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16

The game would then freeze before starting up, requiring a reboot.

So I tried just using D3D.  It started correctly, but the framerate was too slow to be playable.  So I exited, started it in OpenGL, and it worked perfectly.

It might have something to do with the resolution (or other screen settings).  OpenGL initially froze right after changing the resolution.  D3D correctly changed the resolution, and so when OpenGL tried, it didn't crash.

It might mean that you have to 'fake run' it in D3D at each boot, I've only just gotten it working 10 minutes ago, so who knows.

---

### Post by Patrick-Ruff on 2006-12-26
first off, open GL sucks for "grafics". it looks many times worse then my windows comp. Cedega is the obviously better thing here (if none of you have heard of file sharing, I suggest you open your eyes.)

but it appears that nobody has figured out how to get TFT running well under Cedega.  I'm still trying to figure it out . . . .

anyways, Wine uses 100% of my CPU, so I'm not  bothering with that.

---

### Post by Patrick-Ruff on 2006-12-27
actually, nevermind. apparently someone has. you download the patch from blizzard's website, then you patch your installation, then you get a nocd crack, and viola.  

however, one thing still bothers me, why must we use opengl when Cedega has Direct3D implemented into it?

opengl looks like crap, and I'd rather not use it.

---

### Post by wc_pwn on 2007-01-01
I dunno if anybody is still reading this thread but.... I have the same problems with warcraft 3, its not getting read by my cd drive, and I've looked at no-cd files and stuff. I more of a noob when it comes to this stuff and i was wondering how i use my no-cd files to help read my disk, and any other suggestions would be appreciated.:)

---

### Post by janfsd on 2007-01-08
Thanks for the guide, it works for me. I have a question, is there a way of mapping the alt key within Warcraft? Always when I try to display the health bars, it is like the alt key gets stuck and all the keys I press behave like ALT + key combination, any possible solutions?

---

### Post by murlosad on 2007-01-12
> **wc_pwn said:**
> I dunno if anybody is still reading this thread but.... I have the same problems with warcraft 3, its not getting read by my cd drive, and I've looked at no-cd files and stuff. I more of a noob when it comes to this stuff and i was wondering how i use my no-cd files to help read my disk, and any other suggestions would be appreciated.:)

the idea behind the no-cd files is to make it unnecessary to use the disk.

what no-cd files are you using and what version of Warcraft 3 or The Frozen Throne are you running?

-edited something didn't work right when I tried it again, will keep working on it and post if I get it working.

---

### Post by tbay007 on 2007-01-13
I know this is a dumb question.  But with Wine and Warcraft 3 combo, can you play it online with a valid key?  Becuase i have the game bought and everythign, but the actual game is boring and i like playing warcraft 3 on battle.net in windows, in Linux can you do the same thing i mean?  Play it over battle.net?

---

### Post by murlosad on 2007-01-13
> **tbay007 said:**
> I know this is a dumb question.  But with Wine and Warcraft 3 combo, can you play it online with a valid key?  Becuase i have the game bought and everythign, but the actual game is boring and i like playing warcraft 3 on battle.net in windows, in Linux can you do the same thing i mean?  Play it over battle.net?
I've never had a problem playing war3 on battlenet under linux.  even a couple of years ago I played online using cedega and played last night using wine and the Frozen Throne

---

### Post by Pikestaff on 2007-02-27
Okay guys, I've installed WarCraft III and Frozen Throne with Wine, but it seems to hang when I try to start it up, even with -opengl... I get this in the terminal:

```
fixme:cdrom:CDROM_DeviceIoControl Unsupported IOCTL 2d1400 (type=2d access=0 func=500 meth=0)
fixme:cursor:SetSystemCursor (0x111e,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x1126,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1136,00007f03),stub!
fixme:cursor:SetSystemCursor (0x113e,00007f01),stub!
fixme:cursor:SetSystemCursor (0x114e,00007f88),stub!
fixme:cursor:SetSystemCursor (0x115e,00007f86),stub!
fixme:cursor:SetSystemCursor (0x116e,00007f83),stub!
fixme:cursor:SetSystemCursor (0x117e,00007f85),stub!
fixme:cursor:SetSystemCursor (0x118e,00007f82),stub!
fixme:cursor:SetSystemCursor (0x119e,00007f84),stub!
fixme:cursor:SetSystemCursor (0x11ae,00007f04),stub!
fixme:cursor:SetSystemCursor (0x11be,00007f02),stub!
pikestaff@pintsize:~/.wine/drive_c/WarcraftIII$ wine frozenthrone.exe -opengl
fixme:cdrom:CDROM_DeviceIoControl Unsupported IOCTL 2d1400 (type=2d access=0 func=500 meth=0)
fixme:cursor:SetSystemCursor (0x111e,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x1126,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1136,00007f03),stub!
fixme:cursor:SetSystemCursor (0x113e,00007f01),stub!
fixme:cursor:SetSystemCursor (0x114e,00007f88),stub!
fixme:cursor:SetSystemCursor (0x115e,00007f86),stub!
fixme:cursor:SetSystemCursor (0x116e,00007f83),stub!
fixme:cursor:SetSystemCursor (0x117e,00007f85),stub!
fixme:cursor:SetSystemCursor (0x118e,00007f82),stub!
fixme:cursor:SetSystemCursor (0x119e,00007f84),stub!
fixme:cursor:SetSystemCursor (0x11ae,00007f04),stub!
fixme:cursor:SetSystemCursor (0x11be,00007f02),stub!
```

And then a message pops up telling me to check and make sure the CD is in the drive, even though it is!

This is the second game I've installed with Wine, the first (StarCraft) works fine, it's just this one that has the problem.  Any help would be greatly appreciated, I miss my DotA :(

---

### Post by murlosad on 2007-02-27
run 'winecfg' in a terminal and check to make sure the cdrom is actually pointing at the correct place (i.e. /media/cdrom0).  Other than that, if you have another cdrom drive try installing from that and see if it makes a difference.  good luck

---

### Post by Pikestaff on 2007-02-27
> **murlosad said:**
> run 'winecfg' in a terminal and check to make sure the cdrom is actually pointing at the correct place (i.e. /media/cdrom0).  Other than that, if you have another cdrom drive try installing from that and see if it makes a difference.  good luck

Awesome, that got it working, thank you!!  It seems to work perfectly except some of the maps don't work, for example the dota AI map isn't giving me the options to choose teams and stuff so I can't figure out how to play it :-s but at least it starts now!

---

### Post by alexf22 on 2007-03-31
> **holomorph said:**
> Hi, 
I was considering getting a Cedega subscription, since they claim that Warcraft III works well, and then was reading around on the net and saw it mentioned that it actually works under wine just as well.  So I thought I'd give it a shot first; it worked well for me, so I thought I'd share my procedure with other Ubuntu users.  Here's what to do:
[list=1]
[*] Add the wine repository to your sources list:
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
either via Synaptic or just add the line to /etc/apt/sources.list

[*]Refresh your package list:
sudo apt-get update (or click update in Synaptic)

[*] Install winetools (this will install wine also):
sudo apt-get install winetools
or in synaptic search for winetools and install

[*] In a terminal, run 'winetools', it should give you a message about wine not having been configured yet, if it doesn't then you probably have a .wine/ directory in your home folder and you might want to delete that to make sure you're starting from scratch here.
Click QK until you get to the "WineTools" screen.  Select the Base setup and press ok.  From the Base Setup, Create a fake windows drive; make sure to select the correct mount point for your cdrom drive (probably /media/cdrom0). Next install TrueType Font Arial. Finally, install DCOM98.

[*] Exit winetools and open the wine config file that was created in a text editor (eg nano .wine/config).  Look 
for '[Version]' and under that where it says:
"Windows" = "win98"
change it to:
"Windows" = "winxp"
then save the file and exit.

[*] Now it is time to install Warcraft. Put your cd in the drive and type:
wine /media/cdrom0/install.exe
(asssuming that's where your cdrom is mounted)
install as you usually would (I changed the path to C:\Games\Warcraft III, but that's just a personal preference). Exit the installer when you are finished.

[*] Unfortunately wine will not play the movies (though apparently you can watch them in xine or something) so it's best to move them so the game can not find them:
cd .wine/fake_windows/Games/Warcraft\ III/
mv Movies/ Moviez/

[*] Then you can start warcraft with:

wine "Warcraft III.exe" -opengl
[/list]
Note: after upgrading to 1.18 warcraft would not run until I turn on '"HardwareAcceleration" = "Emulation"'	in the [dsound] section of my wine config file; there was an error and message telling me to do so in my terminal when it failed to run.

Let me know if any of this is unclear, I hope it helps.

Bjorn






I am the biggest ubuntu newbie...can you explain all of this in simpler terms please...

thanks

---

### Post by murlosad on 2007-03-31
are you just trying to install wine and Warcraft III? What version of Ubuntu are you using? and can you post your /etc/apt/sources.list file?

press alt+f2 and type this:

gedit /etc/apt/sources.list

---

### Post by alexf22 on 2007-03-31
I already have wine installed and updated...
I am using version 6.10....




deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy restricted main universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates restricted main universe #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted main universe #Added by software-properties
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by murlosad on 2007-03-31
great, if you've already got wine, you are about half way there.  the reason I asked for the sources.list file was to make sure you had the proper repo's to install wine.  Anyhow, you can install warcraft III in a few simple steps.

Quick note - you do have your 3d drivers up and running right?

1. Insert CD :)

2. open terminal (applications >> accessories >> terminal

3. navigate to your cdrom directory (probably /media/cdrom0)
     > cd /media/cdrom0

4. run install program with wine.
     > wine install.exe

this should start the installer, and ask for your cd key... yada yada yada.

basically that is about it.  The other stuff isn't normally necessary.

wine will probably put an icon on your desktop. right click and select properties, go to the launcher tab, at the end of the text in the 'command' box add
      > -opengl

this should enable you to launch warcraft III using opengl by just clicking on the icon on your desktop.

---

### Post by alexf22 on 2007-03-31
okay i got everything done but when I start the game my comp freezes up and my resolution gets messed up and I have to turn off the computer...I think it might be the 3d drivers...what do I do?

thanks again

---

### Post by murlosad on 2007-03-31
what type of video card do you have?

try searching for something like 'nvidia drivers' or 'ati drivers' depending on what you have.

I've used both with good success.

another program you can try is called 'envy' it will download and install your driver for either nvidia or ati.

[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu4_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu4_all.deb)

Not sure about intel, but there is plenty of help for that around here.

Also, make sure you are using the '-opengl' at the end of the wine command - very important

---

### Post by alexf22 on 2007-03-31
do you have an aim account or something that we can talk because I have soooo many questions and I am very confused...all my life I have been pampered with windows machines, but the ignorance, greed and lack of quality stemming from Microsoft has left me in a tantrum so thats why I switched to Ubuntu.

Thanks again and don't be afraid to decline I take no offense...

---

### Post by murlosad on 2007-04-01
> **alexf22 said:**
> do you have an aim account or something that we can talk because I have soooo many questions and I am very confused...all my life I have been pampered with windows machines, but the ignorance, greed and lack of quality stemming from Microsoft has left me in a tantrum so thats why I switched to Ubuntu.

Thanks again and don't be afraid to decline I take no offense...

sorry, I don't use aim or really any im, feel free to private message me anytime (just click on my name and select private message)  but any help you need can probably be found here or on the irc channel (I don't use that either).  There are tons of people around here to answer questions and don't forget the search function :)

---

### Post by berylator on 2007-04-01
Hello, great to be here.

I experience another problem: winetools does not create any config file in my /.wine folder. Therefore, I cannot change my Version to WinXP. Is the name of the config file really "config"?

thanks

berylator

---

### Post by murlosad on 2007-04-01
you can run 'winecfg' from alt+f2 and change the version there.

---

### Post by berylator on 2007-04-01
thanks, this totally works. I installed it now, and everything seemed to work well until I actually tried to run wc3. I ran it with the -opengl option. After displaying the WC3 splash screen, however, an error message popped up saying I didn't install directx. After clicking ok, another error message appeared, saying there was no cd in the drive :(

---

### Post by murlosad on 2007-04-02
I've never gotten the directx error but you can probably solve the no cd issue but running winecfg again and clicking in 'Drives' and making sure that your cdrom is referenced properly (normally just clicking on Autodetect works for me).

oh yeah, make sure your wine is up-to-date

> sudo apt-get upgrade wine

---

### Post by nehalem on 2007-04-09
Well I'm trying it on feisty. 

Everything installed well but I get the cd rom error.  Looking in winecfg it looks like everything is setup fine with the D: referencing /media/cdrom0 corrently and set to cdrom type.

I don't know what it is but I can never get wine to work, it's very frustrating.

Anything I might be missing?  I know I'm using beta software but feisty is very stable.

---

### Post by holomorph on 2007-04-09
I just upgraded to feisty, so I'll try when I get home.  I used to always get the 'please insert cd' thing, but recently re-installed wine and everything and discovered that little selector in winecfg which allows you to configure the type for each drive; selecting cdrom worked like a charm.

This was using the latest wine .deb package from winehq.com, not from the ubuntu repos (though I don't know if it matters).

---

### Post by holomorph on 2007-04-10
Ok, I got home and gave it a shot under Feisty. . . got a 'no cd error'.  

looked around a bit and discovered when I popped my disk in, Feisty mounted it as '/media/Warcraft III', so I ran winecfg and added that as another cdrom drive (which for me was drive F: and make sure the type is set to CD-ROM).  Then tried again and it worked.

Hope that helps.

---

### Post by the_axiom on 2007-05-03
Hi, I've installed wc3 via wine. And I experience though lagg. I am sure it's not my hardware (2gb pc6400, c2d e6300, ati x1950xt).
Anyone knows how to fix?

---

### Post by holomorph on 2007-05-03
> **the_axiom said:**
> Hi, I've installed wc3 via wine. And I experience though lagg. I am sure it's not my hardware (2gb pc6400, c2d e6300, ati x1950xt).
Anyone knows how to fix?

are you sure you're running it with the -opengl option?  If not, it will try to use directX, which could be slowing things down.

---

### Post by murlosad on 2007-05-04
> **holomorph said:**
> are you sure you're running it with the -opengl option?  If not, it will try to use directX, which could be slowing things down.

Also make sure your 3d acceleration is working. With an ATI card you need to have the fglrx driver installed properly.

---

### Post by mnk0 on 2007-05-29
how do u snap the mouse to the window if u run in -window , and also in a dual monitor setup. the bottom doesnt scroll all the way down for me, did anyone else encounter this?? and what is the solution


--
Omar Samad

---

### Post by watskeburten on 2007-06-03
uncheck 'Allow the window manager to manage created windows' in the winecfg > Grafics tab and check 'Allow DirectX apps to stop the mouse from leaving their window'

---

### Post by nerdman978 on 2007-06-06
I cannot find winetools anywhere. It seems like it doesn't exist! All repos are enabled too!

---

### Post by Nego on 2007-06-06
> **nerdman978 said:**
> I cannot find winetools anywhere. It seems like it doesn't exist! All repos are enabled too!

```
wget http://download.formationos.net/winetools/winetools-0.9.4.tar.gz
tar -xf winetools* 
cd winetools* 
sudo ./install
```

Open it with wt

---

### Post by LyokoHaCK on 2007-06-09
I type 
```

swade@Swade-Ubuntu:~$ wine .wine/drive_c/program\ files/Warcraft\ III/Frozen\ throne.exe -opengl

```
The Warcraft III image pops up i hear it reading my CD drive, my screen blinks twice attempting to open WC and opens a dialog saying:

```

**Warcraft III**
Warcraft III was unable to initialize OpenGL.Please ensure you have OpenGL installed and that your display drivers are current.

```

I have an nVIdia XFX 7600GT.

---

### Post by LyokoHaCK on 2007-06-10
> **Nego said:**
> THANK YOU!!!!!!! Finally it is up and running! Running it from my wine directory did the trick! Why is that though?
```

swade@Swade-Ubuntu:~$ wine .wine/drive_c/program\ files/warcraft\ III/frozen\ throne.exe -opengl
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:cdrom:CDROM_DeviceIoControl Unsupported IOCTL 2d1400 (type=2d access=0 func=500 meth=0)
fixme:cursor:SetSystemCursor (0x112e,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x1136,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1146,00007f03),stub!
fixme:cursor:SetSystemCursor (0x114e,00007f01),stub!
fixme:cursor:SetSystemCursor (0x115e,00007f88),stub!
fixme:cursor:SetSystemCursor (0x116e,00007f86),stub!
fixme:cursor:SetSystemCursor (0x117e,00007f83),stub!
fixme:cursor:SetSystemCursor (0x118e,00007f85),stub!
fixme:cursor:SetSystemCursor (0x119e,00007f82),stub!
fixme:cursor:SetSystemCursor (0x11ae,00007f84),stub!
fixme:cursor:SetSystemCursor (0x11be,00007f04),stub!
fixme:cursor:SetSystemCursor (0x11ce,00007f02),stub!
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb8ed50,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb8ed80,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16err:opengl:X11DRV_ChoosePixelFormat glXChooseFBConfig returns NULL (glError: 0)
fixme:imm:ImmAssociateContextEx ((nil), (nil), 16): stub

```

:( No luck. I get an error concerning OpenGL.

---

### Post by skjafar on 2007-06-22
i have been working for 4 hours now trying to run WC III on my system,
in the end i managed to do that, anyway when i start my game using opengl or wothout it does not make any difference, and its extremely slow,

meaning:

wine war3.exe
wine war3.exe -opengl

give me the same problem ( a very slow game)

i a have ATI X1300 and i got the driver using ENVY.

can anybody help

---

### Post by pascalosti on 2007-06-23
total nub is going to try this instal... hope this works

---

### Post by pascalosti on 2007-06-23
Im trying to get winetools to work once i get to.

wt
I get this error
(I have libgtk-2.0 , im  guessing i have an older version of wintools
Do i have to uninstall wintools or can i just install it.)

no suitable Wine directory found...
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Wine 0
wine is executed as wine
Parameters are --noexit
Wine is not configured yet!
Browser is /usr/bin/firefox.
WINEVER is "0".
Calls to wine are executed as "wine".
Config is /home/cc/.wine/winetools.log.
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
/usr/local/winetools/Xdialog: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by Enverex on 2007-06-24
Winetools is old, depreciated and broken, don't use it.

---

### Post by pascalosti on 2007-06-30
When i run Warcraft through the applications\wine 
it starts up but its really slow and choppy.  It ran fine when i had XP installed.
when I run this command

cc@cc-laptop:~$ wine "Warcraft III.exe" -opengl
wine: could not load L"c:\\windows\\system32\\Warcraft III.exe"
: Module not found


Since im not using the "opengl" flag how can i get around that?


I found this for WoW but the "SET" command isnt recognized
[http://www.linuxforums.org/forum/wine/62932-howto-installing-world-warcraft-wine.html](http://www.linuxforums.org/forum/wine/62932-howto-installing-world-warcraft-wine.html)
Once you have installed WoW, the /World of Warcraft/wtf/Config.wtf file needs to be modified. Add the following lines:
Code:

SET gxApi "opengl" 
SET SoundOutputSystem "1" 
SET SoundBufferSize "100"
 SET gxColorBits "24" 
SET gxDepthBits "24"





Never mind the stuff below, my previous problem
//////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

I think the install went fine, now the cd shows "Play Game" rather then "Install game"
(in applications under wine "warcraft 3 does appear with its submenus)
I did try pressing "play Game" which gave me some blinking black screens.
I installed it inside "c:\\program files\\".

when I run this command i get this error


cc@cc-laptop:~$ wine "Warcraft III.exe" -opengl
wine: could not load L"c:\\windows\\system32\\Warcraft III.exe"
: Module not found

How can i delete or uninstall it to retry from start.  Or is there a step i missed.
("uninstaller" does not show any applications)


I used 
wine /media/cdrom0/autoplay.exe
not sure if " install.exe" makes a difference

---

### Post by pascalosti on 2007-07-01
got it working looking deep into this forum topic


wine will probably put an icon on your desktop. right click and select properties, go to the launcher tab, at the end of the text in the 'command' box add
Quote:
-opengl
this should enable you to launch warcraft III using opengl by just clicking on the icon on your desktop.

---

### Post by Enverex on 2007-07-01
> **pascalosti said:**
> When i run Warcraft through the applications\wine 
it starts up but its really slow and choppy.  It ran fine when i had XP installed.
when I run this command

cc@cc-laptop:~$ wine "Warcraft III.exe" -opengl
wine: could not load L"c:\\windows\\system32\\Warcraft III.exe"
: Module not found

That wont work unless you're in the same folder as the EXE itself.

---

### Post by Cigue on 2007-07-14
If I shouldn't use Winetools, then what should I use? Winecfg?

also, when I open Warcraft, I click on the icon on my desktop (properly modded with -opengl in launcher) and my session reboots! what should I do please?

---

### Post by uph0ria on 2007-07-23
Everything is working fine except for this... "unable to validate game version....". Anyone know a fix?

---

### Post by Pioneer5000 on 2007-07-24
If you are using 7.04 i dont think you need to do anything on that list just do this

Type this into terminal:
sudo apt-get install wine

then insert disc (wc3) and then explore go to double click auto run and then just install from there like normal. I managed to getting working with just that. Hope it works for you too.

---

### Post by BOBSONATOR on 2007-07-24
Vi sitter här i venten och spelar lite DotA.!

---

### Post by chaos2286 on 2007-08-04
Hey guys, 

I don't know if this forum gets looked at anymore due to how old the game is, but I'm still struggling with this.  I've installed the game on both wine and cedega, and I get the same result.  I can navigate around in the menus as well as on battle.net.  But about 20 seconds after I actually start a game my monitor shuts off and it just lists the hzs and gives me a status.  I installed my ATI driver with envy and it seemed to go smoothly.  If anyone has had this problem/has any idea how to fix it I'd be thankfulll.  

ps using fiesty fawn 

- chaos

---

### Post by zorkerz on 2007-08-22
Hi all. Warcraft plays beautifully however it freezes during lan play with a windows computer. The freezes require a hard boot so I have not been able to observe any errors in the terminal. I can often get a ways into the game before the freez like 2nd or 3rd hero.

Im running gutsy gibbion with wine 0.9.43.
any ideas.

---

### Post by holomorph on 2007-08-22
Have you tried running it in a window so that you can see the terminal you launched it from?  

Also, what window manager are you using?  I've had a few freezes which are the fault of the window manager locking up (not during warcraft); but then I can usually still move the mouse, just tha clicks and keyboard inputs don't do anything. If it's a hard freeze where the mouse doesn't move anymore either, that's usually a kernel panic I think; not sure what would be causing that, but if it only happens during net play, perhaps it is related to your network card?

good luck

---

### Post by MillDaKill on 2007-08-22
My Setup:
*Xumbuntu 7.04 i386
*wine 0.9.43
*nvidia 7600gs agp
*nvidia binary driver updated on 8-20-2007 via envy
*dual monitor setup


My Problem:
When I try to play warcraft3 my mouse will NOT get locked into the warcraft screen.  My 2nd monitor is set up to the right of my primary screen so when I try to move the mouse over towards the right edge of the game screen it will spill onto the 2nd monitor and make the game pretty much unplayable.

What I have tried:
*setting wine to not use the linux windows manager
*setting wine to grab the DX game screen
*running in a virtual window which I could not get the mouse to lock in on any edge.

What works, but I dont like:
Disabling the 2nd monitor in my xorg.conf file.

If anyone can offer some suggestions I would surely appreciate it.

---

### Post by holomorph on 2007-08-22
if you aren't opposed to losing your second monitor just while you play, you can configure X w/ a few different modes, and then just switch resolutions so it only uses one monitor while you play, and switch back when you are done (without having to restart x and edit the config file every time).

I know you can do this if you're using twinview at least, not sure if you've got some other dual setup.

---

### Post by MillDaKill on 2007-08-22
> **holomorph said:**
> if you aren't opposed to losing your second monitor just while you play, you can configure X w/ a few different modes, and then just switch resolutions so it only uses one monitor while you play, and switch back when you are done (without having to restart x and edit the config file every time).

I know you can do this if you're using twinview at least, not sure if you've got some other dual setup.

I have it set up as 2 different X sessions, if there was an easy way to do that switch that would be great.

---

### Post by zorkerz on 2007-08-22
> **holomorph said:**
> Have you tried running it in a window so that you can see the terminal you launched it from?  
Also, what window manager are you using?

I will try to run it windowed. Im not sure how to at the moment if any one has any advice it would be appreciated. Im not sure i can play warcraft with a small enough resolution to make much diff. My laptops max is 1024x768 and i think warcraft min is 640x480. We shall see.

Im using gnome is that the window manager itself or what window manager does gnome use by default.

I suppose I should say im running gutsy gibbon on a thinkpad x61 with an intel x3100 integrated card (gm965 chipset).
thanks

---

### Post by alanpotpot on 2007-08-24
Its working fine on me except that ctrl is not working. I cannot assign a number on my units :(

---

### Post by Venerence on 2007-08-31
Note that I was getting *both* the no CD error and direct-x error. I fixed it by loading into a session that is *not* XGL. This means no fancy desktop effects for playing warcraft III, however it works nearly perfectly now.

In short, warcraft III will not work in wine if you're running XGL for compiz or beryl or whatever. Log into the base gnome session first and try it.

---

### Post by zorkerz on 2007-08-31
I don't know anything about XGL. My experience is that with desktop effects enabled warcraft iii has problems. This however has gone away in the last few days in gutsy. Though as a side note totem and some other programs do not work still with the special effects.

---

### Post by holomorph on 2007-09-03
> **MillDaKill said:**
> I have it set up as 2 different X sessions, if there was an easy way to do that switch that would be great.

I do it with nvidia's twinview; donno what would be equivalent in your situation, but here's the relevant part of my xorg.conf just in case it helps:

```

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 1400x1050 +0+0, DFP: nvidia-auto-select +1400+0; CRT: 1280x1024 +0+0, DFP: NULL; CRT: 1024x768 +0+0, DFP: NULL"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    Option "AddARGBGLXVisuals" "True"
EndSection

```

the "TwinView" and "metamodes" are the important parts.

---

### Post by scottevan on 2007-09-04
Hi all - I am running Warcraft III under Wine 0.9.44 in Windows XP mode and I can't get my keyboard to work. It is a USB 2 model by Microsoft and it has no trouble communicating with Ubuntu (pressing ALT-TAB works fine) but doesn't seem to be talking to Warcraft. I've tried turning off Beryl but the problem remains.

Got any ideas?

Not sure if this relates, but when I run Warcraft with WINEDEBUG, I get the following:
```
err:ole:CoCreateInstance apartment not initialised
fixme:win:EnumDisplayDevicesW ((null),0,0x34f220,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f46c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f4a4,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
scott@scott-desktop:~$ fixme:ntdll:NtCreateIoCompletion (0x34f7dc, 1f0003, (nil), 0)
fixme:imm:ImmGetOpenStatus (0x125708): semi-stub
fixme:imm:ImmReleaseContext (0x80460, 0x125708): stub
fixme:imm:ImmGetOpenStatus (0x125708): semi-stub
fixme:imm:ImmReleaseContext (0x80460, 0x125708): stub
fixme:imm:ImmGetOpenStatus (0x125708): semi-stub
fixme:imm:ImmReleaseContext (0x80460, 0x125708): stub

```
Thanks!

---

### Post by vexorian on 2007-09-04
have you tried any other WINE app? Does it work with your keyboard? might be a mainstream Wine issue (OR a problem with the keyboard driver with opengl apps... , do games like super tux work?)

I get the same messages when I run war3 in my computer so I am guessing those are unrelated to your issue

---

### Post by scottevan on 2007-09-04
> **vexorian said:**
> have you tried any other WINE app? Does it work with your keyboard? might be a mainstream Wine issue (OR a problem with the keyboard driver with opengl apps... , do games like super tux work?)
Thanks for the excellent suggestions! WINE runs fine typically and I have no problem with SuperTux. However, while testing that, I discovered a solution... the keyboard works fine if I configure WINE to "Allow the window manager to control the windows." Weird! I guess I should submit this bug to the WINE developers.

---

### Post by linuksamiko on 2007-10-01
My Warcraft feezes too on LAN-Games (described one page earlier by zorkerz's Avatar  	
zorkerz). Does anybody know how to fix this problem.

My system:
- Feisty
- Wine in different versions (currently 0.9.44)
- Intel Grafik

When I start a Battlenet game it freezes somewhere during loading-process when a game starts.

It is most likely NOT OpenGL sinc offline games work like a charm and the freez also happens with D3D.
I can play the campaign and custm games against the computer without any problems. Only Battlenet crashes.

Pleas, anybody got an idea?

---

### Post by fusionisthefuture on 2007-10-28
hi guys, i just installed wine, and i have a dual boot laptop.  i can run WCIII: TFT fine from just clicking on the exe in the windows partition, and having wine run it.  it runs with sound, and with all the settings on full, but what im wondering is how do i connect to bnet?  it supposedly works with these versions, and gutsy, and right now ive got my iptables all opened up, and it never connects.

any ideas?

thanks in advance
-arne

---

### Post by balgaltz on 2007-10-28
Hi, i had the same problem before, there's a bug with the battle net connection with wine version 0.9.46 and 0.9.47, not sure about 0.9.48.
But you can use the version 0.9.45 to connect to battle.net, However, theres a patch for wine on version 0.9.47 (the one i use to play on battle net right now). 

You must patch wine 0.9.47 from source.
Patch: [http://bugs.winehq.org/attachment.cgi?id=8368]("http://bugs.winehq.org/attachment.cgi?id=8368")
(save the patch in diff extension)

Code for patching: ```
patch -p0 <./filename.diff
```
It might ask you: **Patch file :** or **Files to patch :** then you have to locate the file _**wine-0.9.47/dlls/kernel32/sync.c**_ in the source folder.

After Patching you have to compile and install wine.
You need libraries or you will get error when compiling.
Needed libraries: [http://ubuntuforums.org/showthread.php?t=29996](http://ubuntuforums.org/showthread.php?t=29996)

In case you don't know how to compile
```
cd wine-0.9.47/
./configure
make depend && make
make install
```

**Not sure if it was "make depend" or "make depends"**, it tells you after ```
./configure
```

There are nocd + battlenet scripts. (Wrote one based on others). The only problem is that when chatting in a game, the **text fonts are ugly**, still looking for a patch for that, actually found one, but it doesn't work. Here: [http://osdir.com/ml/emulators.wine.patches/2003-07/msg00005.html](http://osdir.com/ml/emulators.wine.patches/2003-07/msg00005.html)

Hope this worked for you, as it did for me. Took me some time to learn. Good luck, happy gaming.

---

### Post by PsyWolf on 2007-10-28
I just tried to install the new ATI fglrx driver and with it installed Warcraft III kept freezing.  I reverted back to the driver from the repositories, and it doesn't freeze anymore, but i would like to use the never drivers so if anyone knows how to fix the problem, that would be awesome.

---

### Post by budde on 2007-10-29
balgaltz, i love you!

finally got WC3 to work with battle.net... the only problem is that my ALSA-driver in wine dissappeared.. does anyone know how I can get it back?

thanks again balgatz, you made my day/week/month

EDIT:
recompiled with all the dependencies for wine, like 250mb's unpacked => ALSA still didn't work. "screw ALSA" i thought, and went with OSS instead. works like a charm - played my first ladder game.

---

### Post by jav_ on 2007-11-05
how do i go about disabling alt-right click menu while playing warcraft? im a dota player so i spam alt a lot to see the health bar..so that bar that pops up pisses me off..
t.i.a.

---

### Post by interactivebiostud on 2007-11-12
I install RoC fine but whenever I try to install TFT or ANY expansion for Blizzard games, the install freezes.   I have wine version 0.9.45, it runs as WIndows XP and the cd drive is set as E:.  It freezes when it starts installing the War3xlocal.mpq. I can't even cancel the installation.

Any clue on how to fix this?

Edit: I've also tried it on the latest version of Wine and I still get the same problems.

---

### Post by arik100 on 2007-11-16
hello 
i have just installed ubuntu 7.1 and the latest version of wine 
installation went fine but when i activate the game the movies indeed doesn't work as he said but one more problems occures 
i have no sounds!!
i didn't patch the game yet , anyone has any solution to this problem???

---

### Post by hotweiss on 2007-11-25
> **arik100 said:**
> hello 
i have just installed ubuntu 7.1 and the latest version of wine 
installation went fine but when i activate the game the movies indeed doesn't work as he said but one more problems occures 
i have no sounds!!
i didn't patch the game yet , anyone has any solution to this problem???

The problem seems to be related to DCOM98. As soon as I installed DCOM98 I lost my sound. I fixed it by going into the audio tab in config. For some reason that works.

---

### Post by holomorph on 2007-11-25
I had sound trouble at one point as well, but mine had to do with my having two sound cards.  I had other things playing out my soundblaster, but wine was trying to use my onboard soundcard.  I think I fixed it by making sure my soundblaster got index 0 (configured in /etc/modprobe.d/alsa-base).

---

### Post by Ertai87 on 2007-12-28
OK, so I asked this question in my own thread elsewhere, but nobody's answered it for about a week, so I figured I'd have better luck here.  I installed Wine and set up WC3 before installing the fonts pack.  I've since installed the fonts pack (but not DCOM98 because I don't know what that is), but I still have the choppy hard-to-read Wine default font in my WC3.  How do I fix this?

---

### Post by somethingsin on 2007-12-30
Hey,

My problem:
W3:RoC installed under wine. 
I can get the game to start, but when I try to load a map, it gets stuck somewhere around 3/4 of the loadingbar.

Any help would ofcourse be greatly appreciated!

---

### Post by Ber P on 2007-12-30
I've just installed wc3 yesterday and it runs like a charm. But when trying to enter "human campaign" - it crashes!
I saw sombody describing this problem earlier in this thread, but found no answers.
Is it a known bug? Any workarounds?

I'm using Wine 0.9.51

---

### Post by Ertai87 on 2007-12-30
@Ber P: There's a problem with loading movies in Wine.  Rename or delete the folder containing the movies.  It should work then.  There should be better instructions somewhere on the forums (probably on the front page of this thread).

---

### Post by Ber P on 2007-12-31
> **Ertai87 said:**
> @Ber P: There's a problem with loading movies in Wine.  Rename or delete the folder containing the movies.  It should work then.  There should be better instructions somewhere on the forums (probably on the front page of this thread). 

Ertai87 - Thanks a lot! That did it.

---

### Post by spitfire23bc on 2008-01-06
> **somethingsin said:**
> Hey,

My problem:
W3:RoC installed under wine. 
I can get the game to start, but when I try to load a map, it gets stuck somewhere around 3/4 of the loadingbar.

Any help would ofcourse be greatly appreciated!


I'm having the same problem; any fixes?

---

### Post by vradovic on 2008-01-06
I install WC3 and FT over Wine and now (after update on latest version) everything works. 

I download map dota from [www.getdota.com](www.getdota.com) and i play that over BNET. 

I start game with wine Frozen\ Throne.exe -opengl but it is too slow...it is not like on Windows XP. 

Is there any solution for this. 

ALso when i press ALT + Right mouse click i just got some menu....that sometimes can be problem.

---

### Post by Ertai87 on 2008-01-07
Which Wine are you using?  I found Wine 0.9.45 was ridiculously slow and choppy.  Grab Wine 0.9.52 off the Wine repos by adding the following lines to your sources.list, located in /etc/apt:

#Wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main

Then run an update and upgrade and it should be faster.  If that doesn't work, I dunno.

---

### Post by vradovic on 2008-01-08
wine 0.9.52

everithing works just fine but it is too slow...

i have 
- 3 GHz 
- 1.5 gb RAM
orginal wc3 + FT
grafic card NVDIA 6800 with 128 Mb 
I installed latest grafic driver.

what can i do?

to buy better computer? some dual processor or what?

---

### Post by Ertai87 on 2008-01-08
Nope, your hardware's not a problem (assuming it works properly and you have the right drivers and stuff)...your comp has better specs than mine and mine runs fine.  What graphics settings are you running on?  Perhaps you're trying to put too many resources into WC.  I know I can't play it on max graphics cause it'll lag like heck, so I play it on roughly 1/2 power.

---

### Post by jwalcker on 2008-01-09
well i tried following you're first step and add the url to my sources.list and the updated using the sudo apt-get update and treid to install wine and got

```
justin@justin-ubuntu:~$ sudo apt-get install winetools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package winetools
justin@justin-ubuntu:~$ 

```

as you can tell I'm a bit of a newb, been using Ubuntu Gusty for about a month now but I think I'm learning fast.

---

### Post by Ertai87 on 2008-01-10
Just try installing wine, not winetools.  Or if you have Wine already, just try doing an apt-get update/upgrade.  It should grab the new one automatically.

---

### Post by vradovic on 2008-01-13
any idea ???

---

### Post by vradovic on 2008-01-17
> **Ertai87 said:**
> Nope, your hardware's not a problem (assuming it works properly and you have the right drivers and stuff)...your comp has better specs than mine and mine runs fine.  What graphics settings are you running on?  Perhaps you're trying to put too many resources into WC.  I know I can't play it on max graphics cause it'll lag like heck, so I play it on roughly 1/2 power.

ups sorry i didn't see your post :)

look i try to put resolution on very low 800x600 16 bit.  (in WC3) 

look i think i am very very pro Dota player and mebie to you that (a little bit slower then ususal) itc not a "big deal" but for me that is terrible...

I don't have idea what to do. 
For me it is not problem to buy better hardware but i don't think that is problem. 
I just like ubuntu because i can surf anywhere :)

Can you please tell me what to do?

---

### Post by Ertai87 on 2008-01-17
Hm...I dunno what to tell you then...I can play on 1024x768 in 16 bit with almost no lag on my setup, which is significantly worse than yours...honestly, I'm stumped...sorry bro :(  If you're mot running at least 0.9.51, get that (current version is 0.9.53 if you have the wine repos in your sources list, 0.9.47 I believe if you don't).  Short of that, I can't say anything, cause your hardware is much better than mine and it runs fine for me with pretty much 0 lag (I have a bigger problem with my mouse sensitivity than with lag on my setup).  Or you might want to find someone who knows about graphics drivers in Ubuntu.  My gfx card is integrated, so I don't have issues, but if you have some kind of tricked-out top-of-the-line card, that could also be an issue.

---

### Post by Vinno on 2008-01-19
You guys should get Cedega, i had problems getting warcraft to work with wine, so off i go to cedega and bang, game works off the bat. They have config files for games.

Its a small fee really.

---

### Post by nypdz on 2008-01-21
hi, i run both ubuntu on my laptop and pclinuxos on my pc. i play dota using wine on pclinuxos and it works perfectly fine. however my laptop with ubuntu gives me the following error.

wine: creating configuration directory '/root/.wine'...
Could not load Mozilla. HTML rendering will be disabled.
wine: '/root/.wine' created successfully.
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x34f3f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f640,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f670,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
root@zans:/media/sda3/Program Files/Warcraft# fixme:win:EnumDisplayDevicesW ((null),0,0x34a8ac,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:win:EnumDisplayDevicesW ((null),0,0x34b018,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:win:EnumDisplayDevicesW ((null),0,0x34b0c8,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:imm:ImmAssociateContextEx (0x30028, (nil), 16): stub 

this is using -opengl and after it loads i find wierd color combinations in the game,without opengl i.e., using dxd8 ddl of wine on warcraft III it lags a lot. please help
1.8ghz centrino duo, 2gb ram,80GB,intel 945gm (256MB) graphics card

---

### Post by Deeo on 2008-02-08
Can anyone of you connect to battle.net? 
Because I can't :(
Any idé?

---

### Post by vexorian on 2008-02-09
Hello, reporting that since the CD protection removal this should be much easier than before, but we need to wait/request for an standalone patch for the version without the CD protection. So, let's wait.

nypdz: sounds as if your laptop uses a graphics card without good support, give us specs?

Edit: There are standalone patches!

So, these are the updated instructions. AFTER installing the game, download patch **1.21b** from [http://ftp.blizzard.com/pub/war3x/patches/pc/](http://ftp.blizzard.com/pub/war3x/patches/pc/) , install the patch, possibly using 

```
wine ./War3TFT_121b_English.exe
```
from the directory where you saved the patch file (Note that if you downloaded one for another language, the executable name changes)

Once the patch is succesful you should be able to use wine to run war3 , notice that this also depends on how good Linux support for your graphic card is.

Patch 1.21b removes the CD protection so it should not cause issues anymore like requiring a no-cd crack (and thus being unable to do battle.net) , etc.

---

### Post by hungryOrb on 2008-02-18
Hello Folks,
Just wondering if I could stick my problem up here!

W3 is installed and when trying to run it, it asks for the CD, even though I've updated to the most recent patch which doesnt use the CD. Anyone experienced this?
And please could someone tell me the opengl parameter in full? And where is it placed?

Thanks in advance :D

---

### Post by vexorian on 2008-02-21
1. run war3.exe not "Frozen Throne.exe" try running it from the war3 folder.

When you run "Frozen throne.exe" and it tells you to insert a CD in the latest patch, it means it crashed, things like that happen on init if your directx support is not good enough, get good drivers for your 3d graphics card, and try to run war3 with -opengl

---

### Post by Fluffy_Penguin on 2008-03-02
Hi all, if you're still having problems after following these steps and loads of; ](*,), I would like to suggest the application called "PlayOnLinux" I installed it yesterday, and now the sound AND Battle.net works! (You still have to move/remove/rename/whatever the Movie directory in the warcraft 3 folder though, because they mess up the game big time)

There might be a few lesser issues (that I've been having from time to time myself) like the upper and/or lower menu bars not disappearing, but they are quite minor and are little more than a slight annoyance.

The site is [http://www.playonlinux.com/en/]("http://www.playonlinux.com/en/")
 and the download button is hidden at the very top of the site.
(warning: the site is pretty badly translated in some areas, the program and site is originally French, so watch out or they'll beat you with baguettes!(:lolflag:))

Hope It works for you and good frigging luck.

---

### Post by Enverex on 2008-03-02
Hrm, what exactly does PoL do? I noticed it's kinda an automated installer for Wine, but the games I've seen on their site with it so far are ones that are really straight forward and install/play without issue anyway...

---

### Post by SpiXe on 2008-03-23
Does anybody know how to use no-cd crack in wine? If its possible?

---

### Post by djotaku on 2008-03-23
I've got it installed and I can run Warcraft.  I'm using Warcraft III version 1.14.  I'm able to start single player custom games without any problems.  However, it gets stuck if I try to quit the mission.  

On Single Player Campaign, it won't even start.  The progress bar gets about 75% of the way and then gets stuck.  

Other info that might be relevant:  
I'm using wine-0.9.46 installed via Synaptic
when I run glxgears I get 683.46 FPS
My computer is 1.6 Ghz processor with 512 MB RAM
My graphics card is Intel 950

---

### Post by janfsd on 2008-03-24
> **SpiXe said:**
> Does anybody know how to use no-cd crack in wine? If its possible?
Yes, it is possible, the same way you would use it in windows. Btw, the latest patch of Warcraft 3, allows you to run it without cd.

---

### Post by Patrick-Ruff on 2008-03-25
I recall the fonts on mine were all weird, is there a fix for that?

---

### Post by Realmdown on 2008-03-30
I got it all working beautifully using wine ver 0.9.58, even played a few b.net games. Only problem is, when I hold alt + click it brings up a list as if I was right clicking on the desktop. I tried turning of the windows manager control, which solves that problem, but when I do that I can't type! Anyone experience similar problems/know what I'm doing wrong?

---

### Post by baron162 on 2008-04-01
[http://appdb.winehq.org/appview.php?iVersionId=1177](http://appdb.winehq.org/appview.php?iVersionId=1177)
what wine homepage says about your problem, scroll down to find this:

> Warning
  ALT-KEY COMBO WARNING
Window managers often have the alt key bound to certain features, especially the alt-click. THIS IS NOT A WINE BUG. If you have problems with the alt key in any way DO NOT REPORT IT. Fix your window manager. I'm not going to list steps for every one because there are too many possibilites. Figure out yourself or ask in a help forum (here is okay... but be warned all I use is TWM). If you are desperate, turn off window manager managed windows in winecfg.
KDE
Go into KDE Control Center, expand Desktop, click window behavior, then click window actions tab. You can turn off the alt-combos. If you want to make window specific settings, click on window specific settings under window behavior on the side.
GNOME
The option to change the key binding is in System Menu -> Preferences Menu -> Windows.
 

---

### Post by Realmdown on 2008-04-01
> **baron162 said:**
> [http://appdb.winehq.org/appview.php?iVersionId=1177](http://appdb.winehq.org/appview.php?iVersionId=1177)
what wine homepage says about your problem, scroll down to find this:
Thanks a lot! That's exactly what I needed.

---

### Post by SwordRaven on 2008-04-15
This is a nightmare! :(

Warcraft III Frozen Throne runs fine under 0.9.46 but obviously there is the battle.net and LAN bug

When I upgrade to any other version, -opengl no longer seems to have any effect! :(

Any ideas?

Cheers

---

### Post by vexorian on 2008-04-15
I am using the latest version and -opengl seems to work.

1. How do you recognize it doesn't work?
2. Are you sure no no-cd crack is involved?
3. Are you trying the beta version?

---

### Post by SwordRaven on 2008-04-16
> **vexorian said:**
> I am using the latest version and -opengl seems to work.

1. How do you recognize it doesn't work?
The performance behaves exactly the same as if the opengl flag is not used, about 3fps on them menu and totally unplayable, I have tried 0.9.45, 0.9.46, 0.9.56, 0.9.57, 0.9.58 and 0.9.59 and all exhibit this behaviour except for the 4x versions.
> **vexorian said:**
> 2. Are you sure no no-cd crack is involved?
I haven't used one and it's a fresh install so hopefully not :)

> **vexorian said:**
> 3. Are you trying the beta version?
Of Wine? I was using the versions in the repository, which I believe are 0.9.46 (gutsy) and 0.9.59 (wine repo)

At the moment I am using 0.9.45 because the battle.net bug isn't in that version but there are graphical problems which make the game look ugly ;)

I'm sure it'll probably be something simple but I can't seem to find any information.

My system is an AMD X2 4000+ with 2gb RAM and an ATI x1950 Radeon graphics card. The ATI drivers are installed through the Restricted Drivers Manager and as far as I know are working fine.

Cheers

---

### Post by vexorian on 2008-04-16
No, I mean there is a beta patch for wacraft III around.

I doubt war3 is ignoring -opengl (You are calling war3.exe, not Frozen throne.exe, right?) it looks more as if WINE's performance has dropped on your setup.

> At the moment I am using 0.9.45 because the battle.net bug isn't in that version but there are graphical problems which make the game look ugly

I am right now using 0.9.59, I can play in bnet and the graphics are as fine as usual. One thing I noticed is that after changing to winehq's version I need to use winecfg and something else to setup it correctly.

---

### Post by SwordRaven on 2008-04-16
> **vexorian said:**
> No, I mean there is a beta patch for wacraft III around.

I doubt war3 is ignoring -opengl (You are calling war3.exe, not Frozen throne.exe, right?) it looks more as if WINE's performance has dropped on your setup.

I was calling Frozen Throne.exe so I've changed it to war3.exe although there is no change in performance at all.

I assume it is a problem with wine but is there any way of finding out what? :/

I don't think I'm using a beta patch, I just installed the latest one from the site.


> **vexorian said:**
> I am right now using 0.9.59, I can play in bnet and the graphics are as fine as usual. One thing I noticed is that after changing to winehq's version I need to use winecfg and something else to setup it correctly.

do you know what the something else is perchance? I ran winecfg again and it's using all the same settings as before.

Thanks

---

### Post by rybaxs on 2008-04-30
any idea how to connect into LAN? we can see who created the game but the the other can't connect. its like windows 'firewall issues'. does anyone know how to disable the connection refusal of ubuntu?

---

### Post by fusionisthefuture on 2008-04-30
its probably the same thing that happens with windows, only the problem isnt because of windows itself, its a problem with the router, you have to open a port (i think its 6112 or something like that) at the least, or you can check your enable DMZ box, although i wouldnt recommend this, because it turns off your routers firewall altogether.  if you happen to have a firewall installed on your ubuntu computer (unlikely, youd know if you did) then you would have to allow that port (6112) on that firewall also.  
-fitf

---

### Post by mrx_rf on 2008-05-30
Hi ):P...

Somebody plz help me...

problem:
- the sound not smooth (kinda stuck a little bit)
- land turn to black when i move the cursor (see attachment)

I've install ati driver ([http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)) and already work with compiz.
Already solve blinking/flikering probem with compiz-switch ([http://forlong.blogage.de/article/pages/Compiz-Switch](http://forlong.blogage.de/article/pages/Compiz-Switch))


AMD turion64, ATI Xpress 1100, wine ver 0.9.46, ubuntu 7.10

---

### Post by Gathalimay on 2008-06-11
I'm having problems with the latest version of wine. It worked properly a few months ago, but now it just doesn't work. When Warcraft III loads, it makes my resolution really bad and doesn't even load up the game. I can still see my taskbar and the rest of the screen is just black. It does whether or not I use -opengl. I can still alt-tab to my other windows, but the screen still fails. Any ideas? I've tried changing it back to Windows 2000 but that doesn't help.

Thanks in advance.

---

### Post by vexorian on 2008-06-12
> **Gathalimay said:**
> I'm having problems with the latest version of wine. It worked properly a few months ago, but now it just doesn't work. When Warcraft III loads, it makes my resolution really bad and doesn't even load up the game. I can still see my taskbar and the rest of the screen is just black. It does whether or not I use -opengl. I can still alt-tab to my other windows, but the screen still fails. Any ideas? I've tried changing it back to Windows 2000 but that doesn't help.

Thanks in advance.
I have no idea.

I really think you should report this problem asap.
1) Only the Wine devs would have an idea what's going on.
2) According to what you said, It is a regression, so the best for us all is to get it fixed before retail Wine 1.0

---

### Post by Enverex on 2008-06-12
> **Gathalimay said:**
> I'm having problems with the latest version of wine. It worked properly a few months ago, but now it just doesn't work. When Warcraft III loads, it makes my resolution really bad and doesn't even load up the game. I can still see my taskbar and the rest of the screen is just black. It does whether or not I use -opengl. I can still alt-tab to my other windows, but the screen still fails. Any ideas? I've tried changing it back to Windows 2000 but that doesn't help.

Thanks in advance.

Can't tell you anything from that description. Pastebin the terminal output from when you run it and that should provide some clues.

> **vexorian said:**
> 
2) According to what you said, It is a regression, so the best for us all is to get it fixed before retail Wine 1.0

Not likely to get fixed unless it's a very minor change or one of the very recent patches broke it, too close to the 1.0 release now.

---

### Post by Gathalimay on 2008-06-13
This is what it turns up when I try to run it under wine (typing -opengl returns the same results)

```
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33f3a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f64c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f67c,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 800x600x32 @75! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 800x600x32 @70! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 800x600x32 @60! (XRandR)
fixme:quartz:AVISplitter_InitializeStreams stream 1: frames found: 2172570, frames meant to be found: 2173350
fixme:win:EnumDisplayDevicesW ((null),0,0x33e028,0x00000000), stub!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
err:quartz:AVISplitter_Sample Error sending sample (1)

```

Looks like a problem from xorg and not wine. Says no 800x600 resolution match from X11 (but it should since my resolution is currently 1280x960). I'm leaning towards the refresh rate being the problem here. I had to manually edit the xorg file upon installing Ubuntu to add in resolutions because that resolution section wasn't there when I installed it and that was the only way I could get anything higher than 800x600. However, I never indicated refresh rates for the resolutions

I'll paste the contents of my xorg here:
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection
, but n
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

```

I'm guessing the problem is with the refresh rate and/or the bit depth settings on my xorg and not so much a problem with wine. I'm not sure how to fix it. Any Ideas? Don't I need to add @xx or something after a resolution on the xorg file to indicate a refresh rate? 

okay, so the resolutions should be:
1280x960 @60
1152x864 @75
1024x764 @85/75/70/60
800x600 @85/75/70/60
640x480 @85/75

How can I incorporate refresh rates and bit depths into my xorg file?
Thanks in advance

---

### Post by dmcdante on 2008-07-26
For such questions it is best to read the manuals of the corresponding programs directly instead of asking people for help on the forums. Google for "xorg.conf manpage" if you don't want to use consoles.

greets

---

### Post by PsychedelicWonders on 2008-07-28
Is the intial "how to" in the first post still valid?

Or has since it's been so long, have things changed or been upgraded in anyway?

Or should I just follow the 1st post step by step?

---

### Post by vexorian on 2008-07-29
Just make sure to download standalone patch 1.22 and install it (the patch) after install wc3, it should be the same as running setup.exe

Because blizzard sucks, they changed the compiler for 1.22, so you need to download this:  [http://www.microsoft.com/downloads/details.aspx?FamilyID=200b2fd9-ae1a-4a14-984d-389c36f85647&DisplayLang=en](http://www.microsoft.com/downloads/details.aspx?FamilyID=200b2fd9-ae1a-4a14-984d-389c36f85647&DisplayLang=en) and install it in WINE else war3 will crash. (if you got 1.22)

After that it should work ok, provided you got graphics driver and a valid CD-key.

---

### Post by davidw89 on 2008-08-09
Hi there

Installed Warcraft 3 Reign of Chaos + The frozen throne.

Patched to 1.22a.

Tried running Warcraft 3, didn't work.

Put -opengl command and it loads BUT the screen goes black and the computer freezes. i had to reboot.

I am guessing this had to do with the MOVIES so how do i move the MOVIES to another directory? The FAQ does a bad job at explaining it

and yes i  have installed the file from above post but when i click accept it just closes?

---

### Post by davidw89 on 2008-08-09
Update:

It seems like i didn't enable the Nvidia 8800Gt driver (somehow got disabled)

So now i enable it, restart comp and start warcraft 3. 
There's sound alright but no screen and in fact the screen resolution gets defaulted back to really small :/

---

### Post by davidw89 on 2008-08-09
> Unfortunately wine will not play the movies (though apparently you can watch them in xine or something) so it's best to move them so the game can not find them:
cd .wine/fake_windows/Games/Warcraft\ III/

Explain please?

What do you mean by move? How exactly do you move??
errr

---

### Post by davidw89 on 2008-08-09
Explain how to set this:
> Exit winetools and open the wine config file that was created in a text editor (eg nano .wine/config). Look
for '[Version]' and under that where it says:
"Windows" = "win98"
change it to:
"Windows" = "winxp"
then save the file and exit.

---

### Post by atariman5000 on 2008-08-18
> **davidw89 said:**
> Explain please?

What do you mean by move? How exactly do you move??
errr

I simply renamed the folder to "moviez". This worked for me. Before that, the game would lockup. After renaming the folder, it played!

---

### Post by k1ngb0b0 on 2008-08-18
Hello.  

I followed this guide and it worked GREAT.  I'm only having ONE minor hangup.

I also play world of warcraft and I love how I have it set up.  It's fullscreen and I can rotate my desktop cube to do other things while playing (look up quests, change songs etc.)

I can't get warcraft III to work in the same fashion.  I tried this, but when my cube would rotate the desktop resolution would get really messed up.  All the icons would be really big, the screen would flash and then they'd go back to normal.  This would be fine for awhile but eventually I got a black screen and I had to restart via the power button.

I have the frozen throne expansion and the most current patch from battle.net but I can only get it to run well in window mode.  I hate window mode and it's very hard to play.  Is there anyway I can tweak it to play better on fullscreen?

---

### Post by k1ngb0b0 on 2008-08-19
No ideas?  I haven't had time to play around with it yet today but I'd love to get someone else's opinion on this :)

---

### Post by k1ngb0b0 on 2008-08-20
I figured out the way I have WoW running.

WoW has a video option to run in a windowed mode, to keep the game's gamma the same as the desktop.  There's also more options to prevent resizing and to maximize the window.

Does anyone know if I can simulate this with warcraft 3 somehow?  I'd like to figure this out because playing in standard window mode is terrible.

---

### Post by Rio6000 on 2008-08-20
Hey everyone,

I've just bought Warcraft III and the expansion.
Installed Reign of Chaos just perfectly en it ran like a dream.
just an hour ago i wanted to install the Frozen Throne but it didn't detect ROC apparently because i cant click on the install option in the menu...

They're both "Best seller series" retail boxes and i'm running on 64 bit ubuntu and tried both wine 1.0 and 1.1.2.

hope someone can help me.

cheers,
Rio

---

### Post by dillinger417 on 2008-08-26
Everything seems to be working fine except for saving.  I get an access violation and the game crashes.  This is a ntfs partition I have mounted w/ my user as owner and full permissions.  Anyone know what I might be missing?

edit: I moved files to my home folder and was able to save without problems, so the problem is w/ permissions on the mounted partition not wine or warcraft III. Any advice would still be appreciated as I would like to learn more. Partial cat fstab:
/dev/sdaX /media/sdaX ntfs-3g uid=MY_USER_NAME,defaults,umask=000,locale=en_US.UTF-8 0 0
Plz PM so as not to clutter the thread. thx.

edit 2.0: I got the same error 1 time today playing from my Home folder, but the other ~10 times it saved ok... so idk what the issue is exactly, but I've never been able to save when playing from the other partition. *shrug*

---

### Post by Despot Despondency on 2008-08-26
Hey, I've managed to install wine, using [http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb"), and it seems to be working fine. Managed to install Warcraft 3 too and it's working but I've got a few problems.

1) The screen seems to scroll very sporadically, actually hardly ever, I have to click on the the minimap.

2) The main ubuntu panel still appears along the bottom of the screen

3) The game isn't set to the top left hand side of the screen, but a couple of inches across, so I can see all of the control panel.

Has anyone else had any of these problems? Or know any solutions? Cheers in advance

---

### Post by abitwise on 2008-08-27
If you have Nvidia card, then you can run warcraft 3 without the -opengl option, and it feels a little smoother.

Scrolling problem occurs with desktop cube, turn it off, and no problem anymore.

If you have a gamma problem, create a launcher onto your desktop with this command (or you can run it in a terminal window): xgamma -gamma 1.0

Also don't try to swith desktop when playing or the game may disappear and you can't switch back!

What i might add is that the LAN game also works with Hamachi and also with OpenVPN, if you have skills to run these you can try. But sometimes others may not see your game, still you can join them.

Hope that helps someone, cheers!

---

### Post by phoenix116 on 2008-08-29
I just tried to play wc3 on ubuntu again.
Half a year ago there were a lot of bugs so it was totally unplayable.

Now it works really **fine**! In opengl and directX mode!

first there were just some minor issues:

[LIST]
[*]doesnt work  with widescreen( 1680x1050 ), just like on windows
[*]when i set resolution to 1400x1050, its nearly ok, but there is a black bar on the right side
[*]because it is not fullscreen, the mouse can leave the window and scrolling doesn't work properly on the right side
[/LIST]

I finally got it to work by changing wc3s registry keys for resolution --> all problems solved.

Just thought this could help someone who has the same problems...

---

### Post by Despot Despondency on 2008-08-29
Cool, thanks for the tip. Never used wine before so I had to find how to change the resolution. Found [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3126](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3126), there was a query regarding this problem with the solution. 

Only issue left is the crashes when saving the game, but I haven't been able to find a solution to that problem, so I don't fancy my chances. Anyway it's time to kill some orcs :guitar:

---

### Post by davidw89 on 2008-09-19
How the hell do i open it with -opengl
instructions PLEASE

---

### Post by mcbean on 2008-09-22
> **davidw89 said:**
> How the hell do i open it with -opengl
instructions PLEASE

go to the Warcraft III directory in a terminal, and type 
wine war3.exe -opengl 

Thanks for the useful information in this thread, my main problem was that I was using compiz. I'm Quite new to linux, didn't realise it would interfere.

---

### Post by davidw89 on 2008-10-19
Is there an easier way such as making the .exe -opengl by right clicking on it, properties and adding the -opengl command? Something like that. browsing to the wine program files will take a long time..and i cbs doing that everytime i want to play.

---

### Post by davidw89 on 2008-10-31
> 
go to the Warcraft III directory in a terminal, and type
wine war3.exe -opengl 

This works.

But when i try to create a launcher it doesn't work. Starting to piss me off.

Error:
Could not start war3.exe! Make sure the loader is in your Warcraft III install directory.

Also why IN THE WORLD doesn't the Open with "wine -opengl" work??????????

---

### Post by vexorian on 2008-11-01
> Also why IN THE WORLD doesn't the Open with "wine -opengl" work??????????
That probably ends with the command line becoming "wine -opengl war3.exe" and that means "start program -opengl.exe with argument war3.exe"

So, to avoid your problem:

```

#!/bin/bash
cd "/your/path/to/warcraft III/folder"
wine war3.exe -opengl

```

Save that as a .sh file, mark it as executable, make the launcher to this file or double click the file if you want.

---

### Post by xnostradamusx on 2008-11-01
any idea why when i try warcraft i can manage to play but its slower than playing in windows... btw i havent tried using -opengl command

---

### Post by vexorian on 2008-11-01
> **xnostradamusx said:**
> i havent tried using -opengl

That's probably it.

In warcraft III's case WINE acts a wrapper between directx calls and opengl. If you use -opengl, you'll get a speed boost, in some setups it is significant, in mine not so much.

If it is still slow, then it is a problem related to your video card driver or its absence...

---

### Post by xnostradamusx on 2008-11-01
ahh can you try play warcraft with open gl command and just opening its exe if you see any difference, cause it seems i cant make it work wine or cedega

---

### Post by vexorian on 2008-11-01
> **xnostradamusx said:**
> ahh can you try play warcraft with open gl command and just opening its exe if you see any difference, cause it seems i cant make it work wine or cedega
I already know it won't make a difference in my setup, but  I do know it makes a difference in many others. You have to try it, it is not true you can't do it, you just  need to find out what you are doing wrong in your attempts.

Could you describe us what exactly are you doing to try to run with -opengl and are not accomplishing?

---

### Post by soxs on 2008-11-02
> **vexorian said:**
> That probably ends with the command line becoming "wine -opengl war3.exe" and that means "start program -opengl.exe with argument war3.exe"

So, to avoid your problem:

```

#!/bin/bash
cd "/your/path/to/warcraft III/folder"
wine war3.exe -opengl

```

Save that as a .sh file, mark it as executable, make the launcher to this file or double click the file if you want.

It's easier for most users to do it like that:

```
sudo nano /usr/bin/wc3roc
```

Add these lines:
```
#!/bin/bash
cd $HOME/.wine/drive_c/WC3_INSTALL_FOLDERS
wine ./war3.exe -opengl
```
Save via <STRG><O>

Make the script executable:
```
sudo chmod +x /usr/bin/wc3roc
```

From now on you can run it by simply typing ```
wc3roc
``` into a treminal.

Same for the extension The Frozen Throne:

```
sudo nano /usr/bin/wc3tft
```

Add these lines:
```
#!/bin/bash
cd $HOME/.wine/drive_c/WC3_INSTALL_FOLDERS
wine ./Frozen\ Throne.exe -opengl
```
Save via <STRG><O>

Make the script executable:
```
sudo chmod +x /usr/bin/wc3tft
```

From now on you can run it by simply typing ```
wc3tft
``` into a treminal.






> **vexorian said:**
> I already know it won't make a difference in my setup, but  I do know it makes a difference in many others. You have to try it, it is not true you can't do it, you just  need to find out what you are doing wrong in your attempts.

Could you describe us what exactly are you doing to try to run with -opengl and are not accomplishing?

If you don't get a significant speed boost using the opengl switch, either your driver is messed up or you are suffering like many others from the lib drm error, which consequently leads to indrect rendering. (Plx correct me if I didn't get your point, but at least my last seven PCs showed that behavior, the boost was about 200%)

---

### Post by reg4c on 2008-11-02
Hey, 

I managed to get Warcraft working but one thing is bugging me.
When the mouse goes right then the view is moving right like it should be, but when it moves left then the normal cursor, not the Warcraft one, appears and the view does not move.

How should this be handled?

Cheers

---

### Post by xnostradamusx on 2008-11-05
> **vexorian said:**
> I already know it won't make a difference in my setup, but  I do know it makes a difference in many others. You have to try it, it is not true you can't do it, you just  need to find out what you are doing wrong in your attempts.

Could you describe us what exactly are you doing to try to run with -opengl and are not accomplishing?

ok i manage to make warcraft 3 work and can play now with dota only problem now it works no problem but when i alt+tab and return to my game my graphics is messed up, btw im using interl graphics 380 mb something shared

---

### Post by soxs on 2008-11-05
> **xnostradamusx said:**
> ok i manage to make warcraft 3 work and can play now with dota only problem now it works no problem but when i alt+tab and return to my game my graphics is messed up, btw im using interl graphics 380 mb something shared

winebug

---

### Post by Funnnny on 2008-11-05
I have that problem too. So if it's a bug, is there any way to fix it ?

---

### Post by soxs on 2008-11-05
Info  about the named focus bug:
[http://bugs.winehq.org/show_bug.cgi?id=13547](http://bugs.winehq.org/show_bug.cgi?id=13547)
[http://bugs.winehq.org/show_bug.cgi?id=10841](http://bugs.winehq.org/show_bug.cgi?id=10841)
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3126](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3126)

---

### Post by dacoch on 2008-11-05
I tried to run Warcraft in wine and it did it but the graphics didn't quite work. does any of you know what can I do

---

### Post by soxs on 2008-11-06
> **dacoch said:**
> I tried to run Warcraft in wine and it did it but the graphics didn't quite work. does any of you know what can I do

Info! Info is what we need!
Run it from the commandline, give us the output.
What kind of "bad" rendering? Distorsion? Lost textures? Low FPS? ..

---

### Post by xnostradamusx on 2008-11-06
ok i have wine and cedega and in cedega there is a tool where you can test your computer if you pass cedegas requirements. by default when i tested all passed but direct x failed.

[[img]http://img371.imageshack.us/img371/6344/screenshotxp4.th.png[/img]](http://img371.imageshack.us/my.php?image=screenshotxp4.png)[[img]http://img371.imageshack.us/images/thpix.gif[/img]](http://g.imageshack.us/thpix.php)

but when i bump some solutions about xorg.conf i edited it and after tested with cedega tool again all passed means everything works.

btw heres my comp info


cpu: Intel(R) Pentium(R) Dual CPU T2330 @ 1.60GHz
cpu_ghz: 1.6
memory: 2017
videocard_manufacturer: Tungsten Graphics, Inc
videocard_type: Mesa DRI Intel(R) 965GM 4.1.3002 x86/MMX/SSE2
videocard_ram: 2048
agp_aperture_size: N/A
videocard_driver_version: 1.4 Mesa 7.0.3-rc2
soundcard: HDA Intel at 0x92400000 irq 2
soundcard_driver: ALSA Version 1.0.15
machine_bitness: 32
kernel: 2.6.24-16-generic
x_version:
distro: Debian lenny/sid
GUI version: 6.0.2

and heres what i edited in xorg


run in terminal
    gksu gedit /etc/X11/xorg.conf


Find
Section "Device"
With only one monitor attached there must be only one such section
Add/check the driver to
Driver "intel"
possibly
Driver "i810"
Restart X
This is to force the use of the intel driver mot vesa or mesa

*note this solution is for people using intel graphics only

---

### Post by vexorian on 2008-11-08
> **xnostradamusx said:**
> ok i manage to make warcraft 3 work and can play now with dota only problem now it works no problem but when i alt+tab and return to my game my graphics is messed up, btw im using interl graphics 380 mb something shared
Try running -window, will allow you multi tasking while playing wc3 without alt-tab, well it depends on taste, I do prefer -window, even on windows I used it.

---

### Post by xnostradamusx on 2008-11-08
> **vexorian said:**
> Try running -window, will allow you multi tasking while playing wc3 without alt-tab, well it depends on taste, I do prefer -window, even on windows I used it.

ok i tried now i can multi task but when i click on the game screen my video flickers inside the game each click i do there makes the screen go black and returns normally every click

kinda annoying but not happening when im in full screen, maybe my compiz being enabled affects that.

---

### Post by vexorian on 2008-11-08
Try using that fusion-icon app that allows you to disable compiz temporarily.

---

### Post by poisonkiller on 2008-11-11
Hello!
I'm running Ubuntu 8.10 with WINE 1.1.8 and finally managed to get Warcraft 3 TFT working. Not only that, but Garena too. So... when I start Warcraft up with Garena and try to join a LAN game, I get some weird memory allocation error. Is there any way to fix this?

PS: I'm not really interested in reading 24 pages of text to **maybe** find an answer, so if there is an answer, could somebody guide me to it? :)

---

### Post by soxs on 2008-11-11
> **poisonkiller said:**
> Hello!
I'm running Ubuntu 8.10 with WINE 1.1.8 and finally managed to get Warcraft 3 TFT working. Not only that, but Garena too. So... when I start Warcraft up with Garena and try to join a LAN game, I get some weird memory allocation error. Is there any way to fix this?

PS: I'm not really interested in reading 24 pages of text to **maybe** find an answer, so if there is an answer, could somebody guide me to it? :)

AcceptEx isn't implemented yet completly, so you won't be able to host a LAN game and some other nastinesses...

---

### Post by poisonkiller on 2008-11-12
But can I fix it somehow, like using a patch or something?

---

### Post by soxs on 2008-11-12
> **poisonkiller said:**
> But can I fix it somehow, like using a patch or something?
I don't know if the patch has evolved that far not crashing wc3 every 10-20 minutes... but you could compile 0.945 yourself (thouzgh this is a hell of hassle)

---

### Post by 37452 on 2008-11-28
hello all,
im new in linux n im using ubuntu 8.04 for the last 2 month
im kinda stuck in running dota using wine
im not a legal user of warcraft, just have an iso image of it
im using acer 5315 laptop
warcraft v1.20
wine v1.0 i guess
when i start it first everything just fine just like i played it in win*
but when i played about 30 minutes or so.. the game crashed
and makes my computer not responding at all
and the games colour go blur like a nintendo game colour in 8 bit :confused:
i dont know how to explain it in english
sorry if i have a bad english mate
o... i come from indonesia.. is anyone from here??
thanx in advance mate.

---

### Post by thebuc1010 on 2008-12-02
Hi.  I have a pretty simple question I think.
My computer used to work perfectly with windows xp but then it crashed one day and i got ubuntu 8.04.
I managed to harvest all my old files that I used in windows.
So I used to play a lot of Frozen Throne on windows but I do not have the cd's or the cd keys that I originally used to install the game because of a patch that came out recently that allowed the game to run with out the cd.

So I figured i could just copy my old warcraft3 folder from windows into my 
~/.wine/drive_c/  folder and then just type (in the terminal): wine "Frozen Throne.exe" -opengl . like suggested in this thread.
It looked promising at the start but then it said i needed the cd in the drive to continue which i do not have.
  My patches are all in the folder, and up to date including the no cd patch, so im wondering if anyone has any suggestions on how i could get around the cd requirement.
My wine is the most current version to my knowledge.
thanks for anything.

I just navigated to the folder I pasted all my war3 files into and right clicked on Frozen Throne.exe and tried opening with wine and it also says i need the cd.
I could probably borrow a Cd from a friend but im hoping to avoid this inconvience. Thanks again.

---

### Post by soxs on 2008-12-02
> **thebuc1010 said:**
> Hi.  I have a pretty simple question I think.
My computer used to work perfectly with windows xp but then it crashed one day and i got ubuntu 8.04.
I managed to harvest all my old files that I used in windows.
So I used to play a lot of Frozen Throne on windows but I do not have the cd's or the cd keys that I originally used to install the game because of a patch that came out recently that allowed the game to run with out the cd.

So I figured i could just copy my old warcraft3 folder from windows into my 
~/.wine/drive_c/  folder and then just type (in the terminal): wine "Frozen Throne.exe" -opengl . like suggested in this thread.
It looked promising at the start but then it said i needed the cd in the drive to continue which i do not have.
  My patches are all in the folder, and up to date including the no cd patch, so im wondering if anyone has any suggestions on how i could get around the cd requirement.
My wine is the most current version to my knowledge.
thanks for anything.

I just navigated to the folder I pasted all my war3 files into and right clicked on Frozen Throne.exe and tried opening with wine and it also says i need the cd.
I could probably borrow a Cd from a friend but im hoping to avoid this inconvience. Thanks again.

You lack certain registry keys, but don't aks me which ones, there are hundreds...

---

### Post by dethredic on 2008-12-16
I just installed wine and WC3, but when I try to run WC3 it says I dono't have a CD in, although I do (I just used it to install).

I have wine 1.0.1. I was looking at the winehq page for Wc3 and they have some patch that fixes some things in WC3, but I click the link and it takes me to a page with this:

> 
diff --git a/dlls/kernel32/sync.c b/dlls/kernel32/sync.c
index 08385f1..ec8c16a 100644
--- a/dlls/kernel32/sync.c
+++ b/dlls/kernel32/sync.c
@@ -1826,12 +1826,12 @@ HANDLE WINAPI CreateIoCompletionPort(HANDLE hFileHandle, HANDLE hExistingComplet
     TRACE("(%p, %p, %08lx, %08x)\n",
           hFileHandle, hExistingCompletionPort, CompletionKey, dwNumberOfConcurrentThreads);
 
-    if (hExistingCompletionPort && hFileHandle == INVALID_HANDLE_VALUE)
+/*    if (hExistingCompletionPort && hFileHandle == INVALID_HANDLE_VALUE)*/
     {
         SetLastError( ERROR_INVALID_PARAMETER);
         return NULL;
     }
-
+#if 0
     if (hExistingCompletionPort)
         ret = hExistingCompletionPort;
     else
@@ -1858,6 +1858,7 @@ fail:
         CloseHandle( ret );
     SetLastError( RtlNtStatusToDosError(status) );
     return 0;
+#endif
 }
 
 /******************************************************************************



I have no idea what to do with that.

I am going to try to update Wine and see if that helps the CD thing. Ohh ya, I am in 8.1.

---

### Post by loudog23 on 2008-12-29
> **dethredic said:**
> I just installed wine and WC3, but when I try to run WC3 it says I dono't have a CD in, although I do (I just used it to install).

I have wine 1.0.1. I was looking at the winehq page for Wc3 and they have some patch that fixes some things in WC3, but I click the link and it takes me to a page with this:

I have no idea what to do with that.

I am going to try to update Wine and see if that helps the CD thing. Ohh ya, I am in 8.1.

Same situation here,
Unbuntu 8.10
Wine 1.0.1
Original CD w/key
Dual Core 2.66 1.5g-ram
Drive in Winecfg are OK
Drive is mounted at launch
-opengl was added to laucher
patched latest version 1.22a

Was running it well with Xunbuntu and patch-procedure found on this site.
But can't find a way to ake it work with ubuntu 8.10
Sound and everything is fine during installation

Oh, ya: i get this when i run: wine "war3.exe"-opengl (I get the same with "Warcraft III.exe" but with the CD error)
> lou@LOUPC:~/.wine/drive_c/Program Files/Warcraft III$ wine war3.exe -opengl
err:ole:CoCreateInstance apartment not initialised
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  438
  Current serial number in output stream:  438
[email]lou@LOUPC:~/.wine[/email]/drive_c/Program Files/Warcraft III$

---

### Post by roargg on 2009-01-24
hello!

I installed WC3 to my comp, but after launching Warcraft III I get CD-ROM drive error. It says it is unable to locate my CD from the drive.
Any suggestions what to do?

---

### Post by balgaltz on 2009-01-25
Just install latest manual patch (1.22 Full Patch, assuming you don't have 1.21b), it will no longer require CD.
[http://us.blizzard.com/support/article.xml?articleId=21220]("http://us.blizzard.com/support/article.xml?articleId=21220")

---

### Post by hookdump on 2009-03-03
I love you.

:d:d:d:d

---

### Post by elitenoobboy on 2009-03-07
I was writing a script to disable compiz's edge flipping automatically when the game is launched and then restore it when the game is finished.
The thing is, whenever I launch the game through wine, the process finishes in a few seconds from the terminals point of view, and then it runs the next part of the script re-enabling compiz's edge flipping feature prematurely. Does anyone know why wine acts this way (as opposed to almost every other process out there which require a & for the terminal to return before the process is completed) and how to fix it?

Also, I am finding wine buggy in more ways than that. To get the game to not launch in a virtual window, I had to disable virtual windows for the default setting to get the game to not use VWs, even though I had the application settings configured for frozen throne.exe itself to not use a virtual window. Why does wine ignore it's own application settings in this manner?

Another bug is that I switched desktops while the game was running and now it dissapeared. I can still hear the games sound running, but there is nothing on any of my taskbars or desktops for the game. No way to get back to it.

---

### Post by Morfi777 on 2009-04-28
Please help with this error. I'm pissed looking for solutions which does not exist or they write in other langs than english.

while installing I get such error:
```
Log created 04-28-2009 at  9:17pm.



Setup was unable to add the following file to Z:\home\morfi\Warcraft III\War3.mpq:

    blizzard.ax

Error 0x85200069:  

(C:\temp\020606lockit\Installer\Source\MpqUtil.cpp:63)



Installation canceled.



```

---

### Post by elitenoobboy on 2009-04-28
> **Morfi777 said:**
> Please help with this error. I'm pissed looking for solutions which does not exist or they write in other langs than english.

while installing I get such error:
```
Log created 04-28-2009 at  9:17pm.



Setup was unable to add the following file to Z:\home\morfi\Warcraft III\War3.mpq:

    blizzard.ax

Error 0x85200069:  

(C:\temp\020606lockit\Installer\Source\MpqUtil.cpp:63)



Installation canceled.



```

More info about your system and install environment would be helpful. Why is wine trying to add a file to the Z (root folder) drive? Normally, it would just use C: (~/.wine/drive_c) instead.

---

### Post by Morfi777 on 2009-04-29
> **elitenoobboy said:**
> More info about your system and install environment would be helpful. Why is wine trying to add a file to the Z (root folder) drive? Normally, it would just use C: (~/.wine/drive_c) instead.

Hello! Thanks for the reply :)

I'm using Ubuntu 8.04 version, GNOME, Wine 1.1.20.

Well, I'm using: wine install.exe
Yes, I've chosen Z, but it is no matter.

I tried C:\ of course (choosing from the dir list of course in installation program) but I see exactly the same error :( 
It copy War3.mpq to the new folder = right, then some 2 files and ERROR.

When using PlayOnLinux I get the same error.



Cheers

---

### Post by rothi on 2009-06-04
Hi, I've installed Ubuntu 8.04 today.
My machine is a HP Compaq 6715s
with 2G RAM and ati x1250 Graphiccard

I installed the native Graphicdrivers form the ati-support page.
And I installed wine and added to HKEY_CURRENT_USER/Software/Wine/Direct3D 
the DirectDrawRenderer->opengl and VideoMemorySize->256

Well the game runs fine, so this will maybe help someone.

I have a problem too. When I start a BNet server nobody can enter it.
Ports are opened and ok, for it works fine with WindowsXP.

Any suggestions how to get my Servers accessable?

thx rothi

---

### Post by balgaltz on 2009-06-06
It's probably the AcceptEx problem, it is needed for hosting.
[http://bugs.winehq.org/show_bug.cgi?id=9787](http://bugs.winehq.org/show_bug.cgi?id=9787)
**Check out the comment #370 from Nephyrin zey.**
You might wanna check [http://bugs.winehq.org/show_bug.cgi?id=17809](http://bugs.winehq.org/show_bug.cgi?id=17809) as well because without that patch you will get FATAL_ERROR in BNet Chatroom.

**Patches:**
[http://wiki.winehq.org/Patching](http://wiki.winehq.org/Patching)
***_AcceptEx_***
> [http://bugs.winehq.org/attachment.cgi?id=20300](http://bugs.winehq.org/attachment.cgi?id=20300)
***_secur32: Disable schannel InitializeSecurityContextW._***
> [http://bugs.winehq.org/attachment.cgi?id=20360](http://bugs.winehq.org/attachment.cgi?id=20360)


I compiled wine 1.1.22 with both patches like Nephyrin zey, it works great.
During the compilation you might get an error (I don't remember what it stated),
just do:
> ./tools/make_requests


Use **Snoopy** as Banlist.
Tried with others, jw3banlist aka Bancraft, BW3Ban(couldnt compile / didnt know)
But the best so far is **Snoopy**.  The others were buggy or presented problems.
I use 64bit Jaunty and had to compile **Snoopy (2.9.99.4b)**
[http://snoopy.tuxfamily.org/](http://snoopy.tuxfamily.org/)

Reply back if you want to ask anything about compiling it.

---

### Post by Gosujii-sama on 2009-07-07
yah i started a post didnt find this till after doing schannel searches and stuff.
Issue is with the war3 wine schannel to compile it it needs the latest gnutls-dev however
configure: error: libgnutls development files not found, no schannel support.
This is an error since --with-gnutls was requested.

is the error.

sudo apt-get install libgnutls-dev
[sudo] password for construct: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgnutls-dev is already the newest version.

shows i have the latest version so why cant it compile?
i386 ubuntu 8.04 hardy

---

### Post by Samangh84 on 2009-07-08
Hi everyone,
thanks for all your help.
I installed Wc3 and its working fine, but after i connect to battle.net i get a fatal error.
is there any way to fix that?

---

### Post by elitenoobboy on 2009-07-08
You will need to compile wine from source, as per the instructions here: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3126](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3126)

---

### Post by Gosujii-sama on 2009-07-08
Any news on my post about the libgnutls-dev issue?

---

### Post by balgaltz on 2009-07-25
**Patching and Compiling wine.**
First, you need to get latest source of wine.
[https://sourceforge.net/projects/wine/files/]("https://sourceforge.net/projects/wine/files/")
Although, when you are reading this the latest source might have the implementations.

But this guide will be for 1.1.26.
In case you don't want to search for it, I mirrored the source in the following link.
[https://sourceforge.net/projects/balgaltzwc3/files/]("https://sourceforge.net/projects/balgaltzwc3/files/")
After downloading it, extract the folder.
In the folder (**wine-1.1.26**), download the patches from the link before.
dinput.patch, **acceptex.patch** and **schannel.patch**

***_PATCHING_***
*MUST*
From a Terminal/Console go to the folder.
```
patch -p1 < acceptex.patch
```
Connection stuff with Bnet.
[http://bugs.winehq.org/show_bug.cgi?id=9787]("http://bugs.winehq.org/show_bug.cgi?id=9787")

```
patch -p1 < schannel.patch
```
No more crash when idle in a Channel!.
[http://bugs.winehq.org/show_bug.cgi?id=17809](http://bugs.winehq.org/show_bug.cgi?id=17809)


*Optional*
```
patch -p1 < dinput.patch
```
dinput: option to force mouse warp when on the edge of the screen
Set [HKCU\Software\Wine\DirectInput] "MouseWarpOverride" to
"force_edge" to enable this hack.

*_**Compiling.**_*
Dependencies, 
```
sudo apt-get build-dep wine
```

While still in the folder with the Terminal/Console
```
./configure
```
```
make depend && make
```
Right now, you can try the build
Executing in a Terminal.
```
/home/balgaltz/wine-1.1.26/wine "C:\Program Files\Warcraft III\Frozen Throne.exe"
```
Remember to replace *balgatz* in the code above, with your user.
By the way, I extracted the wine-1.1.26 folder to my home folder.
So if it works, and want to install this wine build.
```
sudo make install
```
Once installed, to test.
```
wine "C:\Program Files\Warcraft III\Frozen Throne.exe"
```

**For an application like Banlist**
You can use Snoopy, [http://snoopy.tuxfamily.org/]("http://snoopy.tuxfamily.org/")
You might need to compile it from source, like I did (I use **64Bit**) but I don't remember the dependencies atm.
You need to get them from Synaptic.
**libpcap0.8-dev**, **xclip**, **libgeoip-dev**.

**References:**
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3126](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3126)
[http://repo.or.cz/w/wine/hacks.git](http://repo.or.cz/w/wine/hacks.git)

---

### Post by pantera10 on 2009-09-01
alright...so i tried running war3 thru wine on my HP laptop with a intel 965 ...and i must say the game ran horribly...it was like i was running space invaders !!...i couldnt see the mouse...the whole application lagged like it had been purged a billion times....

help ?

---

### Post by elitenoobboy on 2009-09-01
> **pantera10 said:**
> alright...so i tried running war3 thru wine on my HP laptop with a intel 965 ...and i must say the game ran horribly...it was like i was running space invaders !!...i couldnt see the mouse...the whole application lagged like it had been purged a billion times....

help ?
How do other 3d games run on the laptop? Both in ubuntu and windows.

---

### Post by pantera10 on 2009-09-05
well i havnt really played any other game on ubuntu yet...but Red Alert 3 , C&C : kanes wrath and War 3 used to work fine on windows...

i did the wine war3 - opengl  command..and well i got the graphics all set..no more space invaders....but the game is still damn slowwww...like really slow....i woudlve pasted the erorrs i get after typing in the war3 -opengl command but i forgot what they were...
something to do with cannot change BPP from 32 to 16...and a few lines starting with FIXED...i'll get them next time i log in...
is it cause my i965 isnt supported by ubuntu ??

---

### Post by elitenoobboy on 2009-09-05
> **pantera10 said:**
> 
something to do with cannot change BPP from 32 to 16...and a few lines starting with FIXED...i'll get them next time i log in...
is it cause my i965 isnt supported by ubuntu ??

It would help to follow the instructions about the intro movies from the wine appdb site. [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3126](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3126)

---

### Post by JakcV on 2009-09-17
I can play the war3 with no lag, but everytime i have to switch off the compiz effect function in order to play it. If i did not switch off, i will restart the Xorg. 
It is troublesome, since i need to reactive it and set back the setting. 
Intrepid 64 bit, with the newest WINE from the mirror at the official site. wine.budgetdedicate.com

---

### Post by Zaggy on 2009-09-19
Thanks balgaltz, that tutorial made me able to host again!
Although running snoopy and doing the "/refresh start 5" command crashes warcraft  :(

[http://pastebin.com/m56dda5f7](http://pastebin.com/m56dda5f7)

---

### Post by arto7177 on 2009-10-28
When I start up Warcraft III using wine war3.exe -opengl the game starts up but immediately random parts of the main menu of Warcraft appear and disappear rapidly with the Desktop being visable most of the time. The buttons on main menu respond like they shoud(clicking them switches to whatever I chose) but the flickering does not go away. I have an radeon x1200 which does not have a currently working proprietary driver, so i am using the open source one. 
The terminal returns
```
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32f244,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f624,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x160028,0x1643a8): stub
```If you need anymore information please ask, I am running on 9.10.

---

### Post by vexorian on 2009-10-28
definitely a driver issue, too bad.

try with -window just in case, also try without -opengl.

---

### Post by arto7177 on 2009-10-28
I tried both but still nothing, while doing some research I realized I do not have an xorg.conf file which should be setting my driver for my video card, i was wondering if that could maybe be the issue.

---

### Post by elitenoobboy on 2009-10-28
> **arto7177 said:**
> I tried both but still nothing, while doing some research I realized I do not have an xorg.conf file which should be setting my driver for my video card, i was wondering if that could maybe be the issue.
How do other 3d games play in ubuntu?

---

### Post by vexorian on 2009-10-28
> **arto7177 said:**
> I tried both but still nothing, while doing some research I realized I do not have an xorg.conf file which should be setting my driver for my video card, i was wondering if that could maybe be the issue.
on normal circumstances, you don't need to tweak xorg.conf manually, but I guess you may try now that things are not normal.

---

### Post by randomguy1 on 2009-11-07
I didnt actually read through the whole thread, so sorry if someone has already mentioned this:
If you run wc3 with the latest wine in -opengl and not windowed you'll expierence that when you alt tab it's no problem to get to the desktop but you cant get into wc3 by clicking on the icon in the panel.
However there is a way way to get back into wc3 again. You simply need to click on your wc3 -opengl launcher again. It will give you an error message saying "warcraft III is already running", and if you click ok you're in the game again.
Tested on ubuntu 9.10 and wine 1.1.32

---

### Post by suzenon on 2009-11-29
Hello.
I'm running warcraft ver 1.24b on wine 1.1.33. My os is 64bit Ubuntu 9.10.
I suffer from my mouse pointer not quite moving screen while moving mouse to the edge. Also i see part (like 10px) of my gnome while playing, however starting a game in -opengl mode fixes the problem.
I still got issue with this mouse on edge of the screen thing. Weird thing is it's working perfectly on top and bottom edge and partialy on left and right edge. By partialy i mean it sometimes makes the screen to move and sometimes not. It's very annyoing playing dota. I have this directx mice option in winecfg checked.

Any clue if this howto below could fix the issue? The part about dinput patch seems like it could resolve my problem. Will i have to delete/uninstall my current wine before patching and compiling this one? Or this patch is already in 1.1.33 version? Or i get all this wrong even?

> **balgaltz said:**
> **Patching and Compiling wine.**
First, you need to get latest source of wine.
[https://sourceforge.net/projects/wine/files/](https://sourceforge.net/projects/wine/files/)
Although, when you are reading this the latest source might have the implementations.

But this guide will be for 1.1.26.
In case you don't want to search for it, I mirrored the source in the following link.
[https://sourceforge.net/projects/balgaltzwc3/files/](https://sourceforge.net/projects/balgaltzwc3/files/)
After downloading it, extract the folder.
In the folder (**wine-1.1.26**), download the patches from the link before.
dinput.patch, **acceptex.patch** and **schannel.patch**

***_PATCHING_***
*MUST*
From a Terminal/Console go to the folder.
```
patch -p1 < acceptex.patch
```Connection stuff with Bnet.
[http://bugs.winehq.org/show_bug.cgi?id=9787](http://bugs.winehq.org/show_bug.cgi?id=9787)

```
patch -p1 < schannel.patch
```No more crash when idle in a Channel!.
[http://bugs.winehq.org/show_bug.cgi?id=17809](http://bugs.winehq.org/show_bug.cgi?id=17809)


*Optional*
```
patch -p1 < dinput.patch
```dinput: option to force mouse warp when on the edge of the screen
Set [HKCU\Software\Wine\DirectInput] "MouseWarpOverride" to
"force_edge" to enable this hack.

*_**Compiling.**_*
Dependencies, 
```
sudo apt-get build-dep wine
```While still in the folder with the Terminal/Console
```
./configure
``````
make depend && make
```Right now, you can try the build
Executing in a Terminal.
```
/home/balgaltz/wine-1.1.26/wine "C:\Program Files\Warcraft III\Frozen Throne.exe"
```Remember to replace *balgatz* in the code above, with your user.
By the way, I extracted the wine-1.1.26 folder to my home folder.
So if it works, and want to install this wine build.
```
sudo make install
```Once installed, to test.
```
wine "C:\Program Files\Warcraft III\Frozen Throne.exe"
```**For an application like Banlist**
You can use Snoopy, [http://snoopy.tuxfamily.org/](http://snoopy.tuxfamily.org/)
You might need to compile it from source, like I did (I use **64Bit**) but I don't remember the dependencies atm.
You need to get them from Synaptic.
**libpcap0.8-dev**, **xclip**, **libgeoip-dev**.

**References:**
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3126](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3126)
[http://repo.or.cz/w/wine/hacks.git](http://repo.or.cz/w/wine/hacks.git)

---

### Post by balgaltz on 2009-11-29
Sup, yeah, the dinput patch could resolve it, I would recommend building a wine with the patches and testing it before uninstalling/replacing your current wine build.
However, I read somewhere that it happens if you are using "Desktop Cube" in Compiz, so try switching to "Desktop Wall" for an instance.

---

### Post by suzenon on 2009-11-29
Wow mate! Thanks a lot it seems to work, turned desktop tube off and it seems to work nicely.

One more thing, how do you make to work alt+tab with warcraft etc. ?

---

### Post by balgaltz on 2009-11-29
There's a trick for that, you can only switch windows if the other window is full-screen. So I binded a key to full-screen, when Im in Warcraft, I alt-tab to the desired window and press the key to make it full-screen, and it will appear, then to go back to Warcraft, just alt-tab to it or unfull-screen the previous window.

Keyboard shortcuts is where you bind it.

---

### Post by suzenon on 2009-11-30
I don't get it. When you alt tab to desired window, can it be anything like terminal? Maybe i really don't get it right, but when i alt tab my warcraft just freezes like that:
[[IMG]http://img37.imageshack.us/img37/493/zrzutekranuh.th.png[/IMG]]("http://img37.imageshack.us/i/zrzutekranuh.png/")
And i can't do anything to restore it. Or it's as it should be and i'm doing it wrong?

---

### Post by balgaltz on 2009-11-30
Ok try this:
Warcraft in fullscreen
Alt Tab to the terminal
   (You wont be able to see the terminal yet if it isnt in fullscreen)
Press key to make a window change to fullscreen
   (Assign it in "Keyboard Shortcuts")
Terminal will appear in fullscreen and you will able to see it.

Then you just Alt Tab to Warcraft whenever you want to go back.

---

### Post by suzenon on 2009-12-01
> **balgaltz said:**
> Ok try this:
Warcraft in fullscreen
Alt Tab to the terminal
   (You wont be able to see the terminal yet if it isnt in fullscreen)
Press key to make a window change to fullscreen
   (Assign it in "Keyboard Shortcuts")
Terminal will appear in fullscreen and you will able to see it.

Then you just Alt Tab to Warcraft whenever you want to go back.

Hey, thanks for answer but i'm doing it exacly like that and it's not working for me. My guess is i got something wrong with my os/wine/war config. It just don't want to unfreeze (and get back to fullscreen) when i alt tab from for example terminal.
btw.
is getting such errors just after starting the game is normal?
```
err:ole:CoCreateInstance apartment not initialised
fixme:win:EnumDisplayDevicesW ((null),0,0x33f160,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5e4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f61c,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x166530,0x16a570): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x166530,0x16a570): stub

```

---

### Post by balgaltz on 2009-12-01
Yeah, I get those errors too.
I recorded a video. Hope its self explanatory.
[http://www.youtube.com/watch?v=8o14A0UzKJI](http://www.youtube.com/watch?v=8o14A0UzKJI)

Just in case:
I used gtk-recordmydesktop to record it.

---

### Post by suzenon on 2009-12-02
I really appreciate your efforts, but it's not working for me. 
However i'm running the game in "opengl" mode. Haven't noticed if you're running it in this mode too.
But!
If i start warcraft normally (without -opengl) alt tab is working just fine. So why i'm running it in opengl? If i'm not using opengl i can see gnome panels on my warcraft window, like that:
[[IMG]http://img10.imageshack.us/img10/5817/zrzutekranu1l.th.png[/IMG]](http://img10.imageshack.us/i/zrzutekranu1l.png/)
I'll look into it and try to eliminate view of my panels while game is running...

---

### Post by balgaltz on 2009-12-02
wine "C:\Program Files\Warcraft III\Frozen Throne.exe"
Nop, I don't run it with opengl.
Btw, I tried with opengl after I Alt Tabbed, I could see the panels, then when I AltTabbed back to Warcraft, here's a screenshot.
[[IMG]http://img18.imageshack.us/img18/4121/afteralttab.th.png[/IMG]](http://img18.imageshack.us/i/afteralttab.png/)

---

### Post by suzenon on 2009-12-02
Hehe, looks like something isn't quite fine with opengl mode. My game just freezes for good.
Anyway, i have no clue why i see these damn panels, but it's possible to hide them with button option in panel properties. So it's kina working because i only see two little buttons instead of not seeing my resources status etc. :)

And hey, thanks again for your help.

---

### Post by balgaltz on 2009-12-02
:D, you are welcome.  Happy gaming, XD.

---

### Post by suzenon on 2009-12-08
In matter of my problems i had with part of gnome panels visible when playing warcraft 3. I've noticed best option is to turn off compiz completely. Easiest way to achive that is by installing compiz switch ( [http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch) ) and adding it to panel (i'm using polish version of ubuntu, so step names are pobably not quite accurate, but everyone should figure it out;) ) Right click panel -> Add to panel -> New program launcher -> Accessories -> Compiz-switch
Then all you need to do is click it before launching warcraft.

Hope this will be helpful to anybody. ;)

---

### Post by JakcV on 2009-12-21
```
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\DATA\\dota\\Storm.dll") not found
err:module:import_dll Library Storm.dll (which is needed by L"Z:\\media\\DATA\\dota\\War3.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\DATA\\dota\\War3.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\DATA\\dota\\War3.exe" failed, status c0000135

```

Last month, i can run war3 with patch 1.21. However, after i upgrade the patch of war3 to 1.24b at Vista, then I cannot run it any more. 
On the output, I think the patch install some dll into the window system. I am not very sure, I hope can get the answer here. Thanks.

Distro: Ubuntu 9.10 64bit
Kernel: 2.6.31
Wine: 1.0.1

---

### Post by Togras on 2009-12-31
I worked through balgaltz Howtodo and warcraft starts 
but it was really super slow
```
wine "C:\Programme\Warcraft III\Frozen Throne.exe"
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33f284,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f658,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f264,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
martin@martin-desktop:~$ fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x161778,0x161700): stub
martin@martin-desktop:~$ wine "C:\Programme\Warcraft III\Frozen Throne.exe"
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33f284,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f658,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f264,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
martin@martin-desktop:~$ fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x161778,0x161700): stub

```
so I am try -opengl
```
wine "C:\Programme\Warcraft III\Frozen Throne.exe" -opengl
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33f284,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f63c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f674,0x00000000), stub!
martin@martin-desktop:~$ fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1465d0,0x14c558): stub
```
so the menu works fine but i am not able to type anything

if anyone have a idea what iam doing wrong please tell it ;)

---

### Post by Togras on 2010-01-09
okay i find a to fix my problem 
```
WINEDEBUG=-all wine explorer /desktop=foo,1280x720 "C:\Programme\Warcraft III\Frozen Throne.exe"  -opengl
``` or
```
wine explorer /desktop=foo,1280x720 "C:\Programme\Warcraft III\Frozen Throne.exe"  -opengl
```
open warcraft in a window and now i can type...

---

### Post by Makmat on 2010-01-10
PROBLEM: I can startup game and all seems to be good speed and graphics,
but after a few seconds game exits. I encountered this:

fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
fixme:win:EnumDisplayDevicesW ((null),0,0x33f168,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f624,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x170768,0x16e7e8): stub
*********************************WARN_ONCE*********************************
File radeon_tcl.c function radeon_run_tcl_render line 499
Rendering was 1454 commands larger than predicted size. We might overflow  command buffer.
***************************************************************************
drmRadeonCmdBuffer: -22. Kernel failed to parse or rejected command stream. See dmesg for more info.


-> Could you help me fixxing this things ??
-> Do you have any questions about how i configured/installed the game?

For now, thanks.

---

### Post by Togras on 2010-01-10
2 questions 
1: witch driver you use? radeon or fglrx?

2: do you use the -opengl function?

at my pc it works fine with the call seen above and the fglrx driver

---

### Post by Makmat on 2010-01-10
1) radeon
2) yes on terminal i type "wine war3.exe -window -opengl"

-> note: they say that wine has problems with "ATI radeon" cards so i didnt try to use fglrx driver, but if u tell it goes i can try to get it...

---

### Post by Togras on 2010-01-11
yes the best way would be to install wine according to balgaltz how do to (side 26)
(if you want you can use for this mwine see more under [http://wiki.ubuntuusers.de/Multi_Wine]("http://wiki.ubuntuusers.de/Multi_Wine") this in german but the commands are the same or try to translate this site....)

if it doesn't work test the fglrx-driver

good luck

---

### Post by Zubb[RU] on 2010-02-12
I have Asus K40AB notebook with Radeon HD 4570, i run war3 succesfully (no lag) but about 10 minutes into the game it crashes every time, i'm not quite sure waht is the problem ...
```
danya@danya-laptop:~$ wine "C:\Program Files\Warcraft III\Frozen Throne.exe" -opengl
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
fixme:win:EnumDisplayDevicesW ((null),0,0x33f384,0x00000000), stub!
err:wgl:X11DRV_wglGetPixelFormatAttribivARB unexpected RenderType(8)
err:wgl:X11DRV_wglGetPixelFormatAttribivARB unexpected RenderType(8)
fixme:win:EnumDisplayDevicesW ((null),0,0x33f64c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f684,0x00000000), stub!
danya@danya-laptop:~$ mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
err:wave:wodOpen Error open: Input/output error
fixme:dsound:mmErr Unknown MMSYS error 3
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
err:wave:wodOpen Error open: Input/output error
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
err:wave:wodOpen Error open: Input/output error
fixme:secur32:schan_InitializeSecurityContextA stub
fixme:mswsock:AcceptEx (listen=16736, accept=16764, 0x2cd00c0, 0, 32, 32, 0x33f4fc, 0x2cd0090), not implemented
fixme:mswsock:AcceptEx (listen=16736, accept=16768, 0x2cd0148, 0, 32, 32, 0x33f4fc, 0x2cd0118), not implemented
fixme:mswsock:AcceptEx (listen=16736, accept=16772, 0x2cd01d0, 0, 32, 32, 0x33f4fc, 0x2cd01a0), not implemented
fixme:mswsock:AcceptEx (listen=16736, accept=16776, 0x2cd0258, 0, 32, 32, 0x33f4fc, 0x2cd0228), not implemented
fixme:mswsock:AcceptEx (listen=16736, accept=16780, 0x2cd02e0, 0, 32, 32, 0x33f4fc, 0x2cd02b0), not implemented
fixme:mswsock:AcceptEx (listen=16736, accept=16784, 0x2cd0368, 0, 32, 32, 0x33f4fc, 0x2cd0338), not implemented
fixme:mswsock:AcceptEx (listen=16736, accept=16788, 0x2cd03f0, 0, 32, 32, 0x33f4fc, 0x2cd03c0), not implemented
fixme:mswsock:AcceptEx (listen=16736, accept=16792, 0x2cd0478, 0, 32, 32, 0x33f4fc, 0x2cd0448), not implemented
fixme:mswsock:AcceptEx (listen=16736, accept=16796, 0x2cd0500, 0, 32, 32, 0x33f4fc, 0x2cd04d0), not implemented
fixme:mswsock:AcceptEx (listen=16736, accept=16800, 0x2cd0588, 0, 32, 32, 0x33f4fc, 0x2cd0558), not implemented
fixme:mswsock:AcceptEx (listen=16736, accept=16804, 0x2cd0610, 0, 32, 32, 0x33f4fc, 0x2cd05e0), not implemented
fixme:mswsock:AcceptEx (listen=16736, accept=16808, 0x2cd0698, 0, 32, 32, 0x33f4fc, 0x2cd0668), not implemented
fixme:mswsock:AcceptEx (listen=16736, accept=16812, 0x2cd0720, 0, 32, 32, 0x33f4fc, 0x2cd06f0), not implemented
fixme:mswsock:AcceptEx (listen=16736, accept=16816, 0x2cd07a8, 0, 32, 32, 0x33f4fc, 0x2cd0778), not implemented
fixme:mswsock:AcceptEx (listen=16736, accept=16820, 0x2cd0830, 0, 32, 32, 0x33f4fc, 0x2cd0800), not implemented
fixme:mswsock:AcceptEx (listen=16736, accept=16824, 0x2cd08b8, 0, 32, 32, 0x33f4fc, 0x2cd0888), not implemented
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:imm:ImmReleaseContext (0x30028, 0x13a7a0): stub
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:mswsock:AcceptEx (listen=16736, accept=16596, 0x2cd00c0, 0, 32, 32, 0x33f548, 0x2cd0090), not implemented
fixme:mswsock:AcceptEx (listen=16736, accept=16600, 0x2cd0148, 0, 32, 32, 0x33f548, 0x2cd0118), not implemented
fixme:mswsock:AcceptEx (listen=16736, accept=16760, 0x2cd01d0, 0, 32, 32, 0x33f548, 0x2cd01a0), not implemented
fixme:mswsock:AcceptEx (listen=16736, accept=16764, 0x2cd0258, 0, 32, 32, 0x33f548, 0x2cd0228), not implemented
fixme:mswsock:AcceptEx (listen=16736, accept=16768, 0x2cd02e0, 0, 32, 32, 0x33f548, 0x2cd02b0), not implemented
fixme:mswsock:AcceptEx (listen=16736, accept=16772, 0x2cd0368, 0, 32, 32, 0x33f548, 0x2cd0338), not implemented
fixme:mswsock:AcceptEx (listen=16736, accept=16776, 0x2cd03f0, 0, 32, 32, 0x33f548, 0x2cd03c0), not implemented
fixme:mswsock:AcceptEx (listen=16736, accept=16780, 0x2cd0478, 0, 32, 32, 0x33f548, 0x2cd0448), not implemented
fixme:mswsock:AcceptEx (listen=16736, accept=16784, 0x2cd0500, 0, 32, 32, 0x33f548, 0x2cd04d0), not implemented
fixme:mswsock:AcceptEx (listen=16736, accept=16788, 0x2cd0588, 0, 32, 32, 0x33f548, 0x2cd0558), not implemented
fixme:mswsock:AcceptEx (listen=16736, accept=16792, 0x2cd0610, 0, 32, 32, 0x33f548, 0x2cd05e0), not implemented
fixme:mswsock:AcceptEx (listen=16736, accept=16796, 0x2cd0698, 0, 32, 32, 0x33f548, 0x2cd0668), not implemented
fixme:mswsock:AcceptEx (listen=16736, accept=16800, 0x2cd0720, 0, 32, 32, 0x33f548, 0x2cd06f0), not implemented
fixme:mswsock:AcceptEx (listen=16736, accept=16804, 0x2cd07a8, 0, 32, 32, 0x33f548, 0x2cd0778), not implemented
fixme:mswsock:AcceptEx (listen=16736, accept=16808, 0x2cd0830, 0, 32, 32, 0x33f548, 0x2cd0800), not implemented
fixme:mswsock:AcceptEx (listen=16736, accept=16812, 0x2cd08b8, 0, 32, 32, 0x33f548, 0x2cd0888), not implemented
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:imm:ImmGetOpenStatus (0x13a7a0): semi-stub
fixme:ntdll:FILE_GetNtStatus Converting errno 12 to STATUS_UNSUCCESSFUL
fixme:ntdll:FILE_GetNtStatus Converting errno 12 to STATUS_UNSUCCESSFUL
fixme:ntdll:FILE_GetNtStatus Converting errno 12 to STATUS_UNSUCCESSFUL
fixme:ntdll:FILE_GetNtStatus Converting errno 12 to STATUS_UNSUCCESSFUL
fixme:ntdll:FILE_GetNtStatus Converting errno 12 to STATUS_UNSUCCESSFUL
fixme:ntdll:FILE_GetNtStatus Converting errno 12 to STATUS_UNSUCCESSFUL
fixme:ntdll:FILE_GetNtStatus Converting errno 12 to STATUS_UNSUCCESSFUL
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x63da4dc9

```

---

### Post by Zubb[RU] on 2010-02-15
Can someone please explain newbie what can cause all those problems? :oops:

---

### Post by elitenoobboy on 2010-02-15
> **'Zubb[RU] said:**
> Can someone please explain newbie what can cause all those problems? :oops:

What wine version are you running it on? If you are running it on a current version, you could try an older version to see if that helps, as wine sometimes has regressions. Do other 3d programs run reliably? Do other wine 3d games run reliably?

---

### Post by Zubb[RU] on 2010-02-17
Thank you, i will try and report.

---

### Post by bakerqj on 2010-03-08
Hey, I'm on karmic 9.10 and I installed War3 fine through wine, audio and video work great, but now when I'm playing on battlenet when it goes to launch a game sometimes it will end the process. I think it's from the windows feature of pulling up the game when you Alt-Tab out of it but it's really annoying! Not to mention hurting my record. It'll find the game but then end process when the game starts loading. Is there a file I an delete to stop it from doing this or a wine configuration which will help. I'm running wine 1.1.40. I can always get the first game to work great but most of the time the second game I try to play it kicks me. Any suggestions, I'd appreciate it. Thanks

---

### Post by bakerqj on 2010-03-09
Seriously.... I might just go buy windows because linux wont play this game. On battlenet it kicks me out all the time! And it's only when I'm launching a game. It will completely end the process of Warcraft 3 with no error dialogue at all. Then it goes as a loss on my record. Anyone else encountering this problem or know how to fix it? Also when I arrange team it seems to kick me out more than usual. With normal games, I'd say it launches the game 50% of the time but with arrange team 25%. Why the difference? It's almost like I spend more time reloading the game because it kicked me out than I do playing it. I don't want to pay money for all of the windows software. I like linux and warcraft 3 anyone know how to get the two to run together smoothly? All the "how-to"'s on this site seem to be outdated. I had it working better but not perfect on my last build and I had to wipe my hard drive and I just can't seem to get it working quite right again. Would LOVE any help! Thanks

---

### Post by Dutchman on 2010-03-14
Same problem here, after about 20 minutes playing I'm randomly kicked out of the game. On previous Ubuntu versions i never had this problem. And this is not something that's only with wine. This show me that Ubuntu is still not ready for a main stream market. Why?

Step 1: Make things work.
**Step 2: IF THINGS WORK, MAKE SURE THEY KEEP WORKING.**

Step 2 is where ubuntu fails TERRIBLY. Over and over again I see that (stable!) updates of software lead to problems that were already solved earlier. And this goes even for kernel updates (ubuntu 9.04 netbook webcam works fine, ubuntu 9.10 system freezes when i enable webcam). THIS IS REALLY ANNOYING AND DOES NOT BIND CUSTOMERS TO UBUNTU GUYS!

(because it happens over and over again). FIX IT

---

### Post by marco.cervantes on 2010-04-21
I cant get Warcraft III to run under Wine. I have the original cdsm and keys. I am using Compiz and when i disble and run war3.exe its very VERY lagy. yes i do use -opengl. What might be the problem? im even thinking of just VM'ing it but i dont like VMs much.

---

