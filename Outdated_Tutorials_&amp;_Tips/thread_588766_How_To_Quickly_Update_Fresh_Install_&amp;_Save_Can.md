---
title: "How To: Quickly Update Fresh Install &amp; Save Canonical Money"
date: 2007-10-23
forum: Outdated Tutorials &amp; Tips
---

### Post by Ek0nomik on 2007-10-23
**Difficulty**:  Beginners.
**Length**:  Varies.  (I predict 5-10 minutes, but network card and user error can play a role. :))

Did you just do a fresh install and update of Ubuntu?  Do you plan on installing Ubuntu onto another computer?  Impatient to wait for your second install to fetch all the updates or are concerned about making Canonical (creators of Ubuntu) pay for you second update?

Assuming you have both computers on a LAN, you can update your second install of Ubuntu much quicker than waiting to download them all from the Ubuntu servers.

Real Life Example:  I just did a fresh install of Ubuntu Gutsy 7.10 three days ago.  I wanted to update my server to Ubuntu Gutsy as well, so I edited the sources.list file and ran an update, and dist-upgrade.  It started to download all the files, but it was going to take **two days** to finish updating because the Ubuntu servers were getting hammered and my Internet was capped at school.  This guide is going to show you how you just need *one* computer updated after a fresh install so you can update quicker and save Canonical money, and allow others to download faster who may need the bandwidth.

This guide is going to show you how to:
[LIST=1]
[*]Copy the update files from your updated computer to your old computer (the one that needs the updates).
[*]Update your second computer with the fetched files.
[/LIST]

To visualize this better, the *updated* computer is going to run Ubuntu Gutsy 7.10.  The *old* computer is going to run Ubuntu Feisty 7.04.

**1.**  You can copy the files to your old computer in a variety of ways.  I personally will suggest you do it with SSH.

Since SSH has been covered hundreds of times, I'll leave setting that up to you.  If you're confused, here is a link that will help:

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto) (If you're nervous, check out the 'Graphically' section.  It's really easy!)

You need to navigate to /var/cache/apt/archives on your *updated* computer.  You will probably see a lot of files in this directory.  Everything you have ever downloaded via apt-get, with Synaptic package manager, or with the Update utility will get stored here.  This is what we're going to make use of!

You can either copy and paste the files graphically or you can transfer the files at the terminal to your *old* computer.  You will want to place these files in the /var/cache/apt/archives folder on your *old* computer.

**Note**:  You will probably get a permission error since /var/cache/apt/archives is owned by root. I would transfer the files to a dummy folder ('My Backups', 'Bin', 'Files', etc.) and than either use 'sudo' while connected to your *old* box via SSH, or you could load Nautilus (your file browser) with root privileges.

**2.** Now on your *old* computer all you need to do is:

Make sure you have your sources.list file edited:

```
gksu gedit /etc/apt/sources.list
```

Search/Replace (Ctrl + H)

Replace your current version with the new one (In my case, replace all 'feisty' words with 'gutsy'.

Save and exit.

Now run these commands:

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

It will now have all the necessary packages already in cache (memory) on your *old* computer!  It doesn't need to download anything, it just merely needs to recognize the files are there, and install them.

---

