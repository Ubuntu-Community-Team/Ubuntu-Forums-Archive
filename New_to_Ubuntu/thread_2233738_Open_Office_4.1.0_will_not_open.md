---
title: "Open Office 4.1.0 will not open"
date: 2014-07-10
forum: New to Ubuntu
---

### Post by sillyboy on 2014-07-10
Using Ubuntu 12.04 Gnome 2

Installed OO 4.1.0.  I will not open, or open any of my .odts.  Did a check "check if already posted" and received No Results... ??? :confused:

Thanks

---

### Post by vasa1 on 2014-07-10
> **sillyboy said:**
> Using Ubuntu 12.04 Gnome 2

Installed OO 4.1.0.  I will not open, or open any of my .odts.  Did a check "check if already posted" and received No Results... ??? :confused:

Thanks
You may have to run it from a terminal and post the output you get in the terminal here. Only thing is I don't know how to launch OpenOffice Writer from the terminal. Maybe someone else knows the command and will post it here.

---

### Post by Dennis N on 2014-07-10
> **vasa1 said:**
> You may have to run it from a terminal and post the output you get in the terminal here. Only thing is I don't know how to launch OpenOffice Writer from the terminal. Maybe someone else knows the command and will post it here.

Try this:

[FONT=Courier New]**ooffice -writer**[/FONT]

This is the command in Ubuntu 10.04 for ver. 3.2 - probably still the same.

---

### Post by Bucky Ball on 2014-07-10
```
soffice --writer
```

That will get writer launched. I imagine

```
soffice
```

... would probably launch office. Try them. I use Libreoffice, but I believe the command is the same in either. The first release where Libreoffice became the default (12.04?) I had issues installing Open Office. I ended up giving up and going with the flow and using Libreoffice. Love it. 

Have you tried Libreoffice? Should be installed by default. Don't like something about it? Virtually identical to OO and problem free on all my installs/computers. :)

---

### Post by sillyboy on 2014-07-10
> **Dennis N said:**
> Try this:

[FONT=Courier New]**ooffice -writer**[/FONT]

This is the command in Ubuntu 10.04 for ver. 3.2 - probably still the same.

I tried it and still no go...

I did a sudo apt-get update, and got this: 
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures 
were invalid: BADSIG 1629D03F4B894331 Launchpad PPA for CPU-G Developers

Does anyone know what the above means?

Thanks

---

### Post by sillyboy on 2014-07-10
> **Bucky Ball said:**
> ```
soffice --writer
```

That will get writer launched. I imagine

```
soffice
```

... would probably launch office. Try them. I use Libreoffice, but I believe the command is the same in either. The first release where Libreoffice became the default (12.04?) I had issues installing Open Office. I ended up giving up and going with the flow and using Libreoffice. Love it. 

Have you tried Libreoffice? Should be installed by default. Don't like something about it? Virtually identical to OO and problem free on all my installs/computers. :)

Here is what I got with the above code:

```
System-Product-Name:~$ soffice
/opt/openoffice4/program/soffice.bin: symbol lookup error: /opt/openoffice4/program/libsvxcore.so: undefined 
symbol: _ZThn648_NK18SvHeaderTabListBox11GetRowCountEv
```

Thanks

---

### Post by Dennis N on 2014-07-10
> **sillyboy said:**
> I tried it and still no go...

I did a sudo apt-get update, and got this: 
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures 
were invalid: BADSIG 1629D03F4B894331 Launchpad PPA for CPU-G Developers

Does anyone know what the above means?

Thanks

Look Here. There are several solutions to sort out:
[http://askubuntu.com/questions/1877/what-is-the-easiest-way-to-resolve-apt-get-badsig-gpg-errors/](http://askubuntu.com/questions/1877/what-is-the-easiest-way-to-resolve-apt-get-badsig-gpg-errors/)

---

### Post by Bucky Ball on 2014-07-10
Please use [code] [ /code] tags for terminal output. Easier to read and neater. (Edit post #6 and have a look at the way I've used them for your code there. ;))

How did you install it? Repostitory? Deb? From Software Centre? Things don't look right by that error. There appear to be bits missing where they're expected to be. *Did you uninstall Libreoffice first?* Like purge it? :-k

---

### Post by vasa1 on 2014-07-10
> **Bucky Ball said:**
> ```
...
[CODE]soffice
```

... I believe the command is the same in either. ...
That's what this link has as well: 

[http://www.openoffice.org/download/common/instructions.html#linux-preinstall](http://www.openoffice.org/download/common/instructions.html#linux-preinstall)

Among other things, it explains how to install Apache OpenOffice on a system which already has LibreOffice. But, from a casual reading, I doubt one can switch back and forth without some pain.

---

### Post by Bucky Ball on 2014-07-11
> **vasa1 said:**
>  But, from a casual reading, I doubt one can switch back and forth without some pain.

That's been my experience. In fact, I've never succeeded in having them both installed at the same time.

---

### Post by sillyboy on 2014-07-11
> **Bucky Ball said:**
> That's been my experience. In fact, I've never succeeded in having them both installed at the same time.

I don't understand a lot of these things.  That's why I'm still in the Absolute Beginners Section.  Can I totally remove OO 4.1.0 and install Libreoffice with out causing more problems?  If so... how?

Thank You

---

### Post by vasa1 on 2014-07-11
> **sillyboy said:**
>  ... Can I totally remove OO 4.1.0 and install Libreoffice with out causing more problems?  If so... how?
...
Could you share how exactly you ended up with OpenOffice on your system? To my mind, LibreOffice should be installed by default unless you've done things to your system you haven't explained to us or you have a non-standard system.

---

### Post by Bucky Ball on 2014-07-11
> **vasa1 said:**
> Could you share how exactly you ended up with OpenOffice on your system?

Yes, I mentioned this before, and I too am curious. Unless you removed Libreoffice, it should still be there so you don't need to re-install it. Remove Openoffice instead. 

If you check the history, Libreoffice is an offshoot of OO by ex-OO devs and they are virtually identical, but, as you've discovered, not quite, cos they don't play nice.

---

### Post by deadflowr on 2014-07-11
> **Bucky Ball said:**
> Yes, I mentioned this before, and I too am curious. Unless you removed Libreoffice, it should still be there so you don't need to re-install it. Remove Openoffice instead. 

If you check the history, Libreoffice is an offshoot of OO by ex-OO devs and they are virtually identical, but, as you've discovered, not quite, cos they don't play nice.

Typically to install OOo you need to remove libreoffice first.This is because they share a few things, notably the file soffice.bin.
If the file is on the system already, the install borks up.
Normally, to install OOo you grab the OOo tar package, extract, move into the folder and run
```
sudo dpkg -i *.deb
```
I've never done it, but I believe there is a way to reinstall libreoffice.
But I think it involves installing it as well from Libreoffice tar package from the libreoffice site.

You can remove openoffice with apt-get if you want.
Probably the best answer as of yet
[http://askubuntu.com/questions/319367/openoffice-didnt-install-correctly-how-do-i-remove-it](http://askubuntu.com/questions/319367/openoffice-didnt-install-correctly-how-do-i-remove-it)

---

### Post by sillyboy on 2014-07-11
> **Bucky Ball said:**
> Yes, I mentioned this before, and I too am curious. Unless you removed Libreoffice, it should still be there so you don't need to re-install it. Remove Openoffice instead. 

If you check the history, Libreoffice is an offshoot of OO by ex-OO devs and they are virtually identical, but, as you've discovered, not quite, cos they don't play nice.

Hello,

I removed Libreoffice and installed OO, following instructions online.  I have been using OO since I was using Windows years ago.  I was just used to it.  Since OO seems DOA, I guess I'll try to use Libreoffice, if I can. Is this possible at this point?

Thanks

---

### Post by Bucky Ball on 2014-07-11
See deadflowr's post #14. Might give you some clues. If you can uninstall OO, I would simply try reinstalling Libreoffice from Software Centre (unsure why that wouldn't work if OO was gone), but deadflowr's advice might be the only option if that doesn't work.

---

### Post by claracc on 2014-07-12
I have found this link: [https://forum.openoffice.org/en/forum/viewtopic.php?f=5&t=65361](https://forum.openoffice.org/en/forum/viewtopic.php?f=5&t=65361), where is discussed the use in windows of LO and OO, but there is an insteresting comment in it about working in linux systems that perhaps addresses the problem:

>Villeroy wrote:Now I recall that both suites want to use the symlink /usr/bin/soffice.
>The --force-overwrite option resolves this problem pointing the symlink to the newly installed >suite. You can manually change the target at any time.

So, the solution seems to be to change the pointing of symlink in case you want to use one LO or other OO office suite (and as far as I know, no need to uninstall any of them).

---

### Post by sillyboy on 2014-07-12
> **claracc said:**
> I have found this link: [https://forum.openoffice.org/en/forum/viewtopic.php?f=5&t=65361](https://forum.openoffice.org/en/forum/viewtopic.php?f=5&t=65361), where is discussed the use in windows of LO and OO, but there is an insteresting comment in it about working in linux systems that perhaps addresses the problem:

>Villeroy wrote:Now I recall that both suites want to use the symlink /usr/bin/soffice.
>The --force-overwrite option resolves this problem pointing the symlink to the newly installed >suite. You can manually change the target at any time.

So, the solution seems to be to change the pointing of symlink in case you want to use one LO or other OO office suite (and as far as I know, no need to uninstall any of them).

Thanks to all who answered.  Problem solved.  Went to SPM, and removed all green (installed) marked entered for LO and removed.  Did same for OO in SPM.  Rebooted.  Reinstalled LO thru Software Center.

Thanks again  :p:p:p

---

