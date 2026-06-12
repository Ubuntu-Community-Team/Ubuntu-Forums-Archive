---
title: "apache2-mpm-prefork -- i cannot uninstall"
date: 2005-03-11
forum: Repositories &amp; Backports
---

### Post by deathwing on 2005-03-11
I cannot unistall this, i will very much appreciate if someone can help me with this.

E: apache2-mpm-prefork:  subprocess pre-removal script returned error exit status 1

Im installing apache 2 with php and mysql

Thanks

Glenn

---

### Post by mtron on 2005-03-24
This bug is already known. From the debian Bug- tracking list: 

Package: apache2-mpm-worker
Version: 2.0.52-1 (and seems to affect also the ubuntu package 2.0.53.-4ubuntu1)
Severity: important

While trying to upgrade an older libapache2-mod-php4, apache2-mpm-worker
should be removed.

But the removal failed, because "/etc/init.d/apache2 stop" returned an
error code (because apache2 was already stopped before).

The pre-removal script shouldn't abort if this happens, because it makes
things harder in case apache2 cannot be started due to some config
problems.

=======
so that means you should try to uninstall it while apache is running. Reinstall apache2 & commmon and play with the config file to get it running. (test it with /etc/init.d/apache2 start or /etc/init.d/apache2 stop) then try to remove it with apt-get

---

### Post by eghlima on 2008-08-09
hi.
i install apache2 that is MPM with mpm_prefork_module.
this apache for best performance create some process for one client.
but i want to disable this future and can not disable.
in apache.conf use some options that might disable this but this not worked.
for example:
<IfModule mpm_prefork_module>
StartServers 1
MinSpareServers 1
MaxSpareServers 1
MaxClients 150
MaxRequestsPerChild 0
</IfModule>

i set StartServers to 1 but this not worked.

please help me.

The pre-removal script shouldn't abort if this happens, because it makes
things harder in case apache2 cannot be started due to some config
problems.

=======
so that means you should try to uninstall it while apache is running. Reinstall apache2 & commmon and play with the config file to get it running. (test it with /etc/init.d/apache2 start or /etc/init.d/apache2 stop) then try to remove it with apt-get[/QUOTE]

---

### Post by eghlima on 2008-08-15
i have this problem in programming with mod_python.
can i solve this problem in installation of mod_python.
please give me a solution if you can.
because i must solve this problem very soon.
thanks

---

