---
title: "Avoid Microsoft Office when working with Windows users?"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by Lalaith on 2011-11-16
Hi! the newbier of the newbies at a sight!

I installed the Ubuntu 11.10 on my new laptop (Asus X35S), and it is the first time I ever switch to an openSource OS.

The fact is that soon I will work on a project team and **we will be sharing Word docs and Excel sheets all the time**. I tried to **open some of the documents with LibreOffice but unfortunately the format changes** and even the pics that had a Word document have vanished.

So the question is: **How have you solved the compatibility problems of the Office documents with Windows users? **Is a Virtual Machine the only way to solve it?

I could'nt avoid buying a laptop with Windows7 installed and although I  have a dual boot, it's not very useful since I have to restart everytime  I want to change to Ubuntu. And also I have problems because Windows does not see the folders I stored on the partition they both share as "data" (for Linux) /D: (for W's).
So I am considering installing VirtualBox with Windows as a guest OS, but it's a shame because this way, even if I paid for a windows OS, I have to download it again and run a pirate copy, right? 
But this way I won't have problems on sharing the documents between Linux and Windows, isn't it?

Sorry there's so many text! :S

---

### Post by morrna on 2011-11-16
> So I am considering installing VirtualBox with Windows as a guest OS

Another option would be to keep Windows as your primary OS and to install Wubi or another virtual machine to run Ubuntu inside of Windows.  What's the reason you want Ubuntu as primary?  I think you get most of the functionality of Linux in those VMs and I believe data on your HD will be accessible to both Windows and Linux that way. (I have little experience with them, so I could be wrong.)

---

### Post by SheaMan on 2011-11-16
I think there is a program called ..yup! WINE [http://wiki.winehq.org/](http://wiki.winehq.org/)
Pal told me was goot :smirk: with wine you can probably install regler old Office and have no problems.

---

### Post by jockyburns on 2011-11-16
Don't think he'd want to install Wine on a dual boot machine with Win7 and Ubuntu OS's. Kind of defeats the object of Wine.

---

### Post by morrna on 2011-11-16
> **jockyburns said:**
> Don't think he'd want to install Wine on a dual boot machine with Win7 and Ubuntu OS's. Kind of defeats the object of Wine.
Wine would allow him to use MS Office without rebooting though.  Sure, it would be redundant, but it might be worth it.

---

### Post by gordintoronto on 2011-11-16
> **morrna said:**
> Another option would be to keep Windows as your primary OS and to install Wubi or another virtual machine to run Ubuntu inside of Windows....

Morrna: Wubi is not a virtual machine. It allows a person to install Ubuntu without changing any partitions, but you boot into either Windows or Ubuntu.

With a virtual machine, I can be running Windows inside Ubuntu (or the reverse), and can switch instantly with just a mouse click.

---

### Post by CharlesA on 2011-11-16
> **gordintoronto said:**
> Morrna: Wubi is not a virtual machine. It allows a person to install Ubuntu without changing any partitions, but you boot into either Windows or Ubuntu.

With a virtual machine, I can be running Windows inside Ubuntu (or the reverse), and can switch instantly with just a mouse click.

Yep.

I run a Linux VM on most of my Windows boxes since I don't feel like dual booting and there are some things I need linux for.

---

### Post by HermanAB on 2011-11-17
Howdy,

I use Crossover from Codeweavers on a daily basis to run MS Office at work.  Crossover is the leading version of Wine.

[http://www.codeweavers.com](http://www.codeweavers.com)

---

### Post by mastablasta on 2011-11-17
> **Lalaith said:**
>  
The fact is that soon I will work on a project team and **we will be sharing Word docs and Excel sheets all the time**. I tried to **open some of the documents with LibreOffice but unfortunately the format changes** and even the pics that had a Word document have vanished.
 
So the question is: **How have you solved the compatibility problems of the Office documents with Windows users? **Is a Virtual Machine the only way to solve it?

 
can you explain? what format changes? fonts? if it's fonts you can install MS fonts.
 
Also what Office are we talking about here? 2010? Or 2007? 2007 works in wine.
 
there are plenty of notebooks that come barebonmes (no OS installed). i am not sure how you were forced into buying a windows one.  too bad you didnt' ask for advice here first on that issue.
 
anyway wine can run Office 2007 i believe. And it's not really that big of a deal to install it. you won't need to dual boot in this case. a launcher/shortcut will be created and you can run office from inside Linux. wine is a virtualisaiton of sort so it might take a bit more memorry and CPU than if you had run the office in windows.
 
 
if you find wine too difficult to use then indeed crossover is another solution. but i think that one needs to be payed for.

---

### Post by Lalaith on 2011-11-17
some answers:

- My aim is to forget windows, so I never considered playing Linux as a guest and windows as the host OS.  :P

- "i couldn't avoid" buying a laptop with windows because the main brands (HP, Asus, Acer...) simply don't sell them. At least at my country. I know there are some alternatives but I couldn't find much offers.

- as for the documents, the format that changes are not only the fonts (easily straightforward to fix :) ), but unordered lists, enters, tabs, pics that won't show anymore... i'm talking about office 2007. 


So I understand wine or crossover is a simpler way to work with office than a virtual machine? I'll try and if it works, solve the thread. Yeah I know it's redundant, but I'd like to erase windows soon.
Thnx to all! Oh, and I'm not a boy [-X  ;)

---

### Post by Mark Phelps on 2011-11-17
You're not "forgetting Windows" if you're using MS Office; you're staying chained to it!

Office 2010 does NOT work in Wine, or any of its add-ons -- and that is what lots of companies use today.  So if this is the version the others are going to use, you will HAVE to stick with Windows to use it.

---

### Post by Cyclane on 2011-11-17
I used to think that there weren't any non-windows laptops in my country, its to late now but next time try to search for notebook barebones.

---

### Post by Cyclane on 2011-11-17
> **Mark Phelps said:**
> You're not "forgetting Windows" if you're using MS Office; you're staying chained to it!

Office 2010 does NOT work in Wine, or any of its add-ons -- and that is what lots of companies use today.  So if this is the version the others are going to use, you will HAVE to stick with Windows to use it.

Well ain't you negative about this subject. In her situation she's gonna work with a group using MS office and asked us if its possible to work with them from Ubuntu. This is possible by using office 2007 in wine and I believe the file format of office 2010 is compatible with office 2007.

Also office 2010 supports saving files in the odt format. That should be compatible with libreoffice

---

### Post by Grenage on 2011-11-17
> **Lalaith said:**
> - My aim is to forget windows, so I never considered playing Linux as a guest and windows as the host OS.

Short of a dual-boot, or virtualisation - you won't be able to run Office 2010 on the machine.  You may be able to run an earlier version with Wine, but there are no guarantees as to what will work.

---

### Post by Mark Phelps on 2011-11-17
> **Cyclane said:**
> Well ain't you negative about this subject. 

Actually -- NO -- I'm being HONEST!  Folks need to know the truth about what works and what does not work.

> This is possible by using office 2007 in wine and I believe the file format of office 2010 is compatible with office 2007.
It's not a matter of file formats; it's a matter of Office software versions.  Office 2010 (which is what many companies use today) does NOT work in Linux. So, if that's what the other folks are using, she is simply out of luck.  

Better she knows that NOW, than after spending hours trying to get it to work in Linux, only to fail.

> Also office 2010 supports saving files in the odt format. That should be compatible with libreoffice
Yeah ... and everyone I know that uses Office 2010 (and that's lots of folks) simply chooses the default format -- which is the new XML format -- which does not work well in OOO or LibreOffice.

Besides, if she is the ONLY one not using MS Office, why should everyone else change what they do, simply because she does not want to use Windows?

If the situation was reversed, and everyone else was using Ubuntu with LibreOffice, and she was the only one using Windows and MS Office, would you expect all those other folks to mess around with Wine simply because she didn't want to use Ubuntu or LibreOffice?  Of course -- not. Instead, she would be told (most probably) to install Open Office in Windows -- and use that.

Unfortunately for her, the obverse (installing  Office 2010 in Ubuntu and using that) is not possible.

---

### Post by Mark Phelps on 2011-11-17
> **Grenage said:**
> Short of a dual-boot, or virtualisation - you won't be able to run Office 2010 on the machine.  You may be able to run an earlier version with Wine, but there are no guarantees as to what will work.

After years of work, CodeWeavers has been able to make Office 2007 (at least, SOME of it) work reasonably well with Wine.

But, as it was with Office 2007, Office 2010 is starting all over again -- with it not working -- as was Office 2007 for nearly three years.

---

### Post by prookie on 2011-11-17
> **Mark Phelps said:**
> Actually -- NO -- I'm being HONEST!  Folks need to know the truth about what works and what does not work.


> **Mark Phelps said:**
> It's not a matter of file formats; it's a matter of Office software versions.  Office 2010 (which is what many companies use today) does NOT work in Linux. So, if that's what the other folks are using, she is simply out of luck.

True Mark. I was also very enthusiastic about moving completely to Linux OS, but reality is that Microsoft Office tools are used everywhere, and LibreOffice and Open Office are not good enough to edit MS Office documents.

My opinion is:
- MS Office needs to be kept as a backup tool. This can not be avoided because Microsoft is defining the trend of development of office tools.

- LibreOffice is a great tool for creating/editing own private documents and creating PDF versions of them. Exporting to .doc or .docx format is good enough only when there is no such complex formatting.

Anyway, I have a question ...

I want to install MS Office 2007 to use it with Wine.
My installation of Office is crashing in Wine.
I use Ubuntu 10.04 LTS and Wine 1.3.
(I will provide more details about crash if needed.)

Is there any cookbook for defining Wine properties during instalation?
Does someone have similiar experience?

Thank you in advance.

pRookie

---

### Post by LowSky on 2011-11-17
I have had little if no issue using LibreOffice for word or spreadsheets and sharing with MS Office users. The only real issue was macros, but there use is less than 1% of all work I ever touched. Most spreadsheets worked fine. I can save to docx and other formats with little problem.

To make matters even easier I export all my finished work to PDF so that it cannot be edited and it looks exactly as I created it too.

keep in mind you should always use the right tool for any job, and if your place of work uses a certain product you should use the same.

---

### Post by CharlesA on 2011-11-17
> **prookie said:**
> 
Anyway, I have a question ...

I want to install MS Office 2007 to use it with Wine.
My installation of Office is crashing in Wine.
I use Ubuntu 10.04 LTS and Wine 1.3.
(I will provide more details about crash if needed.)

Is there any cookbook for defining Wine properties during instalation?
Does someone have similiar experience?

Thank you in advance.

pRookie

Please post a separate thread on that problem. You might want to check the Wine area too.

> **LowSky said:**
> I have had little if no issue using LibreOffice for word or spreadsheets and sharing with MS Office users. The only real issue was macros, but there use is less than 1% of all work I ever touched. Most spreadsheets worked fine. I can save to docx and other formats with little problem.

To make matters even easier I export all my finished work to PDF so that it cannot be edited and it looks exactly as I created it too.

keep in mind you should always use the right tool for any job, and if your place of work uses a certain product you should use the same.

I've been printing stuff to PDF for ages. It's so much easier then sending off something like a resume in doc format and having it look like garbage cuz the person receiving it doesn't have a specific font or a specific version of Word.

---

### Post by Kellemora on 2011-11-17
Hi Lalaith

I don't know about Office10 so this may not be of much help to you.

I run both Ubuntu 8.04 and 10.04, just haven't updated the other machines because they are set in their ways, hi hi....

I had a lot of problems trying to do things in msOffice using Wine so eventually switched over to Virtual Box and love it for running Microsoft when needed.

Regarding msWord docs, Microsoft sets the margins of Word documents and probably others, based on the Printer connected to the machine the document was created on.  So even if you're on another Microsoft machine with a different printer, Word docs get messed up.  Embedding Fonts fails more often than it works and bloats the files considerably.

Open Office is what I use for almost everything now!
On msWord documents generated on an ms machine with the laser printers, they all converted to odt just fine or I could work with them in their original doc formats and everything looked right.
But if they were created on a machine with an ink jet, most documents had to be readjusted, even if viewed in doc format.

Our company uses numerous proprietary fonts that are not public domain fonts.  This means nearly anyone viewing our files will not see what we see on the pages.  So almost everything we do send out is converted to PDF first, the user WILL SEE exactly what you see!

Now for the Good side of the coin!  I'm a contracted writer for a major publishing company who wants all of their work submitted in Word doc format.  Open Office will save your work as a doc file, but make sure your printer margins (not page margins) are set considerably further in than needed for printing purposes and the conversion and opening in a Word doc program will keep everything where it belongs.

Now for the really downside of Microsoft, they are using some new type of proprietary file for Word that does not convert well at all with any known conversion programs.  I know two publishing houses that switched to it and they lost around 150 to 200 contributors each, including myself, because of it.  Hopefully they will see the light soon!

TTUL
Gary

---

### Post by CharlesA on 2011-11-17
> **Kellemora said:**
> 
Regarding msWord docs, Microsoft sets the margins of Word documents and probably others, based on the Printer connected to the machine the document was created on.  So even if you're on another Microsoft machine with a different printer, Word docs get messed up.

I must be doing something wrong, then, since the margins in Word on 2003, 2007 and 2010 on different machines with different printers are always set to 1 inch all around.

Must be a normal.dot thing.

I print to 2 or 3 different printers and the final document looks the same on all of them. Must be me.

---

### Post by JKyleOKC on 2011-11-17
> **Lalaith said:**
> some answers:

-as for the documents, the format that changes are not only the fonts (easily straightforward to fix :) ), but unordered lists, enters, tabs, pics that won't show anymore... i'm talking about office 2007. 


So I understand wine or crossover is a simpler way to work with office than a virtual machine? I'll try and if it works, solve the thread. Yeah I know it's redundant, but I'd like to erase windows soon.I have a similar situation in that a magazine that I handle for my alumni association gets material from the other staff members in DOC and XLS formats, and sometimes even DOCX. In addition, our printer requires the input in Microsoft Publisher format. However I don't have any version of Windows on my main work machines.

Instead, I've created virtual machines in VirtualBox, installed WinXP Pro and Office 2000 in them, and do all the Windows-related work there. I can switch back and forth with just a mouse click, and it all works smoothly.

If your machine has limited CPU and RAM resources, using a virtual machine can be somewhat slower than working natively. However with at least dual-core CPU capability and 2 GB of RAM (which is almost entry-level hardware these days), the virtual machine is at least as responsive as most native installations. The more resources you have in these areas, the better it will work.

I've also found that AbiWord, which is in the repositories (and is the default word processor for Xubuntu instead of OOO or Libre), does an excellent job of dealing with Word-format files, and is even capable of reading the DOCX format and then saving it back out in DOC or RTF format so that older versions of Word (such as my Word 2000) can handle them. It's what I use when someone sends me a DOCX file!

---

### Post by overcast on 2011-11-17
I have tried my best to ask people around me to use Libreoffice. I know i spent a lot of time convincing some to use openoffice.org and now it is painful to ask again to switch to Libre. In any case, it is hard sometimes to deal with some files from windows users.

---

### Post by Mark Phelps on 2011-11-17
> **Kellemora said:**
> Now for the really downside of Microsoft, they are using some new type of proprietary file for Word that does not convert well at all with any known conversion programs. 

You're probably referring to the ".docx" file extension -- which is the XML DEFAULT format that MS introduced with Office 2007.

And, it's not just Word, it's the same for Excel and PowerPoint.

And, yes, it caused a lot of grief when they did that.  The project I was on at the time did not have the funding to upgrade Office 2003 installation to Office 2007 (we had over 1500 PCs), so every time someone on another project (which had upgraded) sent us a Word, Excel, or PowerPoint file, it was in the new XML format and we couldn't use it.

Eventually, MS came out with Reader versions that could be installed for free, and added format conversion add-ons for those of us "stuck" with Office 2003.

---

### Post by RotorRick on 2011-11-19
Just for clarification, will Office2010 not work in a Virtual Machine?

---

### Post by CharlesA on 2011-11-19
> **RotorRick said:**
> Just for clarification, will Office2010 not work in a Virtual Machine?
It will work in a Windows VM. Just won't work in Wine (which isn't a VM)

---

### Post by RotorRick on 2011-11-20
> **CharlesA said:**
> It will work in a Windows VM. Just won't work in Wine (which isn't a VM)


Thank you!    :D

---

### Post by Lalaith on 2011-11-21
All right, I've seen that the best option for me is to install Wine and execute MS Office 2007. As soon as I get this running, I'll solve the thread.

Thanks to all again, it's surprising how much you can learn from the forums! =)

---

### Post by fractalman on 2011-11-21
> **Mark Phelps said:**
>   Besides, if she is the ONLY one not using MS Office, why should everyone else change what they do, simply because she does not want to use Windows?

.

  Because linux rocks!!!  anyone who still uses windows is a mug!!!!! imo :-)

---

### Post by I2k4 on 2011-11-21
Maybe too late, but the easiest obvious remedy IF (big if) the documents are not too sophisticated, would be the new online version of Office:

[http://www.officelive.com/en-us/](http://www.officelive.com/en-us/)

No fuss no muss, but it won't handle complex formatting.

---

### Post by snowpine on 2011-11-21
If you are in a position of authority in your organization, I strongly encourage you to adopt an open document format (which the current version of MS Office supports). 

Consensus is growing that organizations cannot afford long-term to lock all of their documents into proprietary formats owned by Microsoft. The world's governments are in the process of switching to open formats, hopefully private businesses will follow suit: [http://en.wikipedia.org/wiki/OpenDocument_adoption](http://en.wikipedia.org/wiki/OpenDocument_adoption)

When a business chooses to use Microsoft formats, they are gambling that Microsoft will allow them to read/write/edit these proprietary formats indefinitely at no charge. If Microsoft ever switches to "per use" pricing for Office, then these businesses will be up the creek.

Food for thought. :)

---

### Post by sadaruwan12 on 2011-11-21
The best thing to do is to run a VM with VirtualBox 'cos I work with lot of  MS zombies and they can't see a world beyond that but I managed to open some eyes any way when you work with people who use MS stuff run window as Virtual 'cos it'll minimize lot of trouble.

We could have forgotten MS along time ago but they have the majority so best is to go with it to make things work.

---

### Post by Mark Phelps on 2011-11-21
> **I2k4 said:**
> ...
[http://www.officelive.com/en-us/](http://www.officelive.com/en-us/)

When our folks looked into this, they discovered that you have to upload your files to "the cloud" -- something our Management definitely did NOT want to do.

So, if this is still the same limitation, it won't work unless using "the cloud" is a viable option for the company.

---

### Post by I2k4 on 2011-11-21
> **Mark Phelps said:**
> When our folks looked into this, they discovered that you have to upload your files to "the cloud" -- something our Management definitely did NOT want to do.

So, if this is still the same limitation, it won't work unless using "the cloud" is a viable option for the company.

Certainly an issue.  On the other hand, Google Docs is being marketed to small business clients and even government agencies, on the same basis.  For an enterprise customer, Microsoft might even have a more secure service.

---

### Post by satanselbow on 2011-11-21
> **I2k4 said:**
>  Microsoft might even have a more secure service.

That is sarcasm right? :D


I personally would got the Virtual Machine route. I find WINE buggy and generally infuriating to manage. 

A VM would allow you to run Office 2010 (if that is indeed the version required) whereas WINE would peg you back to 2007.

There is of course no reason why you should not set your local version of office to save as ODT and do your bit for the cause if MSO 2010 were commonplace :popcorn:

---

### Post by Mark Phelps on 2011-11-21
> **I2k4 said:**
> ... On the other hand, Google Docs is being marketed to small business clients and even government agencies, on the same basis. 

And while SOME will succumb to the marketing, others will not.

Just wanted to point out that the "OfficeLive" solution came with some drawbacks.

---

### Post by Lalaith on 2011-11-21
but with Virtual Box you have to set up a lot more things like the folders you share between host and guest OS, the whole guest OS (in this case, Windows), the antivirus... I'm not sure this option is at the end more "troubleshooting" than wine... right?

---

### Post by snowpine on 2011-11-21
> **Lalaith said:**
> but with Virtual Box you have to set up a lot more things like the folders you share between host and guest OS, the whole guest OS (in this case, Windows), the antivirus... I'm not sure this option is at the end more "troubleshooting" than wine... right?

True, but I'll let you in on a secret... VirtualBox has a really nice "snapshot" feature, so you can easily roll back your Windows virtual machine to a freshly-installed, virus-free state. :)

---

### Post by Lalaith on 2011-12-02
> **snowpine said:**
> True, but I'll let you in on a secret... VirtualBox has a really nice "snapshot" feature, so you can easily roll back your Windows virtual machine to a freshly-installed, virus-free state. :)

I don't see the point on it... What do you mean by "snapshot"? Is it like a "restart again from the very beginning"? 

I understand that if I want to run more than one program in Windows, VirtualBox is a lot more advantageous to use, but if I only want to work with one windows program, is it really an advantage to install a whole virtual machine, a host OS and runn the app from within? 

Sorry, I'm just trying to learn. :)

---

### Post by snowpine on 2011-12-02
> **Lalaith said:**
> I don't see the point on it... What do you mean by "snapshot"? Is it like a "restart again from the very beginning"? 

Once your Virtual Machine is set up exactly how you like it, you can take a "snapshot." Then if anything goes wrong (virus for example), you can restore to that snapshot. You can even have multiple snapshots. Think of them as "restore points" or "saved games." :)

---

### Post by BC59 on 2011-12-02
> **Mark Phelps said:**
> 
Office 2010 does NOT work in Wine

Now with Wine 1.3 it's working perfectly. I posted here my results:

[http://ubuntuforums.org/showthread.php?t=1885051](http://ubuntuforums.org/showthread.php?t=1885051)

---

### Post by JKyleOKC on 2011-12-02
> **Lalaith said:**
> I understand that if I want to run more than one program in Windows, VirtualBox is a lot more advantageous to use, but if I only want to work with one windows program, is it really an advantage to install a whole virtual machine, a host OS and run the app from within? 

Sorry, I'm just trying to learn.I think it is; I have nine different VMs installed on this box, all but one of them running either WinXP or Win2000, and each of those is devoted to a single application or project. Most of the time, all nine are in "saved" state, which is similar to hibernation of a laptop; they take up a few GB of disk space but no other resources. When I need to work on my income tax return, I fire up the "ttax" VM and everything is there ready to go. If I have a database recovery job to do for a client, I fire up "datasave" and so on. When I'm not using them, they are stored away on the disk and can easily be backed up to an external drive with no hassle.

That one non-Windows VM is where I experiment with other flavors or versions of Linux, with no risk of damaging my main system.

I don't use snapshots as such, although the "saved" state creates a special snapshot for each that's automatically restored the next time I start that VM.

---

