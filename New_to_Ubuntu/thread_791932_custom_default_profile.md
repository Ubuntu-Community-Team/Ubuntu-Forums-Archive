---
title: "custom default profile"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Mr Potter on 2008-05-12
I'm building out a few Hardy boxes for work, and I'm running into a snag, and haven't found much info on it.  If I've created a custom theme what would I need to do to set it as the default system wide?  Say for instance that any new user created on the system would automatically use that theme (and desktop settings):shock: instead of Human?

I know how to do this in Windows (use a dummy account to apply the theme, and make any other system changes, then as administrator copy that user profile into the "Default" folder in "Documents and Settings").  Is there a similar way to do this in Hardy/Ubuntu?  I guess I shouldn't say "is there" I know there is, as I've done it before in 6.06, but it was a while ago, and I can't seem to find the thread on how it was done (and can't remember how for the life of me!).

---

### Post by Monicker on 2008-05-12
> **Mr Potter said:**
> I'm building out a few Hardy boxes for work, and I'm running into a snag, and haven't found much info on it.  If I've created a custom theme what would I need to do to set it as the default system wide?  Say for instance that any new user created on the system would automatically use that theme (and desktop settings):shock: instead of Human?

I know how to do this in Windows (use a dummy account to apply the theme, and make any other system changes, then as administrator copy that user profile into the "Default" folder in "Documents and Settings").  Is there a similar way to do this in Hardy/Ubuntu?  I guess I shouldn't say "is there" I know there is, as I've done it before in 6.06, but it was a while ago, and I can't seem to find the thread on how it was done (and can't remember how for the life of me!).

I know tha files in /etc/skel are used as a template for a new user account.  I haven't tried it myself in regards to themes, but any directories in /etc/skel would automatically be given to a new user, and I would imagine any customization should be in a hidden folder of /home/username.

Worth a try.

---

### Post by Mr Potter on 2008-09-21
I'm going to give that a shot. I have had some success creating a profile folder in "/" dumping things like the theme, icons, fonts, log on screen in it and pointing all of the settings to that folder. I'll give your suggestion a try and report back.

---

