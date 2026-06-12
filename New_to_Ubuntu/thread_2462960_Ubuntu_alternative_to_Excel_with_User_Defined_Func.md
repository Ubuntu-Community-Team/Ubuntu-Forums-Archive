---
title: "Ubuntu alternative to Excel with User Defined Functions"
date: 2021-05-31
forum: New to Ubuntu
---

### Post by mattrix2 on 2021-05-31
Windows refugee here. Not sure where to post this, So I have put it here as I am a newbie.

I often get excel files from other people that have User Defined Functions written in VBA, and have to pass these files back to Microsoft users. The UDFs  mostly do not use Microsoft's Object Model but sometimes they do.

I have searched and found contradictory information about whether or not the Linux options will support these files or not. Apparently Open Office could be made to support most of these features when it was in the hands of Novell, but recent reports on Oracles offering is that it no longer does. So I am confused.

I am able to open these XLS & XLSX files with Excel 2007, so they do not use anything really recent.

I know I am being a little lazy here, I have not yet made the switch to Ubuntu, and am still trying to familiarize myself with how to do things using Ubuntu Live. Just want to do some pre-planning before the big leap.

I am not looking for a cloud solution, and have read good and bad things about:
Soft Maker Free Office.
Kingsoft/WPS Office 
and lastly Libre Office, or better older versions of Open Office.

But there are many other contenders referred to on the net.

Can anyone recommend the most compatible Linux Office, especially with regard to VBA UDFs, & if possible Microsoft's Object Model?

---

### Post by ActionParsnip on 2021-05-31
Does the VBA do very complicated stuff that you couldn't recode in something like Python or Bash? Then feed back into the spreadsheet?

---

### Post by mattrix2 on 2021-05-31
Some of it does do complicated stuff.

From what I understand Python is a very capable language and could easily do everything VBA does. However at this time I would not be able to convert VBA to Python.

---

### Post by grahammechanical on 2021-05-31
Surely the place to enquire about Libreoffice is the Libreoffice web site.

[https://www.libreoffice.org/](https://www.libreoffice.org/)

I can tell you this. In Ubuntu 20.04 Libreoffice is at version 6.4.7.2. Ubuntu 20.04 is a Long Term Support Release and Libreoffice is one of those default applications that get updated throughout the support life of the Ubuntu version.

There are versions of Libreoffice for Windows. Install the latest Windows version and test it out.

Regards

---

### Post by scorp123 on 2021-06-01
> **mattrix2 said:**
>  I often get excel files from other people that have User Defined Functions written in VBA, and have to pass these files back to Microsoft users... 

Same problem here.

You could use Microsoft Office 365 and either download/use Excel (e.g. into a virtual machine?) or give the web-based online version a try?
[https://www.microsoft.com/en-us/microsoft-365/excel]("https://www.microsoft.com/en-us/microsoft-365/excel")

Also before you sign up for anything maybe check with your employer? Many companies that officially use Microsoft Office do have company-wide Office 365 licenses these days so you should be able to get full functionality for as long as you're employed there. At my current job and the one before it was certainly the case for me: as per license agreement between my employer and Microsoft I was allowed to download and run up to 5 x instances of Word, Excel, PowerPoint, Visio, etc. "for private use", and that included running those softwares inside Windows virtual machines or using the online versions. I don't run Windows on any of my desktops so having these options available to me so I can still fill out company-related paperwork was kind of important ... and it worked and still works pretty well for me.

> **mattrix2 said:**
>  I am not looking for a cloud solution ...

Why not? Chances are your employer most likely already is a Microsoft Office 365 customer, and so are you indirectly, at least for as long as you are employed there. If that's the case then it would open up the possibility to legally make use of those services and download Word, Excel etc. into a virtual machine and run the latest Excel that way. 

At least that's how I do it.

---

### Post by mattrix2 on 2021-06-01
Thanks all,

Why not cloud? I am often in places with no or limited internet access.

No employer support for this project.

I am also considering a virtual machine, but not sure if Microsoft will register my software. The point of the move to Linux is so that I don't have to give more $$ to Microsoft. If I have to pay Microsoft to get a workable solution, I might as well stay with Windows, at least it is familiar.

---

### Post by scorp123 on 2021-06-01
> **mattrix2 said:**
>  The point of the move to Linux is so that I don't have to give more $$ to Microsoft. If I have to pay Microsoft to get a workable solution, I might as well stay with Windows, at least it is familiar.

Well, while I can certainly understand *"don't want to give more $$ to Microsoft"* the reality is that interoperability with their IT world won't come free. It will either cost you money or time (e.g. time to find suitable replacements, time to learn those new products, time to adjust your way of working, time to get used to your new OS and how it does things ...) but it will not come "free". The question you have to ask yourself is which one can you afford to spend? Money or time?

Alternative approach: can't you get your contacts to not use Excel? e.g. if whatever solution that necessitates Excel could be moved to e.g. a web-based solution with e.g. a database back-end (e.g. Apache + MySQL maybe?) then the whole need for Excel would go away.

---

### Post by rsteinmetz70112 on 2021-06-01
Libra Office has some compatibility with VBA, but how well it works is beyond my experience. Your best bet would be to download Libra Office and try some of the spreadsheets.

[https://help.libreoffice.org/latest/lo/text/sbasic/shared/vbasupport.html](https://help.libreoffice.org/latest/lo/text/sbasic/shared/vbasupport.html)

One of the issues with looking on the Internet for stuff like this is that it is often outdated.

---

### Post by alanthelinuxguy on 2021-06-03
> **mattrix2 said:**
> ...and am still trying to familiarize myself with how to do things using Ubuntu Live.

Have you tried running the Excel file and macros under LibreOffice Calc in the live version of Ubuntu?  As rsteinmetz70112 noted, Calc now offers some support for VBA.  I was surprised to find one of my Excel macros, that I thought used some "obscure" VBA statements, actually ran perfectly in Calc.

If you are running a live version of Ubuntu, you must still have Windows installed as the main OS.  Why not dual-boot your machine by installing Ubuntu "side-by-side" with Windows, i.e. in a separate disk partition.  The GRUB boot menu will allow you to select which OS to boot into.  This is the system that I use. Linux Mint is the default OS, and I boot Windows when I want to develop/run Excel macros.

Another option, if you are intent, on eliminating Windows, may be to use Wine to run Excel from within Linux.  Various versions of Excel have differing levels of compatibility under Wine.  see: [https://appdb.winehq.org/objectManager.php?sClass=application&iId=11](https://appdb.winehq.org/objectManager.php?sClass=application&iId=11)

Finally, I don't think you should have any difficulties establishing a Windows VM under Linux; however, you should be able to test this by initially dual-booting and trying to create a Windows VM on the Linux side.  If this works satisfactorily, you could then either remove Windows or reinstall Linux using the entire hard drive.  If you are going to blow away Windows completely, I would suggest that you make a full disk image of your system - just in case you change your mind!

---

