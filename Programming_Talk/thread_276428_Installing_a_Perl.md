---
title: "Installing a Perl ???"
date: 2006-10-12
forum: Programming Talk
---

### Post by NeoGreen on 2006-10-12
Someone please help](*,)   I want to learn how to program with Perl, but I can't seem to get it installed on my computer ( I am running Ubuntu Breezy ) I downloaded the tar.gz from the perl website but I cant get it to install.  Well, I really don't know where to go from there. Can anyone point me in the right direction on how to install the Perl?  Any advice will help. thank you.

---

### Post by amo-ej1 on 2006-10-13
what's wrong with ```
sudo apt-get install perl
``` ?

---

### Post by NeoGreen on 2006-10-13
You mean that is all I have to do?  Man, I was just going off of what the book was asking. (Beginning Perl) is the name of the book and it asked me to download it from the Perl Website.  I'll try that today and see if it installs.  Thanks.:)

---

### Post by amo-ej1 on 2006-10-13
Yeah, I remember reading some perl documentation some years ago where it stated that you'd better get your own version of perl and compile it ;-) but that's entirely not needed (especially not for beginning programmers). There are even huge chances that it is already installed on you system.

have you already tried to type perl in a prompt ?

---

### Post by slavik on 2006-10-13
umm, perl should already be installed ...

try 'perl -v' or 'which perl'

---

### Post by NeoGreen on 2006-10-13
I typed perl -v and it gave the following information:

neogreen@ubuntulinux:~$ perl -v

This is perl, v5.8.7 built for i486-linux-gnu-thread-multi
(with 1 registered patch, see perl -V for more detail)

Copyright 1987-2005, Larry Wall

Perl may be copied only under the terms of either the Artistic License or the
GNU General Public License, which may be found in the Perl 5 source kit.

Complete documentation for Perl, including FAQ lists, should be found on
this system using `man perl' or `perldoc perl'.  If you have access to the
Internet, point your browser at [http://www.perl.org/](http://www.perl.org/), the Perl Home Page.

I then typed which Perl and I got the following information:

neogreen@ubuntulinux:~$ which perl
/usr/bin/perl

I guess this mean I have it and it is located in /usr/bin/perl

---

### Post by NeoGreen on 2006-10-15
I see that I also have Anjuta installed on my Ubuntu 5.10.  Can I use Anjuta to write programs with Perl?

---

### Post by taurus on 2006-10-15
You can use any text editor you want to write your program for perl.  Heck, you can even use vi if you feel lucky!!!  Otherwise, use gedit or nano...

---

### Post by NeoGreen on 2006-10-15
Okay, so it really doesn't matter as long as it is a text editor.  I like nano it seems a whole lot easier to use.  So after I write a program in Perl, I should save it as a pl file extention and then run it.  Will Ubuntu compile it for me?

---

### Post by slavik on 2006-10-16
umm, perl is not exactly compiled as C is.

when you write a perl script

for example:
```

#!/usr/bin/perl

print "Hello World\n";

```

it doesn't matter how you save it, but don't forget to make it executable:
```

chmod +x perlscript.pl

```

that's it there is to it.

small lesson on the 'she bang' notation (ricki martin so stole the song from Unix) ...

anyways, that first line is special, basically, it tells the shell which interpreter to use for the rest of the script.

C is compiled at the developer end and nothing special (besides the same environment (OS/CPU)) is required to run the program.

Java is compiled at the developer end but the user must have the virtual machine installed.

Perl is is compiled (into bytecode, just like java) at the end-user end and the end-user must have perl interpreter installed.

Hope that explains things. :)

EDIT:
as for using nano, I suggest you google 'vitutor.' it is a simple text file which teaches you how to use vi/vim (you use vim to actually read it) by actually doing things to the file.

I tend to use Anjuta because pressing the F3 key runs the scripts while F9 only runs the script through the interpreter with -c option (compile but not execute, basically, check for syntax).

Yet another thing, while perl can be easy and fun in the very beginning, it can be very intimidating when you start using hashes of arrays of hashes of arrays of hashes (and onto infinity), of course there is pretty much no practical example where you do stuff like that.

---

### Post by NeoGreen on 2006-10-16
Wow, thanks for the info slavik. I didn't realize the difference, between many program languages. :)

---

### Post by Engnome on 2006-10-16
> **NeoGreen said:**
> Okay, so it really doesn't matter as long as it is a text editor.

As long as you don't use a WYSIWYG editor like abiword or openoffice...

---

