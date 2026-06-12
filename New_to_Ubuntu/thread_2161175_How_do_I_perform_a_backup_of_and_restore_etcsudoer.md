---
title: "How do I perform a backup of and restore /etc/sudoers file?"
date: 2013-07-09
forum: New to Ubuntu
---

### Post by regency on 2013-07-09
Could someone show me how to:

1. backup
2. restore

the /etc/sudoers file?

I need some handholding.

Thanks in advance.

---

### Post by Kopkins on 2013-07-09
Fairly easy. Just do it from command line.

Open terminal.

Use the 'sudo' command. This lets you use the administrative privileges. 

Use the copy command ```
'cp /file/to/copy/ /path/to/new/copy'
```

So we start with sudo, then use the cp command to take the /etc/sudoers file and make a copy of it somewhere else like /etc/sudoers.backup

```

sudo cp /etc/sudoers /etc/sudoers.backup

```

Now if you use the list command 'ls' you should be able to see both files in the /etc/ directory. We'll use 'grep' to filter the results.

```

ls /etc/

```

As you can see there's tons of stuff. So pipe it with '|' to grep and find a match.

```

ls /etc/ | grep sudoers

```

To restore it, you simply have to move 'mv' the backup file back into place. So replace the 'cp' command with 'mv' and reverse the files.

```

sudo mv /etc/sudoers.backup /etc/sudoers

```

Hope this helps. Good Luck!

Kopkins

---

### Post by regency on 2013-07-09
Thank you, Kopkins, for the detailed explanation :)

---

### Post by Kopkins on 2013-07-10
No problem! Glad to help!

Kopkins

---

