---
title: "Can't get reposorities to update (Heron)"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by porchkracker on 2008-08-29
I got the reload screen and it went through the download and install, but when I go and look there is not any new software. Tried 4 times Can anybody help??

---

### Post by Seisen on 2008-08-29
Do you get any errors when you do that or does it say you system is up to date?

---

### Post by porchkracker on 2008-08-31
> **Seisen said:**
> Do you get any errors when you do that or does it say you system is up to date?

My system is up to date, and I do not get any errors, that is what's kind of funny. This system runs better than any windows I have ever had!!. Thanks for your reply

---

### Post by cizco962247 on 2008-09-18
When I run update manager in Ubuntu 8.0 the last couple days it goes to download 17 of 43 files and then hangs and when I close the window out it gives me an error that it could not download all repository indexes
"The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct."
what am i doing wrong?
:(

---

### Post by Sef on 2008-09-19
moved to absolute beginners.

---

### Post by simontaylor on 2008-09-19
a related problem: constant error shown on start up - when I go to update I get

> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/hardy-security/Release](http://nz.archive.ubuntu.com/ubuntu/dists/hardy-security/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

any ideas?

simon

---

### Post by frankleeee on 2008-09-19
Have you made sure that in system-administration-software sources that the CD is ticked off. Also if that is off you might try a different server.

---

### Post by simontaylor on 2008-09-19
looks like my problem is in software sources - as stated - however to do with New Zealand being marked as my Ubuntu software source rather than Main. 

Having changed the local, New Zealand source to Main, I am waiting for updates to check through the files. It's currently stuck at 24.

But I am curious to know what you mean by CD being tick off, frankleeee?

thanks,

simon

---

### Post by frankleeee on 2008-09-19
> **simontaylor said:**
> looks like my problem is in software sources - as stated - however to do with New Zealand being marked as my Ubuntu software source rather than Main. 

Having changed the local, New Zealand source to Main, I am waiting for updates to check through the files. It's currently stuck at 24.

But I am curious to know what you mean by CD being tick off, frankleeee?

thanks,

simon

Right under the server choice is a box that if you have installed with a CD can be turned on or off you want it off to have the computer call the servers.

---

### Post by Orange_and_Green on 2008-09-19
Maybe I can explain as frankleeee seems to be offline right now.

When you open System->Administration->Software Sources, there are 5 checkboxes, then a listbox labeled "download from", and at the bottom there is another checkbox within a field marked Installable from CD-ROM/DVD. (I'm obviously talkeing about the first tab called "Ubuntu software")

If that option is checked, when you install any new packages, the package manager will ask you for the Installation CD/DVD if the pacakges can be found on it. If it's unchecked, then the packages will be downloaded frm the server instead. If you want to see the difference yourself, try installing g++ with the checkbox checked first and unchecked then.

Did you manage to update the package lists BTW?
Good luck:KS

---

### Post by frankleeee on 2008-09-19
> **Orange_and_Green said:**
> Maybe I can explain as frankleeee seems to be offline right now.

When you open System->Administration->Software Sources, there are 5 checkboxes, then a listbox labeled "download from", and at the bottom there is another checkbox within a field marked Installable from CD-ROM/DVD. (I'm obviously talkeing about the first tab called "Ubuntu software")

If that option is checked, when you install any new packages, the package manager will ask you for the Installation CD/DVD if the pacakges can be found on it. If it's unchecked, then the packages will be downloaded frm the server instead. If you want to see the difference yourself, try installing g++ with the checkbox checked first and unchecked then.

Did you manage to update the package lists BTW?

Good luck:KS

Way better explanation.:)

---

### Post by Orange_and_Green on 2008-09-19
:KSThanks...

Excuse me for jumping in, I thought you had gone offline...sorry:popcorn:

---

### Post by simontaylor on 2008-09-19
Hi Orange_and_Green,

what I have below the 5 checkboxes and the download from ... is a larger box with > To install from a CD-ROM or DVD, insert the medium into the drive.
and interestingly I don't seem to be able to mess with what's in that box.

does that count as checked?

The package lists after some to-ing and fro-ing seem to have successfully downloaded.

No warning signs are apparent.

Thanks,
simon

---

