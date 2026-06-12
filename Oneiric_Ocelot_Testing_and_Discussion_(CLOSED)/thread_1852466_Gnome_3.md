---
title: "Gnome 3?"
date: 2011-09-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by burpootus on 2011-09-30
I installed gnome-shell and gnome tweak tool to try out gnome 3. I got the added entries in LightDM to log into after this, but whenever I choose Gnome I log into a session that looks exactly like Ubuntu. It has the unity dash and the same wallpaper. How can I log into a pure Gnome 3 session?

---

### Post by dino99 on 2011-09-30
install gnome-session-fallback

---

### Post by Merk42 on 2011-09-30
> **dino99 said:**
> install gnome-session-fallback
That's required to run GNOME Shell?

---

### Post by Harry33 on 2011-09-30
> **Merk42 said:**
> That's required to run GNOME Shell?

Gnome-shell recommends gnome-session-fallback.
So that gnome-panel could be used, if gnome-shell cannot be loaded.

Also gnome-session suggests gnome-session-fallback

---

### Post by Mr. Picklesworth on 2011-09-30
> **burpootus said:**
> I installed gnome-shell and gnome tweak tool to try out gnome 3. I got the added entries in LightDM to log into after this, but whenever I choose Gnome I log into a session that looks exactly like Ubuntu. It has the unity dash and the same wallpaper. How can I log into a pure Gnome 3 session?

It's possible that you have some residual settings or autostart entries that are telling gnome-session to load Compiz with the Unity plugin enabled. Are you running with a fresh install of Oneiric, or have you upgraded from Natty?

The wallpaper will be the same either way; Unity and Gnome Shell are both running the same software except their respective window managers. That also means you'll need to change your theme to Adwaita if you want Gnome Shell to feel right, and you can do that now with the theme selector under Appearance in System Settings.

---

### Post by Blasphemist on 2011-09-30
I think you've made a bad change in gnome tweak. You should see the same wallpaper but you should see the top panel in shell and not the unity launcher. Do you know what all you changed in gnome tweak? You should be able to choose gnome from the session type at the LDM login screen to get the gnome shell.

---

### Post by burpootus on 2011-09-30
> **Mr. Picklesworth said:**
> It's possible that you have some residual settings or autostart entries that are telling gnome-session to load Compiz with the Unity plugin enabled. Are you running with a fresh install of Oneiric, or have you upgraded from Natty?

The wallpaper will be the same either way; Unity and Gnome Shell are both running the same software except their respective window managers. That also means you'll need to change your theme to Adwaita if you want Gnome Shell to feel right, and you can do that now with the theme selector under Appearance in System Settings.

I upgraded, I actually don't remember how many versions back I've upgraded from, but I haven't done a clean install in a long time. You may be onto something, I hope I can figure it out.

---

### Post by burpootus on 2011-09-30
> **Blasphemist said:**
> I think you've made a bad change in gnome tweak. You should see the same wallpaper but you should see the top panel in shell and not the unity launcher. Do you know what all you changed in gnome tweak? You should be able to choose gnome from the session type at the LDM login screen to get the gnome shell.

I installed gnome tweak, but I haven't been in the gnome 3 environment to know how to tweak it, so I assume it's default.

---

### Post by burpootus on 2011-09-30
I logged into gnome and disabled unity in ccsm, it was no different than disabling it in a ubuntu login. I can't detect one bit of difference between logging into a gnome session or a ubuntu session.

---

### Post by Harry33 on 2011-10-01
> **burpootus said:**
> I logged into gnome and disabled unity in ccsm, it was no different than disabling it in a ubuntu login. I can't detect one bit of difference between logging into a gnome session or a ubuntu session.

You can change the settings in the display manager (lightDM), which controls the sessions you choose.
These are in the file /etc/lightdm/lightdm.conf

```
gksu gedit /etc/lightdm/lightdm.conf
```

Then set this wording:
```
[SeatDefaults]
user-session=gnome
```

After that logout and login and you can be sure you use the gnome session.
Perhaps you should reinstall packages:
- gnome-session
- gnome-session-bin
- gnome-session-common
- gnome-session-fallback
- gnome-shell

Gnome-shell (the default Gnome3 desktop environment) does not use Compiz nor metacity, instead it uses clutter and mutter.

If the above does not help, what happens if you choose classic ubuntu (no effects) from login screen (lightdm)?

---

### Post by volkerbradley on 2011-10-01
> **burpootus said:**
> I installed gnome-shell and gnome tweak tool to try out gnome 3. I got the added entries in LightDM to log into after this, but whenever I choose Gnome I log into a session that looks exactly like Ubuntu. It has the unity dash and the same wallpaper. How can I log into a pure Gnome 3 session?
Had the same problem.  Log out. 
When you get back to the login screen you will see a spoked wheel to the right of your name.  Click on that. Choose Gnome.  Works well.

---

### Post by burpootus on 2011-10-01
> **Harry33 said:**
> You can change the settings in the display manager (lightDM), which controls the sessions you choose.
These are in the file /etc/lightdm/lightdm.conf

```
gksu gedit /etc/lightdm/lightdm.conf
```

Then set this wording:
```
[SeatDefaults]
user-session=gnome
```

After that logout and login and you can be sure you use the gnome session.
Perhaps you should reinstall packages:
- gnome-session
- gnome-session-bin
- gnome-session-common
- gnome-session-fallback
- gnome-shell

Gnome-shell (the default Gnome3 desktop environment) does not use Compiz nor metacity, instead it uses clutter and mutter.

If the above does not help, what happens if you choose classic ubuntu (no effects) from login screen (lightdm)?

I edited the lightdm.conf file, but that result is no different than selecting gnome at login. I completely removed and reinstalled the packages you suggested, with the same result. I did find that mutter was not installed, but installing it yielded no different results. I'm thinking some other packages may not have been installed as well. There is no clutter package per se, but several libclutter this or thats installed, so it's probably ok.

---

### Post by Harry33 on 2011-10-01
> **burpootus said:**
> I edited the lightdm.conf file, but that result is no different than selecting gnome at login. I completely removed and reinstalled the packages you suggested, with the same result. I did find that mutter was not installed, but installing it yielded no different results. I'm thinking some other packages may not have been installed as well. There is no clutter package per se, but several libclutter this or thats installed, so it's probably ok.

These arethe correct ones (though you will have them if you have gnome-shell installed).
Mutter packages = gir1.2-mutter-3.0, libmutter0, mutter-common
Clutter packages = gir1.2-clutter-1.0, libclutter-1.0-0

---

### Post by 23dornot23d on 2011-10-01
Open a terminal and type in ....

**gnome-shell --replace**

What does it show in the terminal  ...... ?

---

### Post by burpootus on 2011-10-01
> **23dornot23d said:**
> Open a terminal and type in ....

**gnome-shell --replace**

What does it show in the terminal  ...... ?

Hey! That certainly changed things. Here's the terminal response:

Window manager warning: Log level 16: Unable to register authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject
Window manager warning: Log level 16: Error registering polkit authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject (polkit-error-quark 0)
      JS LOG: GNOME Shell started at Sat Oct 01 2011 22:48:11 GMT-0500 (CDT)


So I think I am in gnome 3 now. The wording and icons on the top bar aren't displaying correctly. I loaded the adwaita theme, but it's still messed up.

---

### Post by VinDSL on 2011-10-02
> **burpootus said:**
> I think I am in gnome 3 now. The wording and icons on the top bar aren't displaying correctly. I loaded the adwaita theme, but it's still messed up.
Welcome to Gnome Shell!  :D

(Sorry, I couldn't resist)

GS takes some getting used to, just like Unity.

Sounds like you're on your way...

---

### Post by Mr. Picklesworth on 2011-10-02
> **burpootus said:**
> Hey! That certainly changed things. Here's the terminal response:

Window manager warning: Log level 16: Unable to register authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject
Window manager warning: Log level 16: Error registering polkit authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject (polkit-error-quark 0)
      JS LOG: GNOME Shell started at Sat Oct 01 2011 22:48:11 GMT-0500 (CDT)


So I think I am in gnome 3 now. The wording and icons on the top bar aren't displaying correctly. I loaded the adwaita theme, but it's still messed up.

Are you using an ATI graphics card? You'll need the open source driver, instead of the proprietary fglrx driver, because there is [a bug]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/838577") in the proprietary driver. That bug _may_ be fixed in Catalyst 11.9, though I haven't tested it yet.

---

### Post by burpootus on 2011-10-02
> **Mr. Picklesworth said:**
> Are you using an ATI graphics card? You'll need the open source driver, instead of the proprietary fglrx driver, because there is [a bug]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/838577") in the proprietary driver. That bug _may_ be fixed in Catalyst 11.9, though I haven't tested it yet.

I am using an ATI graphics card and I was using the fglrx driver. I tried the open source driver but I still had garbled menus.

I appreciate everyone's help, but I think for me the bigger issue is the direction gnome 3 and ubuntu unity have gone. I'm a desktop computer user and both of these options seem like a step backwards. I like the fact that they are gtk3 based and therefore more technically capable, but I just want to click a menu and open the program I'm after. I was initially turned off with 11.04 and I thought I'd be open minded and try unity again. I didn't go to the trouble of installing gnome 3 on 11.04 to try it out, although I knew about what it was like from reading about it. I used gnome 2 with a downgraded version of compiz to maintain what I was familiar with and worked. But it's time now to break from gnome 2, so I installed the xubuntu desktop. With ubuntu, the whole thing seems strange to me. I can't see what they are targeting with the direction they've gone. I use an android tablet for my portable computing needs, and it seems this new ubuntu direction is aimed towards that sort of platform, and yet unity requires hardware resources that a tablet can't provide. Effective use of unity requires a lot of keyboard interaction and it seems like people figured out in the early 90's that pointing and clicking with a mouse was the way to go. Oh well, xubuntu seems pretty sweet...for now.

---

