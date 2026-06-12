---
title: "Trouble with installing Ubuntu 17.04 from DVD-RW"
date: 2017-08-04
forum: New to Ubuntu
---

### Post by vanquishvictor1998 on 2017-08-04
Hi,

we have made an image of Ubuntu verison 17.04 on a DVD-RW and its seems to be in order. But when we boot our Laptop and force it to load from DVD it constantly ends up loading PClinux no matter what we try. :confused:

The laptop is a Gateway model MX6933B. Any help would be great

Victor A.S

---

### Post by oldos2er on 2017-08-04
You changed your BIOS to boot from DVD first?

---

### Post by vanquishvictor1998 on 2017-08-04
Yes we did that. But it doesn't seem to save hence we forced it to boot from CD/DVD

---

### Post by oldos2er on 2017-08-04
Did you [verify the ISO]("https://help.ubuntu.com/community/HowToMD5SUM") before burning it to disc? If possible have you checked the disc in a different computer?

---

### Post by BenginM on 2017-08-04
At what speed did you burn the iso to DVD!  2x or 4x maximum is recommended not higher .. also verify and check the hashes like oldos2er point you to before the burn process.

---

### Post by vanquishvictor1998 on 2017-08-04
Sorry, we cannot verify the file

The commands given do not seem to work with the ISO file in the download directory where it is stored.

---

### Post by BenginM on 2017-08-04
What command! in the Downloads directory where the  iso file is stored then and the command is $ md5sum ubuntu.iso , or $ md5sum DRAG-DROP-THE-ISO-FILE-HERE , then hit enter. you should see the hashes , compair it with the MD5SUM hashes on the site for the iso.file you downloaded.

---

### Post by vanquishvictor1998 on 2017-08-05
I believe I have found the problem its my laptop's DVD/CD drive. I placed the disc in my main computer and it worked but my laptop doesn't to know what its doing even when I force it to boot from DVD/CD. I'll have to try using a USB.

---

### Post by vanquishvictor1998 on 2017-08-06
Problem is solved. what I burnt onto the the DVD-RW I placed on a USB and now I have ubuntu. Thanks for all the help and support

---

### Post by RobGoss on 2017-08-06
You can mark this thread as solved by using the** Thread tool** tab at the top of this post, Thanks for sharing your solution

---

