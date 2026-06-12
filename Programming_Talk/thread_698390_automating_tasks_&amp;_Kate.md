---
title: "automating tasks &amp; Kate"
date: 2008-02-16
forum: Programming Talk
---

### Post by mr_fong on 2008-02-16
My winter project this year is to set up a home server with webcam, mysql database to manage the data from my weather station, with output to a website hosted by Apache. So far so good, it works.

Right now I am planning the website and am writing a lot of html/php/css test code. I use Kate, safe everything in the home directory of my laptop, then transfer it to /var/www on my laptop. After testing the code on my laptop I ftp it to the server. Quite cumbersome, so I wonder if there is a way to automate it. What I want:

1) when Kate saves files I work on it should save a backup file with sequence number or timestamp so I can trace back the development of the code to the beginning.
2) after saving files should be automatically copied over from the home directory to /var/www.

Can this be done with Kate (or another KDE editor; sorry no vi of emacs for me yet)? What is a smart way of setting up a coding editor? Transfer to /var/www can only be done by sudo or root: how to go around this and still play safe?

As you might have guessed, I am a beginning programmer, so bear with me. My goal is not the final server/website but rather the concepts in security and automation which can be achieved when running a Linux server. Any background theory is therefore highly appreciated. Greetings,

Hans

---

