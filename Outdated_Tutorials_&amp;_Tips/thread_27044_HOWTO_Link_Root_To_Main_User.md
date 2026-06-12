---
title: "HOWTO: Link Root To Main User"
date: 2005-04-14
forum: Outdated Tutorials &amp; Tips
---

### Post by XDevHald on 2005-04-14
This tutorial is from a great site I use all the time, and this has been tested by me and is VERY safe if you follow the directions carefully!

[b]Please note that this is a do at your own risk!

Extra Note: [/b]Doing this does not give you access to doing apt-get, it just gives you FULL access to all roots workings and files.
[b] 
----------------------------------------------------------------------------------------------------

[/b] This is a simple guide to linking root's home directory to that of your main user, which I will call bob for the purposes of this guide. Note that this is just a luxury for a single user who periodically runs programs as root, and that you wouldn't want to do this on any mission critical machines. First, back up any important data currently in /root. Then, as root: 

  rm -rf /root
ln -sf /home/bob /root
cd /etc/cron.hourly
echo "chown -R bob:users /home/bob" >> chown_bob
chmod 555 chown_bob
cd -
[b]----------------------------------------------------------------------------------------------------

[/b] Now root and bob share the same home directory. But when you're logged in as bob you don't have root's privileges, so everything is still reasonably secure. Note that you could also edit /etc/passwd and change /root to /home/bob if you like, but I think the symlink is clearer. 

 Now you don't have to worry about maintaining seperate copies of config files, such as: 

  


[list]
[*]~/.bash_login
[*]~/.bashrc
[*]~/.ssh/known_hosts
[*]~/.vimrc
[/list]etc... 

 The reason the chown command goes in cron.hourly (which causes it to execute every hour on the hour) is so that files created in the home directory belonging to root will soon become owned by bob, so that bob can make use of them, too. And since root has full access to anyone's files (including bob), there's no need for root to own things himself. 

 Should the need arise you can also run the command manually, like so: 

  # /etc/cron.hourly/chown_bob
 ...but you'll rarely have any need to do this, and it's certainly much less hassle than maintaining seperate copies of files in /root and /home/bob, or even linking individual files. 

 A better way to do the chown-ing is to add the following lines to bob's /home/bob/.bash_logout : 

  if [ `/usr/bin/whoami` = 'root' ]
then
        /bin/chown -R bob:users /home/bob
fi
 That way, every time the root logs out, he will change the ownership of the files in /home/bob back to bob.



 **All credits goto gentoo.wiki.com**

---

