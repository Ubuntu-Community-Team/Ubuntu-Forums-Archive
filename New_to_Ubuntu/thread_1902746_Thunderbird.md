---
title: "Thunderbird"
date: 2011-12-31
forum: New to Ubuntu
---

### Post by corncob on 2011-12-31
My friend has a problem with Thunderbird 9.01 and I don't know what to tell her.  Please help:
> The problem is that my accounts are not being displayed in the leftmost tab. When I start Tbird, the tab is completely blank. Before the update, all accounts appeared with all folders (inbox, sent, trash, etc). Now nothing.

The only way I have found to open up a tab for an account is to send myself an email and click on the email alert message when it pops up.


---

### Post by the.phantom on 2011-12-31
see if this helps?
in tbird at the top 

view
folders
all

---

### Post by rectec794613 on 2011-12-31
If that doesn't work she could always clear out Thunderbird's configuration in her home folder. A reinstall could also help...
In the terminal:
```
rmdir /home/USERNAME/.thunderbird
```

To reinstall:
```
sudo apt-get install --reinstall thunderbird
```

Hope this helps.

-Rob

---

### Post by corncob on 2012-01-01
Thanks guys and gals.  But she has already found a fix on another forum, [http://gsfn.us/t/2klhf](http://gsfn.us/t/2klhf) .  "Delete all .json files".  Obscure, huh?

---

