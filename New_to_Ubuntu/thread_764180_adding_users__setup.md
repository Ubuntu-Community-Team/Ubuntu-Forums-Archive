---
title: "adding users / setup ?"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by garyed on 2008-04-23
Now that I think I know enough to get eveybody out of Windows I'm setting up different users/ wife,kids etc...
If they log on they can't use flash in Firefox without downloading & installing. I know how to do that but I was wondering if there was a way for them to use the same Firefox that I use as admin since its already set up with flash etc... 
It just seems kind of redundant to redo the same downloads & installations for each user that is using the same programs.
Am I missing something?

---

### Post by PeterJS on 2008-04-23
Did you install flash from the repositories or did you use some other funny method? Installing flash from the repositories should install it to /usr/lib/flashplugin-nonfree/ and the alternatives system should handle symlinking it in to the right spot for firefox to find it for all users (/usr/lib/firefox/plugins/flashplugin-alternative.so).

---

### Post by garyed on 2008-04-23
> **PeterJS said:**
> Did you install flash from the repositories or did you use some other funny method? Installing flash from the repositories should install it to /usr/lib/flashplugin-nonfree/ and the alternatives system should handle symlinking it in to the right spot for firefox to find it for all users (/usr/lib/firefox/plugins/flashplugin-alternative.so).

I think I installed flash from a tarball but I'm really not sure because it was  quite a while ago & I'm not sure if it was before or after I set the users up.

---

### Post by PeterJS on 2008-04-23
Try installing flash from the repositories, that will get you the latest version setup correctly for all current (and future) users.

---

### Post by garyed on 2008-04-23
> **PeterJS said:**
> Try installing flash from the repositories, that will get you the latest version setup correctly for all current (and future) users.

I just installed flashplugin nonfree from with synaptic & it still doesn't work in my other users. Flash works fine in firefox for me logged in with administater priviliges but not for any one else who logs in. I might try to give them admin priviliges to see how that works but it would defeat my purpose of being admin.

---

### Post by PeterJS on 2008-04-23
> **garyed said:**
> I just installed flashplugin nonfree from with synaptic & it still doesn't work in my other users. Flash works fine in firefox for me logged in with administater priviliges but not for any one else who logs in. I might try to give them admin priviliges to see how that works but it would defeat my purpose of being admin.

I've been assuming your running 32 bit this whole time. 64bit flash is a whole other mess that involves a funny wrapper and some other weird things, I remember it's a bit of a hack.

Any way assuming you're running 32bit you should have a file named:
```

/usr/lib/firefox/plugins/flashplugin-alternative.so

```
which is a symlink to:
```

/etc/alternatives/firefox-flashplugin

```
which should be a link to you're real flash plugin at:
```

/usr/lib/flashplugin-nonfree/libflashplayer.so

```

If any of those are missing or miss directed that would explain your problem.

---

### Post by garyed on 2008-04-23
All those files except for the top symlink I have in my 
/home/<username>/.mozilla/plugins/ directoy

The symlink is not on my system at all.
By the way I'm running Feisty if that matters

---

### Post by PeterJS on 2008-04-23
> **garyed said:**
> All those files except for the top symlink I have in my 
/home/<username>/.mozilla/plugins/ directoy

The symlink is not on my system at all.
By the way I'm running Feisty if that matters

That is a really unique way to have flash installed...

Whats important is that */usr/lib/firefox/plugins/flashplugin-alternative.so* is, or links to, the real flash plugin and that it is world readable, and accessible.

I would suggest uninstalling the flash package, unlinking */usr/lib/firefox/plugins/flashplugin-alternative.so* from where ever it is pointing to, and point it at */etc/alternatives/firefox-flashplugin* with:
```

sudo unlink /usr/lib/firefox/plugins/flashplugin-alternative.so
sudo ln -s /etc/alternatives/firefox-flashplugin /usr/lib/firefox/plugins/flashplugin-alternative.so

```
Then reinstall flash from the repositories. You might be done at this point.
you can run:
```

ls -la /etc/alternatives/firefox-flashplugin 
AND/OR
update-alternatives --list firefox-flashplugin

```
to confirm that the alternatives system is working and the flash plugin is set up for firefox.

If not you'll have to unlink and manually link */etc/alternatives/firefox-flashplugin* with:
```

sudo unlink /etc/alternatives/firefox-flashplugin
sudo ln -s /usr/lib/flashplugin-nonfree/libflashplayer.so /etc/alternatives/firefox-flashplugin
```

---

### Post by garyed on 2008-04-23
Thanks for all the help but I gave up.
I just gave them administrator priviliges & installed flash from the tar.gz
I downloaded from the flash site. 
I then revoked the administaror privilige so everything is O.K. except flash is installed more than once but hust a little waste of space.

---

