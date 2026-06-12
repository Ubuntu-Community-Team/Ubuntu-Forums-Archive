---
title: "Can't do ANYTHING with 'xorg-driver-fglrx'!"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by StupendousMan on 2008-05-20
Hello everyone.

I have an unusual situation here.  I recently installed an ATI Radeon 9550 video card with 256Mb video memory.  I wanted to get Compiz working really smoothly.  thought this would work out perfectly since I had been using a radeon 9300 with 64Mb memory.

Anyhow, on trying to install the ATI drivers I have run into an error message that will not permit me to do anything, not install, uninstall, or reinstall.  Here is the error message that I get in both the Restricted Drivers Manager and in the Terminal:

Writing extended state information... Done
(Reading database ... dpkg: error processing xorg-driver-fglrx (--remove):
 [B][COLOR="Red"]files list file for package `xorg-driver-fglrx' is missing final newline
Errors were encountered while processing:
 xorg-driver-fglrx
Processing was halted because there were too many errors.[/COLOR][/B]
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             

Apparently because the "final newline" is missing, it's preventing me from being able to move forward. As I said, I can't uninstall, reinstall, or overwrite xorg.

So does anyone know what's happening and how I can fix this so I can have fun using Compiz?

All help IS appreciated.  Thanks.

---

### Post by Paqman on 2008-05-20
Try:
```

sudo dpkg --configure -a

```

---

### Post by kellemes on 2008-05-20
Do you happen to have the following file on disk?
```
/var/lib/dpkg/info/xorg-driver-fglrx.list
```

If so.. try to rename it for the time being and remove/purge the package.
It probably has some error in it.

---

### Post by stchman on 2008-05-20
> **StupendousMan said:**
> Hello everyone.

I have an unusual situation here.  I recently installed an ATI Radeon 9550 video card with 256Mb video memory.  I wanted to get Compiz working really smoothly.  thought this would work out perfectly since I had been using a radeon 9300 with 64Mb memory.

Anyhow, on trying to install the ATI drivers I have run into an error message that will not permit me to do anything, not install, uninstall, or reinstall.  Here is the error message that I get in both the Restricted Drivers Manager and in the Terminal:

Writing extended state information... Done
(Reading database ... dpkg: error processing xorg-driver-fglrx (--remove):
 [B][COLOR="Red"]files list file for package `xorg-driver-fglrx' is missing final newline
Errors were encountered while processing:
 xorg-driver-fglrx
Processing was halted because there were too many errors.[/COLOR][/B]
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             

Apparently because the "final newline" is missing, it's preventing me from being able to move forward. As I said, I can't uninstall, reinstall, or overwrite xorg.

So does anyone know what's happening and how I can fix this so I can have fun using Compiz?

All help IS appreciated.  Thanks.

I just now was able to get Compiz working on my ATI equipped laptop after I installed Hardy.  Now Compiz works perfectly.

Getting Compiz to work before was a real pain on ATI before Hardy.

What Ubuntu are you using?  I recommend Hardy for ATI users.

---

### Post by StupendousMan on 2008-05-21
> **Paqman said:**
> Try:
```

sudo dpkg --configure -a

```

Gave that a try and it appears not to have done any good.  I still get the error message saying: 

"[COLOR="Red"](Reading database ... dpkg: error processing xorg-driver-fglrx (--remove):
files list file for package `xorg-driver-fglrx' is missing final newline
Errors were encountered while processing:
xorg-driver-fglrx
Processing was halted because there were too many errors.[/COLOR]"

This is really giving me a headache. For example, I tried to install *Gnome-ppp* and Synaptic couldn't do it because of the error mentioned above.

I just want my computer to be the envy of all my friends, is that so bad???  ;)

---

