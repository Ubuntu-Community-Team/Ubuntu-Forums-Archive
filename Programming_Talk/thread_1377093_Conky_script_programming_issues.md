---
title: "Conky script programming issues"
date: 2010-01-09
forum: Programming Talk
---

### Post by Mahngiel on 2010-01-09
I am trying to get going on some script writing following the precedent set by a script I picked up. It's best if you read the coding first:

```

[COLOR=Navy]#! /bin/bash[/COLOR]
[COLOR=Red]function [COLOR=SeaGreen]net()[/COLOR]
{
   echo [COLOR=Teal]$connect[/COLOR] [COLOR=Magenta]'% Connection'[/COLOR]
}
function[COLOR=Lime] [COLOR=Green]mem[/COLOR][COLOR=SeaGreen]()[/COLOR][/COLOR]
{
   echo [COLOR=Teal]$ram [COLOR=Magenta]'total RAM'[/COLOR][/COLOR]
}[/COLOR]
 
[COLOR=Teal]connect[/COLOR]=$[COLOR=Red]([/COLOR]iwconfig wlan0[COLOR=Red]|grep[/COLOR] [COLOR=Magenta]'Link Quality='[/COLOR][COLOR=Red]|grep[/COLOR] [COLOR=Magenta]'='[/COLOR][COLOR=Red]|grep[/COLOR] --max-count=1 -o [COLOR=Magenta]'\=\([0-9]\+\)'[/COLOR][COLOR=Red]|grep[/COLOR] --max-count=1 -o [COLOR=Magenta]'\([0-9]\+\)'[/COLOR][COLOR=Red])[/COLOR]
[COLOR=Teal]ram[/COLOR]=$[COLOR=Red]([/COLOR]top[COLOR=Red]|grep[/COLOR] -m 1 [COLOR=Magenta]'Mem:'[/COLOR][COLOR=Red]|grep[/COLOR] [COLOR=Magenta]'total[/COLOR]'[COLOR=Red]|grep[/COLOR] --max-count=1 -o [COLOR=Magenta]'[0-9]\{4,\}'[/COLOR][COLOR=Red]|grep[/COLOR] -m 1 [COLOR=Magenta]'[0-9]\{4,\}'[/COLOR][COLOR=Red])[/COLOR] 
[COLOR=Red]pr[/COLOR]
    net [COLOR=Red]&&[/COLOR] mem

[COLOR=Red]exit[/COLOR] 0

```What this is supposed to do is output the percentage of network link quality, followed by my total ram memory.  If you terminal this information, you can see why it _*should*_ work:

```

[COLOR=DarkOrange][COLOR=Navy]king@mahngiel:~$[/COLOR] iwconfig wlan0[/COLOR]
wlan0     IEEE 802.11bg  ESSID:"goesh"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0F:61:FE:B3:B0   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
         [COLOR=DarkOrchid] Link Quality=60/70  Signal level=-50 dBm  Noise level=-66 dBm[/COLOR]
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[COLOR=Navy]king@mahngiel:~$[/COLOR] [COLOR=Black]iwconfig wlan0[/COLOR]|grep 'Link Quality='|grep '='|grep --max-count=1 -o '\=\([0-9]\+\)'|grep --max-count=1 -o '\([0-9]\+\)'
[COLOR=Red]57[/COLOR]

[COLOR=Navy]king@mahngiel:~$[/COLOR] [COLOR=DarkOrange]top[/COLOR]
top - 22:21:38 up 10:04,  3 users,  load average: 0.17, 0.23, 0.17
Tasks: 193 total,   1 running, 177 sleeping,  15 stopped,   0 zombie
Cpu(s):  2.5%us,  2.2%sy,  0.0%ni, 95.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
[COLOR=DarkOrchid]Mem:    505000k total,   469648k used,    35352k free,    38828k buffers[/COLOR]
Swap:  1485972k total,    19180k used,  1466792k free,   194056k cached

[COLOR=Navy]king@mahngiel:~$[/COLOR] top|grep -m 1 'Mem:'|grep 'total'|grep --max-count=1 -o '[0-9]\{4,\}'|grep -m 1 '[0-9]\{4,\}'
[COLOR=Red]505000[/COLOR]

```The problem is, [COLOR=Green]net()[/COLOR] will post display, but [COLOR=Green]mem()[/COLOR] has no output.

I don't know if it's due to how conky inherently defines its objects to call from, or what.  The way I see it, the conky variable for your net is [COLOR=Green]${wireless_link_qual_perc}[/COLOR], so there shouldn't be a reason why conky could understand the first script reference to [COLOR=DarkOrange]iwconfig wlan0[/COLOR].

Any input here would be greatly appreciated.

---

### Post by Brandon Williams on 2010-01-10
Is the line that reads 'pr' really in your script? That's the only thing that doesn't work for me, and I doubt it's expected to be there.

---

### Post by Mahngiel on 2010-01-10
> **Brandon Williams said:**
> Is the line that reads 'pr' really in your script? That's the only thing that doesn't work for me, and I doubt it's expected to be there.

Maybe not, but it does work.  Like I said, i'm new to this scripting idea.  Anyways, i plopped another net() in there so you can see the space is reserved...

---

### Post by kaivalagi on 2010-01-10
Can you just try this in a script file (/tmp/mem.sh):

```
#!/bin/sh
mem=`top|grep -m 1 'Mem:'|grep 'total'|grep --max-count=1 -o '[0-9]\{4,\}'|grep -m 1 '[0-9]\{4,\}'`
echo $mem
```

I am assuming your problem is that something like the above isn't outputting in conky? i.e. the below in a conkyrc:
```
[${execi 5 sh /tmp/mem.sh}]
```
This just gives this:
```
[]
```

If run at the command line you get something sensible:
```
4054116
```

I have other things on but I think you need to look at stdout redirection, so conky sees the output.

---

### Post by Mahngiel on 2010-01-10
> I think you need to look at stdout redirection, so conky sees the output.I'll take a read into this. Thanks for takin the time to respond.

---

### Post by Brandon Williams on 2010-01-10
OK ... I figured it out. The problem is that top requires access to a controlling terminal. When run within conky, it doesn't have that, so top fails. Run top in batch mode (with the -b switch) to get around this.

---

### Post by Mahngiel on 2010-01-11
> **Brandon Williams said:**
> OK ... I figured it out. The problem is that top requires access to a controlling terminal. When run within conky, it doesn't have that, so top fails. Run top in batch mode (with the -b switch) to get around this.

GENIOUS! Thank you so much for helping me figure this out. this works exactly right. 

Kudos.

---

### Post by kaivalagi on 2010-01-11
> **Brandon Williams said:**
> OK ... I figured it out. The problem is that top requires access to a controlling terminal. When run within conky, it doesn't have that, so top fails. Run top in batch mode (with the -b switch) to get around this.

> **Mahngiel said:**
> GENIOUS! Thank you so much for helping me figure this out. this works exactly right. 

Kudos.

Excellent, I must admit I had a quick look at redirecting output and still got messed about with what Brandon has highlighted

Good stuff to know...thanks Brandon!

---

