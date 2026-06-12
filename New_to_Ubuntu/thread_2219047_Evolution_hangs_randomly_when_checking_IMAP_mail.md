---
title: "Evolution hangs randomly when checking IMAP mail"
date: 2014-04-22
forum: New to Ubuntu
---

### Post by christian20 on 2014-04-22
Hi there,

my Evolution (3.8.4) kind of randomly hangs when checking for IMAP mail. I have several accounts, one of them is affected more often, but it's not the only one. All are IMAP accounts. The problem appears as follows:


[LIST]
[*]Evolution tries to check for new mail / refresh a folder
[*]The connection hangs
[*]Cancelling the action (in the bottom bar, clicking the red cross) does not work - Evolution changes the line to "is being cancelled" but never finishes that
[*]I can't exit Evolution from now on
[*]The affected account is no longer usable until I force-terminate Evolution and restart it. Other accounts work as usual.
[/LIST]

I checked /var/log/mail.log and mail.err but there were no entries for Evolution. If there are other places I should check, please help me find them and I will post the information you need.

I'm on Linux Mint 16 with Cinnamon, but before I was on Xubuntu 13.10 and the same problems occured.

Thanks ahead and kind regards,
Christian

Edit: In addition, when killing the Evolution process from *top*, it takes two signals until it actually terminates. No idea if that is related.

---

### Post by jbaerboc on 2014-04-22
Doesn't help your situation much but I have had that issue in Thunderbird, Evolution, and Geery [which crashed after getting stuck]. I ended saying fooey on that and just use webmail instead of a client.

---

### Post by jbaerboc on 2014-04-22
Oh I did find a client called Claws which worked well but I wasn't a fan of it's look/function.

---

### Post by rbmorse on 2014-04-23
FWIW, I've had Evolution, as packaged for Ubuntu 14.04, crash to the desktop for no apparent/many possible reasons.  This is the same behavior I experienced with Evolution on LinuxMint 16.  

I've made peace with Thunderbird, which works flawlessly within its limitations. At least for me.

---

### Post by cwmoser on 2014-04-24
I've used Evolution for years.  
Most of the time it words great.
I tried Thunderbird but it did not allow both of my Email accounts emails
to be merged into the viewing pane like Evolution does.

---

### Post by manicmike662 on 2014-04-24
> **christian20 said:**
> 
my Evolution (3.8.4) kind of randomly hangs when checking for IMAP mail. I have several accounts, one of them is affected more often, but it's not the only one. All are IMAP accounts. The problem appears as follows:


[LIST]
[*]Evolution tries to check for new mail / refresh a folder 
[*]The connection hangs 
[*]Cancelling the action (in the bottom bar, clicking the red cross) does not work - Evolution changes the line to "is being cancelled" but never finishes that 
[*]I can't exit Evolution from now on 
[*]The affected account is no longer usable until I force-terminate Evolution and restart it. Other accounts work as usual. 
[/LIST]


Mine is on 14.04 and version 3.10.4 and does the exact same thing. It also requires a kill -9 to close it and just hangs on every task! :icon_frown:
Something I can reasonably predict is that if I leave email for more than five minutes it will play up. I now have to use it and quit if I don't want it to hang.
Very painful misbehaviour. Seeing as it's not actually crashing, would a stack trace be any use?
Mike

---

### Post by manicmike662 on 2014-04-24
> **manicmike662 said:**
> Mine is on 14.04 and version 3.10.4 and does the exact same thing. It also requires a kill -9 to close it and just hangs on every task! :icon_frown:
Something I can reasonably predict is that if I leave email for more than five minutes it will play up.

Don't like to reply to my own posts but I just found this: [https://syncevolution.org/blogs/pohly/2014/syncevolution-14-released](https://syncevolution.org/blogs/pohly/2014/syncevolution-14-released)
It says "  -d, --duration=seconds/'unlimited' Shut down automatically when idle for this duration (default 300 seconds)"
Of course this is exactly five minutes and seems to explain why it shuts down.
Have I discovered the source of the problem or am I barking up the wrong tree? If the former, it's very easy to both work around and fix.
Mike

EDIT: Probably barking up the wrong tree. syncevolution wasn't installed. Could there be an IMAP 300 second disconnect in evolution?

---

### Post by christian20 on 2014-04-25
Thanks for all your replies. Just to point out, I'm not going to change my mail client. Evolution is great and I'd like to get this fixed.

Also, as there seem to be issues with that, I do not use syncevolution, so the problem described in the first post is not related to that.

---

### Post by WoodenWalker on 2014-04-25
That tended to happen to me when I forgot to put in some information, such as the security options or authentication type. Have you verified these to make sure you did not overlook anything and that there are no typos? (Not trying to doubt you, just saying we all do it, or at least I do.) Lol

---

### Post by christian20 on 2014-04-25
It's all set properly. Most of the time, everything works, just sometimes Evolution hangs.

---

### Post by sbec67 on 2014-05-11
Hi,
same Problem here ... 
Evolution was running for years without any issue... now (since about 2 Month) it has this nasty hanger....
should we open a Bug ?

---

### Post by buzzingrobot on 2014-05-11
Somewhere in Evolution's settings is an option to filter all mail in all subscribed IMAP folders every time you try to pull mail down. 

Deselect that so filters are only applied to mail coming into the inbox.  That made some difference for me.

---

### Post by sbec67 on 2014-05-11
didnt do a thing to me....
what i forgot to say... i only have 1 POP Mail account configured in my Evolution....
This is realy a nasty Bug.. as Evolution hangs completly... you can only kill -9 it :-(

---

### Post by Vladlenin5000 on 2014-05-11
> **sbec67 said:**
> didnt do a thing to me....
what i forgot to say... i only have 1 POP Mail account configured in my Evolution....
This is realy a nasty Bug.. as Evolution hangs completly... you can only kill -9 it :-(

So your problem isn't the same as OP's. You better start your own thread.

---

### Post by sbec67 on 2014-05-13
> **Vladlenin5000 said:**
> So your problem isn't the same as OP's. You better start your own thread.
Hi, i dont think so.... to me it looks like evolution has a connection Problem (doesnt matter to what kind of Server... IMAP or POP) and the falls into a "hanging" state.
For that reason, u are not able to stop Evolution anymore

Regards

---

### Post by sbec67 on 2014-05-14
Hi,
i found a bypass (4 me) ..if i start evolution in a Terminal with
> evolution --disable-eplugin
the Problem disapiers ...  so the Bug seems to be somewhere in a Plugin

Regards

---

### Post by sbec67 on 2014-05-15
Guess was to fast... after some hours, eveolution was hanging again.... :(

---

### Post by sbec67 on 2014-05-22
this is realy strange.. sometimes, i am able to download all my Mails in the queue.. and then al of a suden, evolution hangs ..
no Message ... no dmesg ... nothing i can find...
all u can do to stop evolution is kill -9 or <CTRL> C in the Terminal.....

any one else ?

---

### Post by sbec67 on 2014-06-10
no news here ?

---

