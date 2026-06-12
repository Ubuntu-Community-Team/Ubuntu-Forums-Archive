---
title: "cannot remove ndiswrapper.ko,Permission denied"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by zel108 on 2008-04-28
successfully installed ubuntu under the help by tompickles.
now trying to config my wireless usb adapter and got a problem with permission. the error message is [COLOR="Red"]cannot remove `/lib/modules/2.6.24-16-generic/misc/ndiswrapper.ko': Permission denied[/COLOR].

after check the file ndiswrapper.ko which only root has permission to write with. and i am suppose be the only user for the new ubuntu 8.04 system,and the root with the same pass as me. with my limited knowledge that i couldn't use root login to remove ndiswrapper.ko.

any help is appreciated!

---

### Post by nowshining on 2008-04-28
did you try using sudo?

did you make sure you typed in the password right?

Did you know that in the CLI the password won't show as you tye when you use sudo, just type it out as normally and hit enter.

You can use TAB for completion in the CLI.

---

### Post by zel108 on 2008-04-28
> **nowshining said:**
> did you try using sudo?

did you make sure you typed in the password right?

Did you know that in the CLI the password won't show as you tye when you use sudo, just type it out as normally and hit enter.

You can use TAB for completion in the CLI.

ist happen when i run 'make uninstall'

and there is no password ask me to put when using terminor

---

