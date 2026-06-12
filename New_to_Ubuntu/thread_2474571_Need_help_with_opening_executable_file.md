---
title: "Need help with opening executable file"
date: 2022-05-03
forum: New to Ubuntu
---

### Post by foxpaw474 on 2022-05-03
I'm using no gui ubuntu in termux Android program and I ran into a problem - I have executable named 1, and I can't open it - it says no such file or directory. I tried to use mc file manager to copy path of file. 
cd /
/root/1
Or
. /1
Or 
~/1
That didn't work
I tried creating new folder, moving executable to it and tried to run it
That didn't work
I tried renaming it 
That didn't work
I need some way to open it

---

### Post by ActionParsnip on 2022-05-03
Where is the file located? Please give the absolute path (from "/") and we can advise. I assume you have marked the file as executable using chmod

---

### Post by foxpaw474 on 2022-05-03
Full path (using readlink -f) is /root/1
yes i marked as executable using chmod +x

---

### Post by yancek on 2022-05-03
As pointed out above, you need to either be in the directory in which the file exists or enter the full path to it.  Obviously also needs to be marked executable.  From your post in which you show different attemtps, it seems you don't know where the file is??  I created a file named 1 with a simple echo statement and marked it executable and it ran when run from the directory in which it existed so the suggestions in post 2 should solve this problem.  Also, if it is a bash script, you need: #! /bin/bash on the first line.

---

### Post by ActionParsnip on 2022-05-03
Then run
```

/root/1

```
Assuming "1" is the binary

---

### Post by foxpaw474 on 2022-05-03
Same error

---

### Post by foxpaw474 on 2022-05-03
Mc file manager see file,but cant open it with same error

---

### Post by foxpaw474 on 2022-05-03
It is in the /root directory

---

### Post by yancek on 2022-05-03
If it is in the /root directory, you can't run it as a user but need root privileges, use sudo.  This command works:  sudo /root/./1

Or you can change to the /root directory and run:  ./1

---

### Post by Impavidus on 2022-05-03
I would rarely do anything in the /root directory without first starting a root shell. /root has permissions 700, so ordinary users can't do anything there. In fact, I rarely do anything in the /root directory.

There may be valid reasons to keep this file in /root, but as you posted in New to Ubuntu and appear to have difficulty understanding the way paths work in the terminal, I ask if you're really sure this is the correct approach.

/root is the home directory of the root user. That's not /, also known as the root directory of the filesystem. ~ is the home directory of the user running the shell, so if you're in a root shell, ~ is the same as /root. . is the current directory.

Pay attention to the exact error message. "No such file or directory" (ENOENT) indicates that the some component of the path doesn't exist; in case of a relative path that it doesn't exist relative to your current directory. "Permission denied" (EACCES) means that you have no execute permission on the file or no read or execute permission on some directory in the path. That would be expected if you try to run a file in /root as a normal user.

---

### Post by foxpaw474 on 2022-05-03
I think problem is much deeper 
ldd ./1 says "not a dynamic executable"
File 1 says "1: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 3.2.0, stripped"
Only ./1 doesnt work.

---

### Post by foxpaw474 on 2022-05-04
I also found this
root@localhost:~/bs# readelf -a 1 | grep interpreter
      [Requesting program interpreter: /lib64/ld-linux-x86-64.so.2]
I think i need some library

---

### Post by yancek on 2022-05-04
On my default install of 20.04, I get the same message running:  ldd ./1 says "not a dynamic executable" but both commands I posted in post #9 execute the file correctly.  The file "  /lib64/ld-linux-x86-64.so.2" exists on my system and links to "/lib/x86_64-linux-gnu/ld-2.31.so".  Both files are owned by root and in group root so obviously you would need to run the command with sudo.  The files should exist on a default Ubuntu, at least they are on my 20.04 version so maybe the problem is with Termux or Android.  I'm not familiar with either so...

---

### Post by TheFu on 2022-05-04
> **foxpaw474 said:**
> Same error

Exactly what is the error? Use the 'tee' command to sent it to a file so it can be uploaded here.

The /root/ directory is normally set with 700 permissions, so that only the root account can access any files in there.  If you are trying to access a file and not using sudo or the root username, it won't work.

---

### Post by tboerner on 2022-05-10
Didn't you mention you run it inside android? This is an ARM system and cannot run x86 binaries directly, no matter if 32- or 64-bit. You would need a sort of emulation or translation layer. It seems qemu is capable of this. Dr. Google is your friend (although I prefer duckduckgo.com ;-)

---

