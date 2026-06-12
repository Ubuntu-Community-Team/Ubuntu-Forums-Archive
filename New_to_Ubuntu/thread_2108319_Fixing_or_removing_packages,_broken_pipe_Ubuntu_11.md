---
title: "Fixing or removing packages, broken pipe Ubuntu 11.10"
date: 2013-01-24
forum: New to Ubuntu
---

### Post by Resplendent Raven on 2013-01-24
About 2 weeks ago the update manager popped up and I just updated all the recommended packages like I usually do.
But for some reason this time something went wrong.
Whenever I try to use the 3.0.0-29, my screen resolution is all messed up.
What's worse however is that I can't update software anymore or install new software.
I have managed to ignore the problem for a while (by using .28), but I would really like to fix it now.

I should explicitly mention that 3.0.0-29 failed to install properly.

---

### Post by omeomi on 2013-01-24
What error message(s) do you get when trying to update/install the kernel or other software?

---

### Post by Resplendent Raven on 2013-01-24
```
De afhankelijkheden van de volgende pakketten konden niet geïnstalleerd worden:

linux-headers-3.0.0-29-generic: Depends: linux-headers-3.0.0-29 maar het is niet geïnstalleerd
linux-headers-generic-pae: Depends: linux-headers-3.0.0-30-generic-pae maar het is niet geïnstalleerd
```

Not sure how to change the language of these error messages, but it shouldn't be a problem for you. :)

Basically I can't install the dependencies and I also get broken pipe and BrokenCount>0 messages.
Also no space left on device messages , but I have atleast 500mb and according to Gparted I have 1.1 GiB on / left, so I doesn't really make sense to me.

---

### Post by bodhi.zazen on 2013-01-24
> **Resplendent Raven said:**
> ```
De afhankelijkheden van de volgende pakketten konden niet geïnstalleerd worden:

linux-headers-3.0.0-29-generic: Depends: linux-headers-3.0.0-29 maar het is niet geïnstalleerd
linux-headers-generic-pae: Depends: linux-headers-3.0.0-30-generic-pae maar het is niet geïnstalleerd
```

Not sure how to change the language of these error messages, but it shouldn't be a problem for you. :)

Basically I can't install the dependencies and I also get broken pipe and BrokenCount>0 messages.
Also no space left on device messages , but I have atleast 500mb and according to Gparted I have 1.1 GiB on / left, so I doesn't really make sense to me.

As far as the no space on device, do you have a separate /boot partition ? Is your /boot partition full ?

---

### Post by Resplendent Raven on 2013-01-24
I don't think I have a separate boot partition.
Gparted shows only a / and /Home mountpoint, if that is sufficient to tell.

---

### Post by bodhi.zazen on 2013-01-24
> **Resplendent Raven said:**
> I don't think I have a separate boot partition.
Gparted shows only a / and /Home mountpoint, if that is sufficient to tell.

Post the output of :

```
df -h
```

---

### Post by Resplendent Raven on 2013-01-24
```
Bestandssysteem            Grtte Gebr Besch Geb% Aangekoppeld op
/dev/sda7              11G  9,8G  584M  95% /
udev                  2,0G  4,0K  2,0G   1% /dev
tmpfs                 805M  864K  804M   1% /run
none                  5,0M     0  5,0M   0% /run/lock
none                  2,0G  128K  2,0G   1% /run/shm
/dev/sda8              22G  8,4G   13G  41% /home

```

---

### Post by bodhi.zazen on 2013-01-24
Nothing obvious, try

```
sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade
```

Post any error messages you get (entire text please).

---

### Post by Resplendent Raven on 2013-01-24
The first didn't seem to do anything, the second returned no error messages.

The third returns this:

```
Pakketlijsten worden ingelezen... Klaar
Boom van afhankelijkheden wordt opgebouwd       
Statusinformatie wordt gelezen... Klaar  
U kunt 'apt-get -f install' uitvoeren om dit op te lossen.
De volgende pakketten hebben niet-voldane vereisten:
 linux-headers-3.0.0-29-generic : Vereisten: linux-headers-3.0.0-29 maar het is niet geïnstalleerd
 linux-headers-generic-pae : Vereisten: linux-headers-3.0.0-30-generic-pae maar het is niet geïnstalleerd
E: Er zijn vereisten waaraan niet voldaan is. Probeer -f te gebruiken.

```

Pakketlijsten=Packetlists
Boom van afhankelijkheden=Tree of dependencies

---

### Post by oldos2er on 2013-01-24
11GB is small for a root partition (95% full!), I'd make it twice as big if possible.

---

### Post by Resplendent Raven on 2013-01-24
> **oldos2er said:**
> 11GB is small for a root partition (95% full!), I'd make it twice as big if possible.

Hmm I was under the impression that should be quite enough.
Any ideas how I could remedy this?

---

### Post by Resplendent Raven on 2013-01-24
I already tried to remove some software, but because of the broken pipe errors I can't install or remove...

---

### Post by oldos2er on 2013-01-24
Take a look at [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by bodhi.zazen on 2013-01-24
> **Resplendent Raven said:**
> The first didn't seem to do anything, the second returned no error messages.

The third returns this:

```
Pakketlijsten worden ingelezen... Klaar
Boom van afhankelijkheden wordt opgebouwd       
Statusinformatie wordt gelezen... Klaar  
U kunt 'apt-get -f install' uitvoeren om dit op te lossen.
De volgende pakketten hebben niet-voldane vereisten:
 linux-headers-3.0.0-29-generic : Vereisten: linux-headers-3.0.0-29 maar het is niet geïnstalleerd
 linux-headers-generic-pae : Vereisten: linux-headers-3.0.0-30-generic-pae maar het is niet geïnstalleerd
E: Er zijn vereisten waaraan niet voldaan is. Probeer -f te gebruiken.

```

Pakketlijsten=Packetlists
Boom van afhankelijkheden=Tree of dependencies

Try ```
sudo apt-get -f install
```

If that fails, see

[http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/](http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/)

---

### Post by Resplendent Raven on 2013-01-24
Thank you [[COLOR=#DD4814]**oldos2er**[/COLOR]]("http://ubuntuforums.org/member.php?u=338320"), after looking on that page I decided to remove some of my older kernels (including .29)
And the problem seems to be gone. :)

bodhi.zazen, I had tried sudo apt-get -f install a few times, but that never helped either.
It seems I just needed synaptic manager to remove some older kernels including the failed .29 install.

---

### Post by oldos2er on 2013-01-24
You're welcome.

---

### Post by ogyu1 on 2013-01-24
Hi Resplendent Raven to free up even more hard drive space you can try this commands:
```
 sudo apt-get clean 
``` - to erase downloaded archive files 
and
```
 sudo apt-get autoremove 
``` - to Remove automatically all unused packages
check ```
 man apt-get 
``` for more information.You can free up to 1Gb or more.Good luck ;).

---

