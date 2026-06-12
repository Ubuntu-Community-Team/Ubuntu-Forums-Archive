---
title: "program written in Text Edit (Mac) used in Ubuntu: wierd characters?"
date: 2011-10-08
forum: New to Ubuntu
---

### Post by Old Jimma on 2011-10-08
Hi Community:

I wrote a computer program on a Mac laptop for a language called "R". It worked great... it gave correct answers. The editor I used on the Mac was "Text Edit."

:D

I'm trying to get that program to run on Ubuntu now. I'm using gedit to look at the program, and cut and paste segments of the program into the R command window.

I've made no changes to the program... 

The program worked on the Mac but not on Ubuntu.

:(

There seems to be be invisible characters or some sort of difference between the way the Apple computer sees the file the code is in and how gedit sees the file.

Can someone please advise me on how to get the format of the file the program is in in a format that Ubuntu likes?

Thanks!
Phil Smith
Duluth, GA

---

### Post by stlsaint on 2011-10-08
try using the "vi" editor. In terminal just use vi to open up your document.

---

### Post by DougB1958 on 2011-10-08
In any "file breaks when moved to new OS" problem my first suspect is line-ending conventions. Mac OS nominally uses the same end-of-line marker Linux does (the newline character, \n), but once upon a time Macs used the carriage return character (\r),and some programs still call that the "Mac line ending."

This is something to look for, though not necessarily instructions on how to fix it (though stlsaint's suggestion of doing it through vi is good, I'm sure vi can change one kind of line ending into another even if I'm not enough of a vi user to know exactly how).

---

### Post by Old Jimma on 2011-10-08
Hi DougB and stlsaint:

I haven't used vi in 20 years! :)

I opened the file with vi. I didn't see any weird characters, although some of the line feeds were clearly in the wrong place.

Any other suggestions?

thanks,
Phil

---

### Post by DougB1958 on 2011-10-08
> **Phil Smith said:**
> 
I didn't see any weird characters, although some of the line feeds were clearly in the wrong place.


What did you see? Your program except with some misplaced line breaks? Or something else? I think I need a more detailed understanding of the problem to make more suggestions....

---

### Post by MG&amp;TL on 2011-10-08
Have you compressed it in any way?

I find that compressing python source in .zip format, bouncing it around the web a bit, then unzipping, removes the line indents (and thus it doesn't work!).

---

### Post by Old Jimma on 2011-10-08
Hi all:

Many thanks for all who responded to my query.

Because of the responses, I was able to formulate my problem better and find a solution by [COLOR="Green"]**googling**[/COLOR]:

**[COLOR="Red"]"Howto convert a mac text file format to ubuntu text file format"[/COLOR]**

I found an easy solution at: 

[COLOR="Green"]**[http://ubuntugenius.wordpress.com/2010/10/26/how-to-convert-windowsdos-text-files-to-linuxunix-format/]("http://ubuntugenius.wordpress.com/2010/10/26/how-to-convert-windowsdos-text-files-to-linuxunix-format/")**[/COLOR]

The solution is simple:



[COLOR="Red"][B][LIST=1]
[*]open the file with gedit
[*]file > save as, and then
[*]in the line ending text box, choose the operating system you want your text file format to be converted to.
[/LIST][/B][/COLOR]

For example, if you've got an apple text file and want to convert it to unix/linux, choose "unix/linux" in the line ending box.

Very easy!

My thanks to those who came to my rescue and contribute to Ubuntu!

Sincerely,
Phil Smith
Duluth, GA

---

