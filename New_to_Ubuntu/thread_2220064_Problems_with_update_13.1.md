---
title: "Problems with update 13.1"
date: 2014-04-26
forum: New to Ubuntu
---

### Post by dcunn2002 on 2014-04-26
I converted to Ubuntu from Windows earlier this year and have been accepting updates with no problems so far.
However,  I now get this message;

"The upgrade needs a total of 87.6 M free space on disk '/boot'. Please free at least an additional 28.7 M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'."

I've tried clean and autoclean with no effect. From reading other posts It does look like I have redundant older files in boot but not confident about removing anything without advice  first.

For the record I have files & archives  ending 

-3-11.0-12-generic
-3-11.0-17-generic
-3-11.0-18-generic
-3-11.0-19-generic

what do I remove (anything not -19-?) and how?

Thanks

---

### Post by deadflowr on 2014-04-26
I have had great luck using the command from here
[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

I do suggest running the --dry-run command first, which will tell you if the kernel you need will also be removed.
This should free up more than enough space for you.

---

### Post by Bashing-om on 2014-04-26
dcunn2002; Hi !

If you are running release 13.10 ( saucy)
```

lsb_release -a

```
Then 'autoremove' will remove the old kernels while doing the cleanup.
```

sudo apt-get autoremove

```
Then make sure the system is all updated and happy:
```

sudo apt-get update
sudo apt-get upgrade

```

Please to advise us of the results.

[INDENT][INDENT]my little bit to try and help
[/INDENT][/INDENT]

---

### Post by dcunn2002 on 2014-04-26
> **Bashing-om said:**
> dcunn2002; Hi !

If you are running release 13.10 ( saucy)
```

lsb_release -a

```
Then 'autoremove' will remove the old kernels while doing the cleanup.
```

sudo apt-get autoremove

```
Then make sure the system is all updated and happy:
```

sudo apt-get update
sudo apt-get upgrade

```


[INDENT][INDENT]my little bit to try and help
[/INDENT]
[/INDENT]


That all seemd to work without error but when I then check via  the  software updater from the dash there are aparently still 64 mb of  updates to be intalled and I still get the same error message 
Please to advise us of the results.

---

### Post by Bashing-om on 2014-04-26
dcunn2002; Well !

Let's take a close look at what is:
Post back the out put - between code tags - of terminal commands:
```

df -h
df -i
sudo du -sx * | sort -n

``` the 'du' command will take a bit of time to complete, no rushing and ignore the advisories in respect to /proc ( constantly changing and 'du' can not get a handle on it; a virtual file system and not related to our present issue).
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT]thus the tale 
[INDENT][INDENT][INDENT]is told
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by dcunn2002 on 2014-04-26
> **deadflowr said:**
> I have had great luck using the command from here
[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

I do suggest running the --dry-run command first, which will tell you if the kernel you need will also be removed.
This should free up more than enough space for you.

As a non-technical newbie I didn't quite understand the above, but I followed the link from it to: 

[http://ubuntuforums.org/showthread.php?t=2191894&page=4&p=12866887&viewfull=1#post12866887](http://ubuntuforums.org/showthread.php?t=2191894&page=4&p=12866887&viewfull=1#post12866887)

and that certainly worked, so thankyou for the advice.

---

