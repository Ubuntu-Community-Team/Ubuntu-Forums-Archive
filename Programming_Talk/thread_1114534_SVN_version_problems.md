---
title: "SVN version problems"
date: 2009-04-02
forum: Programming Talk
---

### Post by kerryhall on 2009-04-02
I made an SVN server, and have been happily using it for a few months now. However I have only imported one project.

Now, I have imported a second project, and it says "commited version X" when I import, where X is the latest version of my first project + 1.

Commands that I used:

svn import svn_test_01/ svn://127.0.0.1/svnrepos/svn_test_01/trunk
svn import svn_test_01/ svn://127.0.0.1/svnrepos/svn_test_02/trunk

Can you only use one project per repo?

---

### Post by lloyd_b on 2009-04-02
> **kerryhall said:**
> I made an SVN server, and have been happily using it for a few months now. However I have only imported one project.

Now, I have imported a second project, and it says "commited version X" when I import, where X is the latest version of my first project + 1.

Commands that I used:

svn import svn_test_01/ svn://127.0.0.1/svnrepos/svn_test_01/trunk
svn import svn_test_01/ svn://127.0.0.1/svnrepos/svn_test_02/trunk

Can you only use one project per repo?
SVN does support multiple repos on the same server (with independent revision control), but this must be set up on the server.  Here's a link to some instructions on how to do this:[ One svnserve, multiple repositories]("http://wordaligned.org/articles/one-svnserve-multiple-repositories")

Lloyd B.

---

### Post by kerryhall on 2009-04-03
Is the norm one repo per project?

---

### Post by lloyd_b on 2009-04-03
> **kerryhall said:**
> Is the norm one repo per project?
That's entirely up to the people running the repo.  I've seen projects that had several semi-related projects using a single repo, and others that split up separate parts of a single project into multiple repos so that versioning on each part was independent.

Personally, I prefer the single repo per project concept, since then using "svn log" will show you everything that's happened on the project.  But, that's just a personal preference.

Lloyd B.

---

### Post by DougB1958 on 2009-04-03
> **kerryhall said:**
> Now, I have imported a second project, and it says "commited version X" when I import, where X is the latest version of my first project + 1.

This is how Subversion is supposed to behave -- version numbers effectively just count how many commits have been made to the repository. They have no meaning in terms of logical versions of your project. The Subversion party line is that there are other mechanisms (namely tags) for tracking logical project versions. I won't tell you that you must or mustn't buy into this party line, though if you don't you'll probably be more comfortable in the long run with a different version control system.

Personally, I have been using Subversion for a number of years in a setting where a number of small projects share a repository. Sure, version numbers seem to increment unpredictably as I make commits to my projects, but since I accept the idea that those numbers mean next to nothing anyhow, that's not a problem. (The fact that I came to Subversion without other version control models where version numbers are meaningful already embedded in my mind no doubt helped immensely.)

---

### Post by kerryhall on 2009-04-23
Thanks to everyone! This makes a lot of sense now. Basically, I need to set up a separate repo per project, at least, if I want the version numbers to make sense!

Time to set this up.

Cheers!

---

