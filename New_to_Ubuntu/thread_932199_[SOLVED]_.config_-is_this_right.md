---
title: "[SOLVED] ./config -is this right?"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by bestseclub on 2008-09-28
Itsa me again.
Okay,ive been trying to make this work but i just cant:
I use the cd command to change my directory.Then i use the ./configure to compile the program i placed in that folder.Im shure theres a configure.ac in the folder,but when i use that "./configure" command,it says file or directory does not exist.
I know im doing something stupid.Please help.

---

### Post by Naiki Muliaina on 2008-09-28
To check your in the right directory, navigate to it then type:

```
ls
```

This will list the contents of that folder. If your configure.ac is not there, your in the wrong place :)

---

### Post by jemate18 on 2008-09-28
> **bestseclub said:**
> Itsa me again.
Okay,ive been trying to make this work but i just cant:
I use the cd command to change my directory.Then i use the ./configure to compile the program i placed in that folder.Im shure theres a configure.ac in the folder,but when i use that "./configure" command,it says file or directory does not exist.
I know im doing something stupid.Please help.

can you tell me the folder in which you cd?

what is the program you put in that directory(which you have cd'd)

---

### Post by davidryder on 2008-09-28
When you are at the command prompt you can enter the first few letters of a program and press TAB twice to display all files and directories starting with those letters. 

For instance,

```
./con [TAB] [TAB]
``` will do one of two things. If there is only one entry starting with _con_ it will automatically fill it in. If there is more than one entry you can press TAB again and it will display all entries starting with _con_. 

The error you are getting is due to the file you are attempting to run not existing.

---

### Post by tonybaqain on 2008-09-28
> **bestseclub said:**
> Itsa me again.
Okay,ive been trying to make this work but i just cant:
I use the cd command to change my directory.Then i use the ./configure to compile the program i placed in that folder.Im shure theres a configure.ac in the folder,but when i use that "./configure" command,it says file or directory does not exist.
I know im doing something stupid.Please help.

please give us the name of the application you are trying to compile, and please paste back the response from this command : 

```
sudo dpkg -l | grep -E 'auto(make|conf|gen)'
```

thanks.

---

### Post by bestseclub on 2008-09-28
This is very strange.
The ls shows the "configure.ac".The program is Aqualung.When i type cd /home/bestseclub/Desktop/aqualung and then ./configure it says "bash: ./configure: No such file or directory".

---

### Post by steveneddy on 2008-09-28
aqualung is in the repos.

open a new terminal and type

```
sudo apt-get install aqualung
```

Always look in Synaptic first to see if in there. If the program you want to install is in there, it's much easier to get your software from a repository.

Go to

System --> Administration --> Synaptic Package Manager

Unlike Windows, you don't have to go to the website, download a piece if software and install it. Just look in your own repo, which the list is in Synaptic, and DL it from there. Much easier.

It will be updated automatically that way.

---

### Post by davidryder on 2008-09-28
The command you should be running is 

```
./configure.ac
```

---

### Post by bestseclub on 2008-09-28
And if for some reason i cant use repos?Like when my Ubuntu PC doesnt have working internet? >.<
PS.Havent tried ./configure.ac,though.

---

### Post by steveneddy on 2008-09-28
No internet?

Well - OK.

---

### Post by bestseclub on 2008-09-28
Sounds kinda weird,i know.Anyway,problems with the connection,so im stuck with mobile internet.
Anyway,i tried ./configure.ac and now it says "Permission denied".This is my first compilation,so i really wanna get this done.

---

### Post by steveneddy on 2008-09-28
> **bestseclub said:**
> Sounds kinda weird,i know.Anyway,problems with the connection,so im stuck with mobile internet.
Anyway,i tried ./configure.ac and now it says "Permission denied".This is my first compilation,so i really wanna get this done.

```
sudo ./configure.ac 
```

before you do that, where is this folder located?

Desktop or your /home folder?

FYI - I think there is a DVD out there that you can use in place of an online connection.

---

### Post by bestseclub on 2008-09-28
sudo?Okay ill try again.The folder is located on my Desktop.
PS.What DVD?

---

### Post by bestseclub on 2008-09-28
Ok,i tried "sudo ./configure.ac".It says "command not found".Are you shure the syntax is right?

---

### Post by steveneddy on 2008-09-28
> **bestseclub said:**
> sudo?Okay ill try again.The folder is located on my Desktop.
PS.What DVD?

You, um, need an internet connection, preferably a fast one, but it can be done.

There may be someone with these DVD's for sale online, also.

Anyway, here's the link for making a REPO DVD set.

[http://blog.entner.net/2006/08/16/make-ubuntu-dvds-including-everything/](http://blog.entner.net/2006/08/16/make-ubuntu-dvds-including-everything/)

I'm adding this to my sig.

Here's a store for the DVD's with all repos included.

[http://www.thelinuxstore.org/index.php?main_page=product_info&cPath=41_47&products_id=1612&zenid=ltcdgrr9781771uuba7g2s3445](http://www.thelinuxstore.org/index.php?main_page=product_info&cPath=41_47&products_id=1612&zenid=ltcdgrr9781771uuba7g2s3445)

---

### Post by davidryder on 2008-09-28
What does ```
ls configure*
``` return?

---

### Post by bestseclub on 2008-09-28
What do you mean exactly?ls returns all the files in the folder."configure.ac" also.
Edited: ls configure*.Sorry.Ill check.

---

### Post by steveneddy on 2008-09-28
> **bestseclub said:**
> Ok,i tried "sudo ./configure.ac".It says "command not found".Are you shure the syntax is right?

If you are in the folder where ./configure.ac is, and you are denied permission, 

```
sudo ./configure.ac
```

should do the trick.

If there is a Read Me file in the folder you DLed, read that. It may tell you what to do.

I would get my internet connection going and get it from the repos myself.

[COLOR=Blue]**If you don't have an internet connection, how are you posting online?**[/COLOR]

---

### Post by bestseclub on 2008-09-28
ls configure* returns "configure.ac".Hmm.
PS.Im using mobile,very very slow gprs internet.

---

### Post by davidryder on 2008-09-28
Sounds like you should probably take a look at the readme...

---

### Post by steveneddy on 2008-09-28
Just a suggestion.

Would it be easier to take the PC to a friend's home with an internet connection or a public place with internet and just get it from the repos there?

You could do an update while you are there, also.

Just my .02 .

This may not be the answer you were looking for.

What does the Read Me file say about installing this software?

---

### Post by steveneddy on 2008-09-28
I DLed the aqualung application and looked in the folder.

Clicking the Install icon in the folder brings up a read me that states:

```
./configure
make
sudo make install
```

is the recommended method of installation.

[COLOR=Red]**Notice that it is not ./configure.ac**[/COLOR]

Installing from source is the same almost all of the time.

I also noted from the website that aqualung has lots of dependencies that are required to run the program.

Without an internet connection, you would be in dependency hell, so to speak.

You may just need to get an internet connection and get it from the repos.

---

### Post by bestseclub on 2008-09-28
Lol.Hope not all Linux apps are are so hard to compile.Anyways,lets say this problem is solved..

---

### Post by steveneddy on 2008-09-28
I hope this helped.

It is my opinion that if the application is offered from the repos, it is safer and better to get it off of the repos.

It will, most of the time, run better and you can get it automatically updated when the package is updated.

Once I stopped installing software from out of the repos, my system became much more stable.

---

### Post by bestseclub on 2008-09-28
Hmm,i should buy that ADSL modems.I wonder what they cost.

---

### Post by steveneddy on 2008-09-28
> **bestseclub said:**
> Hmm,i should buy that ADSL modems.I wonder what they cost.

Usually the modem comes for free with the service.

I use AT&T DSL at home and they sent me a package with a modem and a bunch of filters.

So, you have DSL in your home already?

---

