---
title: "Subversion and Netbeans"
date: 2006-06-04
forum: Programming Talk
---

### Post by ghetto on 2006-06-04
Hi,
I'm just starting with a new toy to enhance my coding experience.

I've installed and configured subversion to run as server, and I would use it to manage my Netbeans projects. The repo is up, netbeans have it's plugin. Now I have no idea on how to use all this stuff...

First, netbeans ask me for the svn server, but what url have I to tell him??? I would like to access this server from the office too, which should be straightforward using svn protocol, or not?

Also I read somewhere that svn is supported by monodevelop too, is it true? How can I enable this?

And the last, is there a simple "start guide" for svn, like a tutorial that show how to create a project and use it? Just the basic to start...

I know, I'm a bit lazy but looking through the doc on svn site will take me too much time... if somoeone have experience with it can maybe save me some hours of headache...

Thank you in advance

---

### Post by yaaarrrgg on 2006-06-06
First, try to get svn to work on the command line (without netbeans).  SVN is very similar to cvs in terms of commands.  For example:

```

        TO CHECK OUT FILES FROM SOURCE CONOTROL
            svn co svn://YOURSERVER/PATH/TO/REPOSITORY   LOCAL_COPY
            this will create a new local folder, which you can cd to.

        TO UPDATE LOCAL COPIES OF FILES FROM SOURCE CONOTROL
            svn up

        TO SUBMIT (OR CHECK IN) CHANGES TO SOURCE CONOTROL
            svn ci

        TO ADD A COMPLETELY NEW PROJECT TO SOURCE CONTROL
            cd to INSIDE the folder you want to import
            svn import svn://YOURSERVER/PATH/TO/REPOSITORY/YOUR_PROJECT

        SHORTCUTS:

                svn co                  download copy of repository
                svn up                  bring your copy up to dat)
                svn ci                   check in...or commit
                svn add .              add files in ., will be added on next ci
                svn rm file.txt        removes file file.txt
                svn ls -R               recursively list files in repository
                svn revert -R         recursively revert local copy
                svn log                 show revision log

```

Although, if you don't know the url, then perhaps you haven't set this up?  For instance, you probably would use xinetd.d to configure this.

---

### Post by mlind on 2006-06-07
I dunno about NetBeans, but Eclipse has very good and working plugin called
Subclipse for subversion version control tasks.

---

