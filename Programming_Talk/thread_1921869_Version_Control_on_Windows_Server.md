---
title: "Version Control on Windows Server"
date: 2012-02-07
forum: Programming Talk
---

### Post by gunksta on 2012-02-07
I am slowly but surely moving the company I work for towards better development practices / FOSS. Until recently most projects were one developer per project. However, as the complexity of our projects have grown we increasingly need to involve multiple developers on a project.

Hello Version Control !

I have experience using GIT and I've looked into setting up msysgit on one of our primary servers. All of our servers currently run Windows. (Over time, I'd like to move away from Windows servers, but that what we've got.)

I am also considering subversion and bazaar. From what I have read, all three can run as a service on Windows. Whatever I use, I need to be able to integrate access controls and I think the server guys would prefer to have a nice, easy to use GUI.

I can go over to GitHub and find plenty of pro-GIT folks. I'm hoping to get a broader perspective here. Can BZR effectively run on Windows as a Service and is it easy to set up access control for projects? Can I "push" from the primary repository to a remote server? I've got no real experience setting up / using bzr and I try to provide solutions that encourage FOSS whenever possible to my boss.

I am curious to hear from anyone else who has successfully used a FOSS based version control system running on Windows Server. What did you use and why did you choose it? Etc.

Thanks

Note - I am not trying to start a flame-war here. I just want some perspectives that I can't really get over at GitHub (can't imagine why people there are biased) and I have to run it (the central repo) on Windows. Not my choice, but that doesn't really matter. I am the only Linux user in the company.

---

### Post by lykwydchykyn on 2012-02-07
I guess this isn't quite what you're asking for, but I had a lot of trouble using subversion on a file share.  In our case, it was Netware.  I had a lot of trouble with subversion in general.

I've since switched to git, and I think it's pretty keen all around.  I don't have any trouble using it with any OS.

I don't use a centralized server, though, so I can't comment on that.  Haven't used bzr at all, either.

---

### Post by myrtle1908 on 2012-02-07
Mercurial (pretty much same as GIT) works well on Windows.
[http://mercurial.selenic.com/](http://mercurial.selenic.com/)

VisualSVN if you don't like GIT/Merc distributed source control.
[http://www.visualsvn.com/](http://www.visualsvn.com/)

Edit: sorry haven't time to comment on benefits or my experience of either.  however, I use both and they are excellent and very easy to use ... esp Mercurial on Eclipse.

---

### Post by gunksta on 2012-02-08
I confess, I had not really considered mercurial in part because I don't know anything about it. I glanced at the website and I was immediately greeted with installers for Windows and OS X (obviously I can install locally without going to their website) and since it uses Python I would be able to install it relatively easily which is similar to bazaar in this regard I think. We already use Python on the server for this and that, so using another Python based application keeps our dependencies to a relative minimum.

---

### Post by Simian Man on 2012-02-08
The only ones I've used on Windows were SVN and Mercurial.  Both worked well enough, but I prefer Mercurial in general.  Mercurial is also a little simpler than git, so it may be easier for people new to version control.

---

### Post by gunksta on 2012-02-08
SVN and Mercurial seem like two strong candidates - which begs a question.

I saw a complaint regarding SVN that it was difficult to set up Access Control on SVN. I've never run a SVN server, so I don't really know about that. Obviously, most FOSS version control systems are designed to enable access (which is important for FOSS projects) but we want to have fine grained control of write and to a lesser extent read access to the projects.

Does Mercurial make it relatively simple to restrict access to the code? If someone has more experience with SVN running on Windows who disagrees with what I read, I'd be interested in hearing about that too.

---

