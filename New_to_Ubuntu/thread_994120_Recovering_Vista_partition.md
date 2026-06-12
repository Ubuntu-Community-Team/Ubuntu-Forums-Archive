---
title: "Recovering Vista partition"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by WiseMaturin on 2008-11-26
The problem: I was dual-booting Kubuntu and Vista, and the Vista side stopped working. Most of my information was on the Vista side, and when I try to load it from the boot menu, it will go to the Windows loading screen and load continuously until I shut the computer down. I cannot even access the information from Kubuntu, and it cites that I do not have the correct permissions.

What I'd like: to be able to at least recover the information. Getting Vista working again is not necessary, but the information would be nice to have. It's pictures and other things from years ago that I'd like to *not* lose. That is ideal though, and I know all may be lost.


Is there anything I can do?
I assume that to begin I will need to know why it's not working, which I do not know.
Thanks in advance!

---

### Post by Titan8990 on 2008-11-26
In regards to the Kubuntu permission issue. Is your main filesystem drive formatted in NTFS?

---

### Post by caljohnsmith on 2008-11-26
How about opening a terminal ("Konsole" in Kubuntu) and post the output of:
```
sudo fdisk -lu
```
And for whichever is your Windows partition, most likely sda1 (but change it below if it isn't), do:
```
sudo mount /dev/sda1 /mnt
ls -l /mnt
dolphin /mnt &
```
And please post the output of the above commands. If all goes well, that last command should pull up a file browser and let you browse your Vista files. Let me know how it goes though.

---

### Post by Coreigh on 2008-11-26
Simplest way is to boot from an Ubuntu LiveCD and copy the data and information to the Kubuntu partition or external drive. I do not know if Kubuntu has the same NTFS support that Ubuntu does.

---

### Post by WiseMaturin on 2008-11-26
Results of 'sudo fdisk -lu'

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   307337216   312578047     2620416    c  W95 FAT32 (LBA)
/dev/sda2          161792    21133311    10485760    7  HPFS/NTFS
/dev/sda3   *    21133312   157852061    68359375    7  HPFS/NTFS
/dev/sda4       187542810   312576704    62516947+   5  Extended
/dev/sda5       195382530   312576704    58597087+  83  Linux
/dev/sda6       187558938   195366464     3903763+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

And when I tried to use the second set of code, I got THIS as a result...

```
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda3 /mnt -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda3 /mnt ntfs-3g force 0 0

```


That seems to be the problem. lol
But how do I fix that since I cannot log onto the Windows portion anyway?
Do I try to force it, or will that make things worse?

---

### Post by Titan8990 on 2008-11-26
If you can not log in to Windows to unlock the partition than the force option may be your best bet. I have had good luck with it but you should be aware of the potential for data loss.

---

### Post by jimv on 2008-11-26
Just force it.  It's not going to harm anything.  The NTFS journal is "unclean", but that's not going to harm any of your data.  Mount the partition with this command:

>  mount -t ntfs-3g /dev/sda3 /mnt -o force

Then copy anything you need out of there.

---

### Post by msageg8 on 2008-11-26
must sign in with yourlet's go to the forum Good Services[img]http://pic.piclib.net/sunvv/images/pic/new20_711.gif[/img]About all go to= Good Services ok!sites where they can express&#65281;[shanghai massage](http://www.massageinchina.com/)-shanghai massage this for service[massage in shenzhen](http://www.massageinshenzhen.org/)-All of the massage in shenzhen services[massage shenzhen](http://www.massageinshenzhen.org/)-this service for massage shenzhen[cheapest wow gold](http://www.wowpowerleveling-wow.com/)-wow gold on Sale with Fast site

---

### Post by WiseMaturin on 2008-11-27
I am holding my breath as I try this. And crossing my fingers, toes, and anything else I can conceivably cross.

Okay, it mounted and I seem to be able to access the information.
It also printed something about "Reset $LogFile".
I am wondering if that means that I can sign in like I normally would have now, since $LogFile ha been reset.

Curiously, and I don't know if this is normal or not, but my computer has slowed down tremendously. I was wondering if there was a way to monitor system performance on Kubuntu.
*Edit::: When I closed Dolphin, a notice of "A fatal error occurred". Is this common when force-mounting?*

Thank you very much though! I think my problem is more or less solved.
But I would appreciate it if someone was willing to answer a few of my questions. :)

---

### Post by WiseMaturin on 2008-11-29
So I looked through all the folders and it doesn't even show a Desktop folder.

Does this indicate data loss?

---

### Post by caljohnsmith on 2008-11-29
When you say you are missing the Desktop folder, did you look under the C:\Documents and Settings\<username>\Desktop directory? At least that's where it is in XP, and I think they still use that location in Vista. It sounds like you might be experiencing a hardware problem though, most likely with your HDD. Do you have any diagnostic CDs that came with the HDD? If so, I would run some diagnostic tests on your HDD to check its health. If you don't have a CD that came with your HDD, you can download and use the [Ultimate Boot CD]("http://www.ultimatebootcd.com"), and from the main menu choose Hard Disk Tests > Diagnostic Tools.

---

### Post by caljohnsmith on 2008-11-29
Duplicate post--deleted.

---

### Post by PocketDog on 2008-11-29
Helpfully, Microsoft left 'Documents and Settings' in Vista, but it's empty. Your documents will be in /Users/<user>/

---

### Post by WiseMaturin on 2008-11-30
Curious things have happened. Very curious indeed.
My computer says the partition I am accessing now is 2.5 GB, which is not the size I originally partitioned it for.
However, when I right-click and view the Properties, it tells me the size of the partition is 500.25 GB.
Which is also wrong. The size of my HDD is not even half that. Most of the 500GB is in a folder called "windows".

Documents and Settings has Administrator, Default User, and All Users. There is no folder in the main directory called Users, and I searched the partition and could find no occurrence of a Desktop folder anywhere at all.
Perhaps this is not the correct partition?
Should I unmount this partition?

---

### Post by jimv on 2008-11-30
I suppose you could try mounting SDA1 and SDA2 as well to see what's in those.

---

### Post by WiseMaturin on 2008-11-30
Mounted both sda1 and sda2, and one of them is a Recovery partition for Dell, and has all the folders I would expect to see in the partition I was hoping to recover from, but no files at all.

But when I mounted sda3 again, and tried to access it going through /media/sda3 instead of the MEDIADIRECT folder that popped up in Dolphin when I mounted, it's properties read the right size for the partition only it didn't have any files or folders at all. The properties said that the partition had files AND folders, but I cannot see them at all.

I am very confused now. :confused:

---

### Post by jimv on 2008-12-01
I don't know much about KDE...perhaps try an Ubuntu LiveCD (should automagically mount all your drives) and see what shows up?

---

### Post by WiseMaturin on 2008-12-11
I got fed up and decided that I would reinstall Vista and wipe out the previous data. But the reinstall CD doesn't work! It doesn't load Vista, or start any reinstall feature. What is up?
Maybe Grub is throwing it off?


Well, I'm going to try the LiveCD thing and see if that works.

---

### Post by carml on 2008-12-11
Hi I have got Vista too,I can say you that the folder isn't where you are looking for,but under (tipically) C:\Users\your name\Desktop.

---

### Post by WiseMaturin on 2008-12-13
What usually happens is that I see the folders 'Default User' and 'All Users'. And in neither of those folders are any files at all. Especially not the ones I'm interested in.

But I am going to try and use my Kubuntu Live CD, so wish me luck!

---

