---
title: "update-rc.d: warning: start and stop actions are no longer supported; falling back to"
date: 2018-03-22
forum: New to Ubuntu
---

### Post by oleg.sergiyuk on 2018-03-22
[COLOR=#242729][FONT=Arial]On Ubuntu 17.10 installation hangs when installing ebtables package on the following:[/FONT][/COLOR]
Preparing to unpack .../ebtables_2.0.10.4-3.5ubuntu2_amd64.deb ...                                                     
Unpacking ebtables (2.0.10.4-3.5ubuntu2) ...               
Processing triggers for ureadahead (0.100.0-20) ...        
Processing triggers for systemd (234-2ubuntu12.1) ...      
Setting up ebtables (2.0.10.4-3.5ubuntu2) ...              
Created symlink /etc/systemd/system/multi-user.target.wants/ebtables.service &#8594; /lib/systemd/system/ebtables.service.   
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults  
[COLOR=#242729][FONT=Arial]The output of ps:[/FONT][/COLOR]
root      4432  0.0  0.0   4592   840 pts/4    S+   10:37   0:00 /bin/sh /var/lib/dpkg/info/ebtables.postinst configure
[COLOR=#242729][FONT=Arial]Does it look like the script cannot complete?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]How can I troubleshoot further?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Is it an alternate way to install an ebtables?[/FONT][/COLOR]

---

