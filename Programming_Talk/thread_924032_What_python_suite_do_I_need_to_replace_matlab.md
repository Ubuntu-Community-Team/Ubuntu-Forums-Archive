---
title: "What python suite do I need to replace matlab"
date: 2008-09-19
forum: Programming Talk
---

### Post by elbarto_87 on 2008-09-19
Recently I installed ubuntu, which up to this point has been the first Linux based operating system I have ever used. While I still do not fully know my way around the system, I have found the support and the software to be exceptional.

This has prompted me to look for an alternative to matlab, for a number of reasons, namely licensing restrictions and matlab itself doesn't run as smoothly on linux machines (compared to windows) from my experiences. 

I have read many posts on this site, and after much thought, it appears that if I convert to any language, it should be python. 

I have been looking into SAGE, it appears to offer alot of functionality, tho I dont know if this is too much overkill for what I actually require. What I would like is some advice on what option would be the best for my applications in python.


Basically, I am in the process on writing structural analysis program in matlab as part of my thesis. I have writen many user defined functions, which I call from the command line to manipulate global variables. 

ie. 
anode(0,0,0) adds the point x = 0, y = 0, z = 0  (node 1)
anode(1,1,1) adds the point x = 1, y = 1, z = 1  (node 2)
amem(1,2) connects the points with a line (adds a member between nodes)

As you can see, the way I am use to programing is to write many smaller functions and call them as I need. Ideally I would like to be able to do the same thing with python if it is possible (and is there an alternative to working in a terminal window?).

In the future I will develop these functions into a GUI, for which matlab has the capabilities but I have also read that python has many compatible add ons to do such tasks also.

I will leave my post at that for now, but please be prepared for many questions to follow :).

Thanks


Regards Elbarto

---

### Post by olejorgen on 2008-09-19
You could try octave. It's basically open source matlab. I'm not sure how much gui building functionality they have implemented yet though.

---

### Post by elbarto_87 on 2008-09-19
Thanks for the reply olejorgen. I have tried Octave twice, and while it is promising, I have found it to be a little buggy and I am not a fan of working inside terminal the whole time. In saying that, many people find octave a good replacement for their matlab duties. I tried Scilab briefly, and I think this is an excellent piece of software and one which will grow fast in the scientific community. The UI is pretty good in my opinion, and I think octave would greatly benefit from a similar UI. The editor that comes bundled with Scilab is also very convenient. Tho the Scilab and Matlab syntax are somewhat different, I found it to be the best replacement for matlab I have tried to date.

The reason I chose not to invest more time in Scilab was that to become effective at writing code, I would have to spend hours and hours as I did trying to master the basics of matlab. It makes more sense to me to invest this time in learning a language that is considered somewhat more powerful and flexible then the lanugages specifically for matrix/numerical mathematics. In saying that however, python is alot different language to anything I have used in the past, so I dont expect the transition to be an easy one.

The many open source libraries and community support are key features attracting me at the moment. Also, maybe with some knowledge in python I may be able to give something back to the open source community at some stage in the future.


Regards Elbarto

---

### Post by screech on 2008-09-19
Have you tried qtoctave?
It's a qt gui for octave.

---

### Post by elbarto_87 on 2008-09-19
I have just had a look at qtoctave in google. It looks like a much better interface and I will definitely give it a go with my existing matlab scripts to see how I get on. Thank you for that screech.

In regards to python, is there anyone out there using it for a matlab replacement? It seems like a powerful language according to the posts I have found,but there are so many packages out there I dont know what I need to do the job I need.

I have heard of people useing 
>numpy
>scipy
>matplotlib

I am unsure of how you use all these packages together or if this is all I need to install to have a powerful software suite. Any tips from user out there using this language to solve numeric problems would be appreciated.

Is there a UI that you use for python that you can recommend?
What libraries do you have installed?
Is there a certain editor you prefer?
Do you use a certain application for GUI's?

Elbarto

---

### Post by olejorgen on 2008-09-19
Ipyhon is quite good for quick interactive usage. Of course, something like slime (lisp "ide" for emacs) whould be perfect, but I'm not aware of anything like that.

---

### Post by matja on 2008-09-19
Hi Elbarto,

I've recently migrated from Matlab to matplotlib for plotting and I'm not looking back. The interface is very similar to Matlab if you want it to be, so it shouldn't be that difficult to make the transition. I had prior knowledge of both Python and Matlab though, so your experience may of course differ. To manipulate the plots, you get a little exposure to numpy as well and I haven't found anything to complain about. So, in my humble opinion, I would say numpy/scipy/matplotlib (a.k.a. pylab) is a great choice if you come from a background in Matlab. Whether it's a full fledged substitute for Matlab, I leave for the experts to comment.

The main attraction for me was that now I'm able to glue my whole program together in Python, writing the user interface, displaying the results and even parallelize it with pure Python code and writing the actual simulation routines in C or C++ and calling them from Python. Well, at least that is the plan, we have only just started the project, but so far it has gone very well.

I can also recommend ipython if you want to experiment with pylab. It has a "-pylab" command line option that loads all the necessary modules and make it similar to the matlab terminal. If you're looking for a full IDE, however, I guess it's lacking some features. As for me, I'm one of those emacs guys ;)

Best regards,
Mattias

---

### Post by cb951303 on 2008-09-19
most popular scientific and mathematical python module: [http://www.scipy.org/](http://www.scipy.org/)
edit: oops already mentioned

---

### Post by elbarto_87 on 2008-09-19
Thank you for the suggestions, I will look into ipython and pylab(some good reading material for the week end!).

There are so many different packages an configurations in the open source community which is great if you know what you are looking for, but with so many choices available it seems appropriate to see what configurations are working for others in a similar situation. 

Matja, you mentioned pylab. When I go to my synaptic package manager and search for pylab the only entry I get is matplotlib. Is pylab actually the whole environment or just another library for python. I did find this site [http://www.scipy.org/PyLabAwaits?highlight=((PyLab](http://www.scipy.org/PyLabAwaits?highlight=((PyLab))), but still not sure exactly how to instal "pylab".

I am not expecting to find a 100% replacement for matlab, but given that I only use matlab to about 10% of its computing power I am hoping I can find a suitable package. The development of a GUI for my program is something I will definitely like to look into in the future. Like I said in my original post, I currently need a program that I can build user defined functions and then call them from the command line. With what I have seen off matplotlib, im pretty sure python will handle any plots I need.

The idea of "glueing" my program together at the end of it is also something I am interested in. I cant wait to start experimenting with python packages to learn some of its capabilities.

Regards, Elbarto

---

### Post by Bichromat on 2008-09-19
> **elbarto_87 said:**
> Matja, you mentioned pylab. When I go to my synaptic package manager and search for pylab the only entry I get is matplotlib. Is pylab actually the whole environment or just another library for python. I did find this site [http://www.scipy.org/PyLabAwaits?highlight=((PyLab](http://www.scipy.org/PyLabAwaits?highlight=((PyLab))), but still not sure exactly how to instal "pylab".

Actually, pylab is part of matplotlib. Once you've installed matplotlib, you can import pylab in your code with "import pylab"

---

### Post by elbarto_87 on 2008-09-19
Ok, so if I currently just have the standard python that comes bundled with ubuntu, what packages do I need to install?. Do they come with their own editor? Once I have a solid platform to learn from I think I will be able to pick the language up ok as I have a few ebooks on python, and there seems to be alot of tutorials on the net also. The hardest part for someone new to linux like myself is figuring out where to start I think.....

Sorry for all the questions, and thank you once again for all the help.

Elbarto

---

### Post by CptPicard on 2008-09-19
To be honest your premise seems slightly misguided ... you are engaged in a kind of apples to oranges comparison.

Python is a general-purpose programming language. You write your code in your text editor of choice and then run it through the interpreter to execute it. Whatever libraries you choose to make use of, you're still the coder who is responsible for "putting the application together".

Matlab on the other hand is a kind of mathematics workbench that you work inside using its specialized tools, and this makes it possible for it to have dedicated editors and all that stuff...

---

### Post by Gilabuugs on 2008-09-19
I've never had any problems running matlab in linux enviroments, even my school uses ubuntu servers to run matlab as well as X tunneling even seems to be semi-fast on campus...

unless you want to use numeric python and such things, and actually learning python I suggest using matlab, unless you do not have a liscense in which case you are stuck with octave, sage, different python libraries, etc... (all fine but will not necessarily be the same as matlab)

---

### Post by elbarto_87 on 2008-09-19
I have a student version of matlab, which is doing the job fine but really only limits the use of matlab to "educational purposes". I will not always be a student, and the programs I am writing I intend on maybe using for commercial purposes when I graduate. Another limitation is that when you write a code in matlab, not everyone has access to a copy given the price of it. I have found matlab to be an excellent tool for what I am doing, but after reading through this forum over the last month have found that many people are using python for similar tasks to what I am using matlab.  

> Python is a general-purpose programming language. You write your code in your text editor of choice and then run it through the interpreter to execute it.

I agree CptPicard, I still do not have a clear concept of what python actually is so I appreciate your concise statement above.  


Maybe I have acidently misled you as to what my situation actually is. I am currently writeing code in matlab on a windows machine, and it is going pretty good. With all the talk about numpy/matplotlib/scipy I thought I would look into these open source alternatives to see if they are a feasible option or not. That is why I initially asked what python suite I would need to use in order to convert from matlab. I want to make sure python can actually do what I need before I invest many many hours learning this new language. If I was going to learn another language I would prefer it to be something like python rather than scilab or the likes as there seems to be so many different applications of the python language, where scilb etc are mainly for number crunching.

Elbarto

---

### Post by cb951303 on 2008-09-20
[http://www.scilab.org/](http://www.scilab.org/)
[http://freemat.sourceforge.net/](http://freemat.sourceforge.net/)

some other mature projects

---

