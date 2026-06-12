---
title: "Java Applets not loading in web browser - trouble with uninstall of Sun Java."
date: 2013-07-12
forum: New to Ubuntu
---

### Post by ask_ on 2013-07-12
Hello , 
I am using Lubuntu 13.04 and after install of the OS I had installed Sun Java from the Oracle website. I followed the instructions given on [https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java) . I think , I had made Oracle Java as default. And for many days it worked just fine. Now , since it is not installed via repositories , it doesn't get updated. And whenever the applets would say Update Plug-in I would ignore the warning and run the old plug-in . This worked for a month or so. But recently the applets didn't load at all , they were taking eternity. So I decided to shift to Iced-Tea , Open JDK and that sort of stuff. I even made Open JDK as the default version , but the problem is not going. And I fear I have now executed some steps which I don't completely understand - I uninstalled Open JDK 7 and switched to Open JDK 6 . And the situation is unchanged. Is is possible that you ask me to give the output of some commands in the terminal , using which you may be able to diagnose the problem my system has ? 

Thanks . 
Cheers.

(I didn't mark Lubuntu as prefix because I don't think it is an issue arising due to Lubuntu as such.)

---

### Post by QIII on 2013-07-12
Hello!

I wouldn't use either Oracle (not Sun -- Sun was bought by Oracle) Java 6 or OpenJDK 6.  Both are beyond EOL now.

If you want to use Oracle Java 7 and make sure it gets updated as Oracle releases new updates, I suggest going to the Java wiki in my signature and finding the link "Using webupd8.org's strikingly simple method".

Webupd8.org is highly trusted, so I can confidently recommend it.

The PPA does not contain Oracle Java 7, rather it contains scripts to download from Oracle, install and set Oracle Java 7 as your alternative.  It will also install the plugin.

When you do your normal Ubuntu updates, if there is a new Oracle Java 7 update it will happen automagically.  With the method you used you would have to watch for when new updates are released and repeat the process after having deleted the previous installation.

Best wishes!

---

### Post by Frank_T._Morgan on 2013-10-15
[COLOR=#808080]*(Post removed by author.)*[/COLOR]

---

