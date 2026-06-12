---
title: "Moving a file and renaming it to add an incremented number via bash script"
date: 2007-03-01
forum: Programming Talk
---

### Post by Katryx on 2007-03-01
I'm making a bash script that moves a certain file into a different directory for archival, where the file should then be renamed to add an incremented number, i.e. "filename.ext" -> "filename001.ext," "filename002.ext," because this will be done multiple times with the same source filename and I don't want anything overwritten.  Essentially, each time a file is moved into the archive directory it should be given a unique name relative to the files that already exist in the directory.  I suppose this could also be accomplished by creating a uniquely-named subdirectory for each file, if necessary.

One problem: I don't know how to do this. x) I've searched both on Google and on this forum and didn't find what I needed.  I'm not even sure if bash scripting is appropriate to accomplish this with.

---

### Post by s1ightcrazed on 2007-03-01
Yes, this can be done with bash, but it is going to be a bit tricky. You'll want your script to read the contents of the archive directory and, using tail, read the last file in the dir, and determine the numerical extension on it. You could do this using cut possibly (or you might be able to use sed, but I'm not a big sed fan), where you cut everything after the . so that if your file is filename.005 you grab just the 005. You can then save this to a variable, increment it by 1, and then use that variable to name the next file. 

I can be more specific if you like, but part of programming is learning by doing. Enjoy!

---

### Post by po0f on 2007-03-01
Katryx,

I'm not providing a solution, but an alternative.  When archiving files, I find that a datestamp is a lot easier to scan than just incremented numbers.  Something like `cp file /backup/dir/file-$(date +%F)`.

date's %F modifier tells it to output date in YYYY--MM-DD format.

---

### Post by Mr. C. on 2007-03-01
Katryx,

You can do this in any scripting language; it is trivial in perl.  If you want to use bash, learn about how to a) extract the numeric part of the file, and b) increment numbers.  There are lots of ways to do either of these, including using external commands or the bash built-ins.

This problem reminded me of a homework problem I gave to my shell scripting students some years back.  If you want a fun rename program to start with, see the Week 10 Answers at: 

[http://cis68b1.mikecappella.com/calendar.php](http://cis68b1.mikecappella.com/calendar.php)

Enjoy,
MrC

---

### Post by hellocatfood on 2010-05-08
I want to achieve the same thing and have had just as much luck with Google.

Mr. C, do you still have the documents online somewhere?

---

### Post by Mr. C. on 2010-05-09
I've uploaded the lectures and homework to google docs.  They can be reached here:  

[https://sites.google.com/a/cappella.us/courses/](https://sites.google.com/a/cappella.us/courses/)

The particular file you want is: 10-hwans-vars-params.pdf (the 10 is week 10, so the rest of the file names should be self-explanatory).  I'll add an index later.

---

### Post by hellocatfood on 2010-05-11
It's asking me to sign into your site and I'm not sure how to. I've tried signing in using my Google account but it's not letting me. I think I need a different login. (Or could you upload the doc somewhere else?)

---

### Post by Mr. C. on 2010-05-11
Hmmm, the site and documents are all set to allow anyone to access, no login required.  Can anyone else confirm?

---

### Post by hellocatfood on 2010-05-12
Try logging out of your Google/cappella.us account and then click on the link. It's redirecting to a cappella.us login screen whenever I click on the cis68b1 link

---

### Post by dearingj on 2010-05-12
> **Mr. C. said:**
> Hmmm, the site and documents are all set to allow anyone to access, no login required.  Can anyone else confirm?

I can confirm: it asks me to "please select an account that you would like to use" and gives me two choices: my gmail account (with which I am already signed in on another tab) and "Choose another account". Selecting my gmail account does nothing - it just keeps asking me to choose an account. Selecting "Choose another account" brings me to a login screen where it asks me to "sign into your account at Capella.us" and lets me input a username and password.

---

### Post by Mr. C. on 2010-05-12
I've moved the documents to google sites, instead of google docs, so you should be able to access without login now.  Sorry for the inconvenience.

---

