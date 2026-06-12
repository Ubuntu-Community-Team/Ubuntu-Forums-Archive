---
title: "grub... again..."
date: 2008-09-17
forum: New to Ubuntu
---

### Post by giamba64 on 2008-09-17
I have a bit messed up with Vista and Ubuntu, and now when I try to  boot Vista, I get the horrorous grub message: "Error 13: invalid or unsupported executable format".
I checked the disks with fdisk -lu:

"Disco /dev/sda: 160.0 GB, 160041885696 byte
255 heads, 63 sectors/track, 19457 cylinders, totale 312581808 settori
Units = settori of 1 * 512 = 512 bytes
Disk identifier: 0x46537d41

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   300495824   150247881   83  Linux
/dev/sda2       300495825   312576704     6040440    5  Esteso
/dev/sda5       300495888   312576704     6040408+  82  Linux swap / Solaris

Disco /dev/sdb: 160.0 GB, 160041885696 byte
255 heads, 63 sectors/track, 19457 cylinders, totale 312581808 settori
Units = settori of 1 * 512 = 512 bytes
Disk identifier: 0xa02134ca

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   312578047   156288000    7  HPFS/NTFS"

and it looks like Vista is on (hd1,0), right? and Ubunto on (hd0,0), right?

but doing gedit /boot/grub/menu.lst:

"title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=447d158e-5c53-45a7-94e3-d380b71b1d8f ro quiet splash vga=769
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=447d158e-5c53-45a7-94e3-d380b71b1d8f ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
# title		Other operating systems:
# root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
# map		(hd0) (hd1)
# map		(hd1) (hd0)
chainloader	+1"

Well, grub boots from Ubuntu BUT gives Error 13  for Vista.

Any help? (sorry to bother you all with such a usual question, but I am really a beginner....

Thanx

---

### Post by Orange_and_Green on 2008-09-17
Ciao Giamba:)
> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
# map		(hd0) (hd1)
# map		(hd1) (hd0)
chainloader	+1"
Thanx

If I were you, I would edit /boot/grub/menu.lst, and uncomment the two "map" instructions, like this:

```
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

Good luck!:KS


[EDIT]This would have made sense if Vista had been rooted from (hd1,0). Since Vista is in (hd0), I am not surprised that didn't work. Sorry, my bad :(

---

### Post by karlr42 on 2008-09-17
Looking at your output I take it you have two 160gb physical harddrives?

Also, try uncommenting this *one* line(#root):
```
# title Other operating systems:
**# root**


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1

```
I only say that because it's not commented in my file, and I'm dual-booting too

---

### Post by giamba64 on 2008-09-17
> **Orange_and_Green said:**
> Ciao Giamba:)


If I were you, I would edit /boot/grub/menu.lst, and uncomment the two "map" instructions, like this:

```
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

Good luck!:KS
Oh ya, I had forgot the "#"s since my last try (ooops...)
Now, however, I uncommented the map lines, but ...
Erro3 13 etc...

---

### Post by Orange_and_Green on 2008-09-17
OK next ;)

Does anything change if you try "rootnoverify (hd0,0)" instead of "root (hd0,0)"?

Also, there's something I don't quite get about this configuration... Ubuntu is on /dev/sda yet boots from (hd1,0), and Vista is on /dev/sdb and boots (well, tries to ;)) from (hd0,0)... could you post the contents of /boot/grub/device.map please?

P.S. I apologise for my last post, the two map instructions usually serve the purpose of "tricking" a Windows OS into believing it resides on the system's first boot disk, so it would have made sense if Vista had been installed on hd1. If Vista already is on the boot drive, then map is pointless indeed...

---

### Post by giamba64 on 2008-09-17
> **karlr42 said:**
> Looking at your output I take it you have two 160gb physical harddrives?

Also, try uncommenting this *one* line(#root):
```
# title Other operating systems:
**# root**


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1

```
I only say that because it's not commented in my file, and I'm dual-booting too
yes, unfortunately I had ywo exactly identical 160 GB drives, (incredible, I picked them up from two different "garbage" lots in the office, and they came up two identical 160 GB Maxtor) which makes me confusing in identify which disk has Vista and which one has Ubuntu.
Again, the "# root" comes from my previous tries, but it doesen't work even without comment...

---

### Post by giamba64 on 2008-09-17
> **Orange_and_Green said:**
> OK next ;)

Does anything change if you try "rootnoverify (hd0,0)" instead of "root (hd0,0)"?

Also, there's something I don't quite get about this configuration... Ubuntu is on /dev/sda yet boots from (hd1,0), and Vista is on /dev/sdb and boots (well, tries to ;)) from (hd0,0)... could you post the contents of /boot/grub/device.map please?
I did.... no success...
Actually I found out something which I hadn't noticed and could be  -I believe - critical...
When I tell grub to boot from Vista, a superquick view (before going back to the grub's screen) says:
"Loading GRUB stage2..." or similar, then, choosing again Vista from the grub's screen the same quick view says:
"Loading GRUB"
and then, choosing Vista form the third time Error 13 comes out.
It looks like Error 13 is caused by the (map0) (map1) etc. instructions which mess with the drive.
In short, could it be that grub can't simply access my Vista drive?
What do you think?

---

### Post by giamba64 on 2008-09-17
> **Orange_and_Green said:**
> OK next ;)

Does anything change if you try "rootnoverify (hd0,0)" instead of "root (hd0,0)"?

Also, there's something I don't quite get about this configuration... Ubuntu is on /dev/sda yet boots from (hd1,0), and Vista is on /dev/sdb and boots (well, tries to ;)) from (hd0,0)... could you post the contents of /boot/grub/device.map please?

P.S. I apologise for my last post, the two map instructions usually serve the purpose of "tricking" a Windows OS into believing it resides on the system's first boot disk, so it would have made sense if Vista had been installed on hd1. If Vista already is on the boot drive, then map is pointless indeed...
oops, I was forgetting device.map:

(hd0)	/dev/sda
(hd1)	/dev/sdb

---

### Post by Orange_and_Green on 2008-09-17
> **giamba64 said:**
> 
In short, could it be that grub can't simply access my Vista drive?
What do you think?

Strange indeed isn't it... 

If GRUB could not access the drive at all, I suspect you would get an error more the likes of "device not present"...

If you want to observe at what moment GRUB gives what error, you can always hit 'c' on the GRUB screen instead of 'ENTER' (this will take you to the GRUB shell), and type the commands one at a time.

[EDIT]
> **giamba64 said:**
> (hd0) /dev/sda
(hd1) /dev/sdb

That's weird... yet, when you are in Ubuntu, Vista resides on /dev/sdb1? (try mounting /dev/sdb1 somewhere and see if it contains Vista files)
How about trying root(hd1,0) with the two "map" commands then?

---

### Post by Orange_and_Green on 2008-09-17
Also, just out of curiosity, what happens if you go to BIOS and switch the boot order of the two hard drives?

---

### Post by karlr42 on 2008-09-17
> (try mounting /dev/sdb1 somewhere and see if it contains Vista files
Good idea, the command for that is something like:
```

mkdir Vista
sudo mount -t ntfs-3g /dev/sdb1 /home/<username>/Vista

```
Then look at the Vista folder

---

### Post by giamba64 on 2008-09-17
> **Orange_and_Green said:**
> Strange indeed isn't it... 

If GRUB could not access the drive at all, I suspect you would get an error more the likes of "device not present"...

If you want to observe at what moment GRUB gives what error, you can always hit 'c' on the GRUB screen instead of 'ENTER' (this will take you to the GRUB shell), and type the commands one at a time.

[EDIT]


That's weird... yet, when you are in Ubuntu, Vista resides on /dev/sdb1? (try mounting /dev/sdb1 somewhere and see if it contains Vista files)
How about trying root(hd1,0) with the two "map" commands then?
since Ubuntu thinks that /dev/sda1 is HPFS/NTFS and /dev/sdb1 is Linux, when I try to mount /dev/sdb1 it says:
"/dev/sdb1 already mounted"
and if I try to mount /dev/sda1 it says:
"impossible to find /dev/sda1 in /etc/fstab or /etc/mtab"
Let me try to invert the boot order from the BIOS... I'll be back in a few moments

---

### Post by Orange_and_Green on 2008-09-17
> **giamba64 said:**
> 
"impossible to find /dev/sda1 in /etc/fstab or /etc/mtab"

You did "sudo mount" didnt' you? ;)

---

### Post by Orange_and_Green on 2008-09-17
> **giamba64 said:**
> since Ubuntu thinks that /dev/sda1 is HPFS/NTFS and /dev/sdb1 is Linux,

Sorry, I am really a little confused now... You posted

> **giamba64 said:**
> Dispositivo Boot Start End Blocks Id System
/dev/sda1 * 63 300495824 150247881 83 Linux
/dev/sda2 300495825 312576704 6040440 5 Esteso
/dev/sda5 300495888 312576704 6040408+ 82 Linux swap / Solaris

Disco /dev/sdb: 160.0 GB, 160041885696 byte
255 heads, 63 sectors/track, 19457 cylinders, totale 312581808 settori
Units = settori of 1 * 512 = 512 bytes
Disk identifier: 0xa02134ca

If I read this, it would seem /dev/sda is Linux and /dev/sdb is Vista...
So now it's the other way round?

---

### Post by giamba64 on 2008-09-17
You're right, sorry...
I'm starting to loose my mind...
I confirm: /dev/sda Linux, /dev/sdb Vista

---

### Post by giamba64 on 2008-09-17
...and /dev/sda1 already mounted, impossible to find /dev/sdb1

---

### Post by Orange_and_Green on 2008-09-17
OK, now I've got it :) makes sense now :)

try:

```

title Windows Vista/Longhorn (loader)
root (**hd1**,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1"

```

P.S. You say it doesn't find /dev/sdb1... did you try sudo mounting, i.e.

```

mkdir vista
**sudo** mount /dev/sdb1 vista

```

---

### Post by giamba64 on 2008-09-17
ok, now grub says:
Loading
Starting stage 2 .....

and then the PC frees in a black screen of death...

Argh.......
(P.S.: thanks for your pacience)

---

### Post by Orange_and_Green on 2008-09-17
No problem for me. I am sorry YOU are having such a trouble.

Did you try switching drive boot order? What happened?

---

### Post by giamba64 on 2008-09-17
> **Orange_and_Green said:**
> No problem for me. I am sorry YOU are having such a trouble.

Did you try switching drive boot order? What happened?
absolutely nothing different...
by the way I try to mount vista but

sudo mount /dev/sdb1 vista

asks me to specify filesystem type. I tried to code:

sudo mount -t ntfs /dev/sdb1 vista ntfs

and I got:

"The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?"

---

### Post by caljohnsmith on 2008-09-17
Hi guys, I think you might be getting a little confused about Grub's device.map file, how that relates to Grub on start up, and also how that relates to Ubuntu's order of devices in the /dev directory. When you first start up, the important point is that *Grub sees the order of HDDs the same as the BIOS boot order*. That means if you boot from the Ubuntu HDD, then the Ubuntu entries would be on (hd0). But in your case, since you are able to boot Ubuntu fine from the Grub menu, and its entries use (hd1), that means you must be booting from the Vista drive instead. And that then means that Vista must be on (hd0), not (hd1).

The only time the device.map file is used on start up, to my knowledge, is (for example) when you use references in your Ubuntu entries to /dev/sdX like:
```
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic [COLOR="Blue"]root=/dev/sda2[/COLOR] ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```
Other than that, on start up, Grub doesn't know or care about device.map or the device order in Ubuntu's /dev directory. :)

So bottom line, if I haven't completely overlooked something here, your Vista entry should simply be:
```
title Windows Vista/Longhorn
root (hd0,0)
savedefault
makeactive
chainloader +1
```
So have you all ready tried exactly that, giamba64? Or did you have those mapping lines uncommented from post #1?

---

### Post by giamba64 on 2008-09-17
I'll try it, even if it looks to me that I've already used that entry....

Let's see...

(counless booting...)

---

### Post by Orange_and_Green on 2008-09-17
Hm. Could it possibly be that the vista installation is corrupt?

I believe the first step is to physically locate the Vista drive. If you have a little time to spare, perhaps you could:

1) Pull the power plug from one of the two drives
2) Boot with a live CD and see if the drive that is still on is the Vista or the Linux one;

3)Try running the PC with only the Vista drive (Linux drive cable unplugged) and boot from the vista DVD. See if it recognises the partition and if it lets you "repair" the boot (i.e. overwrite the MBR with its own boot loader)

4)Once you make sure Vista boots again, reattach the Linux drive and tell the BIOS to boot from it. In the best case (depending on where you have GRUB installed right now), GRUB should "magically" work again. If not, you could boot from the Ubuntu live CD and reinstall GRUB (I can give you detailed instructions on that if you wish).

I am glad to assist you with Linux, but unfortunately (well, quite happily actually:twisted:) I have never even touched a computer with Vista so far so I am afreaid I can't help you much on step 3, sorry...

I wish you the best of luck:KS

---

### Post by giamba64 on 2008-09-17
Don't worry, it's my fault.
I know that Vista (or Win) must installed BEFORE and Linux after.... What I find incredible is that if I boot from Ubuntu CD I can mount the Vista partition (actually it's automatically loaded)....

---

### Post by giamba64 on 2008-09-17
> **caljohnsmith said:**
> Hi guys, I think you might be getting a little confused about Grub's device.map file, how that relates to Grub on start up, and also how that relates to Ubuntu's order of devices in the /dev directory. When you first start up, the important point is that *Grub sees the order of HDDs the same as the BIOS boot order*. That means if you boot from the Ubuntu HDD, then the Ubuntu entries would be on (hd0). But in your case, since you are able to boot Ubuntu fine from the Grub menu, and its entries use (hd1), that means you must be booting from the Vista drive instead. And that then means that Vista must be on (hd0), not (hd1).

The only time the device.map file is used on start up, to my knowledge, is (for example) when you use references in your Ubuntu entries to /dev/sdX like:
```
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic [COLOR="Blue"]root=/dev/sda2[/COLOR] ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```
Other than that, on start up, Grub doesn't know or care about device.map or the device order in Ubuntu's /dev directory. :)

So bottom line, if I haven't completely overlooked something here, your Vista entry should simply be:
```
title Windows Vista/Longhorn
root (hd0,0)
savedefault
makeactive
chainloader +1
```
So have you all ready tried exactly that, giamba64? Or did you have those mapping lines uncommented from post #1?
I dit it, but no joy...

---

### Post by caljohnsmith on 2008-09-17
OK, but what exactly happens on start up when you select that new Windows entry? Do you still get a Grub error or is there some other error?

---

### Post by caljohnsmith on 2008-09-17
> **Orange_and_Green said:**
> Hm. Could it possibly be that the vista installation is corrupt?

I believe the first step is to physically locate the Vista drive. If you have a little time to spare, perhaps you could:

1) Pull the power plug from one of the two drives
2) Boot with a live CD and see if the drive that is still on is the Vista or the Linux one;

3)Try running the PC with only the Vista drive (Linux drive cable unplugged) and boot from the vista DVD. See if it recognises the partition and if it lets you "repair" the boot (i.e. overwrite the MBR with its own boot loader)

4)Once you make sure Vista boots again, reattach the Linux drive and tell the BIOS to boot from it. In the best case (depending on where you have GRUB installed right now), GRUB should "magically" work again. If not, you could boot from the Ubuntu live CD and reinstall GRUB (I can give you detailed instructions on that if you wish).

I am glad to assist you with Linux, but unfortunately (well, quite happily actually:twisted:) I have never even touched a computer with Vista so far so I am afreaid I can't help you much on step 3, sorry...

I wish you the best of luck:KS
I agree that it is likely a Vista problem at this point, but unfortunately, since his Grub is actually installed to the master boot record of his Vista drive, he won't be able to boot his Vista drive by itself; he'll get the notorious Grub error 17 or similar, because Grub won't be able to access its stage2 file or menu.lst on his Ubuntu drive if it isn't there.

---

### Post by Orange_and_Green on 2008-09-17
> **caljohnsmith said:**
> I agree that it is likely a Vista problem at this point, but unfortunately, since his Grub is actually installed to the master boot record of his Vista drive, he won't be able to boot his Vista drive by itself; he'll get the notorious Grub error 17 or similar, because Grub won't be able to access its stage2 file or menu.lst on his Ubuntu drive if it isn't there.

That's why I suggested on step 3 that he should boot from the Vista rescue disk with only the Vista drive and let the Vista rescue DVD "fix" the MBR. Afterwards, Grub can safely let that chainload...

BTW, thank you for pointing the thing with the device.map file out :) I am glad I could learn something new myself:):KS

---

### Post by caljohnsmith on 2008-09-17
> **Orange_and_Green said:**
> That's why I suggested on step 3 that he should boot from the Vista rescue disk with only the Vista drive and let the Vista rescue DVD "fix" the MBR. Afterwards, Grub can safely let that chainload...

BTW, thank you for pointing the thing with the device.map file out :) I am glad I could learn something new myself:):KS
+1. You're right, I guess I skimmed too fast and missed your point in #3. That's exactly what I would do to make sure his Vista install is OK. :)

---

### Post by giamba64 on 2008-09-17
it simply says:
"loading stage 2" or similar and then the PC stays on hold

---

### Post by caljohnsmith on 2008-09-17
> **giamba64 said:**
> it simply says:
"loading stage 2" or similar and then the PC stays on hold
So are you not getting the Grub menu any more?

---

### Post by giamba64 on 2008-09-17
> **caljohnsmith said:**
> I agree that it is likely a Vista problem at this point, but unfortunately, since his Grub is actually installed to the master boot record of his Vista drive, he won't be able to boot his Vista drive by itself; he'll get the notorious Grub error 17 or similar, because Grub won't be able to access its stage2 file or menu.lst on his Ubuntu drive if it isn't there.
Actually all my problems started after I installed VISTA, it wrote its own MBR and I could boot only from it.
The I tried to figure out how to restore GRUB and I came out with the idea to use superGRUB which didn't help, though. I could only see the GRUB screen but I couldn't boot form any disk. After reading a bit online (booting fron Ubunto CD) I figured out how to boot from my Ubuntu disk, but I still can't come out with Vista.
Could superGRUB have damaged VISTA's MBR?

---

### Post by giamba64 on 2008-09-17
> **caljohnsmith said:**
> So are you not getting the Grub menu any more?
Yes I am ... But booting with the settings:

title Windows Vista/Longhorn
root (hd0,0)
savedefault
makeactive
chainloader +1

choosing Vista it looks like it starts, but it frees after "Loading stage 2..."

---

### Post by caljohnsmith on 2008-09-17
> **giamba64 said:**
> Actually all my problems started after I installed VISTA, it wrote its own MBR and I could boot only from it.
The I tried to figure out how to restore GRUB and I came out with the idea to use superGRUB which didn't help, though. I could only see the GRUB screen but I couldn't boot form any disk. After reading a bit online (booting fron Ubunto CD) I figured out how to boot from my Ubuntu disk, but I still can't come out with Vista.
Could superGRUB have damaged VISTA's MBR?
From what you have described so far, it looks like it was Super Grub Disk that actually replaced the Vista MBR with Grub. To get the Vista MBR back, you could follow Orange_and_Green's advice about doing a Vista repair. Or first, I think before doing a full repair, I would boot your Vista CD, go to the command line, and run:
```
bootrec /fixmbr 
```
That specifically installs Vista's boot loader to the MBR, nothing else. I would give that a shot first.

---

### Post by Orange_and_Green on 2008-09-17
Well, I wouldn't call that "damaged"... It *overwrites* it ;)

Problem is, while Linux is being "nice" and offers tools like grub to boot other OSes too, Windows really has no interest in being compatible with anything else, so no Windows is capable of booting from anything else than its own boot loader...

So, if you want to be able to boot into vista, you have to restore its boot loader (onto the Vista drive), then install grub onto the Linux drive, and tell grub to "chainload", that is, "passing the ball" to the Vista boot loader.

I can only repeat my former advice to have vista "repair" the MBR of the vista drive (having the linux drive unplugged will make sure nothing strange happens to your Ubuntu installation collaterally), plug the linux drive back in, and then install Grub onto the LINUX drive's MBR...

Good luck:)

---

### Post by Orange_and_Green on 2008-09-17
> **caljohnsmith said:**
> 
```
bootrec /fixmbr 
```

Yep, I had that exactly that in mind... Microsoft calls that a Recovery console. At least, that was like that until XP.
Sorry for being unclear:) Thank you once again for clearing things up caljohnsmith:):KScookie:KS
Today I have difficulties in expressing myself clearly it seems...

---

### Post by giamba64 on 2008-09-17
mmmh it looks lik I 'll be exactly where I tried to get out from.... Possible Vista boot, but NOT guaranteed Ubunto boot... I don't find the GRUB installation that flawless...

---

### Post by giamba64 on 2008-09-17
ok... let's go for it...

---

### Post by Orange_and_Green on 2008-09-17
> **giamba64 said:**
> mmmh it looks lik I 'll be exactly where I tried to get out from.... Possible Vista boot, but NOT guaranteed Ubunto boot... I don't find the GRUB installation that flawless...

To be absolutely sure, you can always pull the plug from the Vista drive before installing grub. So Vista's MBR is safe by default don't you think? ;)

There are many methods to install GRUB, the one I do is:

1)Boot from Ubuntu live CD;
2)```
mkdir Linux_Drive
sudo mount /dev/sda1 Linux_Drive
cd Linux_Drive
ls    {just to make sure this IS the linux drive;)}
sudo grub-install --root-directory=./ /dev/sda
```

[Alternate method]("http://ubuntuforums.org/showthread.php?t=224351")

Good luck:KS

---

