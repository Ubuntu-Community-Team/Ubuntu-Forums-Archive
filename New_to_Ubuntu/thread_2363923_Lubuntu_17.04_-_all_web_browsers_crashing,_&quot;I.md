---
title: "Lubuntu 17.04 - all web browsers crashing, &quot;Illegal instruction (core dumped)&quot;?"
date: 2017-06-16
forum: New to Ubuntu
---

### Post by namesomething on 2017-06-16
It's my first time trying to dedicate some time into understanding Ubuntu or Linux in general, and I'm running into some problems. I just installed Lubuntu 17.04 on my machine yesterday (it's an Athlon XP 2400+ with 1 GB of RAM and a GeForce 6200), let it run the few updates it asked to run, and now every single web browser I try to run crashes either immediately or while trying to load most sites, outputting "Illegal instruction (core dumped)" in the terminal. I know that the version of Firefox shipped in the LiveCD worked fine in here, but using the package manager to revert to it didn't work (it still crashes on startup), and even Firefox 45 ESR, which works on my Windows partition, refuses to work in there. I also tried every single web browser from the software center and a SSE-only version of Pale Moon, but all of them suffer the same fate.

Could those updates have broken something in here, or sneaked in something incompatible with my system by accident? Is there any way to revert everything without reinstalling the whole system?

[edit] Solved it, my explanation is in a post down below. I had completely forgotten about the Flash plugin.

---

### Post by monkeybrain20122 on 2017-06-16
Since you just installed it yesterday maybe try a reinstall and see what happen? Also maybe it is better to install Lubuntu 16.04. It is based on LTS and therefore more stable. I have a tested 17.04 on a spared computer, it gets glches here and there that I don't experience in 16/04 (no show stoppers, just small annoyances)

---

### Post by QIII on 2017-06-16
Hello!

32 or 64 bit OS?  32 or 64 bit browsers?

Do you have a proprietary driver installed for your graphics card.

It sounds like you are able to load at least some sites.  What is different about them?  Could you give us a couple of URLs that work and a couple that cause the crash?

Thanks!

---

### Post by namesomething on 2017-06-16
I believe I've found the problem, I just remembered that the Flash  plugin stopped supporting SSE2-unable processors a long time ago so  after uninstalling flashplugin-installer I'm able to open Firefox and  visit sites with Pale Moon again. Haven't tested for too long, but so far everything seems to run fine.
I'll  look into installing Flash 11.1 another time, according to some  research that was the last one to support poor little CPUs like mine.

In any case, it's a 32 bits OS running the browser versions I found in the Software center and Synaptic, I tried installing the NVidia drivers that the system found though the "additional drivers" link to no avail at the time, and both Google and DuckDuckGo seemed to run fine on QupZilla, but sites like AskUbuntu didn't.

[edit] I think I've played around enough on the sites I usually visit without having any further issues to be sure that uninstalling Flash fixed this problem.

---

