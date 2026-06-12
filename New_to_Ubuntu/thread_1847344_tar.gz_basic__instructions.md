---
title: "tar.gz basic  instructions"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by nksjolinder on 2011-09-20
Hey guys,

so i was wondering if anyone could write out (IN THE MOST BASIC LANGUAGE POSSIBLE!) the process in which you install a tar.gz file? I have run ./configure on one tar i have and it had an error. does that mean it will not install on my computer? also, should i have directed the cd command at the file within the folder (cd /usr/local/src/dymo-cups-drivers-1.2.0) or just to the folder that the file is in(cd /usr/local/src)? thanks!

Nick

---

### Post by haqking on 2011-09-20
> **nksjolinder said:**
> Hey guys,

so i was wondering if anyone could write out (IN THE MOST BASIC LANGUAGE POSSIBLE!) the process in which you install a tar.gz file? I have run ./configure on one tar i have and it had an error. does that mean it will not install on my computer? also, should i have directed the cd command at the file within the folder (cd /usr/local/src/dymo-cups-drivers-1.2.0) or just to the folder that the file is in(cd /usr/local/src)? thanks!

Nick

OK you dont install a tar.gz, you extract its contents and then what you do next depends on whats inside.

People are often scared or confused by installing software in Linux, there is no real reason it is usually straight forward.

**First of all always search in the Software Centre or Synaptic to see if software is already in the repos for easy install or from the developers website where a .deb might be available again for easy install (like a .exe in windows)**

If you have to download it as a package it will often come down in a package/archive format such as xxxxx.tar or xxxx.tar.gz etc.

These are analogous to windows .zip files but with varying compression denoted by the .xx after the .tar such as .tar.gz where .gz is the compression. A .tar file means Tape Archive which is legacy from UNIX when things were backed up to tape drives. The 2 or 3 letters after the .tar refer to the type of compression used to pack down the archive.

See here for dealing with these files [https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

It is often just a simple case of right clicking in your GUI on the file and choosing extract then it will be unpackaged to a directory.

The contents might simply be a .deb file as i said for easy installation see here:
[http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

If the contents is source code then you need to compile this, this is where people often get stumped and is dependant on the developer and the documentation provided, once unpackaged there is often a README text file or a INSTALL file which you should read as it will often contain clear and concise instructions on what to do.

If not then you need to figure it out, see here for information on compiling from source:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

then you should be set ;-)

Have fun

Regards

haqking

---

### Post by raja.genupula on 2011-09-20
hey these are basic installations commands from a tar 
follow them one by one 
```
tar xvf filename.tar
```
then cd to that dir
then do these things 
```
./configure
```
```
make
```
```
sudo make install
```

execute them one by one . at any stage if you got errors . report us back with the error . 

normally we are going to face dependencies issues while installing from TAR , so we cant decide that if its not installed in your system , its not possible in others .
if tar file crashed or damaged so no one can do anything . so follow the above instructions and report us back what you got .
all the best .

---

### Post by Paddy Landau on 2011-09-20
Nick, you already got your answer in [post #2 of your previous thread]("http://ubuntuforums.org/showthread.php?p=11269784#post11269784").

---

### Post by nksjolinder on 2011-09-20
haqking thanks for giving me the big picture on tar files and paddy you are right, i did not read that close enough but luckily i got a a good and broad response to it this time to use for future reference

---

### Post by haqking on 2011-09-20
> **nksjolinder said:**
> haqking thanks for giving me the big picture on tar files and paddy you are right, i did not read that close enough but luckily i got a a good and broad response to it this time to use for future reference

no problem you are very welcome.

peace

---

