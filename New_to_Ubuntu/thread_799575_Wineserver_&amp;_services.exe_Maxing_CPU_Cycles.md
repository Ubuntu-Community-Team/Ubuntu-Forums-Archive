---
title: "Wineserver &amp; services.exe Maxing CPU Cycles"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by zeifertstc on 2008-05-19
I don't consider this to be a huge problem and it is looking like I'm about the only person that has happened to notice this issue when using wine. I can understand the increased fan speeds and use of resources (not to this extent, though) when actually running any number of different resource intensive Windows Apps, however, wineserver and services.exe ramp cpu cycles way up even when they should be mostly idle. After manually killing the processes, the fans slow down and the cpu cycles are freed up again. So, like I said, it's not a huge issue, but one that I'd like to see fixed sometime soon.

Computer Specs:

Intel Celeron D Core 2 Duo 3.33GHz
1Gb Ram
ATI X1650 256Mb Video Card
160Gb HD (use entire disk option when installing Ubuntu)
20Gb HD (backup drive)
Creative Audigy 24-bit surround sound audio card
Netgear wireless (software not currently installed, just hardware)

Wine Version:
wine_0.9.59-0ubuntu5_i386 (installed from Ubuntu Repositories available from fresh install)

Need more info? Let me know what I can provide for you.

Thanks for the assist.

P.S. Does anybody know how to clean up the Wine menu after uninstalling programs/games? I have left over menu entries even after navigating "C:\" and deleting directories (post uninstall).

---

### Post by sdennie on 2008-05-19
It's possible some Windows app isn't closing down correctly or is otherwise misbehaving.  You could try install the latest version of wine to see if it helps.  Instructions can be found here: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Also, I don't think it's possible for wine to cleanup the menu after you uninstall stuff.  You can do it manually by going to System->Preferences->Main Menu and then going to Wine and disabling the things you don't want.

---

### Post by koma77 on 2008-06-01
I also have this issue.
Whenever I start a piece of software through wine services.exe and wineserver starts chewing cycles.
I simply kill the processes (!) and then everything is back to normal.

But why are they started?
What are they?
Why do they suddenly misbehave?

---

### Post by sdennie on 2008-06-01
> **koma77 said:**
> I also have this issue.
Whenever I start a piece of software through wine services.exe and wineserver starts chewing cycles.
I simply kill the processes (!) and then everything is back to normal.

But why are they started?
What are they?
Why do they suddenly misbehave?

Wine is a linux implementation of the Windows API.  It's not unreasonable to think it would need to start some sort of persistent server to provide the same services that would be available on Windows.  Those services may randomly decide to misbehave because of a bug in wine or because they are properly trying to emulate The Windows Experience.

---

