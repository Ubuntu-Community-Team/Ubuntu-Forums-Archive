---
title: "HOWTO Install Museekd and Mucous for Soulseek"
date: 2005-12-27
forum: Outdated Tutorials &amp; Tips
---

### Post by sciurus on 2005-12-27
This is a guide to installing [Museekd]("http://museek.thegraveyard.org/") and [Mucous]("http://thegraveyard.org/daelstorm/"). Museekd is a daemon that connects the the Soulseek filesharing network. Mucous is an ncurses-based frontend to Museekd. The installation of Museeq, a QT frontend for Museekd, is not covered by this guide. If you want a GUI for accessing Soulseek, I suggest installing Nicotine from the repositories.

First we need to install the prerequisites for compiling Museekd.

1) sudo apt-get install build-essential subversion swig libxml++2.6-dev libvorbis-dev python2.4-dev

Let's switch to your home folder.

2) cd ~

The latest release of museekd is very old, so we'll download a development copy through subversion. The username to access it is 'guest', and the password is blank.

2) svn checkout [http://svn.thegraveyard.org:8080/repos/museek/trunk](http://svn.thegraveyard.org:8080/repos/museek/trunk) museek

The subversion copy doesn't include the scons build system, so we have to download the release version as well.

3) wget [http://museek.thegraveyard.org/museek-0.0.040714-2.tar.bz2](http://museek.thegraveyard.org/museek-0.0.040714-2.tar.bz2)

Now let's extract it, 

4) tar -jxvf museek-0.0.040714-2.tar.bz2

Move the scons folder,

5) mv museek-0.0.040714-2/scons museek

And delete it.

6) rm -rf museek-0.0.040714-2.tar.bz2 museek-0.0.040714-2

Now we're ready to switch to the museek folder

7) cd museek

And build it.

8) sudo python scons/scons.py RELEASE=YES MUSEEQ=NO install_museekd install_muscan install_mucipher

After compilation completes, you should have museekd and muscan in /usr/local/bin/. There should also be various museek and mucipher files in /usr/lib/python2.4/site-packages/. We can now switch back to your home directory

9) cd ..

And delete the museekd source.

10) rm -rf museek

The musetup tool doesn't seem to exist in the subversion version, so we will have to create the configuration file by hand. First make its directory, 

11) mkdir ~/.museekd

Switch to it,

12) cd ~/.museekd

Then download a skeleton configration file to it.

12) wget [http://thegraveyard.org/daelstorm/config.xml](http://thegraveyard.org/daelstorm/config.xml)

Edit the configuration and put in your own values for the clent password, interfaces.bind keys, server username and password, download directory, user info, and anything else you care about.

13) nano config.xml

Now you're ready to test museekd

14) museekd

If all went well, you will see

[Museek.SC.DBG] login 1, ** Welcome, you are now connected to the original SoulSeek Network!

and lots of messages like

[Museekal.CM.CYCLE] cycle 5
[Museekal.TT.DBG] 1 frames, total count: 8, td: 1.0, avg: 8.0
[Museekal.TT.DBG] 1 frames, total count: 268, td: 1.0, avg: 268.0
[Museekal.TT.DBG] 1 frames, total count: 8, td: 1.0, avg: 8.0
[Museekal.CM.DBG] Average upload   rate: 8
[Museekal.TT.DBG] 1 frames, total count: 268, td: 1.0, avg: 268.0
[Museekal.CM.DBG] Average download rate: 268
[Museekal.CM.DBG] changing timeout to 15000

Hit ctrl-c to stop museekd.

Now let's get ready to install mucous by switching back to our home directory,

15) cd ~

downloading the latest version,

16) wget [http://thegraveyard.org/daelstorm/scripts/mucous-0.7.0.tar.bz2](http://thegraveyard.org/daelstorm/scripts/mucous-0.7.0.tar.bz2)

extracting it,

17) tar -jxvf mucous-0.7.0.tar.bz2

and deleting the archive.

18) rm mucous-0.7.0.tar.bz2

Now switch to the directory you just extracted.

19) cd mucous

Open a second terminal and run museekd.

20) museekd

return to your original terminal and start mucous.

21) python mucous

Use the /interface and /password commands to set mucous configuration to the same values you specified in museekd's config.xml. Then use /save to save them and /connect to attempt to connect to museekd. If this doesn't work the first time you may want to /exit and restart mucous. Also, you can check ~/.mucous/config to be sure it is saving your settings properly.

You can learn more about how to use mucous by reading [Daelstorm's tips]("http://thegraveyard.org/daelstorm/mucous-tips.php") or typing /help.

If you wish to run mucous on a different system than the daemon, you will need mucipher on that system as well. Instead of downloading museekd, it is possible to install mucipher by downloading and extracting [this file]("http://thegraveyard.org/files/pymucipher-0.0.1.tar.gz") then running sudo python setup.py install. To get museekd to listen for external connections, add <key id="IPADDRESS:2240"/> to interfaces.bind in ~/.museekd/config.xml.

---

### Post by starpause on 2006-08-10
on kubuntu 6.06 when i attempt step 8

```
sudo python scons/scons.py RELEASE=YES MUSEEQ=NO install_museekd install_muscan install_mucipher 
```

i get 

```
scons: *** [Errno 2] No such file or directory: '/usr/lib/python2.4/site-packages/CORBA.py'
scons: internal stack trace:
  File "/home/starpause/museek-0.0.040714-2/scons/scons-local-0.95/SCons/Taskmaster.py", line 364, in next_task
  File "/home/starpause/museek-0.0.040714-2/scons/scons-local-0.95/SCons/Taskmaster.py", line 176, in make_ready
  File "/home/starpause/museek-0.0.040714-2/scons/scons-local-0.95/SCons/Node/Alias.py", line 70, in current
  File "/home/starpause/museek-0.0.040714-2/scons/scons-local-0.95/SCons/Sig/__init__.py", line 370, in bsig
  File "/home/starpause/museek-0.0.040714-2/scons/scons-local-0.95/SCons/Sig/__init__.py", line 370, in <lambda>
  File "/home/starpause/museek-0.0.040714-2/scons/scons-local-0.95/SCons/Node/__init__.py", line 458, in calc_signature
  File "/home/starpause/museek-0.0.040714-2/scons/scons-local-0.95/SCons/Node/__init__.py", line 483, in calc_bsig
  File "/home/starpause/museek-0.0.040714-2/scons/scons-local-0.95/SCons/Sig/__init__.py", line 370, in bsig
  File "/home/starpause/museek-0.0.040714-2/scons/scons-local-0.95/SCons/Sig/__init__.py", line 370, in <lambda>
  File "/home/starpause/museek-0.0.040714-2/scons/scons-local-0.95/SCons/Node/FS.py", line 618, in calc_signature
  File "/home/starpause/museek-0.0.040714-2/scons/scons-local-0.95/SCons/Node/__init__.py", line 464, in calc_signature
  File "/home/starpause/museek-0.0.040714-2/scons/scons-local-0.95/SCons/Node/__init__.py", line 530, in calc_csig
  File "/home/starpause/museek-0.0.040714-2/scons/scons-local-0.95/SCons/Sig/__init__.py", line 404, in csig
  File "/home/starpause/museek-0.0.040714-2/scons/scons-local-0.95/SCons/Node/FS.py", line 1357, in get_timestamp
  File "/home/starpause/museek-0.0.040714-2/scons/scons-local-0.95/SCons/Node/FS.py", line 649, in getmtime
  File "/usr/lib/python2.4/posixpath.py", line 143, in getmtime
    return os.stat(filename).st_mtime
scons: building terminated because of errors.

```

the strange thing, to me, is that the file '/usr/lib/python2.4/site-packages/CORBA.py' does exist! any ideas?

---

### Post by decode on 2006-09-25
i had to install python2.3 to make it work...

---

