---
title: "Do updates use p2p"
date: 2012-10-11
forum: New to Ubuntu
---

### Post by bigmonmulgrew on 2012-10-11
I've just been setting up a ubuntu server 12.04.
I ran an update after it was setup. The downloads are running at just over 50kb/s.
I'm on 40Mb fibre and its pretty good but my provider does shape p2p. Does ubuntus update use p2p?

---

### Post by DuckHook on 2012-10-11
Choke point is probably at mirror end. Try:

[http://askubuntu.com/questions/39922/how-do-you-select-the-fastest-mirror-from-the-command-line/9035#9035](http://askubuntu.com/questions/39922/how-do-you-select-the-fastest-mirror-from-the-command-line/9035#9035)

I don't believe updates are p2p, but don't really know. Would be curious to find out. Anyone?

---

### Post by ALinuxWindowsBalance on 2012-10-11
> **DuckHook said:**
> Choke point is probably at mirror end. Try:

[http://askubuntu.com/questions/39922/how-do-you-select-the-fastest-mirror-from-the-command-line/9035#9035](http://askubuntu.com/questions/39922/how-do-you-select-the-fastest-mirror-from-the-command-line/9035#9035)

I don't believe updates are p2p, but don't really know. Would be curious to find out. Anyone?

Nope. APT does a WGET command to download the updates in a repo on the ubuntu site.
I bet that repo has some torrents, but the default is HTTP, not P2P.

---

### Post by Lars Noodén on 2012-10-11
You can use the package [apt-p2p](http://www.camrdale.org/apt-p2p/).  It will try P2P first and fall back to HTTP.  It would be of most use in a classroom or lab full of machines but might be fine at home too.

---

### Post by bigmonmulgrew on 2012-10-11
Well it must have got faster. I needed 45 updates. I watched the first dozen or so and they all ran at 51.5kb/s. I figured such a stable and low speed must be artificially capped somehow but my ISP only caps torrents and the like.

I gave up watching when one update said it was going to take 15 min. 2 min later I looked and it had finished

---

### Post by bigmonmulgrew on 2012-10-11
> **Lars Noodén said:**
> You can use the package [apt-p2p](http://www.camrdale.org/apt-p2p/).  It will try P2P first and fall back to HTTP.  It would be of most use in a classroom or lab full of machines but might be fine at home too.

nice tip but I'm more interested in making sure it does not go over p2p.

---

