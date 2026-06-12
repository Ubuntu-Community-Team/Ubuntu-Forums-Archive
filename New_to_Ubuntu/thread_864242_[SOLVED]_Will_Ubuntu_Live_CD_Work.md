---
title: "[SOLVED] Will Ubuntu Live CD Work?"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by Confused Computer User on 2008-07-19
I have an Emachines H5088 desktop with Vista home basic. The specs are Pentium IV 3.2GHz, 2GB RAM made up of two DDR2 memory sticks(a bit less when running because of the Video card that shares some of the ram).
My question is will Ubuntu be able to boot from the CD (no install safely and be able to mount the Vista partition (copy or write on it) with out failing to shut down. Reason why I ask this is that on an older Pentium II 400MHz with 256MB RAM Ubuntu doesn't shut down fully. Regardless can any one confirm that it will run OK. (if any one has the same machine it would be most appreciated)
Thanks in advance.

---

### Post by appi2012 on 2008-07-19
Ubuntu should definitely be able to run smoothly on that system. I think 256 MB ram is the minimum for the live cd.

---

### Post by JagDragon on 2008-07-19
It will work fine. I can run a live CD on a 300Mhz laptop with 64MB RAM, and I'm running Ubuntu (Not live) on there right now. You'll run it just fine.

---

### Post by phoenix_abhi on 2008-07-19
UR system will run with all the Ubuntu and compiz features enabled with this specification. Only drawback is Ur Video card has no RAM

---

### Post by Canis familiaris on 2008-07-19
Ubuntu will cruise

---

### Post by Confused Computer User on 2008-07-19
But will it be able to mount the Vista partition as well as be able to write on it? oh... and Thnak you for the quik replies

---

### Post by dexter.deepak on 2008-07-19
you will have to mount your vista partition for writing...remember to have a clean shutdown of windows, or you will have to do a forced mount.
reply if you dont know how to mount.

---

### Post by coffeecat on 2008-07-19
> **Confused Computer User said:**
> My question is will Ubuntu be able to boot from the CD (no install safely and be able to mount the Vista partition (copy or write on it) with out failing to shut down.

The best answer is to try it and see. I can understand your concern about it failing to shut down, but so long as you haven't mounted any filesystems on the internal hard-drive, no harm would be done if you had to press the power button or even cut the power supply to get it to go down. If you had mounted a filesystem on a drive and had to do a hard reset, there would be the danger that the drive would be unmounted uncleanly, possible leading to data corruption.

You could try booting up and if all is well, shut down without doing anything else. If it closes down OK then you could try rebooting in order to mount your Vista partition. As far as mounting Vista is concerned, go to Places > Computer and double-click on the icon representing the Vista partition. That simple procedure ought to work as Hardy mounts NTFS partitions read-write out of the box. If it doesn't, post back and someone can take you through mounting from the terminal.

---

### Post by Confused Computer User on 2008-07-19
Thank you Coffecat for the post. You eased my conscience a bit. Reason why I keep avowing the "try and see" method is because of the fear of corruption of the system. Vista is rather high maintenance in terms that you can't really do too much before it fails. Mind you I'm pleased with the way it's worked so far, but (and there&#8217;s a big but) I will inevitably be force to install Service pack 1 (which I've heard it can bring some slight improvements or just ruin the system). Since I need this computer for school I need to make sure that in the likely event that vista fails, I can still get my files from the disc and put them on my older computer which despite all I've thrown at it, (it's a win 95) it is still able to go on the net open PDFs and Word files and play the occasional old school game.
In short I hope that Ubuntu is able to save me in case of any problems. I also hoped to install Ubuntu on my older system but I just realized that for that one Ubuntu does not recognize the sound card. Oh well, another time, another thread.
Thank you again.

---

### Post by Confused Computer User on 2008-07-19
OK... So I risked it and tried it. It went surprisingly well. I'm buzzing with questions concerning some things but that's for another thread. 
Phoenix_abhi you say:

MARK YOUR THREAD SOLVED

how do I do that?

---

### Post by kamitsukai on 2008-07-19
> **Confused Computer User said:**
> 
Phoenix_abhi you say:

MARK YOUR THREAD SOLVED

how do I do that?

Top of the page, Thread Tools --> Mark this thread solved

---

### Post by Confused Computer User on 2008-07-20
Thank you kamitsukai for telling me how to mark the thread as solved. And thankyou to everyone else who contributed. The conclusion: In the end I decided to try the Live CD and it ran absolutely beautifuly. One problem was that my Video card which has 30MB private memory and then takes the rest from the ram didn't share RAM memory any more. Regardless, this is insignificant since even with 30MB the visual effcts made my jaw drop. The system ran better than expected. Second problem was that my Pentium 4 HT (hyper threading) processor was being seriously used which rearly happens with Vista but I suppose that this is an effect of the Live CD. So Ubuntu Live CD works well on Emachines H5088.

---

