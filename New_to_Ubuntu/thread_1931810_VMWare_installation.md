---
title: "VMWare installation"
date: 2012-02-26
forum: New to Ubuntu
---

### Post by Ketman on 2012-02-26
I've got as far as downloading the file, and putting it in /home/ketman/dos (which I created for DosBox). I've tried to follow these installation instructions.

[COLOR=Red]1. Log on to your Linux host with the user name you plan to use when you run VMware Player.

2. In the terminal window, become root user to perform the initial installation steps.
su or sudo

The command you use depends on your Linux distribution and configuration.

3. If you are installing from a downloaded file, mount the VMware Player CD-ROM.
VMware-Player-e.x.p-<xxxxxxxx>.i386.bundle
VMware-Player-e.x.p-<xxxxxxxx>.x86_64.bundle

VMware-Player-<version>-<xxxxx>.<architecture>.bundle is the installation file. In the filename, <xxxx-
xxxx> is a series of numbers representing the version and build numbers.
[/COLOR]
How you're supposed to carry out step 1 is a mystery to me.

I've done step 2.

Step 3. If I've downloaded it, I obviously haven't got a CD-ROM. Am I supposed to create one?

But I went on to try the mount operation. I get this:

ketman@ketman-desktop:~/dos$ mount VMware-Player-3.1.5-491717.i386.bundlemount: can't find VMware-Player-3.1.5-491717.i386.bundle in /etc/fstab or /etc/mtab
ketman@ketman-desktop:~/dos$

Can anyone help?

---

### Post by baumanno on 2012-02-26
What they mean in 1. is probably "Log on as user who wishes to install VMWare" (that is, 'Dad' wants VMWare, but 'Mom', 'Charlie' and 'Claire' don't)

Have you tried just running

```

$ chmod +x VMware-Player-<version>-<xxxxx>.<architecture>.bundle
$ sh VMware-Player-<version>-<xxxxx>.<architecture>.bundle

```

yet (step 4. of the User Guide)?

Cheers

---

### Post by Ketman on 2012-02-26
^I should have done that, shouldn't I? But with the error messages from the previous command, I didn't think it was worth proceeding. But I followed your suggestion, and it worked. VMWare is installed and running. Live and learn. Thanks.

---

