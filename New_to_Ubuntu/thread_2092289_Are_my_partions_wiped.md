---
title: "Are my partions wiped?"
date: 2012-12-07
forum: New to Ubuntu
---

### Post by GeorgeKs on 2012-12-07
Hi, new to the forum.
I would like to have some information very important to me.
I used to have my hdd in 3 partitions. C:win7 - D:win8 (dual boot) - E:storing files.

I created a usb key with ubuntu 12.10 booted and choose to install. After the question that setup found win8 i choose not to keep previous os and install ubuntu from scratch assuming that ubuntu would install at (previous) C: or D:. Now after the installation i noticed that i got modified partitions. Have i lost everything from E:? Or can i browse somewhere to back my files up?

Thank you very much and sorry for the rush but i'm a bit worried about what happened and i can't find any info about this easily..

---

### Post by audiomick on 2012-12-07
First of all, do not use the computer until you have a chance to try and sort this out. The less the drive is written to, the better your chances of getting stuff back.

I just posted these links in another thread, actually. I think this is where you need to look for help with your problem.

Here are a couple of pages with some info.
[https://help.ubuntu.com/community/DataRecovery]("https://help.ubuntu.com/community/DataRecovery")
[http://askubuntu.com/questions/18619...ition-recovery]("http://askubuntu.com/questions/18619...ition-recovery")

---

### Post by GeorgeKs on 2012-12-07
I used it for a while. Unfortunatelly i don't know anything about linux. All i could do is to install and run testdisk. but the options are confusing... Can i run testdisk from the same pc? I mean not booting from cd?

---

### Post by Grenage on 2012-12-07
You don't want to boot or use the drive that contains the overwritten partitions.  So you'll either want to use a live CD (and have another drive to recover to), or boot from another PC with the drive slaved.

---

### Post by GeorgeKs on 2012-12-07
Shouldn't you warn about the hdd partition modification? I didn't know this would happen. I just lost my life in there. It was a new 1TB HDD. A windows user is used to a single partition installations of the os.

---

### Post by Grenage on 2012-12-07
It's been a long time since I've done a fresh Ubuntu install, but doesn't the option that uses the whole disc, basically say that it's going to erase any existing files?

---

### Post by audiomick on 2012-12-07
Yep.

---

### Post by Bartender on 2012-12-07
George, I feel your pain, but jeepers, you told the LiveCD to do exactly what it did.

[COLOR="Navy"]"setup found win8 i choose not to keep previous os and install ubuntu from scratch"[/COLOR]

If you'd gotten on the forum and described what you were planning to do, we could have pulled you back from the precipice.

---

### Post by critin on 2012-12-07
> **GeorgeKs said:**
> Hi, new to the forum.
I would like to have some information very important to me.
I used to have my hdd in 3 partitions. C:win7 - D:win8 (dual boot) - E:storing files.

I created a usb key with ubuntu 12.10 booted and choose to install. After the question that setup found win8 **i choose not to keep previous os and install ubuntu from scratch assuming that ubuntu would install at (previous) C: or D:**. Now after the installation i noticed that i got modified partitions. Have i lost everything from E:? Or can i browse somewhere to back my files up?

Thank you very much and sorry for the rush but i'm a bit worried about what happened and i can't find any info about this easily..

Do you mean that you **wanted **to wipe both windows systems even though you knew very little about using linux?  That's pretty brave of you.  I think most new linux users keep their windows 'just in case'.  

Your stored stuff can be recovered if you're very careful and haven't messed with the partitions too much.  Don't install anything else until that's done.  Use live cd/usb to recover.

---

### Post by snowpine on 2012-12-07
Once you've restored your Windows, here are easy instructions to test-drive Ubuntu with **no risk or permanent changes** to your system: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by audiomick on 2012-12-07
> **GeorgeKs said:**
>  Can i run testdisk from the same pc? I mean not booting from cd?

I believe it is easier in some respects to run it from a live CD or USB stick. There is info about testdisk in one of those links, if not both.

---

### Post by DuckHook on 2012-12-07
> **Grenage said:**
> It's been a long time since I've done a fresh Ubuntu install, but doesn't the option that uses the whole disc, basically say that it's going to erase any existing files?

> **Bartender said:**
> George, I feel your pain, but jeepers, you told the LiveCD to do exactly what it did.

"setup found win8 i choose not to keep previous os and install ubuntu from scratch"

If you'd gotten on the forum and described what you were planning to do, we could have pulled you back from the precipice.

> **critin said:**
> Do you mean that you wanted to wipe both windows systems even though you knew very little about using linux? That's pretty brave of you. I think most new linux users keep their windows 'just in case'.

Your stored stuff can be recovered if you're very careful and haven't messed with the partitions too much. Don't install anything else until that's done. Use live cd/usb to recover.

Guys. While all this is true, it doesn't *help* the poor man.

> **GeorgeKs said:**
> I just lost my life in there. It was a new 1TB HDD. A windows user is used to a single partition installations of the os.

George, here is my suggestion and I strongly urge you to follow it. With all the respect in the world, it is obvious that you are way out of your depth here and need someone geeky to work this out for you. Therefore:

1. Do not do anything further.
2. Take the hard disk out of your machine.
3. Take it to reputable computer recovery center (these are different than plain old computer shops).
4. Describe to them the precise steps you have taken so far and let them try to recover as much as they can.

Sometimes it's simply better to call in the pros than continue to stumble in the fog and make things worse. Good luck. Sorry your intro to Linux had to start this way.

---

### Post by Mark Phelps on 2012-12-07
IF you're interested in getting your Windows partitions back, you need to do the following:
1) Remove the affected drive from the current PC
2) Go to a Windows PC, download the ISO of Minitool Partition Wizard from their website and burn the CD.
3) Connect the affected drive to that Windows PC
4) Boot from the Minitool CD
5) Use the Partition Repair Wizard against your affected drive to see if it restores the partitions.

---

