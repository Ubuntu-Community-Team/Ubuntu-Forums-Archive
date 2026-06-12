---
title: "File Permissions in Apache"
date: 2012-05-18
forum: New to Ubuntu
---

### Post by andperry on 2012-05-18
I have a LAMP server running on Ubuntu Server 12.04. Some of my PHP scripts require write access to files and/or directories. I seem to only be able to get them to work by setting world write access on everything (i.e. 666 for files and 777 for directories). Whilst the security aspect is not a big issue in this particular environment, it nevertheless does not seem right to have to do this.

I've got copies of the same web sites on a remote host with a web hosting company - the files are all owned by my user and the attributes all set to 644 for files and 755 for directories. This seems more sensible.

Presumably I am missing something in terms of the Apache server and access rights. Any ideas?

Thanks.

---

### Post by Lars Noodén on 2012-05-18
The default group is www-data, so if your files are in that group and that group has write permission, then your script should be able to write to it.

```

sudo chgrp www-data /var/www/*somefile.txt*
sudo chmod g=rw /var/www/*somefile.txt*

```

Or if you want to use a different group, you can use the [SuexecUserGroup](https://httpd.apache.org/docs/2.2/mod/mod_suexec.html#suexecusergroup) directive.

---

### Post by andperry on 2012-05-19
Many thanks for the reply. I've changed the group to www-data for all items and changed the chmod settings to 664 for files and 775 for directories. It now seems to work fine.

---

### Post by Lars Noodén on 2012-05-19
One more thing since we're dealing with the group www-data: Try to follow the Write XOR Execute (W^X) principle and turn off scripting for the directories in question.  Directories with scripts should not be writable by www-data and directories that are writable should not be able to run scripts.

Remember that those files and directories will be writable by the web server even if things go wrong.  So if there is an exploit in your script, the files and directories will be available to the exploited script.  If W^X is followed, then the worst that can happen is that data is messed with.  Otherwise, the directory can serve as a platform for the intruder to write new scripts to further explore and exploit your system.

---

