---
title: "Run conky on startup?"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by beetlejuice_masterson on 2008-10-26
Hi All --

Quick question.  I'd like to run conky when ubuntu starts up...Since I'm running a laptop I frequently turn off & on, and dual boot so it would be convenient just to be able to automatically load it.

Seems like a simple thing to do, just not sure how!  Thanks.

Chuck

---

### Post by OutOfReach on 2008-10-27
Goto System>Preferences>Sessions.
Click on Add and then fill out the necessary data. :)

---

### Post by bumanie on 2008-10-27
Add to seesions as noted above, if running desktop effects, it is usually necessary to write a bash script to delay conky starting for 30-60 seconds to allow all the compiz stuff to load completely. There are example bash scripts available on conky sites.

---

### Post by stoogiebuncho on 2008-10-27
If you don't know what the necessary data is, just write "conky" in every field (without the quotes, of course).

Edit: I didn't need a bash script for mine, so try it without first and possibly save yourself some work.

---

### Post by ad_267 on 2008-10-27
The bash script is sometimes needed because compiz will put shadows around conky otherwise. It can look something like this:

```
#!/bin/bash
sleep 10
conky
```

You can adjust the sleep time accordingly.

---

### Post by bumanie on 2008-10-27
May be you don't need a !bash script, but in the past it was sometimes needed as conky would sit on top of everything, rather than 'behind' if it was not delayed when running in combination with desktop effects like compiz-fusion - may be times have changed since I last used conky. You can always manually start it by not adding it to sessions and hitting alt-F2 and typing conkyrc in the window that appears.

---

### Post by Bruce M. on 2008-10-27
> **beetlejuice_masterson said:**
> Hi All --

Quick question.  I'd like to run conky when ubuntu starts up...Since I'm running a laptop I frequently turn off & on, and dual boot so it would be convenient just to be able to automatically load it.

Seems like a simple thing to do, just not sure how!  Thanks.

Chuck

Check out my signature for the HowTo.

Chimo!
Bruce

---

### Post by asgard_command on 2008-10-27
I had problems running from start up under Hardy without a bash script but have no problems now with Intrepid.

---

### Post by reg4c on 2008-10-27
No problems running it without bash script

Just add a new startup thing in the Sesssions with 'conky' [no quotes] in every field.

Also, if you want to remove Conky shadow that Compiz adds open CCSM, then go to Window decorations, then in the shadow windows add '!(iclass=conky)' without quotes.

Cheers

---

### Post by beetlejuice_masterson on 2008-10-27
Hey All --
Thanks a ton for the help.  I didn't know about the sessions area.

Bash script might be necessary as Conky loaded up fine, but when the wallpaper got painted it disappeared behind it.

How do I get this bash thing set up?  Thanks for all the help--gotta love linux forums.
Chuck

---

### Post by OutOfReach on 2008-10-27
Save the script to a file, anywhere is fine. Then make it executable, Right click on it>Properties>Permissions>and check the 'Make executable' or something along the lines of that.
Then go back to the sessions dialog, then instead of 'conky' in the command section, put the location to where you save the bash script. For example:
```
/home/me/my_bash_script.sh
```

---

### Post by rabbitofdeath on 2008-11-10
This worked perfectly for me! thanks!

---

### Post by asgard_command on 2008-11-10
I don't know why but suddenly my conky wouldn't show up at start up. I have had to revert back to using the bash script which is fine just confusing.
The only changes I think I have made are installing a package libcanberra 0.10 from a ppa suggested on this thread 
[http://ubuntuforums.org/showthread.php?p=6148475#post6148475]("http://ubuntuforums.org/showthread.php?p=6148475#post6148475")

This was supposed to help with a problem with start up sounds so all I can think is that for some reason this is starting some extra process which is clogging things up just enough to mean that conky needs that bit of a delay to start properly.

---

