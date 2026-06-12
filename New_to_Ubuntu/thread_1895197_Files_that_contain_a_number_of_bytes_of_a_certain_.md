---
title: "Files that contain a number of bytes of a certain value"
date: 2011-12-14
forum: New to Ubuntu
---

### Post by casteurr on 2011-12-14
Hello!

Do you know how can I create a file that contains 12 bytes of 0, 8 bytes of 7, 14 bytes of random values and 22 bytes that have the value 25?

I thought of creating a file zero.txt with this command
dd if=/dev/zero of=/home/user/zero.txt count=12 bs=1
a file called random.txt wit
dd if=/dev/random of=/home/user/random.txt count=14 bs=1
and two files called 25.txt and 7.txt and concatenate them, but I can't figure out to create these two files.

Thank you!

---

### Post by perperNorbi on 2011-12-14
You can use ```
echo -ne '\0007' > 7.txt 
``` See ```
man echo
``` for details.

---

### Post by casteurr on 2011-12-14
Thank you sp much. It works! :)

---

