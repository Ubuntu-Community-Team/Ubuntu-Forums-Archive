---
title: "Where can I find a program to help program?"
date: 2007-01-22
forum: Programming Talk
---

### Post by thenetduck on 2007-01-22
Hi, 
    I know how to program in java, c/c++ and am learning Python and want to get started helping develop some open source software. I don't want to dive into any really big projects because this is the first time I really will be working with others programing product. 

   Does anyone know of a poject that is in need of a programming willing to learn and stick with it that isn't as big as say open office or the gnome project etc. I am doing this because I want the experience and feel that I can contribute to the open source community. ( and im a believer) Just something small that would directly help the Ubuntu community etc. Thanks, 

 The Net Duck

---

### Post by jblebrun on 2007-01-22
> **thenetduck said:**
> Hi, 
    I know how to program in java, c/c++ and am learning Python and want to get started helping develop some open source software. I don't want to dive into any really big projects because this is the first time I really will be working with others programing product. 

   Does anyone know of a poject that is in need of a programming willing to learn and stick with it that isn't as big as say open office or the gnome project etc. I am doing this because I want the experience and feel that I can contribute to the open source community. ( and im a believer) Just something small that would directly help the Ubuntu community etc. Thanks, 

 The Net Duck

The options are endless... pretty much everything in the Ubuntu repositories is open-source, and ready for you to dive in and make improvements! The best thing to do would be to try playing around with as many programs as possible, until you find one that you're really interested in, and that you can easily think of improvements or changes to make. The most important part of projects when you're learning is that you feel passionate about what you're working on!

---

### Post by runningwithscissors on 2007-01-22
The best way is to study sources of any existing software you'd like to improve, edit the code with your improvements and submit a patch to the relevant maintainer/developer for consideration.
Remember to submit your contributions to the party that packaged the source for you, i.e. if you are editing sources supplied by let's say, Debian, then submit the patch to the Debian maintainer for that package (consider the IceWeasel example for this. It wouldn't make sense to submit a patch to Mozilla for improvements made to Debain's version of their browser).
If you are using sources supplied by the developer, then send your contributions directly to him/her.

---

### Post by thenetduck on 2007-01-22
wow thanks that was really modivating. So I can just pick any application and go for it I guess. Does ubuntu have an offical "Back Up" program? I feel like somthing like that should be installed by default and mad very simple and easy for somone to backup and restore things. 

 The Net Duck

---

### Post by jblebrun on 2007-01-22
> **thenetduck said:**
> wow thanks that was really modivating. So I can just pick any application and go for it I guess. Does ubuntu have an offical "Back Up" program? I feel like somthing like that should be installed by default and mad very simple and easy for somone to backup and restore things. 

 The Net Duck

I did a search in synaptic for "backup" and it looks like "backuppc" and "rdiff-backup" are the simplest backup programs that I can see that is ubuntu-supported. There are tons of others in multiverse and universe, though. 

You can get the source code using

apt-get source <packagename>

It will put a tarball of the source in whatever directory you execute the command in.

---

### Post by 3rdalbum on 2007-01-22
The last time I checked, Ubiquity had some bugs. It's written in Python... so get to it! :-)

If you can't replicate those bugs, I think a music player would be a good project to get involved with - Exaile, Listen, Quod Libet, or one of those others would probably appreciate some new features.

---

### Post by pmasiar on 2007-01-22
> **thenetduck said:**
> I know how to program in java, c/c++ and am learning Python and want to get started helping develop some open source software. I don't want to dive into any really big projects because this is the first time I really will be working with others programing product. 

   Does anyone know of a poject that is in need of a programming willing to learn and stick with it that isn't as big as say open office or the gnome project etc. I am doing this because I want the experience and feel that I can contribute to the open source community. ( and im a believer) Just something small that would directly help the Ubuntu community etc.

My advice: find something *you* care about, regardless of it size. Find something you may use often and care to learn inside out.
1) Some editor you plan to use? music player? a game?
2) Try a useful tool used by many projects, like TRAC bug tracker, or MoinMoin wiki - if you learn it, chance is you will be an asset for many projects which use it.
3) Learn pygame (game making library), many ganes are with sources, and start there.
4) read [http://www.planetpython.org/](http://www.planetpython.org/) - see what other projects do, and what might interest you. You are going to invest a lot of time - it better be fun!
5) Don't be afraid of big projects - doing something useful usually takes alot of code, but code is written and you don't need to touch it if it works.
6) There is bunch or advanced tasks to program at [http://learnpydia.pbwiki.com/](http://learnpydia.pbwiki.com/)

Good luck! and let us know what is your choice

---

