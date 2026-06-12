---
title: "Could I run UNIX System III under VMware/VirtualBox/Qemu?"
date: 2008-08-10
forum: Other OS Talk
---

### Post by MaxIBoy on 2008-08-10
Because it would be cool. Was there ever an x86 port of UNIX System III or any other ancient UNIX? Barring that, is VMware/VirtualBox/Qemu capable of emulating an architecture which ancient UNIX *can* run on?

---

### Post by mrsteveman1 on 2008-08-10
I think it ran on VAX or DEC PDP-11, so vmware is out.

There may be an emulator for those arch but Qemu can't it seems.

---

### Post by mips on 2008-08-10
You could do a search for:
AIX PS/2, AIX/386, which was done by [Locus Computing Corporation ]("http://en.wikipedia.org/w/index.php?title=Locus_Computing_Corporation&action=edit")for IBM.
PC/IX which was done by [INTERACTIVE Systems Corporation]("http://en.wikipedia.org/wiki/INTERACTIVE_Systems_Corporation") for IBM.
SCO OpenServer UNIX, SVR3.2-based
[http://cbbrowne.com/info/unixlist.html](http://cbbrowne.com/info/unixlist.html) has another list of possibilities.

---

### Post by MaxIBoy on 2008-08-10
Thanks, I will look those up. Maybe I can also find a VAX emulator or something.

---

### Post by mips on 2008-08-11
> **MaxIBoy said:**
> Thanks, I will look those up. Maybe I can also find a VAX emulator or something.

SIMH is about as good as it gets for VAX emulation:
[http://simh.trailing-edge.com/](http://simh.trailing-edge.com/)
[http://en.wikipedia.org/wiki/SIMH](http://en.wikipedia.org/wiki/SIMH)

---

### Post by MaxIBoy on 2008-08-11
Very good find. The Wiki article even links to a .deb!

 I see it can emulate PDP-11 *and* VAX computers. Which would be a better choice?

---

### Post by MaxIBoy on 2008-08-11
Wuh-oh, it doesn't seem to want to compile.
```
maxtothemax@maxtothemax-laptop:~/Desktop/simh$ make
gcc -std=c99 -U__STRICT_ANSI__ -g -lrt -lm -D_GNU_SOURCE -I . PDP1/pdp1_lp.c PDP1/pdp1_cpu.c PDP1/pdp1_stddev.c PDP1/pdp1_sys.c PDP1/pdp1_dt.c PDP1/pdp1_drm.c PDP1/pdp1_clk.c PDP1/pdp1_dcs.c scp.c sim_console.c sim_fio.c sim_timer.c sim_sock.c sim_tmxr.c sim_ether.c sim_tape.c -I PDP1 -o BIN/pdp1 
/usr/bin/ld: cannot open output file BIN/pdp1: No such file or directory
collect2: ld returned 1 exit status
make: *** [BIN/pdp1] Error 1
maxtothemax@maxtothemax-laptop:~/Desktop/simh$ sudo make
[sudo] password for maxtothemax: 
gcc -std=c99 -U__STRICT_ANSI__ -g -lrt -lm -D_GNU_SOURCE -I . PDP1/pdp1_lp.c PDP1/pdp1_cpu.c PDP1/pdp1_stddev.c PDP1/pdp1_sys.c PDP1/pdp1_dt.c PDP1/pdp1_drm.c PDP1/pdp1_clk.c PDP1/pdp1_dcs.c scp.c sim_console.c sim_fio.c sim_timer.c sim_sock.c sim_tmxr.c sim_ether.c sim_tape.c -I PDP1 -o BIN/pdp1 
/usr/bin/ld: cannot open output file BIN/pdp1: No such file or directory
collect2: ld returned 1 exit status
make: *** [BIN/pdp1] Error 1
maxtothemax@maxtothemax-laptop:~/Desktop/simh$ 

```

---

### Post by mips on 2008-08-11
> **MaxIBoy said:**
> Very good find. The Wiki article even links to a .deb!

 I see it can emulate PDP-11 *and* VAX computers. Which would be a better choice?

I no longer use ubuntu but it should be in the repos? It's in the Arch repos for what it's worth.

If I'm not mistaken PDP-11 is really ancient and was one of the first things Unix was developed on, go the VAX route.

---

### Post by MaxIBoy on 2008-08-11
Well, when I tried to install it from repos, it installed into some black hole. I could not find it in any menus, or the menu editor, and when I typed "simh" into the console, I got "command not found." I'll check my /bin folder to see if it installed.

---

### Post by zmjjmz on 2008-08-11
Check /usr/bin or /usr/sbin , not /bin

---

