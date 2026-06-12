---
title: "Strange Automatic Force-quit"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by lariosa42 on 2008-12-01
I have been having a strange problem.  When I quit certain applications (such as firefox or rhythmbox), I often get an error message telling me that the application has had an error, and that I can either "Wait" or "Force Quit."  After about one second, the application force quits on its own. Since I want to quit anyway, this is not really a big deal, but it is a bit irritating, and I'm also worried that it might be a symptom of something else.

(Sorry if this question was already asked, but searching the forum for variants of "force quit" brings up many pages on how to force quit certain programs.)

---

### Post by Locke_99GS on 2008-12-01
Closing an application sends a polite request to finish and shut down (sigterm), if the application hasn't terminated after a few seconds, it may ask you to rudely force the quit (sigkill), but the polite request was already sent. It is likely that the proper termination happened while the force-quit dialog was open.

---

### Post by lariosa42 on 2008-12-02
Thanks for the info.  Is there a way to fix it?  Is it a sign that something else is wrong?

---

### Post by expatCM on 2008-12-02
I have also seen this message, especially with Firefox.  It seemed to appear after one of the system updates which makes me wonder if it will disappear with another update.

Firefox seems to keep a process resident, no idea why.  If I kill the process before attempting to shut down then the message of course does not appear.  I get the impression that it will also fix itself if waiting for a minute or two after closing firefox and before trying to shut down the system ....

---

### Post by Locke_99GS on 2008-12-05
I've experienced it on only a small handful of occasions, so I don't know much about it, really. It is likely that the program has become unstable, or for some reason was not being afforded the resources needed to terminate in a timely manner.

---

### Post by lariosa42 on 2008-12-06
For me it happens (almost) every time I close Firefox.  I payed a bit closer attention, and found out that no matter what I do, Firefox shows the "Force Quit/Wait" window, waits about 2 seconds, and then (force?) quits.  This does not occur on all programs, but it is not unique to Firefox.  

It's getting a bit irritating.

---

### Post by scpatl4now on 2008-12-06
> **lariosa42 said:**
> I have been having a strange problem.  When I quit certain applications (such as firefox or rhythmbox), I often get an error message telling me that the application has had an error, and that I can either "Wait" or "Force Quit."  After about one second, the application force quits on its own. Since I want to quit anyway, this is not really a big deal, but it is a bit irritating, and I'm also worried that it might be a symptom of something else.

(Sorry if this question was already asked, but searching the forum for variants of "force quit" brings up many pages on how to force quit certain programs.)

It has been happening to me with streaming media thru firefox...the whole screen dimms and sometimes I have to force quit the browser

---

### Post by lariosa42 on 2008-12-06
This sounds like a different problem.  Streaming media works fine for me, as does everything else in Firefox, except that when I quit, it asks me if I want to force quit.

Have you tried installing the proper Codecs?  I found [this]("http://onlyubuntu.blogspot.com/2007/03/install-mplayer-and-multimedia-codecs.html") guide pretty helpful.  Use the Feisty Fawn instructions, except replace any instances of the word "feisty" with either the word "intrepid" or the word "hardy" (no quotes) depending on your version of Ubuntu.  If you are still having problems, it could be your hardware, but I doubt it.

---

### Post by Abhinav Gupta on 2009-06-14
I had the wait/force quit problem with firefox. I discovered a 'mysterious'
add-on called 'Ubuntu Firefox Modifications'. I disabled it, and things are lightning quick, no more wait/force quit messages.

---

### Post by Garyhans on 2009-06-14
Thank you for this. Ubuntu Firefox Modifications  Worked perfectly.

---

### Post by Locke_99GS on 2009-06-15
Interesting. Does anyone happen to know what the purpose of this Firefox add-on is?

---

### Post by HeadInTheClouds on 2009-10-04
I get this too (have done for several months), so have just disabled the Ubuntu add on "Ubuntu Firefox modifications 0.7" - I will post in a day or so if the results work for me too.
Running "Ubuntu 9.04 - the Jaunty Jackalope - released in April 2009" on a Lenovo T400 with 4GB ram
Kernel: "2.6.28-15-generic"
Firefox 3.0.14 Mozilla Firefox for Ubuntu canonical 1.0
I also occasionally get the "dimmed" variant, sometimes gets past the issue, sometimes it needs killing.
I don't think it is realated - so is not relevant in this post!

---

### Post by HeadInTheClouds on 2009-10-04
Well Firefox now stops and starts properly!
According to:
[http://answers.yahoo.com/question/index?qid=20090101151756AAq1kN9](http://answers.yahoo.com/question/index?qid=20090101151756AAq1kN9)
the modifications add on apparently allows installation of add-ons via Ubuntu package manager, and it seems makes Firefox start on Google search Ubuntu 
[http://start.ubuntu.com/9.04/](http://start.ubuntu.com/9.04/)
My Firefox now starts on Mozilla
[http://www.mozilla.org/](http://www.mozilla.org/) - which is the default I never got round to changing!
I will try re-enabling the modifications add on and see if this is a just glitch of some sort.

---

### Post by HeadInTheClouds on 2009-10-04
That worked,I re-enabled the Ubuntu Mozilla add-in and until now it has worked fine!
Firefox now exits gracefully and rapidly.

---

### Post by HeadInTheClouds on 2009-10-11
> **HeadInTheClouds said:**
> That worked,I re-enabled the Ubuntu Mozilla add-in and until now it has worked fine!
Firefox now exits gracefully and rapidly.

No it doesn't, I was too quick, I am still getting force quit, so back to disabling the Ubuntu Firefox modifications! :(

---

