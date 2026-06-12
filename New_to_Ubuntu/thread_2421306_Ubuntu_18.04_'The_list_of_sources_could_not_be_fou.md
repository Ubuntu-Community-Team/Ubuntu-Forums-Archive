---
title: "Ubuntu 18.04 'The list of sources could not be found'"
date: 2019-06-19
forum: New to Ubuntu
---

### Post by jch5625 on 2019-06-19
I am supporting a user who is on Ubuntu 18.04. The issue we are encountering is when trying to install anything we get the following error:
Terminal:

```

E: Conflicting values set for option Signed-By regarding source https://packages.cloud.google.com/pt/ cloud-sdk: /usr/share/keyrings/cloud.google.gpg !=
E: The list of sources could not be read.
E: Conflicting values set for option Signed-By regarding source https://packages.cloud.google.com/pt/ cloud-sdk: /usr/share/keyrings/cloud.google.gpg !=
E: The list of sources could not be read.

```

This error occurs on any command to install software while using a users admin account.

Tried the following commands:
```

sudo apt-get install net-tools

```
```

sudo apt upgrade

```

The user tried various other commands and reported having the same issue.

Please help as I have no idea what might be wrong.

---

### Post by TheFu on 2019-06-20
Remove the google PPA from the APT sources. After removal, to a **sudo apt update/upgrade** cycle.  If there aren't any warning/error messages, you've found the issue.

cloud.google.com is not part of Ubuntu.

---

