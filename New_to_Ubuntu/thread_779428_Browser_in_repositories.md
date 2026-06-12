---
title: "Browser in repositories"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by dndrich on 2008-05-02
Ubuntupals:

I just converted a complete novice to Hardy on some old hardware.  It is working great.  She got tired of Windows.  Hardy has Firefox 3 beta, as you know.  She is trying to run Runescape, which is a web based java game.  I have tried it with Firefox 2 on another computer, and it runs fine.  But it locks up here.  I am wondering if switching to another browser would work.  I want this to be easy for her, so it needs to be one in the repositories that can be reached with synaptic download manager graphically.  Any other good browsers out there that support java?

---

### Post by scragar on 2008-05-02
konqueror is a very small, efficient browser that supports Java.

[http://en.wikipedia.org/wiki/Comparison_of_Web_browsers#Web_technology_support](http://en.wikipedia.org/wiki/Comparison_of_Web_browsers#Web_technology_support)

should be a good guide, although I would really recomend either konqueror or opera(which is not in repo's).

---

### Post by Tatty on 2008-05-02
I believe firefox 2 should be in the repos, have a search.

**Edit:** It appears to be listed as firefox-2

---

### Post by Oldsoldier2003 on 2008-05-02
> **Tatty said:**
> I believe firefox 2 should be in the repos, have a search.

yes firefox2 is still available in hardy.

---

### Post by TeoBigusGeekus on 2008-05-02
If she insists on using ff, then she could downgrade to ff2: complete unistallation of the beta from synaptic and then installation of ff2.

To my opinion, you should introduce her to Opera. The latest beta might not be in Synaptic, but it comes as a deb installer so she won't have any problems. 
Opera 9.50beta2 is more stable than ever - let her try it.
[http://www.opera.com/download/linux/?ver=9.50b2]("http://www.opera.com/download/linux/?ver=9.50b2")

---

### Post by MattBD on 2008-05-02
I've just tried a Java-based site and I found the same, so maybe Java support isn't yet that great in FF3.
Firefox 2 is still in the repositories, so you could go for that.

---

### Post by dndrich on 2008-05-02
OK, but isn't it difficult to get rid of Firefox 3 in hardy?  I thought there were some problems with that.  If not, then I will just have her get rid of Firefox 3, and try Firefox 2 or Konquerer.

---

### Post by scragar on 2008-05-02
install what you want, then remove current firefox 3:
```
sudo apt-get install **firefox-2 konqueror** && sudo apt-get remove firefox && sudo apt-get autoclean
```
remove konqueror or firefox-2 as you wish.


also check [http://www.opera.com/support/search/view/841/](http://www.opera.com/support/search/view/841/) for how to add a repository for opera, which is a truely great browser, although it lacks 64 bit support.

---

### Post by kansasnoob on 2008-05-02
IMHO the only flaw in Hardy is Firefox 3 Beta 5.

About once a week I go into synaptic and trade FF2 for FF3 and give it a test drive. I haven't tried for about 4 days, but I learned while Hardy was still in Beta that it's best to have only one or the other and NOT both installed.

---

### Post by cartisdm on 2008-05-02
Opera.....plus it comes with a really fun fish game widget!

---

### Post by scragar on 2008-05-02
> **kansasnoob said:**
> IMHO the only flaw in Hardy is Firefox 3 Beta 5.

About once a week I go into synaptic and trade FF2 for FF3 and give it a test drive. I haven't tried for about 4 days, but I learned while Hardy was still in Beta that it's best to have only one or the other and NOT both installed.

it's proberly actually best to download firefox 2 from the mozilla website, and have firefox 3 installed as the one to recive all the updates, since firefox 2 has experienced very little attention recently, since the first firefox 3 beta. the one downloaded can simply be copied to /opt, and will run fine, I actualy had(on gutsy) firefox 3 beta 4 installed in this way, and although you cannot open both at the same time this does completely avoid any conflicts(although firefox 2 and 3 do disagree about a few minor things like the download files storage format, so it's best to always clear that on exit. it's also not a good idea to install the realplayer plugin, since I had real problems with that.)

---

