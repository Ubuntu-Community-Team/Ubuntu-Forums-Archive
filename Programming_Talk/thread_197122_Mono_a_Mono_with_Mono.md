---
title: "Mono a Mono with Mono"
date: 2006-06-15
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2006-06-15
Hi All

I've been trying to install Mono so that I can learn C# but I've run into a few problems.

I dont use Windowz at all and run only Dapper on my PC at home, (No licence fees, no slow operation & no headaches anymore! LMAO), so I was wowed when I discovered you can still do .NET type stuff !

The only problem is I want to run .NET scripts in Apache2, but the install doesn't seem to have worked!.

I checked the httpd.conf and it points to the 'enabled-modules' folder where there is a .conf and .load file for mono. The only thing is that when I created a standard index.aspx, which only has a few HTML tags in it at th moment, it doesnt know how to handle the .aspx file in firefox and konqueror etc. All it says is 'what would you like firefox to open this application/x-asp-net file with?'

Any Help Is Gratefully Accepted!

Mike

---

### Post by mostwanted on 2006-06-15
Make sure your Apache serves the aspx files correctly and make sure you open your files correctly so that Apache serves them, not the file manager (type localhost in the address bar).

---

### Post by Mickeysofine1972 on 2006-06-15
Hi 

Problem sorted! I found this excellent how-to here: [http://www.codeproject.com/cpnet/introtomono2.asp?df=100&forumid=159057&exp=0&select=1103605](http://www.codeproject.com/cpnet/introtomono2.asp?df=100&forumid=159057&exp=0&select=1103605)

Thanks for your help though!

Mike

---

