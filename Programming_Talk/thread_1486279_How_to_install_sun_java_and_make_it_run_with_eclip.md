---
title: "How to install sun java and make it run with eclipse?"
date: 2010-05-17
forum: Programming Talk
---

### Post by nishoba on 2010-05-17
I'm migrating from Windows-Netbeans IDE to Linux-Eclipse.
As I read on forums and on the web its better to download Eclipse from Eclipse site then install it using Ubuntu repositories and thats what I did.
After that I installed Visual Editor for Eclipse. And now when I start using it drawing components is painfully slow.
Under Preferences->Installed JREs its showing java-6-openjdk.

Now what is the best way to install Suns java and make Eclipse use it, even better make whole system use it and get rid of open java altogether.

I looked in Synaptic for Sun java but can't find it(have all repositories enabled).

---

### Post by GregBrannon on 2010-05-17
This is the 'how to' usually given in response to your install question, and it apparently provides good results:

[http://sites.google.com/site/easylinuxtipsproject/java]("http://sites.google.com/site/easylinuxtipsproject/java")

Your Eclipse performance should be better than you're describing, unless your hardware performance is just not up to the task.  If it doesn't improve with the SUN JRE, come back for more help.

---

### Post by nishoba on 2010-05-18
Thank you, using that source I successfully switched from open to Suns java.

But for Eclipse to use it I had to remove these additional packages(to the ones mentioned on the site): openjdk-6-jre-headless, icedtea-6-jre-cacao and openjdk-6-jre-lib. 
Otherwise Eclipse wouldn't recognize Suns java. Even if I manually added it Eclipse just wouldn't switch to it. When I removed those Eclipse did everything by itself.

PS That didn't fix my problem, but as I was reading more online its Visual Editors problem. Its not really painfully slow, but theres always delay when moving/resizing components(I click it, move it around to where I want it and then it takes few seconds (1-3) to jump into place. Everything else is fast im just not used to this kind of delays.

---

