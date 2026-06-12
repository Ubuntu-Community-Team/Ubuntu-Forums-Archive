---
title: "Chroot Terminal in normal terminal"
date: 2012-01-07
forum: Programming Talk
---

### Post by ryanrio95 on 2012-01-07
Hi.

I have an build script for Riome.
And an question, how to start an gnome-terminal that is chrooted to the directory i want.
Where i can put the codes for the build.
And when the second terminal is closed, the build process needs to continue.

Who can help me out.
Thanks in advance.

---

### Post by Bachstelze on 2012-01-07
Er, why do you need a chroot for building something?

---

### Post by bluexrider on 2012-01-07
```
gksu /usr/bin/x-terminal-emulator
```

may work

---

### Post by dwhitney67 on 2012-01-07
> **Bachstelze said:**
> Er, why do you need a chroot for building something?

It offers a "pristine" environment in which to build s/w.  This environment will include the tools that will be applicable to the target environment, and these may be different from that used by the system.  I had to do something similar when I was building Cross-Compiled Linux From Scratch (CLFS).

---

### Post by dwhitney67 on 2012-01-07
> **ryanrio95 said:**
> Hi.

I have an build script for Riome.
And an question, how to start an gnome-terminal that is chrooted to the directory i want.
Where i can put the codes for the build.
And when the second terminal is closed, the build process needs to continue.

Who can help me out.
Thanks in advance.

Here's an example of using chroot:

```

/usr/sbin/chroot "${DIR}" /tools/bin/env -i \
    HOME=/root TERM="${TERM}" PS1='\u:\w\$ ' \
    PATH=/bin:/usr/bin:/sbin:/usr/sbin \
    /tools/bin/bash --login /sources/scripts/build-iso.sh

```
Basically, this changes the root directory to ${DIR}, and setups the working environment with the definitions for HOME, TERM, PS1, and PATH.  The new instance will be running bash as a login shell, and this shell will invoke a particular shell script (build-iso.sh).

I do not know if you can substitute the gnome-terminal application in lieu of the shell-script, but it might just work.  Try it out.

---

### Post by Bachstelze on 2012-01-07
> **dwhitney67 said:**
> It offers a "pristine" environment in which to build s/w.  This environment will include the tools that will be applicable to the target environment, and these may be different from that used by the system.  I had to do something similar when I was building Cross-Compiled Linux From Scratch (CLFS).

I wasn't asking you. If OP knew how to use a chroot, he wouldn't have asked this question in the first place. So I am assuming he is following some kind of instructions that ask for a chroot, so we must know exactly what those are if we want to be of any help.

---

### Post by ryanrio95 on 2012-01-08
I meant something like this: gksu gnome-terminal -e chroot temp/squashfs-root
but then when i close the new terminal, then the script goes further? or launches another script.
i can make for example, prepare.sh that launches the new gnome-terminal within chroot and then exits, and when i close the new terminal it will run build.sh automatically?

greets

---

### Post by dwhitney67 on 2012-01-08
> **Bachstelze said:**
> I wasn't asking you.
Boohoo.

---

### Post by jwbrase on 2012-01-08
> **ryanrio95 said:**
> I meant something like this: gksu gnome-terminal -e chroot temp/squashfs-root
but then when i close the new terminal, then the script goes further? or launches another script.
i can make for example, prepare.sh that launches the new gnome-terminal within chroot and then exits, and when i close the new terminal it will run build.sh automatically?

greets

OK, so you want to launch the new terminal, do some stuff manually in the terminal in a chroot environment, and then have it go on to the next step in the process when you're done with the manual stuff and close the terminal? Is the stuff it's doing after you close the terminal supposed to be in a chroot too, or just the stuff that you do in the terminal?

---

### Post by jwbrase on 2012-01-08
> **Bachstelze said:**
> I wasn't asking you. If OP knew how to use a chroot, he wouldn't have asked this question in the first place. So I am assuming he is following some kind of instructions that ask for a chroot, so we must know exactly what those are if we want to be of any help.

My impression is that he knows how to do a chroot, but is trying to do some stuff in addition to the chroot, and is having trouble explaining exactly what he wants to do in English (he's from Holland).

---

