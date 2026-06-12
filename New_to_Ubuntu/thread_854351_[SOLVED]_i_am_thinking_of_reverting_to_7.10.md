---
title: "[SOLVED] i am thinking of reverting to 7.10"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-07-09
most of the apps are to new and i get conflicts when try to do things like build blender or download alien arena,i never had this problem with 7.10
my question is should i be patient and wait for the repositories to update
its very frustrating getti the conflict errors and not bieng able to do what i want.should i revert??
rick:confused:

---

### Post by wolfen69 on 2008-07-09
if 7.10 did everything you wanted, why not stay with it?

---

### Post by tjwoosta on 2008-07-09
i am using 8.04 and i have not had any troubles at all with compiling, or downlaoding


i am even playing alien arena right now!


if the package from synaptic doesn't work for alien arena you might also try getdeb.net (thats where i got mine, just make sure its for the right ubuntu version)

---

### Post by rixtr66 on 2008-07-09
i tried get deb but i get the same dependency errors?:confused:
rick

---

### Post by tech9 on 2008-07-09
I tried Hardy too and thought it was too unstable - so I immediately reverted back to 7.10

---

### Post by tech9 on 2008-07-09
> **rixtr66 said:**
> most of the apps are to new and i get conflicts when try to do things like build blender or download alien arena,i never had this problem with 7.10
my question is should i be patient and wait for the repositories to update
its very frustrating getti the conflict errors and not bieng able to do what i want.should i revert??
rick:confused:

Hi Rick,

You can get 7.10 from the following link...

[http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/)

I would back up all your data, (i.e. music, videos, documents - ect) and install 7.10 clean.

Let me know if you need more help.

T9

---

### Post by Canis familiaris on 2008-07-09
> **tech9 said:**
> I tried Hardy too and thought it was too unstable - so I immediately reverted back to 7.10

Did you try 8.04.1. It had numerous bug fixes.

---

### Post by jamesrfla on 2008-07-09
I just did a clean install of Ubuntu Desktop Edition 8.04.1 and it works fine. For some reason the first time the installation failed but I tried it the second time and it worked. No problems so far with 8.04.1

---

### Post by JohnLM_the_Ghost on 2008-07-09
Well, if your Gutsy works for you, then go for it! It is still supported till April 2009! So at least until then have no worries!

Only It's kind of hassle to get all that data to a new installation... and I really recommend you to do fresh install! Actually I don't know a way to revert without fresh reinstall!

p.s. I was also thinking to revert, but I'm just too lazy to get it done.

---

### Post by phidia on 2008-07-09
I had a hardy install during the prerelease cycle. It wasn't really that bad but after hardy's release I saw so many issues in the forums that I just used my gutsy and deleted the hardy install. I'm not bashing hardy I really didn't have any major complaints.

I was interested in the reverting/downgrading idea and came across this:

> Unfortunantly, upgrading
Debian is much easier than downgrading. But, it can be done...

Two options:
1. backup your data and reinstall
2. try apt-get pinning. the process is to
a. update your /etc/apt/sources.list to stable
b. remove most of your installed applications
c. set an apt-preferance to prefer packages marked 'stable'
d. run apt-get -s, and allow it to run
e. cross your fingers

More on downgrading here:
[http://matthewpoer.freehostia.com/wordpress/2006/11/01/abandon-ship-give-me-back-my-dapper-drake/](http://matthewpoer.freehostia.com/wordpress/2006/11/01/abandon-ship-give-me-back-my-dapper-drake/)

 which came from [here]("http://www.debianhelp.org/node/8778").

---

### Post by rixtr66 on 2008-07-10
where can i get 8041 id like to try that before downgrading??
rick

---

### Post by tech9 on 2008-07-10
> **rixtr66 said:**
> where can i get 8041 id like to try that before downgrading??
rick

try this link...

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

