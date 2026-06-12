---
title: "Just some one to one advice needed"
date: 2011-07-05
forum: Programming Talk
---

### Post by overtone on 2011-07-05
Hello all,

This question is in relation to Software architecture and Ruby. I should have mentioned this in the question but now I cant change it.
If your not interested in the above, you should leave now.

I've posted to these forums before ever since I fell in love with kubuntu. After reading this thread:

[http://ubuntuforums.org/showthread.php?t=848612](http://ubuntuforums.org/showthread.php?t=848612)

I decided I'd take a chance and ask a development question and see what kind of answer I get. If its in the wrong forum then I'll remove it. Its more an architectural question so ill get to it anyway.

Its about rest web services, Api's and Ruby.


So I'm a 3rd year CS student and Ive had a fierce interest in Software for a long time. I guess I must be doing something right because I got ymself a paid internship over the summer (yay for me) and the people here are lovely.

Ive been asked to build a content catalog with a few interns to scrape a site and return the hierarchy. Seems simple enough. However yesterday the senior guy who's supposed to be managing us said "I want it to be rest based and the web app should call instantiate the crawler from a post request which means you'll have to build the API"

My head and everyone else's spun because this is something that just isnt mentioned in college. Any request for help has been met with, 'just start coding ruby and you'll eventually understand'. Even the explanations of what an API is were vague. As far as i knew, an API was just a list of classes and functions that were displayed in a javadoc. So I may need a deeper explanation to this.


I'll explain the architecture:

User
|
|***post request******************Take request
|
Webapp------------------------------------------->Crawler-------->WWW


So what I coded was a simple crud application (scaffold) in ruby and have just been modifying it since then. but this bit has been stumping me. Are the web app and crawler 2 different programs? 

I get what a rest request is and how its formatted in ruby but I havent the slightest clue about how to go about starting to build one or what to build. There are a lot of tutorials but they all simply explain what rest and ruby are and how they talk. 

Am i over thinking this? Has anyone any advice or real world demonstration. Even a nice video? I really appreciate any advice given as I want this internship to work out.


p.s were using anemone as the web spider framework.

---

