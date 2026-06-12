---
title: "Installing Firefox 2"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by lolwhites on 2008-04-27
After upgrading, I want to install Firefox 2 so I can keep all my extentions. It's there in the repositories, but when I try to start at after installation, Firefox 3b5 starts. Even typing "firefox-2" into a command line starts Firefox 3. So how can I install and start Firefox 2?

---

### Post by unbuntued on 2008-04-27
> **lolwhites said:**
> After upgrading, I want to install Firefox 2 so I can keep all my extentions. It's there in the repositories, but when I try to start at after installation, Firefox 3b5 starts. Even typing "firefox-2" into a command line starts Firefox 3. So how can I install and start Firefox 2?
First you need to get it from the repository. In the terminal type:
```
sudo apt-get install firefox-2
```

Now that it's installed, you can run ```
firefox-2
```

Edit: You could also try uninstalling firefox 3.

---

### Post by hyper_ch on 2008-04-27
you could also modifiy the extensions and make them compatible with ff3 by altering the version numbers they work on :)

---

### Post by unbuntued on 2008-04-27
> **hyper_ch said:**
> you could also modifiy the extensions and make them compatible with ff3 by altering the version numbers they work on :)
Is that enough to get any extension to work on Firefox 3?

---

### Post by lolwhites on 2008-04-27
ubuntued - I tried installing Firefox 2 in the way you suggest, but the launcher and command still start Firefox 3.
Before I uninstall FF3, where do my extensions live and how do I avoid inadvertantly uninstalling them too?
hyper_ch - how do I modify the extensions? Thanks.

---

### Post by hyper_ch on 2008-04-27
> **unbuntued said:**
> Is that enough to get any extension to work on Firefox 3?

It worked on those I wanted to get work.... the programming behind it is in most cases not bound to the FF version... well, for moste extensions I say it works...

Stored in

~/.mozilla/firefox/[PROFILE]/extensions

In there you see folders for each extension (unfortunately does the foldername not correspond with the plugin name) and inside you'll find somewhere a .jar file. that's the compressed extension. That needs to be uncompressed, then the according version needs to be changed and packed together again... I know, it's tiresome but most extensions can be made work that way.

However, I would find a thing like the WoW plugin editor good, in which you can disable the outdated versions and load them anyway. Maybe somebody could write a plugin for that. :)

---

### Post by ekmon1582 on 2008-04-27
> **unbuntued said:**
> First you need to get it from the repository. In the terminal type:
```
sudo apt-get install firefox-2
```

Now that it's installed, you can run ```
firefox-2
```

Edit: You could also try uninstalling firefox 3.

Would it be like that for any application?

---

### Post by unbuntued on 2008-04-27
> **lolwhites said:**
> ubuntued - I tried installing Firefox 2 in the way you suggest, but the launcher and command still start Firefox 3.
Before I uninstall FF3, where do my extensions live and how do I avoid inadvertantly uninstalling them too?
hyper_ch - how do I modify the extensions? Thanks.
You're firefox preferences live in:
```
~/.mozilla/firefox/
```
I believe (not definitely sure though) that uninstalling FF3 will not remove any of your extensions / preferences.
But before you do so, wait for someone else to confirm this statement.

> **ekmon1582 said:**
> Would it be like that for any application?
Yes it would.
However if you're installing some application from outside the repository, you need to go through some extra steps.

---

### Post by Joshua Netterfield on 2008-04-27
> **ekmon1582 said:**
> Would it be like that for any application?

The best way would be to go to Add/Remove Programs in the Applications menu, and search for Firefox 2 in all available applications. That is more foolproof.

---

### Post by ekmon1582 on 2008-04-27
Thanks guys.

---

### Post by unbuntued on 2008-04-27
> **Joshua Netterfield said:**
> The best way would be to go to Add/Remove Programs in the Applications menu, and search for Firefox 2 in all available applications. That is more foolproof.
Add/Remove programs or the Synaptic Package Manager both use apt-get.

---

### Post by lolwhites on 2008-04-27
I just installed the [Nightly Tester Tools]("https://addons.mozilla.org/en-US/firefox/addon/6543") extension and all my extensions seem to be working now.

---

### Post by gn2 on 2008-04-27
There's a link in my sig which might be useful.

---

### Post by hyper_ch on 2008-04-27
> **lolwhites said:**
> I just installed the [Nightly Tester Tools]("https://addons.mozilla.org/en-US/firefox/addon/6543") extension and all my extensions seem to be working now.

That's cool :)

---

