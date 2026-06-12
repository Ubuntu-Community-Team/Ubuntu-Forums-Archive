---
title: "Beginner trying to find good tools for web development"
date: 2008-04-26
forum: Programming Talk
---

### Post by Miikee on 2008-04-26
I'm trying to build up a databased website, but I've never really programmed before but always wanted to learn.
I'm figuring that I need to learn some of the following languages, beside each language is my current progress in them:

HTML <---Finished up a project with
CSS <----Finished up a project with
Javascript <---- Finishing reading and beginning a project with
PHP <---- Beginning to read more about
MySql <----- Downloaded

I know that the first 2 are rather basic, but it's still a big step for me.  Anyhow I'm using Bluefish and Kompozer.  I also have a basic understanding of how to use gedit, but don't really use it.
I'm trying to decide what program I should use for coding javascript and the rest.
I know that bluefish can be an editor for everything else (PHP, MySQL, Apache).  And I also heard it can do javascript, but I don't see anything in the program suggesting any use of Javascript.  How do I use bluefish for Javascript?
Or if it's no good with javascript, what is good?
The fewer the programs the better.  Since I'm a beginner, I'd really like features that help me find the words/codes/functions I'm looking for while typing (so I don't have to repeatedly look it up on the internet).  And maybe something that helps me stay in the syntax required for the language and get the punctuation and things right.

So, what do I do to best use bluefish for JavaScript? (or where is a website with a tutorial or something... I've already searched for Javascript at bluefish's wiki and didn't find much).
Also what is a good program for javascript coding with the requirements I need?
And what is a good all around program for coding and combining all these languages?

I pretty much want my website to be very interactive, be searchable, be able to have members, etc.

Thank you for the help.

---

### Post by LaRoza on 2008-04-26
How much do you know? Very few of what you are asking for makes sense.

You seem to be over reaching. 

All that you seem to be asking seems to point to a text editor. I use Gedit with its plugins on Ubuntu, and I use Vim. On Windows, I use Crimson Editor. They are all text editors. I write my XHTML, CSS, ECMAScript, PHP, and all programs with them.

If you lack the technical ability to do what you are asking (and even if you did) you are probably better off with an existing solution.

---

### Post by Miikee on 2008-04-26
Ya, I thought I might sound a little bit off my rocker.  I'm not really looking for a solution of any kind yet.  I am trying to learn... teach myself things by doing projects.
All I'm really looking for is a beginner friendly text editor for Javascript.
Such as Bluefish or Kompozer is beginner friendly for HTML.  It has forms that you may fill out to write some of the code for you.

I know this won't be the same for a language like JavaScript, but there must be some kind of program out there that helps you some right?

Like in Bluefish, it has a "function reference" in a sidebar.  Along with menu bars for C, Apache, PHP+HTML, PHP, etc.  But it doesn't have a "function library" or menu bar for JavaScript.
I'm looking for a text editor or program similar to Bluefish that does have a menu bar or function library for JavaScript.

Thank you for the reply.

---

### Post by Dev'olution on 2008-04-26
I like Geany as a web IDE :)

---

### Post by Miikee on 2008-04-26
IDE that was the search term I needed.  Thank you.  I will read up on the Geany.  I also searched "JavaScript IDE" and found several more text editors that are in the same category of what I was thinking of.

---

### Post by Dev'olution on 2008-04-26
'sudo apt-get install geany' in your terminal should let u check it out :)

---

### Post by pmasiar on 2008-04-26
Instead of production-quality servers, like Apache and MySQL you are for learning much better off using simpler tools.

And start with learning better language than PHP. Yes it is close to HTML you know but HTML is about presentation - business logic does not belong there. Python is much better: see FAQ with poll and discussion why. See wiki in my sig for links.

SQLite is excellent simple SQL database, but you may consider even simpler DB, like bdm or shelve: like dictionary (key-value), only persistent. Value can be list or dictionary, not only scalar.

[http://learnpython.pbwiki.com/WebApplication](http://learnpython.pbwiki.com/WebApplication) will get you started: simple web server (in 7 lines of Python), and simple web app.

---

