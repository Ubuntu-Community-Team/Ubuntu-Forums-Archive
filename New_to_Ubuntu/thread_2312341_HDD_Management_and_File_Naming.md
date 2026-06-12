---
title: "HDD Management and File Naming"
date: 2016-02-03
forum: New to Ubuntu
---

### Post by incurablegeek on 2016-02-03
First of all, I have only about 6-8 hours in Kubuntu but am committed for life. This is one helluva an OS. (Windows and MS - RIP)

Briefly, and I don't think this will be a lengthy thread:

1) ***How does Kubuntu handle long file names?***

Background: I have several projects going with many iterations along the way. In Windows (please forgive the use of vulgarity), NTFS truncates file names after so many subdirectories, and I have many subdirectories.

2) [I][B]If I transfer thousands of files off my Windows computers, can I just dump them into a 3 TB HDD and then downsize it later?

[/B][/I]Why do I need to do that? Well, I have 5 computers and a file storage server, so I must consolidate and sort files before I can dump Windows and install Kubuntu.

Passing comment: With very few exceptions, the Ubuntu forums are the most well-mannered on the web. 
OCN is also nicely controlled. 
With that said, let's all please be mindful of the rules that we all agreed to when we first signed up.

---

### Post by blueridgedog on 2016-02-03
The figures I find are:
 #define NAME_MAX         255    /* # chars in a file name */
 #define PATH_MAX        4096    /* # chars in a path name including nul */

As to dumping, I see no reason you can't, as they are just files.  I have accumulated about 10T of junk over the years and have migrated from file system to file system, mostly with rsync or dd.

As to Windows, it is not bad to mention.  In fact, I find Windows10 to be useful and keep a system running in the kids area for them to use.

---

### Post by incurablegeek on 2016-02-03
Thank you so much, Blueridgedog, for taking time to assist me.

So when you say: > The figures I find are:
 #define NAME_MAX         255    /* # chars in a file name */
 #define PATH_MAX        4096    /* # chars in a path name including nul */

Is that something I must do _**before**_ transferring files from Windows to Kubuntu?
Or can I just transfer and "dump away"?

Also, I have a real problem with my keyboard (DAS mechanical) in that * actually shows up when typed as '  -- at least on the command line.
Can I paste on to the command line something typed in LibreWord, for example?

And, yes, I agree with you about Windows. When I told my associates in India I needed to keep one Win 7 computer to "communicate with the outside world", they were not happy. However, what I meant is that I have 25 years experience with Windows but only a few hours with Kubuntu (which I am liking by the way). So I need to hang on to Windows until I really understand Linux.

---

### Post by blueridgedog on 2016-02-03
That is from the kernel source, so it should be good as is.

Most keyboard issues connect back to mapping, but I have always found altering that a bit of voodoo I have not needed to master.

---

### Post by oldfred on 2016-02-03
I back up to DVD for most of my most critical files.
And some of the paths & files names are too long and they get truncated. But it is stuff I forgot I even had, but is included in selection so I do not care.

I have learned with Linux best not to use spaces. Use CamelCase, under_score or justonelongname. Otherwise you have to escape or use quotes to get it to include a space.

Also Linux seems to allow some characters that NTFS does not. If mounting a NTFS formatted partition in fstab include windows_names.

 Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20)

---

