---
title: "stubborn residual configs"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by Arand on 2008-05-17
Hi

I'm having trouble with a package, namely [linux-ubuntu-modules-2.6.24-12-generic] and its residual config.

in the residual config section in Synaptic I have two posts of this same package. An whe I try to purge it it gives me this:
> (Reading database ... 110711 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-12-generic ...
Purging configuration files for linux-ubuntu-modules-2.6.24-12-generic ...
FATAL: Could not open '/boot/System.map-2.6.24-12-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-12-generic
Cannot find /lib/modules/2.6.24-12-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-12-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-12-generic (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-12-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

When I try purging this via apt-get it just says that it's not installed.

Now, how do I get rid of this oddity?


- Arand

---

### Post by nowshining on 2008-05-17
that's easy to remove once u figure it out :)

lolz I mean I had the same prob. Howerver a bit of searching helped me out.

in terminal

sudo rm /var/lib/dpkg/info/

and remove the .post + .list files of the package & or packages ur trying to remove.

Then re-try ur request again. :)

U can use TAB completion to make it easier finding the package .post & .list files.

edit: also remove in /boot/ the ol' kernel info. there. :) if there is a left over - and be careful to remove that ol' kernels configs, etc.. in /boot/ and not ur working kernels..

---

### Post by Arand on 2008-05-18
I had two files [linux-ubuntu-modules-2.6.24-12-generic.postrm] and [linux-ubuntu-modules-2.6.24-12-generic.list] in [/var/lib/dpkg/info]. I have now simply appended [.bak] to these files.

In [/boot] I have no [*-12*] files.

I have restarted, but synaptic still comes up with the erroneous packages.

- Arand

---

### Post by noynac on 2008-05-18
> **Arand said:**
> ...I'm having trouble with a package, namely [linux-ubuntu-modules-2.6.24-12-generic] and its residual config....

I had a somewhat similar problem and the solution was to create an empty directory as follows:

/lib/modules/2.6.24-12-generic

After creating this empty directory, try synaptic again.

The error message you are receiving is somewhat different, so this may be a bit of a long shot. Still, it only involves creating an empty directory and is worth a try.

---

### Post by Arand on 2008-05-18
> **noynac said:**
> I had a somewhat similar problem and the solution was to create an empty directory as follows:

/lib/modules/2.6.24-12-generic

That worked like a charm!

Thank you!

- Arand

---

