---
title: "Need ubuntu fix on my sony vaio(Heating issues)"
date: 2014-07-19
forum: New to Ubuntu
---

### Post by srinath3 on 2014-07-19
[COLOR=#000000]My systems configuration -> [/COLOR]
[COLOR=#000000]Operating System: Windows 7 Home Basic 32-bit (6.1, Build 7600) (7600.win7_rtm.090713-1255)Language: English (Regional Setting: English)[/COLOR]
[COLOR=#000000]System Manufacturer: Sony Corporation[/COLOR]
[COLOR=#000000]System Model: VPCEA23EN[/COLOR]
[COLOR=#000000]BIOS: BIOS Date: 09/23/09 11:58:43 Ver: 08.00.10[/COLOR]
[COLOR=#000000]Processor: Intel(R) Core(TM) i3 CPU M 350 @ 2.27GHz (4 CPUs), ~2.3GHz[/COLOR]
[COLOR=#000000]Memory: 3072MB RAM[/COLOR]
[COLOR=#000000]Available OS Memory: 2990MB RAM

[/COLOR][COLOR=#000000]If someone has this system and have been able to work with linux/ubuntu without any heating issues , please tell me the fix.[/COLOR][COLOR=#000000]
[/COLOR]

---

### Post by Rob Sayer on 2014-07-20
What ubuntu version are you using?  Is it 32 or 64 bit?  It's hard to impossible to tell without that.

My first impulse with this sort of thing would be to see if there's a video card issue.  A quick search found that it uses the Radeon HD 5145 gpu, but those things aren't always correct.  Some ubuntu users seem to have had power issues with that card.

But since that isn't necessarily the actual card, open the terminal and enter:

```
sudo lshw -C video
```

and copy and paste the result here, embedded in [CODE] tags so it's easier to read.

---

