---
title: "newbie question about using git"
date: 2016-02-08
forum: Programming Talk
---

### Post by Drone4four on 2016-02-08
One reason to use git is to track changes and have each of the changes documented well.  So when using git, generally speaking, it’s a good idea to make 12 individual commits, one for each of the 12 individuals modifications made, rather than making 12 modifications scattered around a file tree and committing them in a single, bulk commit.  So for every minor change I make to my source, I should be committing them one by one as I go. amirite?  

Right now I am playing with some basic html and css source files.

---

### Post by Dimarchi on 2016-02-10
Here's one link that should provide further food for thought:

[sethrobertson.github.io/GitBestPractices]("http://sethrobertson.github.io/GitBestPractices/")

As it says on the page, there is no one true answer to this. It will vary according to the situation. This is true of all versioning systems, or other approaches that imitate versioning. You should be able to find your own way adjusted to the way you work with the help of this.

---

### Post by faissaloo on 2016-02-12
I suggest doing it by subject. If you're fixing one bug, do one commit for that one bug unless it's something you're going back to from earlier. If you're adding one feature, do one commit for that feature, unless of course you're fixing something that you didn't catch before your first commit relating to that feature.

---

### Post by Drone4four on 2016-02-16
Thank-you **faissaloo** and **Dimarchi**,  You've answered my question.

---

