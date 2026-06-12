---
title: "[SOLVED] Help!  Why is tty9 using so much cpu and memory?"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by jonobe on 2008-10-26
I have just discovered, as a newbie, the ps command in the terminal window.

I noticed that most activity 0.6%CPU and 3% memory and active for 40 seconds in last hour - far higher than anything else - is coming from tty9 (which i didn't even know I had!).  Here is a copy of what I get:

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root      4786  0.0  0.1   1716   508 tty4     Ss+  07:42   0:00 /sbin/getty 38400 tty4
root      4787  0.0  0.1   1716   508 tty5     Ss+  07:42   0:00 /sbin/getty 38400 tty5
root      4789  0.0  0.1   1716   508 tty2     Ss+  07:42   0:00 /sbin/getty 38400 tty2
root      4791  0.0  0.1   1716   508 tty3     Ss+  07:42   0:00 /sbin/getty 38400 tty3
root      4793  0.0  0.1   1716   508 tty6     Ss+  07:42   0:00 /sbin/getty 38400 tty6
root      5908  0.0  0.1   1716   508 tty1     Ss+  07:42   0:00 /sbin/getty 38400 tty1
root      6085  0.6  3.0  22912 15644 tty9     Ss+  07:43   0:40 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt9
jono      7604  0.0  0.6   6024  3428 pts/0    Ss   07:58   0:00 bash
jono     18639  0.0  0.1   2644  1004 pts/0    R+   09:25   0:00 ps au



Can anyone tell me to what is going on in tty9?  Why so busy?  Should I be concerned or is this normal:confused:

---

### Post by EnGorDiaz on 2008-10-26
> **jonobe said:**
> I have just discovered, as a newbie, the ps command in the terminal window.

I noticed that most activity 0.6%CPU and 3% memory and active for 40 seconds in last hour - far higher than anything else - is coming from tty9 (which i didn't even know I had!).  Here is a copy of what I get:

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root      4786  0.0  0.1   1716   508 tty4     Ss+  07:42   0:00 /sbin/getty 38400 tty4
root      4787  0.0  0.1   1716   508 tty5     Ss+  07:42   0:00 /sbin/getty 38400 tty5
root      4789  0.0  0.1   1716   508 tty2     Ss+  07:42   0:00 /sbin/getty 38400 tty2
root      4791  0.0  0.1   1716   508 tty3     Ss+  07:42   0:00 /sbin/getty 38400 tty3
root      4793  0.0  0.1   1716   508 tty6     Ss+  07:42   0:00 /sbin/getty 38400 tty6
root      5908  0.0  0.1   1716   508 tty1     Ss+  07:42   0:00 /sbin/getty 38400 tty1
root      6085  0.6  3.0  22912 15644 tty9     Ss+  07:43   0:40 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt9
jono      7604  0.0  0.6   6024  3428 pts/0    Ss   07:58   0:00 bash
jono     18639  0.0  0.1   2644  1004 pts/0    R+   09:25   0:00 ps au



Can anyone tell me to what is going on in tty9?  Why so busy?  Should I be concerned or is this normal:confused:


thats extrmely wierd looks like your connected to a telnet... o.o ummm lol

---

### Post by schiznik on 2008-10-26
Thats your X server... you need it (assuming you want a gui)

---

### Post by jonobe on 2008-10-26
> **schiznik said:**
> Thats your X server... you need it (assuming you want a gui)

thanks:)

i've just worked that out now.  Why on tty9 though and not tty7, i wonder?

---

