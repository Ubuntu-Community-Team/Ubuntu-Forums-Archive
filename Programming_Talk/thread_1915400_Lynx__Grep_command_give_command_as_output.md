---
title: "Lynx / Grep command give command as output"
date: 2012-01-26
forum: Programming Talk
---

### Post by HighWire on 2012-01-26
Hey guys,

I need some help with the following :


When I run the following command in a Konsole or in Terminator :

> lynx -dump -nolist website.xx | grep -m5 -A3 -o "Information"The output gives me a brief overview of text stated on this website


But the problem is, that when I make a simple script, like this :

> #!/bin/bash

lynx -dump -nolist website.xx | grep -m5 -A3 -o "Information"which I chmod with : chmod a+x scriptname

and afterwards run with ./scriptname or bash scriptname, it only gives me "Information" as a comment...
I've been searching now for a few days on how to run it correctly from a script, but without succes... it appears that everytime on every variant I used it comes back with only "Information", which I don't understand cause of the fact the command runs fine straight from a Konsole...

Could someone help me with this?

---

### Post by tjoff on 2012-01-26
Welcome to the forums HighWire

The -o option for grep means that only the matched expression (in this case "Storingen Internet") is printed.
Remove the -o option and it should work.

Sorry to doubt your post, but it should not be possible at all to get the detailed output you refer to, when using the -o option. This has nothing to with whether you script the command or not.

---

### Post by HighWire on 2012-01-26
You are right :)

But I did receive output with the -o output as I stated, but without correct markups, without the -o it works fine and even better.

Thank you!

---

