---
title: "perl cgi works, bash cgi gives blank window... ?"
date: 2007-09-01
forum: Programming Talk
---

### Post by OldGaf on 2007-09-01
Hi all,

I am dipping my feet into the wide world of programing. I have my own local server with apache2 installed and running. I am trying a few simple scripts from the net to make sure all is working and I have this problem.

If I run this pearl script:

> #!/usr/bin/perl -w

print "Content-type: text/html\n\n";
print "ha!";
exit;

I get ha! in my browser.

If I run this:

> #!/bin/bash
echo “Content-type: text/html”
echo “”
echo “<html><head><title>Bash as CGI”
echo “</title></head><body>”

echo “<h1>General system information for host $(hostname -s)</h1>”
echo “”

echo “<h1>Memory Info</h1>”
echo “<pre> $(free -m) </pre>”

echo “<h1>Disk Info:</h1>”
echo “<pre> $(df -h) </pre>”

echo “<h1>Logged in user</h1>”
echo “<pre> $(w) </pre>”

echo “<center>Information generated on $(date)</center>”
echo “</body></html>”

I get a blank page..... no errors, but a nice white page.

I have tried other examples of bash cgi scripts and all give the same result.
Is there something else I need to configure for bash to return output to the browser?

---

### Post by banewman on 2007-09-01
Try with !#/bin/sh. That is what bash progs seem to use. :)
Sorry - left then realised your trying to use html with bash syntax - does that work?

---

### Post by OldGaf on 2007-09-01
Lots of sites have examples..... they just don't seem to work for me :)

[Look Here]("http://www.wellho.net/resources/ex.php4?item=a167/lookup.sh")

I tried #!/bin/sh, but get the same results. I need to use #!/bin/bash for my "normal" scripts on feisty so I expect it would be the same here.

---

### Post by PaulFr on 2007-09-01
I copied and pasted your script, and the only changes needed to make it run were:

1. Changed your quotes from [SIZE="5"]&#8220; and &#8221; to ".[/SIZE]
2. Added an **exit 0** at the end (but it works without adding this line).

Did you run your script from the command-line directly and see if there are any errors ?

---

### Post by OldGaf on 2007-09-01
Most excellent!!!!

I figured it would be something simple, but I didn't notice the odd quotes in nano.

I still don't know why I got "nothing" before tho. I would have thought I would have got an error!

Anyway, thanks so much for your help..... now onward and upward what?

---

### Post by OldGaf on 2007-09-01
Solved!

---

### Post by PaulFr on 2007-09-02
Glad to be of help - good luck with your programming. If in the future, you do use Perl for your CGI scripts, a popular library to use is CGI.pm bundled with your Perl (details at **[http://search.cpan.org/dist/CGI.pm/CGI.pm](http://search.cpan.org/dist/CGI.pm/CGI.pm)**).

---

### Post by tr333 on 2007-09-02
> **PaulFr said:**
> Glad to be of help - good luck with your programming. If in the future, you do use Perl for your CGI scripts, a popular library to use is CGI.pm bundled with your Perl (details at **[http://search.cpan.org/dist/CGI.pm/CGI.pm](http://search.cpan.org/dist/CGI.pm/CGI.pm)**).

You should also use taint mode when doing CGI in perl to prevent against security leaks in your code.
"perl -T".

---

