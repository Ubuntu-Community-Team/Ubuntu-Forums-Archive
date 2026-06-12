---
title: "massive help needed - GDM issue ?"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by dreamstalker on 2008-07-17
i was logging into root one day to change some permissions and when i restarted this came up:
server authorization directory (deamon/servauthdir) is set to
/var/lib/gdm but this does not exist. Please correct gdm
configuration and restart gdm
                             <ok>
and then click ok then it says my version and then 
jordan-laptop login:_

now from my understanding im f....ed

---

### Post by hyper_ch on 2008-07-17
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

---

### Post by snowpine on 2008-07-17
:)
Good luck!

---

### Post by dreamstalker on 2008-07-17
srry that link is worth nothing to me

---

### Post by wolfen69 on 2008-07-17
try re-installing gdm
```
 sudo apt-get install gdm
```

---

### Post by t0p on 2008-07-17
I don't know what it is you're askin for.

If you restate your problem, that might help?

---

### Post by ByteJuggler on 2008-07-17
Sounds like you did a bit more than just "change permissions" when you were root... (or you changed the permissions such that no-one can access "/var/lib/gdm"...)

You should log into a console (ctrl-alt-f1, then login at prompt), then go and check if /var/lib/gdm actually exists or not and act accordingly (e.g. if it does exist then it must be some sort of permissions problem so fix that with w.g. "chown" and "chmod" or if it doesn't exist then recreate those folders.)

As an aside:  On Ubuntu, you should generally leave the root account locked and only use "sudo" for commands that require to be run as root.  (So please, do read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) )  If you've unlocked your root account at some point, you can lock it again with "sudo passwd -l root"

---

### Post by bapoumba on 2008-07-17
Thread title edited, please sugget a more appropriate one if needed, thanks.

---

### Post by dreamstalker on 2008-07-17
i found out that i did change all permissions in filesystem to deny....... and can not even login anymore

---

### Post by philinux on 2008-07-17
Seeing as you know how to change permissions.

Boot up and press esc when you see grub stage 1.5 or other.

Select the recovery mode.

This is root mode too.

Change the permissions for your /home folder

---

### Post by dreamstalker on 2008-07-17
i dont no how to change permisiomns through command mode

---

### Post by philinux on 2008-07-17
As a last resort.
Seeing as we're not sure exactly what's been changed. Could be the root file system as well as home.

The best thing I can suggest it to boot the live cd and use it to backup anything important in your home folder.

Like firefox and thunderbird folder, your stuff like pics docs etc etc.
Either use a usb stick or a cd or dvd.

Then reinstall.

Unless someone comes along with a better idea.

---

### Post by dreamstalker on 2008-07-17
i no but i have more than just files that are important and is there any posssability that permissions could be changed ...... i no what i changed......... everything in filesystem drive (i no it was an accident)

---

### Post by philinux on 2008-07-17
Whats the current state. Can you get to the login screen.

We can use the chown command to puts things right either from recovery mode or the live cd.

Also click the report button on your first post and ask the mods to change to the title to

"How do I reset my file permissions to the default"

---

### Post by SunnyRabbiera on 2008-07-17
why were you using root for?

---

### Post by ByteJuggler on 2008-07-17
> **dreamstalker said:**
> i no but i have more than just files that are important and is there any posssability that permissions could be changed ...... i no what i changed......... everything in filesystem drive (i no it was an accident)

OK, try the following:

1) Bootup with Ubuntu LiveCD.
2) Open a terminal.  Type the command:
```
sudo fdisk -lu
```

3) In the output, find the line (there should be only 1, if you have a default/generic install) with "Linux" at the end (not "Linux swap", that's something else), e.g. for example
```
   Device Boot      Start         End      Blocks   Id  System
***/dev/sda1***   *          63   613056464   306528201   83  Linux

```
and then note down the bit at the start, e.g. ***/dev/sda1***

4) Type the following commands, replacing ***/dev/sda1*** with what you noted above:
```
sudo -i
mkdir /mnt/linux
mount ***/dev/sda1 ***/mnt/linux
find /mnt/linux -type d -exec chmod 755 '{}' \;
find /mnt/linux -type f -exec chmod 644 '{}' \;
umount /mnt/linux
exit

```

That should get your system booting again, by granting read privileges to world on every file on your system.  You should obviously go back and tighten that up if needed afterwards.

Note: If you get any error after any command, **stop** and post back here, quoting the exact message you got. 

P.S. It's "I know what I changed...", not "i no what i changed..."

---

### Post by dreamstalker on 2008-07-17
i was using root to change a fstab file...... and no i cannot get to login s1creen only boot then takes me to a command page

---

### Post by ByteJuggler on 2008-07-18
> **dreamstalker said:**
> i was using root to change a fstab file...... and no i cannot get to login s1creen only boot then takes me to a command page

As I said, **boot up with the Ubuntu LiveCD**.   That ***_*will* _***get you to a working desktop, from which you can then follow the rest of the instructions I gave you.

---

### Post by macvr on 2008-09-09
```
server authorization directory (deamon/servauthdir) is set to
/var/lib/gdm but this does not exist. Please correct gdm
configuration and restart gdm
                             <ok>

```
i get his same error... so i tried

> **ByteJuggler said:**
> OK, try the following:

1) Bootup with Ubuntu LiveCD.
2) Open a terminal.  Type the command:
```
sudo fdisk -lu
```

3) In the output, find the line (there should be only 1, if you have a default/generic install) with "Linux" at the end (not "Linux swap", that's something else), e.g. for example
```
   Device Boot      Start         End      Blocks   Id  System
***/dev/sda1***   *          63   613056464   306528201   83  Linux

```
and then note down the bit at the start, e.g. ***/dev/sda1***

4) Type the following commands, replacing ***/dev/sda1*** with what you noted above:
```
sudo -i
mkdir /mnt/linux
mount ***/dev/sda1 ***/mnt/linux
find /mnt/linux -type d -exec chmod 755 '{}' \;
find /mnt/linux -type f -exec chmod 644 '{}' \;
umount /mnt/linux
exit

```

That should get your system booting again, by granting read privileges to world on every file on your system.  You should obviously go back and tighten that up if needed afterwards.

Note: If you get any error after any command, **stop** and post back here, quoting the exact message you got. 

P.S. It's "I know what I changed...", not "i no what i changed..."

but after  i did this and rebooted i get
```

BusyBox v1.1.3(Debian 1:1.1.3-5Ubuntu)
Enter Help for listing

(initramfs)
```

but unlike the OP i DONT KNOW how i got into this mess!!!
need urgent help

---

### Post by macvr on 2008-09-09
guys ????????

how do  i get past? the BusyBox? can i reverse the permissions like this?
```
sudo -i
mkdir /mnt/linux
mount ***/dev/sda5 ***/mnt/linux
find /mnt/linux -type d -exec chmod 644 '{}' \;
find /mnt/linux -type f -exec chmod 755 '{}' \;
umount /mnt/linux
exit

```
or would it mess up  my system further?

---

### Post by ByteJuggler on 2008-09-09
How do you know your problem is permissions?  

What happens if you just exit the busybox shell? (E.g. type "exit" and press Enter.)  There can be many reasons other than permissions for you ending up at the busybox initramfs shell...

---

### Post by macvr on 2008-09-09
my problem wasnt permissions!!!
got some help from the irc and now have recovered the system but my programs are all messed up!do u know of anyway to recover the file permissions for all programs back to normal?

---

### Post by ByteJuggler on 2008-09-09
> **macvr said:**
> my problem wasnt permissions!!!
got some help from the irc and now have recovered the system but my programs are all messed up!do u know of anyway to recover the file permissions for all programs back to normal?

What do you mean by "messed up"?  What problems, exactly, are you having?  Have you already updated the permissions on all files as per my suggestion or not?  Are you getting any error messages?  If so what?

As an aside: Are you running Ubuntu Hardy (8.04)?  I might try to come up with a script to restore the permissions on standard files (rather than blanket changing all of them), if that turns out that it will help...

---

### Post by macvr on 2008-09-09
> **ByteJuggler said:**
> What do you mean by "messed up"?  What problems, exactly, are you having?  Have you already updated the permissions on all files as per my suggestion or not?  Are you getting any error messages?  If so what?

As an aside: Are you running Ubuntu Hardy (8.04)?  I might try to come up with a script to restore the permissions on standard files (rather than blanket changing all of them), if that turns out that it will help...
i have done this to reset the permissions
```
while read -d : dir; do sudo chmod +x "$dir"/*; done <<< "$PATH"

```
the above command was given in the irc...
seems to have corrected the 'permissions denied'/'child process' errors for some programs but still lot of programs seem to give permission errors...

was actually adviced to reinstall the package when i get error.... what if i selected ALL packages in synaptic and reinstalled them?
or if u have a better reset command?[i'm not able to find ur suggestions?]

---

