---
title: "how to run cgi in apache2"
date: 2007-06-05
forum: Programming Talk
---

### Post by riski_lana on 2007-06-05
anyone can help me i have problem with how to run cgi in apache2

example i have 2 file, 
test.cgi and test.exe  

1st ==>  i want to use test.exe in my test.cgi,  how to call it ???
2nd==> in where directory i must put the file test.cgi & test.exe???
3rd ==> how to configure apache2 to permit cgi

tx

---

### Post by pmasiar on 2007-06-05
exe? Is it on windows?

For very simple web server to learn CGI, without configuration hassle (and performance of) Apache, you may use 7-line Python script web server: [http://LearnPython.pbwiki.com/WebApplication](http://LearnPython.pbwiki.com/WebApplication)

Just place script into directory and run it.

---

### Post by riski_lana on 2007-06-05
Sorry i mean exe is executable file from c compiling, so i want to access the executable fom cgi file

---

### Post by bukwirm on 2007-06-06
[Here's]("http://httpd.apache.org/docs/2.0/howto/cgi.html") a tutorial on using cgi with Apache2.

---

