---
title: "How do you get the md5 on an .iso?"
date: 2014-01-22
forum: New to Ubuntu
---

### Post by bc.haynes on 2014-01-22
After downloading an .iso, how do you get its md5 to compare it with the web site's md5?

---

### Post by coldcritter64 on 2014-01-22
In terminal,

```
md5sum </path/to/your/file/yourfilename.iso>
``` eg an iso on the Desktop named image.iso would look like.

```
md5sum ~/Desktop/image.iso
``` press return and copy/paste the output to a text file, on a new line in the text file put the web md5 immediately below it and compare. There are gui apps for this, one is gtkhash, if you wish to check them out. Cheers.

---

### Post by Dave_L on 2014-01-22
You can also create a file containing the md5. Here's an example:

```
ef173f4c6f35e6293e48505a56ccf0fc  archlinux-2014.01.05-dual.iso
```

(I think there are supposed to be two spaces between the md5 and the .iso filename.)

Then you can run md5sum with the -c (or --check) option:

```
$ md5sum -c FILE
archlinux-2014.01.05-dual.iso: OK

```

---

### Post by Buntu Bunny on 2014-01-22
And, for questions or further reading, [HowToMD5Sum]("https://help.ubuntu.com/community/HowToMD5SUM") in the Community Help Wiki.

---

### Post by bc.haynes on 2014-01-27
Thank you** Buntu Bunny** for the HowTo.

---

