---
title: "flash still not available on FF and Chromium"
date: 2012-12-31
forum: New to Ubuntu
---

### Post by jowze on 2012-12-31
First post here, so hello, hello everyone !
(and happy new year).

So I found an old computer and installed Ubuntu PP 12.04 on it, just like on my laptop. Format of XP worked fine and it&#347; now running only on Ubuntu. I made all the available updates and installed the restricted extras. 

FF and chromium both tell me a flash pluggin needs to be added. So I checked forums, tried flash aid, no success. Tried installing hal through the terminal, no success. 

As Im planning on using this old machine solely as a jukebox, I would enjoy accessing flash based websites such as grooveshark, so some help would be much appreciated.

I´m new to troubleshooting Ubuntu, so Im not sure what kind of additional information I can bring to this thread. 

Any help welcome, ubuntu fixed many frustrations Im having on my ex-vista based laptop, Im keen on learning more !

Smiles,
Jowze

---

### Post by Autodave on 2012-12-31
> **jowze said:**
> First post here, so hello, hello everyone !
(and happy new year).

So I found an old computer and installed Ubuntu PP 12.04 on it, just like on my laptop. Format of XP worked fine and it&#347; now running only on Ubuntu. I made all the available updates and installed the restricted extras. 

FF and chromium both tell me a flash pluggin needs to be added. So I checked forums, tried flash aid, no success. Tried installing hal through the terminal, no success. 

As Im planning on using this old machine solely as a jukebox, I would enjoy accessing flash based websites such as grooveshark, so some help would be much appreciated.

I´m new to troubleshooting Ubuntu, so Im not sure what kind of additional information I can bring to this thread. 

Any help welcome, ubuntu fixed many frustrations Im having on my ex-vista based laptop, Im keen on learning more !

Smiles,
Jowze

Try this link.  It has worked on nearly every machine I have ever tried it on.  Note: the GETDEB and PLAYDEB repositories are down, but it will work w/o them in stalled.  Also, in the last phase where you are installing a whole list of programs, before you execute the script, remove the "ruby ripper" from the string.

[http://ubuntuforums.org/showthread.php?t=766683&highlight=flash+quit+youtube](http://ubuntuforums.org/showthread.php?t=766683&highlight=flash+quit+youtube)

Please also note that this is NOT my doing: no credit due to me for this link.

---

### Post by stevejluke on 2012-12-31
Also, be sure to check the basics - like if the Flash plugin is disabled.  In Chromium, go to chrome://plugins/ to see a list of all installed plugins.  Flash should be listed there.  If it is listed and enabled then go to chrome://flash/ to get details on the plugin.  Make sure you have the latest version (11.2).

On FireFox you can go to Edit > Preferences > General > Manage Add-ons > Plugins

---

### Post by jowze on 2012-12-31
thanks for your reply autodave, but still no luck... I followed the terminal commands, then looked for updates, but chromium and firefox still tell me I have a missing pluggin.

Could it be some incompatibility issues as it's a rather old machine ?

---

### Post by monkeybrain2012 on 2012-12-31
Did you isntall Ubuntu-restricted-extras?

---

### Post by jowze on 2012-12-31
stevejluke, yep I followed the path you indicated... It does show the latest flash in the list... sites still ask me for the right plugin, this is a riddle I can solve.

---

### Post by jowze on 2012-12-31
yes monkeybrain restricted extras is the first thing I installed on this PC after putting Ubuntu 12.04 on it

---

### Post by monkeybrain2012 on 2012-12-31
What websites did you test on?

---

### Post by arpanaut on 2012-12-31
> Could it be some incompatibility issues as it's a rather old machine ?Quite possibly, If your cpu does not support sse2 then the newer versions of flash will not work.

Open a terminal **ctrl +alt +t** then copy and paste this command into it.

```
cat /proc/cpuinfo
```go down to flags and see if sse2 is there, if not then you will need to revert to an earlier version of flash.

(Be back in a bit to post a link to a "how to")
Edit: follow darkod's advice in this thread, [http://ubuntuforums.org/showthread.php?t=1993220](http://ubuntuforums.org/showthread.php?t=1993220)

---

### Post by jowze on 2012-12-31
Arpanaut, in the flag list, I have sse but no sse2. probably the machine will need an older version of Flash. I be curious to check your how to when you find it.

Also, maybe I should have xubuntu on this old thing and not Ubuntu...

---

### Post by arpanaut on 2012-12-31
See my edit in previous post.

xubuntu  may work better for you but won't solve the flash problem...

---

### Post by jowze on 2013-01-01
Thanks for your reply.

I tried the fix you proposed. Still no luck. Youtube stays black where the video should be.

I also tried this solution 
[http://ubuntuforums.org/showthread.php?t=2070839&highlight=flash+pentium+III](http://ubuntuforums.org/showthread.php?t=2070839&highlight=flash+pentium+III)

When I enter the command advised in the terminal it says ´no file or directory found'* the flash *pluggin.so file is in the home folder, so I&#7743; not sure what&#347; wrong.

---

### Post by jowze on 2013-01-01
Hello again, checked your solution again, realised I tried the troubleshooting with the wrong version of the flash .so file, So I tried again, problem solved :D

Thanks a lot and happy new year again !

---

