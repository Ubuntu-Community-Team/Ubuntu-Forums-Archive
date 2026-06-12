---
title: "how do I install tar gz?"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by hyperhopper on 2008-09-09
I am trying something new--to install sauerbraten not from synaptic, but from its website, which had a tar.bz2 extension  how do I set this up so that it is playable?

---

### Post by abeisgreat on 2008-09-09
> **hyperhopper said:**
> I am trying something new--to install sauerbraten not from synaptic, but from its website, which had a tar.bz2 extension  how do I set this up so that it is playable?

If I'm not mistaked that is a compression format, so you would extract it and boot the file haha, I might be wrong though.

---

### Post by hyperhopper on 2008-09-09
im extracting it now--but what do you mean by boot the file?

---

### Post by hyperhopper on 2008-09-09
ok-- its has been extracted and it is in my home folder---now what?

---

### Post by james_vanb on 2008-09-09
[http://howto.wikia.com/wiki/Howto_untar_a_tar_file_or_gzip-bz2_tar_file](http://howto.wikia.com/wiki/Howto_untar_a_tar_file_or_gzip-bz2_tar_file)

---

### Post by halitech on 2008-09-09
check here: [http://www.psychocats.net/ubuntu/installingsoftware#lastresorts](http://www.psychocats.net/ubuntu/installingsoftware#lastresorts)

normally its a matter of extracting the file, opening a terminal, changing to the directory where the files are and running ./configure then make then make install but check and see if there is a read me file, it will tell you for sure

---

### Post by hyperhopper on 2008-09-09
huh? how do i use that info?

---

### Post by halitech on 2008-09-09
> **hyperhopper said:**
> huh? how do i use that info?

which set of info?

---

### Post by t0p on 2008-09-09
If you want us to tell you how to install this file, you have to tell us what kind of file it is.  I don't mean the tar gz - that was just an archive.  We need to know what the contents of the tar.gz is.  Probably easiest if you just post here all the contents of the tar.gz that you extracted.  Then I might be able to tell you what to do.

---

### Post by james_vanb on 2008-09-09
Once downloaded, compile by trying:

```
cd "name of .tr.bz2 file without adding .tr.bz2"
./configure
make
make install
```

Where "name of .tr.bz2 file without adding .tr.bz2" is the file you downloaded with .tr.bz2 deleted.

---

### Post by hyperhopper on 2008-09-09
when I cd to the folder(sauerbraten) and type in ./congifure I get no such file or directory found

---

### Post by halitech on 2008-09-09
can you post the output of```
ls -l
``` for us please

---

### Post by james_vanb on 2008-09-09
From the site I think you downloaded from:

```
 Linux/BSD
Getting the game running on a Linux or BSD based system requires a little knowledge of the command line, if this intimidates you, consider getting a copy of Windows for dual booting (install instructions above). Please note these instructions are for a single user install, in most cases you may want to use the packaging system provided by your distribution (which is beyond the scope of this document).

    * Move the installation files to your home directory, if they aren't already.
    * Open up a console/terminal, you should be at a prompt that looks something like, [username@hostname:~]$ or hostname:~$ (in most cases, "~" is interchangable with "/home/username").
    * Type these commands (remembering to adjust for the release and platform):

tar -jxvf sauerbraten_YYYY_MM_DD_CODENAME_PLATFORM.tar.bz
cd sauerbraten
chmod +x sauerbraten_unix bin_unix/linux_client bin_unix/linux_server
```

```
To run the game, type: ./sauerbraten_unix
```

Edit:  That copy sure turned out funky.  Here is the site:

[http://cube.wikispaces.com/Install+Guide](http://cube.wikispaces.com/Install+Guide)

---

### Post by t0p on 2008-09-09
> **james_vanb said:**
> 
Where "name of .tr.bz2 file without adding .tr.bz2" is the file you downloaded with .tr.bz2 deleted.

Well that was as clear as mud!!  :confused:

---

### Post by hyperhopper on 2008-09-09
> **halitech said:**
> can you post the output of```
ls -l
``` for us please
from when i am in home or when i cded into the folder?

---

### Post by halitech on 2008-09-09
from the folder you extracted the files to please

---

### Post by hyperhopper on 2008-09-09
i started running random files in terminal and found one that works!!!---but still--- I think there is a method...

---

### Post by jerome1232 on 2008-09-09
> **james_vanb said:**
> From the site I think you downloaded from:

```
 Linux/BSD
Getting the game running on a Linux or BSD based system requires a little knowledge of the command line, if this intimidates you, consider getting a copy of Windows for dual booting (install instructions above). Please note these instructions are for a single user install, in most cases you may want to use the packaging system provided by your distribution (which is beyond the scope of this document).

    * Move the installation files to your home directory, if they aren't already.
    * Open up a console/terminal, you should be at a prompt that looks something like, [username@hostname:~]$ or hostname:~$ (in most cases, "~" is interchangable with "/home/username").
    * Type these commands (remembering to adjust for the release and platform):

tar -jxvf sauerbraten_YYYY_MM_DD_CODENAME_PLATFORM.tar.bz
cd sauerbraten
chmod +x sauerbraten_unix bin_unix/linux_client bin_unix/linux_server
```

```
To run the game, type: ./sauerbraten_unix
```

Edit:  That copy sure turned out funky.  Here is the site:

[http://cube.wikispaces.com/Install+Guide](http://cube.wikispaces.com/Install+Guide)


Did you read this post? Or the instructions on the site?

---

### Post by ~~Tito~~ on 2008-09-10
Hey all I am back, anyways. This is what I get when I l -sl the folder. . .

I am trying to install win rar. . .Ubuntu skills are sooo rusty that I am having a bit of a hard time with what I used to know. . 

```
felipe@Felipes-Laptop:~$ cd rar
bash: cd: rar: No such file or directory
felipe@Felipes-Laptop:~$ cd /home/felipe/Desktop/rar 
felipe@Felipes-Laptop:~/Desktop/rar$ ./configure
bash: ./configure: No such file or directory
felipe@Felipes-Laptop:~/Desktop/rar$ ls -l
total 1608
-rwxr-xr-x 1 felipe felipe  58800 2008-05-26 04:49 default.sfx
-rw------- 1 felipe felipe    217 2008-05-26 04:49 file_id.diz
-rw------- 1 felipe felipe   6291 2008-05-26 04:49 license.txt
-rw------- 1 felipe felipe    428 2008-05-26 04:49 Makefile
-rw------- 1 felipe felipe   3183 2008-05-26 04:49 order.htm
-rwxr-xr-x 1 felipe felipe 348260 2008-05-26 04:49 rar
-rw------- 1 felipe felipe   1018 2008-05-26 04:49 rarfiles.lst
-rwxr-xr-x 1 felipe felipe 887996 2008-05-26 04:49 rar_static
-rw------- 1 felipe felipe  71092 2008-05-26 04:49 rar.txt
-rw------- 1 felipe felipe   1050 2008-05-26 04:49 readme.txt
-rw------- 1 felipe felipe   8957 2008-05-26 04:49 technote.txt
-rwxr-xr-x 1 felipe felipe 200156 2008-05-26 04:49 unrar
-rw------- 1 felipe felipe   7289 2008-05-26 04:49 whatsnew.txt
felipe@Felipes-Laptop:~/Desktop/rar$ 

```

Never mind, it was reconfigured so all I had to do was "make", and then "make install". . .

My skills are coming back O.o. . .

---

