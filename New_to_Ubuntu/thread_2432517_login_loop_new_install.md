---
title: "login loop new install"
date: 2019-12-03
forum: New to Ubuntu
---

### Post by nashken on 2019-12-03
I've installed ubuntu 14 desktop on an ibm x3650 (because I wanted the desktop).  I upgraded to 16 and everything worked fine. I think did the ugprade to 18 and now I get what appears to be a known issue with a login loop.  I can get to command prompt with ctrl alt f2 or f3.
I moved to lightdm and tried recreating my home directory per some suggestions.  I still cannot logon.  Any suggestions please.

---

### Post by Bashing-om on 2019-12-03
nashken; Hello -  Welcome to the forum

> 
 I can get to command prompt with ctrl alt f2 or f3.


Post back, please, - Between code tags - the output of terminal command:
```

sudo lshw -C display

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

we see if this is not a broken graphic's driver.

[INDENT]could be this -
[INDENT][INDENT]might be that
[/INDENT][/INDENT][/INDENT]

---

### Post by nashken on 2019-12-03
```

  *-display
       description: VGA compatible controller
       product: ES1000
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 6
       bus info: pci@0000:01:06.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=64 mingnt=8
       resources: irq:22 memory:d0000000-d7ffffff ioport:4000(size=256) memory:dfff0000-dfffffff memory:c0000-dffff

```

---

### Post by Bashing-om on 2019-12-03
nashken; Hummm ...

So much for that 1st thought; the driver is loaded and looks good.
Do we get any hints in the log files ?
```

cat /var/log/Xorg.0.log
cat ~/.xsession-errors

```
New location of file: .local/share/xorg/Xorg.0.log that might apply here.

[INDENT][INDENT]when all else fails, read the directions
[/INDENT][/INDENT]

---

### Post by rbmorse on 2019-12-03
Did you by any chance select the option to login automatically on start (user doesn't have to explicitly log in) during installation?  

If I try that I end up with a login loop.

---

### Post by nashken on 2019-12-03
i do not see any obvious errors. Anything I should be looking for?

---

### Post by nashken on 2019-12-03
hmmm....I  might have. I honestly do not remember but I also do not recall signing on after the upgrade to 16. How do I resolve that?

---

### Post by rbmorse on 2019-12-04
I dunno.  I played with creating a new user and trying to log in on that persona which didn't work, then deleting the original user and that didn't work either.  At that point on a new install I didn't have a lot invested in it so I blew it away and re-did it, this time choosing the option to make the user log in at start up and all is well.

---

### Post by nashken on 2019-12-04
OK rebuilt and back to no logon screen...  did NOT select auto sign on...checked each update. Before I go with trying lightdm any way to fix the gnome logon screen? I was hoping the auto sign on might have broken gnome?

---

