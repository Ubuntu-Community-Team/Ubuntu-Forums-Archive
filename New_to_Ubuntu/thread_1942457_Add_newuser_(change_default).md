---
title: "Add newuser (change default)"
date: 2012-03-17
forum: New to Ubuntu
---

### Post by dwhite on 2012-03-17
hi,

I am adding new users (children, spouse) to my home computer, (just installed xubuntu) and i have spent quite a bit of time getting the desktop to be configured the way i like it. Is there a simple way to have this be the default layout for new users that are added.  this would save a great deal of time.

thanks,

doug

i just tried putting my .config/xfce4 file in the newuser .config folder but didn't really work.  got same background some of the settings, none of the launchers, old panels etc.

---

### Post by MG&amp;TL on 2012-03-18
According to:

[http://www.ambience.sk/old/user-account-copy-linux](http://www.ambience.sk/old/user-account-copy-linux)

copying all of the hidden ("dot something") files and directories should probably make the same config. Just make sure that you change the ownership to the new user, otherwise things could go badly wrong for the account. Also, you probably don't want your email passwords, chat configs, internet settings, copied, so I suggest:

a) Caution. Check what their account can do before you let them use it.

b) Only copying the .config folder.

Let us know how it goes. :)

---

### Post by dwhite on 2012-03-20
hi thanks for the suggestions (I only wish i had heeded them :) ) I think this is going to work, I unfortunately was looking at the coding from the link and before going back to reread your suggestions sudo'd my way into trouble.

I realize now how important suggestion b) is I copied all of my .* files in my home directory to the new user, (as opposed to just from my .config folder.)  this had dire consequences as i was no longer able to log into my account for reasons i didn't have time to investigate (I needed computer at work today so i reloaded xubuntu last night).  I will say that when i did log into the newuser account initiially it looked remarkably like my own desktop and I'm confident (but tentative to try at the moment) that it will work fine if i follow your suggestions.

Well another learning experience...when i get up the nerve to try again and i'll let you know if it worked until then i'll mark this thread solved.

thanks again,
doug

> **MG&TL said:**
> According to:

[http://www.ambience.sk/old/user-account-copy-linux](http://www.ambience.sk/old/user-account-copy-linux)

copying all of the hidden ("dot something") files and directories should probably make the same config. Just make sure that you change the ownership to the new user, otherwise things could go badly wrong for the account. Also, you probably don't want your email passwords, chat configs, internet settings, copied, so I suggest:

a) Caution. Check what their account can do before you let them use it.

b) Only copying the .config folder.

Let us know how it goes. :)

---

### Post by MG&amp;TL on 2012-03-20
Well, sorry you had problems. :( At least the next google-er will see that next time.

No problem, any time. :)

---

