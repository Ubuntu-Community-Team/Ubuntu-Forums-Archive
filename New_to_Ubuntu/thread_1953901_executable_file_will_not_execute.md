---
title: "executable file will not execute"
date: 2012-04-07
forum: New to Ubuntu
---

### Post by Teber on 2012-04-07
i just upgraded to ubuntu 11.10. and now the following occurs. i like to play this game called TOME. it comes in an archive. after unpacking the folder containing the game is in my home, with an icon to start the game.

this worked just fine until ubuntu 11.04. now clicking the icon will not do anything. so i tried to start the game in a terminal. in this case the terminal will claim that the file does not exist! i attach screenshots of the properties window.

i have no doubt that this occurs due to my ignorance only. so i would be most grateful if someone would point out where i went wrong. many thanks in advance.

---

### Post by lmarmisa on 2012-04-07
Are you sure that, when you try to run the file from a terminal, you type the absolute or relative path to the file?.

I am not able to see the complete path to the file, but try to type a command similar to (the tab key will help you to complete the path):

```

~/tome-new/t-engine4-linux????/t-engine

```

---

### Post by Teber on 2012-04-07
no joy. the command still gets the response bash: /home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine: No such file or directory

previously i ran the command when in the relative dir. ls gives contents of dir including the t-engine (letter colour green)

---

### Post by lmarmisa on 2012-04-07
> **Teber said:**
> no joy. the command still gets the response bash: /home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine: No such file or directory

previously i ran the command when in the relative dir. ls gives contents of dir including the t-engine (letter colour green)

Hmmm. Could you post the result of this command?

```

ls -l /home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine

```

---

### Post by 3rdalbum on 2012-04-07
Drag the file into the terminal. Click the terminal window again to bring it to the front, then press Enter. Does it work now?

---

### Post by Teber on 2012-04-07
to Imarmisa:

```
jan@jan-G31-M7-TE:~$ ls -l /home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine
-rwxr-xr-x 1 jan jan 3382614 2012-02-25 19:20 /home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine

```

hope this helps

---

### Post by Teber on 2012-04-07
to 3rdalbum:

no same result

---

### Post by lmarmisa on 2012-04-07
> **Teber said:**
> to Imarmisa:

```
jan@jan-G31-M7-TE:~$ ls -l /home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine
-rwxr-xr-x 1 jan jan 3382614 2012-02-25 19:20 /home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine

```hope this helps

Try these two commands:

```

bash /home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine

/home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine

```

Both commands should run ok.

---

### Post by Teber on 2012-04-07
Code: ```
jan@jan-G31-M7-TE:~$ bash /home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine
/home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine: /home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine: cannot execute binary file
jan@jan-G31-M7-TE:~$ /home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine
bash: /home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine: No such file or directory

```

---

### Post by lmarmisa on 2012-04-07
> **Teber said:**
> Code: ```
jan@jan-G31-M7-TE:~$ bash /home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine
/home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine: /home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine: cannot execute binary file
jan@jan-G31-M7-TE:~$ /home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine
bash: /home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine: No such file or directory

```

Really odd. This is a binary file. So, only the second command should work. But the shell says that the file does not exist. This seems wrong.

Try this command:

```

md5sum /home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine

```

The result should be something like 3e9a133117633af26317d90e2d32f677.

---

### Post by Teber on 2012-04-07
and so it is

Code ```
jan@jan-G31-M7-TE:~$ md5sum /home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine
3e9a133117633af26317d90e2d32f677  /home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine
```

i'm completely mystified

thanks for all your trouble so far

---

### Post by lmarmisa on 2012-04-07
> **Teber said:**
> and so it is

Code ```
jan@jan-G31-M7-TE:~$ md5sum /home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine
3e9a133117633af26317d90e2d32f677  /home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine
```i'm completely mystified

thanks for all your trouble so far

Your file is stored in the correct place and the data integrity is verified.

Something seems corrupt about bash.

Try to check if using sh you get the same problem:

```

sh
/home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine

```

---

### Post by Teber on 2012-04-07
here's what happened:

```
/jan@jan-G31-M7-TE:~$ sh home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine
sh: /home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-eng/home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine: not found
```

i would add that clicking on the icon didn't seem to make anything happen...

---

### Post by lmarmisa on 2012-04-07
> **Teber said:**
> here's what happened:

```
/jan@jan-G31-M7-TE:~$ sh home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine
sh: /home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-eng/home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine: not found
```i would add that clicking on the icon didn't seem to make anything happen...

The code you have copied seems not good.

I proposed two different commands:

```

sh

/home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine

```

I recommend another test.

Create a new user account. Named it, for example, test.

Log in that new user account and check if bash runs properly from this test account. Type the command:

```

/home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine

```

---

### Post by bodhi.zazen on 2012-04-07
Do you have a separate home directory and is it mounted noexec ?

Show the output of 

```
mount | grep home
```

---

### Post by Teber on 2012-04-07
again the response: not found

it may help to know that the same problem occurred under kubuntu 11.10, xubuntu 11.10 and fedora 16

---

### Post by Teber on 2012-04-07
i tried the mount command. here's the result:

```
jan@jan-G31-M7-TE:~$ mount | grep home
gvfs-fuse-daemon on /home/jan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jan)
gvfs-fuse-daemon on /home/test/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=test)

```

just for in case it helps. here's the content of fstab:

UUID=79a8fd3b-dce8-4175-b293-683cfb1753b5 swap swap sw 0 0
UUID=5ebb13e9-3d51-4d6d-9a95-1c4f94538661 / ext4 defaults 0 1

---

### Post by lmarmisa on 2012-04-07
> **Teber said:**
> again the response: not found

it may help to know that the same problem occurred under kubuntu 11.10, xubuntu 11.10 and fedora 16

Could you give more details about your last comment?.

I propose a test (maybe my last attempt :D). 

Type these commands:

```

cd ~
mkdir test1
cd test1
cp /usr/bin/md5sum .
./md5sum md5sum

```These are the outputs of the commands on my computer:

```

luis@UB1104ENG:~$ cd ~
luis@UB1104ENG:~$ mkdir test1
luis@UB1104ENG:~$ cd test1
luis@UB1104ENG:~/test1$ cp /usr/bin/md5sum .
luis@UB1104ENG:~/test1$ ./md5sum md5sum
21934e3bedf6f5a85d7c69e326cc3362  md5sum
luis@UB1104ENG:~/test1$

```

---

### Post by Teber on 2012-04-07
would i solve the problem with the following command?

```
sudo chmod /home/jan 755
```

or something similar? i prefer to err on the side of caution

---

### Post by Teber on 2012-04-07
here's my terminal conversation:

```
jan@jan-G31-M7-TE:~$ cd ~
jan@jan-G31-M7-TE:~$ mkdir test1
jan@jan-G31-M7-TE:~$ cd test1
jan@jan-G31-M7-TE:~/test1$ cp /usr/bin/md5sum .
jan@jan-G31-M7-TE:~/test1$ ./md5sum md5sum
c5d1db4b5746ee631d1aea0ee594c47c  md5sum
jan@jan-G31-M7-TE:~/test1$
```

---

### Post by Teber on 2012-04-07
> **lmarmisa said:**
> Could you give more details about your last comment?

i've trying out some other distros yesterday. after each clean install the game would not start.

---

### Post by lmarmisa on 2012-04-07
> **Teber said:**
> here's my terminal conversation:

```
jan@jan-G31-M7-TE:~$ cd ~
jan@jan-G31-M7-TE:~$ mkdir test1
jan@jan-G31-M7-TE:~$ cd test1
jan@jan-G31-M7-TE:~/test1$ cp /usr/bin/md5sum .
jan@jan-G31-M7-TE:~/test1$ ./md5sum md5sum
c5d1db4b5746ee631d1aea0ee594c47c  md5sum
jan@jan-G31-M7-TE:~/test1$
```

Well. Finally something makes sense. :D

All commands are correct!!!.

Hmmm.

I have a doubt. Your game TOME is packed in one .tar.bz2 file. Did you physically unzip/untar that file?. Or did you use the file manager to access to the contents?.

---

### Post by Teber on 2012-04-07
downloaded the file to downloads in my home. then dragged it to the tome dir. and then i unpacked it.

---

### Post by lmarmisa on 2012-04-07
> **Teber said:**
> downloaded the file to downloads in my home. then dragged it to the tome dir. and then i unpacked it.

Do you still have the .tar.bz2 file in your home folder?.

---

### Post by Teber on 2012-04-07
yes i do. for good measure i unpacked it again before starting this thread.

---

### Post by lmarmisa on 2012-04-07
> **Teber said:**
> yes i do. for good measure i unpacked it again before starting this thread.

Ok. Type these commands:

```

cd ~
tar xvf t-engine4-linux32-1.0.0beta38.tar.bz2
cd t-engine4-linux32-1.0.0beta38/
./t-engine

```

---

### Post by Teber on 2012-04-07
weird. the archive will be unpacked by the archive manager in gui. here's what happens in terminal:

```
jan@jan-G31-M7-TE:~$ cd tome-new/
jan@jan-G31-M7-TE:~/tome-new$ ls
t-engine4-linux32-1.0.0beta38-nomusic.tar.bz2
jan@jan-G31-M7-TE:~/tome-new$ cd ~
jan@jan-G31-M7-TE:~$ tar xvf t-engine4-linux32-1.0.0beta38-nomusic.tar.bz2
tar: t-engine4-linux32-1.0.0beta38-nomusic.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
jan@jan-G31-M7-TE:~$
```

could it be a permissions problem as suggested by bodhi.zazen?

---

### Post by lmarmisa on 2012-04-07
> **Teber said:**
> weird. the archive will be unpacked by the archive manager in gui. here's what happens in terminal:

```
jan@jan-G31-M7-TE:~$ cd tome-new/
jan@jan-G31-M7-TE:~/tome-new$ ls
t-engine4-linux32-1.0.0beta38-nomusic.tar.bz2
jan@jan-G31-M7-TE:~/tome-new$ cd ~
jan@jan-G31-M7-TE:~$ tar xvf t-engine4-linux32-1.0.0beta38-nomusic.tar.bz2
tar: t-engine4-linux32-1.0.0beta38-nomusic.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
jan@jan-G31-M7-TE:~$
```could it be a permissions problem as suggested by bodhi.zazen?

The file tar.bz2 is located at folder tome-new, not at home.

Type the commands:

```

cd ~/tome-new/
tar xvf t-engine4-linux32-1.0.0beta38-nomusic.tar.bz2
cd t-engine4-linux32-1.0.0beta38/ 
./t-engine

```

---

### Post by Teber on 2012-04-07
the unpacking worked this time in terminal.

here's what happened next:

```
jan@jan-G31-M7-TE:~/tome-new/t-engine4-linux32-1.0.0beta38$ ./t-engine
bash: ./t-engine: No such file or directory
jan@jan-G31-M7-TE:~/tome-new/t-engine4-linux32-1.0.0beta38$
```

---

### Post by oldos2er on 2012-04-07
Can you show us the output of ```
file /home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine
``` ?

Are you running 64-bit Ubuntu?

---

### Post by lmarmisa on 2012-04-07
> **Teber said:**
> the unpacking worked this time in terminal.

here's what happened next:

```
jan@jan-G31-M7-TE:~/tome-new/t-engine4-linux32-1.0.0beta38$ ./t-engine
bash: ./t-engine: No such file or directory
jan@jan-G31-M7-TE:~/tome-new/t-engine4-linux32-1.0.0beta38$
```

Really this makes no sense. What is the difference between the file md5sum that we copied and the file t-engine that we untar?.

I suppose that the command ls -l will show something similar to this:

```

luis@UB1104ENG:~/Desktop/kk/t-engine4-linux32-1.0.0beta38$ ls -l
total 3364
drwxr-xr-x 2 luis luis    4096 2012-03-26 14:24 bootstrap
-rw-r--r-- 1 luis luis     626 2010-08-01 00:07 CONTRIBUTING
-rw-r--r-- 1 luis luis   35147 2010-04-07 19:43 COPYING
-rw-r--r-- 1 luis luis     212 2011-08-22 15:14 COPYING-TILES
-rw-r--r-- 1 luis luis    1546 2011-07-22 18:41 CREDITS
drwxr-xr-x 8 luis luis    4096 2012-03-26 14:23 game
drwxr-xr-x 2 luis luis    4096 2011-08-18 19:48 lib
-rwxr-xr-x 1 luis luis 3382614 2012-02-25 23:50 t-engine
luis@UB1104ENG:~/Desktop/kk/t-engine4-linux32-1.0.0beta38$

```

---

### Post by Teber on 2012-04-07
```
jan@jan-G31-M7-TE:~/tome-new/t-engine4-linux32-1.0.0beta38$ file /home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine
/home/jan/tome-new/t-engine4-linux32-1.0.0beta38/t-engine: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.8, not stripped
jan@jan-G31-M7-TE:~/tome-new/t-engine4-linux32-1.0.0beta38$
```

i'm using 64 bits

---

### Post by oldos2er on 2012-04-07
I think that's the problem. In the old days you would install ia32-libs, but with multiarch things aren't that simple. If there's a 64-bit version of the game I would try that.

---

### Post by lmarmisa on 2012-04-07
> **oldos2er said:**
> I think that's the problem. In the old days you would install ia32-libs, but with multiarch things aren't that simple. If there's a 64-bit version of the game I would try that.

I agree. The game is apparently only for 32 bits.

Try this command:

```

sudo apt-get install ia32-libs

```NOTE: Bash should give a more accurate information in cases like this. This makes not sense.

---

### Post by Teber on 2012-04-07
> **lmarmisa said:**
> Really this makes no sense. What is the difference between the file md5sum that we copied and the file t-engine that we untar?.

I suppose that the command ls -l will show something similar to this:

```

luis@UB1104ENG:~/Desktop/kk/t-engine4-linux32-1.0.0beta38$ ls -l
total 3364
drwxr-xr-x 2 luis luis    4096 2012-03-26 14:24 bootstrap
-rw-r--r-- 1 luis luis     626 2010-08-01 00:07 CONTRIBUTING
-rw-r--r-- 1 luis luis   35147 2010-04-07 19:43 COPYING
-rw-r--r-- 1 luis luis     212 2011-08-22 15:14 COPYING-TILES
-rw-r--r-- 1 luis luis    1546 2011-07-22 18:41 CREDITS
drwxr-xr-x 8 luis luis    4096 2012-03-26 14:23 game
drwxr-xr-x 2 luis luis    4096 2011-08-18 19:48 lib
-rwxr-xr-x 1 luis luis 3382614 2012-02-25 23:50 t-engine
luis@UB1104ENG:~/Desktop/kk/t-engine4-linux32-1.0.0beta38$

```

yes i suppose it would. maybe oldos2er has the answer. maybe it would work under 32 bits. so as a last desparaditch effort i will install the 32 bi version next to the 64 bits version.

that will have to wait till tomorrow though. i will be going out tonight for to do some volunteer work. and i like to have dinner first at my leisure.

as a single father of a childless family i must do the cooking all myself.

thanks everyone for the contributions. it was sure a learning experience for me so far.

---

### Post by Teber on 2012-04-07
here are my points!

ubuntu community twelve points
communauté ubuntu douze points

thanks a lot folks! the ia32 libs did the trick! you're champs!

---

