---
title: "bash script to execute all scripts in a directory"
date: 2010-11-09
forum: Programming Talk
---

### Post by tarahmarie on 2010-11-09
Hi, all:

I am upping my Dropbox-fu.

I have a cronjob running every minute to execute a script.

Now, what I need that script to do is execute every script in a directory. I have Dropbox running, and I've pointed that script to the Dropbox directory. Ideally, I want a script that does this:

if (there's a script in /specifiedDirectory) {
run it
move it to /otherDirectory
}
else{
do nothing
}

I don't really know where to start. I want to set this up because the most common task that happens to me is wanting a file on my home machine that I don't have handy. I already have written scripts that will copy files from any directory I want to a Dropbox directory (an example is if I should finish an ebook while out, and want a new one). Now, I need to connect the dots between that cron job and the script that will copy the file to where I want it. Once the script is finished executing, it should move itself back to the /Dropbox/scripts directory, or whatever. I may want to write and execute some other scripts and have them pop back to that directory as well.

Any ideas on how I should start?

---

### Post by squaregoldfish on 2010-11-09
I suggest you look into the run-parts command, as seen in /etc/crontab - I think it does what you want, or at least will do with a bit of tweaking.

I can't give any more info than that - I just know that it exists :)

Steve.

---

### Post by James78 on 2010-11-09
```
#!/bin/bash

if [ -e /if/script/in/specified/directory/exists.sh ]; then
  /execute/script/path/script.sh
  mv /path/to/script.sh /move/to/dest/directory/
else
  # do nothing
fi
```

... But you say you wanted it to run every script file in a specified directory? Let me know what you're thinking with some pseudo code..

---

### Post by DaithiF on 2010-11-09
something like:
```
#!/bin/bash
scripts_to_run_dir=/home/you/Dropbox/scripts_to_run
scripts_archive_dir=/home/you/Dropbox/scripts_archive
shopt -s nullglob
for script in "$scripts_to_run_dir"/*
do
    if [[ -x "$script" ]]; then
        "$script"
        mv "$script" "$scripts_archive_dir"/
    fi
done

```

You probably realise that this is a security risk, right?  -- if anyone got access to your dropbox account they could place a malicious script (e.g. rm -rf /home/you/*) into your scripts dir and your cronjob would happily run it.

There are lots of other alternatives for accessing a computer remotely -- ssh for example (which is what I use), so maybe you should explore some of those alternatives instead.

---

### Post by tarahmarie on 2010-11-09
You may be right about the security.  OTOH a simple verification at the beginning of the script and in the cronjob means that no script would execute out of that directory unless it contained my specified code. Plus, CONVENIENT.

---

### Post by TSJason on 2010-11-12
```
for each in thisdirectory/*.sh ; do bash $each ; mv $each thatdirectory/ ; done

```

---

