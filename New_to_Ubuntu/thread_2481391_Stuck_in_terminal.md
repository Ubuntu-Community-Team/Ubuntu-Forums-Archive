---
title: "Stuck in terminal"
date: 2022-11-28
forum: New to Ubuntu
---

### Post by jekep2008 on 2022-11-28
Hi trying to get into the desktop OS when I turn on it boots to command I put my credentials and then left with a command line???

---

### Post by TheFu on 2022-11-28
Is there a graphical environment at all or just a console with text?

If there isn't any mouse pointer seen, then it is probably a console.  This would be what Ubuntu Server looks like. It is a Server OS, not a desktop.  If you want a desktop OS, then install a non-server version of whatever Linux you want.  I'd guess you installed the Server as the most likely problem based on the limited description supplied.

Typically, the GUI would be boot into on any desktop Ubuntu flavor and if that doesn't work, it wouldn't drop you into a Login prompt, but to a grub> screen because the system wasn't able to boot at all.

---

### Post by MAFoElffen on 2022-11-28
Post if this returns any results:
```

sudo apt list xserver-xorg-core | grep 'installed'

```
A Desktop Edition has that package installed by default...

If is doesn't then if
```

sudo apt list ubuntu-server* | grep 'installed'

```
...if that does not return any results, then you have Ubuntu Core installed. If you do get results, then Ubuntu Server Edition.

You can install or fix your GUI Desktop, based on the results you get back.

---

### Post by jekep2008 on 2022-11-28
I know it has a desktop I was in there some months ago but haven&#8217;t played with it in awhile.. I did run some commands back then but now trying to get back in I&#8217;ll try these suggestions and see what happens. When I start it it asks for a password I put that in then it has a boot up screen with an active mouse pointer that says setup on top right corner from there it goes to a command and asks for login and pass which I type in and then just a command line with l@l:~$ here is some of the text I was able to copy if the pic doesn&#8217;t work


[COLOR=#000000][FONT=UICTFontTextStyleBody]rasseures[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]I Last login: Mon Mov 28 C5:49:51 FST 2022 on ttyl[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]A Helcore to Ubunto 14.04.2 LIS (GNU/L inux 5.56.0-30-seneric 886_64)[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]& Documentation:[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]httos://help.ubuntu.com/[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]8 670 packages can de undaleo.[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]0 0 updates are security updetes.[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]1 101:*s Iscou[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]A Architesture:[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]0 CPU op-fiode (s) :[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]8 Bute Order:[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]O CPU(SI:[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]0 On-line CPU(s) list:[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]i Thread(s) per core:[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]a coreis) per socket:[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]8 Socket(s):[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]" HuMa nade(s):[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]y vendor I0:[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]9 CPU family:[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]H Hodel:[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]§ Steppingi[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]3 CPU MHZ:[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]a BOgOMIPS:[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]Y Virtualization:[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]J Lid cache:[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]J Lii cache:[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]J L2 cache:[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]" huMA nodeo cPU(s) :[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]1 101:*$[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]XD6 64[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]32-bi1, 64-bit[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]Little Endian[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]+[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]0-3[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]2[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]2[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]Authent iCARD[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]21[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]19[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]1400.000[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]4192.14[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]ICK[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]20&#1095;&#8364;&#1082;[/FONT][/COLOR]
[COLOR=#000000][FONT=UICTFontTextStyleBody]0-3[/FONT][/COLOR]

---

### Post by TheFu on 2022-11-28
14.04.2 support ended 3 yrs ago.
Time to get either a 20.04 or 22.04 installation working.

---

### Post by tea for one on 2022-11-28
> **jekep2008 said:**
> Helcore to Ubunto 14.04.2 LIS (GNU/L inux 5.56.0-30-seneric 886_64)
Are you using Ubuntu 14.04?
Is this the same problem as your previous thread from November 07 2021? [https://ubuntuforums.org/showthread.php?t=2468667](https://ubuntuforums.org/showthread.php?t=2468667)

---

### Post by jekep2008 on 2022-11-29
yea i tried both of those lines and it say apt does not have a stable DLI interface yet . use with caution in scripts

---

### Post by jekep2008 on 2022-11-29
yeah its the same system i was playin with a year ago

---

### Post by TheFu on 2022-11-29
> **TheFu said:**
> 14.04.2 support ended 3 yrs ago.
Time to get either a 20.04 or 22.04 installation working.

Still stands. It isn't worth any effort to deal with an unsupported OS.

---

### Post by MAFoElffen on 2022-11-29
And from the MOTD Banner, it 14.04 Server Edition. My recommends is install fresh with 20.04 or 22.04 Desktop Edition.

---

### Post by jekep2008 on 2022-11-29
Yea I get it just want to get to desktop get files off and move on thanks for all the help

---

### Post by MAFoElffen on 2022-11-29
If you not comfortable at command line being able to do that... You can boot it from a current Desktop LiveCD media to have a GUI and retrieve files from it, or do a backup... So you can migrate it to a current supported version.

---

### Post by jekep2008 on 2022-11-30
LiveCD media? Or a backup? I&#8217;m in the woods with that.. I have a wallet.dat on there I need to sync if I could get some good help getting back into the system there would be a decent reward for sure!!

---

