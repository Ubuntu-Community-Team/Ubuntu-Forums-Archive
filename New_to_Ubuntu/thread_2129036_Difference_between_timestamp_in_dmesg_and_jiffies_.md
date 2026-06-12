---
title: "Difference between timestamp in dmesg and jiffies inside code"
date: 2013-03-25
forum: New to Ubuntu
---

### Post by ymsaputra on 2013-03-25
Dear All,

What the difference between timestamp which is displayed in dmesg console and the jiffies inside the the kernel module code?

I want to know the time when the function/variable is called by the system. As far as I know, I can know the time by seeing the timestamp in dmesg console 
but I want to know the time inside the kernel module code. Is it true by using jiffies? Any other methods to know the time when the function/variable is called inside kernel module code?

and which is the accurate one?


Thank you for your answers

---

### Post by Doug S on 2013-03-25
Your question is pretty advanced, and certainly not an "Absolute Beginners Section" type question.
The dmseg stuff is time stamped in seconds, while jiffies counts basic time ticks in the kernel.
The jiffies rate varies but have a look at your config file to know for sure for your system. 250 Hertz is fairly common, or 4 milliseconds per tick. Example of where to look:```
doug@s15:~/sguide-1304/lp1159144/serverguide/C$ gr[COLOR=#ff0000]ep HZ /boot/config-3.2.0-39-generic[/COLOR]
CONFIG_RCU_FAST_NO_HZ=y
CONFIG_NO_HZ=y
# CONFIG_HZ_100 is not set
CONFIG_HZ_250=y
# CONFIG_HZ_300 is not set
# CONFIG_HZ_1000 is not set
[COLOR=#ff0000]CONFIG_HZ=250[/COLOR]
CONFIG_MACHZ_WDT=m

```It sounds as though you have the source code and maybe building your own kernel. Maybe you could use "printk" to add debug entries to kern.log (maybe it writes to dmesg also, I don't know) to help.

---

