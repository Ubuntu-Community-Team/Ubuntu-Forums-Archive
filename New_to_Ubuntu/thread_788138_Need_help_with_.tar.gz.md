---
title: "Need help with .tar.gz"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by iwannalearn on 2008-05-09
My first go trying to install .tar.gz (Story so far)

Opened a terminal and did>   sudo apt-get install build-essential

then

tar -xzvf jTDM_1.0.9.tar.gz

and got the following return

xxxxxx@xxxxxx-laptop:~$ tar -xzvf jTDM_1.0.9.tar.gz
tar: jTDM_1.0.9.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
xxxxx@xxxxx-laptop:~$ 

What am i doing wrong please?

Cheers

---

### Post by y-lee on 2008-05-09
Where did you download the file? You have to be in the same directory as the file before your run tar.

---

### Post by ZabiGG on 2008-05-09
Hi ;)

Had the same problem last week. Here's a great link that helped me out.

[http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually](http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually)

Hope this helps...

---

### Post by tamoneya on 2008-05-09
what is the result of ```
ls -la
```Also are you sure that you are in the right directory.  I think firefox prefers to download things to the desktop which would be ~/Desktop

---

### Post by kellemes on 2008-05-09
> **iwannalearn said:**
> My first go trying to install .tar.gz (Story so far)

Opened a terminal and did>   sudo apt-get install build-essential

then

tar -xzvf jTDM_1.0.9.tar.gz

and got the following return

xxxxxx@xxxxxx-laptop:~$ tar -xzvf jTDM_1.0.9.tar.gz
tar: jTDM_1.0.9.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
xxxxx@xxxxx-laptop:~$ 

What am i doing wrong please?

Cheers

The filename isn't correct.

First do a "ls" to make sure it's there..
Not sure if you know, could a helpful tip.. if the filename is myfile.tar.gz you start typing..
"tar -xzvf my" and hit the <TAB>-key.
The filename will be filled in for you.. unless there are more file starting with "my", in that case hitting <TAB> 2 times will give you a list of options..

---

### Post by iwannalearn on 2008-05-09
Guys you are all the best and this forum like ubuntu is the best:lolflag:

Seems i was in the wrong directory!

Many thanks for quick replies and help:)

---

