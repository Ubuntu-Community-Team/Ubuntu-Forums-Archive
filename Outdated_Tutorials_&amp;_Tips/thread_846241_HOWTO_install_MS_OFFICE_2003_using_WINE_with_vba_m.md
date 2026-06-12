---
title: "HOWTO install MS OFFICE 2003 using WINE with vba macro support"
date: 2008-07-01
forum: Outdated Tutorials &amp; Tips
---

### Post by ukripper on 2008-07-01
**_[SIZE="5"][COLOR="DarkGreen"]How to use  MS OFFICE2003 using WINE with VBA support[/COLOR][/SIZE]_**

Install WINE 1.0 or greater from Wine website [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) or if you are using Hardy you can install it from ubuntu repos.

After wine has been installed -

Put your MS office 2003 cd in your drive and in terminal type following:
```
cd /media/cdrom0
```
```
wine autorun.exe
```

And follow instructions as if you were installing it on windows.

Now on your desktop **right click** -->**Create launcher** for each below

Create launchers for each application:
in Command field type this
For excel:
> env WINEPREFIX="/home/your_username/.wine" wine "C:\Program Files\Microsoft Office\OFFICE11\EXCEL.EXE"

For Word:
> env WINEPREFIX="/home/your_username/.wine" wine "C:\Program Files\Microsoft Office\OFFICE11\WINWORD.EXE"

For powerpoint:
> env WINEPREFIX="/home/your_username/.wine" wine "C:\Program Files\Microsoft Office\OFFICE11\POWERPNT.EXE"

For Access:
> env WINEPREFIX="/home/your_username/.wine" wine "C:\Program Files\Microsoft Office\OFFICE11\MSACCESS.EXE"

You are almost done.

Now if you are having problem running your macro then you need to install Dcom98.

Dcom98 contains three dlls from Windows 98: ole32, oleaut32, and rpcrt4. Use winetricks to install it:
In terminal type:
```

wget http://www.kegel.com/wine/winetricks
```
```
sh winetricks dcom98
```


The winetricks script will set to override globally, and if you have any other programs installed in that wineprefix it may affect them. If that happens, you can fix it through winecfg.

Congratulation! Now you have running MS OFFICE 2003 on your ubuntu.

---

### Post by kkjensen on 2008-09-02
Is there really VBA support?  I've tried crossover but nothing vba related seems to work at all.

---

### Post by ukripper on 2008-09-03
> **kkjensen said:**
> Is there really VBA support?  I've tried crossover but nothing vba related seems to work at all.

For OFFICE 2003, yes! VBA macros are fully supported, to some extent you can achieve VBA macros using openoffice as well.

---

### Post by russetaylor on 2008-11-13
So far all my macros are working with this!  None were working in a previous crossover install of Office 2003.   Thanks ukripper!

---

### Post by TwiceOver on 2008-11-13
How is Outlook?  Maybe I'll try this tomorrow as I want to know if the Exchange connection works.

---

### Post by ukripper on 2008-11-14
> **TwiceOver said:**
> How is Outlook?  Maybe I'll try this tomorrow as I want to know if the Exchange connection works.

I've personally never used outlook under ubuntu or any other distro through wine. I'd rather use evolution/kmail for that purpose.

Evolution can be used with exchange server if you have OWA enabled on the server otherwise use Kmail and Kontact which have more features to go with exchange.

---

### Post by ukripper on 2008-11-14
> **russetaylor said:**
> So far all my macros are working with this!  None were working in a previous crossover install of Office 2003.   Thanks ukripper!

i am glad it is working for you!! As I write quite a lot of macros in VBA, it had made life alot easier, thus no need to rewrite the macros in openoffice anymore.:)

---

### Post by kilou on 2008-11-14
Does MS Access 2003 work under Wine? Apparently it doesn't work with Crossover...

---

### Post by ukripper on 2008-11-14
> **kilou said:**
> Does MS Access 2003 work under Wine? Apparently it doesn't work with Crossover...

It does work for me. I don't use it extensively anyway just to check few schemas before i can alter in DBDESIGNER, I mostly use excel with vba. 

MYSQL server would be better option for databases, just an opinion.

---

### Post by kilou on 2008-11-14
OK thanks, I'll first try it in virtualbox because doing the install on my system. If Office really works on Ubuntu + Wine then I'll probably be able to totally drop off XP :)

---

### Post by ukripper on 2008-11-14
> **kilou said:**
> OK thanks, I'll first try it in virtualbox because doing the install on my system. If Office really works on Ubuntu + Wine then I'll probably be able to totally drop off XP :)

Virtualbox would be extra overhead on your system if you just want XP for Access. I would instead install WINE + OFFICE on ubuntu first then go with virtualbox; if Wine didn't workout.

---

### Post by arnold.pietersen on 2008-12-28
> **ukripper said:**
> It does work for me. I don't use it extensively anyway just to check few schemas before i can alter in DBDESIGNER, I mostly use excel with vba. 

MYSQL server would be better option for databases, just an opinion.

Hi Ukripper

Just checking if you could give some steps on how you got Access 2003 to work under Wine. I am using Wine 1.0.1.  

Access starts up.  However, when I create or open a database, it bombs out.

Any help will be appreciated.

---

### Post by augoldfinger on 2009-01-03
Outlook Nor Access will work:(


Out of the Office programs I have used Outlook for 9 years. I have ran my email from that program from that long. I have a 5000 individual customer data-base so I won't be changing from MS Office any time soon.

The Programs that do work, I really care about is Word, & Publisher...I really only care about Word because it is used in conjunction with Outlook, & I really only care about Publisher because I use it to make business flyers 

I used Crossover on my Dapper Drake with great success. Since Ubuntu went to 7.1 my program I bought from crossover never worked. Wine Never worked for me either. It was my hopes that 8.10 would work:confused:

---

### Post by raymund on 2009-03-03
Hi, I tried running VBA macros in Ubuntu 8.04 (Virtualbox on a WinXP machine) and got two error messages:

System Error &H80004005 (-2147467259). Unspecified error.

Out of memory 

Some googling turned up this [link]("http://kbalertz.com/230888/Error-Running-Macro-UserForm.aspx"), which gave a workaround.  However, that workaround involved removing userforms from my VBA project.  

I installed Excel 2003 in Ubuntu 8.04 from the OEM disks I bought with my XP machines.  The version number is 11.5612.5606.  Have later versions of Excel 2003 solved this problem?  My Win XP version, duly registered and updated, is version number 11.8012.6568 SP2.  My userforms work fine in the more up-to-date Win XP version.  

Has anyone gotten userforms to work for later versions of Excel 2003 in Ubuntu 8.04?  Or for Excel 2003 11.5612.5606 in 8.04 not running through Virtualbox?

---

### Post by Saghaulor on 2009-03-04
Followed the howto, but when I run excel, the splash screen loads and will not close. Consequently, I can't do anything with excel because any attempt to do anything results in a system beep and no response.

Any ideas?

---

### Post by studavis on 2009-04-18
I had all sorts of problems with 8.10 and never got Wine to work properly. 8.04 worked a bit better (suspend etc) but Wine never worked well. I have just changed to 9.04, fresh install Wine 1.0.1, no dll changes. Office 2003 (XL, PP and Word) worked fine. Until I imported my settings, that froze XL and I could not uninstall. Had to remove Wine and delete the directory. Fresh install works fine so you'll have to live without all your MS settings. Just added VBA support as described in this thread, works, fine although it's a bit slow.  

Juanty seems to have better Wine/2003 compatibility. With 8.04 my screen would go balck when saving files (in Wine), now it jsut flickers a bit. All in all, Jaunty/Wine 1.0.1 has don it for me.  Good luck

---

### Post by russetaylor on 2009-05-08
Saghaulor #15 -- Just make sure you open Word before Excel after the Office install.  Word will ask you for the name & initials to use within Office.  Once you enter these within Word you can go back to Excel and it will open fine.  I know this works because it has happened to me on several different computers.  For some reason I don't remember this and I always try to open Excel first after an Office install.  Why the name & intial screen for Office freezes Excel but not Word, I have no idea?

---

### Post by Tinhare on 2010-03-11
> **russetaylor said:**
> Saghaulor #15 -- Just make sure you open Word before Excel after the Office install.  Word will ask you for the name & initials to use within Office.  Once you enter these within Word you can go back to Excel and it will open fine.  I know this works because it has happened to me on several different computers.  For some reason I don't remember this and I always try to open Excel first after an Office install.  Why the name & intial screen for Office freezes Excel but not Word, I have no idea?

Actually it hasn't frozen Excel. The name and initials screen is open and hidden behind the Excel splash screen and there is no way to access it.

I also found that if I restarted the machine as I couldn't close Excel either then when I restarted Excel it started and asked if I wanted to run it in safe mode.
Chose Yes and then I was able to put in the user name and initials.

However the above workaround is a better solution, just thought I'd post the answer as to why Excel appears to freeze.

Cheers,
Alan.

---

