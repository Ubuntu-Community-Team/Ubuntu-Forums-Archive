---
title: "Java in FF7 not supported?"
date: 2011-10-09
forum: New to Ubuntu
---

### Post by d4m1r on 2011-10-09
**[SIZE=1]When I go to do a ping test @ pingtest.net, it tries to measure packet loss and to do so it initiates a mini java applet. I am not sure if it worked before, but recently I got notified of an update to both Firefox (v7) and my java runtime client (v6?). Anyway, now when I go to that page and run the test, it gets stuck on "Applet started" and the test doesn't complete. Website works fine on my Windows 7 partition (with Firefox 4).[/SIZE]**


Can someone else try that site with FF7? What version of java are you running locally? Logs from terminal below.

damir@Damir-Ubuntu:~$ ps -ef | grep java
damir     3340  1741  2 17:31 ?        00:00:02 /usr/lib/jvm/java-6-openjdk/jre/bin/java -Xbootclasspath/a:/usr/share/icedtea-web/netx.jar:/usr/share/icedtea-web/plugin.jar -classpath /usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar sun.applet.PluginMain /tmp/icedteaplugin-damir/1741-icedteanp-plugin-to-appletviewer /tmp/icedteaplugin-damir/1741-icedteanp-appletviewer-to-plugin
damir     3481  3426  0 17:33 pts/0    00:00:00 grep --color=auto java

---

### Post by d4m1r on 2011-10-10
Nobody has any idea? :( Can someone confirm that site is working on their own ubuntu partition or tell me what ps -ef | grep java tells me about my java client...is it running?

---

### Post by davdo2004 on 2011-10-10
I can confirm what you have said that the pingtest applet wont run in firefox 7. I tried it with a stand alone version of firefox 3.6 in my home folder and it works perfectly.

---

### Post by -kg- on 2011-10-10
Have you checked everything at the following page?

[http://support.mozilla.com/en-US/kb/Using%20the%20Java%20plugin%20with%20Firefox?s=+java&r=0&as=s]("http://support.mozilla.com/en-US/kb/Using%20the%20Java%20plugin%20with%20Firefox?s=+java&r=0&as=s")

I've never tried pinging myself, so I wouldn't be able to help much.  Have you checked the FF Forums?  Another browser (like Chrome or Opera)?

---

### Post by -kg- on 2011-10-10
OK, I just went to pingtest.net and ran a test.  I initially had the problem you described, but ran it again and it completed.

Do you have Noscript installed?  I allowed the script for the sites first, but it wouldn't complete once I allowed it.  When I ran the test again it completed.

I'm running FF 7.0.1

Edit - I just ran it with a couple of different servers, and the app froze until I allowed it through NoScript.  Then the tests ran fine.

---

### Post by d4m1r on 2011-10-10
> **-kg- said:**
> OK, I just went to pingtest.net and ran a test.  I initially had the problem you described, but ran it again and it completed.

Do you have Noscript installed?  I allowed the script for the sites first, but it wouldn't complete once I allowed it.  When I ran the test again it completed.

I'm running FF 7.0.1

Edit - I just ran it with a couple of different servers, and the app froze until I allowed it through NoScript.  Then the tests ran fine.

Nope, I don't have NoScript. Looks like theres another user with the same issue...Any suggestions kg?

@firefox link, thanks for the link and it ultimately link to a Java page where you can test your version and mine says it is fine and running](*,)

---

### Post by ubupirate on 2011-10-10
Are you using the OpenJDK stuff, or the Sun Java package with reconfiguration to use Sun Java as default?

I use FF7 with Sun Java 6 Update 26 and it works perfectly fine.

---

### Post by d4m1r on 2011-10-10
> **ubupirate said:**
> Are you using the OpenJDK stuff, or the Sun Java package with reconfiguration to use Sun Java as default?

I use FF7 with Sun Java 6 Update 26 and it works perfectly fine.


How do I check? I think OpenJDK is the default and came pre-installed but I manually ran (./) jre-6u27-linux-i586.bin and it created a folder called jre1.6.0_27 in my users home directory.

---

