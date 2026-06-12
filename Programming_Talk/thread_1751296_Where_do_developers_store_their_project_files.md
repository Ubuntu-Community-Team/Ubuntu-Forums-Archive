---
title: "Where do developers store their project files?"
date: 2011-05-06
forum: Programming Talk
---

### Post by crunchytheory on 2011-05-06
I'm relatively new to Linux and have recently taken a job as a kernel hacker. Tall order, yes, so I've got some learnin' to do!

One thing I'm struggling with is where to keep all my "stuff". I'm the kind of person that needs to be completely organized and have a special place for everything.

I've got project files, miscellaneous useful shell scripts (like removing spaces from filenames), project documentation, test applications for project development, etc. All the usual stuff a software developer would have. So my question is, where do other developers usually keep everything?

A fresh install of Ubuntu already has a directory for Music, Pictures, etc. but of course it doesn't have a directory structure set up for developers as everyone has different needs.

If this has been discussed before, please give me a link. But honestly, I had no idea what keywords to search for.

Thanks!

---

### Post by r-senior on 2011-05-06
Traditionally, personal shell scripts go in your ~/bin directory which you add to your path. Personal code libraries (for C at least) go in ~/lib and header files in ~/include. In other words, mirroring the filesystem hierarchy standard.

[http://en.wikipedia.org/wiki/Filesystem_hierarchy_standard](http://en.wikipedia.org/wiki/Filesystem_hierarchy_standard)

You could follow on that theme, depends a lot on what you are developing. For me that's as far as I take it. 

All my development projects go under ~/Development, sub-divided by language and then project. Documentation tends to go in my ~/Dropbox folder because I sometimes need to access it from a web browser if I am working away, or it might go in ~/Documents. Any local software (e.g. web application servers) I put under ~/Software. Java libraries go into a Maven repository on my server, Java code goes into a Subversion repository and gets rebuilt automatically with Hudson.

If you are doing kernel work, you'll become familiar with git which takes a lot of legwork out of managing multiple versions of source code. You can just have one kernel directory tree and switch branches. 

Filing on your own machine is a personal thing and changes over time. No need to worry too much about it. Just try and recognise when it's getting out of hand and needs reorganising - that also applies to the filing of email, bookmarks, etc.

---

### Post by crunchytheory on 2011-05-06
Thank you for the great response! I had my doubts if anyone would actually understand what I was asking, but you answered it perfectly.

Yes, I've been using git for kernel development and was trying to figure out where to keep the clones for different kernel versions. ~/Development sounds like a good place to keep them separate from the rest of the system files.

---

### Post by slavik on 2011-05-06
for my own code/project, I usually create a code dir and then seprate things by languages. also, use git :D

---

### Post by simeon87 on 2011-05-07
I just put everything I need for the project under ~/projects/projectname/ 

I do reuse Java libraries and similar because you can simply configure where they are located using the CLASSPATH.

---

