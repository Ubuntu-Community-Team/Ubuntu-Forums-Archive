---
title: "conflict in libcairo"
date: 2006-07-02
forum: Repositories &amp; Backports
---

### Post by manutremo on 2006-07-02
Hi!

The adept-notifier in my kubuntu installation says that there is an upgrade version of the library libcairo (from 1.1.10-0ubuntu1 to v1.2.0-0ubuntu1). But if I  upgrade this library, I get conflicts because it needs v2.2.1 or greater of libfreetype6, which is not in the repositories.

I think that libfreetype6 also has other dependencies that are missing in the repository.

Will somebody make this new version of libfreetype6 available?

Thanks!

---

### Post by kpkeerthi on 2006-07-02
Yes. I got this conflict too after a recent compiz update. See [http://www.compiz.net/viewtopic.php?id=389&p=13](http://www.compiz.net/viewtopic.php?id=389&p=13)

---

### Post by Anduu on 2006-07-03
Bumping this because it has been two days now and no fix...who is responsible for managing these packages?

---

### Post by benny@linux on 2006-07-04
i have this problem to !!
what to do???
please someone can fix this packege ??

---

### Post by MeneK on 2006-07-05
No news yet??

---

### Post by dakira on 2006-07-05
Hi,

as you can read in the above mentioned thread this is because the compiz repositories include a version of libcairo that can't be installed in a regular Dapper because of dependency problems. The Compiz people shouldn't have put it there in the first place.

Solutions: 
1. Fulfill the dependencies yourself by getting them from debian unstable and then do another upgrade OR
2. just bare with it until the compiz people figure it out (provide the dependencies themselves) OR
3. comment out the compiz repositories in the sources.list and stick with the Xgl/Compiz you have right now

dakira

---

### Post by manutremo on 2006-07-05
Thanks, I deleted the compiz repositories and the conflict disappeared. I had enabled them when doing some tests with xgl/compiz, but am not using it at this time.

---

### Post by munckfish on 2006-07-06
Seems it's been sorted this morning. I've just got some updates through including new 'quinn' versions of libcairo2 and compiz.

---

