---
title: "Back Up Error (.cache/yelp permissions)"
date: 2017-05-05
forum: New to Ubuntu
---

### Post by alauda on 2017-05-05
Hi. Have been using Ubuntu 16.04 for several months with no problems on a Lenovo T60. Have been doing weekly back ups automatically with no problems. However got error: unable to back up files in .cache/yelp and found that permissions for this directory had been set to Root.

I am unclear as to why this has happened, and nothing else seems to have got fouled up. trying restore didn't help.

Is it safe to change the ownership of this directory to Group ?  (As a newby I will require help on exact code for chown commands.)

Regards.

---

### Post by TheFu on 2017-05-05
Welcome to the forums.

Is yelp a program? Did you run it with sudo?

If you've run any GUI programs with **sudo**, then that is the likely cause.  Using sudo won't change the HOME directory and there are often side-effects in many GUI programs.

BTW, if you've never tested your backups by performing a restore, then you don't really know if they are working. Please test them.

---

### Post by alauda on 2017-05-05
TheFU....Thank you for your reply.

Directory involved was        home/.cache/yelp
Yelp is the tool used for browsing Help documentation in Gnome.

Opening Yelp via the Ubuntu "Search your computer" GUI provides the appropriate material so I assume all is ok.
Restore function appears to work correctly on all the data, photos etc.

The "problem" I was posting, was that I have never had these "errors" reported before when the back up utility had finished, and had never noticed a locked directory in /.cache  - I was therefore concerned that I might have clobbered the system somehow.
So far it seems I have not......:wink:         

Cheers.

---

### Post by TheFu on 2017-05-05
I use xman, but don't have much GUI here.  Don't run gnome, unity, kde myself.
If root owns the files, then it is most likely that **sudo** was used.  I cannot think of any other likely reasons for files under there to be owned by root.

 home/.cache/yelp?
Do you mean ~/.cache/yelp or $HOME/.cache/yelp or somewhere else?

~/.cache/ doesn't/shouldn't have anything important.  I wouldn't even back that area up (and I don't).

---

### Post by alauda on 2017-05-05
Whoops....
Directory was       /home/usr/.cache/yelp
It contains the Ubuntu Desktop Guide program files.... important to a Ubuntu newby like me. The back up system defaults to backing up all of /home as far as I can see ... but don't forget i'm a beginner at this.

As I say it all appears to work.

So unless Ubuntu falls over in the next few days I will have to mark this thread as "solved" I suppose. 

Regards.

---

### Post by deadflowr on 2017-05-07
> **alauda said:**
> Directory was       /home/usr/.cache/yelp
It contains the Ubuntu Desktop Guide program files.... important to a Ubuntu newby like me. The back up system defaults to backing up all of /home as far as I can see ... but don't forget i'm a beginner at this.


No, it's just a cache folder.
The guide is in /usr/bin/yelp.
In fact you can obliterate the .cache folder completely and still have a functional system with a functional guide program.
Albeit, doing so resets the system to a more fresh state, possibly removing any customizations you set, and possibly making a few of your more used programs to take a moment longer to open.

But removing the yelp folder and it's contents should have absolutely no affect on running the guide program.

---

### Post by alauda on 2017-05-11
> **deadflowr said:**
> No, it's just a cache folder.
The guide is in /usr/bin/yelp.
In fact you can obliterate the .cache folder completely and still have a functional system with a functional guide program.
Albeit, doing so resets the system to a more fresh state, possibly removing any customizations you set, and possibly making a few of your more used programs to take a moment longer to open.

But removing the yelp folder and it's contents should have absolutely no affect on running the guide program.

Thanks for info Deadflowr.

"Problem Solved"

---

