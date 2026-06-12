---
title: "how to install programs from source code"
date: 2016-11-19
forum: New to Ubuntu
---

### Post by juntjoo2 on 2016-11-19
so I'm trying to install oneDrive from here:

[https://github.com/skilion/onedrive](https://github.com/skilion/onedrive)

and I don't know what I'm doing.  I figured out how to change the directory then tried the instructions from the page and got:

"ben@Hal:~/Downloads$ makemake: *** No targets specified and no makefile found.  Stop.
ben@Hal:~/Downloads$ sudo make install
[sudo] password for ben: 
make: *** No rule to make target 'install'.  Stop."

So what do I do next? Thanks

if anyone can recommend a page or something I should get familiar with, preferably something concise as possible so I don't have to come here for every step of the way to getting comfortable with this that would be good.  I just don't have a clue what I'm doing such that looking through the forums I'm lost.  Thanks

---

### Post by irv on 2016-11-19
I found this, but did not try it. [https://www.maketecheasier.com/sync-onedrive-linux/]("https://www.maketecheasier.com/sync-onedrive-linux/")

EDIT: Maybe I should have said, I have files on onedrive but just get to them from Internet via a browser by going to my onedrive page and sign in. I use dropbox for Linux it works much better. I also copied my onedrive files over to an SD card for backup.

---

### Post by yetimon_64 on 2016-11-19
> **juntjoo2 said:**
> ...
ben@Hal:**~/Downloads**$ sudo make install
[sudo] password for ben: 
make: *** No rule to make target 'install'.  Stop."
... 

You are trying to use the make command in the actual Downloads folder, you need to "cd" into the folder containing the makefile itself to run the make command. Note how I have bolded the path you are using to show you where you are operating from above. 

Use the GUI (file manager) to find the makefile and then cd to the path containing it in the terminal to build the program.

**Edit: **if you downloaded the program as a "zip file" you will need to extract it first. You can do so in the GUI by right clicking the zip file then choosing "Extract Here" you will then have a folder called "onedrive-master" that is the folder you need to "cd" into that contains the makefile.
eg. ```
cd ~/Downloads/onedrive-master
``` then,
```
make
``` and finally,
```
sudo make install
```

Take note of the Ubuntu dependencies in the README.md file first before trying to install.

---

### Post by juntjoo2 on 2016-11-19
thank you.  this is what I got:

ben@Hal:~/Downloads/onedrive-master$ make
dmd -O -release -inline -boundscheck=off -ofonedrive -L-lcurl -L-lsqlite3 -L-ldl src/config.d src/itemdb.d src/log.d src/main.d src/monitor.d src/onedrive.d src/sqlite.d src/sync.d src/upload.d src/util.d
make: dmd: Command not found
Makefile:19: recipe for target 'onedrive' failed
make: *** [onedrive] Error 127


what are dependencies?

---

### Post by deadflowr on 2016-11-19
Personally, I recommend installing and using checkinstall for ease of management.
See:[https://help.ubuntu.com/community/CheckInstall]("https://help.ubuntu.com/community/CheckInstall")

---

### Post by juntjoo2 on 2016-11-19
> **deadflowr said:**
> Personally, I recommend installing and using checkinstall for ease of management.
See:[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

thank you but I don't know enough to consider what you're suggesting.  I haven't a clue why I'm having trouble installing this program in the first place

---

### Post by #&amp;thj^% on 2016-11-19
> **deadflowr said:**
> Personally, I recommend installing and using checkinstall for ease of management.
See:[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

+100
And could not agree more.:D
Just my 2 cents worth.

---

### Post by oldos2er on 2016-11-19
> **juntjoo2 said:**
> what are dependencies?

They are listed in the README.md file that yetimon_64 mentioned, [https://github.com/skilion/onedrive/blob/master/README.md](https://github.com/skilion/onedrive/blob/master/README.md)
Dependencies are files or programs needed by other programs in order to compile correctly, and give you the full functionality of the program.

I would add that compiling code is usually the most difficult way for someone new to Linux to install a program. Have you read [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo) and [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware) ?

Edit: I amended your thread title a bit to better reflect your question.

---

### Post by yetimon_64 on 2016-11-19
> **juntjoo2 said:**
> thank you.  this is what I got:

ben@Hal:~/Downloads/onedrive-master$ make
dmd -O -release -inline -boundscheck=off -ofonedrive -L-lcurl -L-lsqlite3 -L-ldl src/config.d src/itemdb.d src/log.d src/main.d src/monitor.d src/onedrive.d src/sqlite.d src/sync.d src/upload.d src/util.d
make: dmd: Command not found
Makefile:19: recipe for target 'onedrive' failed
make: *** [onedrive] Error 127


what are dependencies?
Read the Readme.md file first for the Ubuntu dependencies, you will need to run the commands there first and make the dmd program BEFORE running the main installation. I haven't actually installed onedrive here, I just downloaded it and read the "Readme.md" file to see what needs to be done.

As a general guide always read the Readme file provided when building from source. There are several commands to run first in there for you to work through before doing the main install in this case.

I also agree with deadflowr's post, checkinstall is a good idea to use with source code installs.
> 
Personally, I recommend installing and using checkinstall for ease of management.
See:[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by juntjoo2 on 2016-11-19
> **1fallen said:**
> +100
And could not agree more.:D
Just my 2 cents worth.


I'm.not.sure.I.need.that.more.than.I.need.a.clue.as.to.how.this.system.works.or.why.my.space.bar.suddenly.doesn't.work.when.replying.


   unless for some reason I skip down the window a bit.  wth?

> **yetimon_64 said:**
> Read the Readme.md file first for the Ubuntu dependencies, you will need to run the commands there first and make the dmd program BEFORE running the main installation. I haven't actually installed onedrive here, I just downloaded it and read the "Readme.md" file to see what needs to be done.

As a general guide always read the Readme file provided when building from source. There are several commands to run first in there for you to work through before doing the main install in this case.

I also agree with deadflowr's post, checkinstall is a good idea to use with source code installs.


thank.you.

I don't know what dependencies are or anything else in these files lol.  I'm less than a newb.

> **yetimon_64 said:**
> Read the Readme.md file first for the Ubuntu dependencies, you will need to run the commands there first and make the dmd program BEFORE running the main installation. I haven't actually installed onedrive here, I just downloaded it and read the "Readme.md" file to see what needs to be done.

As a general guide always read the Readme file provided when building from source. There are several commands to run first in there for you to work through before doing the main install in this case.

I also agree with deadflowr's post, checkinstall is a good idea to use with source code installs.



sudo apt-get install libcurl-dev
sudo apt-get install libsqlite3-dev
sudo wget [http://master.dl.sourceforge.net/project/d-apt/files/d-apt.list](http://master.dl.sourceforge.net/project/d-apt/files/d-apt.list) -O /etc/apt/sources.list.d/d-apt.list
wget -qO - [http://dlang.org/d-keyring.gpg](http://dlang.org/d-keyring.gpg) | sudo apt-key add -
sudo apt-get update && sudo apt-get install dmd-bin


so type these in? I clicked the links for these files and looks like you're supposed to download them? if I type sudo apt-get install libcurl-dev what does that do? does that go on the internet and find this program or something?

---

### Post by yetimon_64 on 2016-11-19
> **juntjoo2 said:**
> thank.you.

I don't know what dependencies are or anything else in these files lol.  I'm less than a newb.

You're welcome, and don't worry about being new. All of us here were at that stage at one time or another, plenty of reading and "trial and error" will iron it all out in the long run if you persist. It does get easier :-).

> **juntjoo2 said:**
> sudo apt-get install libcurl-dev
sudo apt-get install libsqlite3-dev
sudo wget [http://master.dl.sourceforge.net/project/d-apt/files/d-apt.list](http://master.dl.sourceforge.net/project/d-apt/files/d-apt.list) -O /etc/apt/sources.list.d/d-apt.list
wget -qO - [http://dlang.org/d-keyring.gpg](http://dlang.org/d-keyring.gpg) | sudo apt-key add -
sudo apt-get update && sudo apt-get install dmd-bin


so type these in? I clicked the links for these files and looks like you're supposed to download them? if I type sudo apt-get install libcurl-dev what does that do? does that go on the internet and find this program or something?

Yes just follow those commands, they will automatically download and set up what is needed. You may possibly have to install wget first (not sure if it is standard). If the wget command gives an error "no such command" use "sudo apt-get install wget" and try again.

---

### Post by juntjoo2 on 2016-11-19
so I tried this:

ben@Hal:~/Downloads/onedrive-master$ sudo apt-get install libcurl-dev
[sudo] password for ben: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libcurl-dev is a virtual package provided by:
  libcurl4-openssl-dev 7.47.0-1ubuntu2.2
  libcurl4-nss-dev 7.47.0-1ubuntu2.2
  libcurl4-gnutls-dev 7.47.0-1ubuntu2.2
You should explicitly select one to install.


E: Package 'libcurl-dev' has no installation candidate

And I don't know what this means.  what do I do now?

---

### Post by oldos2er on 2016-11-19
> so type these in? Better to copy and paste, less chance for mistakes.

---

### Post by juntjoo2 on 2016-11-19
what is libcurl? is it already somewhere in my ubuntu installation or did I grab it from the internet?

---

### Post by yetimon_64 on 2016-11-19
I would personally try and install the libcurl4-gnutls-dev package and try again.
> 
 Better to copy and paste, less chance for mistakes. 				
+1

---

### Post by juntjoo2 on 2016-11-19
> **oldos2er said:**
> They are listed in the README.md file that yetimon_64 mentioned, [https://github.com/skilion/onedrive/blob/master/README.md](https://github.com/skilion/onedrive/blob/master/README.md)
Dependencies are files or programs needed by other programs in order to compile correctly, and give you the full functionality of the program.

I would add that compiling code is usually the most difficult way for someone new to Linux to install a program. Have you read [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo) and [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware) ?

Edit: I amended your thread title a bit to better reflect your question.


Thank you.  I will check that thread out.  I just created another thread which maybe you'd want to delete if your suggestion here should suffice on getting me going on this.  Thanks

thanks.  so "sudo apt-get" tells it to look on the computer and the internet for a file or just the internet? or are these files in my ubuntu installation or this oneDrive app I downloaded?  

and how do I select this "installation candidate"? 

ben@Hal:~/Downloads/onedrive-master$ sudo apt-get install libcurl-devReading package lists... Done
Building dependency tree       
Reading state information... Done
Package libcurl-dev is a virtual package provided by:
  libcurl4-openssl-dev 7.47.0-1ubuntu2.2
  libcurl4-nss-dev 7.47.0-1ubuntu2.2
  libcurl4-gnutls-dev 7.47.0-1ubuntu2.2

You should explicitly select one to install.


E: Package 'libcurl-dev' has no installation candidate

---

### Post by oldos2er on 2016-11-19
That means there is no package exactly named libcurl-dev. Let's try ```
sudo apt install libcurl4-gnutls-dev
```

---

### Post by juntjoo2 on 2016-11-20
thank you. I will try that out. let me ask, where is the computer looking for this file?  is this in the download or my computer or in some online repository or something? just trying to understand what's going on in front of me. thanks

it worked I guess as I didn't get any errors.  thanks. Now what?  In general when starting a program without a gui, do you do it from from the command terminal?  do you have to navigate to the folder and execute a particular file or something?  I'm almost there!

"The Ubuntu repositories contain thousands of packages, and with 3rd party repositories you can get even more. However, sometimes you might want to compile packages from source"

What is "source"? And is a "package" a working program? What's compiling? You know, years ago I took a Java class. I think the fact that the book was so fat I quit. So source is the raw written code and compiling is putting it together into an executable file you can then run? Did I get that right? And some of these "packages" out there are corrupt so you gotta get the source code and recompile a working package?

---

### Post by oldos2er on 2016-11-20
I'll try to answer a couple of your questions. > where is the computer looking for this file? When you use an *apt install <package>* command, the first place apt looks is to Ubuntu's online repositories. You can think of them as web servers. Your system keeps lists of these servers so it knows where to "look," the main one is the file /etc/apt/sources.list. Note that "sources" here does not refer to source code. Much more info on repositories and the APT system at 

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

> So source is the raw written code and compiling is putting it together  into an executable file you can then run? Did I get that right? That's right. As I said before this is generally the *most difficult* way to install a program because you must do all the little fiddly parts yourself. And no one who's just starting with Linux ever knows what all those fiddly parts are. I sure didn't.

> And some of these "packages" out there are corrupt Well, no. You would compile a program because it isn't in the repositories, or because you want a newer version of it, or for some other personal reason.

> it worked I guess as I didn't get any errors.  thanks. Now what?  Going back to the README.md, next we install the SQLite3 dev package, so run ```
sudo apt-get install libsqlite3-dev
```

---

### Post by juntjoo2 on 2016-11-20
Thank you a lot. I finished installing everything but I don't know what to do with the available commands. ... wait, found the executable... Nice. Looks like it's working...

---

