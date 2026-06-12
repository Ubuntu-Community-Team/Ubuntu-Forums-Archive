---
title: "Selinux ssh permission issue"
date: 2015-03-26
forum: New to Ubuntu
---

### Post by zinny on 2015-03-26
[COLOR=#000000][FONT=Verdana]Hi All,[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Please can someone assist me on this, I enabled Selinux on Ubuntu 14.04 server and it's disabling ssh remote login for all users including root.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]From the ssh terminal I get the following error:[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]ssh root@192.168.x.x[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Last login: Wed Mar 25 12:39:02 2015 from 192.168.x.x[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]/bin/bash: Permission denied[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Connection to 192.168.211.135 closed.[/FONT][/COLOR]


[COLOR=#000000][FONT=Verdana]tail /var/log/auth.log[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]ubuntu sshd[1640]: Accepted password for root from 192.168.x.x port 51082 ssh2[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]ubuntu sshd[1642]: Accepted password for root from 192.168.x.x port 51089 ssh2[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]ubunt sshd[1640]: Received disconnect from 192.168.x.x: disconnected by user[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]audit2allow --all[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]sshd_t[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]This avc is a constraint violation. you would need to modify the attribute of either the source or target types to allow this access.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]possible cause is the source user (system_u) and target user (unconfined_u) are different.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]possible cause is the source role (system_r) and target role (unconfined_r) are different.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]possible cause is the source level (s0) and target level (s0-s0:c0.c255) are different.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]allow sshd_t unconfined_t[/FONT][/COLOR][IMG]https://lqo-thequestionsnetw.netdna-ssl.com/questions/images/smilies/tongue.gif[/IMG][COLOR=#000000][FONT=Verdana]rocess transition.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Please how can I make this changes to take effect.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Thanks in advance.[/FONT][/COLOR]

---

### Post by SeijiSensei on 2015-03-26
Debian/Ubuntu use [AppArmor]("https://wiki.ubuntu.com/AppArmor") by default rather than SELinux.  I only see that on RedHat-flavored distros.  What's wrong with AppArmor?

---

