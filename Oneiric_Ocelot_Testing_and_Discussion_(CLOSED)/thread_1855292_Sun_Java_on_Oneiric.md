---
title: "Sun Java on Oneiric?"
date: 2011-10-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by crjackson on 2011-10-05
Can someone tell me how to install SUN JAVA on Oneiric?

---

### Post by thatguruguy on 2011-10-05
For the record, Java is now owned by Oracle, since Oracle acquired Sun.

The proprietary Java development kit [will no longer be available in the repositories]("http://robilad.livejournal.com/90792.html").

You may want to look [here]("http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html") for instructions on how to install Oracle Java 7.

---

### Post by sammiev on 2011-10-05
I like the manual way. Read [this]("http://sites.google.com/site/easylinuxtipsproject/java") if you wish.

---

### Post by moma on 2011-10-06
I deleted this message because Oracle's (Sun's) java6 has [vanished]("https://launchpad.net/ubuntu/oneiric/+source/sun-java6") from Canonical's [partner repository]("http://www.ubuntuupdates.org/packages/show/361288"). Maybe they're planning to release Java7 instead. I do not know.
I may need to change my guide.

Anyway, check if you can live with OpenJDK java.
See step 7b) of [this guide]("http://www.futuredesktop.org/").

Read also [this question]("http://askubuntu.com/questions/64515/will-oneiric-provide-suns-java6-from-canonicals-partner-repository") on AskUbuntu.com.

---

### Post by thatguruguy on 2011-10-06
> **moma said:**
> I deleted this message because Oracle's (Sun's) java6 has [vanished]("https://launchpad.net/ubuntu/oneiric/+source/sun-java6") from Canonical's [partner repository]("http://www.ubuntuupdates.org/packages/show/361288"). Maybe they're planning to release Java7 instead. I do not know.

Read my post above.

---

### Post by crjackson on 2011-10-06
I installed the OpenJdk and the icetea plugin. It didn't work well for me the last time I tried it (a couple of years ago). We'll see what happens from here.

Thanks for the information.

---

### Post by moma on 2011-10-06
Thanks thatguruguy, I got it now.
No Oracle Java 6 or 7 in Oneiric. Vi have to bet on [OpenJDK]("http://www.futuredesktop.org/#step7b") from now on. Ok?
OpenJDK is also pre-installed in Oneiric.

---

### Post by nicolasdiogo on 2011-10-07
> **thatguruguy said:**
> Read my post above.

thanks for the link.


i am not sure which way to go yet.
but it seems that we will have to make your apps compatible with openjdk soon(ish).


with regards,

Nicolas

---

