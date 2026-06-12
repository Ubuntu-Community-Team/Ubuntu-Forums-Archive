---
title: "How to stop Verbose output for Rsync while running?"
date: 2013-07-20
forum: New to Ubuntu
---

### Post by ulyssesAU on 2013-07-20
There is probably a very easy answer, but I have spent an hour searching to no avail!

I am copying data from my Ubuntu Server 12.04 to a NAS using the instructions from an earlier question I posted - [http://ubuntuforums.org/showthread.php?t=2163219](http://ubuntuforums.org/showthread.php?t=2163219)

I have have run this command:

```
 rsync -av /mnt/raid/media/TV\ Shows  /mnt/nas 
```

I have enabled Verbose output to see what was going on, the trouble is I am transferring 800GB and this takes a while.

**Questions:**
How do I stop the Verbose output but keep the process running in the background? I want to do some other work on the server.
How do I restart the Verbose output to check on the progress?

Thanks for you time in advance - if you can help, keep in mind I am new, so please be detailed :)

---

### Post by dannyboy79 on 2013-07-20
you can't really stop and resume rsync unless you used some other options when you started the command (unless someone else knows how to accomplish that) BUT if you're on a server and want to do other work just use another virtual terminal and hit ctrl-alt-f1 all the way through f6, you can log in to any of those terminals. OR next time become familiar with the screen command, it's very useful when ssh'ing into a machine and you don't want to ssh in twice, screen allows you to disconnect from a screen and start another and then cycle between "screens"

---

### Post by ulyssesAU on 2013-07-20
Thanks for your quick reply! I ssh through iTerm on my Mac - does Virtual terminal apply? Any commands I enter in my iTerm shell show as gibberish while Verbose is outputting e.g. "^[OP^[OQ"

Now this will show my inexperience but I honestly didn't think to open another iTerm window and SSH in again.. this works fine! 

You said "[if] you don't want to ssh in twice" - would it matter much if I do? Are there any drawbacks/conflicts to ssh'ing in again with the same username? Would it be better to ssh into another user profile?

the screen command also sounds useful, I will look further into this!

Edit - If I close iTerm altogether, I assume Rsync will continue running on the server. Now if I come back, for example, 30 mins later and ssh in again, I also assume Rsync Verbose will not just start spitting info out. So how do I get Rsync Verbose going again to check the progress? i.e I would like to know how long I left until the copy job finishes (I know progress in troublesome as Rsync cannot always tell what is not synced so might not be a percentage per se, BUT i can tell by the files transferring how much is left as this is a one time copy job and it goes alphabetically).

---

### Post by nerdtron on 2013-07-20
If you are using rsync on iTerm, I think it will stop copying when you close the terminal you used to issue the rsync command.
What I suggest you should do is that you open a dedicated iTerm window for rysnc and open another window for you to use. Or use the command

```
rsync -a --progress /mnt/raid/media/TV\ Shows  /mnt/nas &
```

--progress will show you the progress and the & at the end will put the command on the background. Or you can also press Ctrl+Z when you are running rsync to pause it and then issue the bg command to send it to background.

And don't worry about copying from the start if you paused/stopped copying midway through the files, rsync is intelligent enough to see which file is completely copied and which is not.

---

