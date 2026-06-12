---
title: "Did PHP surpassed Perl in web developement?"
date: 2011-08-05
forum: Programming Talk
---

### Post by cgroza on 2011-08-05
Hello, I am experimenting with both PHP and Perl and Wikipedia says that Perl is called the "glue" of the web.
I do not get where this comes from since all I see on the web is pages and links ending in ".php".

Can anyone enlighten me?

---

### Post by worseisworser on 2011-08-05
Perl can be glue even if PHP is the more used glue today.

Remeber that popularity doesn't always mean anything or much. Popularity gives you Windows, and it gives you Britney Spears.

---

### Post by LoneWolfJack on 2011-08-06
traditionally, perl is used to glue together server-side applications because it is a very efficient text parser. if you're looking at web programming only, PHP has long surpassed perl as the primary programming language by order of magnitude.

---

### Post by trent.josephsen on 2011-08-06
They're not mutually exclusive.  And just because you see .php on the end of a URL doesn't mean the server doesn't rely on Perl.

I might have a server running Ubuntu with a PHP web app.  Then if I uninstalled PHP the web app would be broken.  But if I uninstalled Perl it's much more likely the server wouldn't work at all.

PHP might be ok for web development (I don't have experience with it myself, and plan to remain that way), and in terms of programs that actually generate the HTML you see on the Web, it may very well be much more popular.  But it's not the Swiss army chainsaw Perl is.  There's a lot more going on with a Web server than the script with the .php extension that serves your pages.

---

### Post by cgroza on 2011-08-06
So it is basically used on the backend while PHP provides the frontend?

---

### Post by enhu on 2011-08-06
generally all pages on the net are **html** even when it uses php extension. 

most of the PHP programmers actually claimed its more secure than the Perl scripting language. I believe its true

---

### Post by trent.josephsen on 2011-08-06
> **enhu said:**
> generally all pages on the net are **html** even when it uses php extension. 

most of the PHP programmers actually claimed its more secure than the Perl scripting language. I believe its true
Um.  What?

Your first sentence shows that you don't understand the difference between the content that's served to you and the language used to generate it.  HTML is the **output**, not the script itself.

As for PHP being more secure than Perl... what?  Are you trolling?

@OP: PHP is not (usually used as) a glue language.  PHP does one thing well: dynamically generated content.  PHP is a general purpose language, so you can do everything else with it, too, but that's a bit like saying you can do everything in math with a pencil and paper:  sometimes you can use better tools to get the job done quicker.

[quote=The Camel Book]Of course, if your job is programming, you can get your job done with any "complete" computer language, theoretically speaking.  But we know from experience that computer languages differ not so much in what they make *possible*, but in what they make *easy*.[/quote]

"Making the easy things easy and the hard things possible" is Perl in a nutshell.  But Perl is a language for everything.  If you stack it against PHP in Web development, you're likely to find Perl has some deficiencies.  That's because Perl wasn't built from the ground up with Web development in mind, and if it had been, it wouldn't be nearly as successful in every other field as it is.  Similarly if you stack it against Java in enterprise-scale application programming, you'll be disappointed.

But Perl is a glue language; it's for doing everything.  And when you want to do X, chances are you can do it quicker with Perl than taking the time to drop everything and learn a new language that's especially good at doing X-like things.  And there are some values of X for which Perl really is the best choice (especially when you have other considerations, like deadlines, cost, and software availability).

My advice?  Learn both so you can make your own decisions.  I bet you'll find Perl way more useful than PHP, even if you use PHP for web stuff more often.

[Disclaimer: I am a Perl programmer.  I know very little PHP and the experience I have had with it, directly and by proxy, has turned me away from it.  I also know Java, Python, C, and a mess of other things I don't particularly care to enumerate.]

---

### Post by lisati on 2011-08-06
> **trent.josephsen said:**
> <snip>
My advice?  Learn both so you can make your own decisions.  I bet you'll find Perl way more useful than PHP, even if you use PHP for web stuff more often.

[Disclaimer: I am a Perl programmer.  I know very little PHP and the experience I have had with it, directly and by proxy, has turned me away from it.  I also know Java, Python, C, and a mess of other things I don't particularly care to enumerate.]
Exactly. 

It can be helpful to at least be aware of some of the options. I have a clutter of various bits and pieces in my head, some more useful than others. Sometimes I surprise myself with how something seemingly irrelevant can lead to a solution.

---

### Post by shawnhcorey on 2011-08-07
Sorry but you can't decide what created the content simply by the extension that appears in the URL.  Most PHP have the extension .php but not all.  Most Perl CGIs have no extension or .html.

You have no evidence that PHP surpassed Perl.

---

### Post by cgroza on 2011-08-07
> **shawnhcorey said:**
> 

You have no evidence that PHP surpassed Perl.
I never said I do. That's why I created this thread.

---

### Post by mendhak on 2011-08-07
According to [langpop.com]("http://langpop.com/"), PHP is beating out C#, Perl and Python.  (Langpop's data is based on searches being performed against various search engines, may not be entirely accurate).  

Most of the development jobs I've seen do ask for PHP, but almost as much ask for Perl.  But that's only my own anecdotal evidence, I cannot speak for others. 

A filetype isn't a very good indicator of what's being  used as you can have both PHP and Perl websites that don't use their .php/.pl extensions, but have 'friendly' URLs such as /forum/thread1818964, or even end in .html.

---

### Post by shawnhcorey on 2011-08-07
> **cgroza said:**
> I never said I do. That's why I created this thread.

But you implied it.  Besides gather data on usage of the web is notoriously difficult.  For example, what is the Perl CGI script for the following URLs?

[http://some.domain/news/recent](http://some.domain/news/recent)

[http://some.domain/news/software](http://some.domain/news/software)

[http://some.domain/news/hardware](http://some.domain/news/hardware)

The most reliable data comes from asking the domain webmasters.  Everything else is a guess.

---

### Post by worseisworser on 2011-08-07
Github hosts a lot of software projects and has a sort of overview:
  [https://github.com/languages](https://github.com/languages)

---

### Post by cgroza on 2011-08-08
> **worseisworser said:**
> Github hosts a lot of software projects and has a sort of overview:
  [https://github.com/languages](https://github.com/languages)
It totally contradicts TIOBE. But they get their results differently.

---

### Post by JupiterV2 on 2011-08-08
TIOBE gets its results based on searches from search engines and other participating sites like Wikipedia. Searches may be an indication of a language's popularity but is not an indication of how wide-spread its usage is. Code Hosting sites like GitHub are indicative of the other side of popularity by showing the number of projects actually using a language. Even then, it's based on publicly hosted projects and not private ones.

---

### Post by dazman19 on 2011-08-12
I am a php developer. I know a little bit of C/C++/Java and python.

I got an old book on apache, written in 2000. Back then php was only 2-3 years old and most bash/dynamic web content was written in perl. I have manipulated a few perl scripts but dont know much of it at all. I have read that its regex library is more efficent.

PHP is very easy to learn, and very cowboy as such. You dont need to think much about pointers/types as you do with a language like C++ because it tends to convert them for you. Not good all of the time, but this does speed up development on the DOM considering you need to write JS/PHP/SQL(ofsomesort) And HTML. 

As of 5.3 it is becoming a much better language. The abilitys of a few new keywords has improved a lot of its Object Orientation. I am looking forward to php 6. 

To answer your question I think for new developments PHP seems to be well regarded. And time will tell how much more popular it becomes.

---

### Post by shawnhcorey on 2011-08-12
> **dazman19 said:**
> I got an old book on apache, written in 2000. Back then php was only 2-3 years old and most bash/dynamic web content was written in perl. I have manipulated a few perl scripts but dont know much of it at all. I have read that its regex library is more efficent.

Efficient and powerful.  So much so that Python has adopted it wholesale.  Since it's open-source, there's no reason any language shouldn't adopt it.

---

### Post by donsy on 2011-08-12
> **dazman19 said:**
> 
As of 5.3 it is becoming a much better language. The abilities of a few new keywords has improved a lot of its Object Orientation. I am looking forward to php 6. 

FWIW I found [this]("http://schlueters.de/blog/archives/128-Future-of-PHP-6.html") while doing a search on php6.

---

