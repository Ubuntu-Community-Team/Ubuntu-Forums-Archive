---
title: "crash on trying to upgrade ubuntu"
date: 2012-03-02
forum: New to Ubuntu
---

### Post by otaji on 2012-03-02
On trying to upgrade, as prompted, to a higher version of ubuntu my pc crashed--possibly because of the limited capacity of my computer. On trying to restart with ubuntu nothing happened, and the only option appears to be to use the item indicated on the startup screen : 'Ubuntu with Linux 2.6.38-5-generic (Recovery Mode)'. As a beginner with ubuntu I haven't a clue as to how to proceed using this procedure. Please can anybody help me in this process with easy to follow steps as I am a beginner. Thanks.

---

### Post by matt_symes on 2012-03-02
Hi

You have 2 main options here.

1. You can try to fix your existing install. This may be problematic especially if it crashed while in the middle of installing packages.

2. Your other option is to back up your data and reinstall. You can reinstall your existing version of Ubuntu or download the upgraded version, burn that to a CD or USB and install that.

What happens when you boot into recovery mode ?

What are the stats of your computer ?

Kind regards

---

### Post by otaji on 2012-03-02
Many thanks for your reply and advice.
The recovery mode produces an interactive screen in which I don't know what inputs to make. Perhaps you can advise on this.
I will try to get an ubuntu cd to try reinstalling.
Best regards

---

### Post by Jake5 on 2012-03-02
Can you write down the options and post them here so we can get a better idea of what you're working with?

---

### Post by matt_symes on 2012-03-02
Hi

> **otaji said:**
> Many thanks for your reply and advice.
The recovery mode produces an interactive screen in which I don't know what inputs to make. Perhaps you can advise on this.
I will try to get an ubuntu cd to try reinstalling.
Best regards

In the recovery console enter these commands and post back the results.

```
df -h
```

```
uname -a
```

```
cat /etc/lsb-release
```

```
free -m
```

That will check free disk space, display the current kernel version, display the current distribution and show how much memory you have.

Kind regards

---

### Post by otaji on 2012-03-03
Thanks very much for your suggestions just noted. I will try to follow them and let you know the results.

---

### Post by otaji on 2012-03-05
My pc is EMachines E4231 Intel Celeron 420@1.60GHz 512MB Windows Vista Basic 48.1GB with 17.3GB free space
Answers for ubuntu codes in recovery mode:
code df -h   invalid option
code uname -a
starting AppArmor profiles
skipping profile in /etc/apparmor.d/disable:usr.bin.firefox
*setting sensors limits
skip stopping firewall :ufa (not enabled)
code: cat /etc/lsb-release
DISTRIB_ID=Ubuntu   DISTRIB_RELEASE=11.10 
DISTRIB__CODENAME=oneiric     DISTRIB__DESCRIPTION="Ubuntu 11.10"
code: free -m
Mem: total       used free shared  buffers cached
      485         114 371   0        33      46
-/+buffers/cache  33  452
swap: 817          0  817
On trying to start recovery mode it's unable to get network con:confused:figuration
Please help as I'm an absolute beginner!  Thanks

---

### Post by matt_symes on 2012-03-05
Hi

The first two commands should have produced out like mine below.

```
matthew@server1:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G  4.0G   14G  23% /
none                  367M  252K  367M   1% /dev
none                  375M     0  375M   0% /dev/shm
none                  375M  420K  374M   1% /var/run
none                  375M     0  375M   0% /var/lock
/dev/sda6             127G  109G   13G  90% /home
/dev/sdc1             917G  765G  106G  88% /mnt/storage
/dev/sdb1             150G   91M  149G   1% /mnt/windows_share
matthew@server1:~$ uname -a
Linux server1 2.6.38-13-generic-pae #56-Ubuntu SMP Tue Feb 14 14:32:30 UTC 2012 i686 athlon i386 GNU/Linux
matthew@server1:~$ 
```

The specs of your system are enough to run Ubuntu server. I only have 750 M on this server and i only added the other 250 last week. It was 500M before that.

```
matthew@server1:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           748        740          8          0         22        523
-/+ buffers/cache:        193        554
Swap:         1905          0       1905
matthew@server1:~$
```

> swap: 817 0 817

I would personally add more swap.

> Please help as I'm an absolute beginner!

My advice ? As you are a beginner, i would back up and reinstall. Your system may be in an inconsistent state if it fell over while installing packages between Ubuntu versions. The problem may be small or large.

A clean install is better than an upgrade anyway.

Kind regards

---

### Post by otaji on 2012-03-06
Hi matt-symes and many thanks for all your help.
I'll take your advice and try a clean install.
I presume that the previous ubuntu version already installed, and not active, will continue to occupy space on my hard disk and can't be erased?

---

### Post by matt_symes on 2012-03-06
Hi

> **otaji said:**
> 
I presume that the previous ubuntu version already installed, and not active, will continue to occupy space on my hard disk and can't be erased?

You can erase the old version when installing. Just format the partition.

Might i suggest a separate home partition as well. You can then reinstall onto your root partition inn the future if you ever need to.

Make sure you backup all your files first though. You can do this from a LiveCD/USB.

Kind regards

---

### Post by otaji on 2012-03-06
Hello matt-symes and many thanks again for all your trouble.
Some stupid beginner questions:
bearing in mind that I used an ubuntu cd (now mislaid but I should be able to find it) to install the initial version which resulted in an automatic split of the hard disk between windows vista and ubuntu. I hardly used ubuntu so I have very few files to back up.
Would I need to backup my windows vista files when installing a new version of ubuntu which I can also presumably download from the ubuntu website?
How do I 'format the partition'? And how does the installed version of ubuntu get erased?
What do you mean by a 'home partition' and a 'separate home partition' and a 'root partition'?
I hope you will accept these beginner quetions.
with my thanks and best regards.

---

### Post by matt_symes on 2012-03-06
Hi

First are you installing Ubuntu server or desktop ? 

For some reason i thought it was Ubuntu server however i see no mention of it in your initial post. 

I suspect it's Ubuntu desktop you are installing. If it then you can specify which partition on one of the installation screens. The screen where it gives you the options to "use the entire hard drive", "install side by side" or "manually specify partitions (Advanced)".

It's the last option you want. It will scan your hard drive looking for partitions and one of them will be ext4 (not linux swap). You need to select that partition as your root partition and format it.

**Does anybody else have a tutorial with pictures of how to install to a specific partition using the manual method ? If so then please post a link on this thread for the OP.**

I always recommend imaging the hard drive (if you have a spare big enough) before installing any operating system that may mess with the partitions. If you want to do this and need help then post back.

If i have missed anything, others will help out.

> What do you mean by a 'home partition' and a 'separate home partition' and a 'root partition'?

Ignore this for the moment. It's more specialised again and may not be right for you.

Kind regards

---

### Post by nothingspecial on 2012-03-06
1. Yes please back up anything you don't want to loose. This is vital before performing an installation.

2. Boot the cd

3. Choose Install Ubuntu

4. Whaen the installer asks you how you want to install Ubuntu choose "something else"

5. Select the ext4 partition and choose to change it

6. Choose to use it as an ext4 journaling file system, give it a mountpoint of / and tick/check the format box.

7. Do not touch the windows ntfs partition.

That's it.

---

### Post by otaji on 2012-03-06
hi and many thanks for 'matt-symes' and 'nothingspecial'
yes it appears to be ubuntu desktop. I don't recall server being mentioned with the installation instructions.
Would ext4 relate to the ubuntu installed software?
How can I image the hard drive? Is this done in one go? I do have a large capacity portable hard drive but I copy a small number of files at a time.
Question for 'nothingspecial' :
you mention specifying 'ext4 journaling file system' and to give it 'a mountpoint of' and you don't say of what. Please explain.
Thanks and best regards to both of you

---

### Post by matt_symes on 2012-03-09
Hi

Sorry for the delay in replying. I have had a very busy couple of days.

> **otaji said:**
> hi and many thanks for 'matt-symes' and 'nothingspecial'
yes it appears to be ubuntu desktop. I don't recall server being mentioned with the installation instructions.
Would ext4 relate to the ubuntu installed software?

ext4 is the filing system Ubuntu uses by default. It's a way of organising your files on your hard drive.

> 
How can I image the hard drive? Is this done in one go? I do have a large capacity portable hard drive but I copy a small number of files at a time.

You can image your hard drive using clonezilla or ddrescue.

Kind regards

---

### Post by matt_symes on 2012-03-09
? duplicate?

---

### Post by otaji on 2012-03-09
> **matt_symes said:**
> Hi

Sorry for the delay in replying. I have had a very busy couple of days.



ext4 is the filing system Ubuntu uses by default. It's a way of organising your files on your hard drive.



You can image your hard drive using clonezilla or ddrescue.

Kind regards
thanks again matt-symes for the additional info. Best regards

---

### Post by otaji on 2012-03-14
Hi matt-symes. I have got nowhere! There is an error showing when I try to install, within Windows Vista, Ubuntu 10.10 using an official Ubuntu disk although this worked ok some months ago. This disk also doesn't work when it is inserted before the pc startup! Any suggestions as to how I can remove the previous ubuntu partition and reinstall 10.10? As a beginner I need simple and very detailed guidelines. 
Best regards

---

### Post by matt_symes on 2012-03-14
Hi

> **otaji said:**
> Hi matt-symes. I have got nowhere! There is an error showing when I try to install, **within Windows Vista**, Ubuntu 10.10 using an official Ubuntu disk although this worked ok some months ago.

Was your previous install a Wubi install or did you install to a partition ?

> This disk also doesn't work when it is inserted before the pc startup! Any suggestions as to how I can remove the previous ubuntu partition and reinstall 10.10? As a beginner I need simple and very detailed guidelines.

Is the first boot device in the BIOS the CD or the hard drive ? 

How did you make the LiveCD ? Please detail the steps you took.

Kind regards

---

### Post by Gremlinzzz on 2012-03-14
wubi install and wubi remove:popcorn:

---

### Post by otaji on 2012-03-22
hi matt-symes and many thanks for your reply. I apologise for the late reply due to my being away for several days.
I originally installed ubuntu 10.10 using a 'computeractive' installation cd. 
On retrying lately I eventually managed to reinstall ubuntu 10.10 within windows vista.
I would like to delete the existing ubuntu 10.10 program as it is useless and occupying useful hard drive space but I think the process is irreversible---according to the  installation disk info as I remember the ubuntu partition can't be deleted?
I think booting takes place first by the hard drive.
Best regards

---

### Post by matt_symes on 2012-03-23
Hi

You should just be able to uninstall it. That should remove the old WUBI install

I am no expert with WUBI though, as i have never used it, so i would wait for someone else to comment first.

Kind regards

---

