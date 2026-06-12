---
title: "Permissions issue - Admin"
date: 2016-04-19
forum: New to Ubuntu
---

### Post by Ed_Bick on 2016-04-19
Hello, I am very new to Ubuntu and using version 14.  I am a software developer and plan to use it for Ruby on Rails.  I am having some issues with permissions, such as ->

>gem install sqlite3 -v '1.3.11' 
You don't have write permissions into /var/lib/gems/1.9.1 directory

> groupadd -f gems
Permission denied

I am an admin. 

When I use the gui to go to the folder and and set the permissions, it tells me I am not the owner of the folder so I can't set the permissions.

????????

Thanks,

Ed

---

### Post by TheFu on 2016-04-19
Welcome to the forums.  We were all new at some point.  Nothing wrong with that. ;)

As a developer, you need to have a strong understanding of multi-user OSes, file and directory permissions to prevent making your apps easily hacked.  Sadly, there isn't a shortcut to this learning, so you really need to start from the beginning and FORGET what you think you've learned in Windows.   User ids are not "administrative" like in Windows.  Some userids may be in groups which allow them escalate their permissions temporarily to a different userid or different group.  Those groups are NOT hard coded and can be anything you like, but normally they have  "wheel" or "sudo" as the group name.  This is probably confusing, no matter.  It will become clearer, over time, with practice.

We all started with limited Unix understanding. That will be solved with experience.. My best advice is to start here: [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) read the first few links. They are short.  The 4th or 5th link is a free PDF book ( that can also be purchased at most book stores) which will teach all about file and directory permissions and get you thinking multi-user.  It is a paradigm shift in thought and takes some time to acquire.  The book teaches basic Unix/Linux skills that every developer on the platform needs.

Forget using the GUI to manage permissions.  The server you deploy any RoR app onto will not have a GUI. Get used to the shell and practice inside it.

Then, your RoR instructor should have been clear that you never want to use the OS installed version of ruby or rails.  You want to own the complete environment and not be tied to the versions installed through any OS package management tool (apt-get).  Most Rubists do this using rvm or rbenv.  Doing this will solve the permissions issue, since everything related to RoR will be run from an environment that your userid (or a "deploy" userid would be better) owns.  Multi-user. Always remember that.

Perl and Python devs do something similar.  Never trust the system versions of their scripting languages. The version of these tools installed on the system through a package manager have different primary goals than someone using RoR for webapp development.  Webapp devs have different needs.

If you just want to understand permissions and ignore the other stuff I've suggested, that is a valid choice. It is a good place to start.  [http://www.penguintutor.com/linux/file-permissions-reference](http://www.penguintutor.com/linux/file-permissions-reference) is a nice primer.  There are some commonly used and subtle permissions they don't cover.  Ubuntu has this: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) guide for a different viewpoint.  Play around with a few userids, groups.  Try making directories, files, changing the owners, groups, and play with all the different permission bits to really see what happens.  There will be a few ah-ha moments.  The setgroupid bits are fun and useful on directories. What does allowing execute permissions, but not read do for a directory?  How do you prevent 1 group having access to a directory, but allow everyone else read access?  There are times when this is useful.

Hope this helps!  And before you publish any RoR app, please review and check the OWASP Top 10 list for common Ruby mistakes. [https://www.owasp.org/index.php/Ruby_on_Rails_Cheatsheet](https://www.owasp.org/index.php/Ruby_on_Rails_Cheatsheet)

---

### Post by grahammechanical on 2016-04-19
This situation will happen to anyone. Even those not wanting to use Ruby On Rails.

When we install Ubuntu we set a username & password and we are set up as administrator. But, and it is a big but in Ubuntu, we normally work as a standard user until we try to do a task that only an administrator can perform. Then we are asked to authenticate the action. That is when our password is accepted as administrator. and once the task is completed we revert to working as a standard user again.

This applies also when we are running commands in a terminal. There are many commands that we can run as a standard user but for those commands that only an administrator can run we prefix the command with the term sudo. 

We are the owners of any folders and documents we create in our home folder. But system directories/folders & files are not owned by us. They are owned by the OS or root, as they say in Linux. The sudo prefix can give us the authority to write to these folders. To give an example:

```
sudo apt-get install <package>
```

Our password will then give the apt-get command authority to write to system folders during the installation process.

Regards

---

### Post by TheFu on 2016-04-19
There is an issue running **sudo gem install** .... it builds bad, unneeded, habits for a RoR developer. For general system administration, it is necessary and a best practice.  

For RoR development, setup rbenv or rvm first, then run the gem installer/upgrader inside that specific environment. Gems can be a pain to manage dependencies. Having a special, different, environment for each webapp is a way to ensure that different webapps with different dependency issues don't conflict.  BTW, **bundler**, a ruby tool, is used inside these environments to maintain correct dependencies for each webapp.  It is up to the app developers to set those dependencies correctly with _just enough_ information so compatible gems can be installed and upgraded, but not so loose that incompatible gems get installed.  Make sense?

---

### Post by Ed_Bick on 2016-04-21
Thanks for the feedback and links.

---

