---
title: "Verify downloaded iso integrity with md5sum or sha1sum"
date: 2006-11-01
forum: Outdated Tutorials &amp; Tips
---

### Post by bodhi.zazen on 2006-11-01
[SIZE=4]**md5sum and sha1sum are utilities to check the integrity of a file, usually a downloaded iso**[/SIZE]

In this example I will use "Ubuntu.iso" and a file "groups", but this works with any file.

**_Note_: This how is performed entirely in a terminal (CLI). No GUI.**

[COLOR=blue]GUI Tool ~ **Windows/Mac/Linux versions**[/COLOR] : [md5 file check (Penguin byte)]("http://penguinbyte.com/software/md5filecheck/")

_EDIT_: [COLOR=blue]The section on multiple files was added at the suggestion of 655 (Thanks 655)[/COLOR].

[SIZE=2]**md5sum**[/SIZE]

_Create a *.md5 file_:
```
md5sum Ubuntu.iso > Ubuntu.iso.md5
```[COLOR=red]_Note_: Do not use this to verify a downloaded iso or file.[/COLOR]
This is an example of how to create a *.md5 on a file you trust. Give this to others to verify the integrity of a file or iso you authored.
*See "How to use md5sum and sha1sum files to verify integrity of downloaded iso images or files" section below.*

_Verify md5sum of a file or iso_:
```
md5sum -c Ubuntu.iso.md5
```[SIZE=2]**sha1sum**[/SIZE]

_Create a *.sha1 file_:
```
sha1sum Ubuntu.iso > Ubuntu.iso.sha1
```[COLOR=red]_Note_: Do not use this to verify a downloaded iso or file.[/COLOR]
This is an example of how to create a *.sha1 on a file you trust. Give this to others to verify the integrity of a file or iso you authored.
*See "How to use md5sum and sha1sum files to verify integrity of downloaded iso images or files" section below.*

_Verify sha1sum of a file or iso_:
```
sha1sum -c Ubuntu.iso.sha1
```

[SIZE=2]**Format of *.md5 and *.sha1 files**[/SIZE]

_Format of a *.md5 or *.sha1_:
> <m5d>  Ubuntu.iso
<sha1>  Ubuntu.iso**[COLOR=red]_Note_: There are 2 spaces between the sum and iso[/COLOR]** 

**Sample *.md5 and *.sha1 file contents:**

groups.md5 (file = groups)
> b2d57f96eba473ce6e8f345e2ae7f149  groupsgroups.sha1 (file = groups)
> 1cab92940e459d872211c7d1a195520d3062029d  groups

[SIZE=2]**How to use md5sum and sha1sum files to verify integrity of downloaded iso images or files**[/SIZE]

_Note_:
[LIST=1]
[*]The iso and iso.md5 or iso.sha1 **must both be in the same directory**.
[*]The directory containing these files must be your current directory.
[/LIST]
_For example_: If your iso and iso.md5 were downloaded to your Desktop:
```
cd ~/Desktop
md5sum -c iso.md5
```_Step-by-step instructions_

_Create an *.iso.md5 or *.iso.sha1 file (to check integrity)_:
[LIST=1]
[*]Get the md5sum or sha1sum from the download site (download the iso.md5/iso.sha1 or create an iso.md5/iso.sha1 as below).
[*]From the CLI:
```
echo "<paste_md5_sum_here>  Ubuntu.iso" > Ubuntu.iso.md5sum

OR

echo "<paste_sha1_sum_here>  Ubuntu.iso" > Ubuntu.iso.sha1sum
```
[*]Or, if you prefer, use a graphical editor (gedit/kate/nano/vim):
[INDENT]
[LIST]
[*]Open an editor
<paste_md5_sum_here>  Ubuntu.iso
Save as Ubuntu.iso.md5
[*]Open an editor
<paste_sha1_sum_here>  Ubuntu.iso
Save as Ubuntu.iso.sha1
[/LIST]
[/INDENT]
[*]Verify the integrity as above, [COLOR=red]use the md5sum and sha1sum from the download site[/COLOR].
[*]Multiple files. To chesk multiple files use multiple entries in your *.md5 or *.sha1 (see bleow). ALL FILES TO BE CHECKED AND THE *.md5 or *.sha1 MUST BE IN THE SAME DIRECTORY.
[/LIST]

[SIZE=2]**Examples (CLI)**[/SIZE]

_Examples using a file groups_:
> _md5_:
bodhi@Arch:~$md5sum groups > groups.md5sum
bodhi@Arch:~$cat groups.md5sum
b2d57f96eba473ce6e8f345e2ae7f149  groups
bodhi@Arch:~$md5sum -c groups.md5sum
groups: OK
bodhi@Arch:~$

_sha1_:
bodhi@Arch:~$sha1sum groups > groups.sha1
bodhi@Arch:~$cat groups.sha1
1cab92940e459d872211c7d1a195520d3062029d  groups
bodhi@Arch:~$sha1sum -c groups.sha1
groups: OK
bodhi@Arch:~$_Multiple files_
This will check any ubuntu*.iso in the current directory.

You will get an error message if the file does not exist, the 2>/dev/null redirects the error message.
```
md5sum -c MD5SUMS 2>/dev/null
```File name = MD5SUMS (_Note_: Unlike other OS, in Linux the file with your sums does not need to end in .md5 or .sha1.
> b9a5be3a5858ade278d664d41310a4ab  ubuntu-6.06.1-alternate-amd64.iso
6cb8582aa5615ed4616165743a0868d7  ubuntu-6.06.1-alternate-i386.iso
0b5b3df02da3d9ed6f4ac482cf541f04  ubuntu-6.06.1-alternate-powerpc.iso
50e3912c555f98f7bca56b2a0200b205  ubuntu-6.06.1-desktop-amd64.iso
fb3af44c21f1f68cc25fda7edb8c1bd3  ubuntu-6.06.1-desktop-i386.iso
502911770ad173dbe82c698379ed7d11  ubuntu-6.06.1-desktop-powerpc.iso
8254b0f3696ed17c52a2cb59c9ebd2cc  ubuntu-6.06.1-server-amd64.iso
5ad76d8b380ab5be713e5daa9ea84475  ubuntu-6.06.1-server-i386.iso
6d1c3b5cb41661365b3db5cf12bb2836  ubuntu-6.06.1-server-powerpc.iso
2ccc1ec608040e6aac8913a016c31bed  ubuntu-6.06.1-server-sparc.iso[SIZE=2]**Check the md5sum or sha1sum after burning a CD**[/SIZE]

K3b will show the md5sum of the iso and check (show) the md5sum of the burned CD/DVD automatically (which is part of the reason I would advise K3b over other options).

**From the CLI:**
_Note_: Some consider this method to be unreliable.
[LIST=1]
[*]Put the disk into your CD/DVD drive.
[*]Mount the CD/DVD if your system does not automount the CD/DVD.
[*]**Address the CD/DVD by /dev/hdxy NOT /dev/cdrom**.
[*]ie **/dev/hdc**
[/LIST]

_Example_
_Note_: On my box my CD is **/dev/hda**
> bodhi@Arch:~$md5sum /dev/hda
a3c9b003d9bb5c7e7fc3645d43b9b8ad  /dev/hda
bodhi@Arch:~$sha1sum /dev/hda
e2882ef99b8079a10d6567493a7ac6e8e89d6a42  /dev/hda
bodhi@Arch:~$
_Note_: This takes some time and you will need to confirm the md5sum visually (no auto check).

**Automation**
This involves some fancy CLI footwork:
_md5sum_:
```
md5sum /dev/hda > ./test && diff ./test /home/bodhi/MyDownloads/fluxbuntu.iso.md5 && rm -f ./test
```Returns:
> < a3c9b003d9bb5c7e7fc3645d43b9b8ad  /dev/hda
---
> a3c9b003d9bb5c7e7fc3645d43b9b8ad  Fluxbuntu.iso
bodhi@Arch:~$
_sha1sum_
```
sha1sum /dev/hda > ./test && diff ./test /home/bodhi/MyDownloads/fluxbuntu.iso.sha1 && rm -f ./test
```Returns:
> < e2882ef99b8079a10d6567493a7ac6e8e89d6a42  /dev/hda
---
> e2882ef99b8079a10d6567493a7ac6e8e89d6a42  Fluxbuntu.iso
bodhi@Arch:~$Which will at least line up the md5/sha1 sums.
**_Note_: You must supply the proper path to the iso.md5 and iso.sha1.**



[SIZE=2]**Windows users**[/SIZE]
_Windows md5sum checker (Free, opensource)_: [winMd5Sum]("http://www.nullriver.com/index/products/winmd5sum")

_Windows sha1sum checker (Free, opensource)_: [sha1sum]("http://lists.gnupg.org/pipermail/gnupg-announce/2004q4/000184.html")
_Note_: This is run from the windows command line, no gui. See link for instructions. 


**[SIZE=4]Download with confidence[/SIZE]**

[COLOR=gray]bodhi.[/COLOR][COLOR=navy]zazen[/COLOR]

---

### Post by DC@DR on 2006-11-01
Great HOWTO, it's clear and easy-to-follow, many thanks :)

---

### Post by 655 on 2006-12-01
Reviving a somewhat old thread here, but...
It was very instructive and to-the-point, thank you.

My one question is, is there a way to run this command on a batch of files at once, with separate .md5 files being generated for each file?  Or to have it work recursively in several directories?

Maybe I need a separate utility to do this :confused:

---

### Post by bodhi.zazen on 2006-12-01
> **655 said:**
> Reviving a somewhat old thread here, but...
It was very instructive and to-the-point, thank you.

My one question is, is there a way to run this command on a batch of files at once, with separate .md5 files being generated for each file?  Or to have it work recursively in several directories?

Maybe I need a separate utility to do this :confused:

655: Thank you fro taking the time to reply.

Absolutely.

The files must to be checked must all be in the same directory, and the *.md5 must also be in the same directory.

Example:

File name = MD5SUMS
> b9a5be3a5858ade278d664d41310a4ab  ubuntu-6.06.1-alternate-amd64.iso
6cb8582aa5615ed4616165743a0868d7  ubuntu-6.06.1-alternate-i386.iso
0b5b3df02da3d9ed6f4ac482cf541f04  ubuntu-6.06.1-alternate-powerpc.iso
50e3912c555f98f7bca56b2a0200b205  ubuntu-6.06.1-desktop-amd64.iso
fb3af44c21f1f68cc25fda7edb8c1bd3  ubuntu-6.06.1-desktop-i386.iso
502911770ad173dbe82c698379ed7d11  ubuntu-6.06.1-desktop-powerpc.iso
8254b0f3696ed17c52a2cb59c9ebd2cc  ubuntu-6.06.1-server-amd64.iso
5ad76d8b380ab5be713e5daa9ea84475  ubuntu-6.06.1-server-i386.iso
6d1c3b5cb41661365b3db5cf12bb2836  ubuntu-6.06.1-server-powerpc.iso
2ccc1ec608040e6aac8913a016c31bed  ubuntu-6.06.1-server-sparc.iso  

To check multiple 5mdsums:

```
md5sum -c MD5SUMS
```

This will check any ubuntu*.iso in the current directory.

You will get an error message if the file does not exist..

So:
```
md5sum -c MD5SUMS 2>/dev/null
```
Redirects all those error messages.

I will add this to the how-to...

HTH

---

### Post by 655 on 2006-12-01
[COLOR="Navy"]**bodhi.zazen:**[/COLOR]

Thank you for more tips :wink: 
I had a more strange and complicated scenario in mind, but I will try the limits of this method for now.

---

### Post by buuntuu! on 2006-12-08
hi everyone, got a shell-newbie-question on 
"How to use md5sum and sha1sum files to verify integrity of downloaded iso images or files"

i downloaded the dapper-iso-file and now i'm stuck trying to check out the md5sum.

i followed the instructions (by the way: thanks to all you patient cracks out there who help us little hatchlings) step 1. to 3.
i managed to create the *Ubuntu.iso.md5sum* (how fascinating, a command line:KS ) 
both the *Ubuntu.iso.md5sum* and the* ubuntu-6.06.1-desktop-i386.iso* are on the desktop

but i get stuck at step 4. i'm not sure what to type!
this is my cli:
mat@mat-laptop:~/Desktop$ md5sum -c iso.md5
md5sum: iso.md5: No such file or directory

so i gave it another try:
mat@mat-laptop:~/Desktop$ md5sum -c ubuntu.6.06.1-desktop-i386.iso.md5sum
md5sum: ubuntu.6.06.1-desktop-i386.iso.md5sum: No such file or directory

and another one:
mat@mat-laptop:~/Desktop$ md5sum -c ubuntu-6.06.1-desktop-i386.md5
md5sum: ubuntu-6.06.1-desktop-i386.md5: No such file or directory

well, obviously i missed something...
damn bill for making me so gui-dependent;) 
can anyone help?
regards, buuntuu

---

### Post by bodhi.zazen on 2006-12-08
Your active or "working directory" needs to be that in which the .iso and md5 are located.

In your case that is ~/Desktop (~ is short hand for /home/user_name).

In the terminal:
```
cd ~/Desktop
md5sum -c Ubuntu.iso.md5sum
```Should do the trick !

I hope you got the Ubuntu.iso.md5sum from ubuntu.

Ubuntu distributes the md5sums as a file "MD5SUMS"

Here is the link: [MD5SUMS](http://ftp.ussg.iu.edu/linux/ubuntu-releases/6.06/MD5SUMS)

Open and save the file to you desktop as MD5SUMS .

Then :```
cd ~/Desktop
md5sum -c MD5SUMS
```

You will get some error messages about missing ubuntu iso's, but that is OK....

---

### Post by buuntuu! on 2006-12-08
thanks for the fast reply:D 
my md5sums were from where you indicated...
however, the reply remains the same:
md5sum: Ubuntu.iso.md5sum: No such file or directory

well, you can't understand everything right away.
in the end i did it the old-fashioned-way...good idea not deleting windows right away:rolleyes: still do need my carrying wheels!

---

### Post by bodhi.zazen on 2006-12-08
Can you post the output of:```
ls ~/Desktop
```

---

### Post by swegner on 2008-10-29
Thanks for the tutorial.  Note though, that you mention the command to check sha1 sums as
```
sha1 -c <sha1sum-file>
```when in fact it should be
```
sha1sum -c <sha1sum-file>
```I appears that you've corrected it in your examples, but I just wanted to point it out for anybody that missed it.  I'm testing on Ubuntu Intrepid 8.10.

---

### Post by bodhi.zazen on 2008-10-29
Thank you for pointing that out, I corrected the typo ;)

---

### Post by carolinason on 2008-11-09
I had always checked iso's by simply typing the command and then the name of the iso.
```
md5sum ubuntu.iso
```
This usually gave the correct value. I had no idea that this was not the correct method. Lately the md5sums have suffered anomalies like K3B could reflect the correct md5sum, when the command line did not. WHY?? I inquired here and found this thread. After reading this thread, I attempted to do this right.

I pasted the md5sum in a file and the name of the iso, like this
```
24ea1163ea6c9f5dae77de8c49ee7c03 ubuntu-8.10-desktop-i386.iso
```
And saved the file with the name ubuntu-8.10-desktop-i386.iso.md5sum as described. And saved it in a directory called iso_verify along with the iso. 

While in the iso_verify directory I run the command at the prompt and get an error
```
:~/iso_verify$ md5sum -c ubuntu-8.10-desktop-i386.iso.md5sum
md5sum: ubuntu-8.10-desktop-i386.iso.md5sum: no properly formatted MD5 checksum lines found
```

I tried naming the file with the file extension md5 and md5sum, since both are in the described in the verify section. This had the same result. 

In the Ubuntu mirrors, the name of the file is MD5SUM and it contains an * before the name of the iso, so I did that ```
24ea1163ea6c9f5dae77de8c49ee7c03 *ubuntu-8.10-desktop-i386.iso
``` and get the result ```
:~/iso_verify$ md5sum -c MD5SUMS 
ubuntu-8.10-desktop-i386.iso: FAILED
md5sum: WARNING: 1 of 1 computed checksum did NOT match
``` BUT K3B reflects the correct md5sum.

I can continue to use the K3B way to verify the md5sum, but would prefer to know what I am doing incorrectly in the command line and why my original way of doing this worked sometimes and sometimes not.



Thanks.

---

### Post by bodhi.zazen on 2008-11-10
The syntax is quite exact.

The name of the file containing the md5sum does not matter, BUT you must have exactly 2 spaces in the file

<md5sum><sp><sp>ubuntu-8.10-desktop-i386.iso

where <sp> = a space

A single space will not work.

---

### Post by carolinason on 2008-11-10
Thank you, the syntax was my problem. I needed two spaces between the hash and the name of the iso. 

I discovered that md5sum can be run directly on an iso and will generate it's hash.

The reason I was getting inconsistent hash's where due to a bad DIMM. I ran memtest and found out the bad news. Good news is, it's cheap to replace it.

Thank You, again!!!

---

### Post by kevdog on 2008-11-12
Bodhi

Great tutorial -- Its quite old but I just ran across it.  Ive seen some of the newer packages offered with md5, sha1, and now whirlpool hashes to verify the integrity.  Anyway you can add whirlpool capabilities?

The only way I know currently how to do this is to install from repository the md5deep package, and then use the command whirlpooldeep.  Do you know another way?

---

### Post by bodhi.zazen on 2008-11-12
> **kevdog said:**
> Bodhi

Great tutorial -- Its quite old but I just ran across it.  Ive seen some of the newer packages offered with md5, sha1, and now whirlpool hashes to verify the integrity.  Anyway you can add whirlpool capabilities?

The only way I know currently how to do this is to install from repository the md5deep package, and then use the command whirlpooldeep.  Do you know another way?

First time I heard of whirlpool, so I of course had to play with it.

Very cool :)

I am afraid the best I can do is give a link :(

[http://www.linux.com/feature/118616](http://www.linux.com/feature/118616)

---

### Post by ciscosurfer on 2008-11-12
> **bodhi.zazen said:**
> First time I heard of whirlpool, so I of course had to play with it.

Very cool :)

I am afraid the best I can do is give a link :(

[http://www.linux.com/feature/118616](http://www.linux.com/feature/118616)And did you happen to catch the username in the example given when the author begins describing how to generate hashes recursively?

---

### Post by bodhi.zazen on 2008-11-12
> **ciscosurfer said:**
> And did you happen to catch the username in the example given when the author begins describing how to generate hashes recursively?
:lolflag: No I missed that, just seemed so ... familiar ?

---

### Post by kevdog on 2008-11-12
Hmm, for a minute I confused bodhi as being the author of md5deep :lolflag:

---

