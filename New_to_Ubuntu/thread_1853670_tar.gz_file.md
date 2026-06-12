---
title: "tar.gz file"
date: 2011-10-02
forum: New to Ubuntu
---

### Post by ekz13 on 2011-10-02
ready to pull my hair out on this one and I'm sure it's a simple answer...but can't seem to find it.

I d/l'd a tar.gz file for a program... how do i install it. I'd like to have a gui install if possible (through the package center or whatnot) but will use term if i have too..

I tried to unzip and do a 

sudo apt-get install "name" 

and it errors out.

any help please??

---

### Post by Rex Bouwense on 2011-10-02
Each tar.gz file or tar ball should come with a install read me file.  Check it out.  There is also a wealth of information on the net and the forums just search install a tar.gz file + your version of Ubuntu.

---

### Post by alphacrucis2 on 2011-10-02
They usually include a readme file that should tell you what to do. Sometimes they contain source files that have to be compiled, sometimes binaries that are installed using an included script.


Edit since you asked about using apt-get. This is used for installing deb packages from online repos (or from CD if set up). If you downloaded a deb package you can install by double clicking (runs software centre in recent versions) or install using gdebi if you have that installed. From the cli use dpkg -i

---

### Post by ekz13 on 2011-10-02
check for the readme, there isn't one unfortunatly, and searching yielded nothing

Ubuntu 10.10- the Maverick Meerkat

---

### Post by dniMretsaM on 2011-10-02
You'll need to decompress the tarball (the .tar.gz file) and see what's in there first. If there is an executable (icon will be a gear) you can simply click on it to run it. If it's source code, you will have to compile. Most likely you'll need to run these command in terminal (be sure you read the README and INSTALL files that came with the program):
```
cd /path/to/source/code/
./configure
make
make test   # <-this command is optional
sudo make install
```Sorry, no GUI for this. For more information on compiling, see [here]("https://help.ubuntu.com/community/CompilingEasyHowTo") (<-fairly complicated).

Also, there is a chance that the package could contain a .deb file. if it does, right click on the file, select "Open With..." and choose the Software Center.

---

### Post by alphacrucis2 on 2011-10-02
> **ekz13 said:**
> check for the readme, there isn't one unfortunatly, and searching yielded nothing

Ubuntu 10.10- the Maverick Meerkat

What is the program? Do you have a link to the web site you obtained it from.

---

### Post by angryfirelord on 2011-10-02
Saying you have a .tar.gz file is like saying you have a .zip file. We can't provide help unless we know what it is that you downloaded.

Now, for most applications that have source code, there are generally three steps that you can issue that will install it. In the command prompt, you simply cd into the extracted archive and type the following:
```
./configure
make
make install
```
If any errors return, you have to figure out what dependencies need to be resolved.

However, since you are running Ubuntu, you don't need to do that as much. What I would do is simply search in the Software Center and see if your application is there. It'll make installation of applications a lot easier for you.

---

### Post by Rex Bouwense on 2011-10-02
What is the program that you are trying to install?

---

### Post by ekz13 on 2011-10-02
fair enough, forgot you can't see what I'm looking at..

I'm messing around with utorrent

files are

webui.zip
utserver (executable)
docs folder

---

### Post by mibart on 2011-10-02
There is no simple, generic one way to install programs shipped in tar.gz archive.

It can be a source code with makefile with it.
It can be a just tar-gzipped binary file to execute.
It can be some script installing the program.
It can be any other thing I haven't mentioned here.

So please specify what program You downloaded (name it, give a link to webpage) - this would make any reasonable help possible, otherwise all we can do here is guessing.

And keep in mind: whenever You can, always install software from official repository available through Synaptic, apt-get or whatever You use to install software. Ubuntu repositories are really reach in packages; are You sure that desired program is not available there?

---

### Post by ekz13 on 2011-10-02
I think this one may have been a weird one (utorrent) I've gotten all the other ones to take and install, just not this one.  Not really a big deal, I was going to mess around with some other distro's and figured I'd d/l them from there. I can use transmission as well I guess

---

### Post by oldos2er on 2011-10-02
utorrent for Linux is a command line program. Is there some feature you need that the default client, Transmission, doesn't provide?

---

### Post by dniMretsaM on 2011-10-02
Did you try the steps I mentioned in my previous post? What happens when you run the executable file? And what's in the docs folder? Anything that might help you with the installation?

> **mibart said:**
> And keep in mind: whenever You can, always  install software from official repository available through Synaptic,  apt-get or whatever You use to install software. Ubuntu repositories are  really reach in packages; are You sure that desired program is not  available there?
[B]
[/B]µTorrent isn't in the repos.

---

### Post by ekz13 on 2011-10-02
> **oldos2er said:**
> utorrent for Linux is a command line program. Is there some feature you need that the default client, Transmission, doesn't provide?



ahh that explains it then.. As for transmission, no it'll work just fine, I think I overreached my abilities, figured I would stretch and get it to work too. :D

---

### Post by dniMretsaM on 2011-10-02
> **oldos2er said:**
> utorrent for Linux is a command line program.

It also has a WUI.

---

### Post by ekz13 on 2011-10-02
> **dniMretsaM said:**
> Did you try the steps I mentioned in my previous post? What happens when you run the executable file? And what's in the docs folder? Anything that might help you with the installation?


[B]
[/B]µTorrent isn't in the repos.



the docs files contains all the variables to run it (from the command line I now know) which makes more sense to me than before. when I run it, it give me a .dat file which I'm guessing I would need to edit with all the command variables in the text file.

thanks for the help all, I appreciate it. like I said, I was feeling froggy and jumped...short

---

