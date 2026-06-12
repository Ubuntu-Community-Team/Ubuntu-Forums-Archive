---
title: "DEB package - dependency checks"
date: 2012-10-18
forum: Packaging and Compiling Programs
---

### Post by sashadolstar on 2012-10-18
Hello,
My question is about dependency checks for the DEB package.

Using a third-party install generation tool, I created a .DEB installation package for my application.

There are several dependencies that are required to be present on user&#8217;s Linux OS for my application to run properly. Specifically, &#8220;make&#8221;, and several &#8220;.so&#8221; libraries, like libgcc.so,libc.so, etc. 

Not all of our Ubuntu users may have required dependencies installed prior to running my package installer.

This third-party installer tool that I used, generates DEB package, but does not include dependency checks.

As members of the Ubuntu community, could you please comment on how a custom .DEB package without dependency checks may be received by Linux-Ubuntu users?

Is it acceptable enough to deliver .DEB for a custom application that does not check dependencies?

Or is it uncommon enough to &#8216;anger&#8217; Linux users?

---

### Post by sashadolstar on 2012-10-18
[FONT=Calibri][SIZE=3]Hello,[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]My question is about dependency checks for the DEB package.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT] 
[FONT=Calibri][SIZE=3]Using a third-party install generation tool, I created a .DEB installation package for my application.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT] 
[FONT=Calibri][SIZE=3]There are several dependencies that are required to be present on user’s Linux OS for my application to run properly. Specifically, “make”, and several “.so” libraries, like libgcc.so,libc.so, etc. [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT] 
[FONT=Calibri][SIZE=3]Not all of our Ubuntu users may have required dependencies installed prior to running my package installer.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT] 
[FONT=Calibri][SIZE=3]This third-party installer tool that I used, generates DEB package, but does not include dependency checks. [/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT] 
[FONT=Calibri][SIZE=3]As members of the Ubuntu community, could you please comment on how a custom .DEB package without dependency checks may be received by Linux-Ubuntu users?[/SIZE]
[SIZE=3]Is it acceptable enough to deliver .DEB for a custom application that does not check dependencies? [/SIZE]
[SIZE=3]Or is it uncommon enough to ‘anger’ Linux users?[/SIZE]
[SIZE=3]Thank you.[/SIZE]
[/FONT] 
[FONT=Calibri][SIZE=3][/SIZE][/FONT] 
[FONT=Calibri][SIZE=3][/SIZE][/FONT] 
[FONT=Calibri][SIZE=3][/SIZE][/FONT]

---

### Post by drmrgd on 2012-10-18
My opinion (for what it's worth) is that people generally expect a deb package to handle dependency issues for them.  Otherwise, they would be content with compiling the package from source.  Not having the dpkg system handle the dependencies kind of takes the steam out of the whole idea.  Again, just my opinion.

---

### Post by pqwoerituytrueiwoq on 2012-10-18
since you are requiring make that means you expect the client to compile your program
debs are pre-compiled apps
you would be better off imo giving a install bash script and a source archive if you want to do it like that

i don't know how to make a deb, i just use a install script, stuff i make is just scripts (php, bash, or sh) and does not require compiling

---

### Post by Cheesehead on 2012-10-18
Manually installing dependencies on a debian system in preparation of installing a deb is very rare and unusual. I would consider a deb package without proper dependency information to be malformed or broken, and perhaps untrustworthy...who knows what other important conventions were overlooked? It defeats the purpose of package management. You may as well just use an install/uninstall script instead.

See [http://www.debian.org/doc/manuals/debian-faq/ch-pkg_basics.en.html#s-controlfile](http://www.debian.org/doc/manuals/debian-faq/ch-pkg_basics.en.html#s-controlfile) for a good place to start on how to include dependency information in your package. The list of dependencies (packages, not files) goes in your source's debian control file.

There are easy tools to figure out which files come from which packages, and what versions of packages you need to use. Just ask if you don't know!

The package manager (apt, Synaptic, Software Center, etc.) uses that dependency information to ensure all dependencies are installed automatically. It's a great system, and it's quite easy to use.

---

### Post by lisati on 2012-10-18
Duplicate threads merged and font edited. Please do not start multiple threads for the same problem, it dilutes the community's ability to help.

---

