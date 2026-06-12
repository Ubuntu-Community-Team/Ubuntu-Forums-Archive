---
title: "[SOLVED] In need of sed help"
date: 2008-07-03
forum: Programming Talk
---

### Post by master_kernel on 2008-07-03
Hi, I am trying to configure my kernel config and I need to use sed to integrate automatic audio support. Here's what I have:

Configuration file (full version attached):
> 
........
#
# Console display driver support
#
CONFIG_VGA_CONSOLE=y
# CONFIG_VGACON_SOFT_SCROLLBACK is not set
CONFIG_VIDEO_SELECT=y
CONFIG_DUMMY_CONSOLE=y
CONFIG_FRAMEBUFFER_CONSOLE=m
# CONFIG_FRAMEBUFFER_CONSOLE_DETECT_PRIMARY is not set
# CONFIG_FRAMEBUFFER_CONSOLE_ROTATION is not set
# CONFIG_FONTS is not set
CONFIG_FONT_8x8=y
CONFIG_FONT_8x16=y
# CONFIG_LOGO is not set
........
# Generic devices
#
# CONFIG_SND_DUMMY is not set
# CONFIG_SND_MTPAV is not set
# CONFIG_SND_MTS64 is not set
# CONFIG_SND_SERIAL_U16550 is not set
# CONFIG_SND_MPU401 is not set
# CONFIG_SND_PORTMAN2X4 is not set

#
# PCI devices
#
# CONFIG_SND_AD1889 is not set
# CONFIG_SND_ALS300 is not set
# CONFIG_SND_ALS4000 is not set
# CONFIG_SND_ALI5451 is not set
........
And the list goes on. What I want to do is use a few sed commands to set ONLY the PCI devices (not the generic) to module mode (shown below):
> 
........
#
# Console display driver support
#
CONFIG_VGA_CONSOLE=y
# CONFIG_VGACON_SOFT_SCROLLBACK is not set
CONFIG_VIDEO_SELECT=y
CONFIG_DUMMY_CONSOLE=y
CONFIG_FRAMEBUFFER_CONSOLE=m
# CONFIG_FRAMEBUFFER_CONSOLE_DETECT_PRIMARY is not set
# CONFIG_FRAMEBUFFER_CONSOLE_ROTATION is not set
# CONFIG_FONTS is not set
CONFIG_FONT_8x8=y
CONFIG_FONT_8x16=y
# CONFIG_LOGO is not set
........
# Generic devices
#
# CONFIG_SND_DUMMY is not set
# CONFIG_SND_MTPAV is not set
# CONFIG_SND_MTS64 is not set
# CONFIG_SND_SERIAL_U16550 is not set
# CONFIG_SND_MPU401 is not set
# CONFIG_SND_PORTMAN2X4 is not set

#
# PCI devices
#
CONFIG_SND_AD1889=m
CONFIG_SND_ALS300=m
CONFIG_SND_ALS4000=m
CONFIG_SND_ALI5451=m
........

One of the ideas I had was:
```
grep SND .config | grep "is not set" | sed -i 's/\# //' .config
grep SND .config | grep "is not set" | sed -i 's/ is not set/=m/' .config
```
The problem was that it enabled everython that had CONFIG_SND, which was not what I wanted. Any suggestions?

---

### Post by WW on 2008-07-03
Are there more lines that begin with "# CONFIG_SND_" after the comment "PCI Devices" that you *don't* want to change?  It is hard to come up with a "safe" command without knowing more about the file.

---

### Post by ghostdog74 on 2008-07-03
No need for that much grep/sed. Use awk.
```

awk '/# PCI devices/{f=1}
f && !/^$/ && /CONFIG/ {
 gsub(/^# | is not set/,"")
 print $0"=m"
 next
}
f && /^$/{ f=0}1' file

```

---

### Post by master_kernel on 2008-07-04
The file is attached. All I want to do is change the PCI devices. Ghostdog's solution may work; I haven't tried it yet.

---

### Post by master_kernel on 2008-07-06
bump :)

---

### Post by WW on 2008-07-06
> **master_kernel said:**
> Ghostdog's solution may work; I haven't tried it yet.

Have you tried it yet?  Did it work for you?

---

### Post by master_kernel on 2008-07-06
Not quite; for an entry like the following (just an example):

# CONFIG_SND_AD1889 is not set
# CONFIG_SND_ALS300 is not set
# CONFIG_SND_ALS4000 is not set
CONFIG_SND_ALI5451=y

It does not work.

---

### Post by ghostdog74 on 2008-07-06
you don't just take code, run it straight, doesn't ask questions when stuck, and bump it without saying what went wrong. If you want to do it on lines with "is not set" , then add the check .
```

awk '/# PCI devices/{f=1}
f && !/^$/ && /CONFIG/ && /is not set/  {
 gsub(/^# | is not set/,"")
 print $0"=m"
 next
}
f && /^$/{ f=0}1' file

```

---

### Post by WW on 2008-07-06
...or using sed:
```

sed -E -i.bak '/PCI devices/,/SPI devices/ s/# (CONFIG_SND_.+) is not set/\1=m/' config.txt 

```
This assumes that the lines of interest are between the lines that contain the text "PCI devices" and "SPI devices".

---

### Post by master_kernel on 2008-07-07
> **ghostdog74 said:**
> you don't just take code, run it straight, doesn't ask questions when stuck, and bump it without saying what went wrong. If you want to do it on lines with "is not set" , then add the check .
```

awk '/# PCI devices/{f=1}
f && !/^$/ && /CONFIG/ && /is not set/  {
 gsub(/^# | is not set/,"")
 print $0"=m"
 next
}
f && /^$/{ f=0}1' file

```

This worked perfectly. Thanks!

> **WW said:**
> ...or using sed:
```

sed -E -i.bak '/PCI devices/,/SPI devices/ s/# (CONFIG_SND_.+) is not set/\1=m/' config.txt 

```
This assumes that the lines of interest are between the lines that contain the text "PCI devices" and "SPI devices".

I tried this and got an error about -E not being an option. I removed that and got another error:
> sed: -e expression #1, char 64: invalid reference \1 on `s' command's RHS


I have no idea what the \1 in the code does. Any suggestions?

---

### Post by WW on 2008-07-07
> **master_kernel said:**
> 

I tried this and got an error about -E not being an option. I removed that and got another error:


I have no idea what the \1 in the code does. Any suggestions?

Sorry, I'm on a Mac at the moment, and I forgot (once again!) that Ubuntu and OS X have different versions of sed.

Change the option -E to -r.

The \1 will be the text that matched "CONFIG_SND_.+".

---

### Post by master_kernel on 2008-07-07
> **WW said:**
> Sorry, I'm on a Mac at the moment, and I forgot (once again!) that Ubuntu and OS X have different versions of sed.

Change the option -E to -r.

The \1 will be the text that matched "CONFIG_SND_.+".
Thanks!

---

