---
title: "Removing Firefox 3 Beta (8.04)"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by viniciuscarvalho on 2008-05-06
Hello there! It was a very unpleasant surprise upgrading to 8.04 and getting a beta software :(
Most of my extensions do not work, and no java support, I searched the forum, tried to copy the files to .mozilla, changed the permissions, nothing. 
So, I just want my 2.0 firefox back :). Is the firefox2 package the old version? Does it replace my icons and shortcuts?

Best regards

---

### Post by aysiu on 2008-05-06
Close Firefox and paste this command in [the terminal](http://www.psychocats.net/ubuntu/firefox): ```
sudo apt-get remove firefox-3.0 && sudo apt-get update && sudo apt-get install firefox-2
```

---

### Post by glennoph on 2008-05-07
Thanks for the commands.
There is one more step that may be helpful that i found.
Create a link from firefox-2 to firefox, for example:

[FONT="Courier New"]
sudo ln -s /usr/bin/firefox-2 /usr/bin/firefox[/FONT]

---

### Post by aysiu on 2008-05-07
> **glennoph said:**
> Thanks for the commands.
There is one more step that may be helpful that i found.
Create a link from firefox-2 to firefox, for example:

[FONT="Courier New"]
sudo ln -s /usr/bin/firefox-2 /usr/bin/firefox[/FONT]
Good to know.

---

