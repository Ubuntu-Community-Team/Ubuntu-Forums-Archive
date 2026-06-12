---
title: "Error Messages following ugrading of Software"
date: 2019-01-21
forum: New to Ubuntu
---

### Post by opeoluwa5520nigeria on 2019-01-21
dpkg: error: unable to create new file ' /var/lib/dpkg/info/format-new': No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)

The above two lines are the error messages that I get following upgrading of software. Please assist in addressing this issue.

Thanks in advance.

---

### Post by #&amp;thj^% on 2019-01-21
check if a file named "format-new" exists in "/var/lib/dpkg/info/".
```

ls -l /var/lib/dpkg/info/format-new
```

If format-new does not exist, create a new file named format-new in " /var/lib/dpkg/info/" directory.
```

sudo touch /var/lib/dpkg/info/format-new  
sudo apt update  
sudo apt upgrade
```

---

