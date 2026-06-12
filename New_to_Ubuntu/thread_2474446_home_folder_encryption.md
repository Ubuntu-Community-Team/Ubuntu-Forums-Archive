---
title: "home folder encryption"
date: 2022-04-29
forum: New to Ubuntu
---

### Post by freeman64 on 2022-04-29
I just want to get my home folder encrypted like I used to.  My previous method is install ubuntu 17.10 and encrypt my home folder. Update to the latest version and I'm good.  How do I upgrade from 17.10 right now from DVD or network?

---

### Post by TheFu on 2022-04-29
17.10 support ended in June 2018.  There haven't been any updates, fixes, security patches since that time.  At this point, there isn't a migration path anywhere, at least not a clean migrations without major hassles.

Also, encrypting just a home directory has been deprecated for years for a number of reasons.  The preferred solution is whole-disk encryption using LUKS, which is a check-box during a fresh install.

Today, I'd suggest backing up your data from the system, then using a 22.04 LTS to perform a fresh install.  Be certain to _**read the Release Notes**_ for issues with some specific hardware. [https://discourse.ubuntu.com/t/jammy-jellyfish-release-notes/24668](https://discourse.ubuntu.com/t/jammy-jellyfish-release-notes/24668) Those notes have upgrade steps for 21.10 or 20.04, FYI, but that upgrade path will fail on your system. The result won't be good.  Nvidia GPU support is both better and worse.  The release notes explain.

For people like you and me, we need to avoid non-LTS releases and still only with LTS releases.  22.04 is an LTS. The standard Ubuntu Desktop for 22.04 has 5 yrs of support.  Before that 5 yrs is up, we need to migrated to the next LTS.  LTS releases are every 2 yrs, in April.  24.04 will be the next one, followed by 26.04.  So, if you do a fresh 22.04 install now, you have 2 LTS opportunities to stay patched.

Please don't use unsupported and unpatched computers. It isn't bad just for you, but for everyone else on any network that the system is connected.

---

### Post by brucew on 2022-05-02
It is possible to encrypt only the /home folder, although the method still requires a full wipe and reload of the disc, and therefore a full backup of the home folder for all users.  Or two if you&#8217;re the belt-and-suspenders type.  This is followed by a manual partitioning when installing the new Ubuntu version.

Bear in mind though that encrypting only /home still leaves everything else vulnerable to mischief and snooping.  Miscreants can still slip in compromised OS files and whatnot, and you can learn a lot from logs&#8230;

It is simpler to encrypt the entire drive and lump all one&#8217;s eggs in a single basket as the previous poster suggested.  If you still want to encrypt only /home, or you want separate encryption choices for your system and home files (as I do), proceed as follows.  Usual warnings about losing passwords applies&#8230; 

If you&#8217;re ready to permanently trash everything on your disc (meaning your data are fully backed up, maybe twice), we can begin by running the Ubuntu installer, choosing any options you see fit up until it asks about disc partitioning.

Manually partition the disc.  On my laptop I use three partitions:

1) EFI (required for booting):  512 MB, formatted as Fat32, I label it EFI, and check the box for boot.

2) Linux system files:  65536 MB, formatted as Ext4, optionally check Encrypt and supply a password, mounted as / and labeled Linux.

3) Home:  Entire remainder of drive, formatted as Ext4, Encrypt checked, password supplied, mounted as /home, and labeled Residence.

In most cases, there will be a small amount of unallocated space remaining.

Proceed from there as you wish.  

If you&#8217;ve chosen to also encrypt /, during the boot process, in a text mode screen you&#8217;ll be prompted for the encryption password to the / partition.  Shortly after, you&#8217;ll be presented with the standard login screen.  (Unless, of course, if during install you set the choice for automatic login.)

If you&#8217;ve elected to leave the system partition unencrypted, You&#8217;ll be presented with a graphical request for the encryption password to /home, before moving on to the standard login screen.  (Unless as above, etc.)

Note that the EFI partition has a lot of leftover space, but it can only be made as small as 320 MB.  I chose 512 just because.  My generous 64 GB root partition is only 20% full.  If your data partition needs a little more elbow room, you might want to allocate only 32,768 MB (32 GB) to the system partition.

Hope this helps.

---

