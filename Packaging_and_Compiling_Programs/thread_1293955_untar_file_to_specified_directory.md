---
title: "untar file to specified directory"
date: 2009-10-17
forum: Packaging and Compiling Programs
---

### Post by jon zendatta on 2009-10-17
hell0
I am building a file that first requires dependencies to reside in Src directory. Currently they are tarred and are residing in Desktop. So I tried this!
[PHP]cd ~/Desktop
tar -xzvf file.tar.gz -C /usr/src/[/PHP]

which threw an error!

So is this the correct command?

[PHP]tar -C /usr/src/ -xzvf file.tar.gz[/PHP]

cheers for any help.

---

### Post by sisco311 on 2009-10-17
> **jon zendatta said:**
> 
So is this the correct command?

[PHP]tar -C /usr/src/ -xzvf file.tar.gz[/PHP]

cheers for any help.

yep

---

### Post by jon zendatta on 2009-10-17
cheers for that, I'm bit cautious with this.Translate > I don't really understand it. all good now.

---

### Post by sisco311 on 2009-10-17
oh, add your user to the src group. /usr/src is owned by root.src and the direcoty has 2775 (drwxrwsr-x [setguid]("http://en.wikipedia.org/wiki/Setuid#setgid_on_directories")) permissions.

---

### Post by Bachstelze on 2009-10-17
The correct command was the first one. Make sure you have permission to write to /usr/src, either by running the command with sudo or by adding yourself to the src group.

---

### Post by jon zendatta on 2009-10-17
true:KS

---

### Post by jon zendatta on 2009-10-17
0k you said my first command was correct, so i used it with sudo. then when i try 
[PHP]cd file[/PHP]
it says no file or directory? Any enlightenment please. I have to got out for 2hours so I'll look later. thank you

---

### Post by Bachstelze on 2009-10-17
> **jon zendatta said:**
> 0k you said my first command was correct, so i used it with sudo. then when i try 
[PHP]cd file[/PHP]
it says no file or directory? Any enlightenment please. I have to got out for 2hours so I'll look later. thank you

You said you wanted to extract it into /usr/src, so that's where you need to look. ;)

---

### Post by jon zendatta on 2009-10-18
yes you are correct, it now has a new home in /usr/src/
thank you:KS

---

### Post by jon zendatta on 2009-10-18
0k. just one more question please? I was able to check the file existed in desired directory using
[PHP]ls -la /usr/src[/PHP]
then change to that directory like so:
[PHP]cd /usr/src[/PHP]
So now what command do I use to cd to that specific file so i can ./configure && make install

thanks for your patience:KS

---

### Post by jon zendatta on 2009-10-18
forget the last question thanks, I have files installed :KS

---

