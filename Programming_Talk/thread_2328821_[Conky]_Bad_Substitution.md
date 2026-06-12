---
title: "[Conky] Bad Substitution"
date: 2016-06-24
forum: Programming Talk
---

### Post by Runedog48 on 2016-06-24
Greetings, I'm attempting to use Conky to overlay information about my hardware. I've managed to modify the default Conky config to my liking, however there's one line that's giving me an error ( bad substitution ). The command works perfectly in terminal but not with Conky.

This is the line of code. I'm attempting to make a bar which is filled based on GPU load. The error is produced when I attempt to pipe the 'grep' output to 'awk' which is supposed to remove the percent sign from the string ( execbar does not seem to like percent signs ).
```

${execbar ${exec aticonfig --adapter=0 --od-getclocks | grep -i -o [0-9]% | awk 'sub(/%/, "")' } }

```

Output when using commands in terminal:
```

runedog48@ThomasTheTrain /etc/conky $ aticonfig --adapter=0 --od-getclocks | grep -i -o [0-9]%
0%
runedog48@ThomasTheTrain /etc/conky $ aticonfig --adapter=0 --od-getclocks | grep -i -o [0-9]% | awk 'sub(/%/, "")' 
0

runedog48@ThomasTheTrain ~ $ conky
Conky: desktop window (140002c) is subwindow of root window (9c)
Conky: window type - desktop
Conky: drawing to created window (0x3200001)
Conky: drawing to double buffer
sh: 1: Bad substitution

```

Side note: I've only started using Linux as my daily driver about 2 weeks ago ( used Windows my whole life ), but I've been programming for a while. I'm still getting used to the switch and there's a lot I don't know yet.

Any help would be greatly appreciated.

---

### Post by Habitual on 2016-06-24
Try sed, not awk?
```
aticonfig --adapter=0 --od-getclocks | grep -i -o [0-9]% | sed 's/\%//g'
```
or this should omit the "%" in the output to begin with,
```
aticonfig --adapter=0 --od-getclocks | grep -i -o [0-9]
``` 

Hope that helps.

---

### Post by Runedog48 on 2016-06-24
> **Habitual said:**
> Try sed, not awk? or this should omit the "%" in the output to begin with 

Thanks for the response. I received the same error when I substituted sed for awk. I cannot omit the "%" because I'm using it to search for the correct number.

---

### Post by Habitual on 2016-06-26
I dunno, sorry.

---

### Post by Runedog48 on 2016-06-27
It seems I was able to get it working by using an external shell script to echo the value, which seems to be Conky friendly.

Conky Config
```

${color grey}GPU Usage$color ( total: ${execp sh ~/scripts/getGPUTemp.sh}% )
${execbar '/home/runedog48/scripts/getGPUTemp.sh'}

```

getGPUTemp.sh
```

gpuload="$(aticonfig --adapter=0 --od-getclocks | grep -i -o [0-9]% | awk 'sub(/%/, "")')"
echo -n $gpuload

```

There seems to be a bit of lag between the bar and the text, but for the most part it works fine. ( Took me so long to figure this out that I don't even want to bother fixing it ).

Screenshot:
[IMG]https://dl.dropboxusercontent.com/u/19018188/Conky%20Overlay.png[/IMG]

I think the original problem was caused by the nested command substitutions, but I don't know exactly what was wrong.

---

### Post by Habitual on 2016-06-27
> **Runedog48 said:**
> It seems I was able to get it working by running by using an external shell script to echo the value, which seems to be Conky friendly.
Never done that! :tongue:
I have tons of "components" left on my hard drive even though I never use them, or conky {code} any more.
I definitely had to use shell.fu in [16 of them]("http://s771.photobucket.com/user/E522260/media/desktop_9_21_2010.png.html").

Good job and well done!

---

### Post by vasa1 on 2016-06-27
Won't```
grep -i -o [0-9]%
```only pick up a single digit?

---

