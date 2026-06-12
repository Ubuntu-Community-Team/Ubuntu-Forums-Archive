---
title: "ruby (not on rails) on web server"
date: 2006-02-09
forum: Programming Talk
---

### Post by oldmanstan on 2006-02-09
I'm learning Ruby slowly. It seems like a cool language. Basically I just like to write programs for fun, I'm not in IT or anything, it's more of a hobby I guess. Anyway, I had my web host put ruby on the server but when I upload the script to my cgi-bin dir it won't run. I have the #! /usr/bin/ruby thing at the top (can't remember what that's called in perl...) and it is chmod'd 777. The script I'm trying to run is just hello world

```
print "hello world"
```

Now I always thought that if you ran something on a web server (assuming the server could execute it) anything sent to stdout went to the browser, works in C++. Does "print" technically not go to stdout?

The error I'm getting is an internal server error which is really weird too. Anyway, any help would be great! Thanks!

---

### Post by sas on 2006-02-11
You're probably getting the error because the script permissions are 777. Most web providers should disallow those scripts for security reasons. Try chmodding it to 755.

---

### Post by oldmanstan on 2006-02-15
Hmmm... that doesn't seem to work. But good suggestion, I will keep it in mind in the future. Thank you!

---

### Post by stoffe on 2006-02-15
Internal server error is a "catch all" error that can mean anything. Do you have access to the logs?

Anyhow, my guess would be that you aren't printing the proper HTTP headers, namely content-type:
```
#!/usr/bin/ruby
print "Content-type: text/html\n\n"
print "Hello World!"
```
If that doesn't work, you might wanna try ```
#/usr/bin/env ruby
``` as it is a catch-all for rubies installed in odd places.

As next step, look up the CGI library for ruby. It takes care of printing headers and a lot of similar things for you and makes life simpler. Or make the leap and try rails. It's sweet.

Oh, and it's called a "shebang". ;)

---

### Post by oldmanstan on 2006-02-15
Awesome! The problem was the HTTP header info... I shoulda thought of that.  Any idea why the browser sometime needs headers explicitly and other times it doesn't seem to? (for instance I have PHP scripts that don't pass headers yet they work fine... PHP do it automatically?)

Anyway, thanks a bunch!

---

### Post by stoffe on 2006-02-16
[QUOTE=oldmanstan]Awesome! The problem was the HTTP header info... I shoulda thought of that.  Any idea why the browser sometime needs headers explicitly and other times it doesn't seem to? (for instance I have PHP scripts that don't pass headers yet they work fine... PHP do it automatically?)

Anyway, thanks a bunch![/QUOTE]
Yes, PHP (and ASP, JSP, Rails and all of those) take care of those things for you. CGI scripts are very close to the metal so you have to do everything yourself. Most languages have a CGI module or something similar you can use that helps with this though. Look here: [http://www.ruby-doc.org/stdlib/](http://www.ruby-doc.org/stdlib/) and here: [http://www.rubycentral.com/book/web.html](http://www.rubycentral.com/book/web.html) (beware that the book is outdated, the [new editition]("http://www.pragmaticprogrammer.com/titles/ruby/index.html") costs a few dollars but is well worth it IMO).

---

### Post by intangir1999 on 2006-02-17
Ruby sounds like a really good program to begin learning.  I myself have a couple of years in the VB.net world, VBA for Apps, and some C++ at the tow of the Linux command line.  Beyond that, I've managed to use MySQL in partner with PHP but have liked the ASP.net - of course I haven't tried creating a fullblown site using either...

Any whoo, for the avid or new to be game designer/programmer, what are the typical shredouts?  it seems that one would either need to go the Python path, but how could Ruby help in the process?

---

