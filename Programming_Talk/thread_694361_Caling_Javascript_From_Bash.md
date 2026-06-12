---
title: "Caling Javascript From Bash"
date: 2008-02-11
forum: Programming Talk
---

### Post by dedtr9 on 2008-02-11
I have some information that I need to login to a web page, but the password needs to be send through their JavaScript before it is submitted. Is there anyway to do this within bash without re-writing their script? Here is the link to the .js file:

[md5.js]("http://lewis.lcsd.k12.wa.us/admin/javascript/md5.js")

The login forum calls "function doStudentLogin(form)" near the bottom as you can see on this page:

[Login]("http://lewis.lcsd.k12.wa.us/public/home.html")

but calling "hex_hmac_md5(pskey, pw);" would work just as well, and you can submit the password directly to that. Its not straight md5, and I don't read enough JavaScript to tell exactly what it is doing.

---

### Post by Jussi Kukkonen on 2008-02-12
As long as the script doesn't use DOM much, you can just install a stand-alone js interpreter and use that (spidermonkey might be a good choice as that's what Mozilla uses in browsers).

---

### Post by dedtr9 on 2008-02-12
I got the interpreter working, but I cannot find a way to call a function, or pass variables from bash to the .js file. There is a tutorial on doing it with c or c++, and I'm learning C++, so would that be easier to make a small c++ program to get the variables then pass it to spidermonkey or is that just complicating things.

---

### Post by Jussi Kukkonen on 2008-02-13
spidermonkey interpreter does accept script arguments after the script name. I'm not familiar with how they're used in js, though.

---

### Post by naugiedoggie on 2008-02-13
> **dedtr9 said:**
> I have some information that I need to login to a web page, but the password needs to be send through their JavaScript before it is submitted. Is there anyway to do this within bash without re-writing their script? Here is the link to the .js file:

[md5.js]("http://lewis.lcsd.k12.wa.us/admin/javascript/md5.js")

The login forum calls "function doStudentLogin(form)" near the bottom as you can see on this page:

[Login]("http://lewis.lcsd.k12.wa.us/public/home.html")

but calling "hex_hmac_md5(pskey, pw);" would work just as well, and you can submit the password directly to that. Its not straight md5, and I don't read enough JavaScript to tell exactly what it is doing.

Hello,

I'm curious to know why this procedure is necessary.  What are you going to do with a "command line login"? 

If I wanted to remotely log in, I'd probably use, or at least try, CGI  -- maybe load the page in a frame and then you can pass the login information into the frame.  You can run CGI from the prompt, too.

Thanks.

mp

---

### Post by dedtr9 on 2008-02-13
I want to get to the page to parse the info i want out of it, but i need to log in first obviously. I can do this usually by using "wget foo.html?username=bah&passworld=blah" , but they apparently felt like making it harder, and it does not sent the password plain text, but they run it through that function first to get their special key.
 From there it is easy, but i am stuck on running it right now. I can use spidermonkey to run the .js file, and i can run the function by modifying it to run at the end, but i still cannot seem to pass any variable values to it. It takes anything i add and seems to ignore it, and I get the resulting line no matter what i try.:
md5.js:344: ReferenceError: pw is not defined

Edit: to clarify, the part i am stuck on is sending the variables to the JavaScript from inside bash, and then returning the answer.

---

