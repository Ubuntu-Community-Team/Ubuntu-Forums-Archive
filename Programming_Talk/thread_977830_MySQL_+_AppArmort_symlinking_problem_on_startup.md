---
title: "MySQL + AppArmort symlinking problem on startup"
date: 2008-11-10
forum: Programming Talk
---

### Post by Oncle Tom on 2008-11-10
Hello dear Ubuntu users,

sorry if you find I don't post in the appropriate forum but I'm not really sure to have found a proper forum for this problem.

Let me explain my problem.
* I usually have my MySQL data location in a non-standard folder
* since Ubuntu 8.04, I had to deal with AppArmor to add more authorized folders (for the new location I mean)
* but now I would like to deal with symlinks to avoid modifying original config files

I succeeded with that but I realize that on startup, mysql server won't start. I need to restart it manually to finally have an access to the custom data location.

Imagine I have 2 files :
 * ~/conf/apparmor/usr.sbin.mysqld-custom
 * ~/conf/mysql/my-custom.cnf

**my-custom.cnf**
```
[mysqld]
datadir         = /home/tparisot/apps/mysql

log_slow_queries       = /var/log/mysql/mysql-slow.log
long_query_time = 2
log-queries-not-using-indexes
```**user.sbin.mysqld-custom**
```
# vim:syntax=apparmor
# Last Modified: Tue Jun 19 17:37:30 2007
#include <tunables/global>

/usr/sbin/mysqld {
  #include <abstractions/base>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>
  #include <abstractions/mysql>

  capability dac_override,
  capability setgid,
  capability setuid,

  /etc/hosts.allow r,
  /etc/hosts.deny r,

  /etc/mysql/*.pem r,
  /etc/mysql/conf.d/ r,
  /etc/mysql/conf.d/* r,
  /etc/mysql/my.cnf r,
  /usr/sbin/mysqld mr,
  /usr/share/mysql/** r,
  /var/lib/mysql/ r,
  /var/lib/mysql/** rwk,
  /home/tparisot/apps/mysql/ r,
  /home/tparisot/apps/mysql/** rwk,
  /var/log/mysql/ r,
  /var/log/mysql/* rw,
  /var/run/mysqld/mysqld.pid w,
  /var/run/mysqld/mysqld.sock w,
}
``````
ls -l ~/apps | grep -i mysql
drwxr-xr-x  6 mysql    mysql    4096 2008-11-07 18:10 mysql
```So after a boot, I do that, it starts without a problem:
```
sudo service apparmor restart && sudo service mysql restart
```I inspected a bit dmesg to see what could cause trouble and it seems there is a problem :
```

sudo dmesg | grep -i mysql
[   24.235999] type=1505 audit(1226065616.742:5): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=4545
[   24.342137] type=1505 audit(1226065616.851:6): operation="profile_load" info="failed: profile already loaded" name="/usr/sbin/mysqld" name2="default" pid=4549
[   26.648358] type=1503 audit(1226065619.158:7): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=0 name="/home/tparisot/conf/mysql/my-custom.cnf" pid=5187 profile="/usr/sbin/mysqld"
[   26.789372] type=1503 audit(1226065619.298:8): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=0 name="/home/tparisot/conf/mysql/my-custom.cnf" pid=5208 profile="/usr/sbin/mysqld"
[   26.918325] type=1503 audit(1226065619.426:9): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=0 name="/home/tparisot/conf/mysql/my-custom.cnf" pid=5259 profile="/usr/sbin/mysqld"
[   27.089297] type=1503 audit(1226065619.598:10): operation="inode_create" requested_mask="a::" denied_mask="a::" fsuid=0 name="/home/tparisot/apps/mysql/parmesan.lower-test" pid=5259 profile="/usr/sbin/mysqld"
[   27.089397] type=1503 audit(1226065619.598:11): operation="inode_create" requested_mask="a::" denied_mask="a::" fsuid=0 name="/home/tparisot/apps/mysql/parmesan.lower-test" pid=5259 profile="/usr/sbin/mysqld"
[   29.823651] type=1503 audit(1226065622.331:15): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=0 name="/home/tparisot/conf/mysql/my-custom.cnf" pid=5291 profile="/usr/sbin/mysqld"
[   30.836492] type=1503 audit(1226065623.342:16): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=0 name="/home/tparisot/conf/mysql/my-custom.cnf" pid=5301 profile="/usr/sbin/mysqld"
[   31.848634] type=1503 audit(1226065624.358:17): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=0 name="/home/tparisot/conf/mysql/my-custom.cnf" pid=5311 profile="/usr/sbin/mysqld"
[   32.861928] type=1503 audit(1226065625.371:18): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=0 name="/home/tparisot/conf/mysql/my-custom.cnf" pid=5321 profile="/usr/sbin/mysqld"
[   33.873938] type=1503 audit(1226065626.382:19): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=0 name="/home/tparisot/conf/mysql/my-custom.cnf" pid=5331 profile="/usr/sbin/mysqld"
[   34.887529] type=1503 audit(1226065627.394:20): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=0 name="/home/tparisot/conf/mysql/my-custom.cnf" pid=5341 profile="/usr/sbin/mysqld"
[   35.899921] type=1503 audit(1226065628.407:21): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=0 name="/home/tparisot/conf/mysql/my-custom.cnf" pid=5351 profile="/usr/sbin/mysqld"
[   36.913259] type=1503 audit(1226065629.422:22): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=0 name="/home/tparisot/conf/mysql/my-custom.cnf" pid=5361 profile="/usr/sbin/mysqld"
[   37.926433] type=1503 audit(1226065630.435:23): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=0 name="/home/tparisot/conf/mysql/my-custom.cnf" pid=5371 profile="/usr/sbin/mysqld"
[   38.938238] type=1503 audit(1226065631.446:24): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=0 name="/home/tparisot/conf/mysql/my-custom.cnf" pid=5381 profile="/usr/sbin/mysqld"
[   39.950070] type=1503 audit(1226065632.458:25): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=0 name="/home/tparisot/conf/mysql/my-custom.cnf" pid=5391 profile="/usr/sbin/mysqld"
[   40.963434] type=1503 audit(1226065633.471:26): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=0 name="/home/tparisot/conf/mysql/my-custom.cnf" pid=5401 profile="/usr/sbin/mysqld"
``````

sudo dmesg | grep -i apparmor
[    0.004000] AppArmor: AppArmor initialized
```But the problem is I really don't see what's causing problem as both config files are OK and on manual restart, it works.

Anyone has an idea ?

Thanks a lot in advance :-)
[    0.741647] AppArmor: AppArmor Filesystem Enabled[   40.975262] type=1503 audit(1226065633.483:27): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=0 name="/home/tparisot/conf/mysql/my-custom.cnf" pid=5410 profile="/usr/sbin/mysqld"

---

### Post by Oncle Tom on 2008-11-20
I continued to inspect the problem. It's related to apparmor :
* I unlinked the /etc/apparmor.d/usr.sbin.mysqld-custom symlink
* I copy/paster its content to /etc/apparmor.d/usr.sbin.mysqld

And on startup, it works.
So it seems I can't redefine the default mysql apparmor profile on startup/boot ? Not really nice :-/
Is it a bug ?

---

### Post by usbrandon on 2008-12-30
I had this problem today and this is the solution.

You have to go into 

/etc/apparmor.d

then edit a file in there called "usr.sbin.mysqld"

There are some lines that specify the current file paths that MySQL uses for its files.  You can change the "/var/lib/mysql..."
portion to wherever you want your database files to be.

After saving the changes from above, restart the apparmor daemon
ie. "sudo invoke-rc.d apparmor restart"

Then you can start up MySQL again in much the same way:

"sudo invoke-rc.d mysql start"

---

### Post by Oncle Tom on 2008-12-30
> **usbrandon said:**
> I had this problem today and this is the solution.

You have to go into 

/etc/apparmor.d

then edit a file in there called "usr.sbin.mysqld"

There are some lines that specify the current file paths that MySQL uses for its files.  You can change the "/var/lib/mysql..."
portion to wherever you want your database files to be.

After saving the changes from above, restart the apparmor daemon
ie. "sudo invoke-rc.d apparmor restart"

Then you can start up MySQL again in much the same way:

"sudo invoke-rc.d mysql start"

Thanks, that's what I've done and told in my previous post (not as explicit as yours however).

It's a solution but I find it a bit dirty. Symlinking is pretty nice and I'm not sure we can do anything else that your exposed solution for now.

---

