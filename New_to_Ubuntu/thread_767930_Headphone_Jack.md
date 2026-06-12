---
title: "Headphone Jack"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by goodywitch on 2008-04-26
So I've been googling trying to figure this out, and I may as well ask someone who may somewhat know what they are doing.  If there is an applicable forum, please let me know (I tried searching, but I'm still confused)

I "installed" ubuntu using wubi
Everything (didn't test printer or ipod) so far works well except for my headphone jack
Sound is coming from my computer, but it ignores my headphone jack.
I plug it in, no sound comes from it my headphones and my speakers are unaffected (it keeps playing)
I d/l updated alsa drivers (not sure if I installed it correctly)
I also tried to modify the /etc/modprobe.d/alsa-base as per other forums, but I'm not allowed to make any changes (but I'm the only user on this computer)????  How did that happen?

Any advice?  I'd love to be able to completely stop using windows (my battery actually lasts twice as long than vista, w/ compfiz at full prettiness)

My computer is a Toshiba Satellite A135-S4666, working on Hardy Heron.  If there's any more info you need to assist me (VERY GRATEFUL for any advice) please let me know.

Um, yea, total newbie, no knowledge of command line or how to even install programs outside the apt-get stuff.  So step-by-step instructions are appreciated.  Thanks!

(unrelated, I get no sound from youtube, but veoh and other sound works ok...is this a youtube thing, or a flash thing)

---

### Post by metol on 2008-04-27
Hi, I have a Toshiba A135-S4666 laptop as well and I had the same problem with the headphone jack not working in Hardy.  I did a little digging and it was a pretty easy fix:

First make a backup of your alsa-base file in case something goes wrong you can always revert back to the original.

```
sudo cp /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base.backup
```

Next edit your alsa-base file:

```
gksu gedit /etc/modprobe.d/alsa-base
```

then scroll to the bottom and add the following line..

```
options snd-hda-intel model=lenovo
```

Save the file and then **reboot**.  My headphones worked fine after adding that line.

Now for your flash problem, there is a bug in flash known to cause problems when other devices are using your sound card.  Installing the following utility fixed it for me:

```
sudo apt-get install libflashsupport
```

After installing, you will need to restart Firefox before trying the flash sound fix.

Regards,
Metol

---

### Post by goodywitch on 2008-04-27
I was wondering how to edit the file.  It worked perfectly.  Thanks!

---

### Post by DBrocks on 2008-04-27
Please mark this thread as solved!! Thanks!!

---

### Post by goodywitch on 2008-04-29
brain spaz...how?

---

### Post by sunpupa on 2008-05-11
> **metol said:**
> Hi, I have a Toshiba A135-S4666 laptop as well and I had the same problem with the headphone jack not working in Hardy.  I did a little digging and it was a pretty easy fix:

First make a backup of your alsa-base file in case something goes wrong you can always revert back to the original.

```
sudo cp /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base.backup
```

Next edit your alsa-base file:

```
gksu gedit /etc/modprobe.d/alsa-base
```

then scroll to the bottom and add the following line..

```
options snd-hda-intel model=lenovo
```

Save the file and then **reboot**.  My headphones worked fine after adding that line.

Now for your flash problem, there is a bug in flash known to cause problems when other devices are using your sound card.  Installing the following utility fixed it for me:

```
sudo apt-get install libflashsupport
```

After installing, you will need to restart Firefox before trying the flash sound fix.

Regards,
Metol
I tried your method,but it's doesn't work to my lenovo laptop.do you have any other advice?

---

### Post by metol on 2008-05-12
> **sunpupa said:**
> I tried your method,but it's doesn't work to my lenovo laptop.do you have any other advice?

Hello sunpupa,

The fix above will only work for specific sound cards.  If you are using a Lenovo laptop, then the "options snd-hda-intel model=??????" line will likely be different.  What model Lenovo are you using?  After a quick search, the Lenovo N200 suggests to use "options snd-hda-intel model=auto" in the /etc/modprobe.d/alsa-base file.

Metol

---

