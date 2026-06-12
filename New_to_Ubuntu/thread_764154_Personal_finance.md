---
title: "Personal finance"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by hawiko on 2008-04-23
Hello,
I have installed UBUNTU Ver.6.06 and love it. I would like to replace Windows XP with it but can't because I have no program to replace Quicken which I am using for my small business finances.I have downloaded Grisbi and can't get it to run and I have downloaded Gnucash and can't get it to run. So I desperately need help, DETAILLED instructions  and I mean D E T A I L L E D on how to proceed.
Can someone out there help this novice with easy to follow instructions ?

hawiko:(:(:(

---

### Post by wolfen69 on 2008-04-23
why cant you get them installed? where did you get them?

---

### Post by Thelasko on 2008-04-23
Did you install from the repositories?
In the terminal type:
```
sudo apt-get update
sudo apt-get install gnucash
```

---

### Post by timzak on 2008-04-23
If you don't want to mess with the terminal, go to Synaptic Package Manager or Add/Remove Programs, search for Gnucash and install from there.  It will automatically set it up for you so you can run it.  Also do a search on "financ" in Synaptic/Add-Remove and you'll get a couple of more options, which you might like better.  Those off the top of my head I can think of are Gnucash, Grisbi, Homebank, and Kmymoney2.  There is also a pay program called Moneydance that has gotten good reviews.  Google it.  It's about $30 and you have to install it yourself.

Good luck.

---

### Post by PinkFloyd102489 on 2008-04-23
I use Homebank and it works just fine. You can get the latest package from getdeb.net.

---

### Post by hawiko on 2008-04-26
Hello again,
first up I would like to thank all the people that responded to my first post and now comes the hammer:
I am at my witts end. First I took timzak's advise and tried to install Gnucash and then Grisbi from Synaptic Package Manager.Both times I got the message "Please insert the disk labelled Ubuntu 6.06_Dapper Drake_Release i386 (20060531.2) in drive/cdrom ( that disk I don't have).
Then I tried PinkFloyd102489's advise and downloaded and installed Homebank from getdeb.net and voila it is installed. But where is it ? How can I run it ? There is no Icon on the desktop, no set up like in Windows  and I can nowhere find it to run it.???

:confused::( hawiko

---

### Post by Island_Jon on 2008-04-28
MONEYDANCE FEATURES / REVIEWS
----------------------------------
[http://www.linuxjournal.com/article/4555](http://www.linuxjournal.com/article/4555) [long escrip of settg it up ]

[http://www.linux.com/article.pl?sid=05/10/31/1653227](http://www.linux.com/article.pl?sid=05/10/31/1653227)

[http://www.linux.com/article.pl?sid=05/10/31/1653227](http://www.linux.com/article.pl?sid=05/10/31/1653227)

 I've been converting to Linux (Ubuntu) for about 1 year.  Quicken was one of the applications that required a serious Linux replacement (GnuCash I tried, but not quite the thing for me).   All I really used in Quicken was the check register.  I researched the matter and finally paid $40 for Moneydance since it was user friendly.  The only other thing I've paid for under Linux has been Acronis backup.  Moneydance runs under Mac and Windows too since it's written in Java (a little slower than GnuCash).

Moneydance did import (after you export from Quicken) all my years of entries in the check register; you have to set up the "accounts" for the categories first in MD.  It was trickier with the mortgage loans.

After many years of PC use I know that it pays to choose a winner when devoting a lot of time and effort to master an important software application.

Moneydance could really succeed in this era of Vistafright Microflight.

Good luck.

---

### Post by ad_267 on 2008-04-28
Is there any reason you are using 6.06? The latest version is 8.04, you may have more luck with that.

---

### Post by Jive Turkey on 2008-04-28
For the most part I've been happy with GnuCash.  However, the ofx-direct-connect feature is not supported by default unless you compile the source yourself along with some of the dependencies that aren't documented very well.  I won't mess with any such program unless it has that feature.  

I havent got it compiled under Hardy yet as the dependencies were unsatisfiable.

I'm not using it for a business but mainly for a checking account register, with ofx enabled I can download transactions from my bank and reconcile with my own records in just a few seconds.  I also track my expenses with it and I have used the invoicing functionality for shared expenses with roomates, It was pretty slick for that.  I also like that you can make it show debit/credit columns.

You say you are using 6.06, why such an old version?

To get this to work for you:

you may need to remove the cd from your sources list, I'm not sure what that would look like in dapper, I havent used it since ...actually I started in ubuntu at edgy and stayed current but for Hardy I go to the menu "System">"Administration">"Software Sources" and uncheck everything in "Installable from CD-ROM/DVD."  If that option doesnt exist in your ubuntu version, you may need to modify a file called "sources.list"

to do so type or copy/paste this command into a terminal:```

sudo gedit /etc/apt/sources.list

```
this should open a text editor with read write privileges to the file.  Notice how some of the lines in the file begin with a "#"?  This is a comment marker and it means that the line is ignored by the apt program which installs software for you.  Find the line that mentions the CD-ROM and put a comment marker("#") in front of it.  click save and close, then run these commands:
```
sudo apt-get update
sudo apt-get install gnucash
```

... while connected to the internet.  You can start gnucash from the Applications>Office>GnuCash menu item or typing "gnucash" in a terminal and pressing enter assuming you have it installed.

You could also browse the repositories with firefox for the gnucash-x.x.x.deb file, download it and double click on the .deb file to install it.  Hope this helps.  

As for the program you installed but cant find, try in a terminal:
```
whereis nameofprogram
```
replace nameofprogram with the actual name of the program, you can use "*" as a wildcard at the end of you are feeling lazy.  If whereis cant find your program it will print:
> nameofprogram:
and nothing else.  If it does it will print the path to all the files that match your query.  you can then locacate and attempt to run the file.

ok first try typing "homebank" in a terminal without quotes, it should just work.  If it does you can create a desktop shortcut using the right-click menu on your desktop with "homebank" in the command feild, you will likely have to specify an icon too.

post back if you have any problems.

---

### Post by neilevan814 on 2008-05-17
Just curious, I am trying to set up my online banking with a compatible linux program.  Have you tried online banking with this program?

Thanks, Neil

---

### Post by undadecor on 2008-07-14
Online banking in GnuCash works great.  Here's a simple How to involving .deb packages instead of compiling:  [http://ubuntuforums.org/showthread.php?t=854770](http://ubuntuforums.org/showthread.php?t=854770)

---

### Post by LowSky on 2008-07-14
as for the error with "please insert cd"

got to menu>system>admin>software sources.. on the first tab uncheck the box labeled something check install CD (should toward the bottom)

---

### Post by miajade20 on 2008-10-02
yes i did. the merit of using linux is increased security. but demerit is slow processing. [quick personal loans ]("http://quickpersonalloans.cn")site was started on linux but soon changed

---

