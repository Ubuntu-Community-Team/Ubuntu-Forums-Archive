---
title: "help with iwl3945 driver and compact wirless"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by craiggale on 2008-10-17
im trying to install the compact-wireless-old patch to enable injection but keep running into the following problem

craig@craig-laptop:~$ tar -xzvf iwlwifi*
tar: iwlwifi-5000-ucode-5.4.A.11: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now

gzip: stdin: unexpected end of file
tar: Child returned status 2
tar: iwlwifi-5000-ucode-5.4.A.11.tar.gz: Not found in archive
tar: iwlwifi-5000-ucode-5.4.A.11.tar.gz.1: Not found in archive
tar: Error exit delayed from previous errors
craig@craig-laptop:~$ sudo cp iwlwifi-5000-ucode-5.4.A.11/iwlwifi-5000-1.ucode /lib/firmware
craig@craig-laptop:~$ bunzip2 compat-wireless-old.bz2
bunzip2: Can't open input file compat-wireless-old.bz2: No such file or directory.
.

my kernel version is 2.6.24-21-generic. and i have installed build essential


the problem occurred whilst running the following code found on this forum


wget [http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-5.4.A.11.tar.gz](http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-5.4.A.11.tar.gz)
wget [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2)
tar -xzvf iwlwifi*
sudo cp iwlwifi-5000-ucode-5.4.A.11/iwlwifi-5000-1.ucode /lib/firmware
bunzip2 compat-wireless-old.bz2
tar xf compat-wireless-old.tar
cd compat-wireless-2.6-old/
make
sudo make install
sudo make unload
sudo make load

any help on how to install compact wireless would be appretaited

---

### Post by hermes0710 on 2008-10-17
Hi,
  I managed to run the first command with no problems. So you might have to download the file again because it seems to be broken.
For the second command i get the same output but when i located it through nautilus i was able to extract it with right click -> extract here. You can do this and then move the extracted files to the directory you are told to.

---

### Post by craiggale on 2008-10-17
hi,

thanks for the help but im a very recent windows convert and im finding .tar files quite confusing. 

could you please tell me which exact files i need to extract and where i need to put them.

---

### Post by hermes0710 on 2008-10-17
I suggest you download the files you need in a folder and then locate this folder with nautilus. Right-clicking these files and selecting "extract here" will do what the command in terminal would.

> .tar files quite confusing
It's not that hard. Just compression files.

---

### Post by Nepherte on 2008-10-18
Use this command
```
tar xvfz iwlwifi-5000-ucode-5.4.A.11.tar.gz
```
instead of
```
tar -xzvf iwlwifi*
```

---

### Post by craiggale on 2008-10-18
im still getting an error when running this code 

bunzip2 compat-wireless-old.bz2

error

bunzip2: Can't open input file compat-wireless-old.bz2: No such file or directory.

---

### Post by Nepherte on 2008-10-18
Replace these two:
```
bunzip2 compat-wireless-old.bz2
tar xf compat-wireless-old.tar
```
with 
```
tar xvfj compat-wireless-old.tar.bz2
```

---

### Post by craiggale on 2008-10-18
craig@craig-laptop:~/Desktop$ tar xvfj compat-wireless-old.tar.bz2
tar: compat-wireless-old.tar.bz2: Cannot open: No such file or directory

---

### Post by Nepherte on 2008-10-19
The error means the file location doesn't exist. Did you download the file? Is the path to the file correct?

---

### Post by runngun on 2008-10-29
try this:

bunzip2 compat-wireless-old.tar.bz2

it worked for me just needed the tar between old and bz2

---

### Post by macogw on 2008-10-29
> **craiggale said:**
> hi,

thanks for the help but im a very recent windows convert and im finding .tar files quite confusing. 

could you please tell me which exact files i need to extract and where i need to put them.

.tar = archive
when you add compression (so, .tar.gz or .tar.bz2 or .tgz), it's pretty much the same as .zip

---

