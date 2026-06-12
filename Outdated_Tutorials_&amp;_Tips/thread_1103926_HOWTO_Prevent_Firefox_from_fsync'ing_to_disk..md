---
title: "HOWTO: Prevent Firefox from fsync'ing to disk."
date: 2009-03-23
forum: Outdated Tutorials &amp; Tips
---

### Post by ibuclaw on 2009-03-23
**Overview**
Firstly, I'd like to give all credit to sdennie for the idea he shared. This is my implementation of it, that I managed to post up before him. ;)

This guide is intended for anyone on Laptops who are taking measures to decrease disk activity, as shown on this howto [here.]("http://ubuntuforums.org/showthread.php?t=839998") Or anyone who is annoyed at firefox (along with SQLite) constantly fsyncing to disk, which could potentially also slow down the speed of the browser too if you are having to wait for the fsync to complete before continuing.

**Implementation**
It's has been a well known fact since the time of Firefox-3.0beta, Firefox constantly fsync's to disk after each time you load/reload a webpage. References as stated below:
[LIST]
[*]Launchpad Bug Report: [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/221009](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/221009)
[*]Mozilla Bug Report: [https://bugzilla.mozilla.org/show_bug.cgi?id=421482](https://bugzilla.mozilla.org/show_bug.cgi?id=421482)
[*]A Mozilla Developer's Blog: [http://shaver.off.net/diary/2008/05/25/fsyncers-and-curveballs/](http://shaver.off.net/diary/2008/05/25/fsyncers-and-curveballs/)
[/LIST]
As can be seen if you run this in a terminal:
```
strace -p `pidof firefox` -e trace=fsync,fdatasync
```

**The fix**, we create a new library with a our own definition of [fsync()]("http://www.opengroup.org/onlinepubs/009695399/functions/fsync.html") inside.
Or, for the technically adept explanation. We turn fsync() into a [NOP function.]("http://en.wikipedia.org/wiki/Nop")

**Steps**
1) Create a new file. Let's name it **fsync.c** for simplicity
```
gedit fsync.c
```
And create our function inside it.
```

int fsync (int fd)
{
    return 0;
}

```
Save and Quit.

2) Compile our library.
```
gcc -fPIC -g -c -Wall fsync.c
```
And link it
```
gcc -shared -Wl,-soname,fsync.so -o fsync.so fsync.o -lc
```
3) Install the library into a logically named directory. (ie: /usr/local/lib or ~/.mozilla)
```
sudo install fsync.so /usr/local/lib
```
4) Assign the library to the **LD_PRELOAD** shell variable.
```
export LD_PRELOAD=/usr/local/lib/fsync.so
```
5) Run firefox
```
firefox &
```
Now run the strace command on it again, and fsync() will be nowhere to be seen.

**Putting it into Practice**

One way to set this the default on all Firefox Desktop icons in Ubuntu, we are going to create a script to be put in the /usr/local/bin directory.
```
gedit firefox
```
And put the following inside:
```

#!/bin/sh
export LD_PRELOAD=/usr/local/lib/fsync.so && /usr/bin/firefox "$@"

```
Save and Quit, now install it.
```
sudo install firefox /usr/local/bin
```
And you are all done.

**Extending this HOWTO**
You can, if you choose, re-implement fdatasync() too, to prevent firefox calling that function, but I would recommend not to due to the differences in the functions, as stated [here.]("http://linux.die.net/man/2/fsync") In short, fdatasync is a more mission-critical sync, whereas fsync just attempts to sync everything regardless of it's state in cache.
However, feel free to extended this HOWTO at your own discretion, fdatasync is defined in the same way fsync is, just incase anyone tries.


Questions/Comments/Suggestions on clean-up are welcome.

Regards
Iain

---

### Post by sdennie on 2009-03-23
I should give you more ideas.  That way I don't have to test them and can just follow your tutorial after you implement them.

---

### Post by paultag on 2009-03-24
outstanding work ian, you tricky brit.

enjoyed this a lot. You should try this with low bandwidth devices such as distros working off of a USB.

Cheers!

---

### Post by ibuclaw on 2009-03-24
@Paultag: Thanks! I'm using this on my Acer Aspire One SSD atm... I am almost certain that firefox is quicker because of this tweak... but I don't know, it may be just a placebo. (Needs benchmarking, for sure).
I'm also how amazed that my laptop has HDD kept spun down too. Usually it's spinning up every 10-20 seconds and generally driving me nuts (Yes, I do use tweaked hdparm settings for Battery Life's sake, but 0.8 Watts of power consumption when spun down is an option I'm willing to take :D).

@Vor, continue to enlighten me with your random thoughts and ideas :)

Regards Iain

---

### Post by smbm on 2009-03-24
Hi

Looks like a great tutorial, got a couple of questions though.

Does this have any implications for data integrity if;

A crash were too occur

You're using EXT4

Sorry if these are silly questions.

Cheers

---

### Post by sdennie on 2009-03-24
> **smbm said:**
> Hi

Looks like a great tutorial, got a couple of questions though.

Does this have any implications for data integrity if;

A crash were too occur

You're using EXT4

Sorry if these are silly questions.

Cheers

Any guide who's purpose is to reduce the frequency which your disk is written to comes with an implicit, "If your machine isn't stable, don't do this because you will lose data".  It doesn't really matter what filesystem you are using, if you crash, you are going to lose data (though, admittedly, it's probably worse with ext4).

---

### Post by smbm on 2009-03-24
Excellent. I'll proceed with caution.

Thank you very much :)

---

### Post by Vadi on 2009-03-24
Good workaround, but too much work for me to do :-/

---

### Post by ibuclaw on 2009-03-30
> **smbm said:**
> Excellent. I'll proceed with caution.

Thank you very much :)

If you do use ext4 and do experience an instability, kernel panic, or crash. Remember, you can always use the Magic SysRq keys to safely reboot.

To ensure that it isn't turned off:
```
echo 1 | sudo tee /proc/sys/kernel/sysrq
```
And in an event of a system crash, you may be able to save yourself with this key combination sequence:

**Alt + PrintScreen** + **R**, **E**, **I**, **S**, **U**, **B**

Or, if you are truly paranoid, begin with **Alt+Screen+S** which should perform an emergency sync of all cached memory back to the hard drive.

Regards
Iain

---

### Post by memories on 2009-04-13
I noticed the syncing as well and I turned off browser.cache.disk.enable in about:config (set to false). 

Firefox is always open, forever, and I have enough RAM that I never need to swap, so it made sense logically. I have noticed that it doesn't hang so much anymore when I have lots of stuff open. Actually now that I think about it, it's quite faster than it was before. 

I'll try your hack. Thanks.

---

### Post by sdennie on 2009-04-14
The syncing described here is caused by the way firefox uses sqlite and the fact that it writes to places.sqlite after every page loads (and that causes an fsync).  Turning off the browser cache isn't a great idea but shouldn't cause any problems.  Redirecting it to a tmpfs is a great idea though.

---

### Post by ibuclaw on 2009-04-14
> **sdennie said:**
> The syncing described here is caused by the way firefox uses sqlite and the fact that it writes to places.sqlite after every page loads (and that causes an fsync).  Turning off the browser cache isn't a great idea but shouldn't cause any problems.  Redirecting it to a tmpfs is a great idea though.

It is an especially great idea if you know what you are doing and get the crons that copy the data back to harddrive setup correctly. (Else, you are loosing all saved data every time you shutdown).

---

### Post by rblyngso on 2009-07-12
Thanks a lot! Running Ubuntu/firefox on my Aspire One with SSD was slow (to put it mildly) before applying this hack.

Another way of applying the hack:

I put the fsync.so in **/opt/mozilla/lib/** and created the following **/usr/local/bin/firefox** (with executable bit set):


```
 #!/bin/sh

export LD_PRELOAD=/opt/mozilla/lib/fsync.so
/usr/bin/firefox "$@"

```

Regards,
Regnar

---

### Post by ibuclaw on 2009-07-12
> **rblyngso said:**
> Thanks a lot! Running Ubuntu/firefox on my Aspire One with SSD was slow (to put it mildly) before applying this hack.

Another way of applying the hack:

I put the fsync.so in **/opt/mozilla/lib/** and created the following **/usr/local/bin/firefox** (with executable bit set):


```
 #!/bin/sh

export LD_PRELOAD=/opt/mozilla/lib/fsync.so
/usr/bin/firefox "$@"

```

Regards,
Regnar

May I just note that since the release of Firefox 3.5, this problem has been none existent.

So the best solution for everyone in the end is to upgrade to Karmic Koala when the Official Release comes through in October. :)

Regards
Iain

---

### Post by DLGandalf on 2010-01-14
ehh, I'm experiencing this under karmic and lucid.

---

