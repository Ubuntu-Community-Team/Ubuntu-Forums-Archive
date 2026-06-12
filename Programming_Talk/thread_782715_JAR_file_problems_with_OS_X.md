---
title: "JAR file problems with OS X"
date: 2008-05-05
forum: Programming Talk
---

### Post by mattgaunt on 2008-05-05
Hey everyone

I finally have a jar file that works when called from a command line, but I have some new problems.


I tried creating a .app file for OS X using jar bundler, it works on my laptop and everything seemed fine, I sent it to a friend and he got the following error :

"You can't open the application SearchWord because the classic environment is no longer supported" 

I dont fully understand what the classic environment is and after searching Google all i could see was that this error occurs on mac OS X 10.4 down since 10.5 doesn't include the classic environment.


But it was made on 10.5 anyone any ideas?

Cheers in advance

Gaunt

p.s. is anyone is wondering what the hell this program is, its word search program ive bn making for a Uni project, the URL will follow if anyone actually wants it - it is a pretty sketchy program though :-P

---

### Post by Zugzwang on 2008-05-05
I guess that "Classic environment" is the old API for programs for the mac prior to OSX. The support was discontinued.

Probably you need to use a newer version of the jar bundler. Alternatively, you can just distribute the jar - this works as well.

---

### Post by mrsteveman1 on 2008-05-05
Classic is a way to run OS 9 itself inside OS X to support older apps at the binary level, stuff so old the developer can't or won't recompile it as a native app. Source level compatibility comes from the Carbon API.

There is no Classic on Intel macs in the first place, so only PPC machines can use it at all. But java shouldn't have anything to do with classic, so its odd that a jar file would trigger this.

You can usually run Jar files directly from the GUI so see if that works, sometimes it doesn't.

---

### Post by mattgaunt on 2008-05-05
cheers guys for the replies, my other developer just updated to the same version as me and used jar bundler on the file and it works on both mine and his machine so its fixed I guess, just weird why my bundled version didnt work :-S

The only reason for using the .app was it just makes the jar file look lil nicer in Mac OS X

But yeah thanks again guys

---

### Post by mattgaunt on 2008-05-05
final note - We think it was cos he has a slightly more up to date version of java compiler

Gaunt

---

