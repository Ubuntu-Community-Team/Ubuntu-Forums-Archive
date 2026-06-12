---
title: "Can't Execute file"
date: 2014-07-22
forum: New to Ubuntu
---

### Post by jballer0602 on 2014-07-22
Tried to execute a file that I checked for execution in "permissions" 

This is what I get

```

root@jerome-K55N:/home/jerome/Downloads# sudo chmod +x unetbootin-linux-608.bin
chmod: cannot access &#8216;unetbootin-linux-608.bin&#8217;: No such file or directory

```

No such file or directory.
The file (.bin) even when changed to made executed still remains as a bin file and doesn't change to a diamond shape.

Help?

Thanks in advance

---

### Post by grumblebum2 on 2014-07-22
What ubuntu release are you using?
Unetbootin is in the repos on 14.04

or

use a ppa for a more recent version,
[https://launchpad.net/~gezakovacs/+archive/ubuntu/ppa](https://launchpad.net/~gezakovacs/+archive/ubuntu/ppa)

---

### Post by nerdtron on 2014-07-23
> chmod: cannot access &#8216;unetbootin-linux-608.bin&#8217;: No such file or directory

chmod says it can't find the file in the current directory.

To be sure, is the file "unetbootin-linux-608.bin" on you /home/jerome/Downloads diectory?
```
cd /home/jerome/Downloads
ls  -lh
```

Be sure to use the correct filename too.

---

### Post by Impavidus on 2014-07-23
Excellent remark by nerdtron, but I see you're a bit puzzled by root permissions. As in, if it doesn't work, use sudo, which isn't really good advice.

You use a root shell and sudo on top of that, but that is redundant. If you're root already you don't have to use sudo and if you can use sudo you don't have to become root. Furthermore, the file you wish to change permissions of is in jerome's (your, I presume) home directory, in which you don't need root permissions to modify anything.

---

### Post by sudodus on 2014-07-23
If you install Unetbootin from the repositories with the terminal window command

```
sudo apt-get install unetbootin
```

or via Synaptic or Software Center, the executable file will be

```
unetbootin
```

---

