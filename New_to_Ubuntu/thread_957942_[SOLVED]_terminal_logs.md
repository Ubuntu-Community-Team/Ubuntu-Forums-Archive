---
title: "[SOLVED] terminal logs?"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by dizzy1kenobi on 2008-10-24
Is there a place where terminal logs and error reports are kept?

---

### Post by bpowell2005 on 2008-10-24
> **dizzy1kenobi said:**
> Is there a place where terminal logs and error reports are kept?

Yes, in /var/log you'll find all kinds of log files.

The main ones I look at (when hunting down problems) are messages, dmesg, kern, and maybe boot.

---

### Post by ciscosurfer on 2008-10-24
> **dizzy1kenobi said:**
> Is there a place where terminal logs and error reports are kept?You may also like to try using Ubuntu's GUI app called System Log.

Found here: System > Administration > System Log

In it you will see various other logs that you can easily traverse (auth.log, daemon.log, debug, etc.)

Using the Filter function is quite useful (View > Filter).  If you're into key combos, you can enter in a filtered term by pressing Ctrl+F

---

### Post by dizzy1kenobi on 2008-10-24
> **bpowell2005 said:**
> Yes, in /var/log you'll find all kinds of log files.

The main ones I look at (when hunting down problems) are messages, dmesg, kern, and maybe boot.

I can't seem to find it.

---

### Post by bpowell2005 on 2008-10-24
> **dizzy1kenobi said:**
> I can't seem to find it.

Hmm, that's odd.

Open a terminal window, and type "cd /var/log" This should put you smack-dab in the middle of the Ubuntu logs!

That being said, I really like ciscosurfer's suggestion of accessing the logs via a gui as well...they're easy to read that way as well. I just go to the terminal because it sometimes seems faster to me.

---

### Post by dizzy1kenobi on 2008-10-24
Thanks, I found the logs but I can't seem to find the error logs I was looking for.  There is a lot there.

---

### Post by ciscosurfer on 2008-10-24
What type of error are you specifically looking for.  In other words, what activity were you doing that made you want to look at the logs?  This will help us in determining which log file you wish to view.

---

### Post by dizzy1kenobi on 2008-10-24
I was on this blog [http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074](http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074).

I followed the directions but after and after I went through the install and entered "ccsm" I came up with some things I didn't understand if I did the command again would it give the same error?  Is it possible there is something I need to uninstall?

---

### Post by bpowell2005 on 2008-10-24
> **dizzy1kenobi said:**
> I was on this blog [http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074](http://forlong.blogage.de/entries/2008/4/26/How-to-set-up-Compiz-Fusion-074).

I followed the directions but after and after I went through the install and entered "ccsm" I came up with some things I didn't understand if I did the command again would it give the same error?  Is it possible there is something I need to uninstall?

It shouldn't hurt to enter the command "ccsm" again...that's a command to run the Compiz configuration & settings manager...which you can also access by going to System, Preferences, Advanced Desktop Effects Settings.

Run it again (in terminal) and tell us what the error is.

Like Cisco said, the location of the error will depend on what type of application you're trying to run.

---

### Post by dizzy1kenobi on 2008-10-24
The "ccsm" opens the settings but the error came after the initial download.  I can't get the cube to work properly what would happen if I download again?

---

### Post by ciscosurfer on 2008-10-24
dizzy, I hate to be debbie-downer here, but setting up Compiz Fusion can be tricky business, to be sure.  There are a number of variables associated with enabling certain plugins, enabling the proper video driver, which video card you have, which version of Ubuntu you are running, etc., etc.  I would suggest taking a peak at [this community help link]("https://help.ubuntu.com/community/LinuxLogFiles") for more information on specific log files that you might find useful in this endeavor.  Directions to setup Compiz Fusion are beyond the scope of this thread though.  A quick search on these forums should give you an idea of what you may be up against (which isn't to say it's necessarily hard to setup, but again, there are simply too many things that could be happening to name and reiterate in this thread).  

Good Luck! And I hope you find the community help link useful :-)

---

### Post by dizzy1kenobi on 2008-10-24
Tell me which file holds the commands that I entered and which hold the messages.

---

### Post by ciscosurfer on 2008-10-24
You can enter the command```
history
```in a terminal to see what you've entered, or ```
history | less
```and step through the file with your Enter key or your Spacebar, or simply tap the up and down arrow keys.   And /var/log/messages is a good place to start.  But I think we already mentioned that...

---

### Post by jpkotta on 2008-10-24
Nothing logs the output of terminal commands in general.  Certain programs keep logs, but these are usually programs that run in the background (called daemons).  They almost always log to files in /var/log/ as previously mentioned.

You can store the output of a particular command with 
```
*command* >& *logfile*
```
E.g.
```
ls >& output.log
less output.log
```
Possibly commands you entered are stored in ~/.bash_history.  It's not really meant for logging, though, it's meant to store commands for reuse.  The default settings for bash history don't work well for logging at all.

---

### Post by dizzy1kenobi on 2008-10-24
OK I have it now thanks all.

---

