---
title: "How to add Ignored update packages back"
date: 2013-04-27
forum: New to Ubuntu
---

### Post by SamerBerjawi on 2013-04-27
Hello,

Few weeks ago I had a problem while updating Ubuntu (I was on 13.04 beta). I was getting MergeList errors, specifically with packages related to languages (Translation-en). I thought the problem would be solved by removing these sources, so I started to remove them one after the other until I found out a solution. Now, while updating, I get the following message:

```
Hit http://archive.ubuntu.com raring-proposed/main Translation-en              
Hit http://archive.ubuntu.com raring-proposed/multiverse Translation-en        
Hit http://archive.ubuntu.com raring-proposed/restricted Translation-en        
Hit http://archive.ubuntu.com raring-proposed/universe Translation-en          
Ign http://archive.ubuntu.com raring/main Translation-en_US                    
Ign http://archive.ubuntu.com raring/multiverse Translation-en_US
Ign http://archive.ubuntu.com raring/restricted Translation-en_US
Ign http://archive.ubuntu.com raring/universe Translation-en_US
Ign http://archive.ubuntu.com raring-updates/main Translation-en_US
Ign http://archive.ubuntu.com raring-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com raring-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com raring-updates/universe Translation-en_US
Ign http://archive.ubuntu.com raring-backports/main Translation-en_US
Ign http://archive.ubuntu.com raring-backports/multiverse Translation-en_US
Ign http://archive.ubuntu.com raring-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com raring-backports/universe Translation-en_US
Ign http://archive.ubuntu.com raring-security/main Translation-en_US
Ign http://archive.ubuntu.com raring-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com raring-security/restricted Translation-en_US
Ign http://archive.ubuntu.com raring-security/universe Translation-en_US
Ign http://archive.ubuntu.com raring-proposed/main Translation-en_US
Ign http://archive.ubuntu.com raring-proposed/multiverse Translation-en_US
Ign http://archive.ubuntu.com raring-proposed/restricted Translation-en_US
```

Eventually, the ones with "Hit" are not the ones I deleted, but the ones with "Ign".

My question is, how can I add these packages back? I tried recreating the source.list, but it didn't do the job. I also tried checking/unchecking the packages, as well as adding sources manually in Software & Updates. 

I also have another problem. Since April 24, I only got a very small update for Ubuntu base. Since I was running 13.04 Beta, I was expecting a bigger update since April 25. Is it me, or Ubuntu are not releasing updates daily? In the last 3 days, I didn't receive any update, and all my sources are checked!

Thank you all in advance

---

### Post by SamerBerjawi on 2013-04-27
Ping

---

### Post by ibjsb4 on 2013-04-27
There is a sources list generator if that will help.

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by SamerBerjawi on 2013-04-28
I tried this one before, it didn't.

---

### Post by ibjsb4 on 2013-04-28
Hummm .. a shot in the dark ..

They are all checked, right?

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

---

### Post by SamerBerjawi on 2013-04-29
yes, everything is checked. im not even receiving updates for ubuntu itself, since 5 days

---

### Post by ibjsb4 on 2013-04-29
I would like to see what you have.  Please post the output of:

```
cat /etc/apt/sources.list
```

---

### Post by oldos2er on 2013-04-30
> **SamerBerjawi said:**
> yes, everything is checked. im not even receiving updates for ubuntu itself, since 5 days

Have you tried switching servers?

---

