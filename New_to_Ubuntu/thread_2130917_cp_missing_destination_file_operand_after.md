---
title: "cp: missing destination file operand after"
date: 2013-03-30
forum: New to Ubuntu
---

### Post by ckboii89 on 2013-03-30
Hi there! I'm trying to install the Java JDK and im following a youtube tutorial on how to do it.

following the video, the guy puts in the command :"cp /home/giovanni/Downloads/jdk-7u17-linux-x64.tar.gz"

when i try to do it, it says its missing a destination file operand after `/home/giovanni/Downloads/jdk-7u17-linux-x64.tar.gz'

and if i try to close the gap between cp and /home, it gives me no such file or directory

Help please???

Thanks!

---

### Post by deadflowr on 2013-03-30
cp stands for copy.
So it needs a place "destination" of where/what-the-filename-to-be-called will be.

```
cp original-file newly-copied-file
```

---

### Post by Impavidus on 2013-03-31
Is it not easier to install from the repositories? I think **openjdk-7-jdk** would provide you with what you need, unless you need specifally your version. Although I admit I don't really know anything about jdk.

Edit: also see this thread: [http://ubuntuforums.org/showthread.php?t=2131017&p=12582083](http://ubuntuforums.org/showthread.php?t=2131017&p=12582083)

---

### Post by eyuel on 2013-03-31
Can you provide a link to the youtube video?

Are you sure he didn't put "[COLOR=#000000]cp /home/giovanni/Downloads/jdk-7u17-linux-x64.tar.gz .[/COLOR]" (with the dot at the end)?

The format of the cp command is "*cp path_to_original_file path_to_new_file"*. In this case, the dot is the path to the new file. (Actually, in this case, it's the path to the directory you want to put the new file in, but that's not important right now.)

---

### Post by schragge on 2013-03-31
> **ckboii89 said:**
> following the video, the guy puts in the command :"cp /home/[COLOR=#ff0000]giovanni[/COLOR]/Downloads/jdk-7u17-linux-x64.tar.gz"First of all, the [COLOR="#FF0000"]red[/COLOR] part is the user name of the guy who put up the video. On your system, this should be changed to something like:
```
cp ~/Downloads/jdk-7u17-linux-x64.tar.gz .
```

---

