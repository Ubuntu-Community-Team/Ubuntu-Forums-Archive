---
title: "Which editor do people use for PHP??"
date: 2005-08-29
forum: Programming Talk
---

### Post by ROUBOS on 2005-08-29
Hi,
I installed Apache2, MySQL and PHP4 to do some server side web development. 

I was wondering which editor do people here use to program in PHP?

I got emacs installed and Gedit ofcourse... ..

---

### Post by Sam on 2005-08-29
I use the great [Eclipse](https://wiki.ubuntu.com/EclipseIDE) with [PHPEclipse](https://wiki.ubuntu.com/PHPEclipse). It supports autocompletion, and it's very powerful. But I use it for large projects containing a lot of php files. For small websites gedit or vim work well :wink:

---

### Post by SGC on 2005-08-29
[Quanta Plus](http://quanta.kdewebdev.org/) is great for working with PHP, you can install it with:
apt-get install quanta

---

### Post by deathseeker25 on 2005-08-29
[QUOTE=SGC][Quanta Plus](http://quanta.kdewebdev.org/) is great for working with PHP, you can install it with:
apt-get install quanta[/QUOTE]


I also use Quanta for my PHP applications...i think it's a nice PHP editor....kinda easy to use, easy to the younger programmers learn PHP and it has all the tools a programmer need...

Never tried Eclips PHP tool but o think i will have to test it someday....

---

### Post by deuce868 on 2005-08-30
I spent the $$ on Zend Studio and never looked back. It's code completion is second to none and I always check out my scripts with its profiling and debugging features. Their dev version I'm testing includes some great stuff like svn integration as well.

---

### Post by Koobi on 2005-09-06
[QUOTE=ROUBOS]Hi,
I installed Apache2, MySQL and PHP4 to do some server side web development. 

I was wondering which editor do people here use to program in PHP?

I got emacs installed and Gedit ofcourse... ..[/QUOTE]
 i started using vim 2 months ago.
i don't think i'll ever switch editors ever again.

i work with PHP and a little XHTML+CSS+XML+XSLT

---

### Post by David Marrs on 2005-09-07
[QUOTE=ROUBOS]Hi,
I installed Apache2, MySQL and PHP4 to do some server side web development. 

I was wondering which editor do people here use to program in PHP?

I got emacs installed and Gedit ofcourse... ..[/QUOTE]
 check out [bluefish](http://bluefish.openoffice.nl).

---

### Post by blissend on 2006-07-12
I've tried so many editors (bluefish, nvu, screem, gedit, quanta, and a few others) but I've only liked Scite. I loved notepad++ in windows and scite is based on the same stuff... scintilla.

[http://www.scintilla.org/SciTE.html](http://www.scintilla.org/SciTE.html)

I like it because it supports automatic syntax styling, multiple files in tabular display, sessions, folding (something I can't live w/o when building big applications), and doesn't have much of a cluttered gui interface.

---

### Post by indytim on 2006-07-12
Any text editor with line numbers and multiple windows.  Need line numbers for de-bugging (unless you write perfect code each time ](*,) ) and multiple windows for multiple file editing at the same time.  

<opinion> The rest of the stuff is a lot of fluff </opinion>.

IndyTim

---

### Post by deuce868 on 2006-07-12
> **indytim said:**
> Any text editor with line numbers and multiple windows.  Need line numbers for de-bugging (unless you write perfect code each time ](*,) ) and multiple windows for multiple file editing at the same time.  

<opinion> The rest of the stuff is a lot of fluff </opinion>.

IndyTim

When you get into large projects a debugger and profiler quickly move from fluff to essential. :mrgreen:

---

### Post by fluffington on 2006-07-12
[Kate](http://kate.kde.org/)

---

### Post by ifokkema on 2006-07-12
> **indytim said:**
> Need line numbers for de-bugging (unless you write perfect code each time ](*,))
That's one of the things I like so much about **gPHPEdit**: While editing your code, press F9 and (if php[4|5]-cli is installed) it parses your file right away and jumps to the line you're having a parse error (if any). No switching to the browser and refreshing necessary, just one button :)

gPHPEdit is my editor of choice, hands down.

---

### Post by Test33 on 2006-07-12
I use Dreamweaver, I just like the option of saving it right to the remote server, I hate having to use third party ftp program. Since I wanted DW8 and I gave up on wine trying to getting it to run, I installed vmware to get windows and now use it that way, works prefect for my freelancing jobs.

---

### Post by fluffington on 2006-07-12
> **Test33 said:**
> I use Dreamweaver, I just like the option of saving it right to the remote server, I hate having to use third party ftp program. Since I wanted DW8 and I gave up on wine trying to getting it to run, I installed vmware to get windows and now use it that way, works prefect for my freelancing jobs.

I use KDE, in which every nearly app on the system has the same capability ('tis one of the biggest reasons I use KDE over GNOME).

---

### Post by slider on 2006-07-14
Currently I use BlueFish. It has cusomizable syntax highlighting and line numbering. It has some pretty bothersome UI bugs that annoy me enough to want to find something else. 

1. The syntax highlighting get's confused fairly often.
2. If I close the fileview pane and reopen it it forgets where it was 
3. It doesn't have powerful text navigation capabilities with the keyboard and is difficult to select text via the mouse on very long lines.

Personally I'm not a big fan of saving files immediately to a remote server (ie with Dreamweaver). I test locally, store it in subversion and push out to the server using lftp. That way if I need to roll back changes I can simply update to the last good revision and push it back out.  Working without SCC is like acrobatics without a net and just too nerveracking for me.

---

### Post by pharcyde on 2006-07-14
vim.. love it

---

### Post by MrHorus on 2006-07-15
Zend Development Environment ([http://www.zend.com)](http://www.zend.com)).

It's built on Java and is avaliable for Windows and Linux and well worth the $100 in my opinion.

Purists will scoff at it since it's closed source but I don't care - it beats anything else I have used hands down :)

---

### Post by slider on 2006-07-15
> **MrHorus said:**
> Zend Development Environment ([http://www.zend.com)](http://www.zend.com)).

It's built on Java and is avaliable for Windows and Linux and well worth the $100 in my opinion.

I like Zend and think they do some good stuff but the licensing model bugs me. I'm not so excited to buy software and then have to rebuy it every year if I want to keep using it. Sounds more like rental to me. If I pop for the $299 to buy the professional version I "get to" keep using it after the year but have to pay for any bugfixes or upgrades. That being said I like that it is licensed per user and I can install it on multiple computers.

---

### Post by GeoMX on 2006-07-16
> **slider said:**
> 
1. The syntax highlighting get's confused fairly often.

I also use Bluefish but I'm looking for an alternative because of this issue (why did the decide to write their own syntax highlighter and not to use an existing one?).
My reason for using an IDE is project managing and syntax highlighting, since I don't work on "big" applications.

---

