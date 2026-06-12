---
title: "HOW TO: Upload Moodle Quiz Scores Directly to Gradespeed 4.0"
date: 2009-09-07
forum: Outdated Tutorials &amp; Tips
---

### Post by Prospero2006 on 2009-09-07
Hello all, I'm a public school teacher in San Antonio, Texas and I thought I'd throw this set of scripts out for anyone who uses Moodle and Gradespeed and would like to have quizzes imported to the gradebook easily. 

This tutorial requires a basic level proficiency with bash, a default Linux command line interface. 

To Convert Moodle Quiz Scores to a Format Gradespeed can import:
[B]
Step One:[/B]
In order for this to work, the student first and last names must be the same on both Gradespeed and Moodle. Our district Moodle server and Gradespeed are both LDAP authenticated, which makes them 90 percent accurate. Most kids are fine.  It's easy to get in and make changes where needed.  Verify this first. 

**Step Two:** Download and unzip the [[COLOR="Blue"]moodlegrader01.tar (Click!)[/COLOR]]("http://linuxclassroom.com/temp/moodlegrader01.tar") Extract the tarball and you should have a folder there called moodlegrader/ 

-CD into moodlegrader, we'll save a couple working files here.
[B]
Step Three: [/B]
   -Log into Gradespeed and tell it to generate a class roster for 
    all classes including name and id number. 
   -Once the roster is generated, in the web browser choose 
view-> page source.
   -Save this raw source to your new moodlegrader/ directory.
    Let's call this file myroster.aspx. <--could be anything. 

**Step Four: **
  -Generate a master class list for the program to compare moodle data against. 
   -Execute:
```

       ./generateidlistscript myroster.aspx 

```
    -This should produce a file called idlist.txt that contains
             studentid firstname lastname

    -NOTE: Step Four only has to be run once at the beginning of the year.
     Once you have that list in place it will function for all quizzes.


**Step 5:**
 -Download a Moodle Quiz Score Report. 
**_ Important_** Use .ODS Format and open it using OpenOffice.
 Export a grade report that contains highest grades only. 

-Save this report to the moodlegrader directory as a .csv file.
(Let's call this myfirstquiz.csv)
**Step 6: **
Execute:
```

./parseopenofficecsv myfirstquiz.csv
./parseopenofficecsv2

```
This will produce a file named uploadme.txt
[B]
Step 7:[/B]
**Back to Gradespeed**
-Click on the assignments tab, find the assignment you want, and choose
grade. (You'll see grade / edit) <--Choose Grade
-On the left you'll see the 'import' button.
-Choose import, leave it as generic, and send the uploadme.txt file.
[B]
Step 8: [/B]
Clean up idlist.txt
After you upload your first class, assuming everything went well, you'll notice 3-7 kids maybe that didn't upload. You need to go into the idlist.txt file and adjust their names so that they match the entries in moodle.  --Capitals Count!
For example:

```

uploadme.txt

000111 Mary DeLaGarza


```

However, Moodle shows 
Mary Delagarza 
or
Mary De-la-garza

or something like that, the solution is to go into idlist.txt and
make it look just like the Moodle entry. Once you make the change, the student grade will drop into the gradebook.

These directions are fairly complicated, but maybe a teacher out there will find them useful. Better yet, maybe a real developer will pick up on the idea and create a one click interface within Moodle!

Email with comments!

Download link for Moodle Grader: [[COLOR="Blue"]Click Here![/COLOR]]("http://linuxclassroom.com/temp/moodlegrader01.tar")

---

