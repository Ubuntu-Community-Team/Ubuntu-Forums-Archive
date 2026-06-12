---
title: "Unable to update openssl and install ssh"
date: 2012-12-04
forum: New to Ubuntu
---

### Post by ChM on 2012-12-04
I have a fresh install of Xubuntu 12.04 on a virtualBox machine and unfortunately I can't update openssl. 

The reason given is that the file list for openssl has no new line at the end of the list. I translated it from french so sorry if it is not the exact same error text in english. 

I was using the french repository when I got this error the first time. Then I switched to the canonical repositiry after purging, cleaning and whatever, and the error is still there.

This is a critical package and I was curious if other people where seeing the same problem. 

I had a VM crash after installing and in the middle of the first update. I had to do a 'sudo apt-get purge' to resolve the problems and beeing able to redo a 'sudo apt-get update'. 

The problem shows up when 'sudo pat-get upgrade' starts or when I do a 'sudo apt-get install ssh' which apparently tries to update openssl before. 

I'm quite frustrated because I wanted to give Xubuntu a try to see if it supports remote connection with NoMachine, since NoMachine can't be used with Ubuntu because of the 3D accelerator dependency.

---

### Post by ChM on 2012-12-04
I checked the openssl file and compaired its content with the one of Ubuntu and they are identical. So I erased the VM and completely reinstalled Xubuntu. I then immediatly installed ssh without problem and checked that it worked. Then after that I updated all packages (193) without problem. 
I guess the hypervisor crash corrupted some files in the Xubuntu machine. 
The problem may thus be considered solved.

---

