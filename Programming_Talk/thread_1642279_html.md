---
title: "html"
date: 2010-12-10
forum: Programming Talk
---

### Post by Drenriza on 2010-12-10
Hope its ok i can ask html stuff here.

I was wondering if anyone knew if it is possible to ping a ip address from a html script. And then import it into a table with red text for no and green for yes.

I want to do this since i have a list with hundreds of ip addresses. And i would like to have a way to see if they are up or down without connecting to them.

Thanks on advance.
Kind Regards

---

### Post by Zugzwang on 2010-12-10
> **Drenriza said:**
> I was wondering if anyone knew if it is possible to ping a ip address from a html script. And then import it into a table with red text for no and green for yes.


You will need some additional scripting language for this (plain HTML is only for document description), and in particular one that works server-side, as pinging surely isn't supported by JavaScript. If you restrict yourself to the Internet Explorer, you can probably also use ActiveX or the like client-side.

---

### Post by Drenriza on 2010-12-10
we use 50% firefox 50% safari (mac browser)

---

### Post by Zugzwang on 2010-12-10
> **Drenriza said:**
> we use 50% firefox 50% safari (mac browser)

Ok, so get something running on the server side. Pure HTML won't do the trick.

---

### Post by Drenriza on 2010-12-10
Im also kinda asking for a little help if anyone could tell me what to look for / after. Or make in what language.

---

### Post by Zugzwang on 2010-12-10
> **Drenriza said:**
> Im also kinda asking for a little help if anyone could tell me what to look for / after. Or make in what language.

Ok, so the first thing that "we" need to know in order to help you is to understand why you actually want to do that - in fact, it is non-obvious why it has to be some kind of "HTML script" - what's for example wrong with a terminal script? This is important to know as you might have good reasons for requesting it in HTML form. You just haven't stated them here. As such reasons are normally tremendously important to keep in mind right from the start, you will need to state them here to get good answers.

Then, provided that you really want to do it in a web-based way, state what you already have: a web server installed somewhere, which scripting languages it supports right at the moment, etc.

Please answer *both* questions.

---

### Post by thatguruguy on 2010-12-10
> **Zugzwang said:**
> Ok, so the first thing that "we" need to know in order to help you is to understand why you actually want to do that

This.  I can think of lots of bad reasons why you want to start pinging random ips, and very few good ones.

---

### Post by Drenriza on 2010-12-10
> Ok, so the first thing that "we" need to know in order to help you is to  understand why you actually want to do that - in fact, it is  non-obvious why it has to be some kind of "HTML script" - what's for  example wrong with a terminal script? This is important to know as you  might have good reasons for requesting it in HTML form. You just haven't  stated them here. As such reasons are normally tremendously important  to keep in mind right from the start, you will need to state them here  to get good answers.

Then, provided that you really want to do it in a web-based way, state  what you already have: a web server installed somewhere, which scripting  languages it supports right at the moment, etc.I currently just have a plain html page, containing tabels, a zebra script, and a tooltip script
[http://www.dhtmlgoodies.com/index.html?whichScript=tooltip_shadow](http://www.dhtmlgoodies.com/index.html?whichScript=tooltip_shadow).

The side contains hundreds of ip addresses (for local use). That i want to check if they are online or not (pingable) so i dont need to connect to them to test, or find out.

It is not a problem making a apache server with php if necessary.

The reasons i ask for it to be html script (little knowledge of what is possible) is because i need my server to ping the destination and not the destinations to ping my server.
If i can keep this in my html page (so i have everything at one place) that would be top dollar. ,)

The result than need to be imported into my html page in a specific table for each site.

Hope it makes sense.

---

### Post by Zugzwang on 2010-12-10
Ah, ok, so you have the following setting:

You have a server computer "A", which also runs a web server program, which needs to be able to contact some set of other computers "B" . You want to monitor its connectivity to the other computers and just want to monitor that the server can contact the other computers. For actually viewing the ping results you use a different computer "C". As you really what to track the connectivity between "A" and the computers "B" and not between "C" and "A", you want the pinging to be executed on "A".

Technically, what you want to achieve shown be doable using the "exec()" command of PHP, which could call the "ping" command from the underlying operating system. By reading the output of the ping tool and parsing it, you would be able to make a nice table out of multiple ping runs. It's just that the "exec" command is often deactivated in the PHP settings. 

Then, there's an old thread on something similar: [http://ubuntuforums.org/showthread.php?t=1572433](http://ubuntuforums.org/showthread.php?t=1572433) - There's a ready-made bash script for what you want. You could run it on the server permanently if you want. Or you could have a PHP script that just triggers executing it and then returns the result. 

There are of course also billion gazillion other scripting languages you can use for your task, it doesn't really matter as long as they are capable of executing the ping command of the underlying OS.

---

