---
title: "remastering cd, generating Release.gpg"
date: 2005-10-14
forum: Packaging and Compiling Programs
---

### Post by moptop on 2005-10-14
I'm not sure this is precisely the right forum, but seems closest of all the categories.  What follows is drawn from a post to ubuntu-users, which hasn't gotten any response after a couple of days.
---------  

I could really use some help with remastering ubuntu cd's -- I thought
I had it licked, but I was wrong.  

I've successfully made a working preseed file (yay!)

now I want to subtract some packages, and add others to the disk.  

To do this I need to generate Packages and Releasee files in the
disk image, and sign them with gpg; I also need to create a new
ubuntu-keyring package, because my public key needs to be in that
package in order for the disk to be recognized.  So I did this:  

made a new ubuntu-keyring thusly:

apt-get source ubuntu-keyring
cd ubuntu-keyring/keyrings
gpg --import < ubuntu-archive-keyring.gpg
gpg --export > ubuntu-archive-keyring.gpg

it generated ENORMOUS ubuntu-keyring
packages (13 megs of keyring instead of 294 k) but I had some space on
the cd, so that was ok.

then I did all the necessary changes to the disk (add packages to
pool, mostly) after which I  have the following in a script

# generate Packages, release, releases.gz

sudo rm $BUILD/dists/breezy/Release.gpg $BUILD/dists/breezy/Release $BUILD/dists/breezy/main/binary-i386/Packages $BUILD/dists/breezy/main/binary-i386/Packages.gz 
apt-ftparchive packages  $BUILD/pool/restricted/ > /tmp/Packages
apt-ftparchive release $BUILD/dists/breezy > /tmp/Release
sudo mv /tmp/Packages $BUILD/dists/breezy/main/binary-i386/
sudo mv /tmp/Release $BUILD/dists/breezy/
gpg --output /tmp/Release.gpg -ba $BUILD/dists/breezy/Release
sudo mv /tmp/Release.gpg $BUILD/dists/breezy/

(the $ are variables, set correctly as it turns out)

well, that looked fine to me -- 

but as it turns out I DIDN'T do it right and I get a message to the
effect of:

Error Reading Release File
This cdrom does not seem to contain a valid 'Release' file... etc.  
I guess there are 2 possibilities here:
1 -- apt-ftparchive is somehow generating a defective Release file
(bummer)
2 -- I'm not signing it right, or I'm not exporting the right keys, or
something.

In any case it's very frustrating!  If anyone can help out at all I'd
be grateful (sooner better than later, I wanted to have these cd's
tomorrow but that is looking like a lost cause...).  I fully intend to
put this up on the wiki as soon as I have it figured out...

thanks,

matt

---

### Post by c_tophe on 2005-10-28
I have the same error in making a multiboot DVD with Ubuntu 5.10 & Windows XP. Anyone has an idea ?

Thanks
Tophe

---

### Post by Red_Phoenix on 2006-01-09
[QUOTE=moptop]
apt-ftparchive packages  $BUILD/pool/restricted/ > /tmp/Packages
apt-ftparchive release $BUILD/dists/breezy > /tmp/Release
[/QUOTE]

Try:
cd $BUILD
apt-ftparchive packages  pool/restricted/ > /tmp/Packages
apt-ftparchive -c <<path to custom apt.conf>> release dists/breezy > /tmp/Release

Otherwise, the Packages file will contain absolute paths, rather than relative ones.

For the apt.conf file, see the following post:
[http://www.ubuntuforums.org/showthread.php?t=114580&highlight=apt-ftparchive](http://www.ubuntuforums.org/showthread.php?t=114580&highlight=apt-ftparchive)

.. though I'm still seeing a problem installing intramfs-tools when the release key is modified (see post above) - anyone have any solutions for that?

Regards,

Leigh.

---

