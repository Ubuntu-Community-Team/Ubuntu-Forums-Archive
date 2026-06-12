---
title: "Python 3.1 equivilent to tokens? Columns?"
date: 2010-03-02
forum: Programming Talk
---

### Post by Stev0 on 2010-03-02
Greetings forums,

Continuing to work on my log parsing project...I've sorta kinda gotten the regular expressions to work the way I want them to, but for the next portion of functionality I'm worried that I'm going to break it. So once again I come asking for guidance. 

Essentially what I have going so far is the program asks you to specify two files, a log file, and a file containing 'suspicious signatures'. It them compiles a regular expression from each line of the signature file and then outputs to the screen anything that it finds matching. What I'd like to do next is, on each line of the signature file, in addition to the regular expression put some sort of description of what it is. IE, say I have a regular expression that indicates connection attempts on port 8080 of a web log. Next to that regular expression indicating port 8080, I want to put something like: #Possible proxy attempt." 

How I'd like it to turn out is for it to output to the screen the excerpt of the regular expression from the line that it matches, and in an adjacent column, print the description, and then in another column, display a count of lines that matched that RE. At this point I'm able to get it to print the matching lines, and increment a count based on what it found, but not sure how to implement columns, or to make the count based solely on individual lines that matched, not the entire log file. Any ideas or suggestions?

---

### Post by Stev0 on 2010-03-02
bump

---

