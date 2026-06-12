---
title: "Restarting service during postinst prevents finishing of deb-installation"
date: 2011-11-03
forum: Packaging and Compiling Programs
---

### Post by Fusel Wusel on 2011-11-03
Hello everybody!

I am currently creating an Ubuntu (Lucid)  package for installation and configuration of a postgresql-8.4 database.

During postinst I need to restart the postgresql service via
```
sudo /etc/init.d/postgresql-8.4 restart
```
which works, as there ist an [OK] on the Console.

But this also prevents the installation from finishing. I mean, the installtion should exit somewhere and the package is installed. But with the restart it does not. When I take out the restart of the postgresql service, the setup runs through without a flaw. I have also tried ```
sudo /etc/init.d/postgresql-8.4 restart || true
``` already which does not help either.

Any suggestions?

---

### Post by SevenMachines on 2011-11-04
Dont use sudo in maintainer scripts. If theres still a problem can you post the full .postinst? Also, try running using dpkg -D to install, or adding set -x to the top of the .postinst script to see the output

---

### Post by Fusel Wusel on 2011-11-04
Thanks for your reply! Ok, so no sudo in Maintainer scripts. But there are some lines where I need to, because I need to call some scripts with another user (sudo -u).
This is the whole .postinst in its most actual form:
```
#!/bin/sh

# Source debconf library.
. /usr/share/debconf/confmodule

set -x
set -e

case "$1" in
    configure)
	db_get enter-admin-pwd
	ENTERADMINPWD=$RET
	db_get local-user-only
	LOCAL_USER_ONLY=$RET
	db_get simulations-user
	SIM_USER=$RET
	echo "Setting up the password"
	sudo -u postgres psql -c"ALTER user postgres WITH PASSWORD '$ENTERADMINPWD'"
	if [ "$LOCAL_USER_ONLY"="true" ]; then
		echo "Resticting access to local users only"
		sed -i 's/local all postgres ident sameuser/#local all postgres ident sameuser/' /etc/postgresql/8.4/main/pg_hba.conf
		sed -i 's/local all all ident sameuser/local all all md5/' /etc/postgresql/8.4/main/pg_hba.conf
	fi
	echo "Creating the database"
	sudo -u postgres psql -c"CREATE DATABASE simdb"
	echo "Configuring the database"
	sudo -u postgres psql -d simdb -f /usr/share/pyshared/mypackage/simdb/sql/setupSimDB.sql
        echo "Creating database user"
	sudo -u $SIM_USER python /usr/share/pyshared/mypackage/simdb/scripts/createUser.py --automatic $ENTERADMINPWD	
	echo "Restarting the postgresql service"
	invoke-rc.d postgresql-8.4 restart
    ;;

    *)
        echo "postinst called with unknown argument \`$1'" >&2
        exit 1
    ;;
esac

#DEBHELPER#
```

With this, setup ends with:
```
+ invoke-rc.d postgresql-8.4 restart
 * Restarting PostgreSQL 8.4 database server      [ OK ]
```
And then nothing. Normally if would expect it to return back to my shell input but it just stays in this condition and I have to CTRL-C it. But if I comment out the invoke-rc.d line, setups runs through.

---

### Post by SevenMachines on 2011-11-04
If it hangs on 'invoke-rc.d postgresql-8.4 restart' then you might want to look at /etc/init.d/postgresql-8.4, try adding set -x to the top of that too. Might be worth looking at the postgresql logs to see if it shows whats stalling

---

### Post by Fusel Wusel on 2011-11-04
Everything seems ok in init.d/postgresql-8.4.
I now tried it with everything except the restart-command commented out. Does not work either. This is the Output:
```
+ set -e
+ db_get enter-admin-pwd
+ _db_cmd GET enter-admin-pwd
+ IFS=  printf %s\n GET enter-admin-pwd
+ IFS=
 read -r _db_internal_line
+ RET=password
+ return 0
+ ENTERADMINPWD=foobar
+ db_get local-user-only
+ _db_cmd GET local-user-only
+ IFS=  printf %s\n GET local-user-only
+ IFS=
 read -r _db_internal_line
+ RET=true
+ return 0
+ LOCAL_USER_ONLY=true
+ db_get simulations-user
+ _db_cmd GET simulations-user
+ IFS=  printf %s\n GET simulations-user
+ IFS=
 read -r _db_internal_line
+ RET=fusel
+ return 0
+ SIM_USER=cka
+ echo Setting up the password
Setting up the password
+ echo Creating the database
Creating the database
+ echo Configuring the database
Configuring the database
+ echo Creating database user
Creating database user
+ echo Restarting the postgresql service
Restarting the postgresql service
+ invoke-rc.d postgresql-8.4 restart
+ [ -r /usr/share/postgresql-common/init.d-functions ]
+ . /usr/share/postgresql-common/init.d-functions
+ . /lib/lsb/init-functions
+ FANCYTTY=
+ [ -e /etc/lsb-base-logging.sh ]
+ . /etc/lsb-base-logging.sh
+ VERSION=8.4
+ restart 8.4
+ do_ctl_all restart 8.4 Restarting PostgreSQL 8.4 database server
+ [ restart ]
+ [ 8.4 ]
+ [ -d /etc/postgresql/8.4 ]
+ ls /etc/postgresql/8.4
+ [ main ]
+ [ -x /usr/lib/postgresql/8.4/bin/postmaster ]
+ status=0
+ log_daemon_msg Restarting PostgreSQL 8.4 database server
+ [ -z Restarting PostgreSQL 8.4 database server ]
+ log_use_usplash
+ [ n = y ]
+ type usplash_write
+ log_use_fancy_output
+ TPUT=/usr/bin/tput
+ EXPR=/usr/bin/expr
+ [ -t 1 ]
+ [ xxterm != x ]
+ [ xxterm != xdumb ]
+ [ -x /usr/bin/tput ]
+ [ -x /usr/bin/expr ]
+ /usr/bin/tput hpa 60
+ /usr/bin/tput setaf 1
+ [ -z ]
+ FANCYTTY=1
+ true
+ /usr/bin/tput xenl
+ /usr/bin/tput cols
+ COLS=80
+ [ 80 ]
+ [ 80 -gt 6 ]
+ /usr/bin/expr 80 - 7
+ COL=73
+ printf  * Restarting PostgreSQL 8.4 database server       
 * Restarting PostgreSQL 8.4 database server       + /usr/bin/expr 80 - 1
+ /usr/bin/tput hpa 79
                                                                               + printf  
 + [ -e /etc/postgresql/8.4/main/postgresql.conf ]
+ basename /etc/postgresql/8.4/main
+ name=main
+ [ -e /etc/postgresql/8.4/main/start.conf ]
+ sed s/#.*$//; /^[[:space:]]*$/d; s/^\s*//; s/\s*$// /etc/postgresql/8.4/main/start.conf
+ start=auto
+ [ auto = auto ]
+ log_progress_msg main
+ :
+ set +e
+ [ restart = stop ]
+ [ restart = restart ]
+ pg_ctlcluster --force 8.4 main restart
+ ERRMSG=
+ res=0
+ set -e
+ [ 0 -eq 0 ]
+ [ 0 -ne 0 -a -n  ]
+ log_end_msg 0
+ [ -z 0 ]
+ log_use_usplash
+ [ n = y ]
+ type usplash_write
+ [ 73 ]
+ [ -x /usr/bin/tput ]
+ printf \r
+ /usr/bin/tput hpa 73
                                                                         + [ 0 -eq 0 ]
+ echo [ OK ]
[ OK ]
+ return 0
+ return 0
+ exit 0

```

exit 0 should be right. But at this point nothing happens...

---

### Post by Fusel Wusel on 2011-11-04
Solved the issue with adding a
```
db_stop
```
at the end of postinst. Now it works.

---

