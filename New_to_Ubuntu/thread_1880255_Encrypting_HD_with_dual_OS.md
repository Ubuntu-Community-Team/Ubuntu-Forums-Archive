---
title: "Encrypting HD with dual OS"
date: 2011-11-13
forum: New to Ubuntu
---

### Post by bedpotato on 2011-11-13
Hello,

Having installed Ubuntu I am happy with it and would like to delete Windows but apparently that's quite hard to do unless you're an expert or are prepared to reinstall. I don't want to reinstall because I've had a lot of hassle just getting this far and don't want to go through all the hassle again. I've got plenty of space still left to spare on my hard drive, but I am worried that having Windows still there might potentially interfere with Ubuntu.

One of the things I want to do next is encrypt my hard drive. I had been considering doing this for a while (even when I had Windows) and would use TrueCrypt to do it. But I found a similar thread about it here:

[http://ubuntuforums.org/showthread.php?t=1614437](http://ubuntuforums.org/showthread.php?t=1614437)

where people have said that it's not possible to actually encrypt a whole hard drive anyway, and that encrypting "home" should be sufficient. I already chose the option to encrypt "home" when installing, so if that's done already, should that make me secure enough, or do I need to have the whole Ubuntu partition encrypted?

Thank you!

---

### Post by Mark Phelps on 2011-11-13
Sorry, but I simply fail to understand the paranoia that folks presume when they feel they have to encrypt either their /home folder, or in your case, the whole drive.

If this is a laptop, once someone obtains the PC, they will simply remove the hard drive, subject it to hardware decription (which is orders of magnitude faster than software decription), and within a few hours, or days, have access to the drive.  That is, if they are professionals.

If they are not, they will simply wipe the drive, reformat it, and use it for whatever they want.  That's if they're not willing to spend $40 and buy a new drive -- costing a LOT less than any laptop.

If it's a desktop in your home, any professionals can gain access to your house inside of 5 minutes, and access to your PC in the same amount of time.  They will simply hook up hardware to your PC, boot using that, image off your drive -- and then, once back at the shop, will once again, be able to use hardware to crack the encryption on the drive.

One more thing, if you encrypt the whole drive, any anything goes wrong, you will have lost the entire contents of the drive.  And, don't say this can't happen.  My company furnishes us hardware-encrypted laptops, and mine is on its THIRD drive -- the previous two got locked up somehow and it wasn't worth their time trying to decrypt it.  You won't have the facilities they do, so if yours goes bad -- you've lost everything.

---

### Post by bedpotato on 2011-11-13
Oh. I see. Thank you.

I didn't know all of that, and I am just very paranoid about my security. Also I had read somewhere that Windows might write things onto the Ubuntu partition and mess things up if Ubuntu is not encrypted, which is one of my motives for wanting to encypt. See original post.

When you say encryption can be cracked with hardware in a matter of minutes, are you referring to Ubuntu's encryption, or Truecrypt's? Based on reports on the net, Truecrypt is reportedly impossible to crack. Example:

[http://forums.pureoverclock.com/showthread.php?9298-Not-even-the-FBI-can-crack-truecrypt](http://forums.pureoverclock.com/showthread.php?9298-Not-even-the-FBI-can-crack-truecrypt)

I think your argument is sort of like saying: "what's the point of locking your front door when thieves who really wanted to get in could break it down with a crowbar?" I feel safer locking all my doors even though I know doing so would not dissuade a truly determined intruder. Locking them is better than leaving them wide open.

Back to my question: will encrypting just the "home" part be enough? I am not really doing it for the security aspect, as I store my stuff on external drives. It's more for the concern I have about Windows writing on the Ubuntu partition, but perhaps that's unfounded. I do not know because I am a non-geek when it comes to computers but I read somewhere else that if updates are made to Windows on a dual system, Windows might write changes on top of the Linux partition unless it's encrypted. 

If someone could just answer me rather than ranting about their personal views on encryption, I would be grateful for some advice. Thank you. :)

---

### Post by alphacrucis2 on 2011-11-13
> **bedpotato said:**
> Hello,

Having installed Ubuntu I am happy with it and would like to delete Windows but apparently that's quite hard to do unless you're an expert or are prepared to reinstall. I don't want to reinstall because I've had a lot of hassle just getting this far and don't want to go through all the hassle again. I've got plenty of space still left to spare on my hard drive, but I am worried that having Windows still there might potentially interfere with Ubuntu.

One of the things I want to do next is encrypt my hard drive. I had been considering doing this for a while (even when I had Windows) and would use TrueCrypt to do it. But I found a similar thread about it here:

[http://ubuntuforums.org/showthread.php?t=1614437](http://ubuntuforums.org/showthread.php?t=1614437)

where people have said that it's not possible to actually encrypt a whole hard drive anyway, and that encrypting "home" should be sufficient. I already chose the option to encrypt "home" when installing, so if that's done already, should that make me secure enough, or do I need to have the whole Ubuntu partition encrypted?

Thank you!


With Windows it is possible for truecrypt to encrypt the entire OS. This is achieved by pre boot authentication using truecrypt's boot loader. As far as I know they (truecrypt) don't support this type of encryption with Linux at this time but you can use truecrypt for encrypting other partitions (will work if you have /home as a separate partition). The truecrypt virtual partition scheme also works under linux.

---

### Post by dave0109 on 2011-11-14
I've never heard of Windows writing onto the other patitions... but as you don't want Windows any more, you can get rid of it.  Problem solved.  FWIW, I've been dual-booting Windows and Ubuntu for nearly 4 years without problems.

Perhaps you're refering to issues of the boot sector getting re-written. This has been known to happen, sometimes, depending on varying circumstances.  Not to me though, and if it did, it's straight forward to boot to the LiveCD and get GRUB installed again.

As for encryption, well, my paranoia is quite healthy.  I use Truecrypt, not for my home folder, but for a part of it.  Whether it can be cracked by the CSI team during the ad-break or not, who knows?

---

### Post by carranty on 2011-11-14
> **bedpotato said:**
> I had read somewhere that Windows might write things onto the Ubuntu partition and mess things up if Ubuntu is not encrypted


That definitely won't happen, I've been running one form of linux or another for 3 years now and have never known that to happen.  As dave said, updating windows can affect the boot menu, perhaps preventing you from booting into Ubuntu, but if this happens its very easy to fix (literally just one command run from the live CD), and encryping you're /home folder probably wouldn't even prevent it. 

If however you want to free up space, deleting your windows partition is quite straightforward, only takes 5-10 minutes, and certainly doesn't require a reinstallation of Ubuntu.  I wouldn't recommend it yet though, keeping Windows handy when you're just starting out is useful, especially if you run into a problem with Ubuntu that affects your network - then the only way to ask for help from this forum will be to use windows!

---

### Post by carranty on 2011-11-14
Also, regarding the pros cons of encryption, I feel that -- like anything -- its a good thing in moderation.  Having no encryption at all does leave your private files vulnerable if your computer gets taken.  However on the other extreme Mark has a good point in that if you encrypt your entire drive and it fails, the chances of you recovering your files are pretty much zero (and these are I assume important files or they wouldn't be encrypted).

In regard to how 'crackable' truecrypt is, its really down to your password, every security measure has a weakness.  The maximum length I think is 132 characters (I might be wrong on that), if you use one that long, and its a random mix of letters/numbers/symbols then yes it's pretty much uncrackable, but to use such a password you'll need a key file, which won't be encrypted and if found by a third party they'll easily decrypt your file. Also if you use a memorable password (Less than say 10 characters) its most certainly crackable.

---

### Post by bedpotato on 2011-11-14
Thank you for all the replies! I agree it's not a good idea for me to delete Windows yet (assuming I would even know how to delete it, which I don't) because there are things I might need. Apart from anything else I have not yet tested my printer to see if it will work on Ubuntu. Based on things I've read on the forums, I have a feeling it won't (or will require lots of tweaking, which I don't know how to do).

So am I OK to just leave Windows there and leave things uncrypted? That seems to be the general consensus. 

Thanks everyone. :)

---

### Post by carranty on 2011-11-14
> **bedpotato said:**
> 
So am I OK to just leave Windows there and leave things uncrypted? That seems to be the general consensus. 

In short, yes.

Also, as far as printers are concerned, HP printers almost always work flawlessly on Linux, but other brands can be difficult/impossible.

---

### Post by fleamour on 2011-11-14
> **Mark Phelps said:**
> Sorry, but I simply fail to understand the paranoia that folks presume when they feel they have to encrypt either their /home folder, or in your case, the whole drive.

If this is a laptop, once someone obtains the PC, they will simply remove the hard drive, subject it to hardware decription (which is orders of magnitude faster than software decription), and within a few hours, or days, have access to the drive.  That is, if they are professionals.

If they are not, they will simply wipe the drive, reformat it, and use it for whatever they want.  That's if they're not willing to spend $40 and buy a new drive -- costing a LOT less than any laptop.

If it's a desktop in your home, any professionals can gain access to your house inside of 5 minutes, and access to your PC in the same amount of time.  They will simply hook up hardware to your PC, boot using that, image off your drive -- and then, once back at the shop, will once again, be able to use hardware to crack the encryption on the drive.

One more thing, if you encrypt the whole drive, any anything goes wrong, you will have lost the entire contents of the drive.  And, don't say this can't happen.  My company furnishes us hardware-encrypted laptops, and mine is on its THIRD drive -- the previous two got locked up somehow and it wasn't worth their time trying to decrypt it.  You won't have the facilities they do, so if yours goes bad -- you've lost everything.

Haha! 

I enjoyed this trollish rant!

;)

---

### Post by bedpotato on 2011-11-14
> **fleamour said:**
> Haha! 

I enjoyed this trollish rant!

;)

I think trollish is the wrong word to use. Trolling is not the same thing as hijacking! ;)

Maybe the hijacker should start their own thread to rant about encryption if they are so strongly opposed to it!

---

### Post by dave0109 on 2011-11-14
I think you had it nailed with your locking the door analogy.  Except that truecrypt is a 9-lever mortice lock with a robocop standing sentry. :-)

---

