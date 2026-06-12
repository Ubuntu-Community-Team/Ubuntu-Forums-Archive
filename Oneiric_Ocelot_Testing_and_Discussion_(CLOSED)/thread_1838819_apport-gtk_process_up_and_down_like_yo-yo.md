---
title: "apport-gtk process up and down like yo-yo"
date: 2011-09-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ventrical on 2011-09-04
The process 'apport-gtk' seems to be using CPU  resources like a yo-yo.  This happening after applying a fix to the zeitgiest bug. I suspect that apport-gtk was doing this all the time. Is this a normal funtion for this process?

---

### Post by ventrical on 2011-09-04
whoops!!

---

### Post by Quackers on 2011-09-04
Agreed. At idle, every 5 or 6 seconds something fires up the cpu's to 35 - 40% and that appears to be apport-gtk. Not as bad here as on yours though.
As you said earlier the cpu usage shows but not in TOP or in TOP processes in conky either.

---

### Post by dino99 on 2011-09-04
dont have that but it crash each time i double-click on a crash file to send a bug report

---

### Post by ventrical on 2011-09-04
Thanks Quackers.

 I am not using my dual core on this laptop. I only have 1.60GHz so that explains  why I have a larger spike. My processor is not heating up but I just thought that I would make a note of it.

---

### Post by ventrical on 2011-09-04
> **dino99 said:**
> dont have that but it crash each time i double-click on a crash file to send a bug report

Yeah .. I got that too .. so I just ignore those flags. I think a lot of them are false positives.

---

### Post by ventrical on 2011-09-04
Here is a screenshot of my Dual Core with 3.0.0-9 kernel at idle just before screenshot.

I now have the zeitgeist-extension file locked in and am abotu to update to 3.0.0-10

---

### Post by ventrical on 2011-09-04
After full update  to 3.0.0.-10- no apport-gtk anomoly.

---

### Post by Quackers on 2011-09-05
No-one else seeing this?

---

### Post by RomeReactor on 2011-09-05
I see it here as well...

---

### Post by 23dornot23d on 2011-09-05
Same here ... was same yesterday too ......

[IMG]http://img535.imageshack.us/img535/1558/notnormalx.jpg[/IMG]

---

### Post by Quackers on 2011-09-05
Thanks, I was wondering if it was something peculiar to the OP and me :-)

---

### Post by 23dornot23d on 2011-09-05
Even after upgrades and a cold re-boot I am still getting the heart beats ...... at least its alive ...... 

weird too as nothing else ie firefox or applications .... are running ...... just the Monitor ....

This is straight after a fresh desktop login ....

[IMG]http://img64.imageshack.us/img64/1069/heartbeatw.jpg[/IMG]

But the upgrade has changed nothing for me (read on another thread the upgrades had sorted this ..... 
will try again tomorrow ...... in case something is late here ....

---

### Post by Quackers on 2011-09-06
I just turned apport off for the moment with the command below, supplied by lucazade :-)
```
sudo sed -i 's/enabled=1/enabled=0/g' /etc/default/apport 
```

---

### Post by VinDSL on 2011-09-06
> **Quackers said:**
> I just turned apport off for the moment with the command below, supplied by lucazade :-)
```
sudo sed -i 's/enabled=1/enabled=0/g' /etc/default/apport 
```
Don't mean to nitpick, but...

That turns it off permanently.  ;)

---

### Post by ventrical on 2011-09-06
I still have it on my single-processor Acer after updates but not on my dual-core. I wonder if VinDSLs' workaround for zeitgiest may apply in this case also?

Return to an earlier version?

So we would need to download  1.22.0ubuntu2

---

### Post by Quackers on 2011-09-06
> **VinDSL said:**
> Don't mean to nitpick, but...

That turns it off permanently.  ;)

That'll do fine until the cpu spiking is fixed :)

I presume it can be turned back on by reversing the enabled=1/enabled=0 
Would that be correct?

---

### Post by mc4man on 2011-09-06
You can turn it back on later if desired
This seems to only show on some installs, never seen here on a B1 from last wk. though did on Sun.'s build in a live session

You could try purging apport (removes 3 packages), doing a log out/in & re-installing the 3

Also, if desired, apport-gtk is not required for filing bugs thru 
ubuntu-bug <package name>
or 
apport-bug /var/crash/whatever.crash
ect.
So you could also just try removing apport-gtk

---

### Post by Quackers on 2011-09-06
Thanks mc4man.
I just ran some more updates and there was one for apport so I'll re-enable it and see what happens.
The other info you've given is good to know though.

---

### Post by ventrical on 2011-09-06
Yep ... thats it !! Right before my eyes :)


 Thanks everybody for your helps !

---

### Post by 23dornot23d on 2011-09-06
> **Quackers said:**
> I just turned apport off for the moment with the command below, supplied by lucazade :-)
```
sudo sed -i 's/enabled=1/enabled=0/g' /etc/default/apport 
```

Cheers Quackers

that will do me fine ..... until someone comes up with a fix ..... ty

[IMG]http://img600.imageshack.us/img600/66/fixed2.jpg[/IMG]

---

### Post by VinDSL on 2011-09-06
> **Quackers said:**
> That'll do fine until the cpu spiking is fixed :)

I presume it can be turned back on by reversing the enabled=1/enabled=0 
Would that be correct?
Correct!

---

### Post by Quackers on 2011-09-06
Cheers ears :-)

---

### Post by VinDSL on 2011-09-24
I just turned apport (back) on.

```

sudo sed -i 's/enabled=0/enabled=1/g' /etc/default/apport

```

Seems to working okay, now...  :)

---

### Post by VinDSL on 2011-09-25
Argh!  :p

Everything worked great, for 24 hours.  Then...

I started getting error dialogs up the ying-yang again.

Same old, same old.  
[LIST]
[*]Error pops up
[*]Click to report
[*]Report doesn't collect info
[*]Another error pops up
[*]Click cancel
[*]Another error pops up
[*]Blah, blah, blah
[/LIST]

So, I've disabled Apport again:

```

sudo sed -i 's/enabled=1/enabled=0/g' /etc/default/apport

```

---

### Post by ventrical on 2011-09-25
> **VinDSL said:**
> Argh!  :p

Everything worked great, for 24 hours.  Then...

I started getting error dialogs up the ying-yang again.

Same old, same old.  
[LIST]
[*]Error pops up
[*]Click to report
[*]Report doesn't collect info
[*]Another error pops up
[*]Click cancel
[*]Another error pops up
[*]Blah, blah, blah
[/LIST]

So, I've disabled Apport again:

```

sudo sed -i 's/enabled=1/enabled=0/g' /etc/default/apport

```


Same here . Thanks . Disabled.

---

