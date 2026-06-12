---
title: "A consistent way to kill processes (shell script)"
date: 2012-03-23
forum: Programming Talk
---

### Post by flurospar on 2012-03-23
I have stumbled upon a problem in which I have to kill a process by its name using a shell script. The script must be portable, and here arises the problem: some systems don't have [FONT=Courier New]pidof[/FONT] , others don't have [FONT=Courier New]killall[/FONT].

The problem aggravates with the fact I cannot determine whether [FONT=Courier New]pidof[/FONT] or [FONT=Courier New]killall [/FONT]is installed by using [FONT=Courier New]which[/FONT], because on some systems like Mac OS X, it is simply absent. On others, [FONT=Courier New]which <progname>[/FONT] produces the following outputi:

[FONT=Courier New]which: <progname>: unknown command[/FONT]

... but I want my script to work silently without any output, so this is not an option for me.

Is there some other platform-independent way to kill processes?

---

### Post by Habitual on 2012-03-23
> **flurospar said:**
> ...I cannot determine whether [FONT=Courier New]pidof[/FONT] or [FONT=Courier New]killall [/FONT]is installed by using [FONT=Courier New]which[/FONT],...

No, neither are install by which...

10.10/11.10
```

sudo dpkg -S $(which which) | cut -d: -f1
debianutils
sudo dpkg -S $(which pidof) | cut -d: -f1
sysvinit-utils
sudo dpkg -S $(which killall) | cut -d: -f1
psmisc

```Sorry I don't know Mac but this site may help...
[http://ss64.com/osx/](http://ss64.com/osx/)

```
kill -9 $$
 
```
may work across all. if called from inside the script.

---

### Post by sudodus on 2012-03-23
I think you can search for the process with
```
ps -A | grep \ procname$
``` for example
```
ps -A | grep \ ps$
```
where "\ " is the preceding space and "$" marks the end of line, so that you really find the process name and not another process. See the different output if you run
```
ps -A | grep ps
``` where I get the following output
```
[COLOR="RoyalBlue"]ps -A | grep ps[/COLOR]
  355 ?        00:00:00 upstart-udev-br
  516 ?        00:00:00 kpsmoused
 1297 ?        00:00:00 cupsd
 2970 pts/1    00:00:00 ps
```
So the following command
```
kill -9 $(ps -A | grep \ procname$|sed -e s/\ *// -e s/\ .*//)
``` should kill the process 'procname'.

---

### Post by Habitual on 2012-03-23
and I assumed his script was the process he intends to kill.

Bad doggy!? ;)

If it is NOT, then my reply won't work.

---

### Post by Vaphell on 2012-03-23
pgrep/pkill are nicer because you don't have to parse anything.

[http://linux.die.net/man/1/pkill](http://linux.die.net/man/1/pkill)

---

### Post by sudodus on 2012-03-23
> **Vaphell said:**
> pgrep/pkill are nicer because you don't have to parse anything.

[http://linux.die.net/man/1/pkill](http://linux.die.net/man/1/pkill)
Yes, that's true, but are they portable, which is necessary for the OP?

---

### Post by jwbrase on 2012-03-23
@OP: Posix specifies that a command by the name of "command" should exist, and that it should have an option "-v" that basically does the same thing as which.

Try "command -v killall".

That should be fairly portable.

> **Habitual said:**
> No, neither are install by which...

I don't think you understand the OP's question. He doesn't want to know if killall and pidof are part of the same package as which. He wants to use which to determine if killall and pidof exist on the system. The problem is that which does not exist on every system.

> Sorry I don't know Mac but this site may help...
[http://ss64.com/osx/](http://ss64.com/osx/)

Interesting. This link says that which *is* available on OS X.

> 
```
kill -9 $$
 
```
may work across all. if called from inside the script.

No, that will kill the shell process itself, which is not at all what the OP is trying to do.

---

### Post by sisco311 on 2012-03-23
Not sure what exactly are you trying to accomplish here, but it sounds like an [XY problem]("http://mywiki.wooledge.org/XyProblem"). :evil:

You might want to check out:
[http://mywiki.wooledge.org/ProcessManagement](http://mywiki.wooledge.org/ProcessManagement)
and
BASH FAQ 042 and 033 (link in my signature);

and of course, if you are looking for a portable solution, then also check out the POSIX specification: [http://pubs.opengroup.org/onlinepubs/9699919799/utilities/contents.html](http://pubs.opengroup.org/onlinepubs/9699919799/utilities/contents.html)

---

