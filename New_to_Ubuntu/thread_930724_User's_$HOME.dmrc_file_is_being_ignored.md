---
title: "User's $HOME/.dmrc file is being ignored"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by didiercool on 2008-09-26
K, I was trying to use samba and fusesmb to employ windows shares and somewhere in the process I ruined my computer.  Now, after attempting to log in, I get the error:

> 
"User's $HOME/.dmrc file is being ignored. This prevents the default sessin and language from being saved. File should be owne dby user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."


...and my computer then restarts.  I researched this a lot and realized its a common error with an apparently easy fix:

> 
Code:

sudo chmod 644 /home/monkey/.dmrc
sudo chown monkey /home/monkey/.dmrc
sudo chmod -R 700 /home/monkey
sudo chown -R monkey /home/monkey


Everyone on the internet (including those on these forums) rejoices with this fix and its solves everything.  I, however, have yet to see any change.  Any suggestions?  At one point during my struggle I found a suggestion that I create the .dmrc file.  Would my 'creating' it overwrite the original one, rending the file useless and inoperable?  Please help!!

---

### Post by prshah on 2008-09-26
> **didiercool said:**
> 
sudo chmod 644 /home/monkey/.dmrc
sudo chown monkey /home/monkey/.dmrc
sudo chmod -R 700 /home/monkey
sudo chown -R monkey /home/monkey

Ouch! the sudo chown/chmod run on the home directory was a bad idea.

In any case, the second command should be:```

sudo chown monkey:monkey /home/monkey/.dmrc

```

I don't know (but I suspect) that you may have broken something else by recursively chmod/chown'ing the files in your home directory. Try the above command and check ```
ls -l ~/.dmrc
-rw-r--r-- 1 user user 28 2008-09-26 20:28 /home/user/.dmrc

```

If this is what you get, try restarting X and see if everything works fine.

And yes, just deleting the file works as well (it will be automatically recreated when you next logon, or just create a blank file)

---

### Post by didiercool on 2008-09-26
I get:
-rwx------ 1 user user 28 etc...
At one point I read that 700 (instead of 644, ie. -rw-r--r--) would work well, and everyone else seemed to say it worked great.  K, on reboot I got the same error.  No change yet.  :(

---

### Post by prshah on 2008-09-26
> **didiercool said:**
> 
 on reboot I got the same error.  No change yet.  :(

OK how about:```

sudo chown monkey:monkey /home/monkey
sudo chmod 755 /home/monkey
```

Note: _not_ recursive.

---

### Post by didiercool on 2008-09-26
K, no change with 755 either.

From the terminal, is there maybe some way to mount my ipod, grab all my music off of my computer (the only thing, ironically, that isn't already backed up on there) and just reformat?  I know that probably seems pretty extreme, but this is beginning to feel like an extreme case!

---

### Post by didiercool on 2008-09-27
Ok, I have now backed everything up on my Ipod through that terminal.  Would it be wise to just reformat?  Or is there still hope?

---

### Post by prshah on 2008-09-27
> **didiercool said:**
> Ok, I have now backed everything up on my Ipod through that terminal.  Would it be wise to just reformat?  Or is there still hope?

Here's one last thing you can try: Login through gnome failsafe (on the login screen, press F10 to open a menu that will allow you to select failsafe session.)

If you're logged in successfully, Click on System-Preferences-Sessions-Session Options, then:

a) _uncheck_ Automatically...
b) Click the Remember currently... button

Safe logout, and then try logging in normally again.

---

### Post by WWSmith36 on 2008-09-27
If you have wine install you may be in a lot of trouble.  The .wine folder has a symbolic link to root(/).  By recursively changing permissions it is possible to have changed all permissions on the machine.

---

### Post by didiercool on 2008-09-27
Well, its too late now, I already started reformatting.  I'm currently updating Hardy.  I did have wine installed, so that may have added to the situation, and I had been using the gnome failsafe terminal.  But there was no using Nautilus.  It couldn't create the files it needed even after I set every permission to 755 (sudo chmod 755 *).  Probably not a wise move in itself, but I was desperate and figured I'd need to reformat anyway so I thought I'd try it.  Oh well.  Thanks for the help though!  I did manage to retrieve all my files with my ipod before I reformatted!  Now I just have to set everything up again and I'll be back to normal.

~peace

---

