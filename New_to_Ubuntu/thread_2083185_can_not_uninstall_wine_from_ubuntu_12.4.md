---
title: "can not uninstall wine from ubuntu 12.4"
date: 2012-11-11
forum: New to Ubuntu
---

### Post by vegas89 on 2012-11-11
Can some one please give me the code script to completely uninstall wine from my ubuntu 12.4  I have tried various codes when I put the question to Google but they just won't do a complete uninstall.  ](*,)

---

### Post by cariboo on 2012-11-11
You can try:

```
sudo apt-get purge <packagename>
```

---

### Post by vegas89 on 2012-11-11
tried that but it doesn't work!

---

### Post by squakie on 2012-11-11
without seeing the output from the purge, and not knowing more about what isn't getting removed, it's hard to tell.

however, keep in mind that there is a hidden folder (.wine) in your home folder that contains everything in terms of config files and the virtual disk that wine is using.  uninstalling the package doesn't remove that folder.

---

### Post by vegas89 on 2012-11-11
But is there a way to get it all out?

---

### Post by monkeybrain2012 on 2012-11-11
> **vegas89 said:**
> But is there a way to get it all out?

But you never answer that question how uninstalling didn't work. More info please.

If the purge works then you need to manually delete the hidden folder .wine in your home directory (ctr+h to see it) and to remove desktop files for applications you installed in wine find the hidden folder .local/share/applications in your home directory and delete the subdirectory wine and that's it.

---

### Post by vegas89 on 2012-11-12
when I did the purge command  it got rid of wine tricks but the configure wine is still in the dash and I am still able to launch it. Also now the OS will not boot unless I use the f7 key. I then use repair broken packages but it will say at the end that it could not resolve 'ppa. launchpad.net'. and just before that , there is mention of something about the wine application.  I hope if I can fully purge this wine app then perhaps this will clear up. I didn't fully understand the last suggestion of what to do to fix this problem. Sometimes I just don't get it !

---

### Post by vegas89 on 2012-11-12
Alright fellow beanheads, What ya'll suggested to do just seemed like to much to go through, so I fixed the OS by doing a new 12.4 install, I'm getting purity good at that. Problem solved!!

---

