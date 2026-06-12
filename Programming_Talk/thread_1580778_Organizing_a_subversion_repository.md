---
title: "Organizing a subversion repository"
date: 2010-09-23
forum: Programming Talk
---

### Post by ownaginatious on 2010-09-23
Hello everyone,

So recently I created a subversion repository on my computer, which I can access through the web with a password over https.

The reason I created this repository was so that I could keep track of a few personal programming projects I'm working on, and so that I could start a new project for a group programming project for school.

Anyway, I'm a little confused as how one 'locks-down' parts of the repository.

Right now, everything in the repository is owned by 'www-data'. I would like to create a folder in the repository called 'personal' which contains my project. I would like it so that to get to the projects in that folder, you would need a specific username and password (my credentials for example).

I would also like to create a 'team' folder with projects I'm working on with others (protected by a different passwords per project perhaps).

So far, I have kind of have no idea how I would go about doing this. Does what I'm saying make sense? Any help would be greatly appreciated.

Thanks!

P.S. I decided to post this in the programming forum rather than the 'repository' one since that forum is more directed to ubuntu/debian repositories.. and cause it's pretty dead. :p

---

### Post by movieman on 2010-09-24
I don't know how to do it over the web, but if you install svnserve you can restrict access to different parts of the repository to specific users.

Alternatively you might have to give in and build different repositories for the different projects.

---

### Post by James78 on 2010-09-24
The best choice you have is to use DAV svn (DAV is an Apache module). (For multiple repositories with different access permissions per repo setup, go to the svnserve part of my post) It's how I have my repositories setup, plus some basic authorization handled through Perl handlers for Redmine.. But you can do the basic authorization using Apache too. Note that for SSL you just need to recreate an exact copy of the other one in your sites VirtualHost. Have fun... Here's a [guide]("http://www.debuntu.org/2006/05/20/54-how-to-subversion-svn-with-apache2-and-dav") for ya.

P.S. If it makes it easier for you, you can use [svnserve]("http://svnbook.red-bean.com/en/1.0/ch06s03.html") instead, which will use the credentials listed in repo/conf authz and passwd. When using svnserve, all URL's are handled through svn:// instead. By default, svnserve requires a full path, so if your repository is in /home/svn/repo, you need to do svn://site.com/home/svn/repo, however you can use the -r (relocate) flag, which will allow you to do the normal svn://site.com/repo

Just keep reading, googling, looking at program flags, reading tutorials, permissions, etc. You'll get it eventually! Also, the [subversion book]("http://svnbook.red-bean.com/nightly/en/index.html") is an inexhaustible supply of information.

It took me a lot of time to get the setup perfect. But I have everything just great. My own webserver for my site, where SVN is integrated into Redmine, perfect svn repository permissions, configurable per repository user access, even some subversion hooks I wrote in Ruby. It's definitely worthit.

---

### Post by r-senior on 2010-09-24
> **James78 said:**
> It's definitely worth it.
I'd certainly agree with that. Version control involves a learning curve but, even for personal projects, delivers great benefits. Being comfortable with managing your own SCM repository, branching, tagging, etc. is great experience for larger projects.

---

### Post by fct on 2010-09-24
See example 6.2 here:

[http://svnbook.red-bean.com/en/1.0/ch06s04.html](http://svnbook.red-bean.com/en/1.0/ch06s04.html)

I started with that config in my company before switching to LDAP user authentication plus the authz permission file for SVN directories.

Works wonderfully.

---

