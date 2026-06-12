---
title: "[SOLVED] [SOLVED] Ubuntu too old to update ?"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by UBUNTESB on 2008-11-18
HELP PLEASE.

I am a windows XP user already running a dual boot ( windows sp2 / windows sp3 )  system.

I decided to install Linux on a spare slave hard disk which was empty.

I had purchased "beginning Ubuntu Linux" a couple of years ago and figured I would start by installing Ubuntu from the cd contained in the book. AHH !!! it was version 5.1 Breezy Badger. I now have it set up with GRUB offering me the  expected choice of linux and the two other windows systems and it works fine. But how do I update.???? it is obviously no longer supported

Could I reformat my slave disk ? obviously losing the option to boot linux from it in the GRUB, and then install 8.04 from a new installation CD ? I am afraid of ending up with two grub programs if I do this. Or could i choose not to install grub again when running the new install? or am I barking up the wrong tree.

In fact I intend using ubuntu for the internet until i get used to it so would installing the latest firefox 3 update onto Breezy improve my security in the same way as the new install???

Many thanks for your help.

---

### Post by jenkinbr on 2008-11-18
That version is long since reached end-of-life.  Try downloading 8.04 LTS hardy or 8.10 intrepid from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) .

---

### Post by CatKiller on 2008-11-18
You *could* take a 5.10 -> 6.06 LTS -> 8.04 LTS (-> 8.10) upgrade path if you really wanted to, but that would be a *lot* of downloading.

If you haven't done much with your install, I'd strongly recommend downloading a newer version and installing that instead. You can install it in exactly the same way that you did with Breezy. Your GRUB configuration should be automatically sorted out in the same way that it was with Breezy.

---

### Post by jpoRS on 2008-11-18
> **UBUNTESB said:**
> In fact I intend using ubuntu for the internet until i get used to it so would installing the latest firefox 3 update onto Breezy improve my security in the same way as the new install???

No, that would not improve your system security up to current release levels.  Your best bet, as has been said, would be to download one of the new releases.  8.04 LTS (Long Term Support) will be supported until 2010, but lacks some of the features of 8.10.

Welcome to the community, don't let this snafu discourage you, Ubuntu isn't nearly as daunting as it seems at first.

Good luck!
jim

---

### Post by louieb on 2008-11-18
> **UBUNTESB said:**
> ...! it was version 5.1 Breezy Badger. I now have it set up with GRUB offering me the  expected choice of linux and the two other windows systems and it works fine. ..But how do I update.???? 

I started out with v5.10 Breezy also.  v8.04  (Hardy)  Ubuntu is so much better.  More features, easier to use. 

What I would do is install fresh. When you get the partitioning stage of the install choose the manual option. Click on the partition that holds  Breezy choose edit,  mount it as / (root), and check the format box.  Your new Ubuntu install will then replace the Breezy install.

BTW:  How much ram do you have? Breezy would run on P1 with 128MB ram. And ran quite well with 256MB ram. Hardy and Intrepid (v8.04 and v8.10)  need more ram to run well.  The minimum is 384MB but to get decent performance you need at least 512MB ram.

---

### Post by gjoellee on 2008-11-18
wooooow that version came out several years ago!

---

### Post by UBUNTESB on 2008-11-19
Thank you all for that advice.

Yes I know it is old but the main reason that it is on there is that I burned myself a cd using the latest release but I was not happy with it. It didnt install correctly so i decided to use a CD which I knew would work. 

As you have gathered then I have tried Ubuntu before and I gave up a little too early in the learning curve. BUT NOT THIS TIME.

So I will PURCHASE a CD and install it.

I will follow the comments given by louieb. just two questions, will the "mount as /"  be an obvious choice on the partitioning screen. and will I not be asked to re-install grub?

I have plenty of ram ( 2 gig ) so i will have no problems there.

I will purchase a CD now and return to this thread at that time.

I dont want to give up again so am going to stick with you experts knowing that I will end up with a better computing experiance.

See you all later

---

### Post by hyper_ch on 2008-11-19
you don't have to purchase an ubuntu cd :) you can (a) download it or (b) order a free one (but it will take several weeks to arrive).

---

### Post by Elfy on 2008-11-19
You don't need to but it, you can get it free from shipit - but it can take a while to arrive - [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

If you have a downloaded and burnt cd already - what errors do you get when you try to run it?

Did you check the downloads md5sum? - information here - [https://help.ubuntu.com/community/BurningIsoHowto#MD5](https://help.ubuntu.com/community/BurningIsoHowto#MD5) Sums

When you booted it did you try the check cd integrity option?

What hardware do you have - particularly gpu?

---

### Post by UBUNTESB on 2008-11-20
I have done it !!!!!

I had been trying to cut corners and hadnt checked the validity of the original CD that I burnt.

It was full of errors. So I followed all of your recommendations and downloaded another iso and burned a new cd carrying out all of the checks as i went.

I followed the procedure given by louieb and it worked a treat so I now have Hardy Heron up and running.

Thank you all---- I will start to use it now.

---

### Post by louieb on 2008-11-20
> **UBUNTESB said:**
> I have done it !!!!!--I now have Hardy Heron up and running.Thank you all---- I will start to use it now.

:)Thats great.   Please click on thread tools and mark this thread as solved.
Welcome to Ubuntu.

---

