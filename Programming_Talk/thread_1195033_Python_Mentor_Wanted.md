---
title: "Python Mentor Wanted"
date: 2009-06-23
forum: Programming Talk
---

### Post by arm-c on 2009-06-23
Hello,

I have written what I feel is a useful program to work with the acerhk driver.  It is still growing and to date, I have had over 750 downloads from SourceForge.net  There are likely many more downloads from other sources (such as RPM Search).

I am using this program as a "learning project".  One that serves to provide me problems and which I seek to write code to solve.  Usually, I look for my answers in the the manual; but not for a liberal arts type person, some of the instructions are cryptic.

As a self-taught / independent learner, I do OK, but I sorely miss having a code mentor that I can turn to when my attempts to find a solution fail OR when i just don't quite grasp the concept.  Also, it helps for a mentor to be able to review my code and offer constructive suggestions on how to improve my code.

If there are any personnel interested in providing such mentorship to me, please let me know.  I don't code all the time and will go in starts/stops at irregular periods based on career demands and life demands.

Drop me a line or post a reply here.

---

### Post by simeon87 on 2009-06-23
For specific problems, it's better to post the problem on a forum, such as this one, as that'll probably solve your problem faster: more people can look at the problem and whatever mentor you choose, that person won't be familiar with all the technologies in all kinds of domains. Unless you mostly work in one type of domain and you're lucky enough to find a mentor in that area.

---

### Post by arm-c on 2009-06-23
Right now, 

The area I want to get a better understanding of is how to manage variables that cross over from Class to Class to Function without using the global keyword.  I'm still reading more tutorials on Python and suspect that I haven't gotten to the point where my questions in this regard *May* be answered.

Hand in hand with that comes a review of structure of my program.

These are general and new programmer oriented.

My program uses pyGTK.  Most of the GUI is done with GLADE 3 and dialogs with hard-coded pyGTK.

I will certainly keep this in mind for a means to find answers to future problems.

Anyone up for taking a quick look at it and offering me some quick pointers or what to read more on?

---

### Post by Paul Miller on 2009-06-23
It looks like you just need to read more code, in general.  I can recommend "Programming Python" and the "Python Cookbook" (the latter of which is also the title of a web site with some interesting code and commentary you can browse) as good resources.  Other than that, look at projects on PYPI that seem well-done to you and start digesting their code.  Only by reading and writing code can you get better at design issues like "where to put state information," which seems like what you're asking here.

If I understand correctly, the solution to your problem is to not make it a problem, really.  If you find a particular object X is frequently needing to access a data member of some other object Y, you might just want to merge the classes X and Y together to avoid having to pass the data around all the time.

OTOH, if what you are dealing with truly is "global" state data (configuration settings can be this way, for instance), and you don't want to pollute the global namespace of your project, wrapping the global state up in a module works well, too.  For instance, using the configuration example, you can just put all the relevant config defaults into a module named, say, config, and import it wherever it needs to be read or modified.

If this isn't what you're trying to do, then I need a more specific example, ideally with code, but cut down to show the essentials of the problem and nothing more (i.e. a minimal example).

Finally, in terms of a "Python mentor," if that's what you truly want, I'd recommend you find someone who's local to you -- either a coworker or a friend you can bounce ideas off of and, who preferably knows Python (or at least programming in general) better than you do.  Randoms on the net aren't good for that sort of thing.  (We're great for answering specific questions, just not any sort of long term relationship thing.  Heh.)

Edit: Oh, and if you want someone to take a look at your code, either post the code or post a link.  Someone will probably do it.  If not, you're no worse off than if you hadn't posted the code.  If the code is long or complex, a minimal example will be better.

---

### Post by blackxored on 2009-06-23
Check some books like "Beginning Python: From Novice to Professional", "Learning Python", "Programming Python", "How to Think Like a Computer Scientist: Python Edition". 
Join the python-users mailing lists. Get some open source projects and study them as far as you're progressing. Post in the forums specific problems & seek solutions. 
That won't make you pro, but it will give you enough knowledge of python to be effective. Then if you wanna be professional, check about methodologies, best practices, team working, etc. 
That's all for now.

---

### Post by arm-c on 2009-06-23
Paul Miller and Blackxored,

Thank you for the excellent responses.  I will dig into some of the links and materials you both recommended.

I will also look at a manner to reduce the code to essential element of the problem.  Yes, the primary problem is configuration variables in the program, but I will come back to that.

I honestly wish I knew another programmer that was local.  My job is not in IT.  Also, the area I live in does not have a LUG that could be a possible source for a python programmer.

I'll limit my posts to specific problems and shortened code when necessary.

Again, thanks so much for the thoughtful and precise comments.

---

### Post by Mirge on 2009-06-23
Right about now I'd kill for a Qt4 mentor :)

---

### Post by master_kernel on 2009-06-26
You could also take a look at the KernelCheck code - it's composed of PyGTK and Glade3.

---

### Post by nvteighen on 2009-06-27
Hm... Look at my sig. PycTacToe was created with such a goal in mind, to be a simple project people could learn from. Version 0.1 has been released and now a Connect-4 module would be great; given the plugin architecture, you can just focus on your module and don't care on what happens elsewhere (just learn to use the API, of course).

If interested, install bazaar and check it out :)

And if you don't like it, there surely are tons of other projects waiting for you (yes... projects always need developers!)

---

