---
title: "The .unison directory"
date: 2011-09-22
forum: New to Ubuntu
---

### Post by derrickr on 2011-09-22
I'm trying to setup Unison to sync my home directory between 3 machines, but am having (newbie) configuration problems.

I've pared down the contents of my home directories so they all have common content, and have included a few ignore path lines in the unison profile to:
```

root = /home/d
root = /media/ufd/home
ignore = Path Music
ignore = Path Videos
ignore = Path VirtualBox VMs
ignore = Path .*
ignorenot = Name .unison/*.prf
```My idea behind the "ignore = Path .*" is to exclude all hidden files and directories, and then use the "ignorenot = Name .unison/*.prf" to not exclude (i.e. include) Unison's profile files.

However, this doesn't have the desired result and the profiles files are totally missed.

In the documentation for Unison it states "[Synchronizing just the profile files in the .unison directory is definitely OK]("http://www.cis.upenn.edu/%7Ebcpierce/unison/download/releases/stable/unison-manual.html#unisondir")".

Unfortunately, I still can't get this aspect to work.

My intention is to synchronise my home directory without any of the . hidden files or directories, but also synchronise the .unison prf profile files.

I've a feeling that I might be misunderstanding some or other important concept, and would appreciate any pointers on syncing just the profile files in the .unison directory.

---

### Post by seawolf167 on 2011-09-22
I'm not familiar with Unision so I can't help you there, sorry :(

But... you could write a simple [rsync ]("https://help.ubuntu.com/community/rsync")script and have it run through [cron ]("https://help.ubuntu.com/community/CronHowto")to sync you directories.

---

### Post by derrickr on 2011-09-22
Hey seawolf167, thanks for the feedback.

After more staring at the documentation, I thought I'd try some other options and found that "ignore = Name {.unison/*}" worked.

I'm still to get my head fully around their use of "Path", "Name" and curly braces {}. But for now, it's working and I'm heading in the right direction - which is what it's all about :)

Unfortunately, I'm not too familiar with rsync (yet), and quite like the features of Unison.

I'm finding home directory synchronisation quite challenging to say the least, so am taking more cautious smaller steps to increase my confidence before diving into the more hard core utilities.

I also read on the [COLOR=Red][Unison wiki faq]("https://alliance.seas.upenn.edu/%7Ebcpierce/wiki/index.php?n=Main.UnisonFAQGeneral")[/COLOR]:
> Rsync is a mirroring tool; Unison is a synchronizer. That is, rsync  needs to be told "this replica contains the true versions of all the  files; please make the other replica look exactly the same." Unison is  capable of recognizing updates in both replicas and deciding which way  they should be propagated.
I'm sure there's be a raised eyebrow or two re which is the better tool, but for now this is the right choice for me at the moment.

Hopefully, this little 'gem' might help someone else with getting used to Unison's features.

---

### Post by derrickr on 2011-09-23
Just in case anyone would like to do similar, here's my default.prf to sync my home directory excluding a few large directories and hidden files/directories, but including .unison's profile files whilst also excluding all other files/dirs under .unison

```
# Set the two roots to sync
root = /home/d
root = /media/ufd32gb

# Set ignores for large/unwanted directories
ignore = Path Music
ignore = Path Videos
ignore = Path VirtualBox VMs

# Set ignore for . hidden files/directories
ignore = Path .*

# Set ignore + ignorenot for .unison profile files,
# excluding Unison's large synchronisation database files
ignore = Path .unison/*
ignorenot = Path .unison
ignorenot = Path .unison/*.prf
```

---

### Post by racknemx on 2013-02-15
Worked like a charm for me, just wanted to say thanks ):P

---

