---
title: "Problem with executing programs from within a Perl script"
date: 2005-10-02
forum: Programming Talk
---

### Post by agora on 2005-10-02
I have just installed Ubuntu Hoary Hedgehog on computer that I use for doing some programming, mostly in Perl. After the system change the scripts started to return errors  (they used to worked correctly under Slackware 9.1 - the previous system on this computer). The problem is with executing other programs or Perl scripts from within the mother script by writing something like this:
system (“Perl_Script.pl”); or `Perl_Script.pl`;
Perl_Script.pl is an executable file, with the standard header #!/usr/bin/perl -w. 
Adding directory before the script name (system (“$current_dir/Perl_Script.pl”); ) solves the problem, but I am wondering if there is another way to do it, since I am not eager to look into hundreds of Perl scripts and modules I wrote so far;) . Do you have suggestions, please.

---

### Post by toojays on 2005-10-02
If these scripts are all in the same directory, you could add that directory to your PATH environment variable.

---

### Post by agora on 2005-10-03
Thanks, but unfortunately they are not in the same directory :???:

---

### Post by Oberjaeger on 2005-10-03
You could add ./ to your path, which while not a great idea, would fix the problem. 
Or, write a perl script to drill through the directories that the scripts are in and edit the system calls.;)

---

