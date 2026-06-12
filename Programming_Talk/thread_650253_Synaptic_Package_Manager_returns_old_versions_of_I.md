---
title: "Synaptic Package Manager returns old versions of IDEs"
date: 2007-12-26
forum: Programming Talk
---

### Post by vagenas on 2007-12-26
Hello! I needed to install Netbeans and Eclipse IDEs on Ubuntu 7.10. After searching by means of the Synaptic Package Manager, I found out that the available versions are:
- netbeans5.5.1-2 and
- eclipse3.2.2-3, respectively,
while the latest ones, according to the official sites are:
- netbeans6.0 and
- eclipse3.3, respectively, Moreover, none of the aforementioned IDE versions are Beta (I think eclipse 3.3 is more-than-5-month-old).
Is this because we are waiting for these versions to get more stable?
Thanks!
Regards!

---

### Post by LaRoza on 2007-12-26
Can you get .debs for them elsewhere?

I don't know why the older versions are in.

---

### Post by vagenas on 2007-12-26
> **LaRoza said:**
> Can you get .debs for them elsewhere?

I don't know why the older versions are in.


The official sites provide only installation files that apply to all Linux distributions (netbeans-6.0-linux.sh and eclipse-jee-europa-fall2-linux-gtk.tar.gz). I have configured synaptic package manager to accept files from main, universe, restricted and multiverse sources. It seems to me that, for the time being, there is no .deb-based way to have the latest versions of these 2 IDEs installed.
Thanks anyway!

---

### Post by Majorix on 2007-12-26
Have you checked getdeb.net? They sometimes provide software that's newer than the ones in the repos. Yeah, I know, it's not nice if we can't have these software in the repos. However, if you are using Gutsy, there must be a way to get those programs in the backports. Ask the folks responsible for the backports, I believe they are active in launchpad.

---

