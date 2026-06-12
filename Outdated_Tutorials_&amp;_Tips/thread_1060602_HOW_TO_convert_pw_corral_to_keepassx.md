---
title: "HOW TO: convert pw corral to keepassx"
date: 2009-02-04
forum: Outdated Tutorials &amp; Tips
---

### Post by hubiedo on 2009-02-04
i am on ubuntu 8.04 and this is how i converted pw corral to keepassx. 

Note: After additional work with keepass / keepassx a simpler method could possibly be used also - see item 8 below

this is not too fancy but it worked. now that i know how to do it, it isn't too bad but the learning curve was difficult. you will have to set up the databases along the way with your super secret pw.

1. keepassx uses the kdb format. keepass (latest version 2.xx beta)on windows xp uses kdbx format. the trick is to convert these formats

2. GENERALLY: after a lot of experimentation i installed keepass 2.xx on winxp keepass, then installed the older version 1.14 under wine (see below) on my ubuntu and installed keepassx to linux ubuntu. i also experimented a lot to get to these steps so you may need to adjust them as applicable but it should get you in the ballpark

3. on the winxp laptop i exported a csv file from pw corral and i used the file converter from this website:

[http://keepass.info/plugins.html](http://keepass.info/plugins.html)

i used this plugin:

Convert To 1.x CSV

i edited the csv file to get rid of headers and other titles etc. i had it down to the description, login, pw only. 

4. i imported the file to a database on keepass 2.0 on winxp. then since it only had the items noted above ( i had 196 entries) i copied the notes one at a time by setting up pw corral and keepass side by side (don't open the individual items when copying - just go down the list and copy the comments) so now the notes were in keepass also. when done i exported a file from keepass on xp to kbd 1x format named xxxlin keepass export.kbd

5. i installed keepass to wine on linux version 1.14 and opened the database xxxlin keepass export.kbd to xxxlin keepass export.kdb.kdb (don't ask me why it named it like that) but i figured it would be easier to tell them apart in /home/xxx/keepass dir. it also asked did i want to keep the original password i answered yes. you cannot open the files directly in keypassx as it will fail due to incorrect pw. 

6. i then opened the final file xxxlin keepass export.kdb.kdb with keepassx and it finally saved it as xxxlin keepass. it has no extension on the file. ??? i don't know why but it worked and i now have my files in both places. -- actually 3 places. now i have to clean up all of this and the dump pwcorral that has been my pw manager for years and worked great. but i needed to move to linux also.

7. i do not have a shared file for win and ubuntu but from keepassx i think you can export a txt file back to win xp keepass 2.0 but i havent tried it yet. 

8. Additioal Info

You may be able to do this fairly quickly by trying to install the keepass 1.14 on win xp (which uses the .kdb format directly and then "send" it to your linux and open the file in keepassx. you will still have to convert the .txt from pw corral to get started as noted above.

if it opens the file and saves it without an extension (which will be impossible to find again from keepassx, just copy it and rename it from a terminal window and add the .kdb extension.  

i hope this helps someone down the line.

---

### Post by auserica on 2009-09-30
If anyone is interested I've written a Perl script which will convert the plain text password corral export to keepassx xml.  Saves a lot of time...

I've attached the code to this reply.

Bryon

---

### Post by bunklung on 2010-04-17
I kept racking my brain a bit until I found out that you need to use the Classic Version of KeePass to properly use the script file from the KeePass Plugin page.

I kept trying to import CSV files into 2.10 from Password Corral 4.0.4 (which actually has a new CSV option) Don't use the CSV option in Password Corral! Only use plain text file when exporting:

[http://www.antifart.com/2010/04/17/how-to-export-passwords-from-password-corral-into-keepass.html](http://www.antifart.com/2010/04/17/how-to-export-passwords-from-password-corral-into-keepass.html)

Once you have everything working in 1.17, you can use import into KeePass 2.10! Tada!

---

### Post by hubiedo on 2010-04-18
Thanks for the response and addittional info. I think others will appreciate the input in the future.

---

