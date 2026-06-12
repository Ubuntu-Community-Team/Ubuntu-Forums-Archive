---
title: "n00b needs help on a script..."
date: 2007-12-11
forum: Programming Talk
---

### Post by evets on 2007-12-11
I have been asked to perform a task. One which seems could be automated using only my Ubuntu. The task is to update a spreadsheet each month.

Being a n00b, I have broken it down to the steps I think it needs to be accomplished in.

Primary Steps:
1. Download the zipped .csv file from a website to the tmp folder. 
2. Unpack it. 
3. Paste it into a spreadsheet. 
4. Name the spreadsheet with a descriptive and chronological name. (I have chosen filename-YYMMDD)
5. Delete the package and unzipped file from the tmp folder.

Secondary Steps:
1. Setup cron.
2. Write a repeating task to run the cron job once a month.


So far, I have wget (url), and it works! LOL

I would normally attempt to learn this on my own, but I am very eager to prove to my associates that using Ubuntu and FOSS is the way to go, and not to use windows and windows packages.  Therefore, I don't have the luxury of taking the time to learn it correctly.


Please help me, if you can.

Thanks so much!

---

### Post by aks44 on 2007-12-11
Why bother with converting the CSV to a specific spreadsheet format, when ALL spreadsheet applications can correctly read CSV files?

As far as I'm concerned I'd lobby to skip step 3 altogether (which is not only a bit complicated, but more importantly **totally useless**, not to say harmful to the portability of the file)...

For the rest...
2. use **gunzip**
4. use **mv** and **date**
5. use **rm**

:D


The cron part should be quite easy too once you have a working script.

---

### Post by evets on 2007-12-11
Thanks for the response. 

> **aks44 said:**
> Why bother with converting the CSV to a specific spreadsheet format, when ALL spreadsheet applications can correctly read CSV files?

Right, but, it needs to update a spreadsheet that is dynamically linked to a website. It's being done by hand now.

As far as I'm concerned I'd lobby to skip step 3 altogether (which is not only a bit complicated, but more importantly **totally useless**, not to say harmful to the portability of the file)...


For the rest...
2. use **gunzip**
4. use **mv** and **date**
5. use **rm**

Ok, I agree with these, so how do I put them together in a script or cron?

Thanks for the help.
:D


The cron part should be quite easy too once you have a working script.

---

