---
title: "error on synaptic package manager 12.4"
date: 2012-10-29
forum: New to Ubuntu
---

### Post by vegas89 on 2012-10-29
I am running ubuntu 12.4 I was trying to load remastersys to the synaptic package manager. Missed a step, did something out of sequence now I get this error box that says    E: Malformed line 60 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
 I don't know what to do with this, can someone please help me get this resolved. Thanks  :confused:

---

### Post by Bashing-om on 2012-10-29
hi ! vegas89;

I anticipate an edit/repair to the referenced line in the file.
post the file /etc/apt/sources.list to see what the edit will be.
terminal code (ctl+alt+t):
```
cat /etc/apt/sources.list  
```[INDENT]and we shall see <==BDQ

[/INDENT]

---

### Post by vegas89 on 2012-10-30
thanks, deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) precise-backports main restricted universe multiverse

deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) precise-security main restricted
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) precise-security main restricted
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) precise-security universe
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) precise-security universe
deb [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) precise-security multiverse
deb-src [http://archive.linux.duke.edu/ubuntu/](http://archive.linux.duke.edu/ubuntu/) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu) main
deb-src [http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu) main
vegas@vegas-desktop:~$

---

### Post by monkeybrain2012 on 2012-10-30
Try to comment out the last two lines with remastersys (i.e. put a "#" in front without quotations) and run synaptic again.

---

### Post by vegas89 on 2012-10-30
Don't know whats going on with reply # 5. But in response to your reply I don't understand what you mean by ( to comment out the lines ) I tried to delete or change them, but was unable to so. Please explain.   I restarted the computer using the F7 key then went to recovery mode, then to repair broken packages. In the course of what seemed to be the repairing process I saw a mention of the line 60 issue. But when the OS came back the problem was still there.

---

### Post by monkeybrain2012 on 2012-10-30
> **vegas89 said:**
> Don't know whats going on with reply # 5. But in response to your reply I don't understand what you mean by ( to comment out the lines ) I tried to delete or change them, but was unable to so. Please explain.   I restarted the computer using the F7 key then went to recovery mode, then to repair broken packages. In the course of what seemed to be the repairing process I saw a mention of the line 60 issue. But when the OS came back the problem was still there.

You need sudo to edit system files.

Here is how to do it, in terminal type

```
gksudo gedit /etc/apt/sources.list
```Give your password, now when the editor opens, you can either comment out the last two lines, that means put a "#" (without quotations) in the beginning of the lines,--that way the system will ignore them treating them as 'comments',--or simply deleting them.

Now start synaptic.

---

### Post by vegas89 on 2012-10-30
Thanks, I Did as you said    ## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner                            I still have the same issue. I am going to do a restart to see if any thing is resolved.

---

### Post by coffeecat on 2012-10-30
> **vegas89 said:**
> Don't know whats going on with reply # 5.

It was a thread hijack post - I've moved it into its own thread.

@vegas89, before you try to edit your sources.list file I suggest you check one thing. In your OP you say the error you saw included:

```
 E: Malformed line 60 in source list /etc/apt/sources.list (dist parse)
```

Yet you only posted about 24 lines of sources.list. Check the length of the your sources.list file. If you didn't post all of it, please do so. You need to look at line 60. It is possible the two remastersys lines that you are looking at may be OK.

---

### Post by vegas89 on 2012-10-30
Thanks for fixing the hijack issue. I just did a restart before I saw your reply and the synaptic package manager came up with no report of any problems !!  This issue seems to be repaired. Thanks for the suggestion, if the problem comes back I will try what you said.  ):P

---

