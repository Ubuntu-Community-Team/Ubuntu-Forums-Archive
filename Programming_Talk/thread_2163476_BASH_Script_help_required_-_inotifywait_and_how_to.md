---
title: "BASH Script help required - inotifywait and how to use fifo queues"
date: 2013-07-18
forum: Programming Talk
---

### Post by Sum Olgy on 2013-07-18
Hey all - first post and all that so please be gentle!

I'm running a bash script to monitor a directory for new file additions.  I then want to run a task on this file.  What I've got so far is fine, so long as only one file is written at a time and another file doesn't arrive before the task finishes.  However, if another file arrives while the task is running notifications go astray and the whole thing starts to go pear shaped.

So, I guess I need some sort of fifo queue.  But I can't think of how best to achieve this in Bash, as my bash scripting ability isn't the best.

So, here's what I've got working so far:-

```
#!/bin/bash

DIR="/home/ftp/upload"
SUFFIX="txt"


inotifywait -qme close_write -m --format %f $DIR/ | while read filename;
do
        echo "File Extension found: " ${filename##*.}
        echo $filename
        echo "Doing stuff"
done


```

However this doesn't work if 'doing stuff' takes longer than the next file takes to arrive

So, what I'd need is something like this (yes, it's 'pseudo code, if that's ok to show what I think I need to do)


```
#Run_queue shell script:

While(true)
{
   Wait_for_a_signal();

   While( queue not empty )
   {
       # Use the next filename in the queue to do stuff with.
       # Remove this filename from the queue.
       # If filenames where added to the queue during execution then
       # the queue is not empty, keep processing them one at a time - first in, first out.
   }
   // Queue is now empty, returning to wait_for_a_signal
}



 
#Shell Script to wait new files to be added to a directory and add them to a queue
# Signal run_queue when something gets added.
#
#!/bin/bash

DIR="/home/ftp/upload"
SUFFIX="txt"


inotifywait -qme close_write -m --format %f $DIR/ | while read filename;
do

       echo "File Extension found: " ${filename##*.}
       echo $filename
       echo "Doing stuff"
       #Append file name and path to queue....
       #signal Run_queue......

done


```

I'm not specifically looking for someone to do this for me, more pointers to ideas on how best to achieve a result.

Thanks in advance.

---

### Post by Vaphell on 2013-07-18
i tested *inotify | while read* combo and it does put file names in queue.

```
while read f; do echo "[$f]"; sleep 10; done < <( inotifywait -qme close_write -m --format %f ~/Desktop )
[Untitled]
[Untitled 2]
[Untitled 3]
[Untitled 4]

```
i spammed new files on desktop rapidly but the names were read after 10s intervals just fine. Do you do something weird in the processing part that might conflict with stdin?

either way you could try calling some script that will process the file asynchronically and read another filename without any wait

```
while read f; do echo "[$f]"; some_script "$f" & done < <( inotifywait -qme close_write -m --format %f "$dir" )
```

---

