---
title: "Bash script to check if process has completed?"
date: 2009-02-22
forum: Programming Talk
---

### Post by Ng Oon-Ee on 2009-02-22
Hi all,

I've been trying out Conky, and am running compiz. I guess most of you would know that Conky must be auto-started with some delay to shift it to AFTER compiz starts, so that the window blends in properly with the desktop background.

However, I'm thinking this would cause unnecessary problems in future if I want to shift my configuration to another faster (or slower) machine, having to change the delay (sleep) again. Or if I add more startup processes, potentially slowing down compiz starting.

So, anyway, I'd like to alter my BASH script for starting up Conky. Currently it is as below:-

```
#! /bin/bash
until [ "$done" = "true" ]
do
	if [ "$(pidof compiz.real)" ]
	then
		conky -c /home/symlinked/Conky/conkymain &
		done="true";
	else
		done="false"
		sleep 5;
	fi
done
exit 0
```

Simple, of course. But it doesn't work as expected, the reason being the compiz.real (or compiz) process exists from the moment its initialized, and BEFORE compiz is really fully loaded.

So, without putting any sort of delay into this script, is there a way I can test the compiz.real process to see if its 'done its job'? Perhaps to see if its idle or what not?

Thanks for your assistance.

---

### Post by leewebb on 2009-02-28
Lookup *wait* in the manpages. You'll want to do [FONT="Courier New"]*wait $i*[/FONT] after you've started your background process and then you can do what you need to do.

---

### Post by Ng Oon-Ee on 2009-02-28
> **leewebb said:**
> Lookup *wait* in the manpages. You'll want to do [FONT="Courier New"]*wait $i*[/FONT] after you've started your background process and then you can do what you need to do.
"man wait" doesn't show me anything, but googling bash wait tells me that wait waits for background processes to complete or for some process to terminate. In this case, the processes compiz and compiz.real do not terminate, and I'm unsure how to check whether they complete.

From the compiz forums, I got a workaround, sending DBUS commands till no error is returned. Posted it up [here.]("http://forum.compiz-fusion.org/showthread.php?p=71428")

Thank you for your help, good sir.

---

