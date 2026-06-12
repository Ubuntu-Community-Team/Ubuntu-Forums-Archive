---
title: "HyperGet - recruiting developers for this new project"
date: 2005-10-31
forum: Programming Talk
---

### Post by wolphin on 2005-10-31
Hi,

I am looking for developers who are able to program fluently in C (for GNOME) - whether it be using Glade, Anjuta, or by complete code. ;)

HyperGet is an application which will hopefully pave the way for new users and attract them to the Linux community (especially Ubuntu users). The idea behind this application is: simplicity, usability, functionality. Its purpose is, in summary, to allow users to download packages (with full dependencies) for their offline Ubuntu (or Debian-based) computer using another computer with access to the internet. The computer used to download the packages can run either Linux or Windows, which will allow even more people to use this application with the fewest number of problems. I have tried to outline solutions to some of the main problems you may already see in HyperGet at its home site, [http://hyper-get.sf.net](http://hyper-get.sourceforge.net).

I have already recruited two developers who are willing to work on the Windows side of the second application, yet am still looking for around 3-5 developers to work on both the first application and the Linux part of the second one.

Even if you decide not to join the other developers, please check out the project's homepage and leave a comment here! Your feedback will be greatly appreciated, and I'm sure it could be put to good use! :D

I am still learning C, which is why I won't be taking part in the coding of the app, but I'm open to both suggestions and offers! Thanks in advance!

Max

Update: I may also be looking for Python or Java developers, so keep your head up! ;)

---

### Post by oldmanstan on 2005-10-31
at this point i probably don't know enough C to be of much help coding but it sounds like an awesome idea and i'd be willing to help any other way that's needed...

as someone who went through 4 or 5 abortive attempts to switch to linux before succeeding i can understand some user's frustration when trying to switch and anything that could make the process smoother and further bolster the community is definitely worthwhile!

---

### Post by wolphin on 2005-11-01
oldmanstan - thank you for your comment! Yes, I think that this application could really help both migrating users and normal users alike! I mean, I've needed an app like this more than once, and one day when I downloaded an app without its dependencies I came up with the idea.... :)

In order to make the second application (the status file interpreter & downloader) cross-platform, we have decided to code it in Java. So, I'm now looking for 2 GTK+ developers and 1 more Java developer. If you are interested, please contact me at [email]aib.wolphin@gmail.com[/email] or by posting a comment here. Thanks!

Max :D

---

### Post by jobezone on 2005-12-15
If I could give you an advice is that you start small. Take a look at apt-zip (I haven't looked at it though) and think on creating an easy GUI for it. Just this would be a great gain.
Also take a look at synaptic, see if that functionality makes sense in it, and if it would be doable by using apt-zip as well.

As for creating a windows version for it, why not take a Ubuntu LiveCd and remaster it to include your software?

My humble advise (from a non-programmer point of view :/ ): Keep it simple, don't reivent the wheel necessary, and re-use as much as possible (acording to your objectives, of course). 

Anyway, good luck!

---

### Post by gord on 2005-12-15
just to note, if you are running a debian basted system you can just get the downloaded packages in .deb format from apt's cache, something like /var/cache/apt/


you can also just get the .debs from the repositorys themselfs as they use the http transfer method, [http://archive.ubuntu.com/ubuntu/pool/main/](http://archive.ubuntu.com/ubuntu/pool/main/)
allthough obviously you don't get dependancys that way.

id also recomend python over java, its much easyer to work with, you can create standalone .exe's and has tie in's to the apt system anyway. you can also use wxwidgets with python via wxpython which gives a nice native look for a lot of platforms. its also very easy to use.

if i had to give some advice though, don't get carryed away, projects that get to big too fast never get done.

---

### Post by macgyver2 on 2005-12-15
That definitely sounds like a useful application.  Twice in the past 6 months I've helped to install Ubuntu on computers with just dial-up modems.  I did the back and forth package retrieval thing (from a windows machine) so I could get everything needed to compile a modem driver (pretty much build-essential).  HyperGet sounds like it's going to be a very nice app.  I look forward to seeing it in action!

---

### Post by Van_Gogh on 2005-12-15
I too think this sounds like a great idea for computer without own broadband connections. My own knowledge of C is not that great, but from what I know I must admit that I would personally *not* like to do this in C when there are so much better alternatives available. I mean, C is best used for processor-intensive applications, while this application clearly is IO-intensive, so it just seems like the wrong tool for this particular job.

I unfortunately don't know any real Java, but I consider myself an acceptable Python programmer, and I've been interested in joining some open source project for a while. So if you decide to go with Python, I'd be interested in joining. My email is terji78 @ yahoo . com

Good luck with the project!

---

### Post by Van_Gogh on 2005-12-15
On a sidenote, if you decide Python+pyGTK(or wxPython), you don't need to create seperate Windows and *nix version, as the GUI-toolset will work on both. Also, I also agree that this doesn't need to be a huge project: just create a crossplatform GUI(quite do-able), a crossplatform program that creates a Debian-like repository file on the removable disk and downloads the needed packages into it(maybe the difficult part, requires knowledge what a Debian-like repository looks like and should work on Windows too.) and a program that: (1)enables the removable disk as a repository, (2)installs stuff from it and then (3)un-enables(sp?) the removable disk repository(easy too).

You probably have your own ideas too how to implement it.

---

