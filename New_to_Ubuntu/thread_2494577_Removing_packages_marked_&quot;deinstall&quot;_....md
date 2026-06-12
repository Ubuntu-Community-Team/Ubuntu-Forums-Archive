---
title: "Removing packages marked &quot;deinstall&quot; ..."
date: 2024-01-20
forum: New to Ubuntu
---

### Post by cwmoser on 2024-01-20
I have a number of packages marked "deinstall" when I execute:  $ dpkg --get-selections | grep -i deinstall

I read that one can remove all packages marked "deinstall" via:
Removes all packages marked as "deinstall" along with their configuration files.
Command: sudo apt --purge autoremove

Is this a safe thing to do to clean up space or should one not do this?
I thought I better get advice before proceeding.

---

### Post by ian-weisser on 2024-01-20
> **cwmoser said:**
> Is this a safe thing to do to clean up space or should one not do this?

It's usually safe...

...but it's a lousy way to reclaim storage capacity. Packages are generally very small. Many are smaller than 1MB. Teeny.

To be sure it's safe, test it:

```
apt autoremove --simulate
```

- Note the lack of -purge flag. Not necessary in a test. Rarely necessary in reality.
- Note the lack of "sudo" in the test command. Another layer of protection from accidental real autoremove.

Read the output carefully to determine if the proposed autoremoval will do what you expect.

Finally, let's review man dpkg for the actual meaning of "install" and "deinstall." They are not the actual or current status of the packages. They are the status *you want them to have* at the end of all package actions, which might be in process or perhaps sometimes not even started yet:

```

Package selection states

    install
       The package is **selected** for installation.

       [...]

   deinstall
       The package is **selected** for deinstallation (i.e. we want to  remove all files, except configuration files).

```

---

### Post by Rubi1200 on 2024-01-20
> **ian-weisser said:**
> It's usually safe...

...but it's a lousy way to reclaim storage capacity. Packages are generally very small. Many are smaller than 1MB. Teeny.

To be sure it's safe, test it:

```
apt autoremove --simulate
```

- Note the lack of -purge flag. Not necessary in a test. Rarely necessary in reality.
- Note the lack of "sudo" in the test command. Another layer of protection from accidental real autoremove.

Read the output carefully to determine if the proposed autoremoval will do what you expect.

Finally, let's review man dpkg for the actual meaning of "install" and "deinstall." They are not the actual or current status of the packages. They are the status *you want them to have* at the end of all package actions (which might be in process):
+100

Always run a simulation first to make sure you are not about to completely break your system.

A thread by a user here recently found out the very hard way what happens if you do not pay attention to what is about to be removed.

---

### Post by Dennis N on 2024-01-20
More info:
How to remove a package from the autoremove list and keep the remainder for removal?  Use the **apt-mark** command:
```
sudo apt-mark manual package-name
```
Then, rerun **sudo apt autoremove**, and it will not appear in the list.

---

