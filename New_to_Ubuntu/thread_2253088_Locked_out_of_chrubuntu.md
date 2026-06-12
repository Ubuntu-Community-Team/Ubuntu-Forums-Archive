---
title: "Locked out of chrubuntu"
date: 2014-11-17
forum: New to Ubuntu
---

### Post by chavi2 on 2014-11-17
Hi,

I'm new to Linux and Ubuntu. I've been using a Chromebook (Samsung ARM) and running Chrubuntu, switching back and forth between Chrome OS and xfce. 
And.. I just locked myself out. 
I was changing permissions on the linux side, using 'sudo chmod 600' and then I kept getting 'access denied' unless I used 'sudo' first.
I logged out of linux, and now, when I try the 'sudo startxfce4' from the Chrome OS terminal, I get this:

[FONT=Courier New]Entering user/local/chroots/precise...
No directory, loggin in with HOME=/
mkdir: cannot create directory '//.pulse/': Permission denied
ln: failed to create symbolic link '//.pulse/default.pa': No such file or directory
/usr/bin/startxfce4: Starting X server
[/FONT]
It keeps doing different things and then getting 'Permission denied', until it just exits chroot and gives up.
What do I do?

If my question isn't clear please let me know how I can make it clearer. This is my first question ever. Forgive my greenhorn-ness.

---

### Post by ajgreeny on 2014-11-17
Changing permissions of what to 600 on the linux side, as you put it? Which folders/files did you change, as it may be almost impossible now to get back to where you were, depending on what you changed.

If it was all in your home, you should be able to run another chmod and get back to the default 755, but having used sudo chmod all those files will now be owned by root and you will also need to change ownership back to you with a **chown** command.

If the files/folders you acted on were owned by root you are going to be in even bigger trouble as there is no standard permissions for them, with many of them having different permissions to each other.

---

