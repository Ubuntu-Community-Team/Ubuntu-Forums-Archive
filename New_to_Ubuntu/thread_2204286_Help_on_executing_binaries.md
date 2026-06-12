---
title: "Help on executing binaries"
date: 2014-02-07
forum: New to Ubuntu
---

### Post by cytg on 2014-02-07
Hi, this must be really noobish .. but i dl'ed xubuntu and tried to manually download and execute newest version of firefox (27)

I have it sitting here
root@xx-xx:/home/xx/Downloads/firefox# ls firefox -la
-rwxr-xr-x 1 xx xx 127352 Jan 28 07:18 firefox
root@xx-xx:/home/xx/Downloads/firefox#

Now if I do
./firefox
v.27 starts. If I do
firefox
v.26 starts (the one that shipped with xubuntu)

Okay, i get that, I've got firefox26 on my path somewhere.
Now I exit to my regular user ...
xx@xx-xx:~/Downloads/firefox$ ls firefox -la
-rwxr-xr-x 1 xx xx 127352 Jan 28 07:18 firefox
xx@xx-xx:~/Downloads/firefox$ 

And do the same
./firefox
v.26 spawns, ignoring v.27 in currect dir. And
firefox
spawns v.26 too.

So why is it that I can only run the binary as root ? Permissions "-rwxr-xr-x 1 xx xx " looks fair no?

Thanks!

---

### Post by cytg on 2014-02-08
nothing? Posting the wrong place? Too weird? Too simple? :)

---

### Post by sudodus on 2014-02-08
No, not too simple ... rather too hard to understand and explain. I'm checking some data and guessing what happens behind the curtain.

A big program package like Firefox consists of several layers of program code. What you call with the command firefox and ./firefox is probably 'only' a shell-script, which in turn calls various program parts, which are probably written in different languages. I'm running 12.04.4 LTS, and I checked what I am running.

 ```
which firefox
/usr/bin/firefox

firefox -v
Mozilla Firefox 26.0

ls -l /usr/bin/firefox
lrwxrwxrwx 1 root root 25 dec  6 17:09 /usr/bin/firefox -> ../lib/firefox/firefox.sh

less /usr/bin/firefox  # shows that it is really [a symbolic link to] a shell-script with ordinary text lines

```

So the version of Firefox from the Ubuntu repository for 12.04.4 is 26. The script at ./firefox finds that version somehow and gives it priority before the local one, maybe because it it using the environment variable PATH. Running as root is following a different internal path of execution (maybe not only because its environment variable PATH might be different).

---

### Post by Isamu715 on 2014-02-08
What exactly do you want to do? If you want the latest version of Firefox just wait a little, it'll get to the official repositories soon.

---

### Post by cytg on 2014-02-08
Wow, nice ... Thanks. Level of understanding++ :).

Isamu -> I know, but I was just curious.. I dont expect a package manager to be able to hold my hand in 100% of circumstances.

Again, nice learning experience, thx.

But then again, id expect this to work

mv firefox firefox2
./firefox2

But that too spawns version 26.

"which firefox2" yields no result (problary because its in current dir ?)

---

### Post by squakie on 2014-02-08
There's a little more going on than that.   Give sudous a chance to research.  These things take time.

---

### Post by cytg on 2014-02-08
00019730   50 6F 69 73  6F 6E 69 6E  67 00 4D 6F  7A 69 6C 6C  Poisoning.Mozill
00019740   61 00 46 69  72 65 66 6F  78 00 32 37  2E 30 00 32  a.Firefox.27.0.2
00019750   30 31 34 30  31 32 37 31  39 34 36 33  36 00 00 00  0140127194636...

thats what i get on a hexedit of firefox2. How can I not spawn fireforx2 with ./firefox2 ? .. Sounds like the binary it self is doing some haywire

maybe my it is my basic linux skills (and they are very very basic) that fail me, but "./" means current dir, right? and "./exec" means execute "exec" in current dir? Is there another pathway im not aware of ?

---

### Post by sudodus on 2014-02-09
Yes **.** means the current directory and **./filename** points to the file 'filename' in the current directory. If the file is executable, you can execute it with **./filename** as a command.

Please look carefully at the code of your various versions of firefox (the shellscript)

```

less firefox
less firefox2
less /usr/bin/firefox
```

It might help you run the new version, if you remove the old version, and make a real installation of the new version to the correct place in the file system. Most software come with scripts to install them, and there should be some kind of document, a README file or document file (file.doc) that describes how to install it.

---

### Post by cytg on 2014-02-09
less firefox2 show it is an elf .. and if I hexedit it and do a ascii search for version 27, i get the result in my post above. So I am pretty sure that "firefox2" is an executable binary sitting in my current directory... yet, still, ./firefox2 spawns the old version. (Well, thats what the about dialog says anyway.. about to not-trust that either)..
I know I can do it "the right way", but I really need to understand what is going on under the hood here... I know I could figure this out under windows, sysinternals, debugging etc. Do I have similar tools available to me here ?

^?ELF^B^A^A^@^@^@^@^@^@^@^@^@^B^@>^@^A^@^@^@p7@^@^@^@^@^@@^@^@^@^@^@

---

### Post by Dave_L on 2014-02-09
The "file" command is handy for determining whether a file is an executable, a script, etc.

You can use "ll" or "stat" to see whether the file is a symbolic link to another file.

---

### Post by cytg on 2014-02-09
xx@xx-xx:~/Downloads/firefox$ stat firefox2
  File: ‘firefox2’
  Size: 127352    	Blocks: 256        IO Block: 4096   regular file
Device: 801h/2049d	Inode: 787005      Links: 1
Access: (0755/-rwxr-xr-x)  Uid: ( 1000/    uber)   Gid: ( 1000/    xx)
Access: 2014-02-08 22:50:37.587050267 +0100
Modify: 2014-01-28 07:18:38.000000000 +0100
Change: 2014-02-08 22:50:31.123050113 +0100
 Birth: -

xx@xx-xx:~/Downloads/firefox$ ll firefox2
-rwxr-xr-x 1 xx xx 127352 Jan 28 07:18 firefox2*

xx@xx-xx:~/Downloads/firefox$ file firefox2
firefox2: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.18, BuildID[sha1]=0x26ebbd57c19b56d5ac05d93907843595de915d99, stripped


Weird huh ?

---

