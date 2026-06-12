---
title: "HOWTO: Speed up firefox browsing"
date: 2006-12-28
forum: Outdated Tutorials &amp; Tips
---

### Post by KnownSense on 2006-12-28
*Disclaimer: Please understand that [COLOR=Red]**you are making these changes at your own risk.**[/COLOR] I will not take any responsibility for any negative consequences caused by following these tips.*


The following tips will help you speed up your browsing experience.

Type **about:config** in the address bar and hit enter. You will notice a lot of configuration entries in the window. We shall add / modify some entries. To add new configuration entries, right-click within the window, choose **New** and select the type of entry.

The following variables will now be modified / added:

    *** nglayout.initialpaint.delay** of the type **integer**, set it to **10**
    * **content.interrupt.parsing** of the type **boolean**, set to **true**
    * **content.max.tokenizing.time** of the type **integer**, set it to **8**
    * **content.notify.backoffcount** of the type **integer**, set it to **-1**
    * **content.notify.interval** of the type **integer**, set it to **2**
    * **content.notify.ontimer **of the type **boolean**, set to **true** 

After all the above entries have been made, close all firefox browser windows, and startup firefox again. Page rendering will be noticeably faster. As always, experiment, and post back here if you get more info.

---

### Post by encompass on 2007-04-30
I want to say that these are all default in Feisty now... good job.

---

### Post by embeemb on 2007-05-01
Works perfectly. Thanks for the howto !!

---

### Post by ashrack on 2007-05-03
> **encompass said:**
> I want to say that these are all default in Feisty now... good job.
Are U sure they are the default settings now in Feisty? Since in my case those options don't even exist

---

### Post by davin on 2007-05-03
good tips get little performance boost..

---

### Post by Kaobear on 2007-05-03
A nice little performance boost.

---

### Post by dwolf on 2007-05-04
Works great.

---

### Post by kobewan on 2007-05-05
They didn't exist for me in Feisty either.

What does this do anyways?

---

### Post by hornett on 2007-05-05
Beware, some of these options may actually slow down Firefox, for example:

Content.notify.ontimer problems:
"   *  This preference does not exist by default.
    * Setting this preference to true will greatly increase rendering time on high speed connections. "

[http://kb.mozillazine.org/Content.notify.ontimer#Related_bugs](http://kb.mozillazine.org/Content.notify.ontimer#Related_bugs)

Just google each preference name to find out what side effects it may have.

---

### Post by Trekko on 2007-05-05
Just a little translation for the swedish people out there.
Integer = Heltal.

Works greit, thx for the tips!


:guitar: :guitar:

---

