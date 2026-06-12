---
title: "Help with homework"
date: 2013-02-18
forum: New to Ubuntu
---

### Post by zzercito on 2013-02-18
Hello everybody!! ):P
I'm VERY new to Linux.  Just started taking my first class and it's quite confusing after being pampered by the Windows GUI for so long.  I think I actually like it better so far though.  Part of the difficulty I'm encountering is that my teacher is not very good, the labs are poorly designed and he doesn't answer my questions via email in a timely manner. 
I've tried searching for answers to my questions in the site but have been so far unsuccessful. :(  
So I was wondering if anybody here would be so kind to help.  Any input would be appreciated. 

For starters here's what I need help with:

#1.  
Enter the entire command line to complete the following task:
 Assume you have a group account called “sales”.  Also assume you have  a directory called “products”.  Change group ownership, including all  subfiles and subdirectories of the   *products*  directory to the *  sales*  group.
 NOTE: Type your answer exactly as you would at a command line:  Do not add extra spaces, no quotations, no $ symbols, etc.
 HINT:  You will need root permissions
Answer:sudo chgrp -R sales products   (wrong)


#2.
[LEFT]Enter the entire command line to complete the following task:
 You have many, many unorganized files in your Documents directory.   From your homedirectory, find all directories or files that contains the  letter “i” anywhere in the filename in or below your Documents  directory.

 NOTE: Type your answer exactly as you would at a command line:  Do not add extra spaces, no quotations, no $ symbols, etc.
Answer:find Documents/*i*    (wrong)


#3.
Enter the entire command line to complete the following task:
 Assume you are in your homedirectory.  Copy all files that begin with ol to the desktop.
 NOTE: Type your answer exactly as you would at a command line:  Do not add extra spaces, no quotations, no $ symbols, etc.
Answer:cp ol* desktop   (wrong)


Thanks! 



[/LEFT]

---

### Post by kabukiM0n0 on 2013-02-18
#2 you would want to be using grep

---

### Post by oldos2er on 2013-02-18
Closed.

From the Code of Conduct:

While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.

---

