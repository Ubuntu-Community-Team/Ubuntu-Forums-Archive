---
title: "basic question"
date: 2005-06-20
forum: Programming Talk
---

### Post by kimes on 2005-06-20
When I install some programs in synaptic pakage manager..I found that some libraries has 2 kinds of pakage. for example, the one is 'libgtk', the other is 'libgtk-dev' the second one has '-dev' prefix.. I can think that is for development right..? but what is extact differences under the hood..?I just think that the first one (without -dev postfix) are installing only library, and second one(with postfix) are installing sources and include files too? Am I right?

---

### Post by antwerx on 2005-06-20
Hello - I think you are essentially correct. Without running a dif against the two I don't  know for sure. 

I don't develop on my main laptop so I don't install or use any of the dev packages unless Synaptic/Apt  tells me too. Also what developing I do is ver basic learning type projects.

But, I think you are absolutley correct.

Hope this helps.  :)

---

### Post by intangible on 2005-06-20
You are right :D.

You only need the -dev packages if you are compiling programs yourself that need to be linked in with said libraries or programs.

---

### Post by LordHunter317 on 2005-06-20
The -dev version of a package contains the static library, the include files, and maybe programmer documentation.

Production systems don't need or want them.  Development systems must have both.

---

### Post by kimes on 2005-06-20
all right.. thanks for you guys' answers..
I also wanna know if there is way to know what some pakages is gonna install on my desktop without install'em.
I might be some options in apt-get or dpkg command..

---

### Post by LordHunter317 on 2005-06-20
apt-file can do it; be forewarned that it has to download ~8MB file to be able to do this.

---

