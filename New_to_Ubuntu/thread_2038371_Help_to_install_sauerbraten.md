---
title: "Help to install sauerbraten"
date: 2012-08-05
forum: New to Ubuntu
---

### Post by jukingeo on 2012-08-05
> **oldos2er said:**
> Copy and paste this in a terminal: ```
sudo apt-get update && sudo apt-get install sauerbraten
```
If there are any errors please copy and paste them in full here.

Yup, I sure did get an error when trying this:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.

What do you make of that?

Of course the game didn't install.

---

### Post by oldos2er on 2012-08-06
Post moved to its own thread.

You might want to try a different server. Run ```
gksu software-properties-gtk
``` and try either the main server or server for US.

Also see [http://askubuntu.com/questions/142508/how-to-fix-5-no-address-associated-with-hostname-error-while-updating](http://askubuntu.com/questions/142508/how-to-fix-5-no-address-associated-with-hostname-error-while-updating)

---

