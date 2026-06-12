---
title: "IDE using files over SSH?"
date: 2006-09-07
forum: Programming Talk
---

### Post by jerrylin on 2006-09-07
Hello,

I just made the switch from Windows to Linux yesterday. I'm trying to find a way to SSH to my school server (or mount the server connection as a drive) and work with the files there from a local IDE.

I am able to SSH in through console, and mount the connection in Ubuntu, however, my local IDE (was trying using Eclipse) does not reconize these files.

Is this even possible? Am I doomed to eternal FTP?

---

### Post by toojays on 2006-09-08
On the contrary. Here's a couple of ideas.

Some IDEs support SSH transparently. I know Emacs does (with Tramp mode), and I suspect that KDevelop does (since KDE has had network transparency for a long time).

Another option, which should work no matter what IDE you want to use, is to use sshfs to create an SSH mount. This is probably different to what you did when you said you mounted the connection in Ubuntu. One howto is at [http://www.ubuntuforums.org/showthread.php?t=103860](http://www.ubuntuforums.org/showthread.php?t=103860)

---

### Post by [h2o] on 2006-09-09
Places->Connect to server   choose SSH and enter your details. Then browse and open files as usual in nautilus. Works like a charm to me.

---

### Post by gmclachl on 2006-09-09
I was going to suggest the that option, however there are a few problems with that as not all files can be opened with their associated programs. For instance I am unable to open html files with Firefox. 

 I followed the link suggested and installed sshfs and it's working well.I also wrote a quick python script to mount it at boot time. 

George

---

### Post by jerrylin on 2006-09-10
I got all the commands to go through, however now, when I try to access the drive it does not work. Double clicking on it on my desktop does nothing, trying to access it within a program produces an error.

Thanks for the previous replies, I think I'm understanding (and loving) linux more.

-Jerry

---

### Post by [h2o] on 2006-09-10
I had similar problems. That I think had to do with SSH keys colliding or something. Try logging on to your ssh server with a terminal and see if you get any error messages. Resolve everything that hinders you from getting a password prompt directly, and then try "Connect to server" again. That solved it for me.

---

### Post by jerrylin on 2006-09-10
I'm able to SSH in terminal and mount the drive by going to Places -> Connect to Server.

My original problem is neither of these made the SSH folder accessable by eclipse. gedit recognizes the files locally.

The link to the walkthrough further up created a drive on my desktop, however  I can't access the ssh folder by clicking browse or trying to open through Eclipse.

Any one have another idea?

Thanks,
-Jerry

---

### Post by kreucher on 2007-11-13
Eclipse doesn't support gnome-vfs like gedit et al do.. But never fear, for SFTP support in Eclipse (basically what you're looking for), check out this plugin:

[http://www.jcraft.com/eclipse-sftp/](http://www.jcraft.com/eclipse-sftp/)

    - nick

---

