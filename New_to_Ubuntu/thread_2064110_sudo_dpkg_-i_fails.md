---
title: "sudo dpkg -i fails"
date: 2012-09-28
forum: New to Ubuntu
---

### Post by mark allyn on 2012-09-28
Hello everyone,
 
I'm experiencing installation problem.  I've copied some .deb files from a CD to /home/mark.  Usinng sudo dpkg -i fails with an error message 'unrecoverable fatal error, aborting: reading files list for package 'libdebian0debian1': input/output error'.
 
I've never seen this error before, and I've had no problems following this methodology in the past.  I tried rebooting but that didn't solve the problem.
 
What's going on?  How to fix?
 
Cheers,
Mark Allyn

---

### Post by mark allyn on 2012-09-28
Sorry.  The package is 'libparted0debian1', not 'libdebian0debuab1'.
 
Cheers,
Mark

---

### Post by drmrgd on 2012-09-28
Do you have enough space on your hard disk to install that package?  Double check that, and of course double check that the package has not become corrupted somehow.

---

### Post by mark allyn on 2012-09-28
Hi Drmrgd,
 
Thanks for responding.
 
I checked and the package is installed.  How do I determine if it has been corrupted?  Sorry about this novice question.
 
Cheers,
Mark

---

### Post by mark allyn on 2012-09-28
Hi again drmrgd,
 
Anyway, even if I got a fresh download of the various libpart0debian1 files, I'd still have a problem.  I don't have internet connectivity and install everything off a CD.  Maybe all I can do is reload the system from scratch.  Ugh.
 
Cheers,
Mark

---

### Post by drmrgd on 2012-09-28
Hi Mark.  I don't think you'll have to do a fresh install.  I am slightly confused about a couple things, though.  You say that the package is already installed.  But are you saying that you've not been able to install the package still or are missing components?

Also, I see that you've specified the Debian libparted library.  Is this on a Debian system and not an Ubuntu system, and if so, what release?  

Finally, please run:

```
sudo df -Th
```

and post the output.  I've seen input / output errors before due to the root partition being too full, and your error might be a simple case of not enough space to install.  It's not the most likely candidate, but certainly the easiest to check.

Checking the integrity of the package is a little more tricky.  If you could find the hash of the original package (often listed with the packages from the various repositories), you can check the MD5sum of the one you have versus the repositories' MD5sum.  This will help you determine whether or not the package is corrupt.  Since you've downloaded it from the repository on one computer and burned it to a CD, it's very possible that somewhere along the lines something popped up.  If you can't find MD5sum info, I'm not sure of a better way to verify the package's integrity other than just re-downloading it and trying again.  Maybe someone has a suggestion to a better trick?

---

### Post by drmrgd on 2012-09-28
OK, I think I had something confused.  When I originally looked that package up, it seemed that the naming was different between the Ubuntu version and the Debian version.  I never thought to check my own system, which seems to have libparted0debian1 installed (swear the Ubuntu version didn't have the word 'debian' in it!).  Still, it would be helpful to know which version you're running.  I'm running 12.04 on a 64-bit system, and here are the package details I have:

```
Package: libparted0debian1
Versions: 
2.3-8ubuntu5 (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages
                  MD5: 8351c24350acd1cda567a096a68bf6b7
 Description Language: en
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en
                  MD5: 8351c24350acd1cda567a096a68bf6b7


Reverse Depends: 
  udisks,libparted0debian1 2.2-1
  ubiquity,libparted0debian1 2.2-1
  libvirt-bin,libparted0debian1 2.2-1
  libparted0debian1:i386,libparted0debian1 2.3-8ubuntu5
  libparted0debian1:i386,libparted0debian1 2.3-8ubuntu5
  python-parted-dbg,libparted0debian1 2.2-1
  python-parted,libparted0debian1 2.2-1
  librdsserver1,libparted0debian1 2.2-1
  libparted0-i18n,libparted0debian1
  libparted0,libparted0debian1 2.3-8ubuntu5
  kvpm,libparted0debian1 2.2-1
  gnu-fdisk,libparted0debian1 2.2-1
  gnome-format,libparted0debian1 2.2-1
  fatresize,libparted0debian1 2.2-1
  udisks,libparted0debian1 2.2-1
  ubiquity,libparted0debian1 2.2-1
  partitionmanager,libparted0debian1 2.2-1
  parted,libparted0debian1 2.2-1
  libvirt-bin,libparted0debian1 2.2-1
  libparted0debian1-dbg,libparted0debian1 2.3-8ubuntu5
  libparted0-dev,libparted0debian1 2.3-8ubuntu5
  gparted,libparted0debian1 2.2-1
Dependencies: 
2.3-8ubuntu5 - libblkid1 (2 2.17.2) libc6 (2 2.14) libdevmapper1.02.1 (2 2:1.02.36) libuuid1 (2 2.16) multiarch-support (0 (null)) parted (16 (null)) nparted (0 (null)) libparted0-dev (0 (null)) libparted0-i18n (5 2.3-8ubuntu5) libparted1 (3 2.2) libparted1:i386 (3 2.2) libparted2 (3 2.2) libparted2:i386 (3 2.2) parted (3 1.4.13+14pre1) parted:i386 (3 1.4.13+14pre1) dmraid (3 1.0.0.rc16-4.1ubuntu2) dmraid:i386 (3 1.0.0.rc16-4.1ubuntu2) libparted0 (3 2.2-4) libparted0:i386 (3 2.2-4) libparted1 (3 2.2) libparted1:i386 (3 2.2) libparted1.4 (3 1.4.24-2) libparted1.4:i386 (3 1.4.24-2) libparted2 (3 2.2) libparted2:i386 (3 2.2) libparted0debian1:i386 (3 2.3-8ubuntu5) libparted0debian1:i386 (6 2.3-8ubuntu5) 
Provides: 
2.3-8ubuntu5 - libparted 
Reverse Provides:
```

If you have the same package on your CD, you might be able to use the MD5sum I have to cross check.

---

### Post by mark allyn on 2012-09-28
Good afternoon, drmrgd,
 
Thanks very much for your attention to this issue.  Unfortunately, in the interim I went ahead and reinstalled the entire 12.04 CD.  BTW, I am on a 32 bit system here.  
 
Even though I can't do any longer what you proposed as far as the checksum is concerned, for what its worth, this has been a good learning experience for me even though I rear it hasn't benefitted you.
 
One thing that I want to try is in fact to read and print the reverse depends.  This is a very helpful tool, it seems.  I couldn't tell from your code what the command was that caused it.  Would you mind awfully telling me what it was (possibly for the second time).
 
Best regards,
Mark

---

### Post by drmrgd on 2012-09-28
Ahhh..too bad I didn't get a response to you in time.  Sorry about that.  Hope the install went OK!

For the output that I sent, I ran:

```
sudo apt-cache showpkg libparted0debian1
```

That (to me) is the granddaddy of them all as it gives the most information on a package.  A somewhat truncated version if you just want to see if you have the package installed, it's installation status, and the version would be:

```
dpkg -l libparted0debian1 # That's a lower-case L and not the number 1 in the command
```

I'm on a different computer now, but the output of that on this system is:

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                        Version                     Description
+++-===========================-===========================-======================================================================
ii  libparted0debian1           2.3-8ubuntu5                disk partition manipulator - shared library
```

Definitely have a read through all of the documentation on Apt and dpkg if you're so inclined.  Lots of really great tricks and tools that one can perform from the commandline.  You could always do very similar tasks with Synaptic and other package managers.  But, I like to try to use the built in commands to their fullest (if I can!).

---

### Post by mark allyn on 2012-09-28
Good evening, drmrgd,
 
It is too bad!  I felt horrible when I saw your post.  If only....
 
But, the learning for me was very helpful for the future.  I snooped around and found sudo apt-cache rdepends <file> and tried that.  It's OK, but doesn't deliver the detail that your showpkg option does.
 
The re-installation worked without problems, thank you.  But, the whole episode has shown me the importance (since I don't have internet on my 12.04 box) of backing up the current image so as not to have to reinstall a lot of stuff off burned CD's.
 
At the risk of annoying you, might I ask if you have recommendation about backup for the system image?  I've seen some stuff about codezilla but am too green to evaluate it.
 
Regards as always
 
Mark

---

### Post by mark allyn on 2012-09-28
I meant Clonezilla.  Sorry, it's rather late.
 
Mark

---

### Post by drmrgd on 2012-10-01
I've not specifically used Clonezilla myself, and so I can't speak to how good it works.  Many seem to like it quite a lot.  I don't mind doing fresh system installs as it goes quite quickly.  I do backup my /home directory on a routine basis to an external storage drive using the Rsnapshot program (basically a tweaked rsync utility with nice functionality).  This wouldn't be useful for a system image, though.

---

### Post by AndyOpie150 on 2012-10-01
drmrgd: I am a linux newbie, and appreciate your posting of this info as well. I'm a sponge with a few hard edges from age.

---

