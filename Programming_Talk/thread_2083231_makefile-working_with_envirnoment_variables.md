---
title: "makefile-working with envirnoment variables"
date: 2012-11-11
forum: Programming Talk
---

### Post by ccps on 2012-11-11
Hi,
 
I have written a makefile. This makefile is to be checked into svn. I used environment variables for my project directory path so that different computers can run the makefile without having to make changes to it.
 
for example:
PRJ_ROOT_DIR := $(REF_DIR)/projectName/trunk/Temp
where environment variable REF_DIR is C:/Users/myName/Desktop.
 
However, by just building the project, makefile automatically changed to:
PRJ_ROOT_DIR := C:/Users/myName/Desktop/projectName/trunk/Temp
 
This shows up in SVN that makefile has been modified.
 
How do i do it such that makefile remains as
PRJ_ROOT_DIR := $(REF_DIR)/projectName/trunk/Temp? Where changes is done in the background and not showed up on the built makefile so that SVN will not detect the change?
 
Thank you.

---

### Post by ofnuts on 2012-11-12
AFAIK this shouldn't happen. Given the path names you are using Windows. Do you use the makefile directly or through an IDE? What version of 'make' is this?

---

