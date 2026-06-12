---
title: "Permission denied in /usr/src"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by nksjolinder on 2011-09-20
Hey guys,

I just downloaded drivers for a printer and they came in the tar.gz file type. I tried extracting the file from the archive manager into the /usr/src file but it says i do not have permission to extract it into that folder. I assume that is the folder where i should be storing my tar.gz files? please help

Nick

---

### Post by TeoBigusGeekus on 2011-09-20
Extract the archive somewhere in your home folder.
Navigate into the extracted folder and see if there is a text files with directions about how to install the drivers.
If not, issue these commands (while in a terminal in the extracted folder):
```
./configure
make
sudo make install
```

---

### Post by dniMretsaM on 2011-09-20
Run this in terminal:
```
sudo chown username:username /usr/src
```That will make you the owner of the file and allow you to modify it's contents without admin privileges. And no, there is no folder where you have to store source code. Any place will do. I store mine in /usr/local/src/. It really doesn't matter. Not that it's always a good practice to have on folder where you keep all the code, just for simplicity's sake.

EDIT: As noted by Teo, you can extract to you home directory also. Like I said, it doesn't matter as long as you know where it is.

---

### Post by nksjolinder on 2011-09-20
thanks!  went ahead and put it in the /usr/local/src folder which worked perfectly

---

### Post by dniMretsaM on 2011-09-20
> **nksjolinder said:**
> thanks!  went ahead and put it in the /usr/local/src folder which worked perfectly

Awesome! Mark as solved please.

---

### Post by Paddy Landau on 2011-09-20
> **dniMretsaM said:**
> Run this in terminal:
```
sudo chown username:username /usr/src
```
Nooooooo!

/usr/src is a system directory. You should not change the owner from root for security reasons.

Please undo it with```
sudo chown root:root /usr/src
```If you need to copy files to a system directory, use the copy command:```
sudo cp [files to copy] /usr/src/[folder]
```However, why have you not tried the [answer in post #2]("http://ubuntuforums.org/showthread.php?p=11269784#post11269784")?

---

### Post by dniMretsaM on 2011-09-20
> **Paddy Landau said:**
> Nooooooo!

/usr/src is a system directory. You should not change the owner from root for security reasons.

Please undo it with```
sudo chown root:root /usr/src
```If you need to copy files to a system directory, use the copy command:```
sudo cp [files to copy] /usr/src/[folder]
```However, why have you not tried the [answer in post #2]("http://ubuntuforums.org/showthread.php?p=11269784#post11269784")?

Ok, now you've confused me. Why shouldn't he change the owner of usr/src/? What does that have to do with security?

Anyway, he said he put it in /usr/local/src/.

---

### Post by Paddy Landau on 2011-09-20
> **dniMretsaM said:**
> Ok, now you've confused me. Why shouldn't he change the owner of usr/src/? What does that have to do with security?

Anyway, he said he put it in /usr/local/src/.
Linux's security depends on a certain model. Remember that, unlike Windows, Linux is designed from the ground up to be a multi-user system; more than one person can sign in at the same time to a Linux computer (albeit that it is unusual to use this feature apart from "switch user").

System files belong to root, and should stay that way.

One side effect is that it prevents malware from changing system files. Should malware get onto your system, it is because you downloaded and ran it; the worst it can do (unless you supply your password) is damage your files. It cannot mess up the system files or programs, and cannot damage the files of any other user on the computer.

In fact, if you run as a non-administrator (which is the recommended method), even supplying your password cannot let the malware damage anything other than your own files.

I'm sure others could add to what I say, but telling someone to change the owner of a system directory goes against the Linux security model and probably against the code of conduct on the Ubuntu Forums.

---

### Post by TeoBigusGeekus on 2011-09-20
> **dniMretsaM said:**
> Ok, now you've confused me. Why shouldn't he change the owner of usr/src/? What does that have to do with security?

Anyway, he said he put it in /usr/local/src/.

The /usr/src folder contains the linux headers and source code of the kernel.
Since the system compiles the kernel from there, it IS a security breach to change the ownership to anything other than root.

---

### Post by dniMretsaM on 2011-09-20
> **TeoBigusGeekus said:**
> The /usr/src folder contains the linux headers and source code of the kernel.
Since the system compiles the kernel from there, it IS a security breach to change the ownership to anything other than root.

Oh I didn't know that. Thanks for the info.

---

### Post by TeoBigusGeekus on 2011-09-20
> **dniMretsaM said:**
> Oh I didn't know that. Thanks for the info.

It's ok; we all make mistakes.
+1 to Paddy's well spoken posts.
See [this]("http://www.pathname.com/fhs/") for more info on linux filesystem hierarchy.

---

### Post by Paddy Landau on 2011-09-20
> **TeoBigusGeekus said:**
> See [this]("http://www.pathname.com/fhs/") for more info on linux filesystem hierarchy.
The file system has been updated slightly since that web page was written. There is a new directory called /run, which will contain all RAM-based folders. E.g. /dev/shm will move to /run/shm.

/run: Ephemeral run-time data.
/var: Persistent run-time data.

[More information on askubuntu]("http://askubuntu.com/questions/57297/why-has-var-run-been-migrated-to-run").

---

### Post by TeoBigusGeekus on 2011-09-20
> **Paddy Landau said:**
> The file system has been updated slightly since that web page was written. There is a new directory called /run, which will contain all RAM-based folders. E.g. /dev/shm will move to /run/shm.

/run: Ephemeral run-time data.
/var: Persistent run-time data.

[More information on askubuntu]("http://askubuntu.com/questions/57297/why-has-var-run-been-migrated-to-run").

Thanks Paddy, appreciated.

---

### Post by dniMretsaM on 2011-09-20
Yeah, I just didn't know /usr/src/ was a system directory, so I didn't know it would be bad. Thanks for clearing it up guys.

---

### Post by nksjolinder on 2011-09-21
Thanks for all the info guys and thanks paddy for the linux wisdom :)

---

