---
title: "creating configuration-installation script"
date: 2007-05-24
forum: Programming Talk
---

### Post by diamantis13 on 2007-05-24
Hi, 
I am making an application that depends on some other programs and libraries. I would like to create an installation script that would check if these programs and libraries are already installed. Does anybody know where can I find some information about how to build such a script? I do not know whether should it be an sh script? Could it be a .deb or .rpm package?
Thank you very much!

---

### Post by Metacarpal on 2007-05-26
There are a number of ways you could go about this (ah, the beauty and ultimate frustration of Linux).  A shell script is one way to go.  For example, if you have the names of all of the binaries and libraries it would depend on, you could have them listed in a text file, then:

```
FAILDEPEND=0
for IDEPEND in `cat *name_of_text_file*`
do
[INDENT]FINDDEP=`find / -iname $IDEPEND`
if [ -z $FINDDEP ]
then
[INDENT]echo "Could not find needed file $IDEPEND"
FAILDEPEND=$(($FAILDEPEND+1))[/INDENT]fi[/INDENT]done
if [ "$FAILDEPEND" -gt 0 ]
then
[INDENT]echo 'Failed to install - one or more dependancies were missing.'
echo 'Please install the files listed as missing above, then run this installer'
exit 1;[/INDENT]
fi
```
Of course, that would require the installer running as a user that had read-access to the paths the dependancies would be in, such as root.

That's only one of many ways of going about it, though.  There are, I'm sure, others that are more elegant and efficient.

Oh, and almost anything can be made a .deb or .rpm

---

### Post by odiseo77 on 2007-05-27
@ diamantis13: I'd suggest you reading [this guide]("http://www.debian.org/doc/maint-guide/"). it's very good and it's a good chance to learn new things. Basically, If you're building a .deb package you need to edit the 'Depends:' line of the 'control' file under the 'DEBIAN' directory (this is in case you're building a package from binaries, if you're using sources and following the guide I just linked to, the debian tools handle all the dependencies detected during the compilation process).

Regards :)

---

