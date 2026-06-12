---
title: "Porblem with installing Crossover"
date: 2013-11-13
forum: New to Ubuntu
---

### Post by steventijs on 2013-11-13
Hi Ubuntu community!

Installed Ubuntu yesterday and must say: it's great! So much nicer than windows xp, my previous system.

I'm trying to install Crossover, though yet without any luck.
The installation goes through a .deb file and I get the following message:

**"Error: Dependency is not satisfiable: dpkg (>= 1.16.5)"**

I checked on the internet what I could do and tried to add the following line at terminal:

*'sudo dpkg --add-architecture i386'*

And then I get:

[I]dpkg: error: unknown option --add-architecture

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' ![/I]


I have no idea what to do with this, looked on the internet but I'm a complete linux newbie ;-)

Anyone any idea how I can still install crossover?

Thanks in advance,
Tijs

ps. I have the 32-bit version of Ubuntu, maybe that's necessary info to fix this thing.

---

### Post by Toz on 2013-11-13
Hello and welcome to the forums.

I guess you're using Ubuntu 12.04. The latest version of Crossover has a dependency for a dpkg version that is greater to or equal to 1.16.5. Ubuntu 12.04 comes with 1.16.1, hence the problem.

There is a [FAQ entry]("http://www.codeweavers.com/support/wiki/linux/faq/ubuntu_satisfy_dependencies") on the codeweaver's website that discusses this to some extent, and suggests that if the deb packages doesn't work, you can:
> If you receive this error, please defer to the ".bin" installer available here. 
...in other words, use the bin installer instead of the deb package.



> I checked on the internet what I could do and tried to add the following line at terminal:

'sudo dpkg --add-architecture i386'
> ps. I have the 32-bit version of Ubuntu, maybe that's necessary info to fix this thing. 
The "--add-architecture" parameter is for 64-bit systems, and since you have a 32-bit install, it won't work for you.

---

### Post by steventijs on 2013-11-13
Wow thanks a lot, that worked :-)

---

