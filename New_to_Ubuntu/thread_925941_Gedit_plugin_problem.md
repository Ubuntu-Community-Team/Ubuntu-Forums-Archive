---
title: "Gedit plugin problem"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by eric2323223 on 2008-09-21
Hi, I am using Ubuntu 8.04 and when I tried to install quickhighlightmode gedit plugin I met this:
1. If start gedit with "gedit", the plugin can be find in active plugin list and worked properly.
2. If start gedit with "sudo gedit", the plugin cannot be find in active plugin list.
Any suggestions?

---

### Post by Pro-reason on 2008-09-22
You oughtn't to start graphical apps with &#8220;sudo&#8221;.  Use &#8220;gksu&#8221; (or &#8220;kdesu&#8221; for KDE).
(See [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo))

I don't know if this is related to your current problem or not.

---

### Post by ad_267 on 2008-09-22
How did you install the plugin? If you put it in ~/.gnome2/gedit/plugins then it is only installed for you, not any other root users, including the root user. If you want all your plugins to be used by root too then you can link the root plugins folder to yours.

```
sudo mkdir /root/.gnome2/gedit
sudo ln -s /home/yournmame/.gnome2/gedit/plugins /root/.gnome2/gedit/plugins
```

---

### Post by eric2323223 on 2008-09-22
It works:) thanks, ad_267.

---

### Post by Pro-reason on 2008-09-22
> **ad_267 said:**
> 

```

sudo ln -s /home/yournmame/.gnome2/gedit/plugins /root/.gnome2/gedit/plugins
```

Just a note:
When giving advice on the forums, it's best if you can keep to a minimum the stuff that the users have to change.  Changing &#8220;yournmame&#8221; into the correct user name is just one more thing for them to type, and mess up.  The following is better:

```

sudo ln -s ~/.gnome2/gedit/plugins /root/.gnome2/gedit/plugins
```

The tilde (&#8220;~&#8221;) automatically expands to that user's directory.  &#8220;$HOME&#8221; does the same.  If you only want the user name itself, you can use &#8220;$USER&#8221;.

---

