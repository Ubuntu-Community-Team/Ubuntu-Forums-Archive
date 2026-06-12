---
title: "Lan Source control server -- but which one?"
date: 2011-07-03
forum: Programming Talk
---

### Post by doas777 on 2011-07-03
I'm looking to add a source control server to my network for personal  projects, and I realize that I have little experience with the non-MS  offerings. I code primarily in Eclipse, Visual Studio, and Geany. IDE  integration is a key requirement.

Can you all recommend any good source control platforms for my needs?
I've looked briefly at svn, git, and mercurial, but they all seem to be for much bigger scenarios than I am looking at. 

any recommendations for a home source control platform?

---

### Post by slavik on 2011-07-03
svn is easy to set up and is supported by all, I would recommend git though as I love it due to the fact that you can make commits on the road, don't require a central server and can merge stuff back in.

---

### Post by ve4cib on 2011-07-03
Git and SVN are definitely the big two choices.

Git has the advantage that it's entirely distributed.  Every working copy is its own repository, so you can commit/revert/branch on one machine, without affecting the central repository (until you push your changes that is).  It's great for projects with multiple people, or for situations where relying on a central server is impractical.

SVN on the other hand has one central server than manages the entire repository.  Everyone commits to and updates from the same server all the time.  In my experience SVN is a little more widely-supported (especially in terms of shell integration and GUIs).  If you're the only one working on the project, or you have a fairly small group, SVN is arguably easier to use.  The only real downside is that to commit changes you need a connection to the central server.

The choice is really just a personal preference if its for your own private projects.  Personally I lean very slightly towards SVN most of the time, simply because I've used it more in the past, and it has some nice GUI tools (TortoiseSVN on Windows, RapidSVN + Meld + Nautilus scripts on Linux).

---

### Post by slavik on 2011-07-03
> **ve4cib said:**
> Git and SVN are definitely the big two choices.

Git has the advantage that it's entirely distributed.  Every working copy is its own repository, so you can commit/revert/branch on one machine, without affecting the central repository (until you push your changes that is).  It's great for projects with multiple people, or for situations where relying on a central server is impractical.

SVN on the other hand has one central server than manages the entire repository.  Everyone commits to and updates from the same server all the time.  In my experience SVN is a little more widely-supported (especially in terms of shell integration and GUIs).  If you're the only one working on the project, or you have a fairly small group, SVN is arguably easier to use.  The only real downside is that to commit changes you need a connection to the central server.

The choice is really just a personal preference if its for your own private projects.  Personally I lean very slightly towards SVN most of the time, simply because I've used it more in the past, and it has some nice GUI tools (TortoiseSVN on Windows, RapidSVN + Meld + Nautilus scripts on Linux).
there is not rabbitvcs which attempts to combine all of them under nautilus, but I like git, because creating a repo for a project is as easy as:

```

mkdir project
cd project
git init

```

---

### Post by doas777 on 2011-07-03
Wonderful responses, Thanks guys!

I had been thinking that svn was going out of fashion, but as you describe it, it does sound like it fits my needs. 

I am intrigued by git however. From the description, it sounds like every client is itself a server. how does the central repository get replicated, and can I back it up?

Thanks again! I'll try svn out and report back.

---

### Post by ve4cib on 2011-07-03
> **slavik said:**
> there is not rabbitvcs which attempts to combine all of them under nautilus, but I like git, because creating a repo for a project is as easy as:

```

mkdir project
cd project
git init

```

But imagine how much easier it could be if you could just go:

```

Open Nautilus
Double-click through a whole bunch of folders to get to where you want to be
Ctrl-Shift-N project
Right-click on Project > Initialize Git Repository

```

:p

---

### Post by slavik on 2011-07-03
> **ve4cib said:**
> But imagine how much easier it could be if you could just go:

```

Open Nautilus
Double-click through a whole bunch of folders to get to where you want to be
Ctrl-Shift-N project
Right-click on Project > Initialize Git Repository

```

:p
wait until rabbitvcs is up to speed on git (this is major vcs after svn)

---

### Post by juancarlospaco on 2011-07-03
Bazaar

---

### Post by doas777 on 2011-07-04
Well, I've gotten svn up and running, though it took a little doing to move the repository off my home partition onto an ops drive, and then to get DAV up via apache. I hadn't realized that most svn interaction is done over DAV. In my security training, I've been taught to be suspicious of it in general.

I was able to get the ankhSVN plugin for visual studio configured and added a couple projects to it. the interface seems intuitive enough, since I'm familiar with VSS/TFS integration from work.

Eclipse seems more troublesome. I've done some research and selected subversive just cause its better integrated into eclipse. I've managed to get eclipse to connect to it, and can browse the repository. I did add a project to the repository using the svn explorer, but it seemed at first like the project had not realized it was now svn-sourced. after restarting eclipse however, that seems to have addressed itself. 

I'll work with them both for a  bit and post back a more informed view.

Thanks guys!

---

### Post by DangerOnTheRanger on 2011-07-04
I'd go with Mercurial. It's distributed, just like Git, but I think it's a little more customizable, due to the fact that it's (mostly) written in Python. If customization isn't a big issue for you, go with Git.

---

