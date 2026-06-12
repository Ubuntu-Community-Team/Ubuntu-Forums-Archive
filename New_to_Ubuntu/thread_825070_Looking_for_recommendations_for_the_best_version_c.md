---
title: "Looking for recommendations for the best version control system."
date: 2008-06-10
forum: New to Ubuntu
---

### Post by laptoplinux on 2008-06-10
I am beginning a major coding project and would like some help with decided which version control software to use.  This is my first time taking on a coding project of this magnitude, and it will also be my first time working with version control.  Since I will be setting up the version control system myself, I can choose which program to go with.

The most popular options seem to be svn, mercurial, git, and bazaar.  Unless there is a compelling reason to pick the centralized svn, the decentralized nature of the other three makes them more appealing to me since I would like the freedom to work without connectivity if necessary.  

So, knowing that I know next to nothing of version control and will need a good, reliable, and flexible system with good documentation and available help for a multi-year software project, what opinions/suggestions/wisdom can you guys offer?

[Note to admins:  Not sure if this is the right forum or not, but I am definitely an absolute beginner when it comes to version control.  Please move this to a more appropriate (i.e. more likely to get a helpful response) forum if you feel it necessary. ]

---

### Post by cmnorton on 2008-06-11
I worked on a team of fewer than twelve engineers, and we used CVS successfully. We used the shared drive mode to get at the repository, and this was on Windows 2000. I use CVS now for the repositories of several database applications; I am the only user.

There are a lot of open source products out there, and you should not only listen to advice here, but also go out and do a lot of research. Try to pick something that will be around a while -- if you can guess -- and that is reasonably well-known in industry. Also, you need to know your requirements.  Some products excel at some things. CVS has bailed me out many times, just because I have prior versions of my source.

The best and most complicated source repository I have used -- started on Unix -- is IBM's -- Atria's -- ClearCase. It is very, very expensive, and did not always merge as well as claimed. PVCS was not bad, but again was a non-open source product. We used some manager at DEC, but I've forgotten its name (CMS?)


So, I am not recommending anything to you other than researching and listening, and knowing what you want to do.

---

