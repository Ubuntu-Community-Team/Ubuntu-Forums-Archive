---
title: "[SOLVED] Unable to compile C file...."
date: 2007-08-22
forum: Programming Talk
---

### Post by amirseg on 2007-08-22
Hi,
I have just installed Ubuntu 7.04, added all the updates, but when I am trying to compile a C file, I always get:
'Draw.c:1:19: error: stdio.h: No such file or directory'

I looked in the forums, and saw all kind of suggestions. I am having a problem with 'http://il.archive.ubuntu.com/ubuntu/pool/main/g/g libc/libc6-dev_2.5-0ubuntu14_amd64.deb which I get an' MD5Sum mismatch on it. I tryed downloading the file from the link, and then in the 'package controller' when installing it I get 'dpkg: error processing /home/amirseg/Desktop/libc6-dev_2.5-Oubuntu14_amd64.deb (--install):
corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)'.
 I tryed doing all king of removing-installing as I was suggested here: 
[http://ubuntuforums.org/showthread.php?t=531555](http://ubuntuforums.org/showthread.php?t=531555) (at the bottum)

and I got: (when running gksudo aptitude install build-essential)

gksudo aptitude install build-essential
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Reading extended state information 
Initializing package states... Done
Building tag database... Done 
The following NEW packages will be automatically installed:
dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev 
The following NEW packages will be installed:
build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev 
0 packages upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 2459kB/7062kB of archives. After unpacking 29.0MB will be used.
Do you want to continue? [Y/n/?] Y


And it just stay like this

what to do?


Thanks
Amir

---

### Post by LaRoza on 2007-08-22
Did you press enter?

---

### Post by amirseg on 2007-08-22
> **LaRoza said:**
> Did you press enter?

:) I guess it is fair to ask it by my message, but yes, I did pressed enter after it and it did nothing...

---

### Post by LaRoza on 2007-08-22
> **amirseg said:**
> :) I guess it is fair to ask it by my message, but yes, I did pressed enter after it and it did nothing...

You'd be surpised :D.

Try it again, maybe using "apt-get", just to see if that works.

---

### Post by Soybean on 2007-08-22
Alternately, try "sudo" instead of "gksudo". For command-line tools like aptitude, you're supposed to use sudo, while gksudo is for GUI tools like Synaptic (oh, you could also try using Synaptic to install build-essential :) ).

---

### Post by amirseg on 2007-08-22
Hi,
I tried all kind ofcombinations as you suggested, and the onlt one worked was *gksudo aptitude install build-essential*.

I got a message:
[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following NEW packages will be automatically installed:
  g++ g++-4.1 libc6-dev libstdc++6-4.1-dev 
The following NEW packages will be installed:
  build-essential g++ g++-4.1 libc6-dev libstdc++6-4.1-dev 
0 packages upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 2459kB/6915kB of archives. After unpacking 28.3MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/main libc6-dev 2.5-0ubuntu14 [2459kB]
Fetched 2459kB in 2m45s (14.9kB/s)                                              
E: Failed to fetch [http://il.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.5-0ubuntu14_amd64.deb:](http://il.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.5-0ubuntu14_amd64.deb:) MD5Sum mismatch
[/I]

Which I guess that the froblem is the last line. I got no idea what is a MD5Sum mismatch, but I really want to sort it over.

Any idea?

---

### Post by LaRoza on 2007-08-22
> **amirseg said:**
> Hi,
I tried all kind ofcombinations as you suggested, and the onlt one worked was *gksudo aptitude install build-essential*.

I got a message:
[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following NEW packages will be automatically installed:
  g++ g++-4.1 libc6-dev libstdc++6-4.1-dev 
The following NEW packages will be installed:
  build-essential g++ g++-4.1 libc6-dev libstdc++6-4.1-dev 
0 packages upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 2459kB/6915kB of archives. After unpacking 28.3MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) feisty/main libc6-dev 2.5-0ubuntu14 [2459kB]
Fetched 2459kB in 2m45s (14.9kB/s)                                              
E: Failed to fetch [http://il.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.5-0ubuntu14_amd64.deb:](http://il.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.5-0ubuntu14_amd64.deb:) MD5Sum mismatch
[/I]

Which I guess that the froblem is the last line. I got no idea what is a MD5Sum mismatch, but I really want to sort it over.

Any idea?

Add the ubuntu CD, if you have one, to Synaptic,  and then install it from that.

---

### Post by amirseg on 2007-08-22
> **LaRoza said:**
> Add the ubuntu CD, if you have one, to Synaptic,  and then install it from that.

Sorry, but I don't understand you.
I got the Ubuntu CD which I installed from. 
What do you mean by adding it to the Synaptic? how? what to install?

Thanks
Amir

---

### Post by LaRoza on 2007-08-22
> **amirseg said:**
> Sorry, but I don't understand you.
I got the Ubuntu CD which I installed from. 
What do you mean by adding it to the Synaptic? how? what to install?

Thanks
Amir

Synaptic has sources which it uses to get the applications. You can use a disk as a source, try running the command with the disk in the drive.

To add, go to System->Administration->Synaptic Package Manager

Look for the tab for adding a cd.

When it wants the cd, it will say "Please insert Ubuntu 7.04 blah... into the disk drive", and then go from there.

---

### Post by amirseg on 2007-08-22
I did as you said, he scanned the CD, the Mounted it, unmounted it, asked if I want to add another CD, I said 'No', and it went back to the Synaptic. I tried to install build-essential from there , so he daid he need to install g++, g++-4.1, libc6-dev, libstdc6-4.1dev as well, I said OK, he marked them, and when downloading he said he cant download from the server, and then said "W: faild to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070418)]/pool/main/g/glibc/libc6-dev_2.5-0ubuntu14_amd64.deb
   MD5Sum mismatch"

So.... what else can I do?

---

### Post by amirseg on 2007-08-22
LaRoZa,

Do you got anything else I ca try or do you know where else I can ask?

---

### Post by LaRoza on 2007-08-22
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=build-essential&version=feisty&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=build-essential&version=feisty&arch=i386)

[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=build-essential&version=feisty&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=build-essential&version=feisty&arch=i386)

Try:

```

sudo aptitude install libc6-dev

```

This will give you the headers (stdio.h included)

---

### Post by amirseg on 2007-08-22
I tryed to get into *usr/share/build-essential/essential-packages-list* 
pressed the amd64 link, choose one of the link, and when he downloaded the additional package files I got the messgae *Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070418)]/pool/main/g/glibc/libc6-dev_2.5-0ubuntu14_amd64.deb MD5Sum mismatch*.

Then I tried to install tehr dependencies one-by-one, and when I tried to install the g++ I got the message *Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070418)]/pool/main/g/glibc/libc6-dev_2.5-0ubuntu14_amd64.deb MD5Sum mismatch*

I guess the proglem I am having is with libc6-dev_2.5-0ubuntu14_amd64.deb (for now)

I tryed downloading it from [http://il.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.5-0ubuntu14_amd64.deb](http://il.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.5-0ubuntu14_amd64.deb)
and saved it on my computer, opened it with archive manager, and I saw 3 files:
control.tar.gz
data.tar.gz
debian-binary

I could open control.tar.gz and saw some files inside, but when trying to open data.tar.gz I got an error saying:
[I]tar: Skipping to next header

gzip: stdin: invalid compressed data--crc error

gzip: stdin: invalid compressed data--length error
tar: Child returned status 1
tar: Error exit delayed from previous errors[/I]

What can I do?


*I tryed to think what could be diffrent in my computer from other computers out there and I think that the only thing is that I have a Hebrew package installed. Does that matter?

Amir

---

### Post by LaRoza on 2007-08-22
> **amirseg said:**
> 
*I tryed to think what could be diffrent in my computer from other computers out there and I think that the only thing is that I have a Hebrew package installed. Does that matter?

Amir

It may be because it is 64 bit. I have heard of weird errors with 64 bit apps. Sorry I can't help. You might want to post something in another sub forum. Since I have blocked viewing certain forums, I don't know what the exact name of the 64 bit forum is, but I am sure it is there.

---

### Post by amirseg on 2007-08-23
> **LaRoza said:**
> It may be because it is 64 bit. I have heard of weird errors with 64 bit apps. Sorry I can't help. You might want to post something in another sub forum. Since I have blocked viewing certain forums, I don't know what the exact name of the 64 bit forum is, but I am sure it is there.

Do you think installing 32bit will solve it?

---

### Post by amirseg on 2007-08-23
> **LaRoza said:**
> It may be because it is 64 bit. I have heard of weird errors with 64 bit apps. Sorry I can't help. You might want to post something in another sub forum. Since I have blocked viewing certain forums, I don't know what the exact name of the 64 bit forum is, but I am sure it is there.

do you thinks switching to 32 bit will solve it?

---

### Post by fct on 2007-08-23
It's working absolutely fine on 64 bits, you don't need to switch to 32 bits.

The md5sum problem means the file was not correctly downloaded or the file in your repository has errors. Try changing the repositories to other equivalent ones, like us.archive.ubuntu.com or similar.

---

### Post by amirseg on 2007-08-23
Can you explain how to do it?

Thanks...
Amir

---

### Post by anubhavrocks on 2007-08-23
can you try 
```
sudo apt-get update && sudo apt-get upgrade 
```

if this command suggests you to upgrade packages please upgrade,and then try to install build-essential.

---

### Post by amirseg on 2007-08-23
Hi,
First of all, thanks a lot for yur help, its important for newbs like me to see that ppl are more then welcome to help.
Second, I solved my problem with [http://ubuntuforums.org/showthread.php?p=2585522#post2585522](http://ubuntuforums.org/showthread.php?p=2585522#post2585522)


bye :)

---

### Post by LaRoza on 2007-08-23
Glad everything worked out :D.

(Mark your thread as SOLVED, if it is)

---

