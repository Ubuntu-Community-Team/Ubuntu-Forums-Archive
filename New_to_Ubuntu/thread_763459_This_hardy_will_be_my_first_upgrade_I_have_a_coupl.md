---
title: "This hardy will be my first upgrade I have a couple of questions."
date: 2008-04-23
forum: New to Ubuntu
---

### Post by spacesearcher on 2008-04-23
I haven't been using ubuntu that long and I have a few Q's about the upgrade to hardy. The first is what will happen to all the settings and programs after I update? Like will I have to re-install all the old ones? and Will firefox plugins/passwords still be on there after the upgrade because there is the firefox update too?

---

### Post by Xiong Chiamiov on 2008-04-23
Everything will still be there if you upgrade, as opposed to installing off the cd.  I just did it today, and it's all fine.  Now, I had some other weird issues... but my data's all fine!

---

### Post by Oldsoldier2003 on 2008-04-23
> **spacesearcher said:**
> I haven't been using ubuntu that long and I have a few Q's about the upgrade to hardy. The first is what will happen to all the settings and programs after I update? Like will I have to re-install all the old ones? and Will firefox plugins/passwords still be on there after the upgrade because there is the firefox update too?

some of your firefox plugins may not be compatible with FF3

---

### Post by Metaleks on 2008-04-23
In addition to these answers, I would like to add that it is *always* wise to backup all your important data.  There is always a chance of something going wrong, so backing up your data is strongly encouraged.  Not only that, but it's just a good habit to get into! :)

I would also like to note that most people experience less problems by just reinstalling the new version of Ubuntu.  Upgrading is a tricky process.  This is not to say that you will experience problems.  Upgrading is seamless, but again, there is always that chance.  If it isn't an issue for you, I recommend reinstalling the version, instead of upgrading.

---

### Post by Oldsoldier2003 on 2008-04-23
> **Metaleks said:**
> In addition to these answers, I would like to add that it is *always* wise to backup all your important data.  There is always a chance of something going wrong, so backing up your data is strongly encouraged.  Not only that, but it's just a good habit to get into! :)

I would also like to note that most people experience less problems by just reinstalling the new version of Ubuntu.  Upgrading is a tricky process.  This is not to say that you will experience problems.  Upgrading is seamless, but again, there is always that chance.  If it isn't an issue for you, I recommend reinstalling the version, instead of upgrading.

I usually upgrade but I have separate partitions for /home and my data.I agree that a fresh install is usually a good thing to do but sometimes it's nicer to do an upgrade if you have highly customized your installation.

---

### Post by kpkeerthi on 2008-04-23
> **spacesearcher said:**
> The first is what will happen to all the settings and programs after I update? Like will I have to re-install all the old ones? 
No you dont have to re-install. All your installed packages will be auto upgraded. However, if you packages installed from 3rd party repositories, be sure to uninstall the packages. Also remove the corresponding lines from your sources.list file. Look in System-->Administration-->Software Sources-->Third-party software.

---

### Post by spacesearcher on 2008-04-23
ok if i want to do a fresh install like some of you recommend would  I install it like I did the first time? except this time I just don't make all the new partitions. i'm dual booting with windows.

---

### Post by Oldsoldier2003 on 2008-04-23
> **spacesearcher said:**
> ok if i want to do a fresh install like some of you recommend would  I install it like I did the first time? except this time I just don't make all the new partitions. i'm dual booting with windows.

correct. just have it install in your existing partitions, it will overwrite.

---

### Post by spacesearcher on 2008-04-23
Sweet, I think thats what im going to do then because I have figured out what default apps I want to use now that I have had ubutnu for a month. I really don't need 5 media players.

Thanks

---

### Post by Paqman on 2008-04-23
> **Oldsoldier2003 said:**
> some of your firefox plugins may not be compatible with FF3

FF2 is still in the Hardy repos, so you can stick to that instead. I'm not so sure including FF3 as the default browser was such a good choice, due to the extension compatibility situation.

Installing the Nightly Tester Tools extension on FF3 allows you to disable version checking though. That allows FF2 extensions in FF3 (although there's no guarantee they'll actually work)

---

