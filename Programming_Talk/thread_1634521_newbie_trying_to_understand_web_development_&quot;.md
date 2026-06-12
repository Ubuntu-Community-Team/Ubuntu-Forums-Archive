---
title: "newbie: trying to understand web development &quot;flow/process&quot;"
date: 2010-11-30
forum: Programming Talk
---

### Post by UbuNoob001 on 2010-11-30
Hey again all...
     Currently I am trying to more fully understand the macro-perspective of what is a typical path to web development. I am completely new to web-design and programming. Here is what I am working with so far:

**Background**
1. A friend and I have an idea for a website that is very data-heavy. The short synopsis would be that the site will need to take public domain data from a variety of other websites, order the data, then manipulate it algorithmically. This new output would be published in both graphical and text form on our site. 

2. Based on the great recommendations of posers in another thread ([http://ubuntuforums.org/showthread.php?t=1629279](http://ubuntuforums.org/showthread.php?t=1629279)), I have decided to go with Python as the language in which we will manipulate the data.

 G[I]iven that we are completely new to xhtml, Python, javascript, flash and other terms such as "CMS", web development framework, the wealth of information available is rather daunting. 
[/I]
**Question**: Could someone please suggest a general resource/book helping with this? I would like to know what a typical development flow looks like. For example (and this may be a complete misunderstanding). It seems like I need to know how to do the following: 
1. gather data from site X,Y and Z
2. manipulate the data using Language 
3. Order that data into a dataset 
4. Find a way (once the xhtml basics/javascript of the site is written) to integrate data into the xhtml, constantly updating

**so the types of questions I have associated with each step above are**
Q1. does one write a script in python to do (1) or is this used simply by a utility like wget?
Q2. this data manipulation can be done with python?
Q3. Ordering that data, does it occur via the programing language Python, or via some other way? Is MySQL simply a formating scheme or is it actually a  WAY to order the data?
Q5. How does one inject this updating data into the site (into xhtml,Java, Flash etc)

[B][I]Ultimately can someone suggest a way to start learning not just how to do these things but to even understand how the questions above(Q1, Q2...) need to be changed so as to understand how to do 1,2,3,4. Either collection of resources, a book etc. 
[/I]
[/B]


Thanks so much for the suggestions. I realize that no one can "hand-hold" me through this process, however if someone can suggest some resources that might prove helpful so that I can understand enough to ask meaningful  questions, id greatly appreciate it. This will be a long process given my naiveté regarding programming and development but Im rather excited. Thanks!

---

### Post by Some Penguin on 2010-11-30
You haven't actually said what sort of data you'd be fetching and what 'manipulation' you'd be doing.

---

### Post by UbuNoob001 on 2010-11-30
> **Some Penguin said:**
> You haven't actually said what sort of data you'd be fetching and what 'manipulation' you'd be doing.


For example, say a city or police-department posts 
1. "real-time" updates to its website of the time, and location of traffic accidents. 

2. accident data from the past in each given location

and suppose a weather service (NOAA) posts 

3. weather conditions for given locations (at a specific time)

and suppose 

4. given the time of day/day of the week is a factor in mood which impacts driving behavior of drivers. 

5. how many on-ramps per mile there are (more risk of accidents) etc. 


and suppose I wanted to combine  all this information algorithmically, weighting it, so that it would yield some output X(1,2,3,4,5) =DR = "driver risk" by location along a highway, so as to indicate not just existent accidents, but risk.  Then the setup would color-code a google map accordingly which would self update at regularly scheduled, small intervals. 

then allow the user to mouse-over an area on the road map and a box would pop up indicating data, links to data, etc etc etc

this sort of thing.

---

### Post by Suparious on 2010-11-30
Basic guideline to hobbyist-development


The first thing I do, when I am thinking about starting a new project, is check [sourceforge.net ]("http://sourceforge.net")for anything that would be remotely similar. Sometimes you can learn from examples, or tailor something pre-written. It is easy to spend a few hours going through completely irrelevant sourceforge projects, but might be worth it.

Once I am confident that nothing else (not even a module of small code segment) can be recycled from the net, then I begin thinking about the 'engine' or 'core' (back-end) of my project.

Once you figure out how you intend to collect your data and store it, the the next logical step would be to think about writing a method to view this data (front-end).

At this point, you would theoretically have a system that collects and displays data. As with typical hobbyist-development behaviour, you may now begin to obsess over your code, tweaking it and adding functions.

This is where you can consider having two separate environments, 'production' and 'development'. Whereby the production environment has an "always working" copy of your code, and the development environment you can break and fix at your leisure.


Informational sources:

I have never been able to effectively retain infromation from books, this is where google has become a great devopment partner (and crutch). If your doing your back-end (or core / engine) portion using python, start small; google something like "python download http data" and look for a code snippet that shows you how to download with python.

As a personal rule (please note, I am not really a developper, just a hobbyist), I don't limit my creativity to just using a single language. Neither should you. If you think that the "manipulation" portion of your data is best with python, then don't struggle to find a way to "collect" your data with python. There are many common linux tools that you can use to collect data (like wget, as you mentionned).


Specific to your project:

> Is MySQL simply a formating scheme or is it actually a WAY to order the data?
MySQL is one of many storage methods for your data. You would order the output on the fly while retrieving the data from MySQL. This would be within the SQL query written in your code.

> How does one inject this updating data into the site (into xhtml,Java, Flash etc)
Well, using a web-based language that supports a MySQL client (there are too many to list, but I enjoy PHP, your python could work here too though.) you could write an add/edit/delete framework to manipulate the data stored within MySQL.

As well, your "back-end" system should be doing the same, but does not need to be web-based and could use any command-line linux tool.


More personal comments:

Are you sure your ready for this kind of project?

---

### Post by UbuNoob001 on 2010-11-30
> **Suparious said:**
> 

More personal comments:

Are you sure your ready for this kind of project?

Suparious, 
   
Thank you SO much for your outline/suggestions. Thats exactly what I was looking for. Your suggestions  will be invaluable. 

As for being ready: *clearly* I am **not** ready. If i were,  I wouldn't have asked such a basic logistics/process question. However, I am a reasonably quick study,enthusiastic,  enjoy learning, have had a thrill working with linux the last year.  So at this point, I am simply gathering information, learning, and with an "end-task" in mind, more motivated to learn the basics of the skills necessary. If these skills get applied in another direction down the line, great. If not, fine I will have learned a lot. 

i will have 3 weeks off from work, and be on vacation,  in December, so Id love to use that time to at least structure an outline of what I need to learn/understand and start gathering resources. 

Thanks again for your help and support. I will leave the thread open as to get some other viewpoints, then mark as solved accordingly.

---

### Post by Some Penguin on 2010-11-30
*shrug*  Front-end development, server architecture, and algorithms are very different skill sets.

One reasonable set of principles to follow is

- Abstract data storage from the algorithmic code as much as possible.
- Abstract the algorithm foo and data storage from the client.
- The server should never trust a non-authenticated client.

 
On (1), most of a system should not depend on deep knowledge of how data is stored.  If, for instance, you find that you need to add columns in a table or rework indices or break apart a table into two tables plus a view, you shouldn't end up needing to change things throughout your entire system.  Ideally, much of a system wouldn't care whether you're even using an SQL backend, but in practice this is fairly difficult unless you are willing to either completely sacrifice ACID, or you create numerous methods that embed application logic in your storage layer.

On (2), for instance- - you can use Apache Tomcat serving JSPs, and JavaScript, and set it up so that your front end only makes HTTP requests to the appropriate servlets.  The front end shouldn't break just because you changed internals, and you shouldn't be exposing your database directly to the client.

(3) should be obvious.

---

