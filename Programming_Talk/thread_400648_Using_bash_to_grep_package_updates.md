---
title: "Using bash to grep package updates?"
date: 2007-04-03
forum: Programming Talk
---

### Post by redline6561 on 2007-04-03
I'm interested in getting Conky to run a bash script hourly with execi that would grep a list of available packages to update from a dist-upgrade and output them in conky. I got the idea after seeing an Arch Linux user use conky to track the latest uploads to Arch repos. The difference was Arch repos have RSS feeds on package updates so he used the conky RSS plugin. I've been able to find no such Ubuntu repo feeds and so have fallen on this as a method. I figure I can either get a bash script to simulate a dist-upgrade and grep the updates. I've modified visudo to allow it to run like so:
> # User privilege specification
root	ALL=(ALL) ALL
redline ALL=NOPASSWD: /home/redline/scripts/conky_updates.sh

This is the script I'm using:
> #!/bin/bash
#
# Runs “apt-get update” and prints the output of a simulated
# dist-upgrade if new packages are found.

if [[ `apt-get update 2>&1 | grep Get` ]]; then
if [[ `apt-get –simulate dist-upgrade 2>&1 | grep Inst` ]]; then
apt-get –simulate dist-upgrade
fi
fi
(Sourced from:
[http://www.mattiaswikstrom.net/linux/20050526-apt-update-script.html](http://www.mattiaswikstrom.net/linux/20050526-apt-update-script.html))


Conky however fails to post the results to the desktop and I know there are waiting updates because I see the update manager notification in my panel.

Finally, Here's the conky.rc excerpt:
> UPDATES ${hr 2}$color
${execi 1800 /home/redline/scripts/conky_updates.sh}


If anyone wants the full conky.rc or other information it's available on request. Anyone have any advice? What am I doing wrong?

---

### Post by bruenig on 2007-04-03
Cool idea, could you explain the syntax of execi. As in what does the 1800 mean. I assume an interval but maybe not.

---

### Post by redline6561 on 2007-04-04
1800 is the interval (in seconds) between which to run the shell script. The two lines I provided are excerpted from my Conky configuration file (conky.rc). You can find examples of conky config files and shell scripts for various functions at [http://conky.sourceforge.net/screenshots.html](http://conky.sourceforge.net/screenshots.html)

The conky manpage is online at [http://conky.sourceforge.net/docs.html](http://conky.sourceforge.net/docs.html)

An example of the look I'm trying to emulate can be found on this arch install:
[http://img166.imageshack.us/img166/609/shotxf3.png](http://img166.imageshack.us/img166/609/shotxf3.png)
My install presently looks like this:
[http://img181.imageshack.us/img181/6383/screenshotss2.png](http://img181.imageshack.us/img181/6383/screenshotss2.png)

I feel like everything should be configured correctly but it doesn't output the dist-upgrade results.

Any other questions please let me know. Thanks for your help.

---

### Post by ssam on 2007-04-04
if you want rss feed s of ubuntu updates try

[http://media.ubuntu-nl.org/rss/dapper.xml](http://media.ubuntu-nl.org/rss/dapper.xml)
[http://media.ubuntu-nl.org/rss/edgy.xml](http://media.ubuntu-nl.org/rss/edgy.xml)
[http://media.ubuntu-nl.org/rss/feisty.xml](http://media.ubuntu-nl.org/rss/feisty.xml)

---

### Post by redline6561 on 2007-04-04
THANK YOU! ssam, you're the greatest. How did you find about the feed if I might ask?

---

### Post by bruenig on 2007-04-04
Ok, so here is what /etc/sudoers (visudo) looks like
```
bruenig ALL=NOPASSWD: /home/bruenig/script
```

Here is what /home/bruenig/script looks like (slightly modified)
```
#!/bin/bash

if [[ $(apt-get update 2>&1 | grep Get) ]]; then
	if [[ $(apt-get --simulate upgrade 2>&1 | grep Inst) ]]; then
		apt-get --simulate upgrade | awk '/Inst/ {print $2}'
        else
		echo "No updates" 
	fi
fi
```

And here is what the .conkyrc line looks like
```
$hr
Updates:
${execi 1800 sudo /home/bruenig/script}
```

Here is what it looks like when there are updates.
[IMG]http://i107.photobucket.com/albums/m290/bruenig/updateconky.png[/IMG]

Here is what it looks like when there aren't any updates.
[IMG]http://i107.photobucket.com/albums/m290/bruenig/noupdateconky.png[/IMG]

---

### Post by redline6561 on 2007-04-04
Thanks a million, bruenig. That's perfect.

---

### Post by ssam on 2007-04-05
> **redline6561 said:**
> THANK YOU! ssam, you're the greatest. How did you find about the feed if I might ask?

these have been mentioned on the ubuntu-dev mailing list a few times.

---

