---
title: "Where do I found the source code for particular app"
date: 2012-02-26
forum: Programming Talk
---

### Post by otsoga on 2012-02-26
Is source code for the applications installed on a system usually stored in a particular directory? Do I have to go to the website of each individual application to download source code? Even though I've used several different distros over the years, I've never been able to take direct advantage of Linux's open source aspect. I'd like to be able to look at the source code of the programs installed on my system to learn more about programming. For example, right now I want to look at the source code for Deluge. I'm sorry if this has been answered before, but I just couldn't come up with search terms that yield satisfactory results and this is something I have intended to find out for years, always quitting before find an answer.

---

### Post by r-senior on 2012-02-26
It's only there if you install it or download it. It won't be anywhere by default. Look at the software sources in Synaptic or Update Manager to see how it is set up.

Once you install sources from the respository, they'll be in /usr/src, /usr/local/src, etc.

You can also usually get source code via a project's home page. They will use various methods, perhaps downloading with Git or Subversion, or letting you download some sort of archive of the source.

For example, for gcc: [http://gcc.gnu.org/svn.html](http://gcc.gnu.org/svn.html)

Links like this also help:

[http://directory.fsf.org/wiki/GNU](http://directory.fsf.org/wiki/GNU)

---

### Post by Bachstelze on 2012-02-26
If you want to "learn about programming", chances are that looking at the source code for a large program will confuse you more than anything.

---

### Post by otsoga on 2012-02-26
Thanks r-senior. You are right, Bachstelze, I need to look at simpler programs. I had attempted to do so before, but there were always issues when i tried to compile -- I think because the programs were written for a Windows/DOS environment and didn't play nice with gcc. I would like to find a site with simple programs that will compile with gcc.

---

### Post by Bachstelze on 2012-02-26
K&R has a lot of example programs that are much simpler to read and analyze.

---

### Post by s3a on 2012-02-26
Open your /etc/apt/sources.list file and copy/paste a selected line which you use to apt-get your programs (if you're not sure, do this process for every line or learn more about the sources.list file - if I see a question, I'll answer it) and add "-src" (without the quotes) after "deb" (without the quotes).

Then do:
```
sudo apt-get update;apt-get source *program_name*
```

and it will download and store the source in the current working directory.

You likely will not understand what is going on in sophisticated programs but you can still learn by focusing on a subset of the code even if you have no idea what goes on in the bigger picture.

---

