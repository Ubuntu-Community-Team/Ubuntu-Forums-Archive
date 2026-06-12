---
title: "Learning how to write programs for the Ubuntu."
date: 2019-03-25
forum: Programming Talk
---

### Post by giraffex on 2019-03-25
Welcome to all
I am currently programming in php. However, I would like to extend my skills and write programs available under linux. So I have two questions. Are there frameworks like for php e.g. codeigniter? When writing a program for Ubuntu, will it also be compatible with other Linux releases? Is there a lot of totorials based on examples?

---

### Post by TheFu on 2019-03-25
WARNING - heavy opinions follow. ;)

I have never written an Ubuntu-only program.  I don't intend to ever do that. Why limit the code in that way?  I haven't written any huge, serious desktop programs in over a decade.  I write "glue" programs every week for different needs. Most are under 100 lines. Few have any GUI, because that isn't my need.

php is almost exclusively used for webapps.  I can't remember **ever** seeing php used outside that realm. php isn't installed on Ubuntu by default either, so choosing a different language would mean not having to get the user to install the supporting tool, language, and libraries.

Perl, Python **are** preinstalled on pretty much every Linux distro.  Some have Ruby pre-installed too.  All of them also run on Windows, if that is a concern.

While you can write programs _just for Ubuntu_, this is highly limiting since Ubuntu is hardly the only Linux distro out there being used widely.
[https://developer.ubuntu.com/](https://developer.ubuntu.com/) is the ubuntu-specific techniques. These use Ubuntu-only libraries, so they won't work on other releases.

The type of program you write will determine the best language, best libraries to use, and which platforms can be supported.  If you use C++ and GTK, then you can support all the Linux desktops, OSX and Windows for a desktop application.   There are perl and python interfaces to GTK, so either of those languages can be used to target the same platforms, for desktop application.  If you don't need a GUI, then the available language choices drastically increase and more platforms can be supported.

Qt is a competing set of cross-platform libraries to GTK.  There are others, but none are as popular or have the deep support for almost everything like GTK and Qt do.

But I would choose to support as many platforms as easily possible by using a very popular scripting language, which lots and lots of libraries, that can be used for webapps, desktop apps, server apps, and as infrastructure glue.  Today, that language is python.  15 yrs ago, that language was perl.  If you need higher performance, then writing cross-platform C or C++ is the way to go.

This article just came out [https://www.techrepublic.com/article/the-3-least-secure-programming-languages/](https://www.techrepublic.com/article/the-3-least-secure-programming-languages/) about which languages attract the most bugs.  In the list of choices, C is, by far, the most powerful, but also needs the most expert programming skill not to have bugs and security failures.  Php is #2.  Basically, it is difficult for inexperienced php programmers to create secure, bug free, programs.

OWASP used to have a Top 10 List for Php which has been removed. They called it like it was, IMHO. It was not flattering to the language or the core php language devs. I know there are experts in php which have been able to write secured programs, but it took them over 5 yrs to get to that point.

If you want to find examples, there are thousands and thousands of them on the internet. F/LOSS projects put their code with all the revisions in repositories online.  Gitlab [https://github.com/topics](https://github.com/topics) and github are popular places.  So, if there is a specific piece of software you use and would like to learn more about, just find that project's code online, go through their bug list and start fixing the easier bugs.  Smaller projects are easier, but don't expect someone to hold your hand to learn a language.  Learn to use git.  Learn to use the specific libraries the project you are helping has chosen. Almost every different package used in Ubuntu has a project page on gitlab or github with the source code available. I'd guess over 99% of the software in the Ubuntu repos is like that.

When I was learning Ruby and Rails about 10 yrs ago, there was a book that our class followed closely. It explained how to perform all aspects of software development. Actually, it barely spend any time on the Ruby language itself.  It concentrated on all the other stuff developers need to know, like:
* distributed version control - git. Git is the undisputed winner.
* test driven development - basically, we create the tests BEFORE writing the code to pass those tests.
* how to use git - there are lots of youtube videos about this. The most difficult part is that the main repo, shared by a project, is just a social agreement, not enforced.
* how to use cucumber - a ruby on rails test tool/language; every language has their own.
* A few different browser javascript libraries - the ones that did almost all the client-side work with just a few lines of code
* Logins and secure session management
* DB lifecycles - moving schema changes forwards and backwards

Then that book concentrated in an example webapp with all the most commonly needed features for all webapps over the remaining 13 chapters.  That book is outdated today. I'm convinced that the only people making money in ruby were the guys selling new books every 2 yrs when they re-wrote the language or released a new Rails framework that broke all prior Rails code. To stay current, was next to impossible. Perhaps that has changed for Ruby stuff.  I went back to coding perl5, which has been stable for decades.  Perl5 has issues, like the lack of multithreaded support, but we have techniques to get around that by spawning outside processes. Perl6 has native thread support and many other built-in features, but it isn't anywhere near as fast as perl5. Perl6 is an entirely different language - sorta like how C and C++ are entirely different languages.  I loved the Ruby language. It is fully OO, intuitive, and able to quickly get things done, but it was slow and had great pains as it matured.  Ruby on Rails is a fantastic webapp development method for small-scale webapps with fewer than 20K users.  I think it has stabilized in the last 5 yrs.  Before I started with Ruby, I already had been programming 15 yrs and new over 30 other languages.

The same ideas would be needed for a desktop application.   For desktop applications, Ubuntu has been pushing a relatively new distribution method called "snaps."  There are some great ideas about snaps and some terrible implementation problems.  Fedora has been pushing a competing solution called Flatpaks.  Both of these distribution methods seek similar end-results, and today they both seem to have similar failures.   I've looked through a few example snap tutorials. They have them based on the language used to build the program.  [https://tutorials.ubuntu.com/tutorial/create-your-first-snap#0](https://tutorials.ubuntu.com/tutorial/create-your-first-snap#0)  One of the main issues I have with Snaps is they are trying to build a walled-garden. Devs have to register in order to distribute snaps.  That is a non-starter for me and my team.  Some code runs inside air-gapped networks. That means moving a file into the network and running an install is required.

I'm just one person with one opinion, often warped.  I haven't seen many professional developers for desktop applications hanging out here. They might drop by from time to time, but most of them will be on their gitlab website working on features and bugs for the projects they support. The main trick is to work on something where you have interest.  That can be sometime completely new or you can help an existing project.  As a new programmer, doing something from scratch will usually fail and be full of newby mistakes. By joining an existing team, you can see how others solved the thousands of little questions. That doesn't mean they will have the best solution for all of them, but it is more likely they will do some really good things that you will recognized when you move on to another project and see a less-good implementation/choice.

---

### Post by SeijiSensei on 2019-03-25
I sometimes write scripts in PHP because I'm accustomed to the language, and it has a lot of handy built-in functions.

You can run a script from the command line like this:
```

#!/usr/bin/php

<?php
PHP code goes here
?>

exit 0

```

The first line tells the shell to use the command-line PHP interpreter to run the script.

However I write shell scripts far more often than ones in PHP.  I mostly use PHP when I have to do things like parse files for which it's well-suited.  I think you should spend some time [learning a little Bash programming]("https://www.google.com/search?q=learning+bash").  It may be more helpful in the short run.

---

### Post by TheFu on 2019-03-25
[http://gtk.php.net/](http://gtk.php.net/)  Also found a Qt-Php binding, but it seems abandoned since 2016.

---

### Post by huff2 on 2019-04-07
Curious ... What do you typically or are interested in using code for?   For me, I always am trying to solve a problem or make an existing   process more efficient. Then, after working out the creative aspects   (pseudo-code-type-stuff :smile:  ) I choose a language that I feel will best  suit the needs. For what I  have done, I really have only ever needed  Python. But that really  changes based on what my program needs to do. I  like the advice to  learn Bash, very useful. 

A few free resources:
[Bash]("https://ryanstutorials.net/bash-scripting-tutorial/bash-script.php")
[URL="https://www.tutorialspoint.com/python3/index.htm"]Python3
[/URL]
By the sounds of it, you will want to familiarize yourself with  packages, libraries, and repositories. Have an understanding of what  dependencies are (this ties into your question about which languages can  easily handle an OS upgrade in Ubuntu). You'll also want to learn how  the Linux file system works, why its different from say, Windows.

As far as packages, maybe try experimenting with snap packages(they are  relatively new, to my understanding). Snapcraft has excellent resources,  as far as I have seen. Debian packages (.deb) are still the widely used  packaging system (is system the right word??) and is a must for  research. Here are some resources for you to check out:

[Snapcraft]("https://docs.snapcraft.io/snap-documentation/3781")
[Ubuntu Packages]("https://www.ubuntu.com/about/packages")
[URL="https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-005-software-construction-spring-2016/calendar/"]MIT open software engineering course (uses Java to teach concepts)
[/URL]
My experience and opinion on choosing a language:

My interest came about during my work as a general manager for an oil  company. They owned and operated gas stations in addition to other  concepts and other resources. My job was to make a suffering concept  achieve growth after 5 years of YoY decline ... It was a tiny Subway!!  Ha! I only had high school experience with Java and that's it. But, I  was first and foremost a problem solver/optimizer. I then began writing  programs that helped me analyze the unsorted, poorly filed data the  store produced. I also wrote programs that helped me monitor whatever  KPI I wanted. In the beginning these were all command-line programs  because I didn't think about other users or it being user-friendly to  someone other than myself. The store became profitable and I moved on,  but now I'm obsessed with the tech world in general. 

My point is that I realized that the world is about solving problems.  Consumers pay for solutions. Problem: I'm hungry but only have 20 min  Solution: My Subway, ha. This is a simplified example but think, what  software can you create to help solve the consumer and the store's  problem? The consumer needs to quickly see you as an option and the  store needs a way to better communicate that it has the solution to a  seeking consumer. This applies to EVERYTHING. 

It would be helpful for you to make a brainstormed list (I love  mind-mapping) of problems "WE" face everyday. The scope can be global or  local or personal. It doesn't matter. Example: People love to save  money on gas, some spend a lot of time on deciding WHERE to go. Can you  create an app for a cell phone that optimizes this decision? What  solutions are available today? How can you make it better? How can you  make it available to everyone? The answers to these questions will get  increasingly specific until you find the proper language and tools to  use to accomplish the task.

Use a language to learn and apply the concepts. Don't try to memorize,  learn what is happening. Then, look at how it is done in another  language. My final vote is Python. It is very readable and is growing.  Ubuntu, of course, is very Python-friendly. Python has a great list of  modules that help with everything from networking to  scientific/financial applications. AI and facial recognition sound cool?  Python can help you. 

Hope I gave you some good ideas to jump off of. Have fun and create something that helps someone else solve a problem! :smile:

OH! and I really suggest you get involved at the GitHub communities.  Tons of projects to explore and help with. Plus, you'll gain experience  with project flow and working with other developers - a must. You can  build a nice little portfolio at the same time.

---

