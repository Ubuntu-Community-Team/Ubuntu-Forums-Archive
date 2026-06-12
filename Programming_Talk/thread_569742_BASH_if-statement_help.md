---
title: "BASH if-statement help"
date: 2007-10-07
forum: Programming Talk
---

### Post by niviq on 2007-10-07
I've been trying to make this simple BASH-script, and I ran into the problem that grep is taking the ] as an argument.
How do I terminate the string gerp is sharching for? (semicolon doesn't work!)

```
#! /bin/bash
if [ -n amixer get 'External Amplifier' | grep "off" ]; then
	amixer set 'External Amplifier' on;
	amixer set PCM 90%;
else
	amixer set 'External Amplifier' off;
	amixer set PCM 30%;
fi
```

Also, if there is something more wrong with this code then alert me!
The code uses amixer to toggle the External Amplifier and volume of PCM.. Or that what it's was supposed to do :P

---

### Post by Ramses de Norre on 2007-10-07
Something like this maybe:```
#! /bin/bash
if [ -n $(amixer get 'External Amplifier' | grep "off") ]; then
	amixer set 'External Amplifier' on;
	amixer set PCM 90%;
else
	amixer set 'External Amplifier' off;
	amixer set PCM 30%;
fi
```
I can't decently test it here.

---

### Post by niviq on 2007-10-07
Thanks!
It works like this:

```
#! /bin/bash
if [ -n "$(amixer get 'External Amplifier' | grep off)" ]; then
	amixer set 'External Amplifier' on
	amixer set PCM 90%
else
	amixer set 'External Amplifier' off
	amixer set PCM 30%
fi
```

---

