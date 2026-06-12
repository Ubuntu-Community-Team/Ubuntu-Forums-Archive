---
title: "Cannot uninstall mpd with &quot;sudo apt-get remove mpd&quot;"
date: 2014-01-10
forum: New to Ubuntu
---

### Post by winfried.moser on 2014-01-10
Hi!


I am trying to install mpd since several weeks, but didn't manage to make it work flawlessly (restart didn't work). In the process of tampering around with duplicate mpd systemfiles in different folders (some in /lib/mpd, some in /etc, some in ~/.mpd) I accidentially deleted /etc/mpd.conf AND ~/.mpdconf (yes really!), and now it seems impossible to uninstall or reinstall mpd. How can I now completely purge mpd from my system?
 
Thanks for your help.
Winfried

This is the output of "sudo apt-get remove mpd":


Removing mpd ... sed: can't read /etc/mpd.conf: No such file or directory sed: can't read /etc/mpd.conf: No such file or directory awk: cannot open /etc/mpd.conf (No such file or directory)  error processing mpd (--remove):  subprocess installed pre-removal script returned error exit status 1 sed: can't read /etc/mpd.conf: No such file or directory dpkg: error while cleaning up:  subprocess installed post-installation script returned error exit status 2 Errors were encountered while processing:  mpd

---

### Post by ian-weisser on 2014-01-10
> **winfried.moser said:**
> Removing mpd ... sed: can't read /etc/mpd.conf: No such file or directory sed: can't read /etc/mpd.conf: No such file or directory awk: cannot open /etc/mpd.conf (No such file or directory)  error processing mpd (--remove):  subprocess installed pre-removal script returned error exit status 1 sed: can't read /etc/mpd.conf: No such file or directory dpkg: error while cleaning up:  subprocess installed post-installation script returned error exit status 2 Errors were encountered while processing:  mpd

Please use [code] tags when posting output. It makes the output *much* easier to parse.

One easy way to try to fix the problem is to create a dummy file(s) for the package manager to erase.
The package manager often doesn't care about the contents of the file. It just needs a file to read or delete. An empty file works.
**$ touch /etc/mpd.conf**
**$ sudo apt-get purge mpd**  ("purge" also removes the config files in /etc)

If that doesn't work, try reinstalling mpd so you can delete it.
**$ sudo apt-get install --reinstall mpd**

Finally, let us know if those don't work. There is a nuclear option that forces dpkg to *think* it deleted the package. But it doesn't, and the detritus is left all over your system to manually clean up. Rarely needed.

---

### Post by winfried.moser on 2014-01-11
i created also ~/.mpdconf, as i before had also this one, and tried the dummy-suggestion, the answer of apt-get is ...

[code]
Removing mpd ... 
 * /etc/mpd.conf must have pid_file set; cannot stop daemon. 
invoke-rc.d: initscript mpd, action "stop" failed. 
dpkg: error processing mpd (--purge): 
 subprocess installed pre-removal script returned error exit status 1 
action: abort-remove not supported 
Errors were encountered while processing: 
 mpd 
[code]

Then I found an old version of my mpd.conf in forum.musicpd.org and transferred it to my two empty mpd config-files
Obviously the uninstall procedure needed the line

[code]
pid_file "~/.mpd/pid"
[code]

Thanks for your help!!

---

### Post by squakie on 2014-01-11
It sounds as if it thinks the daemon is either running or it expects it to be running.  However, I would try following [ 						 					]("http://ubuntuforums.org/member.php?u=1841707") 				 				 					 						 	[**[COLOR=#000000]ian-weisser[/COLOR]**]("http://ubuntuforums.org/member.php?u=1841707")'s complete post - try the reinstall.

If that doesn't work, then I would start by:

ps -e | grep mpd and see it it shows any process running with "mpd".  If so, I'd kill those processes:

sudo kill -kill <process id or list of process ids here>

I think I would next try:

sudo apt-get purge mpd


Aslo, instead of trying this all from the command line, try the following:

sudo apt-get install synaptic

when that has finished go to the menus and select synaptic package manager, then enter mpd in the search string.  Try flagging any of the mpd packages you recognize for removal and then click apply.  This is just a graphical front-end to apt, but makes some things easier to work with.

---

### Post by winfried.moser on 2014-01-11
Thanks for your hints! I did follow ian-weissers complete post several times.
Nonetheless I solved my problem 1 minute ago by inserting ...

[/code]
pid_file "~/.mpd/pid"
[/code]

to my config-file. now the uninstall process worked
Thanks for your help, I will need your hints anyway as I dont expect to get it right now ...

---

### Post by squakie on 2014-01-11
Well, this IS interesting.  I just installed mpd so I could try to duplicate your problem, and I did.  I have also succeeded in duplicating the "can't get rid of the dang thing" problem.  Trying to reinstall fails, trying remove or purge fails, trying to purge via synaptic package manager fails.  Initially I did have a daemon running that got started by the install process - I killed it before I started the rest of try to remove - don't know if that messed things up more or not.  Going to check to see if I can find the removal script it apparently runs for mpd to terminate things and then go on to the remove.  Right now I don't have a solution.

---

### Post by squakie on 2014-01-11
Didn't see your success post until now - sorry about that.  I also had success in removing in a different way:

- I found the .deb file by using the file manager and searching for mpd
- I right-clicked and selected open with and selected archive manager
- I then found the mpd.conf there, extracted it only to my home folder
- via terminal and sudo, copied mpd.conf from my home folder to /etc
- ran sudo apt-get remove mpd again and it worked

Just another way to do it, but yours seems much shorter and quicker!  Good job!

---

### Post by winfried.moser on 2014-01-11
thanks. one of my first linux-successes :-)

---

