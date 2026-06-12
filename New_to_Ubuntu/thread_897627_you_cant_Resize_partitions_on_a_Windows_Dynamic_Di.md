---
title: "you cant Resize partitions on a Windows Dynamic Disk"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by popper on 2008-08-22
a continuation or more to the point an answer to how you CAN fix this windows crumby Dynamic partition as per the old archived thread

it doesnt allow you to resize unfortunately, but you can set the drive back to a real partition table that other tools can then use.

[http://ubuntuforums.org/showthread.php?t=367307](http://ubuntuforums.org/showthread.php?t=367307)

alas you cant conserve your data there , you have to use XPsp2 to delete the dynamic Drive as per [http://support.microsoft.com/kb/309044](http://support.microsoft.com/kb/309044)

However they are not clear, you do not right click the white drive section, you actually click the text to the left of it, that is were the  right click "Convert to Basic Disk" option is, once done you can again use partition magic in windows or Gparted in *nix etc as per usual.

it the fault of wondows XP(sp2) as i just tryed it,it asks you to make a basic disk and instead makes a Dynamic disk (on large 250gig+ drives at least), i just tryed it on a brand new drive and could not find a way to reverse it and make it useable again, so went looking for an answer, on finding the old archived thread above and NO answer,i am making this new thread to help others that search later for an answer to make your drive useable again.

step by step:
in windosxpSP2.
left click start,
right cick "my computer"/manage,
left click Disk Management,
right click your Dynamic drive in the white bar area on the left of the text,and delete the partion, and any other partitions you might have made that are on that same drive until it says its blank,

it doesnt save a valid generic partition MBR block that linux tools such as Gparted can work with until you also right click the text on the left of the bar and right click select "Convert to Basic Disk." and save...

friggin windows and its drive overlays are to blame, i wanted a generic primary partition from the word go ,and indeed selected "basic drive" that is supposed to make valid generic primary partitions etc, but MS went and make a "Dynamid Drive" anyway, messing up all my tools and in effect locking the drive until i did the above, im happy now as i can use it, if you want to keep your data on a Dynamic drive and convert to a real partition though it might be a challenge and not possiblea sfar as i can see, unless you have done it for real and know the answer OC, add it here if so, so others can learn and save masses of time and effort.

at least anyone that searchs for this problem can start using their dives again and put something good like Unbuntu on it :guitar:

hope this helps someone in the future and i do wonder what happened did KiwiPete
[http://ubuntuforums.org/member.php?u=236059](http://ubuntuforums.org/member.php?u=236059) managed to distroy the MS DD MBR and get on , although 2 months without the reply seems rather a long time to not get a working drive answer here.

i do wonder if linux DD might have been used to make this MS Dynamic disk MBR all go away, but if you have this problem you have MS running anyway as that caused the problem in the first place it seems fittig to use it to sort it then overwrite it with Unbuntu

---

### Post by mungatsuma on 2012-10-23
Had the same problem. A friend of mine bought a laptop and decided he wanted it partitioned. Used windows tools and dynamic partitions resulted. I used GNOME Disk Utility from a live USB Iso. I use Knoppix, but live ubuntu ISO will also do fine. This will allow you to delete the whole drive, after backing up ofcourse, (that is where the live usb comes in) to an external drive. Then repartition correctly, either with  disk utility or Gparted, since it will now be able to carry on from here.

NB Remember to select either GUID or MBR in disk utility when deleting in disk utility.

After that create your NTFS partition, I always add a FAT 32 one, then an extended partition for housing the linuxes.

Reinstall Windows, in my friends case it was Windows 7, then install Ubuntu and enjoy the best of both worlds. Not that there is much to enjoy in MS without coughing dough.

---

### Post by overdrank on 2012-10-23
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

