---
title: "New to CGI"
date: 2008-10-29
forum: Programming Talk
---

### Post by luke77 on 2008-10-29
Hi everyone,

I have been learning python for several months and have gone through several tutorials. I've decided to learn about CGI programming in Python because it seems that lots of people use it, and because I've kind of hit a wall in terms of learning new things. I know absolutely nothing about networking or web programming and didn't even know what CGI s until about a week ago. Anyways, there aren't any great intro tutorials that I've found but there are several articles on it, and I'm trying to start out by running examples in the tutorials. I'm sure that I'm doing something wrong but don't know how CGI should be run differently. Here's a sample script from a intro that I am trying to run:
```

#!/usr/bin/env python

import cgi
import cgitb; cgitb.enable()  # for troubleshooting

print "Content-type: text/html"
print

print """
<html>

<head><title>Sample CGI Script</title></head>

<body>

  <h3> Sample CGI Script </h3>
"""

form = cgi.FieldStorage()
message = form.getvalue("message", "(no message)")

print """

  <p>Previous message: %s</p>

  <p>form

  <form method="post" action="index.cgi">
    <p>message: <input type="text" name="message"/></p>
  </form>

</body>

</html>
""" % message
```

I'm not sure exactly what the output is supposed to be, but when I run this with my IDLE interpreter on Windows, the output is simply:
> 
Content-type: text/html


<html>

<head><title>Sample CGI Script</title></head>

<body>

  <h3> Sample CGI Script </h3>



  <p>Previous message: (no message)</p>

  <p>form

  <form method="post" action="index.cgi">
    <p>message: <input type="text" name="message"/></p>
  </form>

</body>

</html>

I'm pretty sure this is not what I'm supposed to be getting. Is there a special way to run CGI scripts, like in a web browser or something? Sorry for the basic question...any help appreciated.

Luke

---

### Post by LaRoza on 2008-10-29
> **luke77 said:**
> 
I have been learning python for several months and have gone through several tutorials. I've decided to learn about CGI programming in Python because it seems that lots of people use it

CGI is rarely used, in any language, for modern scripts.

> 
I'm not sure exactly what the output is supposed to be, but when I run this with my IDLE interpreter on Windows, the output is simply:

CGI is meant to be run on a server. I don't know why you viewed it in IDLE, when it is obviously meant to be viewed in a web browser.

> 
I'm pretty sure this is not what I'm supposed to be getting. Is there a special way to run CGI scripts, like in a web browser or something? Sorry for the basic question...any help appreciated.


Yes, it is meant for servers.

If you don't know XHTML (which seems like a strange statement, but you said you didn't know what the output was going to be...), learn it.

---

### Post by ZuLuuuuuu on 2008-10-29
The output is fine but you should run this on a server with CGI configured, so that this output is passed to the browser and browser "renders" this output. I don't remember the configuration exactly, but it is not very complicated:

 - You first install a server like Apache on Linux or IIS on Windows,
 - Then specify a folder as your "CGI folder" which you will put your CGI scripts in. Say, "cgi-bin".

Then whenever a call has been made to your server, like:

[http://localhost/cgi-bin/your_script.py](http://localhost/cgi-bin/your_script.py)

*your_script.py* will be run by the server, then the incoming output will be sent to the browser of the client (in this case it is you) by your server.

You can get better explanation of configuring the server (and generally about CGI) from:

[http://blob.perl.org/books/beginning-perl/3145_Chap12.pdf](http://blob.perl.org/books/beginning-perl/3145_Chap12.pdf) (Don't worry it is a legal online book. Actually a chapter of it.)

Although it is a Perl book, the configuration part is the same for CGI programming (You know you can do CGI programming in Perl, Ruby etc. as well as Python). Then how do the server know which language you used? The she-bang line specifies which interpreter should be run. In your case, it is:

```
#!/usr/bin/env python
```

which invokes the *Python* interpreter.

As LaRoza said, you should first learn a little bit about HTML itself to understand how a web page works and then go to creating *dynamic* web pages via CGI. Here is a good start for learning HTML:

[http://www.w3schools.com/html/html_intro.asp](http://www.w3schools.com/html/html_intro.asp)

---

### Post by luke77 on 2008-10-29
> **LaRoza said:**
> CGI is rarely used, in any language, for modern scripts.


CGI is meant to be run on a server. I don't know why you viewed it in IDLE, when it is obviously meant to be viewed in a web browser.



Yes, it is meant for servers.

If you don't know XHTML (which seems like a strange statement, but you said you didn't know what the output was going to be...), learn it.

Thanks. If you say CGI is rarely used, can you recommend a better course to take to learn basic web programming using Python? I've read tutorials that describe sockets, etc. but I'm not sure how to actually do anything relevant with that information (for a hobbyist programmer), aside from checking email and web sites.  Anyways, it sounds like I should learn XHTML first to understand CGI. Can you explain how to view a script such as the one one I posted in a browser? 

When I save it to disk as a text file and enter the location (C:\Python25\echoserver) in my browser, it simply displays the text. If I save it as a python file and enter the location in my browser, I get a popup asking if I want to save the file on my computer...

Again, sorry for the basic questions.

---

### Post by kilroywashere on 2008-10-29
That output looks good.  Just like a regular python script outputs text via stdout, so does your CGI. 

Note your first line of output:

> Content-Type: text/html 

  This is an important piece of a CGI because it establishes the MIME type that will be used to let the web browser know how to handle the data to follow (example if your CGI was a hit counter serving up images it might use a Content-Type: image/jpeg ).  

The rest of the output data in your example is HTML markup text that tells the web browser how to do fancy formatting of the the text.  I assume you know the HTML side of it already (if not that would be a good place to start).

W3 Schools is a great place to get started learning HTML if you need to.
[http://www.w3schools.com/html/DEFAULT.asp]("http://www.w3schools.com/html/DEFAULT.asp")

  Normally a CGI is ran by a web server (on the server) when a web browser makes a request to a given URL, only the output from the CGI is transmitted to the web browser (CGI's run on the server not on the web browser). 

 You will need to setup a web server capable of running CGI scripts if you do not have one already.  As it seems you are running Windows, you may want to use IIS as it might be installed already, otherwise you could alternatively install Apache.  

Hope this helps you get started.  Good Luck!

---

### Post by LaRoza on 2008-10-29
> **luke77 said:**
> Thanks. If you say CGI is rarely used, can you recommend a better course to take to learn basic web programming using Python? I've read tutorials that describe sockets, etc. but I'm not sure how to actually do anything relevant with that information (for a hobbyist programmer), aside from checking email and web sites.  Anyways, it sounds like I should learn XHTML first to understand CGI. Can you explain how to view a script such as the one one I posted in a browser? 


First, learn the basics of the web. XHTML + CSS at least. The way your would view that in a browser would be to run it on a properly configured server, or use the Python testing server (see pmasiar's sig) and type the address in a browser.

> 
When I save it to disk as a text file and enter the location (C:\Python25\echoserver) in my browser, it simply displays the text.
Yes, that is the default behavior for that MIME type.

> If I save it as a python file and enter the location in my browser, I get a popup asking if I want to save the file on my computer...
Yes, see above ;)

Your browser just does requests (and client side scripting). The server would have to execute it.

---

### Post by kilroywashere on 2008-10-29
> Thanks. If you say CGI is rarely used, can you recommend a better course to take to learn basic web programming using Python?

I wouldn't pay too much attention to that comment Luke.  Although there are many frameworks to make CGI easier, CGI hasn't really gone away.  PHP for example is widely used to make dynamic pages but in principle is the same thing as what your trying to do.  Generally someone with a background doing CGI has a better understanding of what's actually happening over someone who has only used a fancy framework (that being said, if you want to develop this as a marketable skill learning one of the modern frameworks is probably the way to go).

---

### Post by LaRoza on 2008-10-29
> **luke77 said:**
> 
I've decided to learn about CGI programming in Python because it seems that lots of people use it,

> **kilroywashere said:**
> I wouldn't pay too much attention to that comment Luke.  Although there are many frameworks to make CGI easier, CGI hasn't really gone away.  PHP for example is widely used to make dynamic pages but in principle is the same thing as what your trying to do.  Generally someone with a background doing CGI has a better understanding of what's actually happening over someone who has only used a fancy framework (that being said, if you want to develop this as a marketable skill learning one of the modern frameworks is probably the way to go).

I wouldn't pay any attention to this post either ;) My statement about CGI being used is true. CGI is old and there are better ways. CGI is a primitive and less efficient solution. Sure, it works, and was very popular, but now the technology has moved. CGI can be used for testing, and Python itself can be used to write a server for testing. [http://learnpython.pbwiki.com/WebApplication](http://learnpython.pbwiki.com/WebApplication)

Someone with a background of CGI doesn't have a better understanding. It is simple. Sure, using an apache module instead of CGI has the same basic function, but it is usually more efficient and better than CGI.

I am not sure why you broght up frameworks, I don't use them.

---

### Post by luke77 on 2008-10-29
Thanks guys. Looks like I have some reading to do.

---

### Post by CptPicard on 2008-10-29
To answer the actual frameworks question, the two main competitors in the Python space are TurboGears and Django.

---

### Post by pmasiar on 2008-10-29
> **LaRoza said:**
> First, learn the basics of the web. XHTML + CSS at least.

I disagree. Very basic HTML is enough, and your pages would work just fine without CSS: won't look pretty but who cares? :-)

CGI is just fine for basic web apps, why use complicated framework if you can use something simpler what is also easier to understand?

Example is you running your script in IDLE. CGI means that web server (like Apache) accepts HTTP request, finds relevant script to execute it, and sends response (formatted as HTML page) to the browser to display it. So obviously **not** the commandline as you did :-) 

CGI is easier to understand that any frameworks, but maybe frameworks may have better tutorials to get you started. Both Django and Turbogears framework come with simple web server, and will create running app for you.

But I still would recommend to start with plain CGI, just to understand what framework does for you. See above link at LearnPython wiki (also in my sig) for simple CGI web server you can use.

---

### Post by LaRoza on 2008-10-29
> **LaRoza said:**
> CGI is a primitive and less efficient solution. Sure, it works, and was very popular, but now the technology has moved. CGI can be used for testing, and Python itself can be used to write a server for testing. [http://learnpython.pbwiki.com/WebApplication](http://learnpython.pbwiki.com/WebApplication)


> **pmasiar said:**
> I disagree. Very basic HTML is enough, and your pages would work just fine without CSS: won't look pretty but who cares? :-)


It would depend on the goals. I believe that XHTML (not HTML...) and CSS are basic knowledge for those getting into any sort of web development. Knowing CSS 2 back to front isn't important, but being familiar with it is. They are the basic languages of the internet.


> 
CGI is just fine for basic web apps, why use complicated framework if you can use something simpler what is also easier to understand?

I never said it wasn't, and advocated its use for that ;) And even linked to your wiki on it.

> 
But I still would recommend to start with plain CGI, just to understand what framework does for you. See above link at LearnPython wiki (also in my sig) for simple CGI web server you can use.

So would I. My statement was a counter to a claim in the first post, not saying CGI shouldn't be used, just that it is primitive and not the best solution for live websites.

---

### Post by pmasiar on 2008-10-29
> **LaRoza said:**
> not saying CGI shouldn't be used, just that it is primitive and not the best solution for live websites.

CGI is just fine for web app which has just couple hits a day. That is exactly sweet spot where persistent web app server is overkill, IMHO.

---

### Post by LaRoza on 2008-10-29
> **pmasiar said:**
> CGI is just fine for web app which has just couple hits a day. That is exactly sweet spot where persistent web app server is overkill, IMHO.

A couple hits a day? I suppose. I would doubt how dynamic such a low traffic site has to be though.

---

### Post by pmasiar on 2008-10-29
> **LaRoza said:**
> A couple hits a day? I suppose. I would doubt how dynamic such a low traffic site has to be though.

Excuse me? If page is generated as a customized response to user's query, it is dynamic, even if is hit once a month - it cannot be static page.

"Dynamic" means "generated according to input parameters in request". It has nothing to do with the speed.

---

### Post by LaRoza on 2008-10-29
> **pmasiar said:**
> Excuse me? If page is generated as a customized response to user's query, it is dynamic, even if is hit once a month - it cannot be static page.

"Dynamic" means "generated according to input parameters in request". It has nothing to do with the speed.

I know. I was just musing about a site that only gets a couple hits, yet needs to have changing contents.

---

### Post by luke77 on 2008-10-30
Ok, me again. I downloaded the simple server script from LaRoza's site:

```
import CGIHTTPServer
import BaseHTTPServer
class Handler(CGIHTTPServer.CGIHTTPRequestHandler):
    cgi_directories = ["/cgi"]
PORT = 8000
httpd = BaseHTTPServer.HTTPServer(("", PORT), Handler)
print "serving at port", PORT
httpd.serve_forever()
```

and saved in C:\cgihome\server\cgihttpserver.py . 

Then I run from the command prompt, and get the response "serving at port 8000" . 

Then, as specified, I save a simple CGI file in C:\cgihome\cgi\echo-client.py : 

```
#!c:\Python25\python.exe

print "Content-Type: text/html"
print
print """\
<html>
<body>
<h2>Hello World!</h2>
</body>
</html>
"""
```

When I try to run this with the server running in the command line, I get 404 error: "File not found". This shows up both in the browser window and the command prompt window. When I try using a .html file saved in C:\cgihome, I get the same error.

Where am I going wrong?

Thanks again,
Luke

---

### Post by ghostdog74 on 2008-10-30
@OP, if you can have a second choice, you can go with PHP. If you cannot have a second choice and Python is a must, you can give Spyce a shot.

---

### Post by pmasiar on 2008-10-30
> **luke77 said:**
> the simple server script from LaRoza's site:

Hey! That's **my** wiki! :-)

Did you tried the simplest 3-line example: [http://ubuntuforums.org/showthread.php?t=332041](http://ubuntuforums.org/showthread.php?t=332041) ?

---

### Post by luke77 on 2008-10-30
> **pmasiar said:**
> Hey! That's **my** wiki! :-)

Did you tried the simplest 3-line example: [http://ubuntuforums.org/showthread.php?t=332041](http://ubuntuforums.org/showthread.php?t=332041) ?

Sorry! Yeah, I did, and I can't even get that to work...

---

### Post by luke77 on 2008-10-30
Bump?

---

### Post by stevescripts on 2008-10-30
file permissions?  (SWAG)

---

