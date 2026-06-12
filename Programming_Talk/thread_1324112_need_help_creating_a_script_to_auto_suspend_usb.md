---
title: "need help creating a script to auto suspend usb"
date: 2009-11-12
forum: Programming Talk
---

### Post by Axx83 on 2009-11-12
Hi guys, last day I was tinkering with my laptop. Since karmic I decided to ditch laptop-mode and simply run the (very) few commands that laptop mode managed in a different way.

Let's start by saying that I don't know that much about programming.

About usb autosuspend:

I found on the internet these two scripts:
```
#!/bin/bash
for i in /sys/bus/usb/devices/*/power/level; do
	[ "$(cat $i)" = "auto" ] && continue
	echo "auto" > $i
done

for i in /sys/bus/usb/devices/*/power/autosuspend; do
	[ "$(cat $i)" -ge 0 2>/dev/null ] && continue
	echo "2" > $i
done
```
and
```
#!/bin/bash
for DEVICE in /sys/bus/usb/devices/*; do
  if [ -w $DEVICE/power/autosuspend ]; then
    echo 2 > $DEVICE/power/autosuspend
  fi

  if [ -w $DEVICE/power/level ]; then
    echo auto > $DEVICE/power/level
  fi
done
```
that basically say the usb bus to auto suspend and do it in 2 seconds, if I'm right.

I personally prefer the first, but again maybe I'm wrong.

Now I found in karmic that power manager runs some scripts in the folder /usr/lib/pm-utils/power.d/ running them with false when going to ac power and true when going to battery power.

like this
```
#!/bin/sh

path_mc="/sys/devices/system/cpu/sched_mc_power_savings"
path_smt="/sys/devices/system/cpu/sched_smt_power_savings"
val=0

case "$1" in
	true)
		echo "**sched policy powersave ON"
		val=1
		;;
	false)
		echo "**sched policy powersave OFF"
		val=0
		;;
esac

# Based on the values (1-enable, 0-disable) for these controls,
# sched groups cpu power will be determined for different domains.
# When power savings policy is enabled and under light load conditions,
# scheduler will minimize the physical packages/cpu cores carrying the
# load and thus conserving power

if [ -w "$path_mc" ] ; then
	echo $val > $path_mc
fi
if [ -w "$path_smt" ] ; then
	echo $val > $path_smt
fi

exit 0
```

How can I make the usb autosuspend script to do nothing when commanded false and run those echos when commanded true ?

Thanks a lot.

---

### Post by scragar on 2009-11-12
```
#!/bin/bash
if [ "$1" -eq "true" ]; then

  for i in /sys/bus/usb/devices/*; do
    if [ "$(cat $i/power/level)" != "auto" ]; then
      echo "auto" > $i/power/level
    fi;
    if [ "$(cat $i/power/autosuspend)" -ge 0 2>/dev/null ]; then
      echo "2" > $i/power/autosuspend
    fi
  done
fi
```

---

### Post by Axx83 on 2009-11-12
First of all thanks for the help.

Something doesn't work it seems:

```
/usr/lib/pm-utils/power.d/95hdparm-apm true: 
/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128
success.
/usr/lib/pm-utils/power.d/anacron true: stop: Unknown instance: 
success.
/usr/lib/pm-utils/power.d/laptop-mode true: success.
/usr/lib/pm-utils/power.d/sched-powersave true: **sched policy powersave ON
success.
/usr/lib/pm-utils/power.d/usb_autosuspend true: [: 12: Illegal number: true
success.
```

Taken from pm-powersave.log.

I have no idea what that means

---

### Post by scragar on 2009-11-12
OK, forget that, just use your old script(I tried mixing the two to get the best of both, clearly I broke something).
```

#!/bin/bash
if [ "$1" -eq "true" ]; then

  for i in /sys/bus/usb/devices/*/power/level; do
	[ "$(cat $i)" = "auto" ] && continue
	echo "auto" > $i
  done
  for i in /sys/bus/usb/devices/*/power/autosuspend; do
	[ "$(cat $i)" -ge 0 2>/dev/null ] && continue
	echo "2" > $i
  done
fi
```

---

### Post by Axx83 on 2009-11-12
Thanks again.

Now it says:

> /usr/lib/pm-utils/power.d/usb_autosuspend true: /usr/lib/pm-utils/power.d/usb_autosuspend: line 2: [: true: integer expression expected
success.

I'm sorry if I'm not helping much, but all my considerations are based on speculations.

Let me know if you find out what to change next.

---

### Post by scragar on 2009-11-12
I'm an idiot.

-eq is for numbers
= is for strings.

```

if [ "$1" = "true" ]; then

```
Modify line no 2.

Can't believe I missed something that simple.

---

### Post by Axx83 on 2009-11-13
works beautifully man, thanks very much for the help, I'll soon post a comprehensive guide with all these little easy scripts. Thanks again.

---

