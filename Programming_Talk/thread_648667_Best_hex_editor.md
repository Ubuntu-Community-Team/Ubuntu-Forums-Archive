---
title: "Best hex editor?"
date: 2007-12-23
forum: Programming Talk
---

### Post by Sir Nose on 2007-12-23
On some parts, I'm still migrating from Windows. One program I haven't been able to find is a easy-to-use and flexible hex (binary) editor. Which one do you people use?

---

### Post by Wybiral on 2007-12-23
GHex.

---

### Post by slavik on 2007-12-23
or khex if you use kde

---

### Post by pmasiar on 2007-12-28
I use mc (midnight commander) on Linux and Total Commander on Windows - they are both clones of excellent Norton Commander from old MS-DOS days, and are much more than hex editor - basically it is the only tool you would ever need :-) : [http://en.wikipedia.org/wiki/Orthodox_file_manager](http://en.wikipedia.org/wiki/Orthodox_file_manager)

They can do tricks like comparing directories, picking files to copy/move, and much much more.

---

### Post by jfordwashere on 2008-03-07
If you have wine installed, try iHex. You can get it [[COLOR="Blue"]here[/COLOR]]("http://www.memecode.com/ihex.php").

---

### Post by ruy_lopez on 2008-03-07
xxd - for piping into
mc - for editing

---

### Post by pmasiar on 2008-03-07
Hey, ruy_lopez, great to see another MC fan! 

Kids these days have no idea how much can be done in character-based app like MC, how it can be visual and intuitive without having the GUI overhead. :-)

---

### Post by lnostdal on 2008-03-07
emacs

---

### Post by LaRoza on 2008-03-07
> **lnostdal said:**
> emacs

Vim

[http://www.vim.org/htmldoc/usr_23.html#23.4](http://www.vim.org/htmldoc/usr_23.html#23.4)

---

### Post by ruy_lopez on 2008-03-07
Another command line hex editor is "biew" (for some reason I can never remember the name).

---

### Post by LaRoza on 2008-03-07
> **ruy_lopez said:**
> Another command line hex editor is "biew" (for some reason I can never remember the name).

[http://biew.sourceforge.net/en/biew.html](http://biew.sourceforge.net/en/biew.html)

Looks neat.

---

### Post by dburnett77 on 2008-03-08
Gnu Hex Editor, GHex, is good.
A neat tactic for mysterious files, to inadvertently cause check-fails, is:  Random insertion of soft-reboot.
0F16x

anywhere in the file.  If you kernel doesn't flag or correct, it's probably virulent.
Then you wait and see if it gets touched again.  If not, no further action necessary...

---

### Post by dmgExP on 2008-03-26
> **pmasiar said:**
> I use mc (midnight commander) on Linux 

AAH!! Another fan of the console interface I presume??

Can somebody please point me to a utility that makes editing the "ls" directory colours easy -- turboc style????

Thanks

---

### Post by todb on 2008-10-15
> **LaRoza said:**
> Vim

[http://www.vim.org/htmldoc/usr_23.html#23.4](http://www.vim.org/htmldoc/usr_23.html#23.4)

I've long vacillated between Windows and Debian Linux, and the deal breaking for long-term Linux use, for me, was the lack of a decent GUI-fied text/hex/anything editor akin to [UltraEdit]("http://www.ultraedit.com/").

I use gvim for pretty much all text -- html, ruby, xml, C, etc -- and now I think I've finally stumbled upon a useful set of macros for using gvim as a hex editor. Check this:

[http://vim.wikia.com/wiki/Improved_Hex_editing](http://vim.wikia.com/wiki/Improved_Hex_editing)

I've been messing around with this this morning, and it looks to be at least serviceable for simple hex editing, but searching and replacing blocks of binary is still pretty painful. I'm now off to hunt for another appropriate macro for that (looks to be just a matter of creative regexing).

---

### Post by erdem_a on 2008-12-09
Best hex editor is that what I made :)
No no, its not ready. But when I complete, I thought it's best hex editor in linux mainland ( and macOS to, But I don't think that it will beat WinHex)

If you want, you can try it at [wxHexEditor.sf.net]("http://wxHexEditor.sf.net")

( It's better to use SVN, It has write support. :)
:)

---

### Post by Cannaregio on 2008-12-20
I think one of the best, recent editors, is okteta.

[http://utils.kde.org/projects/okteta/]("http://utils.kde.org/projects/okteta/")

Last updated in october 2008

It's for kde, unfortunately, but still quite good imho.

[HTML]sudo apt-get install okteta[/HTML]

This said -and since most hexediting for obvious reasons will anyway target windoze programs- the excellent old edition of hexworkshop 3.1 (also look for 3.1.1), easy to find on the web as old abandonedware, works [COLOR="Blue"]perfectly[/COLOR] with wine under intrepid.

Cheers!

---

### Post by bgbraithwaite on 2010-08-12
[**Okteta**]("http://utils.kde.org/projects/okteta/") is the best KDE4 hex editor I've used.

---

### Post by surfer on 2010-08-12
+1 for okteta.

---

### Post by qetuR on 2011-09-03
> **erdem_a said:**
> Best hex editor is that what I made :)
No no, its not ready. But when I complete, I thought it's best hex editor in linux mainland ( and macOS to, But I don't think that it will beat WinHex)

If you want, you can try it at [wxHexEditor.sf.net]("http://wxHexEditor.sf.net")

( It's better to use SVN, It has write support. :)
:)

This one is really good actually. Great job! :guitar:

---

### Post by Senesence on 2011-09-04
```
sudo apt-get install hexer
```

Hexer is the best.

---

### Post by erdem_a on 2012-03-15
> **Senesence said:**
> Hexer is the best.
Hexer? It uses "C#" and I don't allow any mono program at my PC! 

In this time, the best gets better.
I released [wxHexEditor]("http://www.hexeditor.eu") v0.20.
**New features** are:
[LIST]
[*]Sector Indication on Disk devices, also has Go to Sector dialog...
[*]Formatted CopyAs! It's easy to copy part of a file in HEX format for C/C++ source, ASM source, also supports HTML,phpBB and Wiki page formats with TAGs!!
[*]Support Hex or Text editor alone operation.Also can disable Offset region.
[*]Compare binary files, allows merge of near results.
[*]Decimal, Hexadecimal, Octal and LBA ("Sector+Offset") addressing modes, (switchable one to another by right click of mouse on Offset panel.
Save selection as a dump file feature for make life easier.
[*]"Find Some Bytes" feature for quickly find next meaningful bytes at file/Disk
[*]MD/RIPEMD/SHA/TIGER/HAVAL/CRC/ADLER/GOST/WHRILPOOL/SNEFRU checksum functions (via integrated mhash library.)
[*]Import & Export TAGs support from file.
[*]Many bugfixes...
[/LIST]
And if you use SVN version, there is **Process RAM editing** feature!.

[IMG]http://www.wxhexeditor.org/images/screenshot.png[/IMG]

Also want to indicate that, it's not well known hex editor, specially on linux world (yet). I don't have enough bug reports. I want more users use it and got feedback/bug reports. Please share wxHexEditor to increase popularity and make me motivate working on it... Thanks

[http://www.hexeditor.eu]("http://www.hexeditor.eu")

---

### Post by jwbrase on 2012-03-15
I personally use [ht]("http://hte.sourceforge.net/"), which can also be found in the Ubuntu repositories.

---

