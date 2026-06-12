---
title: "access Wordpress test site on windows partition from Ubuntu"
date: 2014-02-10
forum: New to Ubuntu
---

### Post by andrew68 on 2014-02-10
Hello everyone. I am a new Linux user currently runnning a triple-boot Windows XP/Windows 7/Ubuntu 13.10 pc. I am an absolute beginner and have a strong desire to learn the Ubuntu way and break free from commercial operating systems. Essential to this goal is my ability to continue work on my test Wordpress site. I have set this site up on a seperate partition that is accessable from XP and Windows 7 through WampServer. The partition label is wordpress and the windows path is W:/wamp/www/testsite. In Ubuntu I am able to mount and access files on this partition through the launcher drive icons at the bottom of the sidebar. When I look at the properties of the folder in question (testsite), the location shows as /media/andrew/wordpress/wamp/www. My desire is to be able to access this test site that has been previously created in this windows partition, from Ubuntu. I have  already installed LAMP. I want to be able to swtich back and forth between Windows and Ubuntu while I am working on this test site and I think this will be a good way for me to be able to ease into Ubuntu without risking my progress on the test site. If anyone does endeavor to help me accomplish this task please remember that I am a newbie. Thank you. I really want to make the change and I think that learning about Ubuntu while working on an actually project would be the most likely way for me to stick with it.

---

### Post by Bill Tetzeli on 2014-02-10
I have no clue as what Wordpress is or how to use it, but my first instinct if you want to go back and forth between Ubuntu and Windows would be to install Virtualbox in Ubuntu, do a reinstall of Windows 7 in Virtualbox and run it from there - that way you could go back and forth between the two OS's without rebooting.  From the filepath, though, it looks like you have the testsite on a separate or networked hard drive, and I don't know if you could access it from Windows running virtualized in Ubuntu.

---

### Post by sandyd on 2014-02-10
> **andrew68 said:**
> Hello everyone. I am a new Linux user currently runnning a triple-boot Windows XP/Windows 7/Ubuntu 13.10 pc. I am an absolute beginner and have a strong desire to learn the Ubuntu way and break free from commercial operating systems. Essential to this goal is my ability to continue work on my test Wordpress site. I have set this site up on a seperate partition that is accessable from XP and Windows 7 through WampServer. The partition label is wordpress and the windows path is W:/wamp/www/testsite. In Ubuntu I am able to mount and access files on this partition through the launcher drive icons at the bottom of the sidebar. When I look at the properties of the folder in question (testsite), the location shows as /media/andrew/wordpress/wamp/www. My desire is to be able to access this test site that has been previously created in this windows partition, from Ubuntu. I have  already installed LAMP. I want to be able to swtich back and forth between Windows and Ubuntu while I am working on this test site and I think this will be a good way for me to be able to ease into Ubuntu without risking my progress on the test site. If anyone does endeavor to help me accomplish this task please remember that I am a newbie. Thank you. I really want to make the change and I think that learning about Ubuntu while working on an actually project would be the most likely way for me to stick with it.

Note that you will have to import the mysql database from the windows side before you can use wordpress.

---

### Post by andrew68 on 2014-02-11
Thanks for your reply. Well [WordPress]("http://www.wordpress.org") is a popular open source blogging tool, based on PHP5 and MySQL. I don't need to go back and forth between the two OS's without rebooting but I would like to be able to access the test site from either OS. I think there is some way to do this with a virtual host but I haven't been able to get it working yet. I would rather do this outside of Virtualbox if possible.

---

### Post by andrew68 on 2014-02-11
sandyd - Thanks for your reply. I was hoping I could avoid importing so that the existing database could be shared between the operating systems. I had the same problem getting XP and Windows 7 to share the database and essentially had to trick the operating systems to get it to work. There may have been an easier way but this is my first experience with any of this (Apache/MySQL,PHP) and I wasn't able to find anything online that solved my issue, so I improvised and it worked. I was hoping I could do the same with Linux but of course it was easy with two windows operating systems. My lack of knowledge about Linux makes this much more difficult and maybe my thinking that I should be able to do this is just wishful thinking, but I'm not giving up yet. It sure would be nice if I could access the same database from all three operating systems.

---

