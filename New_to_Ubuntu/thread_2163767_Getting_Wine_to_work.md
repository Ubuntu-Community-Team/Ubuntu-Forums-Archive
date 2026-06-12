---
title: "Getting Wine to work"
date: 2013-07-19
forum: New to Ubuntu
---

### Post by drivingmemad on 2013-07-19
Hi all,
Sorry to bother you but I seem to be a bit stuck trying to get wine to work.
Reason for Wine:
I need to print to a kodak ESP5250 AIO printer ... Cant find any Linux drivers for it

Results so far:
Installed Wine 1.4.1 OK from the Ubuntu software centre
Downloaded aio_installer.exe from Kodak
in Terminal I typed wine downloads/aio_install.exe
The installer kept stalling at Wine : Mono ....
Downloaded wine-mono-0.0.8.msi
In terminal I typed wine downloads/wine-mono-0.0.8.msi
Got error message BAD exe ...
Googled this and found a post that said I need to type winetricks dotnet20 at a command line
Typed the command line command which advised me mono wasnt installed and a browser window opened up at [http://download.cnet.com/Microsoft-NET-Framework-Redistributable-Package-x86/3000-10250_4-10726028.html](http://download.cnet.com/Microsoft-NET-Framework-Redistributable-Package-x86/3000-10250_4-10726028.html)
I downloaded dotnetfx.exe 
At the terminal I typed wine downloads/dotnetfx.exe and this completed successfully
Tried the command line to install mono for wine once again ... getting "BAD exe" still
Tried the command line wine downloads/aio_install.exe and I keep getting font related error messages (ie *FONTname *is missing installation will now end)

Any ideas? Or can somebody point me in the right direction.

Many thanks.
Drivingmemad

ps Oh! almost forgot. Im running:-
Ubuntu 13.04 
Dell Inspiron 1720 
4GB Ram
Intel Pentium Dual CPU T2370 @ 1.73GHz × 2 
 160GB HDD with tons of space

pps should I try Windows XP emulation instead of Windows 7, do you think that will make a difference?

---

### Post by Mark Phelps on 2013-07-19
You can't install Windows drivers using Wine -- it is not made to do that.  And, even if you could, they would not work -- because you need Linux drivers.

---

### Post by drivingmemad on 2013-07-20
Hi Mark,
Thanks for that, so the only solution is a print device with Linux drivers?
ie NOT my kodak printer.

---

### Post by Zill on 2013-07-20
drivingmemad: Does this thread help? ...
[LIST]
[*][Does a Kodak ESP3 printer work in Lucid?]("http://ubuntuforums.org/showthread.php?t=1507273")
[/LIST]

---

