---
title: "Help with Permission Denied Problem"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by SweetGAPeach on 2012-08-01
OMG, this is my first time using a Linux operating system.  Could someone PLEASE help me with an error.  I am trying to launch MicroSoft Word, but I keep getting a message about permission denied.  Any tips on how I can get permission granted?  Thanks.................:confused:

---

### Post by levlaz on 2012-08-01
Microsoft Word does not work in Ubuntu unless you install it with crossover office. 

If you're using Ubuntu there is a program called LibreOffice already installed that has all the same functionality of word and is compatible.

---

### Post by SweetGAPeach on 2012-08-01
Thanks, I used it a few times.  However, when I attempt to download Word docs from the internet, the system is asking "What program to open it with"....I have no idea how to find one.  And I'm concerned because my Microsoft package was working fine until today..............................

---

### Post by levlaz on 2012-08-01
> **SweetGAPeach said:**
> Thanks, I used it a few times.  However, when I attempt to download Word docs from the internet, the system is asking "What program to open it with"....I have no idea how to find one.  And I'm concerned because my Microsoft package was working fine until today..............................

Libreoffice should open word documents by default. Try to save them to your downloads folder and open them from there.

I am a little confused that you say word has been working...how is this possible? 

How did you install word? Which version of word is it? (2002,2007,2010??)

---

### Post by SweetGAPeach on 2012-08-01
I have Word 2007.  I purchased my tower from a local computer store and Word 2007 was already installed.....???

---

### Post by SweetGAPeach on 2012-08-01
I can use Writer, but I prefer Word.  I'm an online student and Writer is not one of the supported softwares.......................

---

### Post by levlaz on 2012-08-01
I am very confused lol.

So you purchased a computer with Linux on it ... that had Word installed? 

Sorry this is just very uncommon and I want to make sure we are on the same page.

---

### Post by levlaz on 2012-08-01
Do out get the "permission denied" when you try to open a specific file or just when you try to open word?

---

### Post by SweetGAPeach on 2012-08-01
Now I'm totally confused.......since it's uncommon

---

### Post by SweetGAPeach on 2012-08-01
It only happens with the Microsoft package.  I was having a problem the other day and tried to fix it myself. ..... can't remember exactly what I did.  But I remember googling and found a solution.  I went to a software folder, right clicked, and chose some type of change that affected 'permissions'

---

### Post by SweetGAPeach on 2012-08-01
I have purchase 2 new computers and both were destroyed by viruses....which I believe originated from my school's online blackboard.  At any rate, I decided to purchase a used computer from a local computer repair shop.  I explained my concern about viruses and that's when the owner told me about Linux...so I purchased the computer???

---

### Post by mlentink on 2012-08-01
> **SweetGAPeach said:**
> I can use Writer, but I prefer Word.  I'm an online student and Writer is not one of the supported softwares.......................

To use documents, it is irrelevant whether your school support the software or not. Usually they support a file-format, which is something else. You can read and produce  .doc documents with LibreOffice just fine, but I would alert your school that the internal format of LibreOffice is an open standard (the Open Document standard) that they should support.

With levlaz I'm curious as to how Word 2007 came to be installed on an Ubuntu box. This is highly unusual, as Word can only by run on Linux with special supporting software, and even then not completely. How did the company you bought it from sell you this? Did they tell you it would work? And if so, did they guarantee it?

Come to think of it, we could use a bit more info. What version of Ubuntu (linux) are you using? How do you start up Word? Is there a menu item for it?

---

### Post by houseworkshy on 2012-08-01
Some help but mostly a bump.
  
I'd recomend installing a program called sysinfo in order to most easily answer some of the questions your would be helpers have asked.  The quick way is to open a terminal and enter "sudo apt-get install sysinfo" it will ask for your password and after that install.  It will put a link in the "System tools menu" click that to run it, then choose to save a file ( save it anywhere, the desktop will do ).  That file will have all your system specs.  It's a useful thing to have anyway.

The other thing to do is change the file associations from word to libreoffice  or open office.  That is quite easy, just right click on a word file ( it's listing in your file manager, not inside the opened file itself )  and look at it's properties to get to open the box you can change it from.  Use the "open with" tab, on my system that causes a global change.  You will find a permissions tab in the same box, I don't know what you did but be sure that you have read and write permissions for yourself and you don't need to allow it to be executeable.  Make sure you have libreoffice or openoffice installed first, no point associating with a non-existant.

When saving files you have made which you want to open at school choose "save as" rather than save.  There is a drop down menu which lets you choose from many file types.  Just in case the school Word processor has problems, which is very unlikely but can sometimes happen, save a second version in rich text format ( .rtf ) which any old thing can read.  That way you are covered.

The help documentation on this site if very good and I recommend it.  [https://help.ubuntu.com/](https://help.ubuntu.com/)   Well worth reading as it includes some installers ( something called apt;urls, which may not be safe elsewhere but are here ) so you can set up some of the applications you'd like to have as you learn.  Could go through the whole thing in an hour or so.  Perfect first step.

Handy to have something like this on the drive too ( it's free ) [http://ubuntu-manual.org/downloads](http://ubuntu-manual.org/downloads)  just choose the appropriate version.

Enjoy, and one thing the owner was right about is that linux is still far less prone to malware.

Some extra bits and bobs.  

Most things in a linux can be done via the GUI but as I don't know which one you have I'll mention the command line way which is the same for all linuxes bar a few slight differances in package management etc.  To use command lines open a terminal to put them in.  Not sure where that will be on your system, sometimes accessories, sometimes system tools.  It will certainly be there anyway.

If you didn't set it up I'd be tempted to change passwords.  The quick way is via the terminal and the command is passwd.  Rather than explain it I'll mention another usefull source of help which you always have with linux.  For help on commands just enter "man" in front of one, that will take you to the manual page for it.  In this case it would be "man passwd", when you've finished reading enter "q" to close the page and go back to the terminal.  "man man" shows how the help works.  One  can have many terminal windows open at a time so I like to have one for the help and one for what I'm doing.

There is a firewall in Ubuntu but it is not turned on by default.  Maybe the previous owner has already done this or installed a graphic way of manageing it but just in case he/she hasn't....

"sudo ufw default deny"  first then followed by "ufw enable" will set up a safe default.  The reason I didn't use "sudo" for the second command is because what "sudo" does is grant full admin powers for 15 minets for whatever follows in that terminal so if quick the second command won't need it.  If you waited longer then 15 minets before putting in the second command you'd need to put sudo in front of the second command.  Browsing in admin is never wise so to end the sudo timer early enter "sudo -k".  If you want more detail "man ufw" and "man sudo" will give it.

The last bits are a bit command lineish.  Don't get the wrong idea and be put off by that.  In day to day use linux is just as graphic as windows or mac's ( actually it can be even more so.  search for "compiz" in youtube for a glance at what it can do)   it's just that I don't know which of the many graphic user interphases you have installed and the commands work in anything.

---

### Post by levlaz on 2012-08-01
I'm sorry I can't be of more help because honestly I have no idea what the problem is. 

On a side not I finished an online degree while I was in the Navy and even though my school "didnt support" anything but MS word I finished the entire degree while using OpenOffice. 

Perhaps you could try posting this question in the Wine forums. Theymay have more people who are familiar with these types of issues.

---

### Post by mikaelcrocker on 2012-08-01
This may be stupid but have you tried **sudo**, or whatever files you're trying to access you may be able to change the permissions on them using **chmod**.  I don't know exactly what it is, but if you're a novice user, seems like I shouldn't rule it out.

---

### Post by SweetGAPeach on 2012-08-01
I am not a program expert.  I studied DOS back in high school, that was 20 years ago.....at any rate.  I know Microsoft software works on my computer, I bought it used....it was already installed.  It has worked for 6 months now.  I know how to access the terminal and type the codes, but I have no clue what programming language to use along with sudo.  Unfortunately, I cannot troubleshoot it myself.....I am only familir with Windows and DOS, Visual Basic.......  I checked the directory in the terminal and I see the Microsoft office software there.  Not sure how to tell you what system I am using.  I guess I can restart the PC and check.  The only thing I know is Linux, ubuntu, and Gnome....ROTFLMBOH...thanks

---

### Post by levlaz on 2012-08-01
I am assuming you are running MS Office in WINE. If so I would move this conversation over to [WINE HQ]("http://www.winehq.org/")

They may be able to help you better since more users on there use WINE and probably MS office.

---

### Post by Dawnbandit on 2012-08-02
> **SweetGAPeach said:**
> Thanks, I used it a few times.  However, when I attempt to download Word docs from the internet, the system is asking "What program to open it with"....I have no idea how to find one.  And I'm concerned because my Microsoft package was working fine until today..............................
You'll need to install wine to run it. Or use Play On Linux.

---

### Post by haplorrhine on 2012-08-02
> **SweetGAPeach said:**
> I can use Writer, but I prefer Word.  I'm an online student and Writer is not one of the supported softwares.......................
Like other contributers, I have used LibreOffice for schoolwork.  Just ask professors about supported formats.

libreofficeforum.org and help.libreoffice.org provide good instructions.

---

### Post by cortman on 2012-08-02
SweetGAPeach: Are you using Ubuntu? How do you know?

---

### Post by drmrgd on 2012-08-02
I've been wondering the same thing.  However, let's get some empirical data here.  Would you please run the following commands, and post the output here (even if it's just an error!) for us using the Code Tags (hash tag looking thing) please:

```
lsb_release -a
``` 

```
uname -a
```

```
ll ~/.wine/drive_c/Program\ Files/
```

To be sure the syntax is correct, you can just copy and paste what I've put here.  This will help us identify your OS, architecture, and whether or not there is an MS Office install in Wine (if it installs where I think it does that is!).

This will at least be a start to understand what you're seeing and trying to do.

---

### Post by SweetGAPeach on 2012-08-03
Thanks for your help.

When I enter:   
lsb_release -a
[U]
The response is:[/U]
Distributor ID:    Ubuntu
Description:    Zorin OS 5.2
Release:    11.04
Codename:    natty

---

### Post by SweetGAPeach on 2012-08-03
Then after entering-  

uname -a

I got this response---

Linux chambers-System-Product-Name 2.6.38-15-generic #64-Ubuntu SMP Fri Jul 6 17:18:17 UTC 2012 i686 athlon i386 GNU/Linux

---

### Post by SweetGAPeach on 2012-08-03
And lastly, after entering---

ll ~/.wine/drive_c/Program\ Files/

I got this reply----

total 16
drwxrwxr-x 4 chambers chambers 4096 Jul 26 01:15 ./
drwxrwxr-x 5 chambers chambers 4096 Jul 26 01:15 ../
drwxrwxr-x 2 chambers chambers 4096 Jul 26 01:15 Common Files/
drwxrwxr-x 2 chambers chambers 4096 Jul 26 01:15 Internet Explorer/


Thanks again

---

### Post by SweetGAPeach on 2012-08-03
Btw, this is the error msg I receive when trying to launch Word 2007:

There was an error launching the application.

Details: Failed to execute child process "/home/chambers/.cxoffice/Microsoft Office 2007/desktopdata/cxmenu/StartMenu.C^5E3A^5Fusers^5Fcrossover^5FStart^2BMenu/Programs/Microsoft+Office/Microsoft+Office+Word+2007" (Permission denied)

---

### Post by SweetGAPeach on 2012-08-03
I have wine and play ....still won't open : (

---

### Post by mlentink on 2012-08-03
If I look at the output, you don't need Wine, you're already using Crossover, which is based on Wine. Since I use neither, I really can't help you with your issue, but I would strongly advise posting on the Crossover support forums.

---

### Post by SweetGAPeach on 2012-08-03
How do I find the crossover support forum and will I get busted for reposting the question there?  Someone busted me earlier for a repost...lol

---

### Post by houseworkshy on 2012-08-03
The operating system you are using is Zorin OS 5.2 11.04.  It's website  is here [http://zorin-os.com/](http://zorin-os.com/)  I don't know much about that one.  It's a  linux with a GUI interphase made to resemble windows.  It is a  crippleware OS, the phrase is not intended as a flame, I use it for  software which one can use for free in a basic form but have to pay some  money to get full functionality.  Similar to shareware.
  
Like windows there are several prices, not a lot the highest seems to be  $15 + $3 for post and packing for a physical disc of their ultimate  version.   You'd have to check the site for any extra charges.  I have  read several posts here from people who are very happy with it.  Linux  dressed as windows appeals to many windows users as it seems to be an  easy transition.  I was never crazy about windows anyway so Zorin's not  for me which is why I don't know much about it.

The Zorin users will though they have a forum here [http://www.zoringroup.com/forum](http://www.zoringroup.com/forum)

If you don't like zorin there are many choises in linux, this site is the best I know for hunting and links to reviews [http://distrowatch.com/](http://distrowatch.com/)

Most distro's are free.  And many run live which means you can download,  burn to a cd or dvd, then boot with that in the drive to get a taste of  what they are like without changeing your system.  You could even use  the word processor on one of those and save you work to a memory stick  as a stop gap whilst you work out the MS word in Zorin problem.  I guess  deadlines may be pressing.

---

### Post by CharlesA on 2012-08-03
Good detective work houseworkshy. I poked around the Zorin site and it looks pretty "meh" to me, but I guess the versions that cost money include paid software.

Transfering the document to a USB stick and booting another Distro live would be a good idea.

---

### Post by drmrgd on 2012-08-03
Ahhhh....there we go, Crossover Office on Zorin.  Unfortunately, I am not familiar with either.  However, houseworkshy's advice is great - hit up the Zorin forums to see if anyone has any advice there.

---

### Post by SweetGAPeach on 2012-08-03
Thanks for your help everyone.

---

