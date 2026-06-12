---
title: "Bash script for monitoring changes in a directory tree"
date: 2008-10-17
forum: Programming Talk
---

### Post by librano on 2008-10-17
hi all!

I am trying to write a script and I am pretty new at this. So I think I will need some suggestions and advice.

I want to write a very small, fast and lightweight script to monitor a directory tree (including sub directories and files) for changes. This could be new files, files being deleted or changes to a file. Changes in this directory will have to trigger another script to run.

Ways I have found of doing this are by using ls, find or rsync to periodically check for changes while running in a loop

What would be the most efficient way of doing this? I would be grateful if you could maybe write a little bit of example code.

Thanks.

---

### Post by Hospadar on 2008-10-17
You might consider creating a script which takes some sort of snapshot of a directory/tree and writes it to a file and compares the current tree to the previously recorded tree.  Then maybe use a cron job to call your script periodically.  cron is designed to periodically run tasks without your input, so it might be just the right choice.

---

### Post by stylishpants on 2008-10-17
A more elegant approach than trying to maintain the dir tree state within your script and polling, is to write your script based on one of the tools that wraps the inotify api.

Inotify can send a message when the dir tree is modified in some way.  The inotify-tools package provides a lightweight wrapper around the inotify api that is designed to be used in scripting. 

Here's an example script from the inotifywait man page:

```
      #!/bin/sh
       while inotifywait -e modify /var/log/messages; do
         if tail -n1 /var/log/messages | grep httpd; then
           kdialog --msgbox "Apache needs love!"
         fi
       done

```

---

### Post by ghostdog74 on 2008-10-17
for systems with no such tools as inotify, its very easy to create . here's a poor man's way
```

base="/tmp/monitor.base"
dir_to_monitor="/home/yhlee/test/"
check="/tmp/status_now"
if [ ! -e $base ] ;then
    find "$dir_to_monitor" |sort > $base
fi
# check 
find $dir_to_monitor | sort > $check
#if there's difference, then there's change.
diff $base $check 
...
...
#more code
...

```

---

### Post by librano on 2008-10-30
thanks for your replies.

inotify seems to be the best option. However I have one problem. I've been trying to figure this out but I'm kind of stumped. This is the command I would like to run...

```
inotifywait -m -r --format '%f' -e modify -e move -e create -e delete ~/test
```

This would give me the names of files the are modified, moved, deleted or created in the test directory. 

My problem is: How do I get the output of this command (name of the file) as it is being output... and use it in another script... or in this script in another command?

thanks.

---

### Post by librano on 2008-10-30
it one of those times i find the answer just after asking the question... this is what i was looking for

```
inotifywait -m -r --format '%f' -e modify -e move -e create -e delete ~/test | while read line
do
	echo "hello $line"
done
```

---

### Post by Mr.Macdonald on 2008-10-30
Not to take over the thread but is there a way to run a process that does this, because there are a lot of processes on my machine that just sit and wait, does this make my comp. go slower

---

### Post by charding on 2012-02-12
Know how I would implement inotify to do bi-directional sync of directories?

---

### Post by F35 on 2012-03-05
librano proposed on October 30th, 2008 07:32 PM the solution you see.  I am unclear where the actual list of changes is being written to.  Is it to the screen?  Is it to a file?  
Any suggestions on what to add to the script he proposed which would push the results to a file?

---

### Post by Khayyam on 2012-03-05
> **F35 said:**
> [..] I am unclear where the actual list of changes is being written to.  Is it to the screen?  Is it to a file?  Any suggestions on what to add to the script he proposed which would push the results to a file?

echo prints to stdout .. so redirect to a file like so:

```
echo $line >> /path/to/logfile.txt
```

HTH ... khay

---

