---
title: "Time Lock on Ubuntu"
date: 2011-10-21
forum: New to Ubuntu
---

### Post by meinertj on 2011-10-21
Hey all,

I live in a community house and am the most tech savvy, therefore the computer manager.  We've decided we don't want anyone using the computer before 8am and after 9pm.  I'm running Ubuntu 11.10 and am wondering if there is any way to set the computer to be password locked during certain hours but open to use other hours.  Does anyone know if something like that exists?   Thanks for any help/advice in advance!

James

---

### Post by e79 on 2011-10-21
You could give a look at [Timekpr]("https://launchpad.net/timekpr") but it looks like its under development still...

Have a look [here]("http://www.linuxplanet.com/linuxplanet/tutorials/6584/1") as well for a little tutorial.

Hope this helps

---

### Post by llamabr on 2011-10-21
Maybe this:

[http://www.google.com/search?q=pessulus&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:unofficial&client=iceweasel-a](http://www.google.com/search?q=pessulus&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:unofficial&client=iceweasel-a)

Note that your question is not really an absolute beginner question, so if you don't get anything good, you might take it somewhere more appropriate for a better answer, like security threads or something like that.  ubuntuforms has lots of different threads.

---

### Post by Paqman on 2011-10-21
> **meinertj said:**
> Does anyone know if something like that exists?

Yes, you want [Gnome Nanny]("apt:nanny"). It can lock any user account by time of day, among other ways of restricting access.

---

### Post by ArgusVision on 2011-10-21
Nice. I'll have to check out Gnome Nanny. I was trying to do the same thing editing pam.d files. With no real success.

---

### Post by Larkspur on 2011-10-21
> **ArgusVision said:**
> Nice. I'll have to check out Gnome Nanny. I was trying to do the same thing editing pam.d files. With no real success.


Unfortunately, it seems none of these options work on 11.10, according to [this]("http://askubuntu.com/questions/68918/how-do-i-restrict-my-kids-computing-time") thread at AskUbuntu.  That thread also included a very detailed guide on how to use pam, which might help you.  There's also a link (at the bottom) to a non-repository app.

---

### Post by ArgusVision on 2011-10-21
Thanks Larkspur. That looks like what I was doing, but I may have missed a step. I'll see if I can tinker with it some more this weekend.

---

### Post by foxy123 on 2011-10-23
> **ArgusVision said:**
> Thanks Larkspur. That looks like what I was doing, but I may have missed a step. I'll see if I can tinker with it some more this weekend.

any luck with it?

I was trying to find a source file for timekpr to compile it manually but with no luck.

---

### Post by E411 on 2011-10-23
I would try to lock all their accounts through a cron job

at 9pm it writes a nologin file in /etc and removes it at 8am

not sure if it would work on ubuntu though. 

Alternatively:

sudo usermod -s /bin/false username

---

### Post by foxy123 on 2011-10-23
> **E411 said:**
> I would try to lock all their accounts through a cron job
I'm not sure whether it's easy to do. What I need for example is to lock the account on weekdays after 2hrs of use or after 8pm and after 3hrs or after 9pm on weekends. Also I need to be able to grant extra time if required (during holidays or if something needs to be done for homework).

---

### Post by E411 on 2011-10-23
> **foxy123 said:**
> I'm not sure whether it's easy to do. What I need for example is to lock the account on weekdays after 2hrs of use or after 8pm and after 3hrs or after 9pm on weekends. Also I need to be able to grant extra time if required (during holidays or if something needs to be done for homework).


with sudo usermod -s /bin/false username you will prevent them to login

with sudo usermod - s username it goes back to normal (in the case there is a homework)

with the cron job you decide of the frequency

what is not solved yet is the case of someone being logged in already

but hey, you better lock the fridge imo and let the computer available ;)

---

### Post by Slim Odds on 2011-10-23
> **E411 said:**
> I would try to lock all their accounts through a cron job

at 9pm it writes a nologin file in /etc and removes it at 8am

not sure if it would work on ubuntu though. 

Alternatively:

sudo usermod -s /bin/false username

This would be a lot more appropriate:```
sudo passwd <-l|-u> <username>
```

-l for lock, -u for unlock

But, as was mentioned, this does not help for someone already logged in.

---

### Post by E411 on 2011-10-23
for forcing users to log out see here: [http://ubuntuforums.org/showthread.php?t=1535905](http://ubuntuforums.org/showthread.php?t=1535905)

sudo pkill -KILL -u username
but like they say, it's rather brutal...

---

### Post by ArgusVision on 2011-10-24
@Foxy123 Sorry, but no I didn't. My Dad ended up in the hospital this weekend, and I spent it visiting him and running some errands for him and my Mom. I still intend to work on this though. 

Using cron to make an account locked/unlocked sounds feasable.
As for killing all user processes... harsh is a relative term.
I'm sure there's a way to have a message pop up "2 min until shutdown, save all work now." Just not sure how one might accomplish this from bash.
(Since cron uses bash commands.)

Any suggestions?

---

### Post by foxy123 on 2011-10-24
I tried to build the package from source. It builds and installs but does not work :-(

---

### Post by ArgusVision on 2011-10-26
Minor update for the question I posed earlier.

The line 
```
notify-send 'System will shutdown in 2 minutes' 'Please save all work and shutdown. Any unsaved data will be lost.' --icon=gtk-cancel
```

Will pop-up a warning in the upper right hand corner of most Ubuntu machines.

Will test if it works from cron though...

Edit: Did not work from cron. I know cron executes in the background, but I thought this would work. It does work directly from the terminal, FYI.

---

### Post by foxy123 on 2011-10-26
> **ArgusVision said:**
> Minor update for the question I posed earlier.

The line 
```
notify-send 'System will shutdown in 2 minutes' 'Please save all work and shutdown. Any unsaved data will be lost.' --icon=gtk-cancel
```

Will pop-up a warning in the upper right hand corner of most Ubuntu machines.

Will test if it works from cron though...

Edit: Did not work from cron. I know cron executes in the background, but I thought this would work. It does work directly from the terminal, FYI.

Timekpr has been updated. Though it works only with GDM.

---

