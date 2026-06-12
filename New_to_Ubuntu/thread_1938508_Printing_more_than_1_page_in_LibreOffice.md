---
title: "Printing more than 1 page in LibreOffice"
date: 2012-03-09
forum: New to Ubuntu
---

### Post by Ganeshx on 2012-03-09
Hey.  I am trying to print a one page document from LibreOffice.  It works, but it will only print one at a time, no matter how many I set.  I need about 55-60 copies printed by tomorrow morning, and it seems a bit tedious to print one at a time.

Any fixes?

---

### Post by Script Warlock on 2012-03-09
have you set the range and copies properly? like all documents and number of copies.

---

### Post by _0R10N on 2012-03-09
In the bottom-right corner of your printing options windows there's an option to set the number of copies you want.

---

### Post by Ganeshx on 2012-03-09
> **Script Warlock said:**
> have you set the range and copies properly? like all documents and number of copies.

Yes.  I've checked so many times now.


> **_0R10N said:**
> In the bottom-right corner of your printing  options windows there's an option to set the number of copies you  want.

I realize this.  It still only prints one copy, no matter how many I set.

---

### Post by Ganeshx on 2012-03-10
Bump.

---

### Post by critin on 2012-03-10
> **Ganeshx said:**
> Bump.

Troubleshoot the printer through its Help page/site/manual

---

### Post by roger_1960 on 2012-03-11
Hi Ganeshx

You are not alone!

I have the same problem with Libreoffice and 10.04 with a Brother DCPJ315W.  Very strangely, my other Ubuntu 11.10 PC and a Macbook print multiple copies fine to the same printer using Libreoffice.

I looked on the Brother site and found a thread which said (for Openoffice) to tick the "collate copies" box when printing.  This didn't work for me, but you could try it.  Otherwise do post back if you find the answer.

---

### Post by gymka on 2012-03-18
after update to libreoffice 3.5 i'm too have this problem. earlier everything was ok, before libreoffice update everythin gworked.
OS: archlinux

---

### Post by kurt18947 on 2012-03-18
I wonder if there's an issue with Libre Office and Brother's printer drivers talking to one another.  I have a problem with envelopes.  I tell Libre Office I want to use a #10 envelope.  Print preview shows correct formatting.  The Brother printer is determined that I want to print a DL envelope :mad:. My fix (it's a PITA) is to go to printing -> right-click the printer icon, left-click 'properties', then left click the appropriate category.  For copies, it's under 'job options'.  For paper size/type, it's 'printer options'.

---

### Post by Azdour on 2012-03-19
Hi,

We are also having this issue on two separate printers (HP and Samsung). It seems the ppa version of LibreOffice has a bug in it:

[https://bugs.freedesktop.org/show_bug.cgi?id=46904](https://bugs.freedesktop.org/show_bug.cgi?id=46904)

Its kind of frustrating that a bug so simple to test for has slipped through the net....

Edit: Looks like libreoffice 3.5.1 has been released. Lets hope that by the time it makes it to the PPA that this bug is fixed

---

### Post by Azdour on 2012-03-23
Hi,

Looks like the issue has not been fixed in the 3.5.1 update.

---

### Post by Pilot6 on 2012-03-27
This issue can be easily fixed.

You need to edit file /etc/libreoffice/psprint.conf

Replace 
;PSLevel=0

by

PSLevel=2

---

### Post by roger_1960 on 2012-03-28
Hi

Thanks - that works!  For anyone else, you do need to delete the semi colon at the start of the line as well as change 0 to 2.

Open the file for editing in terminal  with
```
gksudo gedit /etc/libreoffice/psprint.conf
```
and enter your password.  Edit and save.

---

### Post by Azdour on 2012-03-28
Hi,

Unfortunately that did not work for me, I'm on Ubuntu 10.04, LibreOffice 3.5.1.2

---

### Post by roger_1960 on 2012-03-28
Hi again

It worked on 3.5.0 build 13. with 10.04  I havn't done the last update yet - I'll try soon.

---

### Post by roger_1960 on 2012-03-28
Hi

Just did the latest update.

Now using 
LibreOffice 3.5.1.2 
Build ID: 350m1(Build:102)

and it (see posts #12 and #13) still works...multiple copies print as expected.

---

### Post by Azdour on 2012-03-28
Hi,

That's really strange. I have the same version as you and I've tried a number of things including the fix in #12 but if I have a single page document and ask for 2 copies I only get one.

---

### Post by Pilot6 on 2012-03-28
> **roger_1960 said:**
> Hi

Thanks - that works!  For anyone else, you do need to delete the semi colon at the start of the line as well as change 0 to 2.

Open the file for editing in terminal  with
```
gksudo gedit /etc/libreoffice/psprint.conf
```
and enter your password.  Edit and save.
What do you mean by this? Just open the file and close it? PSLevel sets printer language from PDF to Postscript level 3. You may try level 1 or 2 depending on your printer.
PSLevel=0 sets PDF instead of driver default.
With postscript it seems OK with multiple copies.

---

### Post by roger_1960 on 2012-03-28
Hi Pilot6

I meant just to explain how to edit the file according to your earlier post, by edit, I meant change the line

; PSLevel=0

to 

PSLevel=2

as you suggested.

---

### Post by Pilot6 on 2012-03-29
> **Azdour said:**
> Hi,

That's really strange. I have the same version as you and I've tried a number of things including the fix in #12 but if I have a single page document and ask for 2 copies I only get one.

My method "does not work" after you use spadmin. You need to clenup after it.
Delete file psprint.conf from ~/.config/libreoffice/3/user

and remove new lines starting with name of you printer in [] in /etc/libreoffice/psprint.conf

Or just change PSLevel in ~/.config/libreoffice/3/user

---

### Post by Azdour on 2012-03-30
Hi Pilot6,

Thanks for the help on this issue.

> Delete file psprint.conf from ~/.config/libreoffice/3/user

There is no psprint.conf file located there.

> remove new lines starting with name of you printer in [] in /etc/libreoffice/psprint.conf

I'm not sure what you are asking here. I've looked at /etc/libreoffice/psprint.conf and the only things in [] are [__Global_Printer_Defaults__]
and [Generic Printer]. There is nothing that mentions the name of the printer I use.

---

### Post by Pilot6 on 2012-03-30
It seems that you did not use any setup programs. So, you just need to remove ; and change 0 to 2. Do not use 3, since it seems not to work.

---

### Post by Azdour on 2012-03-30
Hi,

Sorry, I have already followed post #12. That was the first thing I tried...

---

### Post by Curtis6767 on 2012-03-30
I'm on 12.04 with latest 3.5.1.2

I had problem printing multiple copies, but went into Properties and then Device and changed the default PDF to PostScript(level from driver)

I also un-checked Collate, but I'm not sure that had anything to do with this.

Printing multiples now but having to go into Device each time and select PostScript.

dysfunctional but works until a fix comes along, I guess.

---

### Post by Pilot6 on 2012-03-30
I posted how to set defaults to postscript. Not to have to change it every time you print.

---

### Post by Curtis6767 on 2012-03-30
Got it working by changing the '0' to '2'.

Thanks

---

### Post by Joshun on 2012-04-01
Can I just say thanks to everyone who posted this, it's such a simple fix, and has saved my day!
:popcorn: :guitar: :KS

---

### Post by Azdour on 2012-04-03
Hi,

I can now happily confirm that it is fixed and post #12 did the trick. Our setup here is slightly different as we use DRBL. I had to refresh all the psprint.conf for all the clients. Thanks Pilot6.

---

