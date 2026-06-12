---
title: "web page scripting to database... without Apache/MySQL"
date: 2010-01-01
forum: Programming Talk
---

### Post by memilanuk on 2010-01-01
I've been getting my feet wet with PHP/MySQL, primarily via XAMPP/Portable Apps on my usb stick.  I've got two projects in mind, which is why I'm working at learning this stuff.  One is a membership database for a local non-profit club I'm involved in.  That one pretty much needs to be online for all the usual reasons.  The other idea/project is a match scoring application.  There... network connections will be next to non-existant, and expecting the end user (volunteer) to be able to install and configure even XAMPP may be a stretch.  Basically what I'd like to have is the ability to store and retrieve information in a database without having to run a server process, and be able to provide a simple browser-based interface to this 'application' without having to run (or configure) a web server.  From what I've read SQLite should handle the first part - but the second part I'm not so sure about.  Ideally I'd be able to give the end user a zipped folder that they could unpack wherever they wanted, and run just about everything from within that folder whether it was on their desktop or on a usb drive.

I'm sure much of what I'm looking for is probably a ways ahead of my current level of knowledge so I'm not so much looking for exact details as much as a sense of what is technically possible, vs. what is feasible, and what languages/technologies I should be focusing on towards the end goal.  Windows is going to be the primary end-user platform (simple fact of life), generally on older second or third-hand laptops though I'd like to keep things as cross-platform as possible (Mac OS X, possibly Linux) which is kind of why I was wanting to stick with the browser-based idea.  I have also dabbled in Python a bit (strictly CLI though) and as such am somewhat inclined in that direction if it would be a decent solution.

Anywho... any ideas, suggestions, etc. would be much appreciated.

TIA,

Monte

---

### Post by Hellkeepa on 2010-01-01
HELLo!

If you want to run a web-based application in browser, then you need a web server. You can't get around this fact.
However, you don't need to use a full-fledged Apache install for this. You can use a embedded small HTTP server, like Lighttpd or similar. You'd still need to have an installer, to set up some preliminary stuff on the user's computer. Things such as selecting an unused port for the web server, auto-starting the web server at boot, and such stuff.

The second option you have, is to build a self-contained GUI-application. I'd recommend a language which has good support for Qt then, seeing as it's a fairly easy to use and cross-platform library.

The third option is to host the application yourself, on a dedicated server. Make it a true web-application, in other words.

Happy codin'!

---

### Post by memilanuk on 2010-01-01
Okay... so lets modify this a bit and say 'browser based'.  Because as I said, network connection is going to be iffy to non-existant and the end user is a volunteer data-entry monkey (perhaps a bit harsh, but true).  I was hoping to be able to use a familiar and consistent interface across multiple platforms.  Originally when I started tinkering with Python that was the direction I was going (self-contained app written in Python with Tk for the interface, SQLite for the db), but I got side tracked on other things involving PHP & MySQL in the interim.

---

