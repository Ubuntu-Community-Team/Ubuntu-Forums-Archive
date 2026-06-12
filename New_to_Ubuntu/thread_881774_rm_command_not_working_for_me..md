---
title: "rm command not working for me."
date: 2008-08-06
forum: New to Ubuntu
---

### Post by Jonas thomas on 2008-08-06
I ran a java uninstaller to remove opencascade but it didn't get every thing..  So I'm going in a blowing away whats left but for some reason there are some things that just wont go....

For example:
```
jonas@Ubuntu4:/opt/OpenCASCADE6.2.0/samples/tutorial/src$ ls -a
.  ..
jonas@Ubuntu4:/opt/OpenCASCADE6.2.0/samples/tutorial/src$ cd ..
jonas@Ubuntu4:/opt/OpenCASCADE6.2.0/samples/tutorial$ ls
src
jonas@Ubuntu4:/opt/OpenCASCADE6.2.0/samples/tutorial$ rm src
rm: cannot remove `src': Permission denied
jonas@Ubuntu4:/opt/OpenCASCADE6.2.0/samples/tutorial$ sudo rm src
rm: cannot remove `src': Is a directory
jonas@Ubuntu4:/opt/OpenCASCADE6.2.0/samples/tutorial$ ls -l
total 4
drwxrwxrwx 2 root root 4096 2008-08-06 07:22 src
jonas@Ubuntu4:/opt/OpenCASCADE6.2.0/samples/tutorial$ 

```
Here's what got me confused. I get and error message saying that rm can't remove a directory, but the man pages say they can.  I pretty sure that the directory is empty (ls -a) right???  I looked at the permission (ls -l) and it looks like nothing special.  I tried "sudo rm src" and that doesn't work.   Am I missing something very obvious here???

---

### Post by tuxxy on 2008-08-06
Try adding a sudo to the start of the command to give tyou admin privs for the command.

```
sudo rm (file)
```

---

### Post by PmDematagoda on 2008-08-06
You are running rm on a directory, in which case you would need(since it is empty):-
```
sudo rmdir name-of-dir
```
However if the directory in question contains files, then the command would be:-
```
sudo rm -r name-of-dir
```

---

### Post by Jonas thomas on 2008-08-06
I tried that, (see the code box) it didn't work.

---

### Post by hyper_ch on 2008-08-06
for a directory you need to use the -R option

---

### Post by Dr Small on 2008-08-06
> **tuxxy said:**
> Try adding a sudo to the start of the command to give tyou admin privs for the command.

```
sudo rm (file)
```
And if it is a directory, use:
```
sudo rm -R *directory*
```

---

### Post by markjensen on 2008-08-06
Some of those are directories, so you might want to look into a recursive rm, and this is where you are going to need to be careful!

Combining the sudo root powers, with recursive removal will do just that.  Even if you type something in wrong.   It can remove... well... **everything**.

What, exactly, are you trying to remove.   Can you post the rm command you tried?

The **sudo rm -rf /path/to/directory** command will do a wonderful and irreversible job.

---

### Post by t0p on 2008-08-06
The command 'rmdir' is used to delete empty directories. To delete directories that contain files, use 'rm -r'.

---

### Post by tuxxy on 2008-08-06
Be careful when using rm -rf double check you have the correct paths before executing

---

### Post by Jonas thomas on 2008-08-06
Got it.  Thanks all.

---

