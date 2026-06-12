---
title: "Questions about Ubuntu privacy"
date: 2018-08-21
forum: New to Ubuntu
---

### Post by ja00 on 2018-08-21
Hello - I am a beginner and I will be using the system on a desktop to store clients' personal data.

1. By default, does Ubuntu store any files or other data to "the cloud"?  (Compare with Google, which stores pictures and other personal info on their servers.)  

2. Any way to confirm this is not happening or to disable this function? 

3. Does Ubuntu store files or other data in multiple locations locally? (Compare with Apple Time Machine.) 

4. Can files be securely deleted?  (Compare with Apple secure erase in finder.)

5. Any other suggestions to make sure data does not go onto the Internet? 

Thanks for helping me understand this operating system.

---

### Post by QIII on 2018-08-21
> 1. By default, does Ubuntu store any files or other data to "the cloud"? (Compare with Google, which stores pictures and other personal info on their servers.) 

Not by default.

> 2. Any way to confirm this is not happening or to disable this function?

It's not.

> 3. Does Ubuntu store files or other data in multiple locations locally? (Compare with Apple Time Machine.) 

This is a bit ambiguous, but not by default.  You can install packages to do that, but don't if you don't want to.

> 4. Can files be securely deleted? (Compare with Apple secure erase in finder.)

Yes.  You can use the shred command.  But be sure you know what you are doing first and be very careful.

> 5. Any other suggestions to make sure data does not go onto the Internet?

Unplug it from the router.  Seriously.  Anything can be hacked.  But within a reasonable calculation of risk/usability, that's not practical.  But you can do a lot to harden your machine.  As far as what *you* do, just don't install or use anything that would expose data to the web.

Linux is no different from Windows in this respect.  You have to take the time to secure your machine.

---

### Post by deadflowr on 2018-08-22
For secure deletion you can install a package called nautilus-wipe, which will add a wipe option to dropdown list when you right click on a file.
You need to restart the file manager in order for it to appear after the initial install (log outs and reboots will also work)

---

### Post by ubantunovice2 on 2018-08-22
I had similar concerns. If you search 'Ubuntu privacy' you'll find many ways to make Ubuntu more secure by changing some settings in settings/privacy.

[https://fixubuntu.com](https://fixubuntu.com)
[https://www.linuxbabe.com/ubuntu/ubuntu-stubby-dns-over-tls](https://www.linuxbabe.com/ubuntu/ubuntu-stubby-dns-over-tls),
Etc.

---

