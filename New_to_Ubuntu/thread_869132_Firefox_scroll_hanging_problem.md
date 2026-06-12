---
title: "Firefox scroll hanging problem"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by Raistlin82 on 2008-07-24
Hi all,

I'm running hardy and have encountered a few problems with Firefox 3. The problems I have been having are:

When scrolling Firefox hangs for an age

If i have closed Firefox and then later want to open it again i get the error message - Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system.

These problems seem to be getting more frequent, and as such, more annoying :( Since my move to Ubuntu a couple of months ago I've found Firefox to be great, but since version 3 its been a downhill experience (with the browser not the OS - which is awesome!!) if anyone can help fix the problems i  have encountered please let me know

---

### Post by bbqsandwich on 2008-07-24
> **Raistlin82 said:**
> If i have closed Firefox and then later want to open it again i get the error message - Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system.

Well, to kill the Firefox process, you can open a terminal and type

```
ps -e
```

You will see a list of processes. Find firefox, and look for the four-digit process number next to it. Then in a terminal type:

```
sudo kill ####
```

where #### is the process number. But that doesn't address your greater problem of performance issues.

Personally I prefer Firefox over Opera because some sites just don't work well in Opera. Also Firefox has great add-ons to customize it, like NoScript, Greasemonkey, Stylish, Firebug, etc.

---

### Post by Raistlin82 on 2008-07-24
Next time it happens i'll try your suggestions.... dont know why I didnt think of sudo kill, doh! Still a bit of an annoyance though.  Is it possible to downgrade to a pervious version of Firefox or is that just a bad idea?

---

### Post by bbqsandwich on 2008-07-24
> **Raistlin82 said:**
> Next time it happens i'll try your suggestions.... dont know why I didnt think of sudo kill, doh! Still a bit of an annoyance though.  Is it possible to downgrade to a pervious version of Firefox or is that just a bad idea?

It is possible to downgrade but I would advise against it because the latest version has the latest patches against security threats.

But if you really want to do it, try one or both of the two sets of instructions in this thread:

[http://ubuntuforums.org/showthread.php?t=770789](http://ubuntuforums.org/showthread.php?t=770789)

---

### Post by ice60 on 2008-07-24
opera is better then firefox, so you should use opera lol.

you can get the process id of firefox like this -
```
pidof firefox
```

and you can kill every process that has the name firefox in it with this command
```
pkill firefox
```
firefox should be the only program with firefox in it's name so you should be safe to just run that!!

opera is about as customisable as firefox, maybe more so, but no one seems to know about it, i don't know why???

---

### Post by Raistlin82 on 2008-07-24
> **bbqsandwich said:**
> It is possible to downgrade but I would advise against it because the latest version has the latest patches against security threats.

But if you really want to do it, try one or both of the two sets of instructions in this thread:

[http://ubuntuforums.org/showthread.php?t=770789](http://ubuntuforums.org/showthread.php?t=770789)

thats kinda what i figured, would rather stay up to date with all the security updates.  Anyone else have the mid-scroll hang on Firefox?

---

### Post by rlandrum on 2008-07-28
I too have had my share of problems with firefox.

My problem is that firefox will crash, and then I can't get it to start again.  The only remedy seemed to be a reboot (ala windows).

After some thought, it occured to me that the problem must therefore be in /tmp, since it's cleared on reboot.  Further investigation (with strace) revealed that firefox was attempting to open a previously opened esd socket, which it was unable to do, and eventually timed out attempting.

My fix was:

```

killall firefox
rm /tmp/.esd-*

```

This is consistent with the bulk of my crashes...  Which almost always occur when playing video or loading flash that involves sound (like pandora), both cases involving esd.

---

### Post by fatriff on 2011-03-24
So many people complain about this.. Most of them have compiz enabled.. Things stutter and pause when scrolling because your card can't hack the load or you have the wrong driver installed for it.

I too had this issue and the solution was simple and now i'm flying like never before! Before, just having 4 tabs open caused serious slowdown and jerking and pausing while scrolling.. Now I have non and I can have 10 tabs open if I like and more than 1 playing video perfectly and this is on a 1.6ghz toshiba laptop with 1GB of ram.

Disable compiz if you want the speed you deserve..

If you don't want to disable it then install the new firefox 4 as it flys anyway compared to the last version.

---

