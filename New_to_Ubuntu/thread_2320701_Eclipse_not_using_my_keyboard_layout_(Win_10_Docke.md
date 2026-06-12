---
title: "Eclipse not using my keyboard layout (Win 10 Docker host, X11, sshd, eclipse)"
date: 2016-04-16
forum: New to Ubuntu
---

### Post by Stefan_Bhlmann on 2016-04-16
Hi all,

eclipse doesn’t use my Swiss-German keyboar layout. Please may someone help?

As I can’t narrow down the problem to a single component not sure what know-how is needed. Here my setup :
Windows 10 PC with X-Windows-Server Xming
Docker (Dockerfile attached)
Docker using debian or ubuntu in the FROM clause
sshd, jdk1.8.0_77 and eclipse 4.5.2 installed inside the container
Connecting to the container through SSH and X11 forwarding
On the terminal/bash the keyboard works fine
Eclipse starts an X-Widow sucessfully on my Windows-PC
BUT – AND THIS IS MY PROBLEM – In the eclipse editors my keyboard is not accepted (for example: pressing Shift-3 yields # instead of ***, shift 4 yields $ instead of ç … and so on**)
 
Where is my problem: Is it X-Windows-related, and Eclipse-issue, a docker problem or a general locale-configuration issue? Please help me to narrow down.

---

### Post by mustermann-23 on 2016-11-24
Hi [[COLOR=#000000]Stefan_Bhlmann[/COLOR]]("https://ubuntuforums.org/member.php?u=2028357"),

did you solve your problem in the mean time? I am facing the same problem, but under different circumstances. I guess it is Eclipse-related, because that is the only programme that does show such weird behaviour regarding input methods:
Sometimes it DOES allow me to switch to German, but very rarely and I couldn't figure when it does and when it doesn't. It may happen right in the middle of coding. It then also might just-as-well switch back to English...
I am running an all-English Ubuntu system on my laptop equipped with a German keyboard. I installed a secondary input method for using an external Taiwanese keyboard to write traditional Chinese. This works through first changing the keyboard layout to Taiwanese (which is equivalent to the US standard, I think) and then using the Chewing input method (Fcitx). But the standard setting is German and it always works just fine, except in Eclipse ](*,)
I realised that when I'm typing in some window where it's working fine, the symbol shows either a keyboard (when typing with German or Taiwanese ["English"] layout) or a Chinese character (when typing with Chewing input method) - but when I'm typing in Eclipse the symbol will change to Tux.
I tried running Eclipse with a German locale (LC_ALL=de_DE.utf8), but then it won't even start, just telling me something like "there was an error".

Any help would be highly appreciated :)

---

