---
title: "32-bit; Firefox + Flash =OMNOMNOM to CPU."
date: 2008-09-28
forum: New to Ubuntu
---

### Post by Grimhound on 2008-09-28
I've had a /lot/ of issues with Firefox 3 and Flash on my 32-bit Hardy setup. It's crashed, freaked out, and done a variety of other things less than desirable. Just a moment ago while trying to watch a video, I noticed that it dragged the entire system through the mud. I looked at the System Monitor, and made a test of it to display the system resource usage by Flash within Firefox 3.

[IMG]http://img517.imageshack.us/img517/592/omnomnomwm1.png[/IMG]
](*,)

---

### Post by kansasnoob on 2008-09-28
Look at post #7 here:

[http://ubuntuforums.org/showthread.php?t=919695](http://ubuntuforums.org/showthread.php?t=919695)

---

### Post by gjoellee on 2008-09-28
If you are using flash 9, upgrading to flash 10 usually helps. Download here: [http://www.kshoster.net/node/39](http://www.kshoster.net/node/39)

---

### Post by Grimhound on 2008-09-28
> **gjoellee said:**
> If you are using flash 9, upgrading to flash 10 usually helps. Download here: [http://www.kshoster.net/node/39](http://www.kshoster.net/node/39)

Already using 10.

> **kansasnoob said:**
> Look at post #7 here:

[http://ubuntuforums.org/showthread.php?t=919695](http://ubuntuforums.org/showthread.php?t=919695)
I had already done all of that. Hasn't really improved much in resource use.

My real hope is that they fix this in 8.10 so the rigamarol isn't necessary. >_>

Edit: Just did what you recommended /again/, loaded a Flash video after relogging, and boom. 95-100% CPU use. That shouldn't happen. :P

Flash on Firefox on Ubuntu SUCKS.

---

### Post by Grimhound on 2008-09-28
I guess there will never be a fix for Flash + Firefox when it comes to Ubuntu in this generation. :(

---

### Post by Grimhound on 2008-09-28
No ideas on how to make Flash not suck up processor resources?

---

### Post by skullmunky on 2008-09-29
I don't have an answer, but it -is- possible.  I'm using ff3 and flash player 9, 8.04 32 bit, no special tweaks, and I get around 50% max when watching video fullscreen.  doesn't help you, I know, but maybe can be encouraging ...

how about with FF2?

---

### Post by carolinason on 2008-10-05
i would think the flash+ff problem is upstream and not ubuntu's fault. i experience the problem in debian as well.

---

### Post by carolinason on 2008-10-05
i also tried downgrading to ff2, dependency issue, even though i could try a bzip version from an archive, ad epiphany, no go.

---

### Post by kansasnoob on 2008-10-06
> **Grimhound said:**
> Already using 10.


I had already done all of that. Hasn't really improved much in resource use.

My real hope is that they fix this in 8.10 so the rigamarol isn't necessary. >_>

Edit: Just did what you recommended /again/, loaded a Flash video after relogging, and boom. 95-100% CPU use. That shouldn't happen. :P

Flash on Firefox on Ubuntu SUCKS.

So, flash/firefox is not crashing?

Install flashblock:

```
sudo apt-get install flashblock
```

And no, it won't stop you from using flash! You'll just see a F button where the Flash would usually be. Click on it and you'll see flash!

---

### Post by Nider on 2008-10-06
I tried to install Flash 10 and I could because it said 

ERROR: Dependency is not satisfiable: libnss3-1d

What does this mean!?

> **kansasnoob said:**
> So, flash/firefox is not crashing?

Install flashblock:

```
sudo apt-get install flashblock
```

And no, it won't stop you from using flash! You'll just see a F button where the Flash would usually be. Click on it and you'll see flash!

I also tried the flashblock thing, and after I type sudo apt-get install flashblock, it said 

E: Couldn't find packge flashblock

---

### Post by kansasnoob on 2008-10-06
Also where you've tried lots of different flash installs it'd be good to type:

> about:PLUGINS

in the URL window. (btw that can be upper or lower case, I just use upper case so I don't end up with this: about:plugins)

I've gotten frustrated with this also but I swear my fix works! I should say my combination of fixes works! I didn't figure out anything, I just picked what works from really smart people!

---

### Post by kansasnoob on 2008-10-06
> **Nider said:**
> I tried to install Flash 10 and I could because it said 

ERROR: Dependency is not satisfiable: libnss3-1d

What does this mean!?

What source were you installing from?

What version of Ubuntu do you have?

---

### Post by kansasnoob on 2008-10-06
Nider,

You should start your own thread.

Specify what version of Ubuntu you're using and the specific problem(s) you're having.

Fixes for one version of Ubuntu will not work on others!

---

