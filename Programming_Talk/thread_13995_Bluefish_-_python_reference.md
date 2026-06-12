---
title: "Bluefish - python reference?"
date: 2005-02-04
forum: Programming Talk
---

### Post by domzo on 2005-02-04
After reading the good comments about bluefish I decided to try it out. It looks pretty good so far.

However I have a question... 
On my machine at work (Suse 9.2) the 'function reference' (panel on the left hand side) has a reference of Python commands (as well as HTML, PHP and CSS2). This is really handy.

However, when I installed bluefish on Ubuntu (using Synaptic), the python reference is missing :cry:

I'm sure it must just be a plugin or something I need to install, but I can't work out where what or how. Does anyone know where to get the python reference???

cheers, 

domzo

---

### Post by stroopwafel on 2006-02-05
I have the same question: I can't open the php ref on the left hand side panel.

Can anybody help us?

---

### Post by David Marrs on 2006-02-06
It works ok on my machine. Do you both have the documentation packages installed for python and php?

---

### Post by stroopwafel on 2006-02-14
[QUOTE=David Marrs]It works ok on my machine. Do you both have the documentation packages installed for python and php?[/QUOTE]

I just installed bluefish using "apt-get bluefish"
How do I install the documentation packages for php?

---

### Post by David Marrs on 2006-02-15
try "sudo apt-get install phpdoc"

---

### Post by stroopwafel on 2006-02-16
[QUOTE=David Marrs]try "sudo apt-get install phpdoc"[/QUOTE]


I tried it but it didn't work:
```
SWOne:~$ sudo apt-get install phpdoc
Password:
Reading package lists... Done
Building dependency tree... Done
Package phpdoc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package phpdoc has no installation candidate

```
What else can I try to install html and php references in bluefish?

---

### Post by Vinze on 2006-11-25
> **stroopwafel said:**
> I tried it but it didn't work:
```
SWOne:~$ sudo apt-get install phpdoc
Password:
Reading package lists... Done
Building dependency tree... Done
Package phpdoc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package phpdoc has no installation candidate

```
What else can I try to install html and php references in bluefish?

Try sudo apt-get install php-doc

---

### Post by shannonbrown on 2010-12-17
**_Problem:_** development language references not available in side panel of Bluefish (e.g., Python, Perl, etc.).

This may help.

According to the Bluefish 2+ Manual Project (see [http://bfwiki.tellefsen.net/index.php/Side_Panel]("http://bfwiki.tellefsen.net/index.php/Side_Panel")), the Info Browser plug-in is NOT enabled by default after installation.

**Potential Solution:** Enable Info Browser
1) Open Bluefish.
2) Select EDIT...PREFERENCES
3) Navigate to the PLUGINS entry
4) Check the Info Browser checkbox.
5) select APPLY.
6) Select OK (closes the PREFERENCES window).
7) ***[Optional]*** Close and re-open Bluefish.
8 ) You should now see the Info Browser item in the SIDE PANE [By default the side pane is the window on the left of the editor.] The Info Browser TAB icon is a round blue icon with an 'i' letter in the middle and is located at the bottom of the left side, SIDE PANE.
9) ***[Optional]*** If you do not see the SIDE PANE, press f9 or navigate to VIEW ... SIDE PANE. 

SB

---

