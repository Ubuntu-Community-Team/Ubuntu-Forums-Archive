---
title: "Firefox 3.0 Flash Issue"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by RetroDemon on 2008-06-18
I use firefox 2 with no problems, I recently upgraded to Firefox 3.0 and cant seem to get any flash things to work, videos or games. Here is what i see:
[IMG]http://i24.photobucket.com/albums/c5/mafiaxman/Screenshot-1.png[/IMG]

when i right click it, it just brings up something for Gnash, but it dont do jack. 

Everything on Firefox 2 still works though, so it dont make sence. 

Help

---

### Post by RetroDemon on 2008-06-18
I even manually installed Flash 9 and the Gnash still wont let it play, nor can i uninstall Gnash.

---

### Post by stchman on 2008-06-18
I use the proprietary Flash plugin.

```
sudo apt-get install flashplugin-nonfree
```

Works like a charm in Firefox 3.

---

### Post by RetroDemon on 2008-06-18
Didnt work, still doesnt the same blank spot thing.

---

### Post by RetroDemon on 2008-06-18
Am i stuck with using Firefox 2? Ive tried 3 or 4 diffrent ways to fix Firefox 3 flash issue, non seem to work.

---

### Post by Kingsley on 2008-06-18
Maybe you accidentally installed gnash some while ago. Try this.

```
sudo apt-get remove gnash
```
```
sudo apt-get reinstall flashplugin-nonfree
```

---

### Post by RetroDemon on 2008-06-18
that first code worked, i didnt need to use the second code, so i guess i had both, but Gnash was overtaking. Thanks

---

### Post by stchman on 2008-06-18
> **RetroDemon said:**
> that first code worked i think, but the second code when put in says:

E: Invalid Operation reinstall

Just do this:

```
sudo apt-get install flashplugin-nonfree
```

There is no reinstall option to my knowledge.

---

### Post by Kingsley on 2008-06-18
haha, my mind was stuck on YUM. I think I meant sudo apt-get install --reinstall flashplugin-nonfree. At least the OP's probably is solved. :)

---

### Post by kevinlang21 on 2008-06-18
I also have a similar issue. The only difference is that I don't even get a blank space. It says I don't have the latest version of flash installed. 

I don't have gnash installed, and according to my terminal, I have the latest version of flashplugin-nonfree. 

When I try to view flash, it says I don't have the latest version of flash installed, when things work fine in firefox 2. When I click on the install missing plugins button on the firefox popup, I end up with "Firefox could not install this item because "install-gl0..rdf" (provided by the item) is not well-formed or does not exist. Please contact the author about this problem." 

Could anyone help please?

Thanks

---

### Post by alienexplorers on 2008-06-18
I downloaded flashplayer 10 at the Adobe website.  Installed it and Flash video's run great now.

---

### Post by kevinlang21 on 2008-06-18
what directory did you install it to and how did you install it? thanks

---

