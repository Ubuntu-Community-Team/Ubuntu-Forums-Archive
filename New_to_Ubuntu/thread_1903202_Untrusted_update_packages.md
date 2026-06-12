---
title: "Untrusted update packages"
date: 2012-01-01
forum: New to Ubuntu
---

### Post by Sleepy-zz-John on 2012-01-01
For about the last 1 month,  my Ocelot's Update Manager has been presenting me with a set of updates which, when I try to install them,  bring up a note that they are untrusted.   Please see my attached "Updates.jpg" and "Untrust.jpg".   I'm not sure whether my failing to install these is blocking any more recent updates,  but since this trouble started a month ago, no other new updates have been presented,  which I find unusual. 

One by one, I've tried deselecting all of the listed updates except one and checked to see whether that one could be implemented on its own, but no,  they all bring up the same untrusted note.  

So two questions:

1.  How come untrusted packages are getting into my updates like this?

2.  How can I remove them so that I can resume normal updating?

---

### Post by Nuno Machado on 2012-01-01
> **Sleepy-zz-John said:**
> For about the last 1 month,  my Ocelot's Update Manager has been presenting me with a set of updates which, when I try to install them,  bring up a note that they are untrusted.   Please see my attached "Updates.jpg" and "Untrust.jpg".   I'm not sure whether my failing to install these is blocking any more recent updates,  but since this trouble started a month ago, no other new updates have been presented,  which I find unusual. 

One by one, I've tried deselecting all of the listed updates except one and checked to see whether that one could be implemented on its own, but no,  they all bring up the same untrusted note.  

So two questions:

1.  How come untrusted packages are getting into my updates like this?

2.  How can I remove them so that I can resume normal updating?
Hi please try this way and see if it works, open your terminal and run sudo apt-get update and after sudo apt-get upgrade.

Thanks

Nuno

---

### Post by Sleepy-zz-John on 2012-01-01
Thanks for the swift response,  Nuno.

Tried that.   Results in my attached "Update.txt"

There were quite a lot of error failures as you can see,  but I tried the upgrade nevertheless,  and that asked me whether I wanted to install without verification.    

Since I didn't really undertand the implications I took the cautious approach at this stage and answered "no",   so I'm still getting the same response from Update Manager as before.

---

### Post by alphacrucis2 on 2012-01-01
Note the :8080 on the end of the ip addresses. Looks like it is trying to connect via a http proxy. Did you you configure a proxy server?

---

### Post by Sleepy-zz-John on 2012-01-02
Yes,  thanks alphacrucis,  I agree that 8080 does look odd.

Hmmm...  don't think I've got any proxy server set,  but sorry to say I'm not 100% sure.  About a month ago, I remember trying something to do with proxy server setting to allow https access via wifi in a public library.  Can't be quite sure what I did,  but thought I undid it at the time.  How (in Ocelot) can I double-check if I've inadvertently left some proxy-server setting that I shouldn't?  

I've looked in Network -> Network Proxy and found "Method" set to "None"

I've looked in Firefox -> Edit -> Preferences -> Advanced -> Settings and found "Use system proxy settings" checked.

Is there anywhere else I should look?

Another possible clue is that I'm currently in Thailand,  but I downloaded my Ocelot upgrade from Natty via that public library wifi source while I was in England last October.    However some Ocelot updates did work successfully between October and early December.   This updating trouble only started in December.

---

### Post by Elfy on 2012-01-02
Maybe - [http://ubuntuforums.org/showpost.php?p=10972099&postcount=2](http://ubuntuforums.org/showpost.php?p=10972099&postcount=2)

Untrusted updates are probably coming from a ppa you have enabled - you can disable those in software sources one at a time see if it goes. Or realise that is where it is coming from and accept it.

---

### Post by Sleepy-zz-John on 2012-01-02
> **forestpiskie said:**
> Maybe - [http://ubuntuforums.org/showpost.php?p=10972099&postcount=2](http://ubuntuforums.org/showpost.php?p=10972099&postcount=2)
Yes,  you're a genius forestpiskie!   Removing that apt.conf file has completely fixed it.   A massive backlog of updates and upgrades have just come through and been installed,  so my Update Manager is now completely clear.  Well done and thank you!
>  Untrusted updates are probably coming from a ppa you have enabled - you can disable those in software sources one at a time see if it goes. Or realise that is where it is coming from and accept it.
No,  it wasn't from a .ppa   It must all have been caused by the proxy server that I didn't even reralise I had set.   :redface:

---

### Post by Elfy on 2012-01-02
The only genius I have is remembering that I had seen it before and a bit of google-fu

Glad you're sorted out - can you mark thread solved.

---

### Post by Nuno Machado on 2012-01-02
> **Sleepy-zz-John said:**
> Yes,  you're a genius forestpiskie!   Removing that apt.conf file has completely fixed it.   A massive backlog of updates and upgrades have just come through and been installed,  so my Update Manager is now completely clear.  Well done and thank you!

No,  it wasn't from a .ppa   It must all have been caused by the proxy server that I didn't even reralise I had set.   :redface:
Glad it worked out for you, i was going to suggest that youmight needed to disable some repository you had :)

Good luck

Thanks

Nuno

---

### Post by Sleepy-zz-John on 2012-01-02
Appreciate your comment Nuno, even though it's solved.   Actually I believe an element of "post mortem" analysis after problems have been fixed could be very instructive.   In this case I'm not quite clear what you meant by "disable some repository".   Would you care to give an example?

---

### Post by audiomick on 2012-01-02
> **Sleepy-zz-John said:**
> ...what you meant by "disable some repository".   Would you care to give an example?
If you look around in the settings of the software centre (or synaptic) you will find your list of package sources. These can be individually disabled. If some package is giving you grief, you can disable the source that it is coming from, and the updater will then ignore it. Of course, if you disable the main source for the OS, you wont get any updates at all.

---

### Post by Nuno Machado on 2012-01-02
> **Sleepy-zz-John said:**
> Appreciate your comment Nuno, even though it's solved.   Actually I believe an element of "post mortem" analysis after problems have been fixed could be very instructive.   In this case I'm not quite clear what you meant by "disable some repository".   Would you care to give an example?
Well no need to anwser that as i was trying to help you.

What i was saying is that you needed to edit the file that forestpiskie mentioned, but i see, that you already have solved it, and if it is no more comment needed.

And what audiomick said above too is valid.

And i did not see the "Solved" mark at the top of the topic.

Have a nice stay at Ubuntu forums. :)

Be well

Nuno

---

