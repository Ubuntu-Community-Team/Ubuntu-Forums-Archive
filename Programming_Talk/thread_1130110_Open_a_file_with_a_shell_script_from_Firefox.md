---
title: "Open a file with a shell script from Firefox"
date: 2009-04-19
forum: Programming Talk
---

### Post by jebbench on 2009-04-19
Hi,

I've created a script that accepts a file as it's first argument and simply moves the file to another directory.

What I want to do is set this script as the default program for the nzb file type in Firefox so that whenever I download a nzb it is moved to another directory.

If I right click on a nzb and open it with my script it works fine, but if I try to use the "Open with" option in the Firefox download window nothing happens.

The script is
```
# Script to move passed file to the Hellanzb queue directory.
#
# Define the queue directory.

d="$HOME/.hellanzb/nzb/daemon.queue"
# Check that a file has been passed.

if [ $# -eq 0 ]
then
	echo "Usage: hellqueue /path/to/file"
	exit 1
fi

if [ -f $1 ]
then
	if mv $1 $d
	then
		echo "File $1 has been moved to $d"
		exit 0
	fi
else
	echo "$1 does not exist."
	exit 1
fi
```

Thanks for any help.

---

### Post by unutbu on 2009-04-19
There may be a way to get Firefox to do what you describe, but I don't know how. An alternative might be to monitor your Firefox default download directory. (See [http://ubuntuforums.org/showthread.php?t=1104716](http://ubuntuforums.org/showthread.php?t=1104716)). You can use dirmon (or incron) to run the script every time a .nzb file is placed there.

---

### Post by ostrm on 2009-04-19
There is an add-on for Firefox, that does what you want: [downsort](http://downloadstatusbar.mozdev.org/downsort/index.html)

I'm using it to save pdfs, pictures, tar.gz and so on in different directories by default and it works quite well. I don't like the config GUI though :-)

---

### Post by jebbench on 2009-04-19
Thanks for the ideas,

I've tried downsort but it didn't do anything, the files were still saved to my desktop and I agree the interface is horrible.

I don't really want to have a script running in the background all the time, it's overkill for what I want, thanks for the idea though.

Does anyone know the way FF passes a file to another application?

---

### Post by jebbench on 2009-04-19
I've managed to get this working, all I did was to move my script into /bin and Firefox now executes it without problem.

It would be nice to know why this is if anyone knows?

---

### Post by smattr on 2011-01-31
I realise this thread is pretty old, so apologies if you've already found the answer to this. I was trying to do exactly the same thing with my NZBs with no luck when I stumbled across this thread.

After a fair bit of trial and error I discovered the problem is that the (temporary) file you are passed has permissions 400. If you chmod 666 the file in your script you should be able to do whatever you want with it - in my case scp it to my server.

---

