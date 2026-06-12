---
title: "Printing PHP PostScript"
date: 2008-08-07
forum: Programming Talk
---

### Post by rabatitat on 2008-08-07
I'm developing an application that needs to print formatted documents (i.e. reports, invoices, etc.)

I'm using PostScript with PHP5 and MySQL5 on Ubuntu 8.04.

I'm used to using the PHP printer functions (which works on Windows machines). How do I use PHP to print the output to a Linux user?

Methods I'm contemplating:

1. Output the report to a PDF/PostScript file and have the user print that.

(I don't like having to do this since I'd rather have it print right away without the user having to manipulate other programs outside of the browser).

2. Make an external program and have it print the file then destroy the file.

3. Direct I/O?
(I'm trying this now...)

Other possibilities?

---

### Post by drubin on 2008-08-07
Are these scripts running by a web interface ie apache or CLI?

**EDIT:** Giving the option to the user to pdf it is a much nicer option as then they can choose to print or even email it.

This is the options most banking sites give that I have seen, can't be a bad option. :)

---

### Post by MacAnthony on 2008-08-07
you can use php's exec() function to execute a print command.

exec("lpr -P <printer> -r <path_of_file_to_print>");

That command will print the file and then delete them. Of course this only works if the server the file is run on has access to the printer they would want to print to.

---

### Post by drubin on 2008-08-07
> **MacAnthony said:**
> you can use php's exec() function to execute a print command.

exec("lpr -P <printer> -r <path_of_file_to_print>");

That command will print the file and then delete them. Of course this only works if the server the file is run on has access to the printer they would want to print to.

DEFF change to output to pdf, The whole point of websites is to have access from any where/ with very limitied software installed. This means that you can "only print" on the same server the files are severed from... You also have very little choice as to the options a user can select. 

I personally like to chose to print most things in black and white, on the draft setting,  to save ink.

---

### Post by rabatitat on 2008-08-11
> **rubinboy said:**
> DEFF change to output to pdf, The whole point of websites is to have access from any where/ with very limitied software installed. This means that you can "only print" on the same server the files are severed from... You also have very little choice as to the options a user can select. 

I personally like to chose to print most things in black and white, on the draft setting,  to save ink.

Yup, my assumption is that the users don't have access to accroread and exec is disabled on my server...

I'll just make a printer friendly format with CSS and provide a pdf download...

now if they'd only make printers with XML parsers... hmmm...

---

