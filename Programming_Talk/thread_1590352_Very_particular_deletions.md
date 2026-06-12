---
title: "Very particular deletions"
date: 2010-10-07
forum: Programming Talk
---

### Post by ludwigvan1988 on 2010-10-07
I have large data files (32,000 lines) that I need to cut down. My problem is (1) I need to remove every row that contains "B" in column 22 and (2) I don't know anything about programming. 
How do I accomplish this? 

(If you can only solve problem 1 that's fine) :)

---

### Post by lloyd_b on 2010-10-08
> **ludwigvan1988 said:**
> I have large data files (32,000 lines) that I need to cut down. My problem is (1) I need to remove every row that contains "B" in column 22 and (2) I don't know anything about programming. 
How do I accomplish this? 

(If you can only solve problem 1 that's fine) :)

1.  In a terminal window:```
egrep -v "^.{21}B" file.txt > newfile.txt
```where "file.txt" is the filename to be processed, and "newfile.txt" is the new file to be created without those lines.

2.  Take a class in programming :)

For an explanation of what that command does:  'egrep' is a version of the 'grep' program that handles "extended regexes".  Don't worry what these are for now - trust me - they're needed for this.

'grep' is a utility program that searches through files to locate lines that contain certain things, as specified by a "pattern".  In this case, we want everything *but* the lines that match, so we give it the "-v" option to invert the match (show only non-matching lines, rather than the default of showing only matching lines).

The pattern "^.{21}B" - the "^" means "start of line".  The "." says "match any character".  The "{21}" says "repeat the previous match 21 times" (you can get the same results with "^.....................B", but the form I provided is a little easier to handle).  The "B" is "match a literal character "B".  So in total, "match any line that has a B in the 22nd column).

'grep' normally sends it's output to stdout (aka, the screen).  The "> newfile.txt" tells it to take what would normally be displayed on the screen, and send it to a file called "newfile.txt" instead.

Lloyd B.

---

