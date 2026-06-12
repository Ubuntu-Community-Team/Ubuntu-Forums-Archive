---
title: "[Tutorial] Debianize Github Projects And Upload to Ubuntu PPA"
date: 2011-09-19
forum: Packaging and Compiling Programs
---

### Post by Gias Kay on 2011-09-19
Hello all,

Due to the need of a project I am currently working on, I have to go through the horrible process of Debianizing a Github project, then putting it onto Launchpad PPA. I've documented the process in detail, including many useful tips which might save you a great lot of time tinkering around if you happen to have similar needs.

Since the guide is pretty long (spanning four parts), I'll only list out the table of contents below with their links:

**[SIZE="3"]Debianize Github Projects And Upload to Ubuntu PPA[/SIZE]**

**_[[COLOR="RoyalBlue"]Part 1[/COLOR]]("http://blog.gantrithor.com/post/10300791891/debianize-github-projects-and-upload-to-ubuntu-ppa-1")_**
[LIST]
[*]Reference
[*]Introduction
[*]Step 1: Ready Your Tools
[*]Step 2: Check Debianization History
[/LIST]

**_[[COLOR="RoyalBlue"]Part 2[/COLOR]]("http://blog.gantrithor.com/post/10350973701/debianize-github-projects-and-upload-to-ubuntu-ppa-2")_**
[LIST]
[*]Step 3: Clone the Project from Github
[*]Step 4: Branch Layout
[/LIST]

**_[[COLOR="RoyalBlue"]Part 3[/COLOR]]("http://blog.gantrithor.com/post/10355916535/debianize-github-projects-and-upload-to-ubuntu-ppa-3")_**
[LIST]
[*]Step 5: Update Packaging Information
[LIST]
[*]Step 5A: Update changelog File
[*]Step 5B: Update control File
[*]Step 5C: Update copyright File
[*]Step 5D: Update rules File
[*]Step 5E: Update patches Subdirectory
[/LIST]
[*]Step 6: Build the Package
[/LIST]

**_[[COLOR="RoyalBlue"]Part 4[/COLOR]]("http://blog.gantrithor.com/post/10403897049/debianize-github-projects-and-upload-to-ubuntu-ppa-4")_**
[LIST]
[*]Step 7: Upload to PPA
[*]Step 8: Keep Your PPA Up-to-date
[/LIST]

Hope this to be of helps to anyone who found yourself inside a similar shoe ):P

---

### Post by Gias Kay on 2011-09-19
I could also use some helps; as detailed inside [this post]("http://blog.gantrithor.com/post/10405024929/install-node-js-npm-via-apt-get-synaptic"), the upstream has removed the man pages from the source in v1.0.30:

[COLOR="DeepSkyBlue"][https://github.com/isaacs/npm/commits/v1.0.30](https://github.com/isaacs/npm/commits/v1.0.30)[/COLOR]

So if I try to build v1.0.30 with the existing *rules* file, **$ man npm** will end up giving errors. I am not sure if this means I need to generate these man pages myself, or I need to do some modifications to the existing *rules* file, or that I need to patch the source, or?

Hope someone could help me on this one, or handing some advices. Many thanks :)

---

