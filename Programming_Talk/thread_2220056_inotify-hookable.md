---
title: "inotify-hookable"
date: 2014-04-26
forum: Programming Talk
---

### Post by 13l-jason on 2014-04-26
I'm hoping to find someone familiar with inotify-hookable.  (See Here: [https://metacpan.org/pod/App::Inotify::Hookable](https://metacpan.org/pod/App::Inotify::Hookable))

I'm developing an application (PHP) that I'd like to have triggered by inotify-hookable.  I can get inotify-hookable to trigger and call my script just like I want.  The problem is that I can't seem to figure out how to get it to pass the name of the modified/created/deleted file.  

On a related not, I've used inotifywait to stick the filename in a file, or stdout, but in this case, I can't get it to launch my script.

My next step (not ideal, but I think it'll work) is to have inotifywait update a flat file, then have inotify-hookable watch that file for changes and launch my script.

Any thoughts?

Thanks

---

### Post by 13l-jason on 2014-04-27
OK, I'm terribly surprised that no one knows the answer to my question.  I think my plan be is going to work.  I have run into another issue though, maybe I can get some help with this.  I'm using a bash script to launch a couple of inotify processes.  I'd like to track these processes with the script so that when the script get's closed, it can kill those processes.  Is there an easy way to do this?

Thanks

---

### Post by ofnuts on 2014-04-28
1) You can get the PIDs of the process you lauch in the backrgound (special variable "$!")

2) Then you intercept signals to your script: [http://linuxcommand.org/wss0160.php](http://linuxcommand.org/wss0160.php)

3) During the processing of these signals you send a signal to your child process (INT/TERM/HUP)

OTOH closing a bash instance normally kills the processes that it started so if this is not the case these children are doing something to dodge the standard termination signal (SIGHUP)

---

### Post by 13l-jason on 2014-04-29
Thanks, that's exactly what I was looking for.  Though, eventually this will be running as a daemon, looks as though there's a lot to do to get the script prepared for that, this will certainly get me through R&D phase.

Thanks

---

