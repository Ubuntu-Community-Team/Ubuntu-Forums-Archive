---
title: "Canon Ip2600 driver issue"
date: 2011-04-27
forum: Outdated Tutorials &amp; Tips
---

### Post by torontopronto on 2011-04-27
Hi guys,

i thought I'd share my experience in trying to get the canon Ip2600  driver to work.  This has been a frustrating experience especially for  someone who is not a programmer and is new to Linux.

So as it turns out I got frustrated to MS Windows and was determined to  move over to Ubuntu.  I happen to have no less than 4 Canon Ip2600  printers (I do a type of home business, they are cheap printers and I  have a ink-fill system setup).  You can just imagine my frustration when  Ubuntu could not run the canon printers.  I spent a lot of time doing  research from a lot of people posting in this forum and other forums.   So many people would follow the posts and report back saying, "thanks -  great - my printer works now..." yet I followed the instructions and my  printer did not work.  I think the biggest insult is when there is a  post title that says, "SOLVED".  The issue wasn't necessarily solved....  just some people got it right.

I wish somebody at canonical or one of you intrepid programmers would  program a patch as this appears to be a problem for all canon printers.   I came across what appeared to be a patch but the site where the patch  was meant to be located was non-existent.  But until the day we can  simply click on a patch - or an Ubuntu upgrade makes an allowance for  this issue, I thought I'd give you guys a step by step guide in a "Linux  for Dummies" level.  

Just as I highlight: **Much of what I have here was actually posted by others, I have just combined the whole process into one loooong post for you.**   

Also, please remember this is how I solved the problem on my computer -  this process will work for both the i386 machines and AMD64 machines:

So what are we going to do:
A) You are looking to download two compressed driver files from the  Canon internet site - the "cnijfilter common" and the "cnijfilter  ip2600".  

B)You will then be looking to make an adjustment to these compressed  files.  After the adjustment, you will then re-package those driver  files.

C) you will launch the driver installation - at this stage people with AMD64 computers will use a slightly different process

D)   You will enforce a "chown root " command on the various directories (something to ensure that the filter does not fail)

E) **you will select the correct PPD file on installation.** (I made  this last one bold only because I have not found this last requirement  in any of my extensive research on the topic and I am hoping it is the  final process that helps you out)


(i believe this process also works if you have something other than an  ip2600 - you will have to apply your own logic to make sure you download  the appropriate driver file)

**Items A, B, C** above will be repeated twice for the two files that will need to downloaded, modified, repacked and launched:
 
(As a form of footnote - this first sequence was posted by [Edgar Ilaga]("http://ubuntuforums.org/member.php?u=890253") and a similar post was also made by [zhez_100]("http://ubuntuforums.org/member.php?u=440817") )

Let's get started in sequence:

1. There are 2 Canon sites that I know of - one in Europe and one in  Asia.  I suggest you go to the one in Asia as the European site has a  tgz file that may confuse you.    

2. Download the "cnijfilter-common" file located here: [http://support-asia.canon-asia.com/contents/ASIA/EN/0100118902.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100118902.html)

3.  From my firefox browser I have the option to "save the file" to my  desktop.  Once you have saved the file to your Desktop, check your  Desktop you should see a compressed file called "cnijfilter-common  2.90-1_i386.deb"

4. open the terminal (if you are new, click on Applications-accessories-terminal)

5. change the directory to your desktop (type: cd ~/Desktop)   [note the terminal is case sensitive]

6.  now type: $ dpkg-deb -x cnijfilter-common 2.90-1_i386.deb **common**

7. check your desktop - you should see a folder (with files inside) called "common" if you have this right, you are getting it.

8. now type: dpkg-deb --control cnijfilter-common_3.90-1_i386.deb

9. check your desktop - you should see a folder (with files inside) called "DEBIAN" if you have this right, this is working.

10. now we need to alter the "control" file within DEBIAN.  Let's change  the directory up a level to the DEBIAN directory, type: $ cd DEBIAN      [note this is case sensitive so use upper case]

11. You should see the directory structure that looks something like: ...:~/Desktop/DEBIAN$   

12. Now type: $ gedit control
 
13. A new window will open up with a text file inside.  You can click in  that file and navigate the file as though it was a Word file (or Open  Office Word processor for the open office fundamentalists).  Scan  through all the hightech jargon and look for the word "libcupsys2" - now  change that word to read "libcups2"

14. Save the file and close it.

15. now go back to your desktop and simply drag the "DEBIAN" directory into the "common" directory.

16. Go back to your terminal and if you still have the directory shown  as: ...:~/Desktop/DEBIAN$ you need to back a level.  Type: "$ cd  ~/Desktop" and you should return to your desktop directory  (....~/Desktop$ )

17. Now to re-package the driver. type: $ dpkg -b common cnijfilter-common_2.90-1_i386.deb

18. If this ran smoothly then you have successfully modified the "cnijfilter-common" driver.

19.  If you have a 386 machine, you now simply double click on the file  and it will install.  If you have an AMD64 machine you need to force the  architecture.... (back to the terminal)

20. From a post by Pau sanchez I got the following code.  type: $ sudo  dpkg -i --force-architecture cnijfilter-common_2.90-1_i386.deb

21.  If it all worked well, you should get a run of messages that start  off with a statement "warning: overriding problem....package  architecture (i386) does not match system....   and the statement ends  with "Setting up cnijfilter-common (2.90)....    WELL DONE  the software  is being installed....

22. so far so good, you have adjusted, repacked and installed the first  driver. - as a bit of good house keeping - delete the directory on your  Desktop called "common" (you don't need anymore and it may cause  confusion with the next process).

Now let's go through the exact process AGAIN... but this time with a different driver - the "cnijfiler-ip2600series" driver

1. Go back to the Canon Asia internet site

2. Download the "cnijfilter-ip2600series_2.90-1_i386.deb" located at  [http://support-asia.canon-asia.com/contents/ASIA/EN/0100119102.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100119102.html)

Now the next steps are identical to the above listed from 3 to 22.  (except you use "cnijfilter-ip2600series_2.90-1_i386.deb" instead of  "cnijfilter-common 2.90-1_i386.deb")

off you go through the whole process.....

**D)   You will enforce a "chown root "**
once you have completed modifying and installing the two drivers you  still need to do this sudo chown thing.  So back to the terminal.  This  time you have to be at your base directory.  You can simply open up a  whole new terminal and it defaults to that base directory.  Now type the  following commands in sequence:
$ sudo chown -hR root /usr/lib/cups/filter
$ sudo chown -hR root /usr/lib/cups/backend
$ sudo chgrp -hR root /usr/lib/cups/filter
$ sudo chgrp -hR root /usr/lib/cups/backend

Everytime you hit enter (after each line) there should be no remarks or  statements in response, it should simply return back to the original  root directory.  Be careful of spacing (I got caught out a few times)

okay you have apparently assigned rights to those full directories -  apparently it is necessary for the process to work (I found this out the  hard way)

**E) you will select the correct PPD file on installation.**
Alright - this has been a big break through for me.  A very simple issue  that has NOT been raised in these forums, in fact many posts in this  forum state that when installing the printer, you simply keep clicking  on the "forward button" and it installs itself... NOT TRUE!!!

When you install the printer, start off by clicking forward, the option  then comes up for you to direct to the a PPD file.... SELECT THAT  OPTION.  Then you have to navigate to the IP2600 PPD file, located at   File System/usr/share/PPD/canonip2600.ppd

once you have selected this file, now proceed with the installation process.........

I hope this works for you........ Good Luck......

---

### Post by Jazzy_Jeff on 2011-04-27
I personally only use HP printers. Everyone of them have worked out of the box with no problems. It is a good idea in the future to buy hardware from manufacturers who fully support Linux.

---

### Post by Sef on 2011-04-29
Moved to T & T.

---

