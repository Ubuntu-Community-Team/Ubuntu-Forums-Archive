---
title: "How to completely remove empathy"
date: 2015-11-26
forum: New to Ubuntu
---

### Post by fangorn2 on 2015-11-26
I would like to completely remove empathy with Synaptic or apt-get (and eventually be able to use other IRC clients).
I am not sure if I should also remove dependencies as well.
Using either 'Mark for removal' or 'Mark for complete removal', Synaptic would leave unchecked packages empathy-common and telepathy-idle.
According to [this article]("http://installion.co.uk/ubuntu/vivid/main/e/empathy/uninstall/index.html") empathy-common is included in the list of dependencies. On the other hand I suspect there is a reason if Synaptic would not remove some packages that look related to empathy.

I would not know how to use apt-get.
Commands suggested in the above article look different from those suggested in the [Ubuntu apt-get howto]("https://help.ubuntu.com/community/AptGet/Howto").

What would you suggest to do?

Many thanks in advance

---

### Post by ajgreeny on 2015-11-26
If you use synaptic to remove it, does synaptic list other packages that will be removed as well as empathy?

Empathy has a lot of dependencies.
I use xubuntu and do not have empathy installed, but it pulls in a lot of packages if I want to install it, but you may already have if you use ubuntu with unity.

In any case, you can remove empathy with synaptic, then use the Status filter in the left hand column to show the **Installed (auto-removable)** packages which can safely be removed as well, which does exactly the same as terminal command ```
sudo apt-get autoremove
```

---

### Post by fangorn2 on 2015-11-26
Many thanks.
I marked empathy for complete removal with Synaptic and let it make the job.
The following packages also have been automatically included by Synaptic for removal and consequently removed:

- nautilus-sendto-empathy
- account-plugin-aim
- account-plugin-yahoo
- account-plugin-jabber
- account-plugin-salut


After removal, with Status filter selected in the left hand column to show the **installed **packages, the list still includes the following packages:

- empathy-common
- audium-theme-ubuntu
- gnome-contacts
- telepathy-idle


Instead, with Status filter to show the **Installed (auto-removable)** packages the list includes two packages:

- empathy common
- gnome-contacts

---

### Post by ajgreeny on 2015-11-26
Unless you are very short of space I would not worry about removing those two packages too much.

As I said, I don't use empathy and have no idea whether or not gnome-contacts is a dependency of anything else that you do not have installed but might use instead of empathy in future, and therefore might be useful.

You can, however, definitely remove empathy-common as without empathy it is no longer needed.

---

