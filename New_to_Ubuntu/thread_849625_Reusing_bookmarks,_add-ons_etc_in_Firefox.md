---
title: "Reusing bookmarks, add-ons etc in Firefox"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by t0p on 2008-07-04
I'm still using Gutsy, but I plan to install Hardy soon.

I've got a lot of bookmarks, add-ons and so on in my Firefox (version 2.0.0.14). If I save and reuse the .mozilla directory from my home directory, will this transfer everything to the new Firefox?  And will my add-ons still work in Firefox 3?

---

### Post by annda on 2008-07-04
if you upgrade all of your settings will be transfered, including FF. if you plan a clean install of Hardy, back up the directory ~/.mozilla/firefox/**some_string**.default

unpack it into the corresponding new ff directory ~/.mozilla/firefox/**some_other_string**.default

---

### Post by Vivaldi Gloria on 2008-07-04
> **t0p said:**
> I'm still using Gutsy, but I plan to install Hardy soon.

I've got a lot of bookmarks, add-ons and so on in my Firefox (version 2.0.0.14). If I save and reuse the .mozilla directory from my home directory, will this transfer everything to the new Firefox?  And will my add-ons still work in Firefox 3?

If I were you, I'll first upgrade to ff3 in gutsy and use the "export bookmarks to a file" option of ff3 to save your bookmarks to a file to be on the safe side. As an added benefit, first upgrading to ff3 in gutsy will guarantee that your .mozilla folder works with ff3. 

About add-ons. Not all ff2 add-ons work with ff3. So check your add-ons individually.

---

### Post by Bubba64 on 2008-07-04
Nightly tester tools in the Mozilla add on link will force anything to work in FF3 if they are already installed.

---

### Post by t0p on 2008-07-04
> **Vivaldi Gloria said:**
> If I were you, I'll first upgrade to ff3 in gutsy and use the "export bookmarks to a file" option of ff3 to save your bookmarks to a file to be on the safe side. As an added benefit, first upgrading to ff3 in gutsy will guarantee that your .mozilla folder works with ff3. 


How do I upgrade to FF3?

---

### Post by Vivaldi Gloria on 2008-07-04
> **t0p said:**
> How do I upgrade to FF3?

I don't know. But I remember seeing a lot of threads about it. Search this forum for

```
gutsy firefox 3
```

---

### Post by ayenack on 2008-07-04
You can copy the bookmarks like this. Open a Terminal.

**cp ~/.mozilla/firefox/profile/bookmarks.html ~/Desktop/** (This will copy the bookmarks to your desktop.)

Then copy this onto a USB drive or CD/DVD Floppy whatever. Once you've installed Ubuntu 8.04 copy the file back to your desktop and do this.
[B]
cp ~/Desktop/bookmarks.html ~/.mozilla/firefox/profile/[/B]

I think but am not sure that Ubuntu 8.04 will import the bookmarks during install though. Many of the add-ons that work in FF2 will not work with FF3 so the add-on situation is hit and miss. You'll have to see which of the add-ons you use are available to you.

You could alway uninstall FF3 and install FF2 on Ubuntu 8.04 if you want to use the same add-ons.

---

### Post by Bubba64 on 2008-07-04
> **Vivaldi Gloria said:**
> If I were you, I'll first upgrade to ff3 in gutsy and use the "export bookmarks to a file" option of ff3 to save your bookmarks to a file to be on the safe side. As an added benefit, first upgrading to ff3 in gutsy will [COLOR="Red"]*guarantee*[/COLOR] that your .mozilla folder works with ff3. 

About add-ons. Not all ff2 add-ons work with ff3. So check your add-ons individually.

Your not GUARANTEEING much of anything are you.

---

### Post by silkstone on 2008-07-04
If you install the Foxmarks add-on to FF (2 or 3) that will upload your bookmarks to a server and synchronise them with any other machine you use (Windows or Ubuntu), and with any updated version of FF or Ubuntu.

This is just an alternative to the methods already suggested, and it does allow synchronisation between different machines in the future.

---

### Post by Vivaldi Gloria on 2008-07-04
> **Bubba64 said:**
> Your not GUARANTEEING much of anything are you.

I meant that when you copy the .mozilla folder of a ff3@gutsy to ff3@hardy then it will work.

So I suggest that instead of

```
ff2@gutsy ---> ff3@hardy
```

do

```
ff2@gutsy ---> ff3@gutsy ---> ff3@hardy
```

What are you not happy with?

---

### Post by Bubba64 on 2008-07-04
> **Vivaldi Gloria said:**
> I meant that when you copy the .mozilla folder of a ff3@gutsy to ff3@hardy then it will work.

So I suggest that instead of

```
ff2@gutsy ---> ff3@hardy
```

do

```
ff2@gutsy ---> ff3@gutsy ---> ff3@hardy
```

What are you not happy with?

I'm just giving you a hard time when it comes to a drastic move such as changing distros the word guarantee may give a false hope and cause somebody to act without really understanding, Personally I try to keep my advice or answers to problems that can easily be fixed, and not result in a whole loss of important stuff. :)

---

