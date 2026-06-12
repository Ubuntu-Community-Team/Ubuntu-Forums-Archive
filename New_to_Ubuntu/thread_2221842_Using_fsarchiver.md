---
title: "Using fsarchiver"
date: 2014-05-04
forum: New to Ubuntu
---

### Post by LastDino on 2014-05-04
I tried using fsarchiver to clone my Xubuntu installation on my passport HD.

> X@X:~$ sudo blkid
/dev/sda1: UUID="4e138eda-27c8-41cb-877c-e4476559bbd5" TYPE="ext4" 
/dev/sda3: UUID="29e2d3b7-9d7e-45d9-a5af-6876674acd05" TYPE="ext4" 
/dev/sda4: UUID="28da9fb7-539f-404c-9f9e-bdd003821c2b" TYPE="ext4" 
/dev/sda5: UUID="63697cde-bda4-449e-bc54-ca8505aa540f" TYPE="ext4" 
/dev/sda6: UUID="378b48ff-56dc-4650-b7a6-5c2202dfd7ee" TYPE="ext4" 
/dev/sda7: UUID="32a35bd7-9cde-4c86-90c9-aea4ae656339" TYPE="swap" 
/dev/sdb1: LABEL="My Passport" UUID="4E1AEA7B1AEA6007" TYPE="ntfs" 
X@X:~$ sudo fsarchiver -v -j2 -a -A savefs /dev/sdb1/bak/ubu.fsa /dev/sda3
[errno=20, Not a directory]: archwriter.c#116,archwriter_create(): cannot create archive /dev/sdb1/bak/ubu.fsa
Analysing filesystem on /dev/sda3... 				 			

Here /dev/sda3 is my ''/'' drive and I need to clone that to my external: /dev/sdb1. As you can see I get error that you can not create archive, why is that? 

If there are any other software which allow me to do the same (simply cloning the OS not the storage drives (according to need) please suggest them with procedure, if possible. ;)

Thanks in advance!

---

### Post by monkeybrain20122 on 2014-05-04
Opps, sorry, wrong instructions. For the destination you need to put something like /media/yourname/drivename
You can find the drive name by opening it in the file manager

so ```

sudo fsarchiver -v -j2 -a -A savefs /media/yourname/drivename/bak/ubu.fsa /dev/sda3
```

Same goes with restore.

My bad.

---

### Post by LastDino on 2014-05-04
It's ok, but to copy/clone my XUbuntu installation, is cloning my ''/'' enough? Or do I need to clone my ''/home'' as well? 

Also, cloned image is compressed or cloned as it is?

---

### Post by sudodus on 2014-05-04
1. Can you figure out why fsarchiver complains like it does? What is not a directory? Why can't it create the archive? Can you create directories and files with other tools on the target drive?

- Maybe the target partition is mounted without write permissions.
- Maybe there are problems because the target partition has the NTFS file system (instead of a linux file system).

>  [errno=20, Not a directory]: archwriter.c#116,archwriter_create(): cannot create archive /dev/sdb1/bak/ubu.fsa

2. I do not know fsarchiver, but some similar tools. Usually it does not work well to clone or make an image from a mounted partition, particularly the system's root partition. Maybe that is your problem. In that case, boot from a live session from a CD/DVD/USB drive, and try the fsarchiver command again.

Edit: [s]3. If still no go, let us hope [COLOR=#008000]someone who knows fsarchiver[/COLOR] will chip in and help[/s] :-)

4. Finally, it might be an option to try another tool, the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971"), and ***make your own tarball***. That tarball can be used to install the system in another computer (if it is a BIOS system, but does not work with UEFI).

---

### Post by monkeybrain20122 on 2014-05-04
Depends on what do you want to do with the clone. 

If you accidentally screw up your system because of some updates you can just reformat the / and restore just that part. But if you want to migrate your system somewhere then of course you need both.

basically, you can restore it anywhere, but same / has to go with the same /home to boot (uuid info in /etc/fstab). So if /home is already there, like if you just mess up the system, you just need to restore /, while not touching /home at all.

---

### Post by LastDino on 2014-05-04
> **sudodus said:**
> 1. Can you figure out why fsarchiver complains like it does? What is not a directory? Why can't it create the archive? Can you create directories and files with other tools on the target drive?

- Maybe the target partition is mounted without write permissions.
- Maybe there are problems because the target partition has the NTFS file system (instead of a linux file system).



2. I do not know fsarchiver, but some similar tools. Usually it does not work well to clone or make an image from a mounted partition, particularly the system's root partition. Maybe that is your problem. In that case, boot from a live session from a CD/DVD/USB drive, and try the fsarchiver command again.

3. If still no go, let us hope [COLOR=#008000]someone who knows fsarchiver[/COLOR] will chip in and help :-)

4. Finally, it might be an option to try another tool, the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971"), and ***make your own tarball***. That tarball can be used to install the system in another computer (if it is a BIOS system, but does not work with UEFI).

1.I had created the directory in my passport just in case to see what happens before posting here, result was same.

2. I chose fsarchiver because it allows to clone while system is running, unlike clonezilla which needs you to unmount drives you need to clone and boot from its live mode ;)

3.Yeah, Monkybrain is the man in question :p

4.I didn't knew about that, I'll try. 

Thank you for your quick reply!

---

### Post by monkeybrain20122 on 2014-05-04
> **sudodus said:**
> 1. Can you figure out why fsarchiver complains like it does? What is not a directory? Why can't it create the archive? Can you create directories and files with other tools on the target drive?

- Maybe the target partition is mounted without write permissions.
- Maybe there are problems because the target partition has the NTFS file system (instead of a linux file system).



2. I do not know fsarchiver, but some similar tools. Usually it does not work well to clone or make an image from a mounted partition, particularly the system's root partition. Maybe that is your problem. In that case, boot from a live session from a CD/DVD/USB drive, and try the fsarchiver command again.

3. If still no go, let us hope [COLOR=#008000]someone who knows fsarchiver[/COLOR] will chip in and help :-)

4. Finally, it might be an option to try another tool, the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971"), and ***make your own tarball***. That tarball can be used to install the system in another computer (if it is a BIOS system, but does not work with UEFI).

No problem. My bad, I gave the wrong instructions. Just made a trial run cloning to an ntfs formatted drive. worked.

---

### Post by LastDino on 2014-05-04
> **monkeybrain20122 said:**
> Depends on what do you want to do with the clone. 

If you accidentally screw up your system because of some updates you can just reformat the / and restore just that part. But if you want to migrate your system somewhere then of course you need both.

basically, you can restore it anywhere, but same / has to go with the same /home to boot (uuid info in /etc/fstab). So if /home is already there, like if you just mess up the system, you just need to restore /, while not touching /home at all.

I see. Thanks a bunch! I'll try this again! 
Thanks for that software suggestion as well, btw :KS

---

### Post by monkeybrain20122 on 2014-05-04
BTW, fsarchiver doesn't work with gpt and uefi as far as I know. I gave these instructions on another thread where the OP wanted to wipe XP from a dual boot, such complications don't exist on XP machines.

---

### Post by LastDino on 2014-05-04
> **monkeybrain20122 said:**
> BTW, fsarchiver doesn't work with gpt and uefi as far as I know. I gave these instructions on another thread where the OP wanted to wipe XP from a dual boot, such complications don't exist on XP machines.

Mine is ex-XP machine as well, no worries, I read that thread and even subscribed it just in case there was something new ;D

---

### Post by sudodus on 2014-05-04
[I][COLOR=#000000]Goten0007,

[/COLOR][/I]To be on the safe side, I would save an image of /home too.

I think you have soon succeeded with fsarchiver and help from monkeybrain20122 :-)

---

### Post by monkeybrain20122 on 2014-05-04
> **sudodus said:**
> [I][COLOR=#000000]Goten0007,

[/COLOR][/I]To be on the safe side, I would save an image of /home too.


That is a good advice. I usually save / more frequently and just keep a 'shell' for /home in case the system is completely toasted like a hard drive failure and need to recover the whole system elsewhere. By a 'shell' I mean I exclude most data, which I back up with usual file back up utilities. So I would run savefs with the --exclude option. That way the cloning and restoring are very fast. / is usually small so again cloning and restoring with fsarchiver are very fast.

So the command would be something like
    ```
sudo fsarchiver -v -j2 -a -A savefs /media/yourname/drivename/bak/ubu_home.fsa /dev/sda5 --exclude=Music --exclude=Downloads --exclude=Videos 

```

---

### Post by LastDino on 2014-05-04
Looks like we celebrated too quickly.

> glen@Maxwell:~$ sudo fsarchiver -v -j2 -a -A savefs /media/glen/My Passport/bak/ubu.fsa /dev/sda3
oper_save.c#1155,oper_save(): Passport/bak/ubu.fsa is not a valid block device
glen@Maxwell:~$ sudo fsarchiver -v -j2 -a -A savefs /media/glen/MyPassport/bak/ubu.fsa /dev/sda3
[errno=2, No such file or directory]: archwriter.c#116,archwriter_create(): cannot create archive /media/glen/MyPassport/bak/ubu.fsa
Analysing filesystem on /dev/sda3...
glen@Maxwell:~$ sudo fsarchiver -v -j2 -a -A savefs /media/glen/MyPassport/bak/ubu.fsa /dev/sda3


The drive is mounted and I can copy/paste/delete things from it fine, so it is probably not permission problem. I've already tried removing space between ''My Passport'' and few other things as you can see, I think it being NTFS might really be the problem here? Or is it something else?

---

### Post by monkeybrain20122 on 2014-05-04
Analysing file system takes a bit of time. What did it say?

  Never abort it when it is running, if that happens make sure you shut down and reboot immediately or something may stay in /tmp and corrupt your system.

Ntfs is not a problem, I just got an ntfs drive and backed up to it (cloning a ntfs system may be a problem, as in trying to clone Windows)

---

### Post by sudodus on 2014-05-04
You need quotes around the path containing a blank

```

"/media/glen/My Passport/bak/ubu.fsa" /dev/sda3
```

---

### Post by LastDino on 2014-05-04
> **monkeybrain20122 said:**
> Analysing file system takes a bit of time. What did it say?

  Never abort it when it is running, if that happened make sure you shut down and reboot immediately or something may stay in /tmp and corrupt your system.

It threw me back to my prompt without showing in result or even error while analyzing. I did not abort it from me end.

> glen@Maxwell:~$ sudo fsarchiver -v -j2 -a -A savefs /media/glen/MyPassport/bak/ubu.fsa /dev/sda3
[errno=2, No such file or directory]:  archwriter.c#116,archwriter_create(): cannot create archive  /media/glen/MyPassport/bak/ubu.fsa
Analysing filesystem on /dev/sda3...
glen@Maxwell:~$

---

### Post by LastDino on 2014-05-04
> **sudodus said:**
> You need quotes around the path containing a blank

```

"/media/glen/My Passport/bak/ubu.fsa" /dev/sda3
```

Let me try this :KS

Edit:

Nope, looks like that is not it.

> glen@Maxwell:~$ sudo fsarchiver -v -j2 -a -A savefs ''/media/glen/My Passport/bak/ubu.fsa'' /dev/sda3
oper_save.c#1155,oper_save(): Passport/bak/ubu.fsa is not a valid block device
glen@Maxwell:~$ sudo fsarchiver -v -j2 -a -A savefs ''/media/glen/My_Passport/bak/ubu.fsa'' /dev/sda3
[errno=2, No such file or directory]: archwriter.c#116,archwriter_create(): cannot create archive /media/glen/My_Passport/bak/ubu.fsa
Analysing filesystem on /dev/sda3...
glen@Maxwell:~$ sudo fsarchiver -v -j2 -a -A savefs ''/media/glen/My-Passport/bak/ubu.fsa'' /dev/sda3
[errno=2, No such file or directory]: archwriter.c#116,archwriter_create(): cannot create archive /media/glen/My-Passport/bak/ubu.fsa
Analysing filesystem on /dev/sda3...
glen@Maxwell:~$ 


---

### Post by monkeybrain20122 on 2014-05-04
You should detach, remount the drive. If there is a space in the name use quotations as sudodus said.

---

### Post by monkeybrain20122 on 2014-05-04
> **Goten0007 said:**
> Let me try this :KS

But detach and reattach the drive first.

---

### Post by LastDino on 2014-05-04
> **monkeybrain20122 said:**
> But detach and reattach the drive first.

Yes, tried that as well. No luck.

Also, why is it that this particular command not asking for my sudo password? That is bit odd.

---

### Post by monkeybrain20122 on 2014-05-04
It should ask for your sudo password.

What was the output?

Maybe reboot and try again?

---

### Post by LastDino on 2014-05-04
> **monkeybrain20122 said:**
> It should ask for your sudo password.

What was the output?

> glen@Maxwell:~$ sudo sh -c "sync; echo 3 > /proc/sys/vm/drop_caches"
[sudo] password for glen: 
glen@Maxwell:~$ sudo fsarchiver -v -j2 -a -A savefs ''/media/glen/My_Passport/bak/ubu.fsa'' /dev/sda3
[errno=2, No such file or directory]: archwriter.c#116,archwriter_create(): cannot create archive /media/glen/My_Passport/bak/ubu.fsa
Analysing filesystem on /dev/sda3...
glen@Maxwell:~$ sudo fsarchiver -v -j2 -a -A savefs ''/media/glen/My Passport/bak/ubu.fsa'' /dev/sda3
oper_save.c#1155,oper_save(): Passport/bak/ubu.fsa is not a valid block device
glen@Maxwell:~$ 



As you can see, others are asking but not this one. And error is same and I tried both with and without space. This is some food for thought.lmao

---

### Post by monkeybrain20122 on 2014-05-04
How did you change the name of the drive?

---

### Post by monkeybrain20122 on 2014-05-04
The drive should be mounted. So if you used gparted to change its label it would become unmounted.

---

### Post by LastDino on 2014-05-04
> glen@Maxwell:~$ sudo fsarchiver -v -j2 -a -A savefs /media/glen/My Passport/bak/ubu.fsa /dev/sda3
[sudo] password for glen: 
oper_save.c#1155,oper_save(): Passport/bak/ubu.fsa is not a valid block device
glen@Maxwell:~$ sudo fsarchiver -v -j2 -a -A savefs ''/media/glen/My Passport/bak/ubu.fsa'' /dev/sda3
oper_save.c#1155,oper_save(): Passport/bak/ubu.fsa is not a valid block device
glen@Maxwell:~$ sudo fsarchiver -v -j2 -a -A savefs ''/media/glen/My_Passport/bak/ubu.fsa'' /dev/sda3
[errno=2, No such file or directory]: archwriter.c#116,archwriter_create(): cannot create archive /media/glen/My_Passport/bak/ubu.fsa
Analysing filesystem on /dev/sda3...
glen@Maxwell:~$ 


Result after restart, it asked for password first time but not after that. 
I didn't change the name, original name as I see in file manager is: /media/glen/My Passport/
And it is mounted.

---

### Post by sudodus on 2014-05-04
It seems to me that fsarchiver is not helped by the quotes. I suggest that you change the label of the partition in the USB drive to a label without a space (for example My_Passport or backup1 (whatever suits you).

Use ***gparted*** to change the label.

Then mount it, change the command with fsarchiver to use the new label (and path to the target).

---

### Post by monkeybrain20122 on 2014-05-04
Seems that the space is the problem. Since quotations don't work, maybe you need to change the label to something without space. There maybe a way to do it with the disk utility, but since I never used it I would suggest gparted, which needed to be installed.

Once you installed gparted, open it, go to gparted > Device, locate the external drive and unmount it and then right click to change label. Then click "apply". When done, detach and re-attach it. Go to the file manager to see if the drive name has changed.. 

And then run fsarchiver again. Good luck. :)

---

### Post by LastDino on 2014-05-04
> **sudodus said:**
> It seems to me that fsarchiver is not helped by the quotes. I suggest that you change the label of the partition in the USB drive to a label without a space (for example My_Passport or backup1 (whatever suits you).

Use ***gparted*** to change the label.

Then mount it, change the command with fsarchiver to use the new label (and path to the target).

Unmounted
Label changed with gparted to Passport
Mounted

How I see it in file manager: /media/glen/Passport/


> glen@Maxwell:~$ sudo fsarchiver -v -j2 -a -A savefs /media/glen/Passport/bak/ubu.fsa /dev/sda3
[sudo] password for glen: 
[errno=2, No such file or directory]: archwriter.c#116,archwriter_create(): cannot create archive /media/glen/Passport/bak/ubu.fsa
Analysing filesystem on /dev/sda3...
glen@Maxwell:~$ 

Reply from terminal.
Though, something new, I found out that it asks for pass when I restart the terminal only. (With this particular command)

Edit:
Actually, I tried this command with ''..'' again even though you said otherwise and it has successfully started to analyze the thing. I'll bounce back here to show the results. 
> sudo fsarchiver -v -j2 -a -A savefs ''/media/glen/Passport/bak/ubu.fsa'' /dev/sda3
Man has gotta eat something to live :P

---

### Post by LastDino on 2014-05-04
> **monkeybrain20122 said:**
> Seems that the space is the problem. Since quotations don't work, maybe you need to change the label to something without space. There maybe a way to do it with the disk utility, but since I never used it I would suggest gparted, which needed to be installed.

Once you installed gparted, open it, go to gparted > Device, locate the external drive and unmount it and then right click to change label. Then click "apply". When done, detach and re-attach it. Go to the file manager to see if the drive name has changed.. 

And then run fsarchiver again. Good luck. :)

'k by the time I came back from kitchen things looked like this

> Statistics for filesystem 0
* files successfully processed:....regfiles=139975, directories=16338, symlinks=45454, hardlinks=2, specials=85
* files with errors:...............regfiles=0, directories=0, symlinks=0, hardlinks=0, specials=0



So, ''/'' has been cloned successfully, I guess?

Thank you for going through so much trouble. I'll do the same with /home. :KS

---

### Post by monkeybrain20122 on 2014-05-04
Congrad! You made it. :) Now you can mark the thread as solved. :)

Edited: Since you use the -v option there should be a long list of outputs of file names and % etc. Did you see that?

---

### Post by LastDino on 2014-05-04
> **monkeybrain20122 said:**
> Congrad! You made it. :) Now you can mark the thread as solved. :)

Edited: Since you use the -v option there should be a long list of outputs of file names and % etc. Did you see that?

Yes, yes, I did! 


One more thing, since I've separate ''/boot'' will I've to install grub again if I want to boot from this cloned system when I copy this to some other machine?

---

### Post by monkeybrain20122 on 2014-05-04
Hmm.. That makes things a bit more complicated. I have never used a /boot partition, just / and /home.  I don't know if you can just install grub in your / on restore. may need to mess with things like fstab as well.

In my case grub is in / so just restore and work, don't need to do anything.

---

### Post by LastDino on 2014-05-04
Can't I just clone ''/boot'' too? Sounds like it should work, at least for system which has same BIOS. Or at least mine.

---

### Post by monkeybrain20122 on 2014-05-04
> **Goten0007 said:**
> Can't I just clone ''/boot'' too? Sounds like it should work, at least for system which has same BIOS. Or at least mine.

yes I would think so.

---

### Post by LastDino on 2014-05-04
Cool! 
I'll marked this as solved.

---

### Post by monkeybrain20122 on 2014-05-04
BTw in this case you may want to always clone /boot and / together in one single archive

so the command would be (say sda2 is /boot, sda3 is /)

```
sudo fsarchiver -v -j2 -a -A savefs /media/yourname/drivename/bak/ubu.fsa /dev/sda1 /dev/sda3
```

To restore /boot to sda6 and / to sda7, for example, you would do
```
sudo fsarchiver -v -j2 restfs /media/.../ubu.fsa id=0,dest=/dev/sda6 id=1,dest=/dev/sda7
```

Remember restore is run from a live usb so the media's name will change.
-a  -A are not necessary if you clone by running fsarchiver in a live usb, they are for live cloning

---

### Post by sudodus on 2014-05-04
Congratulations :KS

---

### Post by LastDino on 2014-05-04
> **monkeybrain20122 said:**
> BTw in this case you may want to always clone /boot and / together in one single archive

so the command would be (say sda2 is /boot, sda3 is /)

```
sudo fsarchiver -v -j2 -a -A savefs /media/yourname/drivename/bak/ubu.fsa /dev/sda1 /dev/sda3
```

To restore to /boot to sda6 and / to sda7, for example, you would do
```
sudo fsarchiver -v -j2 restfs /media/.../ubu.fsa id=0,dest=/dev/sda6 id=1,dest=/dev/sda7
```

Remember restore is run from a live usb so the media's name will change.
-a  -A are not necessary if you clone by running fsarchiver in a live usb, they are for live cloning

Hmm thanks for that, I'll make one more image with ''/'' and /boot together. 'k

Thank you again ^^

---

