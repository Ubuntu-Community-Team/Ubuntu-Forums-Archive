---
title: "Google Chrome strange behaviour"
date: 2012-07-08
forum: New to Ubuntu
---

### Post by AlbertJB on 2012-07-08
Hello all,

Recently I'm having seriously issues with Google Chrome version [COLOR=#303942][FONT=Ubuntu]20.0.1132.47
[/FONT][/COLOR]The thing is sometimes I type some letters inside some pages' forms and I don't see the letters I amb typing, but they are typed indeed and take efect (I know this because pressing OK button takes effect). I must zoom out or zoom in to see the letters typed. Any of you are having the same trouble? 

I'm using Ubuntu 12.04, gnome-classic no effects. 

Thanks in advance

---

### Post by DaJL on 2012-07-09
Same here, and when on youtube if I try to add a video to a favorite  I get a messed up screen.

Ubuntu 12-04 with KDE 4.8.4

---

### Post by AlbertJB on 2012-07-09
Thanks a lot DaJL to confirm this Chrome bug. Can you confirm please your Chrome version too?

I've switched to Firefox and everything is OK (although I find the profiles manager a bit complicate, Chrome Users was much more user-friendly :(  )

Let's see if there are more people having this same issue.

---

### Post by DaJL on 2012-07-09
Same version as you. Think it has to do with the bundled flash.  

I just tried running it from command line with the following command:
google-chrome --disable-bundled-ppapi-flash

and now it runs properly!

---

### Post by Pilot6 on 2012-07-09
The problem is with bundled flash 11.3. If Chrome starts it is enough to disable flash 11.3 in ```
about:plugins
```. Chrome 11.2 will be used.
If Crome does not start at all, which happens with old CPU that do not support SSE2 (like AthlonXP), then start Chrome as in the post above.

---

### Post by AlbertJB on 2012-07-09
Thank you very much, Pilot6, I've done that and it seems everything is ok again. Nonetheless, I'll give it a try to Firefox :p

---

### Post by Pilot6 on 2012-07-09
Firefox is not a bad choice. But I got used to Chrome and there is no reason to change anything because of this small problem.
On the machine where Crome does not start I made a link in .local/share/applications with the disable flash key and put it to the launcher. That's it. If you just edit link in /usr/share/applications, it will be rewritten on every Chrome update.

---

### Post by AlbertJB on 2012-07-09
@Pilot6 I'm not switching to Firefox just for this reason, believe me. I think FF is more suitable to Ubuntu systems, I also have Thunderbird, well integrated in Gnome. Chrome certainly is one of the best browsers, but I don't want to be Google-dependent (I already have gmail, google drive, google search, google calendar, google plus, etc..), they have enough information about me, I like to support open source projects even though their products not being "the best" and don't like the idea of having ALL my information in just one company.

But I don't want to start a flame. Everyone is free to choose how they want to store their information and which software they want to work with. ;)

---

### Post by Erdnalex on 2012-07-13
Thanks Pilot6, I had that problem and it fixed it...

---

### Post by Ace..... on 2012-09-10
> **DaJL said:**
> 
I just tried running it from command line with the following command:
google-chrome --disable-bundled-ppapi-flash
and now it runs properly!

I was very interested to find this solution.

Does anybody understand the implications of this command?

I ran it, and now even launching from the chrome icon I appear to have no problems.

Q: Has this command disabled the bundled flash for eternity?

(If not, perhaps I must simply wait till the glitches re-occur.)

Q. If not, can I create an icon for this command line?

Q. If it has totally disabled it, how does this effect the auto updates for chrome?

Actually, as an aside...... I couldn't understand why this bug was not picked up ages ago, as it has been bothersome for a good few months. Hence why I finally gave up waiting for a bug fix update, and tracked down this thread.

Thanks for the info :)

---

### Post by Epodx64 on 2012-09-10
I'm using Chrome 23.0.1255.0 dev it's crashed on me about 5x already I wish they'd update the Chromium repo's there's a few PPA's with dev builds but I haven't found a 64bit one yet.

---

