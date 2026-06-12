---
title: "apt-get - list of software?"
date: 2005-03-02
forum: Repositories &amp; Backports
---

### Post by welly on 2005-03-02
Hi all,

Question regarding apt-get. I understand it's the command line alternative to Synaptic, and I've noticed that people have recommended its use. However! Should I want XYZ application downloaded and installed, how would I know what name to use with apt-get? Is there an apt-get --list or something similar? Is there a page anywhere which lists all the software available using apt-get? I wanted to get hold of mplayer which a few people have recommended so tried apt-get install mplayer. Didn't work unfortunately. Basically how do I know the name of the package to use with apt-get for any application, not necessarily mplayer?

Cheers!

Welly

---

### Post by Ryujin on 2005-03-02
It may not come stock with ubuntu, but you can run aptitude on the command line for a complete list of the tree

---

### Post by mike998 on 2005-03-02
apt-cache search <*program name*>
That will usually give you a list of programs with that word in the title.

---

### Post by rosslaird on 2005-03-02
You can search for packages on the web by going here:

[http://higgs.djpig.de/ubuntu/www/](http://higgs.djpig.de/ubuntu/www/)

You can enable the mplayer sources in /etc/apt/sources.list by adding this:

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

Ross

---

### Post by Ryujin on 2005-03-02
Won't mixing repositories like that break stuff?

---

### Post by rosslaird on 2005-03-02
Not usually (*usually*).

Nerim has mostly mplayer-related stuff, so it's pretty safe. If you were to add the debian unstable sources, on the other hand, that might break stuff. One way to be safe (safer) is to use the apt-get command line, which will typically show if there are going to be problems. So, after adding the nerim sources for mplayer, you could run:

sudo apt-get update
sudo apt-get install mplayer

It might ask you to choose between versions. Choose the version you want and run the install command again. Look for anything that might be removed or replaced or upgraded. There might be new stuff since your last Ubuntu upgrade, and if you're worried about that just disable all sources except nerim for this procedure (put a # at the beginning of the line of each source, and it will be skipped). That way, apt will only see the mplayer sources and you will get a very nice and small snapshot of what's being done.  After mplayer is installed, re-enable the ubuntu sources and upgrade again. You can also use so-called "apt-pinning" to make sure that apt will never install anything over your ubuntu versions (billions of posts about how to do this are on the web).

I don't typically use pinning; I just watch my upgrades carefully while they're being done by apt. Besides, if something breaks you can almost always fix it. That said, in three years (in Debian and Ubuntu) I've never had any serious breakage issues. If something comes online that will break something else, it's usually fixed quickly, or there is a workaround made available (there was a situation with kde audio libraries a while back, and it was fixed the same day).

---

### Post by heymattay on 2012-03-04
Despite the age of this thread, it helped point me in the right direction to find a list of every package available for downloading via

[INDENT][FONT="Courier New"]sudo apt-get[/FONT]
[/INDENT]
Here's the link I found which I believe to be the source of the packages

[INDENT][FONT="Courier New"][http://archive.ubuntu.com/ubuntu/pool/main/](http://archive.ubuntu.com/ubuntu/pool/main/)[/FONT][/INDENT]

If you back up to /pool/ you'll find four directories, each one storing very similar info. I felt /main/ was self explanatory for being the source of most, if not all [FONT="Courier New"]sudo apt-get[/FONT] packages. 

=============================================

Now that the reason for posting is taken care of, I shall tell you the story of a mere accident once again changing the course of history.

I was initially interested in what else I could download after discovering the simplicity of retrieving Apache Ant via [FONT="Courier New"]sudo apt-get[/FONT]. Naturally, I typed

[INDENT][FONT="Courier New"]sudo apt-get help[/FONT]
[/INDENT]
There, I found this list of commands:

[INDENT][FONT="Courier New"]   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove packages and config files
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies
   changelog - Download and display the changelog for the given package
   download - Download the binary package into the current directory[/FONT][/INDENT]

I chose

[INDENT][FONT="Courier New"]sudo apt-get upgrade[/FONT]
[/INDENT]
Whereas I meant to choose

[INDENT][FONT="Courier New"]sudo apt-get update[/FONT]
[/INDENT]
This mistake lead me to upgrading my entire system. While the process ran, my cursor landed on links so I copied one at random, 

[INDENT][FONT="Courier New"]http://http://archive.ubuntu.com/ubuntu/[/FONT]
[/INDENT]
After browsing through a few folders, I ran into /main/ and changed my life.

The End

---

### Post by nothingspecial on 2012-03-04
Thanks for the info.

But please don't bump ancient threads to the top.

Closed.

---

