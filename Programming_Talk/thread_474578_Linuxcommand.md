---
title: "Linuxcommand"
date: 2007-06-15
forum: Programming Talk
---

### Post by Xoanan on 2007-06-15
Hi All

I have been reading and trying out the tutorials on Linuxcommand.org, and I have run into a problem.
> 
As you may know, a well formed HTML file contains the following content:

<HTML>
<HEAD>
    <TITLE>
    The title of your page
    </TITLE>
</HEAD>

<BODY>
    Your page content goes here.
</BODY>
</HTML>

Now, with what we already know, we could a write a script to produce the above content:

#!/bin/bash

# make_page - A script to produce an HTML file

echo "<HTML>"
echo "<HEAD>"
echo "  <TITLE>"
echo "  The title of your page"
echo "  </TITLE>"
echo "</HEAD>"
echo ""
echo "<BODY>"
echo "  Your page content goes here."
echo "</BODY>"
echo "</HTML>"
       

This script can be used as follows:

[me@linuxbox me]$ make_page > page.html

It has been said that the greatest programmers are also the laziest. They write programs to save themselves work. Likewise, when clever programmers write programs, they try to save themselves typing.

This bit>  make_page > page.html



doesn't seem to function.  I type it in CLI and I get "command not found", yet it does seem to create an HTML file.  I can't see the HTML file when I try to open it with the browser, but the file is there and is labeled as an HTML file.  

I know there is something I am missing in this example.  Can someone point me in the right direction?

Thanx in advance.:popcorn:

---

### Post by mvaniersel on 2007-06-15
I don't see the problem right away, but here are a few things to check:

Try to run the command as
 
./make_html > page.html

so with a ./ in front of it, this tells bash to look for the script in the current directory

Also, did you make make_html executable with chmod +x make_html ?

What do you see if you open page.html in gedit?

Check the modification time on page.html (with ls -l), does it change every time you run the script?

---

### Post by Xoanan on 2007-06-15
> **mvaniersel said:**
> I don't see the problem right away, but here are a few things to check:

Try to run the command as
 
./make_html > page.html

so with a ./ in front of it, this tells bash to look for the script in the current directory

Also, did you make make_html executable with chmod +x make_html ?

What do you see if you open page.html in gedit?

Check the modification time on page.html (with ls -l), does it change every time you run the script?

Oops!  I did not use chmod to make it and executable.  I will do that when I get back home.  Thanx!
:oops:

---

### Post by Tomosaur on 2007-06-15
The > operator will always create the file, even if the preceding command files. Your problem is, as you've discovered, that you didn't make the script executable.

As it stands, you can be even lazier and scrap all those 'echo' commands in favour of one big string with escaped line-breaks.

---

### Post by Xoanan on 2007-06-15
> **Tomosaur said:**
> The > operator will always create the file, even if the preceding command files. Your problem is, as you've discovered, that you didn't make the script executable.

As it stands, you can be even lazier and scrap all those 'echo' commands in favour of one big string with escaped line-breaks.

Yes, I had actually gotten further into the reading; I had just forgotten how to convert it to HTML, so I had to back and review it.  Oops!

---

