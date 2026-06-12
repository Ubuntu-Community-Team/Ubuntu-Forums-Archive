---
title: "error in starting puppet"
date: 2014-10-02
forum: New to Ubuntu
---

### Post by mia3 on 2014-10-02
Hi,

I've gotten error once I want to start pupp
et.The log file is showing following message:

root@master:~# tail -f /var/log/syslog
Oct  2 08:39:15 master puppet-agent[30713]: (/File[/var/lib/puppet/lib]) Could not evaluate: Could not retrieve file metadata for puppet://master.openstacklocal/plugins: Connection re
fused - connect(2)Oct  2 08:39:15 master puppet-agent[30713]: (/File[/var/lib/puppet/lib]) Wrapped exception:
Oct  2 08:39:15 master puppet-agent[30713]: (/File[/var/lib/puppet/lib]) Connection refused - connect(2)
Oct  2 08:39:15 master puppet-agent[30713]: Could not retrieve catalog from remote server: Connection refused - connect(2)
Oct  2 08:39:15 master puppet-agent[30713]: Using cached catalog
Oct  2 08:39:15 master puppet-agent[30713]: Local environment: "production" doesn't match server specified environment "common", restarting agent run with environment "common"
Oct  2 08:39:15 master puppet-agent[30713]: Could not retrieve catalog from remote server: Connection refused - connect(2)
Oct  2 08:39:15 master puppet-agent[30713]: Using cached catalog
Oct  2 08:39:16 master puppet-agent[30713]: Finished catalog run in 0.10 seconds
Oct  2 08:39:16 master puppet-agent[30713]: Could not send report: Connection refused - connect(2)

I've run Ubuntu12.04 on openstack and installed mln, puppet, foreman. 
All of codes (include installing puppet,..) has been written on foreman and everything worked fine already.
I wanted to test it again so ran following command:

*service apache2 stop*
[I]puppet cert clean --all

[/I]#And use this command to start it:
[I]puppet master --no-daemonize --verbose
But it doesn't start...

I appreciate any help in this issue.

Thanks,



As I've run it again, it gives following error now:

[/I]root@master:~# tail -f /var/log/syslog
Oct  2 10:00:01 master CRON[5972]: (foreman) CMD (   cd ${FOREMAN_HOME} && /usr/sbin/foreman-rake ldap:refresh_usergroups >>/var/log/foreman/cron.log 2>&1)
Oct  2 10:09:15 master puppet-agent[6007]: Unable to fetch my node definition, but the agent run will continue:
Oct  2 10:09:15 master puppet-agent[6007]: Error 400 on SERVER: Failed to find master.openstacklocal via exec: Execution of '/etc/puppet/node.rb master.openstacklocal' returned 1:
Oct  2 10:09:16 master puppet-agent[6007]: Could not retrieve catalog from remote server: Error 400 on SERVER: Failed when searching for node master.openstacklocal: Failed to find master.openstacklocal via exec: Execution of '/etc/puppet/node.rb master.openstacklocal' returned 1:
Oct  2 10:09:16 master puppet-agent[6007]: Using cached catalog
Oct  2 10:09:16 master puppet-agent[6007]: Local environment: "production" doesn't match server specified environment "common", restarting agent run with environment "common"
Oct  2 10:09:17 master puppet-agent[6007]: Could not retrieve catalog from remote server: Error 400 on SERVER: Failed when searching for node master.openstacklocal: Failed to find master.openstacklocal via exec: Execution of '/etc/puppet/node.rb master.openstacklocal' returned 1
:
Oct
  2 10:09:17 master puppet-agent[6007]: Using cached catalog
Oct  2 10:09:17 master puppet-agent[6007]: Finished catalog run in 0.20 seconds
Oct  2 10:17:01 master CRON[6149]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

---

