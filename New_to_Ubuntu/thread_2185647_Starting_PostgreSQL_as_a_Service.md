---
title: "Starting PostgreSQL as a Service?"
date: 2013-11-03
forum: New to Ubuntu
---

### Post by von Corax on 2013-11-03
I've installed PostgreSQL 9.1 on Precise using SPM. I can manage the daemon using pg_ctl, log in, create databases etc. etc., but I would like to have it start automatically and it doesn't. [FONT=courier new]**sudo service postgresql start **[/FONT]does nothing; subsequent **[FONT=courier new]service status[/FONT]** returns nothing, and **[FONT=courier new]pg_ctl status[/FONT]** reports *[FONT=courier new]no server running[/FONT]*.

As far as I can tell, I seem to have all of the rc scripts in all the places they're supposed to be, so the service should start automatically, but it doesn't so obviously I don't.

Any assistance would be greatly appreciated, and I'll try my best to provide any requested clarifications.

---

### Post by SeijiSensei on 2013-11-03
I have no idea what "SPM" is, but the standard Ubuntu installation of PostgreSQL 9.1 uses Upstart.  I just restarted an instance with "sudo service postgresql restart" on this 13.10 machine.  [Since the source is the same for both Precise and Saucy]("http://packages.ubuntu.com/source/precise/postgresql-9.1"), I don't think this is a versioning issue. 

The versions do differ in the least-significant digit (.9 vs .10) for what it is worth.

---

### Post by von Corax on 2013-11-03
"SPM" is the Synaptic Package Manager under the Administration menu, and as I mentioned in the original post, [FONT=courier new]**sudo service postgresql start**[/FONT] does not appear to do anything. I have a script named postgresql under /etc/init.d/, as well as symlinks named S*nn*postgresql and K*nn*postgresql in my various /etc/rc*n*.d/ directories. What am I missing?

EDIT: what I installed was the 9.1.9 binary package, which has since upgraded itself to 9.1.10.

---

### Post by SeijiSensei on 2013-11-05
Here, for comparison sake, is the manifest for my copy of postgresql-common, which includes the Upstart scripts.  My server version is 9.1.10-1.

```

Seiji@GhostWorld:~$ dpkg -L postgresql-common
/.
/var
/var/log
/var/log/postgresql
/var/lib
/var/lib/postgresql
/usr
/usr/sbin
/usr/sbin/pg_updatedicts
/usr/bin
/usr/bin/pg_ctlcluster
/usr/bin/pg_upgradecluster
/usr/bin/pg_config
package diverts others to: /usr/bin/pg_config.libpq-dev
/usr/bin/pg_virtualenv
/usr/bin/pg_lsclusters
/usr/bin/pg_createcluster
/usr/bin/pg_dropcluster
/usr/share
/usr/share/postgresql-common
/usr/share/postgresql-common/upgrade-scripts
/usr/share/postgresql-common/upgrade-scripts/SPECIFICATION
/usr/share/postgresql-common/testsuite
/usr/share/postgresql-common/init.d-functions
/usr/share/postgresql-common/run-upgrade-scripts
/usr/share/postgresql-common/pg_checksystem
/usr/share/postgresql-common/t
/usr/share/postgresql-common/t/051_inconsistent_encoding_upgrade.t
/usr/share/postgresql-common/t/031_errors_disk_full.t
/usr/share/postgresql-common/t/005_PgCommon.t
/usr/share/postgresql-common/t/090_multicluster.t
/usr/share/postgresql-common/t/002_existing_clusters.t
/usr/share/postgresql-common/t/050_encodings.t
/usr/share/postgresql-common/t/170_extensions.t
/usr/share/postgresql-common/t/043_upgrade_ssl_cert.t
/usr/share/postgresql-common/t/150_tsearch_stemming.t
/usr/share/postgresql-common/t/040_upgrade.t
/usr/share/postgresql-common/t/070_non_postgres_clusters.t
/usr/share/postgresql-common/t/130_nonroot_admin.t
/usr/share/postgresql-common/t/030_errors.t
/usr/share/postgresql-common/t/TestLib.pm
/usr/share/postgresql-common/t/180_ecpg.t
/usr/share/postgresql-common/t/120_pg_upgradecluster_scripts.t
/usr/share/postgresql-common/t/042_upgrade_tablespaces.t
/usr/share/postgresql-common/t/template
/usr/share/postgresql-common/t/052_upgrade_encodings.t
/usr/share/postgresql-common/t/080_start.conf.t
/usr/share/postgresql-common/t/041_upgrade_custompaths.t
/usr/share/postgresql-common/t/160_alternate_confroot.t
/usr/share/postgresql-common/t/020_create_sql_remove.t
/usr/share/postgresql-common/t/060_obsolete_confparams.t
/usr/share/postgresql-common/t/010_defaultport_cluster.t
/usr/share/postgresql-common/t/003_package_checks.t
/usr/share/postgresql-common/t/001_packages.t
/usr/share/postgresql-common/t/085_pg_ctl.conf.t
/usr/share/postgresql-common/t/110_integrate_cluster.t
/usr/share/postgresql-common/t/100_upgrade_scripts.t
/usr/share/postgresql-common/t/140_pg_config.t
/usr/share/doc
/usr/share/doc/postgresql-common
/usr/share/doc/postgresql-common/copyright
/usr/share/doc/postgresql-common/architecture.html
/usr/share/doc/postgresql-common/README.Debian.gz
/usr/share/doc/postgresql-common/README.Devel
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/postgresql-common
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/pg_lsclusters.1.gz
/usr/share/man/man1/pg_virtualenv.1.gz
/usr/share/man/man8
/usr/share/man/man8/pg_upgradecluster.8.gz
/usr/share/man/man8/pg_createcluster.8.gz
/usr/share/man/man8/pg_updatedicts.8.gz
/usr/share/man/man8/pg_dropcluster.8.gz
/usr/share/man/man8/pg_ctlcluster.8.gz
/etc
/etc/sysctl.d
/etc/sysctl.d/30-postgresql-shm.conf
/etc/init.d
/etc/init.d/postgresql
/etc/postgresql-common
/etc/postgresql-common/pg_upgradecluster.d
/etc/postgresql-common/createcluster.conf
/etc/logrotate.d
/etc/logrotate.d/postgresql-common
/usr/share/doc/postgresql-common/changelog.gz

```

I'd try reinstalling like this
```

sudo apt-get update
sudo apt-get remove postgresql* --purge
sudo apt-get install postgresql-9.1

```

---

### Post by von Corax on 2013-11-09
Thanks, that seems to have sorted it.

Since Synaptic is merely a front-end for apt-get, can I assume the problem was with the 9.1.9 package rather than anything else?

---

