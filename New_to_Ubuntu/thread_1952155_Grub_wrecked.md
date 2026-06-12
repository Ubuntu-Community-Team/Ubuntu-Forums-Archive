---
title: "Grub wrecked?"
date: 2012-04-03
forum: New to Ubuntu
---

### Post by carloslosgrande on 2012-04-03
Just tried installing 12.04 beta.

I have 11.10 installed on one disc, various partitions and had Mint12 on another, various partitions.

I tried to overwrite/install 12.04 over Mint, leaving me with 11.10 as backup in case anything went wrong.

Something did go wrong - an unrecoverable error.

So I shut down the install and then tried to restart with 11.10 but at initial screen I get;
[B]error file not found
grub res>[/B]

I assume that this means grub has been wrecked?

If so, how do I fix this?

Thanks.

---

### Post by ratcheer on 2012-04-03
If you can't boot to anything installed on the disk, you can boot to a LiveCD, chroot to one of the systems on the disk, and use it to run grub-install. It is not an especially simple process, but it is documented on the Ubuntu Wiki. Or, at least, it used to be.

If you can't find anything, I will try to write up some instructions. Also, I will go try to find a link for you.

Tim

---

### Post by wojox on 2012-04-03
I find reinstalling grub2 from a [LiveCD]("https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files") works well.

---

### Post by ratcheer on 2012-04-03
Here is a link to the documentation, but it covers so many varying situations, it may be confusing:

[https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot)

Tim

---

### Post by carloslosgrande on 2012-04-03
I'm currently running on the liveCD.
I have no idea how to run grubinstall
I had a look on my other root system in boot/grub but I can't see install.
It's under some other folder?

---

### Post by carloslosgrande on 2012-04-03
I'll read through and try that,
thanks.

---

### Post by carloslosgrande on 2012-04-03
I'm now back into my system - 11.10

I tried the chroot method, 3 times, no luck.

Read up the page to 'boot repair' ditto with that.

Read down to purge & reinstall method - success!

Thanks for the link Ratcheer.

---

### Post by ratcheer on 2012-04-04
You are welcome. But I've never had the chroot method fail for me, at least after I finally figured out what it all meant. Anyway, I'm glad you're back in business.

Tim

---

