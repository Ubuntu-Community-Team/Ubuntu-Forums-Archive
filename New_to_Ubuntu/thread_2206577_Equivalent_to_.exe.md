---
title: "Equivalent to .exe?"
date: 2014-02-19
forum: New to Ubuntu
---

### Post by cy1on on 2014-02-19
I am a noob in the Linux world and I have a question regarding installing programs. In Windows there are .exe files that is an executable file that will put all of the files in "Programs" folder.

I know that if I install a program in Linux it's either in Ubuntu Software Center or through the terminal. But is there in Linux a equivalent file to .exe and is there any talk about a graphical installation process like in Windows/Mac for the users that isn't interested of doing it through the Terminal? (For the programs that won't be in the Software Center). I'm just curious if that's possible in the future or already is?

---

### Post by SeijiSensei on 2014-02-19
To answer the second question first, there are something like 40,000 applications in the Ubuntu "[repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu")."  It's unlikely you would need to look elsewhere.  Software for Linux is managed in an entirely different fashion than software for Windows.  Rather than installing applications from random, untrustworthy locations on the Internet, all the software for Ubuntu is compiled and tested by Canonical before being distributed in the repositories.  There are other options, but mostly you should stick with what is available through the Software Center.

As for the first question, Unix doesn't use specific file extensions to designate executable programs the way Windows does.  The Firefox executable is stored as /usr/bin/firefox.  Most software that you would normally use [resides]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure") in either /bin or /usr/bin.  The first includes basic stuff that you would need even in an emergency like the "ls" program to list directories.  The vast bulk of software on your machine is stored under /usr/bin.  There are good historical reasons for this distinction, but they are not especially relevant for single users on desktop machines.

Another feature of Unix is that executable programs need to [marked]("https://help.ubuntu.com/community/FilePermissions") as such at the filesystem level.  

One other important feature is the widespread use of dynamic libraries in Unix.  Programs "depend" on the existence of other software called libraries that include common functions that many programs share.  Video players, for instance, take advantage of libraries of media codecs, and browsers use libraries that handle HTTP requests.  This decentralized approach exists on Windows as well, but commercial developers often build "static" binaries with all the libraries included to avoid potential versioning conflicts.  Linux handles that problem by including the list of requirements in the "package" file along with the specific program itself.  If you install a package from the command prompt with "sudo apt-get install package_name" you'll often see the installer include other "dependencies" on which the program of interest relies.

---

### Post by Don_Stahl on 2014-02-19
Nice overview, SeijiSensei! As a noob, I appreciate the clarity.

---

### Post by Mark Phelps on 2014-02-19
> In Windows there are .exe files that is an executable file that will put all of the files in "Programs" folder.

That's not really how Windows apps get installed.  They are packaged to invoke an "installer", and then using information embedded in the package, different information is written into different parts of the Windows filesystem. In many cases, over a half-dozen different directories are involved, including the so-called "registry" which is really a collection of four different database files known as "hives".

Mentioning this because the Linux installers (.deb packages) work along very similar lines -- they put different information from different components of the apps into different locations in the Linux filesystem.

---

### Post by cy1on on 2014-02-19
> **SeijiSensei said:**
> To answer the second question first, there are something like 40,000 applications in the Ubuntu "[repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu")."  It's unlikely you would need to look elsewhere.  Software for Linux is managed in an entirely different fashion than software for Windows.  Rather than installing applications from random, untrustworthy locations on the Internet, all the software for Ubuntu is compiled and tested by Canonical before being distributed in the repositories.  There are other options, but mostly you should stick with what is available through the Software Center.

As for the first question, Unix doesn't use specific file extensions to designate executable programs the way Windows does.  The Firefox executable is stored as /usr/bin/firefox.  Most software that you would normally use [resides]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure") in either /bin or /usr/bin.  The first includes basic stuff that you would need even in an emergency like the "ls" program to list directories.  The vast bulk of software on your machine is stored under /usr/bin.  There are good historical reasons for this distinction, but they are not especially relevant for single users on desktop machines.

Another feature of Unix is that executable programs need to [marked]("https://help.ubuntu.com/community/FilePermissions") as such at the filesystem level.  

One other important feature is the widespread use of dynamic libraries in Unix.  Programs "depend" on the existence of other software called libraries that include common functions that many programs share.  Video players, for instance, take advantage of libraries of media codecs, and browsers use libraries that handle HTTP requests.  This decentralized approach exists on Windows as well, but commercial developers often build "static" binaries with all the libraries included to avoid potential versioning conflicts.  Linux handles that problem by including the list of requirements in the "package" file along with the specific program itself.  If you install a package from the command prompt with "sudo apt-get install package_name" you'll often see the installer include other "dependencies" on which the program of interest relies.

Aha, ok. Thank you so much for clearing that up for me. I don't find it difficult, I was just curious how things work on Linux.

---

