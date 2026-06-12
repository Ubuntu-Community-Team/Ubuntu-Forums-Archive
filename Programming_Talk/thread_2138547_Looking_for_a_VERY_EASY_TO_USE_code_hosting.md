---
title: "Looking for a VERY EASY TO USE code hosting"
date: 2013-04-24
forum: Programming Talk
---

### Post by fedebaka on 2013-04-24
Hi! I have a little project which is for a Fortran course which the course attendants have to do in small groups (3 or 4). We are physicists and teachers with little knowledge on linux, and even little knowledge on windows (except for me). I even have trouble showing them what IDE to use and how to install it and the compiler (sometimes on windows, sometimes in linux).

So I want to recommend a code hosting platform for my group and the others to use and work in collaboration from each one's home or office. I tried github, google code and sourceforge and all require installing svn, git or mercurial, creating a directory structure which will be synchronized with the server's via push/get comands (only sourceforge let me upload files via browser), then they would have to do their own diffs and merges (?), etc., all of which will be very complicated for my mates. I also tried some cloud coding tools but they're all oriented to html, javascript, etc.

So can anyone recommend a service that would ideally have collaboration, version history, diffs, but very very simple, say, like a wiki: one has a version history which shows who added what change and when, can edit online or alternatively download a file, edit and reupload choosing to overwrite or merge with changes someone else made, a discussion page to talk about bugs and goals, etc., All to be done without installing more software? (and if it's web based it wouldn't require a specific OS, they would edit either online or with their preferred IDE or text editor).

Thanks!

---

### Post by TheFu on 2013-04-24
github is the stock standard answer, but any git-based free service is probably fine. There are a few - google is your friend.

Learning** git** is a professional skill that anyone programming needs to know.  With great power comes great responsibility.  Perhaps watching a few youtube "How-To Git" tutorials will get them over the learning curve?  There is a free **ProGIT** book on the internet too - reading 2 chapters should be enough for end users.

I've used other version control systems - SCCS, RCS, Visual SourceSafe, CVS, SVN, and git. I even used daily ZIPs of the source code.  Trust me, git is the best of all worlds.  Git has the most plugins for IDEs too.

BTW, I learned Fortran before any other language that I've used too.  Using 5 git commands isn't really that hard, is it?

---

### Post by trent.josephsen on 2013-04-24
I think you've found your own solution: a wiki. From my own experience, git is not as difficult as it is intimidating, but it sounds like you don't intend to make use of any of the features that would recommend it over a wiki -- so why bother? There are plenty of free wiki hosting services, or you could install some wiki software yourself if you have a server everyone can access.

Or just use Dropbox or Google Docs, depending on your priorities.

---

### Post by fedebaka on 2013-04-25
Well, thanks for the responses guys! You're right, trent, I'd like a more code-oriented wiki but if there aren't any this could do. Though thefu is right too, maybe an opportunity to learn to use this for maybe in the future collaborate in some other projects. I'll give the choices to the group, i guess, with the pros and cons. Thanks!

---

### Post by TheFu on 2013-04-25
> **fedebaka said:**
> Well, thanks for the responses guys! You're right, trent, I'd like a more code-oriented wiki but if there aren't any this could do. Though thefu is right too, maybe an opportunity to learn to use this for maybe in the future collaborate in some other projects. I'll give the choices to the group, i guess, with the pros and cons. Thanks!

I re-read your OP and have another idea - **Redmine**.  There are hosted services, probably for a fee. - maybe not [https://www.hostedredmine.com/](https://www.hostedredmine.com/)  I run a redmine server for my company, so we can track projects, ideas, and code. We have internal and external users - it is pretty easy to get new users understanding it. It takes a little to get redmine running, if you want to self-host.  It is a Ruby on Rails apps - with all the good and bad that entails.

Each Redmine project can have a code repo too - hooks up to git, svn or cvs, I believe.  We don't use this function - don't really want project managers or "idea guys" having access to source code.  Still, it is an option if you want a GUI front-end to git.  Real devs will use the CLI interface with their ssh creds anyway.

Running your own git server is relatively easy - just need to read 1 more chapter in ProGIT - I think it took me 10 minutes to setup a corporate Git server, then another 90 minutes to talk a few developers through their setup and use.  The entire DVCS idea was new to them - we're old guys.  OTOH, we do like to code on airplanes, so git is perfect.  Git doesn't need a GUI or web front-end, that is just a "cheese factor" for decision makers - I don't know any real coders that use it. Heck, even on github, I'm much more inclined to use CLI git commands than bother with the web interface. The web is just so, so, so slow.

---

### Post by nvteighen on 2013-04-25
I'd say GitHub, but you already discarded it... for reasons I don't really get.

Setting up a git or a bzr repository is almost trivial (especially bzr)... use the manuals you find on the internet. These are tools that are almost a must if you want to code collaboratively in a sane way.

---

