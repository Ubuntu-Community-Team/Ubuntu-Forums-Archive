---
title: "printer won't print"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by briar rabbit on 2012-04-30
Hello,

I am trying to get a printer to work on my Ubuntu 10.04

I have the hplip installed.

I have a hp deskjet 5550 and it is recognized by something called "Manage Print Jobs".  However there is no printing going on.  It merely says 'Status' 'Stopped'.

The problem may be that I have no dialog box as such is in the screenshot for the hplip in the Software Center.

I tried to install 'hplip-gui' thinking this gui would be the screenshot I have seen 'advertised'.  I get the following warning when I try to mark this for installation.

=====
Could not mark all packages for installation or upgrade

The following packages have unresolvable dependencies.
Make sure that all required repositories are added and
enabled in the preferences.

hplip-gui:

  Depends: hplip (=3.10.2-2ubuntu2) but 3.10.2-2ubuntu2.2 is to be installed
=====

I looked for "3.10.2-2ubuntu2' in the synaptic manager but did not see it.

I do not know command lines.
Shouldn't the printer or hplip be in the Applications like the Manage Print Jobs?

If someone could help me with this it would be great.

---

### Post by Hadaka on 2012-04-30
"printer stopped" sounds like you interupted a print job with your attempt to add some file.
Are you trying to add the printer...or simply test it by sending a file to it to print?

---

### Post by briar rabbit on 2012-04-30
Thanks Hadaka,

> "printer stopped" sounds like you interrupted a print job with your attempt to add some file.

I don't think so. every test I send to it says 'stopped'. 

> 
Are you trying to add the printer...or simply test it by sending a file to it to print?

The printer is added I guess cause its listed in the 'manage print jobs'
Yes I am trying to test it but, going through 'manage print jobs' does not seem like the right thing to be doing.

I do wonder why it is that the printer does not give me the dialog screen like it shows it has in the Software Center.  And, where is the printer located, how do I reach it?  Do you know what I mean?  Like I can go to the movie player whether I am playing a movie or not, why can't I go to the printer?

---

### Post by Hadaka on 2012-04-30
IF..your printer is installed..here is a simple terminal command to test it.
ctrl alt t   open a terminal
code:

echo "Ubuntu is best" > testprint
lp testprint



please post back any errors or mark solved if it prints
thanks

---

### Post by briar rabbit on 2012-04-30
It says 'command not found'
you may have missed the part above that says I do not do command lines very well.

What do you know about the dialog box for hplip as it is seen in the software center?

---

### Post by Hadaka on 2012-04-30
There are only 2 simple commands
open a terminal by pressing Ctrl and Alt and T at the same time
a black screen will pop up
type in these two commands one line at a time followed by pressing enter


echo "Ubuntu is best" > testprint

lp testprint



or simply copy and past them one line at a time
Im not a 10.4 user so i dont now about dialog box for printing....if there even is one.

HP usually loads by just plugging it into the usb port, im surprised you are having
a problem.

good luck

---

### Post by Hadaka on 2012-05-01
Hello again..were you able to get your printer to print?

I looked up your printer..HP5550...its just a basic printer, no fax,no scan no
toaster oven or bread maker like alot of the new multi function printers. Just
a basic printer..for text..pics or documents.
I also looked in the software center at the HPLIP application
its pretty much a 3rd party program that adds bells and whisteles for such
things as sanning..and other functions your printer doesnt do. Its not really
supported by the ubuntu boys nor are there any upgrades for it.
I'm not quite sure what you were expecting from this application HPLIP
The type of printing you will be doing is basic...text..pictures and the like.
Almost any aplication you are using...libra office family..shotwell..or whatever
usually has a print icon at the top of the page..this is where you tell your printer
to print...not export the file to HPLIP. you can also always click the "file" and then choose Print.
so..I hope i havent confused you more..just trying to figure out why you think you have a printer
problem. HP is very linux friendly. Its usually a hands free operation to add the printer, just plug in
the usb port..and its all magic from there..no commands needed..no questions to answer..it just adds
it as your default printer. Try those 2 commands i sent you in terminal mode just to verify it will print.

---

