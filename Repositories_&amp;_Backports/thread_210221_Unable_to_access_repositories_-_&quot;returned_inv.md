---
title: "Unable to access repositories - &quot;returned invalid header&quot;"
date: 2006-07-06
forum: Repositories &amp; Backports
---

### Post by Optiker on 2006-07-06
I previously started a thread in "Installation" under a title "Kubuntu 6.06 - GIMP won't install in Dapper" because the proiblem first showed up when I tried installing GIMP in my newly installed Kubuntu Dapper. However, after a series of posts and replies, and some odd, erratic behavior, activity died out without a solution, so I decided to try starting a new thread here since the problem is more general than just GIMP, and what I've learned in the process suggests it is  more closely tied to repositories, or to my path to get to them (internal or external to my intranet).

I've gone through a number of different sources.list sets, starting with the default, and trying at least a couple from pointers by replies to other posts on several different forums and newsgroups. Oddly, I installed from the same installation CD at home on my home computer, and have seen no problems like this at all, suggesting that it's either an inhouse problem here at work, or that something about my computer here is affecting the installation.

Symptoms: I can't seem to install anything from the repositories. I can't get an update. Adept currently shows 975 packages available, and if I do a "Fetch Updates" it does so, but gets no new ones - same 975 reported. If I do a sudo  aptitude update from the command line, I get a string of errors like the following that has come to be characteristic of the problem...
---------------------------
Err [http://mirrors.uwa.edu.au](http://mirrors.uwa.edu.au) dapper/main Packages
  The HTTP server sent an invalid reply header
---------------------------
followed downstream by...
---------------------------
Failed to fetch [http://mirrors.uwa.edu.au/ubuntu/dists/dapper/Release.gpg](http://mirrors.uwa.edu.au/ubuntu/dists/dapper/Release.gpg)  The HTTP server sent an invalid reply header
---------------------------

At one point, my inhouse IT guy changed to a set of repositories that he normally uses, and it worked. I think at that point, I installed GIMP, and put off other stuff until the following Monday. When I tried to install another app then, the old behavior and error messages started again.

I've been through another cycle like that....for no reason, after changing to a different set of mirrors, it seems to work, but then reverts to the old behavior. At one point, when it seemed to be working, I tried to install WINE. The installation seemed to have worked and the status message said that it was successful. However, I couldn't find any of the WINE components, and it was clear it hadn't acutally installed. When I went back to Adept, WINE was not listed as an available package, and it was back to 975 packages.

The latest thing I tried was to go to the EasyUbuntu site and from the command line, download, install and run EasyUbuntu using the syntax pased from teh EasyUbuntu download page. All seemed to go well until I made my selections (including the repositopries selection) and clicked "OK". It opened the log window and ran, but the log indicated the same old problem...same error message, "The HTTP server sent an invalid reply header".

Any help that might point me to a solution would be most appreciated.

Thanks!
Optiker

---

### Post by Optiker on 2006-07-18
The problem is solved!   :D 

I was able to get help on the mailing list of the local Linux users group, who also work at the same lab as I do. As far as I can tell, it seems that our internal network is somehow messing up the headers. The solution is to replace http with ftp. Works fine! Everything working as expected!

Optiker

---

