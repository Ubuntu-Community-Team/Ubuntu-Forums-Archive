---
title: "Setting up gcc/g++"
date: 2007-01-29
forum: Programming Talk
---

### Post by Mygly on 2007-01-29
Hey all, I'm pretty new to the linux world in general, although I had dapper installed a few months ago, and before that mandriva and mandrake at a point before that, but I still know relatively little about linux. In my programming lab at college the machines we use are running debian and when I compile my programs I can use the g++ command, it seems regardless of what directory I am in. However I have tried to set up a Ubuntu partition to emulate this and it doesn't seem like it's working. I tried to use the g++ command but it said it was an unknown command or something along those lines. Anyone know what the problem might be? (as a side question I can't seem to find openSSH anywhere on the system, although it says it's installed). I thank you guys for any help you can give me.

---

### Post by phossal on 2007-01-29
Have you run:
```
sudo apt-get install build-essential
```

---

### Post by Mygly on 2007-01-29
Just that command exactly? or in correspondence to something else? To both, the answer is no. To be honest, I'm not sure what that means exactly. Wouldn't the command have to reference g++ in some way? Thanks for the reply.

---

### Post by phossal on 2007-01-29
Run that command exactly as it is. Then report back. ;)

[edit] This command installs the various compilers and resolves some dependencies. The only caveat is that you may have to enable the correct repositories to have access to the package. Just *try* running the command and we'll solve any problems as they arise.

---

### Post by Mygly on 2007-01-29
After running the command all seems well. Although I have to get the files from the computer science department servers to check and make sure. So it looks like my next task is finding openssh, and an ftp client if openssh doesn't have one.

---

### Post by Fasga on 2007-01-29
```
sudo apt-get install openssh-server
```
OR
```
sudo apt-get install openssh-client
```
AND
```
sudo apt-get install gftp
```

Edit: Read the post.  Try 'locate openssh'.

---

### Post by Mygly on 2007-01-30
Alright, everything seems to be going well now except one thing, after I compile how do I run the program? In the lab if I after I compile, i just type in the name of the file and then hit enter/return and it will run. What do i have to do here?

---

### Post by tux123 on 2007-01-30
Try to launch it with the full path to the file. For example you just can put a "./" in front of the filename and the bash will probably find it (the command will then looks like "./myapp" or "./a.out" if you haven't specified any name).

PS: Normally the bash looks in all directories listened in the $PATH environment variable. For security reasons the current directory isn't included there, but you can append it if you want (for example in your ~/.bashrc).

Regards
Christoph

---

### Post by wonderboy07 on 2007-02-01
> **phossal said:**
> Run that command exactly as it is. Then report back. ;)

[edit] This command installs the various compilers and resolves some dependencies. The only caveat is that you may have to enable the correct repositories to have access to the package. Just *try* running the command and we'll solve any problems as they arise.

Hi there,
I've been struggling all day to try to get my system to allow me to compile a script from sourceforge. It's coming up with errors trying to locate 'cc1plus' (and possibly an execvp?) and what I've been able to glean off of google is that this is caused because of g++/c++ not being present on the system. 

I've tried running apt-get:
========
sudo apt-get install build-essential

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate
========

I've even tried it with the '--force-yes' argument but to no avail, it still gives me the same message. Does anyone by chance have any suggestions as to what I can do to get around this? I've been unable to locate anything of more interest in Synaptics either. 

Thanks for the help!

-A

---

### Post by lnostdal on 2007-02-01
paste the contents of /etc/apt/sources.list

edit: can you install anything at all at the moment? ..  i believe build-essential is part of the set of packages that should be available as default

---

### Post by phossal on 2007-02-01
I think Inostdal is correctly assuming you're unable to get the package because you have not enabled the repositories. Visit this site: [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)  One of the many things you'll learn is how to modify your sources.list file correctly.

---

