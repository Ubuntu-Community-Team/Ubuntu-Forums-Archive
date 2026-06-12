---
title: "Not able to Run/find &quot;configure&quot; command"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by branthan on 2008-06-17
Hi every 1,
i am not able to Run/find the ./configure file.I was installing aircrack and The message comes configure command not found.

I extracted the tar.gz file and then try to do the ./configure command. then it shows the error. Please Advice.

---

### Post by cdtech on 2008-06-17
What's the exact error your seeing?

You may need to install the build essentials.
sudo apt-get install build-essential

---

### Post by bumanie on 2008-06-17
before you are able to compile, you need to install the linux C compiler.
> sudo apt-get install build-essential You should have more luck after that. If you already have build-essential installed, you should look at the text file inside the extracted folder and look at the installation instructions. If you can't understand them, post the installation instructions and someone will help you.

---

### Post by iaculallad on 2008-06-17
Synaptics Package Manager made life easier: Goto System->Administration->Synaptic Package Manager, click on the "Search" button and input the word "aircrack" (that's w/o quote) in the search field. Right-click on the Aircrack Package and select "Mark for Installation" and click on "Apply".

---

### Post by hyper_ch on 2008-06-17
and you know, after untarring you'll have to enter the according dir to run ./configure - however installing from the repos is much more recommended.

---

### Post by f1italian on 2008-06-17
Ok. So I'm in the same boat with this guy and can't get my ./configure to work. I have the whole build-essential thing going on and I even did the gcc thing (although I don't even really know what that is exactly). Either way I still get this error in the terminal when i enter "./configure"

bash: ./configure: No such file or directory

am I just entering something in wrong? I'm trying to install Firefox 3.0 (woot) and it's in a tar.bz2 file. Now I'd get an easier format to install, but I can't seem to access the page to get there. So I'm stuck with tar.bz2 for now. I looked at Synaptic but they don't have the newest version, just Beta 4. I've been trying to follow the instructions here, 

[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

but as I said before i can't get the darn ./configure command to work.

Thanks for your help...

---

### Post by oldos2er on 2008-06-17
Either you're in the wrong directory, or there's no file named configure in the directory.
I'm pretty sure Firefox comes with precompiled binaries, so once you unpack the archive, change to the firefox directory and run ./firefox .

---

### Post by f1italian on 2008-06-18
I extracted the tar.bz2 file and all that jazz. You're right in that there is no configure file. So I ran ./firefox in the correct directory and Firefox popped up. I was happy to see that, but it was still Firefox 3 Beta 4. I went back to that monkeyblog thing and it said how i have to run make or make install. I type like "make firefox" but no dice. It just says "make: Nothing to be done for `firefox'." I really don't know what to do at this point. I've extracted it and am stratching my head on how to install it. 

Thanks for your help so far. I'm really a noob at this stuff, but it seems the only way to learn this linux stuff is the hard, slow, and mildly painful way.

---

### Post by ChameleonDave on 2008-06-18
> **f1italian said:**
> 

bash: ./configure: No such file or directory


Well, if it's not there, it's not there.  That's nothing to do with Ubuntu; it's what you downloaded.

"./" means "the current directory".  So, "./configure" means "run the file called 'configure' in this directory".

To see whether there is such a file in the current directory, you can of course simply type "ls", which lists the current directory contents.

Some tarballs have no configure file.  You just have to type "make".  Some don't even require that: they simply contain an exectable that you can run, straight off.

There is almost certainly a file containing instructions in the tarball.  Again, just extract the contents of the tarball, use the "cd" command to enter the new directory, and type "ls".  If you see that there is a file called "README" or "installing" or "instructions"... well, I've sure I don't need to tell you what to do!

---

### Post by N.N. on 2008-06-18
> **f1italian said:**
> I extracted the tar.bz2 file and all that jazz. You're right in that there is no configure file. So I ran ./firefox in the correct directory and Firefox popped up. I was happy to see that, but it was still Firefox 3 Beta 4. I went back to that monkeyblog thing and it said how i have to run make or make install. I type like "make firefox" but no dice. It just says "make: Nothing to be done for `firefox'." I really don't know what to do at this point. I've extracted it and am stratching my head on how to install it. 

Thanks for your help so far. I'm really a noob at this stuff, but it seems the only way to learn this linux stuff is the hard, slow, and mildly painful way.

As oldos2er remarked, the contents of the .tar.bz2 file you downloaded from mozilla's website is already compiled. Therefore trying to compile the contents of the archive with ./configure, make, and make install is unnecessary and won't work. (Cf. the note on monkeyblog: "not all files with an extension named .tar, .tar.gz, and so on are archives with source code in them - they might be precompiled! If the archive is precompiled, there should be an installer or a binary executable inside it.")

It should be sufficient to change to the extracted firefox directory and run ./firefox or perhaps ./firefox-bin in order to run the application.

---

### Post by f1italian on 2008-06-18
> It should be sufficient to change to the extracted firefox directory and run ./firefox or perhaps ./firefox-bin in order to run the application.

Ya you were right. It's funny how it was right in front of me the whole time. I ran ./firefox and what do ya know it worked. Thanks!

---

### Post by branthan on 2008-06-21
hi all, sry 4 te late reply. 

my problem is still ter :( . i tried sudo apt-get install build-essential .. but nothing is happening. the results says there is nothing called build essential
when i looked into the folder there is no configure file.
so i tested with another software(wine) which has the configure file. I ran followed these steps
1. extracted
2. went into the main folder
3. ./configure
4. make ( Result - cannot find the make file) 
5. after that i ran make install 

cannot install or something like that, i cannot remember the exact error. 
:confused:

---

