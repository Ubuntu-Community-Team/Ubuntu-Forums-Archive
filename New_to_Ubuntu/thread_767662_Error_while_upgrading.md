---
title: "Error while upgrading"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by dannytatom on 2008-04-25
```

Setting up lshw (02.12.01-2ubuntu1) ...
Setting up mtr-tiny (0.72-2ubuntu1) ...
Setting up nano (2.0.7-1ubuntu1) ...
///usr/share/gnome/help/blackjack/el/blackjack.xml:402: parser error : Entity '&#914;&#959;&#942;&#952;&#949;&#953;&#945;' not defined
                  <para><guimenuitem>&#928;&#961;&#959;&#964;&#953;&#956;&#942;&#963;&#949;&#953;&#962;&&#914;&#959;&#942;&#952;&#949;&#953;&#945;;</gui
                                                                           ^

```

It's kept going with the upgrade, but is this anything I should look in to?

---

### Post by Rocket2DMn on 2008-04-26
It seems like that should be OK, it looks like it's talking about something in a help file.  Can you tell us how it went?   Did it work out ok?

---

### Post by tyler_roach on 2008-05-10
I had the same problem the original poster had. I did a fresh install of hardy KDE4, then tried to install Gnome via aptitude install ubuntu-desktop.

The only way I could resolve the problem was going into the XML file mentioned in the error message, and deleting the item causing the error.

---

