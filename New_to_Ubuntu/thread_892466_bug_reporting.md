---
title: "bug reporting"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by ub newb on 2008-08-17
Hi, 

I signed up for launchpad, and read the wiki page on bug reporting but I am still a bit confused. I used synaptic to install amaya and when I tried to open amaya from the menu icon, the application GUI flashed onscreen for a second and then off. 

So I have two questions as a noob, is this a bug, and since apport didn't open, how would I file a report on it? 

I am running Ubuntu 8.04 as the only OS. 

thanks

---

### Post by dje on 2008-08-17
open a terminal (applications >> accessories >> terminal) and type this:
```
amaya
```
post the output here

to report bugs go to [here]("https://launchpad.net/ubuntu/+filebug") also look at bugs already filed against amaya [here]("https://launchpad.net/ubuntu/+bugs?field.searchtext=amaya&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=")

dje

---

### Post by Costas100 on 2008-08-25
Sorry to pop in uninvited, I just had the same problem with amaya and followed your instruction from the terminal. This is what I got back:

[03:49:09 PM: Deleted stale lock file '/home/costas/.amaya-costas'.

(amaya:15329): Gtk-CRITICAL **: gtk_widget_set_colormap: assertion `!GTK_WIDGET_REALIZED (widget)' failed
The program 'amaya' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 7700 error_code 8 request_code 142 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
costas@]

I have no idea how to use the sync command. I am running Ubuntu Studio, which maybe the problem. I think it is time to reformat and install 8.04 after I get acquainted with terminal commands.

Sorry again if I am intruding
Costas

> **dje said:**
> open a terminal (applications >> accessories >> terminal) and type this:
```
amaya
```
post the output here

to report bugs go to [here]("https://launchpad.net/ubuntu/+filebug") also look at bugs already filed against amaya [here]("https://launchpad.net/ubuntu/+bugs?field.searchtext=amaya&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=")

dje

---

### Post by LowSky on 2008-08-25
ubuntu studio is ubuntu with extra packages and that isn't your issue.

this seems to be an issue with the repos versiom from debian/ubuntu repos
Also try turing off compiz before using it might help.

try installing the deb from amayas website
[http://www.w3.org/Amaya/Distribution/amaya_10.0.1-0ubuntu1_i386.deb](http://www.w3.org/Amaya/Distribution/amaya_10.0.1-0ubuntu1_i386.deb)

if that doesn't work try this version, it a pre release for 10.1
[http://wam.inrialpes.fr/software/amaya/amaya_10.1-pre3-0ubuntu1_i386.deb](http://wam.inrialpes.fr/software/amaya/amaya_10.1-pre3-0ubuntu1_i386.deb)

---

