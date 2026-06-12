---
title: "Disable run Dropbox for some user"
date: 2009-01-29
forum: Outdated Tutorials &amp; Tips
---

### Post by orrie on 2009-01-29
I will now show you guys how to disable the nautilus-plugin Dropbox for some users and enable it for some users.

1. Add an group (dropbox).
2. Change owner on libary-files.
3. Change mode on libary-files.
4. Add the user that want's to use Dropbox to an group.

[color="RED"]**Be aware that you have to be root before doing this.**[/color]

Do this in the terminal:
```

$ sudo addgroup dropbox
$ sudo chown root:dropbox /usr/lib/nautilus/extensions-2.0/libnautilus-dropbox.*
$ sudo chmod 640 /usr/lib/nautilus/extensions-2.0/libnautilus-dropbox.*
$ sudo adduser <user> dropbox

```

<user> is the username for the user that want's to be running Dropbox at startup.
If there are more users that want's to use Dropbox do step 4 again.

And if you want a script doing this for you, you can check it out [[color="RED"]here[/color]](http://projects.orrie.org/?p=news&category=script&project=disable-dropbox&do=read).

---

### Post by jaygo on 2009-02-19
how would you disable dropbox for root?

---

### Post by orrie on 2009-02-19
> **jaygo said:**
> how would you disable dropbox for root?

In this guide I have shown how to disable it for normal users.
Since the owner of the files matching /usr/lib/nautilus/extensions-2.0/libnautilus-dropbox.* is root in the group dropbox you wouldn't be able to disable it for the root user.

---

### Post by binbash on 2009-02-20
I was looking for this, helped me a lot

---

