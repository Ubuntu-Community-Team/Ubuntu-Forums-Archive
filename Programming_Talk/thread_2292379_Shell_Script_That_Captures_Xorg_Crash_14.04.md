---
title: "Shell Script That Captures Xorg Crash 14.04"
date: 2015-08-27
forum: Programming Talk
---

### Post by coljohnhannibalsmith on 2015-08-27
Hello,

I'm running Flashback-Compiz sessions in 14.04 and have been having problems with Xorg crashing after several hours of use, more frequently when xscreensaver is enabled. A very talented gentleman suggested that I tunnel in from one pc to the other with ssh and run "top," so that I can see which process/s are hanging at the time Xorg crashes. I tried this; but was unable to capture it because it takes the Desktop about 2 1/2 hours to fail on average; so I'm not around when it happens. What I need is a way to automate this process by writing a shell script that will capture the state of process/s when the crash occurs. This could be done by using a program such as "top" to monitor the processes; and then redirecting top > its output to a file when a certain condition is met such as Xorg > 11% cpu with time-stamp. This script could even run on the local machine, since I've determined that the local machine still responds to terminal commands, when Xorg crashes.

I'm thinking of a line such as [COLOR=#ff0000]*IF xorg > 11% cpu |  top > file.txt*[/COLOR].

I've also had problems with other equipment; such as my router and satellite modem crashing due to heat. I live in a very humid area and although my home is kept at a comfortable temperature, about 76 degrees farenheit; I think it may still be possible that my system is overheating. Perhaps I'll also want to monitor cpu temp at crash time? Could the display overheating also cause Xorg to fail? I'm using a screensaver that turns on every pixel; this may well be overheating the display?

Any help appreciated.

Thanks, Hannibal

---

### Post by QDR06VV9 on 2015-08-28
Not being a proficient programmer myself, I have used this more or less from time to time in helping friends
Just for Example
> **The basics**

[COLOR=#000000][FONT=Times New Roman]Start the server normally. Go over to your second machine and ssh into the first one. su root, and type[/FONT][/COLOR]
gdb /opt/xorg-debug/Xorg $(pidof Xorg)[COLOR=#000000][FONT=Times New Roman]or[/FONT][/COLOR]
gdb /usr/bin/Xorg $(pidof X)[COLOR=#000000][FONT=Times New Roman]depending on your setup.[/FONT][/COLOR]
More here [http://www.x.org/wiki/Development/Documentation/ServerDebugging/](http://www.x.org/wiki/Development/Documentation/ServerDebugging/)
And just my 2 cents on Screensavers.
> [FONT=Open Sans]Screen savers are a left-over solution from a previous technology. In spite of their name, screen savers no longer &#8220;save&#8221; anything &#8211; all they do is waste electricity. Screen savers are not necessary on modern, flat-panel LCD displays.
[/FONT][FONT=Open Sans]Having your computer automatically turn off its display is the new &#8220;screen saver&#8221; &#8211; it saves energy, reduces your electricity bill, and increases your battery life. Screen savers may look pretty, but they do it when no one is looking.[/FONT]
More here [http://www.howtogeek.com/128644/htg-explains-why-screen-savers-are-no-longer-necessary/](http://www.howtogeek.com/128644/htg-explains-why-screen-savers-are-no-longer-necessary/)
Hope this what you were after.
Regards

---

### Post by coljohnhannibalsmith on 2015-08-28
> **runrickus said:**
> Not being a proficient programmer myself, I have used this more or less from time to time in helping friends
Just for Example

More here [http://www.x.org/wiki/Development/Documentation/ServerDebugging/](http://www.x.org/wiki/Development/Documentation/ServerDebugging/)
And just my 2 cents on Screensavers.

More here [http://www.howtogeek.com/128644/htg-explains-why-screen-savers-are-no-longer-necessary/](http://www.howtogeek.com/128644/htg-explains-why-screen-savers-are-no-longer-necessary/)
Hope this what you were after.
Regards

Looks like a step in the right direction. thanks.

BTW, I find screensavers comforting; and I often use them as night-lights. It and 's also sometimes a useful way to determine if you have User environment issues. I have less frequent UE crashes.

---

### Post by coljohnhannibalsmith on 2015-08-28
> **runrickus said:**
> Not being a proficient programmer myself, I have used this more or less from time to time in helping friends
Just for Example

More here [http://www.x.org/wiki/Development/Documentation/ServerDebugging/](http://www.x.org/wiki/Development/Documentation/ServerDebugging/)
And just my 2 cents on Screensavers.

More here [http://www.howtogeek.com/128644/htg-explains-why-screen-savers-are-no-longer-necessary/](http://www.howtogeek.com/128644/htg-explains-why-screen-savers-are-no-longer-necessary/)
Hope this what you were after.
Regards

Here's the output from the first command:

```

sophie@sophie-Inspiron-1545:~$ gdb /opt/xorg-debug/Xorg $(1805)
1805: command not found
GNU gdb (Ubuntu 7.7.1-0ubuntu5~14.04.2) 7.7.1
Copyright (C) 2014 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>.
Find the GDB manual and other documentation resources online at:
<http://www.gnu.org/software/gdb/documentation/>.
For help, type "help".
Type "apropos word" to search for commands related to "word"...
/opt/xorg-debug/Xorg: No such file or directory.
(gdb) show configuration
This GDB was configured as follows:
   configure --host=x86_64-linux-gnu --target=x86_64-linux-gnu
             --with-auto-load-dir=$debugdir:$datadir/auto-load
             --with-auto-load-safe-path=$debugdir:$datadir/auto-load
             --with-expat
             --with-gdb-datadir=/usr/share/gdb (relocatable)
             --with-jit-reader-dir=/usr/lib/gdb (relocatable)
             --without-libunwind-ia64
             --with-lzma
             --with-python=/usr (relocatable)
             --with-separate-debug-dir=/usr/lib/debug (relocatable)
             --with-system-gdbinit=/etc/gdb/gdbinit
             --with-zlib
             --without-babeltrace

("Relocatable" means the directory can be moved with the GDB installation
tree, and GDB will still find it.)
(gdb)
``` 

Here's the output from the second:
```

sophie@sophie-Inspiron-1545:~$ gdb /usr/bin/Xorg $(1805)
1805: command not found
GNU gdb (Ubuntu 7.7.1-0ubuntu5~14.04.2) 7.7.1
Copyright (C) 2014 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>.
Find the GDB manual and other documentation resources online at:
<http://www.gnu.org/software/gdb/documentation/>.
For help, type "help".
Type "apropos word" to search for commands related to "word"...
Reading symbols from /usr/bin/Xorg...(no debugging symbols found)...done.
(gdb)
```

Also, I couldn't fing "xorg-debug" is Synaptic. I do however have gdb installed.

In the meantime I'll check the man-pages for correct syntax.

Thanks, Hannibal

---

### Post by QDR06VV9 on 2015-08-29
[LIST]
[*][COLOR=black]Using gdm3 3.4.1 and above: uncomment Enable = true in the [debug] section of the /etc/gdm3/daemon.conf file.[/COLOR]

[*][COLOR=black]Using an older gdm3 package: The idea is to tweak the daemon’s LocalXserverCommand setting, adding the -core option. As of gdm3 2.30, the defaults can be found in /usr/share/gdm/gdm.schemas. Sample /etc/gdm3/daemon.conf excerpt:

A fair explanation found here [http://pkg-xorg.alioth.debian.org/howto/use-gdb.html](http://pkg-xorg.alioth.debian.org/howto/use-gdb.html)

BTW have you looked at .xsession-errors in your home Directory and /var/log's yet?[/COLOR]
[/LIST]

---

### Post by coljohnhannibalsmith on 2015-08-29
> **runrickus said:**
> 
[LIST]
[*][COLOR=black]Using gdm3 3.4.1 and above: uncomment Enable = true in the [debug] section of the /etc/gdm3/daemon.conf file.[/COLOR] 
[*][COLOR=black]Using an older gdm3 package: The idea is to tweak the daemon&#8217;s LocalXserverCommand setting, adding the -core option. As of gdm3 2.30, the defaults can be found in /usr/share/gdm/gdm.schemas. Sample /etc/gdm3/daemon.conf excerpt:

A fair explanation found here [http://pkg-xorg.alioth.debian.org/howto/use-gdb.html](http://pkg-xorg.alioth.debian.org/howto/use-gdb.html)

BTW have you looked at .xsession-errors in your home Directory and /var/log's yet?[/COLOR] 
[/LIST]


I have installed gdm on both the target and remote machines; I hope this won't reconfigure my Flashback sessions. I have gdm 3.10.0.1-0ubuntu3.2 in 14.04 TT.

Here's the output from .xsession-errors: (the contents haven't changed in a while)
```

Script for ibus started at run_im.
init: indicator-bluetooth main process ended, respawning
init: indicator-application main process ended, respawning
init: indicator-application main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-application respawning too fast, stopped
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth main process ended, respawning
init: indicator-bluetooth respawning too fast, stopped
```

The only log file that looked funny was Xorg.falesafe.log: (this was highlighted in red)
```

\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00
```

I think I'm ready to try gdb again. Is there anything else I should know?

Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2015-08-29
This is from latest try with gdb:

sophie@sophie-Inspiron-1545:~$ gdb /usr/bin/Xorg $1762
GNU gdb (Ubuntu 7.7.1-0ubuntu5~14.04.2) 7.7.1
Copyright (C) 2014 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>.
Find the GDB manual and other documentation resources online at:
<http://www.gnu.org/software/gdb/documentation/>.
For help, type "help".
Type "apropos word" to search for commands related to "word"...
Reading symbols from /usr/bin/Xorg...Reading symbols from /usr/lib/debug//usr/bin/Xorg...done.
done.
Attaching to program: /usr/bin/Xorg, process 762

warning: unable to open /proc file '/proc/762/status'

warning: unable to open /proc file '/proc/762/status'
ptrace: No such process.
/home/sophie/762: No such file or directory.
(gdb)

---

### Post by steeldriver on 2015-08-30
Your gdb command is malformed I think

If you have determined a PID for the running process (using the 'ps' command for example) then you should just give it as-is on the command line - no $ or $() around it. The former  - as in your last attempt **$1762** - tries to expand it as a variable, and the latter - which you tried previously **$(1805)** - tries to run a **command** called 1805 and use the **result** of that as the PID. This form is useful if you want to use pgrep or pidof to get the PID on-the-fly in a single command (see below).

Also the name of the process is **Xorg** but the name of the binary program is just /usr/bin/**X**

[SIZE=4]**But that's probably a good thing**[/SIZE]

First, unless you are running as root (sudo or sudo -i) you won't be allowed to attach to a root-owned process.

Second and most important **you must do this from outside the X session** - either a virtual terminal or via SSH. The first thing that happens when (if) you successfully attach is that gdb will pause the attached process: until you type 'continue' or 'cont' the X server process will be frozen. Obviously you won't be able to type 'cont' if gdb is running inside a terminal emulator inside the frozen session.

In fact, I'm not sure even using a virtual terminal will be helpful - you should be able to attach, but then will likely be unable to switch back to VT7 in order to make the session fail in a way you can observe.

Finally, unless you have all the relevant debug libraries installed, the stack trace is not likely to be meaningful.

If you still want to go ahead, there appears to be some useful information here --> [http://www.x.org/wiki/Development/Documentation/ServerDebugging/](http://www.x.org/wiki/Development/Documentation/ServerDebugging/) however note that in place of the suggested

```
 gdb /opt/xorg-debug/Xorg $(pidof Xorg)
```
or 
```
gdb /usr/bin/Xorg $(pidof X)
```

you will probably want
```
gdb **/usr/lib/debug/usr/bin/Xorg** $(pidof X)
```

since that's where the Ubuntu xserver-xorg-core-dbg package seems to put the debug-linked binary.

---

### Post by tgalati4 on 2015-08-30
Does this problem happen with all screensavers?  Or just one?  Some screensavers are pathological--meaning they make a graphics call that will fail on some graphics cards--due to a bug or missing feature in an open driver.  So, try a simple screensaver and monitor its behavior.  I agree with runrickus, using a screensaver is a relic from the past.  Does the computer lock up if you use screen blanking instead?  If so, then there may be something else going on.

---

### Post by coljohnhannibalsmith on 2015-08-30
> **tgalati4 said:**
> Does this problem happen with all screensavers?  Or just one?  Some screensavers are pathological--meaning they make a graphics call that will fail on some graphics cards--due to a bug or missing feature in an open driver.  So, try a simple screensaver and monitor its behavior.  I agree with runrickus, using a screensaver is a relic from the past.  Does the computer lock up if you use screen blanking instead?  If so, then there may be something else going on.

On my own, I've been following the same line of thinking; so I have tried using a simple screensaver, one with a lot of black, with the same result. Also, I have DE crashes w/o the screensaver active, in Flashback and in Unity; but since installing GDM, I have yet to observe another DE crash. In the meantime I'll go back to running TOP from a remote shell, while I peruse the recommended literature.

Thanks, Hannibal

---

### Post by QDR06VV9 on 2015-08-31
Are you using [COLOR=#000000][FONT=helvetica neue]Nouveau video driver?[/FONT][/COLOR]

---

### Post by coljohnhannibalsmith on 2015-08-31
No. I'm using I915:

*-display
             description: VGA compatible controller
             product: 3rd Gen Core processor Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             [COLOR=#0000ff]*configuration: driver=i915 latency=0*[/COLOR]
             resources: irq:44 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:3000(size=64)

---

### Post by QDR06VV9 on 2015-08-31
Have you tried to blow some of the dust that gathers in humid environments(Canned Air) ?
 I am Aware it is a Laptop, Also what is the Output of
```
free
```

---

### Post by coljohnhannibalsmith on 2015-08-31
> **runrickus said:**
> Have you tried to blow some of the dust that gathers in humid environments(Canned Air) ?
 I am Aware it is a Laptop, Also what is the Output of
```
free
```

Yes I cleaned both machines; neither of them were very dirty.

free:

sophie@sophie-Inspiron-1545:~$ free
             total       used       free     shared    buffers     cached
Mem:       8076520    2104188    5972332     216660     121888     944900
-/+ buffers/cache:    1037400    7039120
Swap:      4150268          0    4150268
sophie@sophie-Inspiron-1545:~$ 

Also, I did get the crash again. Please see attachment.

---

### Post by QDR06VV9 on 2015-08-31
Sorry my friend I am at a loss for any more suggestions for now.
Could not read the important parts of your Xorg crash.
Kind Regards

---

### Post by coljohnhannibalsmith on 2015-09-01
```

ExecutablePath

/usr/bin/Xorg

Package

xserver-xorg-core-lts-utopic 2:1.16.0-1ubuntu1.2-trusty2

ProblemType

Crash

Title

Xorg crashed with SIGABRT in_libc_message()

ApportVerion

2.14.1-0ubuntu3.13

Architechture

amd64

CoreDump
CrashCounter

1

Date

Mon Aug 31 16:17:21 2015

Dependencies
Disassembly
DistroRelease

Ubuntu 14.04

```

---

### Post by coljohnhannibalsmith on 2015-09-01
Xorg after crash: (please see attachment)

---

