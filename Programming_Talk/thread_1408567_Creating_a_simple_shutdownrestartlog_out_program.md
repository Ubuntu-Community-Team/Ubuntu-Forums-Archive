---
title: "Creating a simple shutdown/restart/log out program"
date: 2010-02-16
forum: Programming Talk
---

### Post by ClearyA on 2010-02-16
So I'm not totally new to linux, I took a break for school, but now I'm back! Basically what I'm looking to do is create three separate programs which when run, causes a shutdown, a restart, or a log out. The end goal of this is to have evolution scan the subject line of incoming emails for three separate commands essentially, that will launch these programs so I can shutdown/restart/log out my computer remotely. Im guessing python may be the best way to go about this? I'll need semi detailed instruction as I am not familiar with python, or too much programming for that matter. I would also not be opposed to another method of doing this, and so I suppose I should note that I have an iPhone I could jailbreak if there is a way to access my system remotely using some sort of SSH through a jailbroken iPhone (not sure if this is even possible but it seems as though someone else must have thought to do this). Any help is appreciated! And Im glad to be back in Ubuntu! :)

---

### Post by ratcheer on 2010-02-16
Why reinvent the wheel? These programs are already built in and there are many ways to call them. My preference is to "sudo init 0" to shutdown and "sudo init 6" to restart.

Tim

---

### Post by Zugzwang on 2010-02-17
> **ratcheer said:**
> Why reinvent the wheel? These programs are already built in and there are many ways to call them. My preference is to "sudo init 0" to shutdown and "sudo init 6" to restart.

Tim

I think the point is that the OP wants to do this automatically on certain events.

@OP: Intergration into Evolution is likely to be more complicated than just having a process that receives e-mails from a certain server and acts depending on its contents. For example, [this page]("http://docs.python.org/library/poplib.html") contains some minimal example of accessing a mailbox via POP in Python (bottom of the page). you just have to replace the "print j" command by something that checks for the "magic word" in the E-mail, and execute the command 'system("shutdown -h now")' if received. Then let the script run with root rights every minute by making a cron job out of it and you're done (oh, and don't forget removing the e-mail from the server then!).

---

### Post by ClearyA on 2010-02-17
Thanks a lot! That was what I was looking for more or less. Cheers!

---

