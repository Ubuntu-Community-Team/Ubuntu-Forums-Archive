---
title: "GUI &quot;Windows style&quot;  API's for Ubuntu"
date: 2012-09-09
forum: New to Ubuntu
---

### Post by mark allyn on 2012-09-09
Hello eveyone,
 
As a newcomer to Ubuntu (and more generally, Linux), and familiar with Windows API's for creating Microsoft Windows, I am seeking a recommendation from the community as to a package that would allow me to create GUI's for apps I write (primarily) in C.  I do not have internet service on my Ubuntu 12.04 machine, but I do have a working CD drive from which I can load burned CD's.
 
I hope I'm not repeating a previous posting, but I was unable to find anything on this subject in searching GOOGLE or this forum.
 
Cheers to all,
 
Mark Allyn

---

### Post by arsenic23 on 2012-09-09
This might be a good place to start:  [GTK vs QT]("http://www.wikivs.com/wiki/GTK_vs_Qt")

---

### Post by vexorian on 2012-09-09
You can even use winapi and run it as a WINE :/

What ubuntu "native" apps normally use is GTK. Currently the hopeful next standard is GTK 3.0

Other apps use QT.

There is also wxwidgets which allows you to develop for both ubuntu and windows at (almost) the same time.

Depending of what you want, maybe you are making a game, then things like SDL or Ogre might work better for you.

Your main problem will be installing the required packages since you have no internet. Honestly, lack of internet is really an ubuntu killer and will make everything harder for you.

But there are approaches... Here is a starting point: [http://ubuntuforums.org/showthread.php?t=1100816](http://ubuntuforums.org/showthread.php?t=1100816)

---

### Post by mark allyn on 2012-09-09
Good evening, vexorian and arsenic23,
 
Yes, lack of internet is definitely a problem.  I hope to fix this issue in the next few weeks.
 
If I were to download gtk or qt can you recommend sites for the downloads?  Qt is worrisome because it appears to be c++ and I am uncomfortable in this language.  
 
Thanks,
Mark

---

### Post by vexorian on 2012-09-09
The only site from which you have to download is Ubuntu's own repositories. Installing gtk development packages from else where is probably not going to work.

You will need the development gtk packages. (You already have gtk installed. but not the development ones).

If you would like an IDE, you can try anjuta out. (The anjuta package).

You will need the **gnome-devel** metapackage and also the **build-essential** metapackage.

After that, to get started, try this: [http://developer.gnome.org/gtk3/3.4/](http://developer.gnome.org/gtk3/3.4/) (Ignore the part about installing (compiling) the libraries, you already did that when installing the packages.

Whenever I say "install package" you will have to follow the guide I linked about how to download packages from another computer and installing them in yours.

---

### Post by anewguy on 2012-09-10
+1.  You may also want to try code-blocks.

Keep in mind - whenever possible always use the software center (or synaptic package manager) to install packages - in this case the GTK development libs and supporting packages.  The package manager, or front ends like synaptic or the software center, will not only install the package you selected, but will also install the packages that it depends on to be functional.

I have used GTK, and just a thought for you:  GTK is also available for Windows - I have done cross-platform development in C with GTK with no code changes.

Also, there are tools, such as glade, to help you with the work of GTK in the repositories as well.  While these indeed work, and may make your development quicker, keep in mind that you don't get real understanding of how things actually work.  Personally I prefer to actually understand what's going on - it can help make debugging easier and it also gives you a little more freedom doing some things.

I haven't used QT yet myself, but I've seen positive comments on it as well - I don't know if it is cross-platform or not.

BTW - can you get access to public internet at a library, coffee shop, etc.?  If so, I would highly recommend it.  There are ways to automatically generate download scripts for everything that makes up a package and it's dependencies, but having an internet connection would make things MUCH easier.

---

### Post by Vaphell on 2012-09-10
> I haven't used QT yet myself, but I've seen positive comments on it as well - I don't know if it is cross-platform or not.

it is definitely cross-platform and imo it's the best cross-platform toolkit available. The number of convenient classes if offers makes the mind boggle, not to mention QtCreator is a nifty IDE and QtDesigner makes it easy to lay apps out.

---

### Post by anewguy on 2012-09-10
> **Vaphell said:**
> it is definitely cross-platform and imo it's the best cross-platform toolkit available. The number of convenient classes if offers makes the mind boggle, not to mention QtCreator is a nifty IDE and QtDesigner makes it easy to lay apps out.

Thanks for that info.  As I mentioned, I've never used it, so I really don't know anything about it.  However, with your comments I may just have to finally try it!

Thanks!
Dave ;)

---

### Post by mark allyn on 2012-09-10
This is pimarily for anewguy, but thanks as well to others:
 
Here's the thing.  I don't have an internet connection on my ubuntu box.  My very primitive understanding of the software center is that it really depends importantly on the internet in order to download not only the package, but also the package's possibly many dependencies.  Am I correct about this?  
 
It's important to me to understand this particular point.  Because, I have been trying desperately to install g++  (the GNU cplusplus compiler), and it depedends on a cloud of different dependencies.  Each of these I have to locate, download on another box, and then burn to a CD and then install on the ubuntu box.  It's a mess.  I've about given up. 
 
Thanks for your help.
 
Mark

---

### Post by SeijiSensei on 2012-09-10
Managing software on a Linux box is very difficult without Internet access.

There are DVDs for Ubuntu that have a much larger array of packages than the ones included with an installation CD.  If you have a DVD, you can try installing from there.

Otherwise I'd say you should wait until you get your Internet service straightened out, or you're likely to be in for a long and frustrating experience trying to install everything you need manually.

---

### Post by mark allyn on 2012-09-10
Hello SeijiSensei,
 
My experiences thus far confirm your assertion about the importance of Inet connectivity.  The first thing that has hit me in the face is the huge problem with dependencies.  There is this torrent, cascade of dependencies upon dependenices.  Oh my word!  Coming out of Microsoft I had no idea how big the problem is for Linux users.  MinGW also shields users from the problem, so to be fair, it is not only Microsoft that buffers users....  Cygwin also does this too.
 
For the time being I have downloaded from GNU the GNU Core and gnu c++ packages.  I'm going to try to install from them.  
 
Cheers,
Mark

---

### Post by Vaphell on 2012-09-10
there are advantages and drawbacks to all technical solutions.
Windows programmers usually package their software with the complete set of .dll files required by the program (or even compile statically to create one huge binary blob with everything) because it's more of 'every man for himself' environment where nobody counts on the operating system to provide necessary bits. That reality introduces much overhead and a dll hell were somewhat standard libraries exist in 20 slightly different versions in the system (many of which have known vulnerabilities). When you install a game but it needs dx9something.dll with a greater number at the end, it's the users job to hunt for that lib/install latest dx, though i've heard win8 also moves in the online repository direction.


With community driven effort package managers make much sense. Repo with common libs to use by all reduces the overhead and duplication of code (so the system is more efficient at the use of resources), all dependencies are automatically sorted out for you, so you don't have to do any of that 'shuffle dozen of installer disks' nonsense. The drawback is things get hairy when you lack stable internet connection or want to install out of repo program with a set of libraries that conflict with the system versions.

---

### Post by anewguy on 2012-09-11
There is the ability, though I would have to go hunting to find it again, to generate a script from the package manager to download packages elsewhere.  There are 2 big things to remember here:

- yes, internet access is of high importance.  If you have a wireless adapter, I suggest going to a public library, coffee house, etc., that offers free internet access to at least use the internet to get what you need.  I mentioned this in my thread, as I was under the impression that wireless or wired internet was not a hardware problem on your PC, but rather at your location.  If indeed you just plain don't have a wireless adapter and have no place to go - including a friend or school, etc. - that might let you hard wire to their router, then by all means let me know and I'll dig up the stuff on generating the script to download the packages so you can have someone do that for you.  I just thought since you talked like Windows was working in 1 of your replies that perhaps a lack of internet connection we might be able to fix.  Either way, an internet connection is almost going to be manadatory for you to avoid fighting dependencies and missing libs for a long, long time - been there, done that, won't ever do it again.

- don't struggle with trying to install g++ and going into dependency "heck".  This is why using the package manager is so important - it will grab the dependencies as well.  Also, be sure you have installed the build-essential package.

- GTK will also have dependencies - again using the package manager and yes, the internet, is the only way to do this.

- I've also used mingw - it does what it's supposed to in Windows. 

If you are just having trouble getting your wireless to work before you can use the internet, post that back as well and the output of lspci (or lsusb if using a usb dongle for wireless) and we can try first to get that working for you.

I'd like to make sure we've exhausted every possible thing before you give up on it.

---

