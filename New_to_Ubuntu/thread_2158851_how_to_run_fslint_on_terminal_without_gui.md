---
title: "how to run fslint on terminal without gui"
date: 2013-06-30
forum: New to Ubuntu
---

### Post by 007casper on 2013-06-30
How can I run fslint on the server?  I can only use command line, no gui.

I saw this answer, but I am not sure how to go about it... 

by pixelbeat
> Hi I'm the Author of FSlint.
The GUI is a wrapper around a core command line utilities.
On a standard install you can add these utils to the path with:

export PATH="$PATH":/usr/share/fslint/fslint

Then you can use the utilities like:

findup /folder #list duplicates
findup -m /folder #merge duplicates using hardlinks
findup -d /folder #delete all but first duplicate
findup -dt /folder #report what would be deleted

fslint /folder #run all tools on a folder 
[http://ubuntuforums.org/showthread.php?t=272292&](http://ubuntuforums.org/showthread.php?t=272292&)

This might be obvious but I am not sure where to put "export PATH="$PATH":/usr/share/fslint/fslint" - under user bashrc ?

please advise. Thank you

---

### Post by steeldriver on 2013-06-30
you can export the PATH right there in the console to make the programs available for the current session, or add it to your ~/.bashrc to set it at every login

---

### Post by 007casper on 2013-06-30
thank you so much.

how can run 'findup -m /folder' without session time out?

I wanted command to run even if the terminal has been closed.

---

