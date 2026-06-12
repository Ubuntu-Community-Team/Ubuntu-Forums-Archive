---
title: "howto remove libreoffice and reinstall openoffice"
date: 2011-12-30
forum: New to Ubuntu
---

### Post by Old Jimma on 2011-12-30
Hi Ubuntu Community:

I'm running 10.04.

I was having trouble with OpenOffice this morning... big trouble!

So, I followed the instructions at [http://www.ubuntugeek.com/install-libreoffice-in-ubuntu-11-0410-1010-04-using-ppa.html]("http://www.ubuntugeek.com/install-libreoffice-in-ubuntu-11-0410-1010-04-using-ppa.html") to remove OpenOffice and install LibreOffice.

Guess what? LibreOffice will not open my .docx files!

How to I completely remove LibreOffice and reinstall OpenOffice?

I tryied with Synaptic, but couldn't find a way to do it.

Thanks!
Phil de Duluthistan

---

### Post by kaldor on 2011-12-30
Good morning.

It should be a fairly easy task. Remove LibreOffice, remove PPA, install OpenOffice.

1: Remove all the LibreOffice packages from the software centre. 

2: In the Software Centre, go to Edit -> Software Sources. In the Other Software tab, remove or untick the LibreOffice entries. Exit the Software Centre.

3: In the terminal, run the following...

```
sudo apt-get update && sudo apt-get install openoffice
```

This should work. I am on a mobile device right now, so I apologize if I missed anything or was too vague. Feel free to ask for further assistance :)

Also, I would recommend grabbing LibreOffice from the official site. It has some MS Office compatibility enhancements over OpenOffice. The PPA never worked for me.

---

### Post by Old Jimma on 2011-12-30
Hi Kaldor:

I used your approach to remove LibreOffice. I'm pretty sure I've got LibreOffice removed now. I can't find it in my Main Menu anywhere. \\:D/

The coded I used to install LibreOffice was [http://www.ubuntugeek.com/install-libreoffice-in-ubuntu-11-0410-1010-04-using-ppa.html]("http://www.ubuntugeek.com/install-libreoffice-in-ubuntu-11-0410-1010-04-using-ppa.html") had me adding another repository: I
>  sudo add-apt-repository ppa:libreoffice/ppa

So, I went to my "other software sources" that refered to libreoffice, and I unchecked that source, also.

However, the code you recommneded
> sudo apt-get update && sudo apt-get install openoffice

didn't work, so I tried to install OpenOffice from the Ubuntu Software Center. :-k

I Got the message:
>  PACKAGE DEPENDENCIES CANNOT BE RESOLVED. 
This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time.

:oops:

Even after rebooting, the approach you outlined did not work. :|

Can you recomended what else I might try?

I'm grateful for your help, Kaldor!

Sincerely,
Phil de Duluthistan

---

### Post by cortman on 2011-12-30
The latest version of LibreOffice (3.4.3) that came bundled with my 11.10 installation opens .docx files just fine...?

---

### Post by kurt18947 on 2011-12-30
I've found .docx files that LibreOffice won't open as well though my situation right now doesn't require round-tripping MS-Office files.  If I find myself in that situation and the files are more than lightly formatted text, I think I'll look at Softmaker office.  I've installed it as a 30 demo and it opens the problematic files okay. The UI is dated but oh well.   I believe there's an older version (8?) available for free.  I got on their mailing list and they were selling the latest version for around $39 US for a limited time.  I like and use LibreOffice 3.4.4 but it does seem to have issues with heavily  formatted or graphics heavy .docx files.

---

### Post by Old Jimma on 2011-12-30
I appreciate the comments of Cortman and Kurt.

However, my goal is to
[LIST]
[*]delted LibreOffice completed (I think I did that), and
[*]Reinstall OpenOffice (I'm having trouble with that).
[/LIST]

When I use Ubuntu Software Sources to install Open Office, I get the message:

> Package Dependencies Cannot Be Resolved.
This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time.

Can somebody suggest what I might do to overcome this apparent error?

THanks!
Phil Smith

---

### Post by Paddy Landau on 2011-12-30
> **Phil Smith said:**
> Guess what? LibreOffice will not open my .docx files!
That is bizarre. I have Libre Office 3.3.4 straight from the repository (I use 11.04), and it opens .docx files just fine! What version of Libre Office did you have? You might have saved yourself a lot of bother asking for help with that instead.

However, you did ask: To install Open Office:
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

Please let us know if OO opens your .docx files any better than Libre Office did -- I for one would be most interested.

---

### Post by Nesaskewatch on 2011-12-30
I had the same issue when I tried to install Openoffice on 11.10.  Simply will not open, nor is it even listed in the dashboard -- even though software center shows it as being installed.  I saw somewhere that the linux version of Oo is in transistion or something.  Might be why it wont open as a stand alone.  Libre doesn't quite seem ready for prime time.  Not many working extensions nor any templates.  The wizards are extremely buggy.  I have 11.04 on a separate partition and I run Open Office from there.  Maybe the next LT release will have a better version of Libre office?

---

### Post by Paddy Landau on 2011-12-30
> **Nesaskewatch said:**
> Libre doesn't quite seem ready for prime time.  Not many working extensions nor any templates.
You can use the same Open Office extensions and templates for Libre Office -- they are fully compatible.

> **Nesaskewatch said:**
>  Maybe the next LT release will have a better version of Libre office?
I hope so. I'm rather concerned that Libre Office has forked from Open Office, because OO has some spectacular extensions that save me literally hours of time. If Libre Office ceases to support those extensions and then fails to attract the same talent for extensions, oh dear.

---

### Post by Old Jimma on 2011-12-30
Hi All:

I've enjoyed the comments about LibreOffice.

I found a thread on how to install OpenOffice:

[http://ubuntuforums.org/showthread.php?p=8808996](http://ubuntuforums.org/showthread.php?p=8808996)

Good luck!

Phil de Duluthistan

---

### Post by Paddy Landau on 2011-12-31
> **Phil Smith said:**
> I found a thread on how to install OpenOffice
So, did it open .docx?

---

