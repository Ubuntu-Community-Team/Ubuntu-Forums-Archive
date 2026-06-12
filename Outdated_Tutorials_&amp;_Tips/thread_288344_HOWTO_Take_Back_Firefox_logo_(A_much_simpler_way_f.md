---
title: "HOWTO: Take Back Firefox logo (A much simpler way for Edgy)"
date: 2006-10-29
forum: Outdated Tutorials &amp; Tips
---

### Post by bruenig on 2006-10-29
As the title says, this is a simpler way to restore the firefox icon in the task bar and on the bar at the top of the window.

Because edgy ships with a firefox logo, some symbolic linking or copying ought to do the trick.

First backup your old icons.
```

sudo mv /usr/share/pixmaps/mozilla-firefox.xpm /usr/share/pixmaps/mozilla-firefox.xpm.old
sudo mv /usr/lib/firefox/chrome/icons/default/default.xpm /usr/lib/firefox/chrome/icons/default/default.xpm.old

```

Now you can do one of two things. 

1) You can symlink these files to the logo edgy ships with.
```

sudo ln -s /usr/share/pixmaps/firefox.png /usr/share/pixmaps/mozilla-firefox.xpm
sudo ln -s /usr/share/pixmaps/firefox.png /usr/lib/firefox/chrome/icons/default/default.xpm

```

Or
 
2) You can copy the logo itself with cp.
```
sudo cp /usr/share/pixmaps/firefox.png /usr/share/pixmaps/mozilla-firefox.xpm
sudo cp /usr/share/pixmaps/firefox.png /usr/lib/firefox/chrome/icons/default/default.xpm
```

Don't do both.

And that should be it. If for whatever reason it doesn't work and you want to replace the other icons you would just do the following.
```
sudo rm /usr/share/pixmaps/mozilla-firefox.xpm
sudo mv /usr/share/pixmaps/mozilla-firefox.xpm.old usr/share/pixmaps/mozilla-firefox.xpm
sudo rm /usr/lib/firefox/chrome/icons/default/default.xpm 
sudo mv /usr/lib/firefox/chrome/icons/default/default.xpm.old /usr/lib/firefox/chrome/icons/default/default.xpm
```

---

### Post by bionnaki on 2006-10-30
cool.
how would you do it for thunderbird?

---

### Post by bruenig on 2006-10-30
> **bionnaki said:**
> cool.
how would you do it for thunderbird?

I don't have thunderbird, I guess I could install it and try to figure it out. Unless there is a real thunderbird icon somewhere on your machine, this linking obviously won't work.

---

### Post by Janux on 2006-10-30
I'm sorry for hijacking this, but anyone knows why this isn't the default behaviour of Firefox?

---

### Post by bruenig on 2006-10-30
> **Janux said:**
> I'm sorry for hijacking this, but anyone knows why this isn't the default behaviour of Firefox?

My thought is that the logo that ships with edgy is not technically part of the firefox browser. It is only used for menus and such. The blue globes are used in direct conjunction with the browser. Apparently that distinction is big enough to allow for one and not the other.

---

### Post by ShadowRage on 2006-10-30
> **Janux said:**
> I'm sorry for hijacking this, but anyone knows why this isn't the default behaviour of Firefox?

copyright issues.
yes, firefox has a copyright on the logo, and unless ubuntu releases an unpatched, direct release of firefox, they cant ship the browser with the default firefox logo intact. It's the ame reason we have the iceweasel drama with debian. It's part of mozilla's use of copyright. As if the ubuntu or debian developers patch firefox with fixes that have yet to be covered in official builds, the browser is technically not firefox anymore. Thus the firefox logo cant be officially used, that's up to the user to do or not.

Ah, IP laws, arent they just fun?

---

### Post by bruenig on 2006-10-30
> **ShadowRage said:**
> copyright issues.
yes, firefox has a copyright on the logo, and unless ubuntu releases an unpatched, direct release of firefox, they cant ship the browser with the default firefox logo intact. It's the ame reason we have the iceweasel drama with debian. It's part of mozilla's use of copyright. As if the ubuntu or debian developers patch firefox with fixes that have yet to be covered in official builds, the browser is technically not firefox anymore. Thus the firefox logo cant be officially used, that's up to the user to do or not.

Ah, IP laws, arent they just fun?

I think, and maybe this isn't true but it is relevant anyways, his question may have been on the fact that the real firefox logo is used in some places but not others. So why, if the IP laws forbid use of it, would it be allowed anywhere?

---

### Post by WiseElben on 2006-10-30
This is a much better way than [this]("http://www.ubuntuforums.org/showthread.php?t=199193"). Good work on the find.

---

### Post by Epperly on 2006-10-30
What I just do is save the icons from the internet then move it or not, doesn't matter.. properties and select it.
If you wanna move it I just move it with the other stuff, /usr/share/pixmaps
[Thunderbird Icons]("http://images.google.com/images?q=thunderbird%20icon%20png&ie=UTF-8&oe=UTF-8&client=firefox&rls=org.mozilla:en-US:unofficial&sa=N&tab=wi")

---

