---
title: "nautilus not remember folder views."
date: 2008-04-22
forum: New to Ubuntu
---

### Post by Arand on 2008-04-22
Is there a way to set nautilus to reset folder view upon restart? / Not remember folder views?

I've looked through gconf and found nil.



- Arand

---

### Post by Hospadar on 2008-04-22
Are you looking to change the default folder view?  that can be done in edit->preferences.  I'm not sure there's a standard way to make it forget the views (for individual folders I assume is what you mean).

If that's what you want, you'd have two options as far as I see, either just delete the entire nautilus config on boot/login, which would mean it doesn't remember any settings, or, figure out where it keeps track of which folders have what views, and write a script to clear that out every time you login.  It probably wouldn't be to difficult to do with bash, a little creative grep-ing and piping as long as you figure out where it is.

---

### Post by Arand on 2008-04-25
Alright, it seems this data is stored in /home/user/.nautilus/metadata [EDIT: Wrong, correct path is /home/user/.nautilus/meta**files**]

And here deleting the file related to a certain folder will reset the settings to default for that folder, after a 'relogin' is done.

So, that'll be an easy enough script I guess, now I'll just have to find out how to autorun it at login or logout...

*Goes HowTo-hunting*

-Arand

---

### Post by Arand on 2008-04-25
Okay, could I have someone's opinion on this before I shove it in for execution at shutdown.

This is what it looks like:
```
#!/bin/bash
  # This is a script which deletes
  # all folder-specific view-settings
  # for nautilus. Excluding
  # view-settings for the Desktop.
  # this will only take effect in
  # nautilus upon user login.
find ~/.nautilus/metafiles/ -name "file:%2F%2F%2F*.xml" -not -name "file:%2F%2F%2Fhome%2Fmw%2FDesktop.xml" | xargs -r rm
```

Also how exactly do I make it execute at shutdown?

Do I copy this script (after making it executable) to /ect/init.d and then just do:
```
sudo update-rc.d this_script start 90 0 6
```
??

- Arand

---

### Post by pelle.k on 2009-02-13
This is an old thread, but it still deserves an answer, so...
> Do I copy this script (after making it executable) to /ect/init.d and then just do:
```
sudo update-rc.d this_script start 90 0 6
```
No. That is system wide, run with escalated privilegies (e.g. root). Also **~/** would expand to **/root** since that is root's home folder...

What you want to do is place that script in say **/usr/local/bin**;
```
sudo gedit /usr/local/bin/nautilus-cleanup-metafiles.sh
```
And paste that code there. Then make it executable;
```
sudo chmod +x /usr/local/bin/nautilus-cleanup-metafiles.sh
```
Then preferably run it at login by adding it to autostart, **Preferences>Sessions>Add**. Name it whatever you want, put
```
nautilus-cleanup-metafiles.sh
```
as the command to run.

---

### Post by Arand on 2009-02-17
> **pelle.k said:**
> This is an old thread, but it still deserves an answer, so/.../

Tackar så mycket Pelle! :D

I made a slight modification in implementation though:

```
sudo chmod ug+x /usr/local/bin/nautilus-cleanup-metafiles.sh
```
and
```
sudo chown root:1000 /usr/local/bin/nautilus-cleanup-metafiles.sh
```
To disable other (guest account!) users than current (1000) from executing this script.

---

### Post by pelle.k on 2009-02-18
Varsågod! :)
If that's what you're after, there are other ways of accomplishing that as well.

1. To block other than <username> (put this at the top of your script);
```
if [ "$(whoami)" != "<username>" ]; then
        exit 1
fi
```

2.To block other than <user id> (put this at the top of your script);
```
if [ "$(id -u)" != "<user id>" ]; then
        exit 1
fi
```

3. If you create the folder "bin" in your home directory, it's gonna be in your (and only your) $PATH, which means you can run the script from a terminal, but not anyone else (unless the specifically run **/home/<username>/bin/nautilus-cleanup-metafiles.sh**).
I think this last solution is the most elegant in this case.

---

