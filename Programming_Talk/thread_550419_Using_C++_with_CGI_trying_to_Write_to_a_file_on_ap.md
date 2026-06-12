---
title: "Using C++ with CGI trying to Write to a file on apache"
date: 2007-09-13
forum: Programming Talk
---

### Post by jjaeger4 on 2007-09-13
Ok, I looked around here a little but couldn't find anything in particular to get my problem. What I want to do, basically, is get my C++ program to work to take the information a person enters on a form on my web page to go into a file (working as a database or something to that affect. Here is about what I've got for the program.

```
#include <iostream>
#include <fstream>
using namespace std;

int main()
{
        char a[256];
        cout << "Content-type: text/html\n\n";
        cout << "<h1>Hello in C++</h1>\n";
        cout << "<pre>\n";

        cin >> a;
        cout << a;
        ofstream file("./myFile");
        file << a;
        file.close();

        cout << "</pre>\n";
}

```

That is the code for the C++ part of the cgi.

This is the code for the form on the web page.

```
<center><form action = "a.cgi" method = post>
<label>Enter your name:</label>
<input size = "20, 20" name = "name" maxstring = "20">
<button type = "submit" name = "choice" value = "1">Yes</button>
<button type = "submit" name = "choice" value = "2">No</button> 
<button type = "submit" name = "choice" value = "3">Maybe</button>
</form></center>

```

It won't write anything to the "myFile" I'm not sure what I need to do... I've not worked with CGI too much but I've got intermediate experience in C++. I can work it in Python too if that makes any difference? Kthnx!

- Jesse

---

### Post by pmasiar on 2007-09-13
Python would be much easier IMHO.

[http://learnpython.pbwiki.com/WebApplication](http://learnpython.pbwiki.com/WebApplication) has 2 simple examples. What database do you use? Is this part of bigger application? Do you want to do it yourself all, or use some web app framework to make your app easier?

---

### Post by jjaeger4 on 2007-09-13
Basically all I want to do with it is know how to set up a basic form on an HTML page and when the person hits the "submit" button it writes that information to the "myFile" file on my server.  It is really simple, I'm sure, I just think I am missing something here. I could do it if it were just in a C++ terminal but I want it to write a file on the server, ya know? :D

---

### Post by pmasiar on 2007-09-14
print a HTML to output by handmade code is simple thing. Parse the response is not - you better use CGI library for that. Your program needs to accept response and write it to the file, right?

---

### Post by jjaeger4 on 2007-09-14
Yes, I suppose. I'm not new to programming in C++ so much but I am new to the whole incorporating it into web development and what not.

---

### Post by pmasiar on 2007-09-14
If you are decent C++ programmer you will pick up Python in a day. Python is much more productive for web development (more flexible when handling strings). C is better for deep libraries which has to run fast.

Python prides itself with making good use of dynamic "duck" typing, making library API simpler than related C API where possible.

Check WebApplication link above for example how to receive response from submitted HTML form. Writing to file is trivial:

[php]
outfile = open('path/to/file', 'w')
outfile.write(string_variable)
outfile.close()
[/php]

---

