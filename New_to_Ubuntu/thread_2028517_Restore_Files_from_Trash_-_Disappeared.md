---
title: "Restore Files from Trash - Disappeared"
date: 2012-07-18
forum: New to Ubuntu
---

### Post by bgphelps on 2012-07-18
Hi,

I just came across two errors and now am missing some photos that I would like to get back.

1) Accidentally sent a folder of photos to the Trash. Went I went to restore them, it would not let me move them out of the trash. Rather, I received the following message: 

> There was an error copying the file into media/(location)/(file name).

Show more details

Items in the trash may not be modified 

I had been opening the trash as a separate window. To see what would happen, I added the Trash to the Cairo Bar and accessed it through there. It worked fine so I clicked 'Restore' to get my files back.

Then, I went to the Photos directory where they were and cannot find them. They are no longer in the Trash or in my photos directory. Any suggestions on how to access them?

Thanks!

Edit: 

After clicking restore, the photos folder I had open stopped being responsive. I can move it and minimize it, but cannot do anything else.

Also, I am using Ubuntu 12.04. Not letting me update my profile

Finally, the folders had switched around some since the pictures had been put into the trash. So it is possible that it tried to restore to a place that no longer existed, which may be what is causing this problem.

---

### Post by irv on 2012-07-18
First: from the error message it looks like this was done from a removable media. If the media wasn't plugged in this might have cause this error.  After restarting the system try plugging in the media and try this again.

Have you tried to restart the system since this happen? This might be causing the problem with not being able to accessing the directory. Try a restart and see if this will fix this problem.

---

### Post by bgphelps on 2012-07-18
Thanks IRV.

There wasn't any media directly involved. All the files and destinations were on the hard drive.

But, let's think about this in another way. That first error happened, but then it basically went away. I just thought it would be useful as context.

What happened next was that the Trash Bin was working, I clicked restore, and now I am not sure where the files have gone to. I've searched for them and they do not show up, but they are no longer in the trash either.

Any ideas?

Many thanks

bg

p.s. Tried restarting, still cannot locate the files

---

### Post by irv on 2012-07-18
If you know the name of the file you can just search for it in Nautilus. 
Again, did you restart your system? And after can you access the directory?

I have a app on my system call "Recoll" that does a good job of finding things. You could install it and try it. The first time you run it, it take some time to run because it does an index of all your files on your system. It only needs to do this once. It builds a database. As you add files to your system you need to re-index.

I hope you can find them, and I hope there didn't get deleted permanently.

---

### Post by bgphelps on 2012-07-18
Thanks. Tried searching for them in Nautilus but they did not come up. Needless to say I won't be trusting the Restore function anymore. I have no idea where that sent them, but they seem to be gone. 

I'll give that program a shot. Thanks for your help!

---

### Post by mapes12 on 2012-07-18
Go to /home then hit Ctrl+h. Find a file called .local>share>Trash and have a look if your files are lurking around in there somewhere.

Ctrl+h again will remove the hidden files view once you're done.

---

### Post by bgphelps on 2012-07-18
Hey, was able to find them using Recoll, just about where Mapes12 said they would be which would probably have been another solution. 

Thanks for the help!

Brian

---

### Post by irv on 2012-07-18
> **bgphelps said:**
> Thanks. Tried searching for them in Nautilus but they did not come up. Needless to say I won't be trusting the Restore function anymore. I have no idea where that sent them, but they seem to be gone. 

I'll give that program a shot. Thanks for your help!

I have deleted files and directories before and had to restore them, and it worked with no problem. In fact I just tried it by deleting a directory and restore it with no problem.

What I would do is create a directory and put some garbage files in it and try deleting it and restore it and see if you can recreate the problem.

---

