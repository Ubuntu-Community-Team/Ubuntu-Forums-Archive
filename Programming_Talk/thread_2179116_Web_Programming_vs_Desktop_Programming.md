---
title: "Web Programming vs Desktop Programming"
date: 2013-10-06
forum: Programming Talk
---

### Post by cwblanch on 2013-10-06
First I want to apologize if I used Desktop Programming wrong. That's just how I've read it referred to.

I know there are probably a ton of posts in various places about this, but I just want peoples opinions about it.

I've been teaching myself programming, python specifically, but I've found a site that teaches web programming. And the site is teamtreehouse. I've read a bit about it and it seems good. But I want to know if I learn web programming will I further my general knowledge about programming? Because I've read that learning one language will make the next one easier to grasp. 
But I've also read that web programming, HTML and CSS for example, isn't actual programming and won't do anything for programming knowledge.
BUT JavaScript is a web language that is applicable. I don't know!

OR should I learn both at the same time?? I've also read people saying that you shouldn't learn more than one at the same time.

I'm sorry about the rambling questions, but this is what comes of reading tons of posts about these topics and not knowing where to go with it.

Thank you!

---

### Post by ofnuts on 2013-10-06
Writing HTML/CSS is a form of programming. You have to produce text and make sure the computer understands it correctly to execute what you want it to do. Like in more "standard" programming, there are several ways to achieve the results, but some a more efficient/maintainable that others.

Spreadsheets and word processors are also a form of programming (even if the computer under M$ control can sometimes behave like a raving psycho instead of a gentle and logically-minded machine).

---

### Post by SeijiSensei on 2013-10-07
Web programming often means building applications that rely on server-side processing, typically in conjunction with an SQL database.  This site is written in [PHP]("http://www.php.net/") and uses such a database, probably MySQL.  HTML is a "markup language," with embedded codes to create links, add italics, etc. CSS is a method to create a stylesheet that attaches particular attributes to HTML tags.  

You can view the HTML "source code" for rendered pages in most browsers.  In Firefox, you right-click on the page and choose "View Source."  Try that for this site.  You'll see a "meta" tag in the header for this site that links to [this CSS stylesheet](http://ubuntuforums.org/css.php?styleid=117&langid=3&d=1376300680&td=ltr&sheet=bbcode.css,editor.css,popupmenu.css,reset-fonts.css,vbulletin.css,vbulletin-chrome.css,vbulletin-formcontrols.css,).

Web programming is much more limited than programming in general, because you are constrained to use a browser as the application's interface.  However you can still write scripts in PHP that can be run the command line, just like any other programming language.  I write such scripts from time to time because I am very familiar with the language, and because PHP has a lot of built-in functions for complex tasks like managing connections to an IMAP mail server.

---

### Post by Lars Noodén on 2013-10-07
Also, web services are stateless.  Each time a link is selected, a new connection is made afresh.  On the server side, your application has to do all kinds of tricks to pretend otherwise.  

I'd give desktop programming a try first.  Since you are using Python you could look at Qt or PyQt.

[http://www.cs.usfca.edu/~afedosov/qttut/](http://www.cs.usfca.edu/~afedosov/qttut/)

---

### Post by SeijiSensei on 2013-10-07
> **Lars Noodén said:**
> Also, web services are stateless.  Each time a link is selected, a new connection is made afresh.  On the server side, your application has to do all kinds of tricks to pretend otherwise.

Well, really just one trick, using [sessions]("http://php.net/manual/en/features.sessions.php").  I can't remember the last time I developed a site that didn't use sessions to track users across pages.

---

### Post by Lars Noodén on 2013-10-07
Yes, there are of course libraries to handle sessions.  

I had hoped however that HTTP 2 would be stateful, but it seems that control of the WWW has become too politically charged for technical discussions to percolate up in the overal plans.

---

### Post by edouardtavinor on 2013-10-09
> **SeijiSensei said:**
> Well, really just one trick, using [sessions]("http://php.net/manual/en/features.sessions.php").  I can't remember the last time I developed a site that didn't use sessions to track users across pages.

I feel I should mention a few things here. 
1/ In europe using cookies to store a session id is illegal unless you ask for consent from the visitor. 
2/ Don't worry about backend programming. Keep your data in flat files on the server and fetch it once. Then store it in the indexeddb in your browser.
3/ Don't use JavaScript. It's an unintuitive language that will bite you at some stage. Instead, have a look at Dart, for example.

Happy coding!

---

### Post by SeijiSensei on 2013-10-09
Just because the EU requires that you state that you use session cookies doesn't make them any less valuable.  They are not the same as "tracking cookies" like the ones advertisers use.  Session cookies only persist until they reach their expiration (typically four hours on sites I design) or you close your browser.  They are designed to track a user while interacting with the site.  It is not illegal to use cookies on sites hosted within the EU if the user is informed about them up front as, for instance, on the [Economist]("http://www.economist.com/") home page.

As for storing data in a browser, I can't begin to think about how to do that nor would I want to.  My sessions often contain a dozen or more PHP arrays, some quite large, along with a variety of other variables that contain information I only want to retrieve once from the database per session.  Any site that uses logins like this one is going to be using session cookies as well.  I count five such cookies for this site.  I also use MD5 strings as session identifiers to make them impossible to guess.  (The FTD florist site once used cookies identified by a simple incrementing integer.  It made it possible to see other people's transactions simply by guessing a different number.)  It is entirely possible to use session cookies and not violate user's privacy in any meaningful way.

---

### Post by Vaphell on 2013-10-10
> **SeijiSensei said:**
> I also use MD5 strings as session identifiers to make them impossible to guess.  (The FTD florist site once used cookies identified by a simple incrementing integer.  It made it possible to see other people's transactions simply by guessing a different number.)

flowers? that's nothing, i recall reading about the bank that had the same issue :)
That said, i hope your raw session ids are really long so they don't sit together with their hash in some rainbow table yet, 'md5' and 'impossible' in 1 sentence... that does not compute ;-)

---

### Post by edouardtavinor on 2013-10-10
> **SeijiSensei said:**
> Just because the EU requires that you state that you use session cookies doesn't make them any less valuable.  They are not the same as "tracking cookies" like the ones advertisers use.  Session cookies only persist until they reach their expiration (typically four hours on sites I design) or you close your browser.  They are designed to track a user while interacting with the site.  It is not illegal to use cookies on sites hosted within the EU if the user is informed about them up front as, for instance, on the [Economist]("http://www.economist.com/") home page.

As for storing data in a browser, I can't begin to think about how to do that nor would I want to.  My sessions often contain a dozen or more PHP arrays, some quite large, along with a variety of other variables that contain information I only want to retrieve once from the database per session.  Any site that uses logins like this one is going to be using session cookies as well.  I count five such cookies for this site.  I also use MD5 strings as session identifiers to make them impossible to guess.  (The FTD florist site once used cookies identified by a simple incrementing integer.  It made it possible to see other people's transactions simply by guessing a different number.)  It is entirely possible to use session cookies and not violate user's privacy in any meaningful way.

The difference between the intention of a session cookie and a tracking cookie makes no difference to the law. The law demands that you get the consent of the person visiting the site.

To store information in the browser, html5 offers 2 possibilities: local storage and an indexed database in the browser. This allows you to write complex applications which run in the browser without needing a server to do anything but deliver the information the first time you load it. You don't need a session, you don't need a database on the server, you don't need php. You just deliver html, css and javascript files, and the javacript file loads the data you need using ajax from flat files also stored on the server. After that the application can run offline without an internet connection, like gmail, google docs etc. 

By the way, for those who insist on doing it the old way, the solution to setting cookies in the browser is to pass the sessionid as a parameter with every request.

---

### Post by ofnuts on 2013-10-10
> **edouardtavinor said:**
> To store information in the browser, html5 offers 2 possibilities: local storage and an indexed database in the browser. This allows you to write complex applications which run in the browser without needing a server to do anything but deliver the information the first time you load it. You don't need a session, you don't need a database on the server, you don't need php. You just deliver html, css and javascript files, and the javacript file loads the data you need using ajax from flat files also stored on the server. After that the application can run offline without an internet connection, like gmail, google docs etc. 

Hmmm. That works if you don't need to store anything and everyone is using the same data (like checking an interactive map)... But if you need to upload you data for storage, or if the data is specific to some user (mail...) then you need to check user privileges on the server, so you are back with server code (PHP or else), databases...

---

### Post by SeijiSensei on 2013-10-10
> **Vaphell said:**
> That said, i hope your raw session ids are really long so they don't sit together with their hash in some rainbow table yet, 'md5' and 'impossible' in 1 sentence... that does not compute ;-)

Yes, they are.  I use a combination of "ps aux" and some other transitory strings to generate the hash.  I could use SHA1 instead, but since we're talking about something that exists for just a few hours, I'm not really concerned about cracking MD5.  Plus I rarely build sites where financial transactions are involved.  I do work on sites governed by HIPAA rules, but in those cases all the "patient health information" is encrypted with AES256 before storage.  

> By the way, for those who insist on doing it the old way, the solution to setting cookies in the browser is to pass the sessionid as a parameter with every request. 

I wrote a PHP function way back that tests to see if the user accepts cookies.  If she doesn't, I pass the ID in the GET request.

---

### Post by edouardtavinor on 2013-10-10
> **ofnuts said:**
> Hmmm. That works if you don't need to store anything and everyone is using the same data (like checking an interactive map)... But if you need to upload you data for storage, or if the data is specific to some user (mail...) then you need to check user privileges on the server, so you are back with server code (PHP or else), databases...

Indeed, but writing an application and writing an application which requires state to be shared between different instances of this application running on different computers are two different things. As the original question was about "web vs desktop programming", I assumed that state should be saved locally and not sent around the net through a hundred gateways to some unknown server.

---

### Post by cwblanch on 2013-10-14
Thank you everybody for all the responses. I'm learning just reading through all the responses. I want to apologize for not responding to anyone for so long. I've gotten a new computer and was having a crazy time remembering my new login info.

> **Lars Noodén said:**
> Also, web services are stateless.  Each time a link is selected, a new connection is made afresh.  On the server side, your application has to do all kinds of tricks to pretend otherwise.  

I'd give desktop programming a try first.  Since you are using Python you could look at Qt or PyQt.

[http://www.cs.usfca.edu/~afedosov/qttut/](http://www.cs.usfca.edu/~afedosov/qttut/)

I like the look of PyQt. I have to read more about it to understand what is doing with python. I think I forgot to mention I'm still very new to python.

PyQt is basically a gui for your python code? So you can make the interface behave how you want it and I assume add code in the background to do what you want? Like you can have a simple gui print the questions for a quiz and take user input?

---

### Post by cwblanch on 2013-10-14
> **SeijiSensei said:**
> Web programming often means building applications that rely on server-side processing, typically in conjunction with an SQL database.  This site is written in [PHP]("http://www.php.net/") and uses such a database, probably MySQL.  HTML is a "markup language," with embedded codes to create links, add italics, etc. CSS is a method to create a stylesheet that attaches particular attributes to HTML tags.  

You can view the HTML "source code" for rendered pages in most browsers.  In Firefox, you right-click on the page and choose "View Source."  Try that for this site.  You'll see a "meta" tag in the header for this site that links to [this CSS stylesheet]("http://ubuntuforums.org/css.php?styleid=117&langid=3&d=1376300680&td=ltr&sheet=bbcode.css,editor.css,popupmenu.css,reset-fonts.css,vbulletin.css,vbulletin-chrome.css,vbulletin-formcontrols.css,").

Web programming is much more limited than programming in general, because you are constrained to use a browser as the application's interface.  However you can still write scripts in PHP that can be run the command line, just like any other programming language.  I write such scripts from time to time because I am very familiar with the language, and because PHP has a lot of built-in functions for complex tasks like managing connections to an IMAP mail server.

Thank you for your response. I did a few exercises online for HTML and CSS, I found it very interesting and rewarding to be able to write a few lines of code and be able to see your progress quickly. But I didn't know about PHP being a server-side language. I hadn't looked into it much, but I assumed it was a different version of HTML.
There's a lot more to all programming than I originally thought, and I like the challenge.

---

### Post by King Dude on 2013-10-15
When people ask me what language to learn, I ask them what kind of programming they want to do. What programming would you like to do? Is your heart set on web programming, or is web programming your idea of an easy way to learn general computer programming?

---

### Post by mahesh3 on 2013-10-19
I think there are phases to learn. If you want to pay bills and work for wages then learn whatever makes good money in the market. If you want to give back to the world with what you have got in terms of skills then the whichever language helps the most from your side is good.Web based apps are taking over, however those who want to own their data prefer desktop apps.

---

