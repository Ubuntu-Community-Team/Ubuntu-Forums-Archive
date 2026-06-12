---
title: "[SOLVED] Hardy plus something?"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by sayakb on 2008-06-04
Hello all
I have tried various distros, but never dual booted Linux with Linux. 
I have a laptop with this setup:
```

glade@Mean-Machine:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.5G  3.5G  5.6G  39% /
varrun                499M   88K  499M   1% /var/run
varlock               499M     0  499M   0% /var/lock
udev                  499M   44K  499M   1% /dev
devshm                499M   12K  499M   1% /dev/shm
lrm                   499M   43M  457M   9% /lib/modules/2.6.24-18-generic/volatile
/dev/sda3             146G   29G  115G  20% /home
gvfs-fuse-daemon      9.5G  3.5G  5.6G  39% /home/glade/.gvfs
glade@Mean-Machine:~$ 

```So I could naturally shrink my /home by 10GB or something.
Now the question is, which distro should I install on that 10GB space, keeping in mind:
1. It shouldn't be based on Ubuntu (Since I can install DEs and WMs and use them as different sessions, so I see no reason to install a whole new OS ;)). Like for example, rather than installing fluxbuntu, I'll install fluxbox WM.
2. It should **not screw up my Hardy **installation (Ive spent loads of time on Hardy, and I don't want to lose it :D :D)

Which distro will recognize Hardy and add it to GRUB/LILO or whatever? Please suggest something that is 100% sure to follow these two criteria.

Thanks in advance
Regards
Dave
(Sayak Banerjee)

---

### Post by JoshuaRL on 2008-06-04
Try Gentoo, and talk to ajmorris for help.  He's really good at Gentoo.

---

### Post by sayakb on 2008-06-04
Ok.. guess I don't have an ISO.. I'll download it :)
Is it 100% certain that I won't lose Hardy?
Thanks

---

### Post by JoshuaRL on 2008-06-04
Well, I'm not 100% certain from personal experience.  I've only booted up the live CD.  But I know that ajmorris here on the forums dual boots it, and is really knowledgable about Gentoo.  I'm sure he'd love to help if you needed it.

Just a little FYI about Gentoo.  Don't look for help from their forums.  There's a big knowledgebase there, but not very nice.

---

### Post by sayakb on 2008-06-04
Thanks :) I'll contact ajmorris after I download the ISO. :)

---

### Post by sayakb on 2008-06-04
I was also thinking of Suse10.3
Has anyone done Suse10.3 install on a system having Hardy and the result has been positive?

---

### Post by dje on 2008-06-04
i've had two installs of ubuntu on the same computer and during installation it detects the other and adds it to the new menu.lst before installing grub onto the new install so you can choose which at boot up

hope that helps,
dje

---

### Post by Oldsoldier2003 on 2008-06-04
> **LinuxIsInnovation said:**
> I was also thinking of Suse10.3
Has anyone done Suse10.3 install on a system having Hardy and the result has been positive?

I havent used suse in a long time but there should be no issues. lately (within the last month I have mutlibooted  these oses with hardy as my main OS. Some of them required some grub magic but nothing a semi advanced new user couldn't handle...


PCLinuxOS- cant remember
Fedora-Recognized Ubuntu
Debian (Lenny and also Etch)- always recognizes ubuntu and other oses
Gentoo- i think i had to grub this one
Arch- had to grub
Mint- recognized ubuntu
CentOS- IIRC i had to configure grub
Slackware- had to grub
Slax- cant remember
puppy linux- pretty sure it recognized ubuntu
damn small linux- pretty sure it recognized ubuntu

I tried several other distributions as well but these are the most memorable ones.

---

### Post by meborc on 2008-06-04
i would try fedora 9... and/or arch... in arch you would need to configure grub yourself i believe

and btw - you can't lose hardy unless you format the partition hardy is on... otherwise, even if grub does not recognize hardy, it is really easy to fix grub

---

### Post by sayakb on 2008-06-04
> **meborc said:**
> i would try fedora 9... and/or arch... in arch you would need to configure grub yourself i believe

and btw - you can't lose hardy unless you format the partition hardy is on... otherwise, even if grub does not recognize hardy, it is really easy to fix grub

Yes right. Ofcourse !!

---

### Post by sayakb on 2008-06-04
> **Oldsoldier2003 said:**
> I havent used suse in a long time but there should be no issues. lately (within the last month I have mutlibooted  these oses with hardy as my main OS. Some of them required some grub magic but nothing a semi advanced new user couldn't handle...


PCLinuxOS- cant remember
Fedora-Recognized Ubuntu
Debian (Lenny and also Etch)- always recognizes ubuntu and other oses
Gentoo- i think i had to grub this one
Arch- had to grub
Mint- recognized ubuntu
CentOS- IIRC i had to configure grub
Slackware- had to grub
Slax- cant remember
puppy linux- pretty sure it recognized ubuntu
damn small linux- pretty sure it recognized ubuntu

I tried several other distributions as well but these are the most memorable ones.

Semi advanced new user... :lolflag:
Correct you are!!
That is huge info. I'll take a look at fedora 9.. seems pretty good. Though I'll try Gentoo on my desktop (Found the 2007.0 CD!!)

---

### Post by kamitsukai on 2008-06-04
pclinuxos is pretty good especially the gnome community version (never dual booted with ubuntu though...)

---

### Post by sayakb on 2008-06-04
I do have another question in mind. Will the /home and swap be visible to both the OSs?

---

### Post by Oldsoldier2003 on 2008-06-04
> **LinuxIsInnovation said:**
> I do have another question in mind. Will the /home and swap be visible to both the OSs?

swap will be visible to all oses. I do not recommend sharing /home between multiple distros. but yes it is visible if you have a separate hime and mount it as /home in the new installation. Especially be advised that if you want to use files owned by your main Ubuntu account you will have to custom create the account with the appropriate UID in fedora and most other non debian distros since they start the user UID space at 500, where Debian based distros start at 1000.

Another thing to remember is that since most distros will format your swap partition without asking, you'll have to fix the fstab for you Ubuntu install to reflect the new UUID of the swap partition, or identify it by /dev/sdXY

---

### Post by sayakb on 2008-06-04
Ok.. practically, I don't need a /home intensively for Fedora. So I'll not create a separate /home and will store my data on the Ubuntu's /home (which will appear as /media/sdax in Fedora if Im not wrong)
But the swap UUID thing worries me. DO I have to waste another 2GB to create a separate swap?

---

### Post by Oldsoldier2003 on 2008-06-04
> **LinuxIsInnovation said:**
> Ok.. practically, I don't need a /home intensively for Fedora. So I'll not create a separate /home and will store my data on the Ubuntu's /home (which will appear as /media/sdax in Fedora if Im not wrong)
But the swap UUID thing worries me. DO I have to waste another 2GB to create a separate swap?

no, use the current swap partition. Fedora will use it with no issues, you'll just have to fix Ubuntu's fstab if the partition gets formatted. If the UUID gets changed then Ubuntu will not be able to find it and will start without a swap partition. Easily enough fixed  by fixing the fstab and running swapon.

---

### Post by wiscados on 2008-06-04
How will formatting swap make any difference?
Wouldn't it be like flushing the RAM when you poweroff the computer?

I've never had problems with swap when multibooting...

---

### Post by sayakb on 2008-06-04
> **Oldsoldier2003 said:**
> no, use the current swap partition. Fedora will use it with no issues, you'll just have to fix Ubuntu's fstab if the partition gets formatted. If the UUID gets changed then Ubuntu will not be able to find it and will start without a swap partition. Easily enough fixed  by fixing the fstab and running swapon.

What if I remove the UUID from fstab? I guess Ubuntu will still mount my swap.

---

### Post by Oldsoldier2003 on 2008-06-04
> **LinuxIsInnovation said:**
> What if I remove the UUID from fstab? I guess Ubuntu will still mount my swap.

removing the UUID and replacing it with the device path works just fine

---

### Post by Oldsoldier2003 on 2008-06-04
> **wiscados said:**
> How will formatting swap make any difference?
Wouldn't it be like flushing the RAM when you poweroff the computer?

I've never had problems with swap when multibooting...

because when the swap partition is formatted the UUID will change. Hardy uses uuid in the fstab by default so it will no longer mount that partition until you repair the fstab entry. As long as you make sure a partition doesn't get formatted then the uuid will not change and you can continue without the need to tweak fstabs

---

### Post by sayakb on 2008-06-04
Thanks. Though I am sincerely inclined towards trying Suse10.3, I'll download Fedora too.. But first I'll try Suse10.3
This addresses my queries I guess. Many thanks to Oldsoldier2003

---

### Post by sayakb on 2008-06-05
Okay.. Suse is up and running! Anyone knows how to add sources to the repos? Or should I post a separate thread at the Other OS talk?

---

