---
title: "Ubuntu's Newbie asking a silly thing"
date: 2012-07-03
forum: New to Ubuntu
---

### Post by czgirb on 2012-07-03
I read an article which say:
==== **Make sure you have access to this path: /home/***/xyz/** =====
What I want to ask is:
... How can we go to the **xyz folder**?
... How can we know we have access to that path or not?

If the file was downloaded and placed in the **/home/***/Downloads**, for example **xyz.xml** file, how can we install that file through Terminal?
[B]* cd Downloads
* sudo install xyz.xml[/B]
Please revised the command if it's not right

Please help ...

---

### Post by Grenage on 2012-07-03
> **czgirb said:**
> I read an article which say:
==== **Make sure you have access to this path: /home/***/xyz/** =====
What I want to ask is:
... How can we go to the **xyz folder**?
... How can we know we have access to that path or not?

If the file was downloaded and placed in the **/home/***/Downloads**, for example **xyz.xml** file, how can we install that file through Terminal?
[B]* cd Downloads
* sudo install xyz.xml[/B]
Please revised the command if it's not right

Please help ...

Well I assume that *xyz* is just a placeholder for a directory name, rather than the actual directory name; it's much like *** for the user.

You would get there in a terminal using:

```
cd /home/*<user_name>*/*<directory_name>*
```

Or using the ~ shortcut, whih will use the current user's home directory:

```
cd ~/*<directory_name>*
```

How to run the file, that depends on what it is.  If it's an executable, you'll likely need to make it executable:

```
chmod +x ~/downloads/*<file_name>*
```

You can then run it (while in that directory) using:

```
./*<filename>*
```

---

### Post by codemaniac on 2012-07-03
> **czgirb said:**
> I read an article which say:
==== **Make sure you have access to this path: /home/***/xyz/** =====
What I want to ask is:
... How can we go to the **xyz folder**?

You can use cd command to navigate to different directories .
```
cd /path/to/xyx
```

> ... How can we know we have access to that path or not?
Please refer the below link to know more about linux file system permissions .Every file or directory in a Linux file system has an set of permission policies associated with it .That is who are the authorised users or group that can read , write or execute them .
[http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html)


> If the file was downloaded and placed in the **/home/***/Downloads**, for example **xyz.xml** file, how can we install that file through Terminal?
[B]* cd Downloads
* sudo install xyz.xml[/B]
Please revised the command if it's not right

Please help ...
In Ubuntu software installation is a breeze .
Have a look at the below link .
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

