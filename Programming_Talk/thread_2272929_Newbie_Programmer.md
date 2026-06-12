---
title: "Newbie Programmer"
date: 2015-04-09
forum: Programming Talk
---

### Post by branau on 2015-04-09
Hey guys, I just recently finished up with the Python tutorial over at Codecademy, and I'm not quite sure where to go from here. My long-term goal is to get into either Full Stack web development or web app development, which is why I decided to go with Python. Plus, I had read in many places that the Python community is helpful and Python is a relatively easy language to learn. I don't feel quite confident enough to jump in on an open source project just yet, considering I have a basic at best understanding of Python, but I would like to learn Django. Would you recommend I continue with strictly Python until I have a better grasp on it or would it be alright for me to move on to using Django, considering it's written in Python?

---

### Post by TheFu on 2015-04-09
I think you did well with Python as the first language. 
[http://blog.jdpfu.com/2011/10/19/how-to-learn-to-program](http://blog.jdpfu.com/2011/10/19/how-to-learn-to-program) - learn to be a programmer. I think it is important to concentrate on 1 language in the beginning - 3-6 months (depending on effort).  There are lots of books to work through - you are ready for those now.

Are you using TDD and version control? If not, start immediately.  I can't speak for Python, but for Ruby there is a Rails + Ruby training book that teaches everything a current-gen ruby-on-rails dev should be using - ruby, rails, rvm/rbenv, TDD, git, heroku.  The TDD and git stuff is completely cross-language/cross-platform. [http://blog.jdpfu.com/2007/09/06/Ruby-on-Rails-huh](http://blog.jdpfu.com/2007/09/06/Ruby-on-Rails-huh)  The Ruby book we used in my classes was: [https://www.railstutorial.org/](https://www.railstutorial.org/) - look for something like that for python + whatever framework you like.

Oh - and try to find some real humans using the language/framework you want to learn. Go and meet them in person. Join their group, learn, talk, teach. Nothing forces you to learn like having to teach others.

And find an itch that you have - scratch it - that means write a little program you need/want and use it.

---

### Post by branau on 2015-04-09
Thanks for your reply!

Right now I work as an English teacher in Mexico and I only work two days a week. The other 5 days I spend pretty much all day working at this stuff so I'm sure that within 3-6 months I could easily get the hang of it. I'll take a look at that article and do my best to only stick to Python and its libraries and frameworks for the next 3-6 months.

I've been sort of doing TDD in the sense that I break my projects down into steps and work on them one at a time, but I haven't been saving them as separate files or anything like that. More like I just start my program, and continually overwrite the same file as I add new stuff to it. I'll read up some more on TDD though as well. And I'll keep an eye out for some Python + Django books. 

As for the people, I've joined up with the LoCo group for my state in the USA, Oregon, but I'll see if there are any Python/Django specific groups too. 

Thanks for your help! I really appreciate it and I'll get started on these points immediately.

---

### Post by TheFu on 2015-04-09
TDD is where you write test cases (in code) before you write the code itself. Then you run the tests, see it fails, and work on the code until all the test cases pass.  Most languages have excellent tools to make this happen, python is no exception.  Make this a habit now. It does save time.  You don't need a separate book on this TDD stuff.  I'm looking for a book that teaches all these things but with django and python now.  The [http://pythonhackers.com/top-python-projects/](http://pythonhackers.com/top-python-projects/) python koans link there is interesting - solidify your python AND see how TDD should work. Nice.

Also, get used to using git (DVCS) now. This is more important than TDD. [http://www.youtube.com/watch?v=bwQqz3cb1Jc](http://www.youtube.com/watch?v=bwQqz3cb1Jc) - a nice overview.  It is addictive if you've ever used other version control tools. 

This may not be necessary, but before you get too far, you really want to get used to managing everything about your coding environment - do NOT trust the system versions of python. Always load your own into a separate area. There are tools for this - I don't use python, but rvm and perlbrew are the tools for ruby and perl to manage multiple environments without touching the system versions.  The system python is used by all those packages (apt-get) which depend on python and is usually fairly old.  Also, install django into the same environment - having a compatible "stack" is very important.  I don't use version control to manage stacks, just my project code.

Hopefully, this stuff isn't confusing. 

Oh and the book that is project-based teaching fundamentals of software development (git, tdd, etc) [http://www.obeythetestinggoat.com/](http://www.obeythetestinggoat.com/)
Good luck!

---

### Post by branau on 2015-04-09
Interesting, I'll download the python koans program and get started with that. Luckily that book you shared is available online for free so I've marked that in my bookmarks as well, I'll be sure to work through that. It appears to work with Python 3 and Django, so that seems right on track with what I'm going for. 

That video is quite long but I'll watch it if it's worth the time. I've played around a little bit on GitHub to see how it works but I haven't done any real work with it so this could be helpful.

As for the coding environments, are you referring to IDE's? I understood everything from your post except this part. I haven't actually used any IDE's yet because I read it's best to just work with a simple text editor when you're getting started.

---

### Post by TheFu on 2015-04-09
> **William_Brawner said:**
> As for the coding environments, are you referring to IDE's? I understood everything from your post except this part. I haven't actually used any IDE's yet because I read it's best to just work with a simple text editor when you're getting started.

No.  I mean when you type "which python" what does it return?  If it returns /usr/bin/python - that is the system python and probably NOT what you want to use developing webapps.  You need to manage all the code in the environment - the entire software stack needs to be self-contained and NOT dependent on the OS versions.  If you use apt-get install to setup your total stack, you've failed.  
[http://stackoverflow.com/questions/2812471/is-there-a-python-equivalent-of-rubys-rvm](http://stackoverflow.com/questions/2812471/is-there-a-python-equivalent-of-rubys-rvm) and [https://github.com/yyuu/pyenv](https://github.com/yyuu/pyenv)

github is fine, but not the same as what you'll use daily with your own git setup. After you watch that video, you'll understand the social aspects of git - which is key.  There is a free Git Book - Git Pro or Pro Git ... if you prefer a book - but I don't think it covers the social aspects of using git.

---

### Post by branau on 2015-04-09
Got it. Yeah, I've been using the system python so far, so I'll install pyenv and get used to using that as well. I'll also figure out how to install Django with that. 

And I'll take a look at that book as well as the video. 

Thank you big time for your help. When I finished the course at Codecademy I really had no clue where to go next. Now I've got plenty to keep me busy with for quite some time haha. I really appreciate your help!

---

### Post by TheFu on 2015-04-10
PyCon 2015 Videos are up: [https://www.youtube.com/channel/UCgxzjK6GuOHVKR_08TT4hJQ/videos](https://www.youtube.com/channel/UCgxzjK6GuOHVKR_08TT4hJQ/videos)

---

### Post by branau on 2015-04-10
Wow that channel is full of information. I'll add viewing those videos to my to-do list. Thanks again!

---

### Post by TheFu on 2015-04-10
> **William_Brawner said:**
> Wow that channel is full of information. I'll add viewing those videos to my to-do list. Thanks again!

I'd hoped someone else would comment - someone who actually does Python. Oh well.  At least you can see from the videos that the topics I was suggesting aren't just mine. The entire community is pushing this stuff.

I'm grabbing the Ansible video myself. Not really for programmers, more for sys admins, but if you have 5 or more systems to maintain, ansible is my go-to solution.

Oh ... and if you need a little diversion: [http://blog.jdpfu.com/2015/04/10/new-favorite-band](http://blog.jdpfu.com/2015/04/10/new-favorite-band) - good for a smile.
I'm putting off doing taxes today.

---

### Post by branau on 2015-04-10
Yeah I would like to hear from someone who knows Python quite well but regardless, I really appreciate all of the information you have provided to me. Even if you can't answer my specific questions about Python, you've helped me greatly with Computer Programming in general. 

Haha I'll take a look at that. I don't have to file my taxes since I live in Mexico and don't make enough to require my filing them in the States :P

---

### Post by branau on 2015-04-13
Another question, if anyone sees this. I've been working with Python for about 2 weeks, 6 hours a day on average (yes, I have no social life), and I'm quite confident that I can easily manage functions, strings, dictionaries, lists, read/writing to files, importing/creating modules, logic and looping, basic stuff like that. I learn very quickly and remember much of what I learn, especially when I use it (and I practice writing and reading code for much of those 6 hours average per day). My question is, at what point could I or should I start picking up another language? I'm planning on learning C, as I'd love to contribute to the development of Ubuntu and from what I understand, many programming languages are modelled after or built using C. To be more specific, what should I be able to do before I undertake learning a second language?

---

### Post by TheFu on 2015-04-13
Complete a non-trivial program following best practices in Python (TDD/git/design patterns, etc.). I would encourage learning OOD/OOP too.

OTOH, it is your learning process. If you want C, go do C.  Compile languages have some different considerations.

---

### Post by branau on 2015-04-14
Thanks again Fu, I'll see what I can do.

---

