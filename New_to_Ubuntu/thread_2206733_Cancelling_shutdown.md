---
title: "Cancelling shutdown"
date: 2014-02-20
forum: New to Ubuntu
---

### Post by Penfold1971 on 2014-02-20
I wish to cancel a shutdown I set up in Terminal, remotely, (and incorrectly), and issue a different shutdown command.

What command will cancel an already set up shutdown?

---

### Post by Lars Noodén on 2014-02-20
You can cancel a shutdown that's in the queue with -c

```

sudo shutdown -c

```

I don't know if it will stop a machine from shutting down once the process has commenced.

---

### Post by Penfold1971 on 2014-02-20
Brilliant, Lars. That worked a treat.

What I had done was (with 'sudo' in front of course), 'shutdown -h 1402201535', thinking that my system would be shut down (this afternoon) at 3.35 pm. I had thought that digits were in the correct yymmddhhmm format, and that I had the command correct. Had I made a mistake?

I got the alarming response that the system would shutdown in 1402201535 minutes! Well, shutdown did NOT occur at 3.35 pm, and I therefore wanted to use my old tried and tested 'shutdown -h now' command, which has worked.

---

### Post by Lars Noodén on 2014-02-20
The time syntax for [shutdown](http://manpages.ubuntu.com/manpages/saucy/en/man8/shutdown.8.html) is just a time either relative or absolute, but no date.  So it's worth checking the manual page when trying something new or unfamiliar.  If you want to do a lot of testing to find the right settings, you can also use -k which will just go through the motions without actually shutting the system down.

---

### Post by Penfold1971 on 2014-02-20
Thanks for that, Lars. I should have checked the man pages.

---

### Post by Lars Noodén on 2014-02-20
They do vary in quality quite a bit.

---

### Post by Penfold1971 on 2014-02-20
Well, as a novice myself, I'm glad you said that because I often consider myself a bit dim when I read them. I find that my response, on reading an item is, sometimes, "Does that mean … ?", if you understand. Testing it out isn't something I feel confident about, which is why I ask around. I appreciate the patience of people like you who are willing to help with what must seem like simple issues.

---

