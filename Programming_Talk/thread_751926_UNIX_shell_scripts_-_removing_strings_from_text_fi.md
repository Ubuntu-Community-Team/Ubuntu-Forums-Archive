---
title: "UNIX shell scripts - removing strings from text files"
date: 2008-04-11
forum: Programming Talk
---

### Post by Granddragon on 2008-04-11
Hello, having a bit of a hard time trying to figure out how to do this.

c) The script should allow the user to enter a search string and delete all records in the my_old_cars file that contain a string matching the search string. For example, if the user enters “1948”, the script deletes all records containing “1948”

How can i do this in a shell script? is there some sort of command that will search a file for a specific string and delete any instances? or am i trying to do this the wrong way.

Thanks for any help

---

### Post by ghostdog74 on 2008-04-11
this exercise appears in Guide to unix using Linux right? you should be able to find ways to do it from that chapter where this exercise is. to ask use to enter something, use read. to search for 1948, you can use sed, awk, grep or even pure bash.

---

