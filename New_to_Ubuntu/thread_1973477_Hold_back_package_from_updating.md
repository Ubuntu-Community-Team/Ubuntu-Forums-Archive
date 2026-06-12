---
title: "Hold back package from updating"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by Fraoch on 2012-05-04
I've modified Unity to remove the workspace switcher by following these instructions:

[http://askubuntu.com/questions/38789/remove-the-workspace-switcher-launcher-from-unity-launcher](http://askubuntu.com/questions/38789/remove-the-workspace-switcher-launcher-from-unity-launcher)

Works perfectly, except...the package manager knows that Unity has now been modified and will always attempt to update it with the copy in the repo.

I have tried both locking and holding the package version, using all the methods on this page:

[http://askubuntu.com/questions/18654/how-to-prevent-updating-of-a-specific-package](http://askubuntu.com/questions/18654/how-to-prevent-updating-of-a-specific-package)

Unity is indicated with a lock icon in Synaptic but Update Manager still wants to update it.  It doesn't even think there's a newer version, it just knows there's been a change:

```
Installed version: 5.10.0-0ubuntu6
Available version: 5.10.0-0ubuntu6
```

Is there anything I'm missing?  Shouldn't this have worked?

Thanks.

---

### Post by pqwoerituytrueiwoq on 2012-05-04
```
echo "package hold" | sudo dpkg --set-selections
```should take care of updetes in teh command line
marking it as locked in synaptic will take care of it in the update manager

also that settings will have no effect on the package manager's package
the only thing that will break that mod is a update that fixes the bug

---

### Post by Fraoch on 2012-05-04
> **pqwoerituytrueiwoq said:**
> ```
echo "package hold" | sudo dpkg --set-selections
```should take care of updetes in teh command line
marking it as locked in synaptic will take care of it in the update manager

That command was in the link I posted and I did try it.

However you got me to double-check.  Turns out I did something stupid.  When the directions said:

```
echo "package hold" | sudo dpkg --set-selections
```

I literally typed "package hold".  The command did not error out but

```
dpkg --get-selections
```

showed that unity was still set to "install", not "hold".

So I tried:

```
echo unity hold | sudo dpkg --set-selections
```

And now unity is set to "hold", not "install".

It's sort of working now, Unity still appears in Update Manager but it is unchecked and can't be rechecked.  So I guess this means I won't be able to accidentally update it, which is good.  It's just a little messy.:tongue:

Thank you.

---

### Post by Fraoch on 2012-05-17
A little bump with some weirdness going on.

On one of my computers this all seemed to work fine.  On another computer also running 12.04:

```
sudo dpkg --set-selections
```

hangs the terminal.

Now they're both doing it, and now both will constantly try to update Unity.  The only way I could get it to hold back was when dpkg --set-selections worked as explained in the last post.  It now seems like

```
echo unity hold | dpkg --set-selections
```

doesn't actually do anything.

I'm a noob when it comes to bash commands, but I think this is just trying to place the text "unity hold" in the dpkg status area.  If that's the case, why does it hang?  What can I do to make it work?

I suspect maybe automatic updates is interfering with dpkg?

---

### Post by wilee-nilee on 2012-05-17
You can set a lock in synaptic on any package if you have synaptic installed. Tick on the actual package, then hit package you will see the lock version in the drop down.

---

### Post by Fraoch on 2012-05-17
Thanks for the response!

> **wilee-nilee said:**
> You can set a lock in synaptic on any package if you have synaptic installed. Tick on the actual package, then hit package you will see the lock version in the drop down.

Yes, I have pinned/locked the packages this way.  It doesn't seem to make any difference to the Update Manager, it wants to update them regardless.

That is confusing, I thought they both used apt?

---

### Post by wilee-nilee on 2012-05-17
> **Fraoch said:**
> Thanks for the response!



Yes, I have pinned/locked the packages this way.  It doesn't seem to make any difference to the Update Manager, it wants to update them regardless.

That is confusing, I thought they both used apt?

Are you sure,  maybe what you are getting is actually a fix for the locked version, and not a upgrade.

---

### Post by Fraoch on 2012-05-17
My first post shows the "upgrade" is the same version number as the one it's trying to replace.  This is still the case.

When it did work on my other machine, the entries were still there in the Update Manager but were unchecked and couldn't be re-checked.  But the update versions were the same.  It detects my modified package has been changed from the current package (even though the version numbers are the same) and is trying to update it.

Edit: I just went into Update Manager to post the current version numbers:

```
Changes for the versions:
Installed version: 5.12-0ubuntu1
Available version: 5.12-0ubuntu1
```

and amazingly it's sort of working now, the update is unchecked and can't be rechecked.

<scratches head> OK I guess then?  Weird.

---

### Post by wilee-nilee on 2012-05-17
> **Fraoch said:**
> My first post shows the "upgrade" is the same version number as the one it's trying to replace.  This is still the case.

When it did work on my other machine, the entries were still there in the Update Manager but were unchecked and couldn't be re-checked.  But the update versions were the same.  It detects my modified package has been changed from the current package (even though the version numbers are the same) and is trying to update it.

Edit: I just went into Update Manager to post the current version numbers:

```
Changes for the versions:
Installed version: 5.12-0ubuntu1
Available version: 5.12-0ubuntu1
```and amazingly it's sort of working now, the update is unchecked and can't be rechecked.

<scratches head> OK I guess then?  Weird.

May have to do with the cache having the update, and a new update run sets it straight.

Ubuntu is sort of like this with updates and upgrades, it is a two way communication with the repos.

---

### Post by Fraoch on 2012-05-17
Thanks for the help.

I updated the package cache many, many times and the problem persisted.  Not sure why it's working now...

Sometimes you just have to be thankful it is working and not question why.:biggrin:

---

### Post by wilee-nilee on 2012-05-17
> **Fraoch said:**
> Thanks for the help.

I updated the package cache many, many times and the problem persisted.  Not sure why it's working now...

Sometimes you just have to be thankful it is working and not question why.:biggrin:

Yeah. :)

---

