---
title: "How to uninstall Evolution"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by kender42 on 2008-08-06
I tried to uninstall evolution mail because it doesn't have the features I need and it also has a conflict with thunderbird but everytime I try to unistall it I noticed it's tied to most of the desktop and os. How can I uninstall evolution without breaking everything.

---

### Post by Blutack on 2008-08-06
Are you sure it conflicts with Thunderbird?  You can remove the Evolution package (which will remove the entry from the menu), however various parts of Gnome require evolution libraries which is why you cannot remove them.  What exactly is the nature of the conflict?

---

### Post by northern lights on 2008-08-06
Sorry mate, gotta leave it.

As you have noticed, it's libraries are part of the extended package ubuntu-desktop.

You can remove the launcher from the gnome menu via "System > Preferences > Main Menu".

---

### Post by billgoldberg on 2008-08-06
> **Blutack said:**
> Are you sure it conflicts with Thunderbird?  You can remove the Evolution package (which will remove the entry from the menu), however various parts of Gnome require evolution libraries which is why you cannot remove them.  What exactly is the nature of the conflict?

Sure you can remove Evolution.

```
sudo apt-get autoremove evolution --purge
```

But I can't predict what it will take down with it.

I don't see that much trouble though.

If it takes down the ubuntu desktop, well just install the apps you need without installing the ubuntu-desktop meta package, so you wont have evolution.

---

### Post by northern lights on 2008-08-06
> **billgoldberg said:**
> Sure you can remove Evolution.

```
sudo apt-get autoremove evolution --purge
```

But I can't predict what it will take down with it.

I don't see that much trouble though.

If it takes down the ubuntu desktop, well just install the apps you need without installing the ubuntu-desktop meta package, so you wont have evolution.
Fair enough. You _can_ do a lot of things if you have an idea how to get them accomplished. However, evolution is a small app. And since I'm sure the OP has no interest in restoring his desktop environment, I'd say screw the extra 8544KB and leave evolution...

---

### Post by kender42 on 2008-08-06
The conflict that I'm having with thunderbird is that everytime I click it in the start menu it starts evolution instead. I installed tb through the synaptic package manager

---

### Post by northern lights on 2008-08-06
In general:

You can start thunderbird via the run dialog, invoke via Alt+F2, then type "thunderbird", hit Enter key.

Or create a launcher, add "thunderbird" in the command entry box.

However, all of the above is not necessary, since, it does what you describe because evolution is still your preferred mail reader.

Navigate to "System > Preferences > Preferred Applications". Make thunderbird default mail reader.

---

### Post by billgoldberg on 2008-08-06
> **northern lights said:**
> Fair enough. You _can_ do a lot of things if you have an idea how to get them accomplished. However, evolution is a small app. And since I'm sure the OP has no interest in restoring his desktop environment, I'd say screw the extra 8544KB and leave evolution...

True.

I just didn't want the OP to have the impression he can't remove something as simple as an email client.

---

### Post by northern lights on 2008-08-06
> **billgoldberg said:**
> I just didn't want the OP to have the impression he can't remove something as simple as an email client.
+1

Agreed. I wouldn't want to be left with a wrong idea either.

D'accord.

---

### Post by loboc on 2008-08-06
Removing a package like ubuntu-desktop doesn actually do anything.  Ubuntu-desktop doesnt contain anything but dependicies.  Evolution is one of those dependicies. The only thing that might happen to you if one of these umbrella packages is reemoved is you will miss a program that the admins at canonical feel should be included by default changes. Like they go from fspot to picasa for photo managment.  

You can always install ubuntu-desktop and run a dist-upgrade and then remove evolution again adnaseum.  

As for adding thunderbird to your panel menus are you using the slab menu or the Main Menu applet

---

### Post by kender42 on 2008-08-06
Thank you for that piece of advice. That worked. Since I can't get rid of evolution at least I can work around it.

---

### Post by billgoldberg on 2008-08-06
> **kender42 said:**
> Thank you for that piece of advice. That worked. Since I can't get rid of evolution at least I can work around it.

You can get rid of evolution, I already said how to do it.

---

### Post by stchman on 2008-08-06
> **kender42 said:**
> I tried to uninstall evolution mail because it doesn't have the features I need and it also has a conflict with thunderbird but everytime I try to unistall it I noticed it's tied to most of the desktop and os. How can I uninstall evolution without breaking everything.

```
sudo apt-get autoremove evolution
```

Evolution should not interfere with Thunderbird.  Evolution has more features than Thunderbird as well.

I used the command to remove Evolution from my laptop with no consequences.

---

