---
title: "Randomizing via bash"
date: 2010-09-16
forum: Programming Talk
---

### Post by wigout on 2010-09-16
So.

I have a constrained system. I don't have sort -R as an option. awk is not an option.

What I'm interested in is taking a text file and randomizing the lines in the file.

There's two approaches so far (the first based on examples found at:
[http://hivearchive.com/2007/10/18/bash-one-liner-to-randomize-lines-in-file/](http://hivearchive.com/2007/10/18/bash-one-liner-to-randomize-lines-in-file/) ).
```

cat text.file | 
   while read i; 
      do echo "$RANDOM $i"; 
   done 
| sort | sed -r "s/^[0-9]+ //" > 
text.temp; mv text.temp text.file
``````

while read i; 
   do let R=$RANDOM%9999999+1000000; 
   echo "$R $i"; done < text.file 
| sort | 
   while read line; 
   do echo `expr substr "$line" 9 2000`; done > text.temp&& mv text.temp text.file

```on a 4000 line file, the first version is at least twice as fast as the second.

The second approach came of trying to use less non-builtin bash commands. (sed was dropped). sort remains, of course. 

I thought that switching away from sed would make the script faster, but not so.

Aside from attaching a number to the top of each line with $RANDOM and then employing sort, any other randomizing approach utilizing bash that might be faster/convenient?

Advice & insight and alternative approaches are welcome.

-wigout

---

### Post by lloyd_b on 2010-09-16
Hmmm - an interesting little problem.

For the first example, it can be made a *little* faster, by replacing 'sed' with the 'cut' command.  Since you know that the line will always start with a number followed by a space, you can easily cut this away:```
| sort | cut -d' ' -f2- > 
```The speed difference is pretty trivial, though - on my machine, feeding it a 17k line source file, it reduces the run time by 10ms to 100ms.

I would expect the second version to be twice as slow, since you're looping through the data twice.

A couple of notes on the second one.  First off, $RANDOM will always be in the range 1-32767.  So your modulo operation is completely meaningless (it'll always return the starting number).  Adding to 1000000 to force it to 7 places works, but you can force it to always be at least (and at most) 5 places by just adding 10000 (that'll give you a number in the range 10001 to 42767).

Second, there's no need to use 'expr' - If you want a built-in solution to the substring extraction, use this:```
do echo "${line:9}";
```

Do you have Perl available on that system?  There are some simple (and possibly faster) solutions available on the net to handle this question in Perl...

Lloyd B.

---

### Post by wigout on 2010-09-16
Well I am reluctant to admit that what I'm actually scripting in is busybox sh (which is, I guess, primarily based on ash) on an embedded device, which is not quite bash. For some reason I can't get the:
do echo "${line:9}";
[FONT=monospace]
to run.

both:
echo ${PROG:0}
&
echo "${PROG:0}"
return:
-sh: Syntax error: Bad substitution

perl is not available by default (it requires a fair number of hoops).

I'd rather rely on the available commands, and builtins as much as possible.

I am really *new* to bash (well, busybox sh / ash) scripting. 

My understanding is that whenever possible shifting from "external" commands to bash builtins will usually net a faster script.

Here's a thread I found while looking for info on making bash scripts work more efficiently/faster:
[http://ubuntuforums.org/showthread.php?t=548778](http://ubuntuforums.org/showthread.php?t=548778)

Anyway the cut command vs sed saved about 30 seconds on processing the 4000 line file.

Any others takes on this or suggestions?

-wigout
[/FONT]

---

### Post by gmargo on 2010-09-16
EDIT: Oh drat, you said **awk** was not an option (why not? - post the list of commands your busybox is compiled to support) .... so ignore this... sorry.

If you are writing for **busybox** shell (aka **ash**) then why are you talking about **bash**? Besides, there is no $RANDOM in ash.  However, **busybox** can save the day if it's got **awk** built in.

Here's a simple **awk** script to randomize input lines.:

```

BEGIN {
    count = 0;
}

{ lines[count++] = $0 }

END {
    srand()

    while (count > 0)
    {
        n = int(count-- * rand())
        print lines[n]
        delete lines[n]
        if (n != count)
        {
            lines[n] = lines[count]
            delete lines[count]
        }
    }
}

```

---

### Post by wigout on 2010-09-16
I apologize starting off the thread discussing bash. 

Clearly my situation calls for advice for the ash shell, specifically the ash shell built into busybox. 

awk isn't part of this busybox install.

I don't know about $RANDOM in a pure ash shell, but on the busybox shell $RANDOM works just fine.

thanks,
wigout

---

### Post by wigout on 2010-09-16
help entered on the shell
gives:
```
help 

Built-in commands:
-------------------
        . : alias bg break cd chdir continue eval exec exit export false
        fg getopts hash help jobs kill let local pwd read readonly return
        set shift times trap true type ulimit umask unalias unset wait
```
busybox gives:
```
busybox
BusyBox v1.1.3 (2010.06.08-12:57+0000) multi-call binary

Usage: busybox [function] [arguments]...
   or: [function] [arguments]...

        BusyBox is a multi-call binary that combines many common Unix
        utilities into a single executable.  Most people will create a
        link to busybox for each function they wish to use and BusyBox
        will act like whatever it was invoked as!

Currently defined functions:
        [, [[, addgroup, adduser, ash, basename, busybox, cat, chmod,
        chown, chroot, clear, cp, cut, date, dd, delgroup, deluser, devfsd,
        df, dirname, dmesg, du, e2fsck, echo, egrep, eject, expr, false,
        fdisk, fgrep, find, free, fsck, fsck.ext2, fsck.ext3, ftpget,
        ftpput, getopt, grep, halt, head, hexdump, hostname, httpd, hwclock,
        id, ifconfig, inetd, init, insmod, ipcrm, ipcs, kill, killall,
        klogd, linuxrc, ln, logger, login, losetup, ls, lsmod, lzmacat,
        mkdir, mke2fs, mkfs.ext2, mkfs.ext3, mkfs.extk, mknod, mkswap,
        mktemp, modprobe, more, mount, mv, netstat, nice, passwd, pidof,
        ping, pivot_root, poweroff, printf, ps, pwd, readlink, reboot,
        rm, rmdir, rmmod, route, sed, sh, sleep, sort, stty, swapoff,
        swapon, sync, syslogd, tail, tar, tee, telnetd, test, tftp, time,
        touch, tr, true, tune2fs, udhcpc, udhcpd, umount, uname, unlzma,
        unzip, uptime, usleep, vi, wc, wget, which, yes

```Given the sh is really just a subset/applet of busybox.... are all of the functions above considered "builtins" for the purpose of scripting for busybox?

-wigout

---

### Post by lloyd_b on 2010-09-16
Busybox is just a single executable, with lightweight versions of many common utilities, including the shell.  So all of those "currently defined functions" should be the same as a built-in, in that no external program has to be executed (it just calls another function within Busybox to do the job).  That means there's no reason to shy away from using them.

('cut' is faster in this case than 'sed' for the simple reason that 'cut' is logically much simpler - it doesn't have to mess around with pattern recognition, just look at each line, and strip off everything up to and including the first space character.)

$RANDOM is an option for Busybox - it can be built with or without it.  Apparently the build that you're using has it.  It may or may not be compatible with bash's $RANDOM though.  Try running the command "echo $RANDOM" a few times, and see if it's outputting numbers in the range 1-32767 or not.

Am I correct in assuming that you can not recompile Busybox to add additional features?  Also, can you compile *anything* for the target system?  There's a simplified Perl called "microperl" that's a lot less work to install than regular Perl.

Lloyd B.

---

### Post by wigout on 2010-09-16
$RANDOM seems random on this device.

optware can be installed on this device, and through that perl and such. optware even has its own gcc.

However, I am trying to write a script that can work for the device without utilizing such add-ons so that I can still easily share the script.

The machine is underpowered so any efficiency tips & suggestion are welcome.

The longest task I have come across so far is this randomizing bit. For the 4000 line file, it takes about 5:30 minutes, (with your cut substitution it's just under 5 minutes).

By the way I had to add the text.temp "holding file" because otherwise the output would get truncated. That is, text.file would start with 4000 files and at the end of the process only 365 files would be there. So some part of the line would outpace the other part, run out and quit the process prematurely- well from my point of view.

-wigout

---

### Post by lloyd_b on 2010-09-16
> **wigout said:**
> $RANDOM seems random on this device.

optware can be installed on this device, and through that perl and such. optware even has its own gcc.

However, I am trying to write a script that can work for the device without utilizing such add-ons so that I can still easily share the script.

The machine is underpowered so any efficiency tips & suggestion are welcome.

The longest task I have come across so far is this randomizing bit. For the 4000 line file, it takes about 5:30 minutes, (with your cut substitution it's just under 5 minutes).

By the way I had to add the text.temp "holding file" because otherwise the output would get truncated. That is, text.file would start with 4000 files and at the end of the process only 365 files would be there. So some part of the line would outpace the other part, run out and quit the process prematurely- well from my point of view.

-wigout

That temp file is always going to be necessary - reading input from a file and then outputting to the same file is never going to be safe.

Here's a variant of the "best so far" script, with some simple profiling added.  Could you run this, and post the results:```
echo -n "Appending :"
date
cat text.file |
   while read i;
      do echo "$RANDOM $i";
   done > text.1

echo -n "Sorting   :"
date
cat text.1 | sort  > text.2

echo -n "Cutting   :"
date
cat text.2 | cut -d' ' -f2- > text.temp

echo -n "Moving    :"
date
mv text.temp text.file

echo -n "Done      :"
date
```On my machine, the overwhelming majority of the time required is the time for the initial "read the file, and prepend a random number to sort on".  I'm curious if this is also true on your limited system, or if the sort and cut are actually taking a noticeable fraction of the total time.

I did a quick test on my machine.  With a *very* long file (119k lines), using the shell to prepend those numbers for sorting took about 8 seconds.  Using a very simple C program to do exactly the same thing took 0.2 seconds.  Unless someone comes up with something substantially faster than the read loop to prepend those numbers, you may need to install a compiler just to create a simple utility to speed up that part of the process.

Lloyd B.

---

### Post by wigout on 2010-09-16
I saved your script as func-test2
here's the output with the same 4000 line file I've been looking at.

```
./func-test2     
Appending :Fri Jan  1 00:04:03 CST 2010
Sorting   :Fri Jan  1 00:09:04 CST 2010
Cutting   :Fri Jan  1 00:09:05 CST 2010
Moving    :Fri Jan  1 00:09:06 CST 2010
Done      :Fri Jan  1 00:09:06 CST 2010

```

When I ran the code in its larger context (a playlist manager- the current routine is mixing 4000 music files in a playlist file), expressed like as in example 1 but with cut I got a start to finish of:
```
date; ./test-script; date
Fri Jan  1 00:11:03 CST 2010
Fri Jan  1 00:16:08 CST 2010
```

-wigout

---

### Post by lloyd_b on 2010-09-17
> **wigout said:**
> I saved your script as func-test2
here's the output with the same 4000 line file I've been looking at.

```
./func-test2     
Appending :Fri Jan  1 00:04:03 CST 2010
Sorting   :Fri Jan  1 00:09:04 CST 2010
Cutting   :Fri Jan  1 00:09:05 CST 2010
Moving    :Fri Jan  1 00:09:06 CST 2010
Done      :Fri Jan  1 00:09:06 CST 2010

```

When I ran the code in its larger context (a playlist manager- the current routine is mixing 4000 music files in a playlist file), expressed like as in example 1 but with cut I got a start to finish of:
```
date; ./test-script; date
Fri Jan  1 00:11:03 CST 2010
Fri Jan  1 00:16:08 CST 2010
```

-wigout

As I suspected - you're spending 5 minutes on that machine just prepending the numbers to allow the sort, and only a few seconds to actually perform the sort (and remove the numbers used for the sort).

If this is something that you need to run as fast as possible, then I strongly suggest installing a compiler, and finding/writing a C program to do the randomization for you - it will probably reduce the overall time required to a matter of 3 or 4 seconds, as opposed to the 5 minutes it's currently taking.

Shell scripting is wonderful for some things, and the fact that it's so portable is a bonus, but it is NOT generally going to be the best in terms of performance (for most jobs, performance is less of an issue than the time required to develop the solution).  

If you insist on sticking with shell scripting and the Busybox utilities for this job, I don't really expect you get get this process to run much faster.

Lloyd B.

---

### Post by wigout on 2010-09-17
I took your advice and download the sourcecode for a program called shuffle from:
[http://www.eskimo.com/~scs/src/]("http://www.eskimo.com/%7Escs/src/")

I used qemu in combination with a mipsel system image (my player is a mipsel machine) from:
[http://impactlinux.com/fwl/downloads/binaries/](http://impactlinux.com/fwl/downloads/binaries/)

I used the dev-environment.sh script from there, compiled shuffle, dropped it on my machine.

The "shuffle" of the 4000 line song took about one second.

So that's a huge time savings and worth the trouble- I think I'll keep the script in bash and "outsource" the shuffling to shuffle.

Thank you for your help here.

-wigout

---

