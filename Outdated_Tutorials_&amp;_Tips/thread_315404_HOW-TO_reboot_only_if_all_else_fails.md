---
title: "HOW-TO reboot only if all else fails"
date: 2006-12-09
forum: Outdated Tutorials &amp; Tips
---

### Post by xyz on 2006-12-09
I searched the forum but didn't find this HowTo. Sorry if I missed it somehow.

I learned it when I was using Mandriva. 
If your system doesn't react at all, *you are totally stuck*, and even Ctrl+Alt+backspace gives nothing, try and 'save' the following phrase somewhere in your mind:

**R**aising **S**kinny **E**lephants **I**s **U**tterly **B**oring

Hit the following key sequences; do give it some time between each keystrokes:
*( SysRq = print screen ) (Use the LEFT Alt key )*
```
Alt+SysRq+r 
Alt+SysRq+s
Alt+SysRq+e
Alt+SysRq+i
Alt+SysRq+u
Alt+SysRq+b
```

> The r stands for put keyboard in raw mode
The s for sync the disk
The e for terminate all processes
The i for kill all processes
The u for remount all filesystems read only
The b for reboot the system

**Use it as a procedure only if all else fails!!**

_Please pay attention to the following:_
> PS: If your filesystem is Ext3 or ReiserFS and on reboot it wants you to do a filesystem check, don't touch any key when it asks you to press "Y" and let it recover the journal automatically.

NOTE: For the skinny elephants to work you need to have the sysrq-key enabled in the kernel. (CONFIG_MAGIC_SYSRQ)
You can check if it is enabled by typing 'ls /proc/sys/kernel/sysrq' if it's there, it's enabled.
Thanks to Mischa for pointing this out. 
I found out about this here:
[BY BRUNO]("http://www.brunolinux.com/01-First_Things_To_Know/Skinny_Elephants.html")

---

### Post by outofnicks on 2006-12-09
Is this preferable to a hard shutdown? That is, holding the power button in on my Dell tower until it powers down--?

---

### Post by xyz on 2006-12-09
I think ANYTHING is better than a hard shutdown!
The "Raising Skinny Elephants Is Utterly Boring" allows for gradual 'shutdown'.

---

### Post by kackler on 2006-12-09
run the command "shutdown -r now" to reboot or "shutdown -h now" to power down completely.

---

### Post by dbott67 on 2006-12-09
> **kackler said:**
> run the command "shutdown -r now" to reboot or "shutdown -h now" to power down completely.

As the original poster mentions:
> If your system doesn't react at all, you are totally stuck, and even Ctrl+Alt+backspace gives nothing, try and 'save' the following phrase somewhere in your mind

If you're system is locked/frozen/stuck, you won't be able to open a terminal...

---

### Post by ajm2005 on 2006-12-09
:)

---

### Post by flargen on 2006-12-09
I prefer to use alt + sysrq + k to kill all processes on the current terminal. It is especially useful if the X server dies and alt + ctrl + backspace doesn't work, because it allows you to log in again without restarting you computer.

---

### Post by xyz on 2006-12-12
> alt + sysrq + k
Just wondering if that wouldn't be a bit drastic?

---

### Post by mdowney on 2006-12-12
Is there any way to do this with a Mac keyboard?  I don't have a SysRq key.

---

### Post by outofnicks on 2006-12-12
My Macs don't have Ubuntu so don't know if this would work but the F13 key is in the same location, and also is labeled "Print Screen" as on the PC keyboard. But on my 97-key USB Mac keyboard, which you may have, that block of keys doesn't exist. There is a "help" key to the right of the F12 key, which may also work? Or possibly this is a PC-only thing?

---

### Post by xyz on 2006-12-13
> **mdowney said:**
> Is there any way to do this with a Mac keyboard?  I don't have a SysRq key.
Well I don't have a Mac so...
[Mac OS X keyboard shortcuts]("http://docs.info.apple.com/article.html?artnum=75459")
Sorry if you already know about this but you may find what you need there.
What about what "outofnicks" suggested?
Let us know...

---

### Post by mdowney on 2006-12-13
Not really sure, its a USB Mac keyboard, they standard 103 key one.  I think the Mac shortcuts will only work in Mac OS X.  I have not had a chance to try the F13 combo, yet.  Next time I get a hardlock in X I will try it.

---

### Post by tenghoward on 2006-12-13
Is this type of shutdown will result data lost? If so, maybe I need to use my backup copy if I use this method.

---

### Post by xyz on 2006-12-14
> **tenghoward said:**
> Is this type of shutdown will result data lost? If so, maybe I need to use my backup copy if I use this method.
I have used it several times and never lost anything. Just wait 15-20 seconds between each keystroke as a precaution.
Good day!

---

### Post by drphilngood on 2006-12-14
Thanks for sharing this, xyz.

---

### Post by outofnicks on 2006-12-14
> **mdowney said:**
> Next time I get a hardlock in X I will try it.

All I need is to have several OpenOfficedocs, a bunch of big pics in The Gimp, Firefox and Thunderbird open at the same time--that does it :rolleyes: ,

---

### Post by xyz on 2006-12-15
> **drphilngood said:**
> Thanks for sharing this, xyz.
You're welcome.

---

### Post by mozkill on 2006-12-15
I usually reboot using the command "init 6"  .  is there anything wrong with doing it that way?

---

### Post by fraenhawk on 2006-12-15
moz: As was stated already, the point of this is if your computer is not responding. If it's not responding, how/where are you going to type "init 6" anywhere?

xyz: I'll definitely have to keep this in mind, although I have to say I've only really been in a situation this would help with once that I can remember.

---

### Post by xyz on 2006-12-19
fraenhawk..knock on wood! 
> ...I've only really been in a situation this would help with once that I can remember.
Reply With Quote
...and the one and only time you may be in that situation...well that's when you'll need to remember it. It's good to have that solution at hand when -and IF- you need it.

---

### Post by rfdeshon on 2007-01-26
Thanks for this, my edgy install locks up every couple days. This is a lot better than hard reseting my laptop every time. Does anyone else have problems with X after an upgrade from Dapper to Edgy where the keyboard will stop responding and no new applications will launch but everything else seems to be running?

---

### Post by ltk5 on 2007-01-26
hm... interesting. Would have to try it, everything is better that just Power Off.:o

---

### Post by outofnicks on 2007-01-26
Having forgotten about this trick, or just failing to write it down somewhere, I've used Ctl-Alt-Delete which simply logs me out so I can log in for a fresh start. Anything wrong with this?

update:
> If your system doesn't react at all, you are totally stuck, and even Ctrl+Alt+backspace gives nothing,
oops, never mind...

---

### Post by durand on 2007-01-26
um...what about ctrl+alt+f1(etc)

---

### Post by of_darkness on 2007-01-28
Have had several hardlocks so i tried the above keys in the sequens posted n then evry other key on the keybord but*too no effect at all.. kubuntu edgy n a swedish*logitech wireless keybord..whith swedish key mapp layout..

---

### Post by firstc624 on 2007-01-28
i can't ge this to wrok even when not in a hard lock.  i have a laptop and when it is actually running i get  a print screen image

---

### Post by xyz on 2007-02-12
> **durand said:**
> um...what about ctrl+alt+f1(etc)
I'll have to try next time but I have a feeling even that wouldn't work when totally stuck.

*of_darkness*
I sure wish I could understand why a Swedish keyboard layout would prevent this from working? What would then be the **SysRq** key equivalent?

---

### Post by durand on 2007-02-16
it doesnt...

---

### Post by Nonno Bassotto on 2007-02-19
> For the skinny elephants to work you need to have the sysrq-key enabled in the kernel.

is it enabled by default in the Ubuntu kernel? When I type
```

ls /proc/sys/kernel/sysrq

```
I just get
```

/proc/sys/kernel/sysrq

```

---

### Post by muguwmp67 on 2007-02-19
My solution to the reboot issue was reconfiguring my power button.  

Preferences>Power Management
General tab
change the action when the power button is pressed.

This performs a clean (I think)  shut down when I press the power button.  None of that hard shutdown stuff now.  You won't want to do this if you have a power button on your machine that is susceptible to being pressed by accident, but it works for me.

---

### Post by xyz on 2007-02-20
> This performs a clean (I think) shut down when I press the power button.
I have no idea if this does an OKish shutdown.

For the other folks, I'll redirect you to [Tony Luck's site]("http://developer.osdl.org/dev/robustmutexes/REPOS/fusyn.hg/?cmd=file;filenode=32d0a5eb8f92fa9221a6311440ffafbc042e510b;file=Documentation/sysrq.txt") because it is explained much better/ more precisely than I could.
Let us know if this worked for you! Thx.

---

### Post by xyz on 2007-02-24
**Please pay attention to this:**
> PS: If your filesystem is Ext3 or ReiserFS and on reboot it wants you to do a filesystem check, don't touch any key when it asks you to press "Y" and let it recover the journal automatically.

NOTE: For the skinny elephants to work you need to have the sysrq-key enabled in the kernel. (CONFIG_MAGIC_SYSRQ)
You can check if it is enabled by typing 'ls /proc/sys/kernel/sysrq' if it's there, it's enabled.
Thanks to Mischa for pointing this out.
*_It's been added to the original post._*

---

### Post by n8bounds on 2007-02-24
This is from source docs:

[http://lxr.linux.no/source/Documentation/sysrq.txt](http://lxr.linux.no/source/Documentation/sysrq.txt)

---

### Post by xyz on 2007-11-03
Hi Gutsy Users,

Does this work for you? Does for me.

---

### Post by Endolith on 2007-11-05
I just used this for the first time.  I'm in Gutsy, and it worked without changing anything in the kernel.

My computer locked up about two hours ago.  I saw from the system monitor applet that the memory and swap space were maxed out, and I couldn't open virtual terminals or anything.  I went to bed, expecting it to solve itself after a while.  I came back now and it was still locked up.

You should really note Alt+SysRq+F, though, which kills the process that's using the most memory.  That got me back into GNOME, but things weren't working right anymore.  The keyboard was completely dead, and the window manager wasn't behaving correctly.  I looked around to see if there was any unsaved data and then did these steps.  It worked.  Thanks!

---

### Post by joopbraak on 2011-05-04
> **xyz said:**
> NOTE: For the skinny elephants to work you need to have the sysrq-key enabled in the kernel. (CONFIG_MAGIC_SYSRQ)
You can check if it is enabled by typing 'ls /proc/sys/kernel/sysrq' if it's there, it's enabled.

It's actually like this:

You can check if it is enabled by typing 
```
cat /proc/sys/kernel/sysrq
```
if the command returns "1" the sysrq-key is enabled.

If it returns "0" you can enable it with
```
echo 1 > /proc/sys/kernel/sysrq
```

---

