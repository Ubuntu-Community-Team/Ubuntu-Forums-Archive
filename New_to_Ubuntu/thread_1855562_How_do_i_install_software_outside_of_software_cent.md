---
title: "How do i install software outside of software center 11.04?"
date: 2011-10-06
forum: New to Ubuntu
---

### Post by pkhamidar2com on 2011-10-06
im an absolute noob in linux so im wondering how do i download and install programs outside of the software center


for example i want to download and install 7zip.... it says tar.gz, how do i go about installing this file? If id ouble click it it just opens it... how do i actually install?

also how do i install stuff like kazam
[https://launchpad.net/kazam/stable](https://launchpad.net/kazam/stable)

its rdf or something...

im really confused


also another question, how can i get the calibri windows 7 font for ubuntu 11.04? I feel the text is too big and bulky, i prefer winodows 7 font looks etc...

---

### Post by Basher101 on 2011-10-06
Why do you not want to use the Software Center? it is especially made for making installing programs easy for newbies. You can install programs using the Terminal too. Otherwise the easiest way is to download files with the ending [COLOR="Red"].deb[/COLOR], as they will install like a normal "setup.exe" from windows. But the .deb packages will open the Software Center to install...

p.s. .rdf is the format that Redhat based distributions like Fedora use, so you wont be able to install those in ubuntu.

---

### Post by Paqman on 2011-10-06
[Using Software Centre, .debs and other packages]("http://www.psychocats.net/ubuntu/installingsoftware")

[Using PPAs]("http://www.makeuseof.com/tag/ubuntu-ppa-technology-explained/")

---

### Post by Linux_junkie on 2011-10-06
When searching for software to install outside of the Software Centre best looking for .deb files but it would be safer to stick with the Ubuntu/Debian repo's.  There are around 30,000+ apps in the repo's so you should be able to find an app from it.

Here is a screenshot of the 7zip utility in the Software Centre.

---

### Post by blackbird34 on 2011-10-06
tar.gz means you have to compile it yourself i think, it's not as easy as software center

---

### Post by Paqman on 2011-10-06
> **blackbird34 said:**
> tar.gz means you have to compile it yourself i think, it's not as easy as software center

Actually .tar.gz is just a compressed archive. It could contain anything, from source code that needs compiling, to a script that will run without being compiled, to pictures of lolcats. If the developer is doing his job right there should be a handy README inside it with instructions about what to do.

The big problem with installing software without using the package manager is that it won't get updated, and can potentially break the dependency system in your machine if you start installing weird libs to get your app to run. Best not to try. Almost everything you'll ever need is in the repos, or available as a .deb or PPA.

---

### Post by Johnny3 on 2011-10-06
Take it from and old new bee stick with software center , synaptic package manager, and deb. files. Now if you want to learn other be ready to do a new install. Some time I make Ubuntu so much better it won't work. So I do a new install. 
Good luck and God Bless Johnny3 65++

---

### Post by CaptainMark on 2011-10-06
> **Basher101 said:**
> p.s. .rdf is the format that Redhat based distributions like Fedora use, so you wont be able to install those in ubuntu.

do you mean .rpm i just googled .rdf and got a load of unrelated stuff

---

### Post by oldos2er on 2011-10-06
7zip is in the repositories. ```
sudo apt-get update && sudo apt-get install p7zip
``` After you install it, it will be available to use in Archive Manager.

There's a PPA for kazam here: [https://launchpad.net/~and471/+archive/kazam-daily-stable](https://launchpad.net/~and471/+archive/kazam-daily-stable)

---

### Post by Rusky on 2011-10-06
Using the software center is easiest, updates the program automatically, and allows you to remove it easily. You can also use apt-get for the same effect from the command line. If Ubuntu's repositories don't have it, you can look for a PPA, or a .deb from the program's website and install that way.

However, if you do need to install from source (which is probably what is in that .tar.gz) for some reason, probably because you want or need a version that's not available in the repositories, a PPA, or a .deb package, you can compile it yourself without too much difficulty.

This is only a convention, not a guaranteed way to install from source, so **make sure to read the README and INSTALL files before you do this**, but in general it works this way.

Unpack all the files in the archive into their own directory and open a terminal there (type cd *where/you/unpacked/the/files*). Then run ```
./configure
make
sudo make install
``` configure might have you install some tools first, like g++, but once it succeeds the next two commands will compile the program and then install it on your machine.

---

### Post by proxy.qtz on 2011-10-06
You could try apt-get install or Synaptic.

---

