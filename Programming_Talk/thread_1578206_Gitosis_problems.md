---
title: "Gitosis problems"
date: 2010-09-20
forum: Programming Talk
---

### Post by hurra on 2010-09-20
I've spent the last 14 days on git and gitosis problems. I did always find a way around my problems but now I'm stuck. To briefly summarize the situation:

I have setup gitosis, created a project and I can check in and out of it. Then I added another uses, giving him access to the project by adding him to gitosis.conf, but he can not even clone project. Then I added yet another user for the same project (following same procedure), he has access to everything (clone, pull and push). Finally, I added one more user who can not do anything either.

I could live with all of this, because I have access to work on the project.

Now I have added a new project, or have I? To my best believe, I have done everything the exact same way as with the first project. 

I do not get a repository in the repository folder on my server (when doing "git remote add..." and push). I have tried following ALL the guides google gave me on "how to create a new repository gitosis" (is up to page 7 before not ALL hits are marked as visited).

I have also tried to follow a different path, starting with "git init --bare" on the server, and then try to clone it. Didn't work either.

I get the following error no matter what I try:
ERROR: gitosis.serve.main: Repository read access denied
fatal: The remote than hung up unexpectedly

(But it works fine for accessing gitosis-admin and my first project)

Then I read about debugging of gitosis. I have tried with -v, --verbose and adding LogLevel = DEBUG in gitosis.conf, none of these give me extra information.

Project setup gitosis.conf:
[group project]
writable = project
members = me
LogLevel = DEBUG

To my best believe, everything is done the exact same way, as I did when setting up my first project.

I'm really stuck, how do I proceed now?

---

