---
title: "is my machine compromised?"
date: 2008-08-04
forum: Philippine Team
---

### Post by Script Warlock on 2008-08-04
pls help me about this log entry from my server and if found compromised what would i do to prevent it.....

---

### Post by Nessa on 2008-08-04
It would help tons if you post the log entry. :)

---

### Post by Script Warlock on 2008-08-04
oopps eto pala yung log files: (pasensya ha kung medyo mahaba di pa rin kc ako marunong mag-attach ng file d2)

Aug  4 18:16:07 UbuntuServer sshd[24512]: Failed password for invalid user staff from 200.43.197.146 port 35644 ssh2 
Aug  4 18:16:11 UbuntuServer sshd[24514]: Invalid user sales from 200.43.197.146 
Aug  4 18:16:11 UbuntuServer sshd[24514]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 18:16:11 UbuntuServer sshd[24514]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar 
Aug  4 18:16:12 UbuntuServer sshd[24514]: Failed password for invalid user sales from 200.43.197.146 port 36693 ssh2 
Aug  4 18:16:16 UbuntuServer sshd[24518]: Invalid user recruit from 200.43.197.146 
Aug  4 18:16:16 UbuntuServer sshd[24518]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 18:16:16 UbuntuServer sshd[24518]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar 
Aug  4 18:16:19 UbuntuServer sshd[24518]: Failed password for invalid user recruit from 200.43.197.146 port 38408 ssh2 
Aug  4 18:16:22 UbuntuServer sshd[24524]: Invalid user alias from 200.43.197.146 
Aug  4 18:16:22 UbuntuServer sshd[24524]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 18:16:22 UbuntuServer sshd[24524]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar 
Aug  4 18:16:24 UbuntuServer sshd[24524]: Failed password for invalid user alias from 200.43.197.146 port 39363 ssh2 
Aug  4 18:16:29 UbuntuServer sshd[24529]: Invalid user office from 200.43.197.146 
Aug  4 18:16:29 UbuntuServer sshd[24529]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 18:16:29 UbuntuServer sshd[24529]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar 
Aug  4 18:16:31 UbuntuServer sshd[24529]: Failed password for invalid user office from 200.43.197.146 port 40202 ssh2 
Aug  4 18:16:35 UbuntuServer sshd[24533]: Invalid user samba from 200.43.197.146 
Aug  4 18:16:35 UbuntuServer sshd[24533]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 18:16:35 UbuntuServer sshd[24533]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar 
Aug  4 18:16:37 UbuntuServer sshd[24533]: Failed password for invalid user samba from 200.43.197.146 port 41717 ssh2 
Aug  4 18:16:41 UbuntuServer sshd[24539]: Invalid user tomcat from 200.43.197.146 
Aug  4 18:16:41 UbuntuServer sshd[24539]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 18:16:41 UbuntuServer sshd[24539]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar 
Aug  4 18:16:43 UbuntuServer sshd[24539]: Failed password for invalid user tomcat from 200.43.197.146 port 42545 ssh2 
Aug  4 18:16:46 UbuntuServer sshd[24544]: Invalid user webadmin from 200.43.197.146 
Aug  4 18:16:46 UbuntuServer sshd[24544]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 18:16:46 UbuntuServer sshd[24544]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar 
Aug  4 18:16:48 UbuntuServer sshd[24544]: Failed password for invalid user webadmin from 200.43.197.146 port 43370 ssh2 
Aug  4 18:16:52 UbuntuServer sshd[24552]: Invalid user spam from 200.43.197.146 
Aug  4 18:16:52 UbuntuServer sshd[24552]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 18:16:52 UbuntuServer sshd[24552]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar 
Aug  4 18:16:54 UbuntuServer sshd[24552]: Failed password for invalid user spam from 200.43.197.146 port 44305 ssh2 
Aug  4 18:16:58 UbuntuServer sshd[24556]: Invalid user virus from 200.43.197.146 
Aug  4 18:16:58 UbuntuServer sshd[24556]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 18:16:58 UbuntuServer sshd[24556]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar 
Aug  4 18:17:00 UbuntuServer sshd[24556]: Failed password for invalid user virus from 200.43.197.146 port 45130 ssh2 
Aug  4 18:17:01 UbuntuServer CRON[24568]: pam_unix(cron:session): session opened for user root by (uid=0) 
Aug  4 18:17:01 UbuntuServer CRON[24568]: pam_unix(cron:session): session closed for user root 
Aug  4 18:17:03 UbuntuServer sshd[24567]: Invalid user cyrus from 200.43.197.146 
Aug  4 18:17:03 UbuntuServer sshd[24567]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 18:17:03 UbuntuServer sshd[24567]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar 
Aug  4 18:17:05 UbuntuServer sshd[24567]: Failed password for invalid user cyrus from 200.43.197.146 port 45949 ssh2 
Aug  4 18:17:09 UbuntuServer sshd[24580]: Invalid user oracle from 200.43.197.146 
Aug  4 18:17:09 UbuntuServer sshd[24580]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 18:17:09 UbuntuServer sshd[24580]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar 
Aug  4 18:17:10 UbuntuServer sshd[24580]: Failed password for invalid user oracle from 200.43.197.146 port 47034 ssh2 
Aug  4 18:17:14 UbuntuServer sshd[24587]: Invalid user michael from 200.43.197.146 
Aug  4 18:17:14 UbuntuServer sshd[24587]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 18:17:14 UbuntuServer sshd[24587]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar 
Aug  4 18:17:17 UbuntuServer sshd[24587]: Failed password for invalid user michael from 200.43.197.146 port 47878 ssh2 
Aug  4 18:17:21 UbuntuServer sshd[24596]: Invalid user ftp from 200.43.197.146 
Aug  4 18:17:21 UbuntuServer sshd[24596]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 18:17:21 UbuntuServer sshd[24596]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar 
Aug  4 18:17:22 UbuntuServer sshd[24596]: Failed password for invalid user ftp from 200.43.197.146 port 49145 ssh2 
Aug  4 18:17:26 UbuntuServer sshd[24606]: Invalid user test from 200.43.197.146 
Aug  4 18:17:26 UbuntuServer sshd[24606]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 18:17:26 UbuntuServer sshd[24606]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar 
Aug  4 18:17:28 UbuntuServer sshd[24606]: Failed password for invalid user test from 200.43.197.146 port 49968 ssh2 
Aug  4 18:17:32 UbuntuServer sshd[24612]: Invalid user webmaster from 200.43.197.146 
Aug  4 18:17:32 UbuntuServer sshd[24612]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 18:17:32 UbuntuServer sshd[24612]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar 
Aug  4 18:17:34 UbuntuServer sshd[24612]: Failed password for invalid user webmaster from 200.43.197.146 port 50932 ssh2 
Aug  4 18:17:41 UbuntuServer sshd[24616]: Invalid user postmaster from 200.43.197.146 
Aug  4 18:17:41 UbuntuServer sshd[24616]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 18:17:41 UbuntuServer sshd[24616]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar 
Aug  4 18:17:43 UbuntuServer sshd[24616]: Failed password for invalid user postmaster from 200.43.197.146 port 51762 ssh2 
Aug  4 18:17:47 UbuntuServer sshd[24631]: Invalid user postfix from 200.43.197.146 
Aug  4 18:17:47 UbuntuServer sshd[24631]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 18:17:47 UbuntuServer sshd[24631]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar 
Aug  4 18:17:49 UbuntuServer sshd[24631]: Failed password for invalid user postfix from 200.43.197.146 port 53410 ssh2 
Aug  4 18:17:54 UbuntuServer sshd[24634]: Invalid user postgres from 200.43.197.146 
Aug  4 18:17:54 UbuntuServer sshd[24634]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 18:17:54 UbuntuServer sshd[24634]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar 
Aug  4 18:17:56 UbuntuServer sshd[24634]: Failed password for invalid user postgres from 200.43.197.146 port 54231 ssh2 
Aug  4 18:17:59 UbuntuServer sshd[24640]: Invalid user paul from 200.43.197.146 
Aug  4 18:17:59 UbuntuServer sshd[24640]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 18:18:00 UbuntuServer sshd[24640]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar 
Aug  4 18:18:01 UbuntuServer sshd[24640]: Failed password for invalid user paul from 200.43.197.146 port 55290 ssh2 
Aug  4 18:18:05 UbuntuServer sshd[24647]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar  user=root 
Aug  4 18:18:07 UbuntuServer sshd[24647]: Failed password for root from 200.43.197.146 port 32969 ssh2 
Aug  4 18:18:11 UbuntuServer sshd[24652]: Invalid user guest from 200.43.197.146 
Aug  4 18:18:11 UbuntuServer sshd[24652]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 18:18:11 UbuntuServer sshd[24652]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar 
Aug  4 18:18:13 UbuntuServer sshd[24652]: Failed password for invalid user guest from 200.43.197.146 port 33800 ssh2 
Aug  4 18:18:19 UbuntuServer sshd[24657]: Invalid user admin from 200.43.197.146 
Aug  4 18:18:19 UbuntuServer sshd[24657]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 18:18:19 UbuntuServer sshd[24657]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar 
Aug  4 18:18:21 UbuntuServer sshd[24657]: Failed password for invalid user admin from 200.43.197.146 port 34736 ssh2 
Aug  4 18:18:24 UbuntuServer sshd[24665]: Invalid user linux from 200.43.197.146 
Aug  4 18:18:24 UbuntuServer sshd[24665]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 18:18:25 UbuntuServer sshd[24665]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar 
Aug  4 18:18:27 UbuntuServer sshd[24665]: Failed password for invalid user linux from 200.43.197.146 port 35786 ssh2 
Aug  4 18:18:31 UbuntuServer sshd[24671]: Invalid user user from 200.43.197.146 
Aug  4 18:18:31 UbuntuServer sshd[24671]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 18:18:31 UbuntuServer sshd[24671]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar 
Aug  4 18:18:33 UbuntuServer sshd[24671]: Failed password for invalid user user from 200.43.197.146 port 37046 ssh2 
Aug  4 18:18:36 UbuntuServer sshd[24677]: Invalid user david from 200.43.197.146 
Aug  4 18:18:36 UbuntuServer sshd[24677]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 18:18:36 UbuntuServer sshd[24677]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar 
Aug  4 18:18:38 UbuntuServer sshd[24677]: Failed password for invalid user david from 200.43.197.146 port 37868 ssh2 
Aug  4 18:18:42 UbuntuServer sshd[24681]: Invalid user web from 200.43.197.146 
Aug  4 18:18:42 UbuntuServer sshd[24681]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 18:18:42 UbuntuServer sshd[24681]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar 
Aug  4 18:18:45 UbuntuServer sshd[24681]: Failed password for invalid user web from 200.43.197.146 port 38797 ssh2 
Aug  4 18:18:49 UbuntuServer sshd[24684]: Invalid user apache from 200.43.197.146 
Aug  4 18:18:49 UbuntuServer sshd[24684]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 18:18:49 UbuntuServer sshd[24684]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar 
Aug  4 18:18:50 UbuntuServer sshd[24684]: Failed password for invalid user apache from 200.43.197.146 port 39630 ssh2 
Aug  4 18:18:54 UbuntuServer sshd[24690]: Invalid user pgsql from 200.43.197.146 
Aug  4 18:18:54 UbuntuServer sshd[24690]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 18:18:54 UbuntuServer sshd[24690]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar 
Aug  4 18:18:57 UbuntuServer sshd[24690]: Failed password for invalid user pgsql from 200.43.197.146 port 41132 ssh2 
Aug  4 18:19:00 UbuntuServer sshd[24695]: Invalid user mysql from 200.43.197.146 
Aug  4 18:19:00 UbuntuServer sshd[24695]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 18:19:00 UbuntuServer sshd[24695]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar 
Aug  4 18:19:02 UbuntuServer sshd[24695]: Failed password for invalid user mysql from 200.43.197.146 port 42719 ssh2 
Aug  4 18:19:06 UbuntuServer sshd[24701]: Invalid user info from 200.43.197.146 
Aug  4 18:19:06 UbuntuServer sshd[24701]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 18:19:06 UbuntuServer sshd[24701]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar 
Aug  4 18:19:09 UbuntuServer sshd[24701]: Failed password for invalid user info from 200.43.197.146 port 43850 ssh2 
Aug  4 18:19:12 UbuntuServer sshd[24710]: Invalid user tony from 200.43.197.146 
Aug  4 18:19:12 UbuntuServer sshd[24710]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 18:19:12 UbuntuServer sshd[24710]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar 
Aug  4 18:19:14 UbuntuServer sshd[24710]: Failed password for invalid user tony from 200.43.197.146 port 44731 ssh2 
Aug  4 18:19:18 UbuntuServer sshd[24715]: Invalid user core from 200.43.197.146 
Aug  4 18:19:18 UbuntuServer sshd[24715]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 18:19:18 UbuntuServer sshd[24715]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar 
Aug  4 18:19:21 UbuntuServer sshd[24715]: Failed password for invalid user core from 200.43.197.146 port 45552 ssh2 
Aug  4 18:19:29 UbuntuServer sshd[24719]: Invalid user newsletter from 200.43.197.146 
Aug  4 18:19:29 UbuntuServer sshd[24719]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 18:19:29 UbuntuServer sshd[24719]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=host146.200-43-197.telecom.net.ar 
Aug  4 18:19:31 UbuntuServer sshd[24719]: Failed password for invalid user newsletter from 200.43.197.146 port 46654 ssh2 
Aug  4 19:17:01 UbuntuServer CRON[26963]: pam_unix(cron:session): session opened for user root by (uid=0) 
Aug  4 19:17:01 UbuntuServer CRON[26963]: pam_unix(cron:session): session closed for user root 
Aug  4 20:17:01 UbuntuServer CRON[29470]: pam_unix(cron:session): session opened for user root by (uid=0) 
Aug  4 20:17:01 UbuntuServer CRON[29470]: pam_unix(cron:session): session closed for user root 
Aug  4 20:34:57 UbuntuServer sshd[30261]: pam_smbpass(sshd:auth): unrecognized option [missingok] 
Aug  4 20:34:57 UbuntuServer sshd[30261]: Accepted password for pusoicafe from 192.168.0.240 port 4200 ssh2 
Aug  4 20:34:57 UbuntuServer sshd[30280]: pam_unix(sshd:session): session opened for user pusoicafe by (uid=0) 
Aug  4 20:35:03 UbuntuServer sshd[30280]: pam_unix(sshd:session): session closed for user pusoicafe 
Aug  4 20:35:37 UbuntuServer sshd[30325]: Accepted publickey for nx from 192.168.0.240 port 4204 ssh2 
Aug  4 20:35:37 UbuntuServer sshd[30330]: pam_unix(sshd:session): session opened for user nx by (uid=0) 
Aug  4 20:35:38 UbuntuServer sshd[30340]: pam_smbpass(sshd:auth): unrecognized option [missingok] 
Aug  4 20:35:39 UbuntuServer sshd[30340]: Accepted password for pusoicafe from 127.0.0.1 port 56703 ssh2 
Aug  4 20:35:39 UbuntuServer sshd[30342]: pam_unix(sshd:session): session opened for user pusoicafe by (uid=0) 
Aug  4 20:35:39 UbuntuServer sshd[30342]: pam_unix(sshd:session): session closed for user pusoicafe 
Aug  4 20:35:39 UbuntuServer sshd[30347]: Accepted publickey for pusoicafe from 127.0.0.1 port 56704 ssh2 
Aug  4 20:35:39 UbuntuServer sshd[30349]: pam_unix(sshd:session): session opened for user pusoicafe by (uid=0) 
Aug  4 20:36:38 UbuntuServer sshd[30330]: pam_unix(sshd:session): session closed for user nx 
Aug  4 20:36:39 UbuntuServer sshd[30349]: pam_unix(sshd:session): session closed for user pusoicafe 
Aug  4 20:40:49 UbuntuServer sshd[30847]: pam_smbpass(sshd:auth): unrecognized option [missingok] 
Aug  4 20:40:49 UbuntuServer sshd[30847]: Accepted password for pusoicafe from 192.168.0.240 port 4280 ssh2 
Aug  4 20:40:49 UbuntuServer sshd[30861]: pam_unix(sshd:session): session opened for user pusoicafe by (uid=0) 
Aug  4 20:41:27 UbuntuServer sshd[30861]: pam_unix(sshd:session): session closed for user pusoicafe 
Aug  4 21:17:01 UbuntuServer CRON[466]: pam_unix(cron:session): session opened for user root by (uid=0) 
Aug  4 21:17:01 UbuntuServer CRON[466]: pam_unix(cron:session): session closed for user root 
Aug  4 22:17:01 UbuntuServer CRON[3773]: pam_unix(cron:session): session opened for user root by (uid=0) 
Aug  4 22:17:01 UbuntuServer CRON[3773]: pam_unix(cron:session): session closed for user root 
Aug  4 22:54:05 UbuntuServer sshd[5531]: Did not receive identification string from 125.215.218.34 
Aug  4 22:55:17 UbuntuServer sshd[5565]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 22:55:20 UbuntuServer sshd[5565]: Failed password for root from 125.215.218.34 port 54853 ssh2 
Aug  4 22:55:26 UbuntuServer sshd[5572]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 22:55:27 UbuntuServer sshd[5572]: Failed password for root from 125.215.218.34 port 57544 ssh2 
Aug  4 22:55:33 UbuntuServer sshd[5579]: Invalid user apple from 125.215.218.34 
Aug  4 22:55:33 UbuntuServer sshd[5579]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 22:55:33 UbuntuServer sshd[5579]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 22:55:36 UbuntuServer sshd[5579]: Failed password for invalid user apple from 125.215.218.34 port 58713 ssh2 
Aug  4 22:55:42 UbuntuServer sshd[5587]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 22:55:44 UbuntuServer sshd[5587]: Failed password for root from 125.215.218.34 port 60878 ssh2 
Aug  4 22:55:50 UbuntuServer sshd[5599]: Invalid user brian from 125.215.218.34 
Aug  4 22:55:50 UbuntuServer sshd[5599]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 22:55:50 UbuntuServer sshd[5599]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 22:55:51 UbuntuServer sshd[5599]: Failed password for invalid user brian from 125.215.218.34 port 33779 ssh2 
Aug  4 22:55:58 UbuntuServer sshd[5612]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 22:56:00 UbuntuServer sshd[5612]: Failed password for root from 125.215.218.34 port 35167 ssh2 
Aug  4 22:56:06 UbuntuServer sshd[5622]: Invalid user andrew from 125.215.218.34 
Aug  4 22:56:06 UbuntuServer sshd[5622]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 22:56:06 UbuntuServer sshd[5622]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 22:56:08 UbuntuServer sshd[5622]: Failed password for invalid user andrew from 125.215.218.34 port 36246 ssh2 
Aug  4 22:56:14 UbuntuServer sshd[5628]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 22:56:15 UbuntuServer sshd[5628]: Failed password for root from 125.215.218.34 port 37395 ssh2 
Aug  4 22:56:22 UbuntuServer sshd[5633]: Invalid user newsroom from 125.215.218.34 
Aug  4 22:56:22 UbuntuServer sshd[5633]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 22:56:22 UbuntuServer sshd[5633]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 22:56:24 UbuntuServer sshd[5633]: Failed password for invalid user newsroom from 125.215.218.34 port 38425 ssh2 
Aug  4 22:56:30 UbuntuServer sshd[5639]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 22:56:31 UbuntuServer sshd[5639]: Failed password for root from 125.215.218.34 port 39843 ssh2 
Aug  4 22:56:38 UbuntuServer sshd[5643]: Invalid user magazine from 125.215.218.34 
Aug  4 22:56:38 UbuntuServer sshd[5643]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 22:56:38 UbuntuServer sshd[5643]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 22:56:40 UbuntuServer sshd[5643]: Failed password for invalid user magazine from 125.215.218.34 port 40949 ssh2 
Aug  4 22:56:46 UbuntuServer sshd[5650]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 22:56:49 UbuntuServer sshd[5650]: Failed password for root from 125.215.218.34 port 42024 ssh2 
Aug  4 22:56:55 UbuntuServer sshd[5662]: Invalid user research from 125.215.218.34 
Aug  4 22:56:55 UbuntuServer sshd[5662]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 22:56:55 UbuntuServer sshd[5662]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 22:56:56 UbuntuServer sshd[5662]: Failed password for invalid user research from 125.215.218.34 port 43177 ssh2 
Aug  4 22:57:02 UbuntuServer sshd[5668]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 22:57:05 UbuntuServer sshd[5668]: Failed password for root from 125.215.218.34 port 44513 ssh2 
Aug  4 22:57:11 UbuntuServer sshd[5675]: Invalid user cjohnson from 125.215.218.34 
Aug  4 22:57:11 UbuntuServer sshd[5675]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 22:57:11 UbuntuServer sshd[5675]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 22:57:13 UbuntuServer sshd[5675]: Failed password for invalid user cjohnson from 125.215.218.34 port 46057 ssh2 
Aug  4 22:57:19 UbuntuServer sshd[5683]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 22:57:20 UbuntuServer sshd[5683]: Failed password for root from 125.215.218.34 port 47758 ssh2 
Aug  4 22:57:27 UbuntuServer sshd[5689]: Invalid user export from 125.215.218.34 
Aug  4 22:57:27 UbuntuServer sshd[5689]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 22:57:27 UbuntuServer sshd[5689]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 22:57:29 UbuntuServer sshd[5689]: Failed password for invalid user export from 125.215.218.34 port 48754 ssh2 
Aug  4 22:57:35 UbuntuServer sshd[5696]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 22:57:37 UbuntuServer sshd[5696]: Failed password for root from 125.215.218.34 port 50063 ssh2 
Aug  4 22:57:43 UbuntuServer sshd[5705]: Invalid user photo from 125.215.218.34 
Aug  4 22:57:43 UbuntuServer sshd[5705]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 22:57:43 UbuntuServer sshd[5705]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 22:57:45 UbuntuServer sshd[5705]: Failed password for invalid user photo from 125.215.218.34 port 51293 ssh2 
Aug  4 22:57:51 UbuntuServer sshd[5712]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 22:57:53 UbuntuServer sshd[5712]: Failed password for root from 125.215.218.34 port 52249 ssh2 
Aug  4 22:57:59 UbuntuServer sshd[5723]: Invalid user gast from 125.215.218.34 
Aug  4 22:57:59 UbuntuServer sshd[5723]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 22:57:59 UbuntuServer sshd[5723]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 22:58:02 UbuntuServer sshd[5723]: Failed password for invalid user gast from 125.215.218.34 port 53472 ssh2 
Aug  4 22:58:08 UbuntuServer sshd[5730]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 22:58:09 UbuntuServer sshd[5730]: Failed password for root from 125.215.218.34 port 55290 ssh2 
Aug  4 22:58:15 UbuntuServer sshd[5737]: Invalid user murray from 125.215.218.34 
Aug  4 22:58:15 UbuntuServer sshd[5737]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 22:58:15 UbuntuServer sshd[5737]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 22:58:17 UbuntuServer sshd[5737]: Failed password for invalid user murray from 125.215.218.34 port 56288 ssh2 
Aug  4 22:58:24 UbuntuServer sshd[5747]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 22:58:26 UbuntuServer sshd[5747]: Failed password for root from 125.215.218.34 port 57470 ssh2 
Aug  4 22:58:32 UbuntuServer sshd[5752]: Invalid user falcon from 125.215.218.34 
Aug  4 22:58:32 UbuntuServer sshd[5752]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 22:58:32 UbuntuServer sshd[5752]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 22:58:34 UbuntuServer sshd[5752]: Failed password for invalid user falcon from 125.215.218.34 port 58584 ssh2 
Aug  4 22:58:40 UbuntuServer sshd[5756]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 22:58:42 UbuntuServer sshd[5756]: Failed password for root from 125.215.218.34 port 59954 ssh2 
Aug  4 22:58:49 UbuntuServer sshd[5764]: Invalid user fly from 125.215.218.34 
Aug  4 22:58:49 UbuntuServer sshd[5764]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 22:58:49 UbuntuServer sshd[5764]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 22:58:50 UbuntuServer sshd[5764]: Failed password for invalid user fly from 125.215.218.34 port 33365 ssh2 
Aug  4 22:58:57 UbuntuServer sshd[5772]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 22:58:59 UbuntuServer sshd[5772]: Failed password for root from 125.215.218.34 port 34410 ssh2 
Aug  4 22:59:05 UbuntuServer sshd[5778]: Invalid user gerry from 125.215.218.34 
Aug  4 22:59:05 UbuntuServer sshd[5778]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 22:59:05 UbuntuServer sshd[5778]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 22:59:07 UbuntuServer sshd[5778]: Failed password for invalid user gerry from 125.215.218.34 port 35751 ssh2 
Aug  4 22:59:13 UbuntuServer sshd[5783]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 22:59:15 UbuntuServer sshd[5783]: Failed password for root from 125.215.218.34 port 37105 ssh2 
Aug  4 22:59:21 UbuntuServer sshd[5790]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 22:59:23 UbuntuServer sshd[5790]: Failed password for root from 125.215.218.34 port 38305 ssh2 
Aug  4 22:59:29 UbuntuServer sshd[5801]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 22:59:31 UbuntuServer sshd[5801]: Failed password for root from 125.215.218.34 port 39209 ssh2 
Aug  4 22:59:37 UbuntuServer sshd[5810]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 22:59:40 UbuntuServer sshd[5810]: Failed password for root from 125.215.218.34 port 40536 ssh2 
Aug  4 22:59:46 UbuntuServer sshd[5825]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 22:59:48 UbuntuServer sshd[5825]: Failed password for root from 125.215.218.34 port 41725 ssh2 
Aug  4 22:59:54 UbuntuServer sshd[5834]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 22:59:56 UbuntuServer sshd[5834]: Failed password for root from 125.215.218.34 port 42721 ssh2 
Aug  4 23:00:04 UbuntuServer sshd[5842]: Invalid user guest from 125.215.218.34 
Aug  4 23:00:04 UbuntuServer sshd[5842]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 23:00:04 UbuntuServer sshd[5842]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 23:00:06 UbuntuServer sshd[5842]: Failed password for invalid user guest from 125.215.218.34 port 44025 ssh2 
Aug  4 23:00:13 UbuntuServer sshd[5852]: Invalid user test from 125.215.218.34 
Aug  4 23:00:13 UbuntuServer sshd[5852]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 23:00:13 UbuntuServer sshd[5852]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 23:00:15 UbuntuServer sshd[5852]: Failed password for invalid user test from 125.215.218.34 port 45296 ssh2 
Aug  4 23:00:21 UbuntuServer sshd[5871]: Invalid user test1 from 125.215.218.34 
Aug  4 23:00:21 UbuntuServer sshd[5871]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 23:00:21 UbuntuServer sshd[5871]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 23:00:24 UbuntuServer sshd[5871]: Failed password for invalid user test1 from 125.215.218.34 port 46678 ssh2 
Aug  4 23:00:30 UbuntuServer sshd[5877]: Invalid user teste from 125.215.218.34 
Aug  4 23:00:30 UbuntuServer sshd[5877]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 23:00:30 UbuntuServer sshd[5877]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 23:00:31 UbuntuServer sshd[5877]: Failed password for invalid user teste from 125.215.218.34 port 48102 ssh2 
Aug  4 23:00:37 UbuntuServer sshd[5887]: Invalid user admin from 125.215.218.34 
Aug  4 23:00:37 UbuntuServer sshd[5887]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 23:00:37 UbuntuServer sshd[5887]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 23:00:39 UbuntuServer sshd[5887]: Failed password for invalid user admin from 125.215.218.34 port 49380 ssh2 
Aug  4 23:00:45 UbuntuServer sshd[5894]: Invalid user postgres from 125.215.218.34 
Aug  4 23:00:45 UbuntuServer sshd[5894]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 23:00:45 UbuntuServer sshd[5894]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 23:00:48 UbuntuServer sshd[5894]: Failed password for invalid user postgres from 125.215.218.34 port 49229 ssh2 
Aug  4 23:00:54 UbuntuServer sshd[5903]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 23:00:55 UbuntuServer sshd[5903]: Failed password for root from 125.215.218.34 port 50228 ssh2 
Aug  4 23:01:01 UbuntuServer sshd[5909]: Invalid user webmaster from 125.215.218.34 
Aug  4 23:01:01 UbuntuServer sshd[5909]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 23:01:01 UbuntuServer sshd[5909]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 23:01:03 UbuntuServer sshd[5909]: Failed password for invalid user webmaster from 125.215.218.34 port 51409 ssh2 
Aug  4 23:01:09 UbuntuServer sshd[5916]: Invalid user web from 125.215.218.34 
Aug  4 23:01:09 UbuntuServer sshd[5916]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 23:01:09 UbuntuServer sshd[5916]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 23:01:11 UbuntuServer sshd[5916]: Failed password for invalid user web from 125.215.218.34 port 52339 ssh2 
Aug  4 23:01:17 UbuntuServer sshd[5922]: Invalid user http from 125.215.218.34 
Aug  4 23:01:17 UbuntuServer sshd[5922]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 23:01:17 UbuntuServer sshd[5922]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 23:01:19 UbuntuServer sshd[5922]: Failed password for invalid user http from 125.215.218.34 port 53624 ssh2 
Aug  4 23:01:25 UbuntuServer sshd[5927]: Invalid user httpd from 125.215.218.34 
Aug  4 23:01:25 UbuntuServer sshd[5927]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 23:01:25 UbuntuServer sshd[5927]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 23:01:27 UbuntuServer sshd[5927]: Failed password for invalid user httpd from 125.215.218.34 port 54442 ssh2 
Aug  4 23:01:33 UbuntuServer sshd[5936]: Invalid user www from 125.215.218.34 
Aug  4 23:01:33 UbuntuServer sshd[5936]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 23:01:33 UbuntuServer sshd[5936]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 23:01:35 UbuntuServer sshd[5936]: Failed password for invalid user www from 125.215.218.34 port 55878 ssh2 
Aug  4 23:01:41 UbuntuServer sshd[5942]: Invalid user www1 from 125.215.218.34 
Aug  4 23:01:41 UbuntuServer sshd[5942]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 23:01:41 UbuntuServer sshd[5942]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 23:01:43 UbuntuServer sshd[5942]: Failed password for invalid user www1 from 125.215.218.34 port 57335 ssh2 
Aug  4 23:01:49 UbuntuServer sshd[5951]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 23:01:50 UbuntuServer sshd[5951]: Failed password for root from 125.215.218.34 port 58584 ssh2 
Aug  4 23:01:57 UbuntuServer sshd[5957]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 23:01:59 UbuntuServer sshd[5957]: Failed password for root from 125.215.218.34 port 59900 ssh2 
Aug  4 23:02:05 UbuntuServer sshd[5961]: Invalid user ftp from 125.215.218.34 
Aug  4 23:02:05 UbuntuServer sshd[5961]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 23:02:05 UbuntuServer sshd[5961]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 23:02:07 UbuntuServer sshd[5961]: Failed password for invalid user ftp from 125.215.218.34 port 33069 ssh2 
Aug  4 23:02:13 UbuntuServer sshd[5971]: Invalid user ftpuser from 125.215.218.34 
Aug  4 23:02:13 UbuntuServer sshd[5971]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 23:02:13 UbuntuServer sshd[5971]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 23:02:15 UbuntuServer sshd[5971]: Failed password for invalid user ftpuser from 125.215.218.34 port 34325 ssh2 
Aug  4 23:02:21 UbuntuServer sshd[5980]: Invalid user data from 125.215.218.34 
Aug  4 23:02:21 UbuntuServer sshd[5980]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 23:02:21 UbuntuServer sshd[5980]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 23:02:23 UbuntuServer sshd[5980]: Failed password for invalid user data from 125.215.218.34 port 35675 ssh2 
Aug  4 23:02:29 UbuntuServer sshd[5991]: Invalid user oracle from 125.215.218.34 
Aug  4 23:02:29 UbuntuServer sshd[5991]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 23:02:30 UbuntuServer sshd[5991]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 23:02:32 UbuntuServer sshd[5991]: Failed password for invalid user oracle from 125.215.218.34 port 36639 ssh2 
Aug  4 23:02:38 UbuntuServer sshd[5998]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 23:02:40 UbuntuServer sshd[5998]: Failed password for root from 125.215.218.34 port 37941 ssh2 
Aug  4 23:02:46 UbuntuServer sshd[6004]: Invalid user user from 125.215.218.34 
Aug  4 23:02:46 UbuntuServer sshd[6004]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 23:02:46 UbuntuServer sshd[6004]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 23:02:47 UbuntuServer sshd[6004]: Failed password for invalid user user from 125.215.218.34 port 38932 ssh2 
Aug  4 23:02:54 UbuntuServer sshd[6010]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 23:02:56 UbuntuServer sshd[6010]: Failed password for root from 125.215.218.34 port 39957 ssh2 
Aug  4 23:03:02 UbuntuServer sshd[6018]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 23:03:04 UbuntuServer sshd[6018]: Failed password for root from 125.215.218.34 port 41189 ssh2 
Aug  4 23:03:10 UbuntuServer sshd[6023]: Invalid user install from 125.215.218.34 
Aug  4 23:03:10 UbuntuServer sshd[6023]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 23:03:10 UbuntuServer sshd[6023]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 23:03:12 UbuntuServer sshd[6023]: Failed password for invalid user install from 125.215.218.34 port 42084 ssh2 
Aug  4 23:03:18 UbuntuServer sshd[6029]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 23:03:21 UbuntuServer sshd[6029]: Failed password for root from 125.215.218.34 port 43390 ssh2 
Aug  4 23:03:27 UbuntuServer sshd[6039]: Invalid user linux from 125.215.218.34 
Aug  4 23:03:27 UbuntuServer sshd[6039]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 23:03:27 UbuntuServer sshd[6039]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 23:03:28 UbuntuServer sshd[6039]: Failed password for invalid user linux from 125.215.218.34 port 44499 ssh2 
Aug  4 23:03:34 UbuntuServer sshd[6049]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 23:03:36 UbuntuServer sshd[6049]: Failed password for root from 125.215.218.34 port 44689 ssh2 
Aug  4 23:03:42 UbuntuServer sshd[6057]: Invalid user service from 125.215.218.34 
Aug  4 23:03:42 UbuntuServer sshd[6057]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 23:03:42 UbuntuServer sshd[6057]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 23:03:45 UbuntuServer sshd[6057]: Failed password for invalid user service from 125.215.218.34 port 45457 ssh2 
Aug  4 23:03:51 UbuntuServer sshd[6063]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 23:03:52 UbuntuServer sshd[6063]: Failed password for root from 125.215.218.34 port 46314 ssh2 
Aug  4 23:03:59 UbuntuServer sshd[6071]: Invalid user demo from 125.215.218.34 
Aug  4 23:03:59 UbuntuServer sshd[6071]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 23:03:59 UbuntuServer sshd[6071]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 23:04:00 UbuntuServer sshd[6071]: Failed password for invalid user demo from 125.215.218.34 port 47739 ssh2 
Aug  4 23:04:06 UbuntuServer sshd[6080]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 23:04:08 UbuntuServer sshd[6080]: Failed password for root from 125.215.218.34 port 48565 ssh2 
Aug  4 23:04:15 UbuntuServer sshd[6092]: Invalid user mysql from 125.215.218.34 
Aug  4 23:04:15 UbuntuServer sshd[6092]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 23:04:15 UbuntuServer sshd[6092]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 23:04:17 UbuntuServer sshd[6092]: Failed password for invalid user mysql from 125.215.218.34 port 49935 ssh2 
Aug  4 23:04:23 UbuntuServer sshd[6106]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 23:04:25 UbuntuServer sshd[6106]: Failed password for root from 125.215.218.34 port 51353 ssh2 
Aug  4 23:04:31 UbuntuServer sshd[6115]: Invalid user password from 125.215.218.34 
Aug  4 23:04:31 UbuntuServer sshd[6115]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 23:04:31 UbuntuServer sshd[6115]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 23:04:33 UbuntuServer sshd[6115]: Failed password for invalid user password from 125.215.218.34 port 52205 ssh2 
Aug  4 23:04:39 UbuntuServer sshd[6121]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 23:04:41 UbuntuServer sshd[6121]: Failed password for root from 125.215.218.34 port 53632 ssh2 
Aug  4 23:04:47 UbuntuServer sshd[6132]: Invalid user pass from 125.215.218.34 
Aug  4 23:04:47 UbuntuServer sshd[6132]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 23:04:47 UbuntuServer sshd[6132]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 23:04:49 UbuntuServer sshd[6132]: Failed password for invalid user pass from 125.215.218.34 port 54590 ssh2 
Aug  4 23:04:55 UbuntuServer sshd[6145]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 23:04:57 UbuntuServer sshd[6145]: Failed password for root from 125.215.218.34 port 55997 ssh2 
Aug  4 23:05:03 UbuntuServer sshd[6155]: Invalid user system from 125.215.218.34 
Aug  4 23:05:03 UbuntuServer sshd[6155]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 23:05:03 UbuntuServer sshd[6155]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 23:05:05 UbuntuServer sshd[6155]: Failed password for invalid user system from 125.215.218.34 port 57403 ssh2 
Aug  4 23:05:11 UbuntuServer sshd[6162]: Invalid user temp from 125.215.218.34 
Aug  4 23:05:11 UbuntuServer sshd[6162]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 23:05:11 UbuntuServer sshd[6162]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 23:05:13 UbuntuServer sshd[6162]: Failed password for invalid user temp from 125.215.218.34 port 58310 ssh2 
Aug  4 23:05:19 UbuntuServer sshd[6170]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 23:05:21 UbuntuServer sshd[6170]: Failed password for root from 125.215.218.34 port 59670 ssh2 
Aug  4 23:05:27 UbuntuServer sshd[6238]: Invalid user fedora from 125.215.218.34 
Aug  4 23:05:27 UbuntuServer sshd[6238]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 23:05:27 UbuntuServer sshd[6238]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 23:05:29 UbuntuServer sshd[6238]: Failed password for invalid user fedora from 125.215.218.34 port 60509 ssh2 
Aug  4 23:05:35 UbuntuServer sshd[6248]: Invalid user falcon from 125.215.218.34 
Aug  4 23:05:35 UbuntuServer sshd[6248]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 23:05:35 UbuntuServer sshd[6248]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 23:05:37 UbuntuServer sshd[6248]: Failed password for invalid user falcon from 125.215.218.34 port 33606 ssh2 
Aug  4 23:05:43 UbuntuServer sshd[6258]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 23:05:45 UbuntuServer sshd[6258]: Failed password for root from 125.215.218.34 port 58775 ssh2 
Aug  4 23:05:51 UbuntuServer sshd[6270]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 23:05:53 UbuntuServer sshd[6270]: Failed password for root from 125.215.218.34 port 59637 ssh2 
Aug  4 23:05:59 UbuntuServer sshd[6278]: Invalid user cocolino from 125.215.218.34 
Aug  4 23:05:59 UbuntuServer sshd[6278]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 23:05:59 UbuntuServer sshd[6278]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 23:06:02 UbuntuServer sshd[6278]: Failed password for invalid user cocolino from 125.215.218.34 port 32793 ssh2 
Aug  4 23:06:08 UbuntuServer sshd[6287]: Invalid user server from 125.215.218.34 
Aug  4 23:06:08 UbuntuServer sshd[6287]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 23:06:08 UbuntuServer sshd[6287]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 23:06:10 UbuntuServer sshd[6287]: Failed password for invalid user server from 125.215.218.34 port 34191 ssh2 
Aug  4 23:06:16 UbuntuServer sshd[6292]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 23:06:18 UbuntuServer sshd[6292]: Failed password for root from 125.215.218.34 port 35154 ssh2 
Aug  4 23:06:24 UbuntuServer sshd[6298]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root 
Aug  4 23:06:26 UbuntuServer sshd[6298]: Failed password for root from 125.215.218.34 port 36664 ssh2 
Aug  4 23:06:32 UbuntuServer sshd[6309]: Invalid user master from 125.215.218.34 
Aug  4 23:06:32 UbuntuServer sshd[6309]: pam_unix(sshd:auth): check pass; user unknown 
Aug  4 23:06:32 UbuntuServer sshd[6309]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34 
Aug  4 23:06:34 UbuntuServer sshd[6309]: Failed password for invalid user master from 125.215.218.34 port 38292 ssh2 
Aug  4 23:06:43 UbuntuServer sshd[6316]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=125.215.218.34  user=root

---

### Post by loell on 2008-08-04
are you actually using ssh server? or not that you know of? 

it seems someone or something  is brute forcing it.

---

### Post by patoy on 2008-08-04
someone is trying to login to the machine.

---

### Post by Script Warlock on 2008-08-05
ya i use SSH and VNC for remote desktop pero maingat akong maglog-in using nomachine with my username at passwd...may maisuggest ba kayong security measure? or some counter measure.....

---

### Post by loell on 2008-08-05
you can use  [denyhosts]("apt:denyhosts") 

originally from [http://www.simonandjun.com/wordpress/2007/09/27/securing-ssh-with-denyhost/]("http://www.simonandjun.com/wordpress/2007/09/27/securing-ssh-with-denyhost/")

so basically after installing it, put this IP address 200.43.197.146 in **/etc/hosts.deny** file.

---

### Post by Script Warlock on 2008-08-05
oi salamat pala sa reminder eto pala yung ginamit sa kaibigan kong linux admin sa isang company d2 sa cebu....buti na lang na mention mo very salamat sa yo boss.....try ko lang install at ipatakbo to pero kung di ko mapagana ng maayos balik ako d2 sa thread para makapagtanong uli...ty again sa best supporting community ng ubuntu....

teka nga pala may firestarter at ufw ang ubuntu paano pala to mag-work together sa denyhost ala bang conflict or something?

---

### Post by Nhatz on 2008-08-05
Hehehehe :) someone's trying to hack into your box. sundin mo yung payo ni loell astig yan! hehehehehe:)

ASTIG! :guitar:

---

### Post by jsgotangco on 2008-08-05
make sure you use ssl keys as well rather than passwords

---

### Post by Dr Small on 2008-08-05
I think you ment, 'ssh keys'.
Anyhow, judging from the logs, I saw a boat load of failed logins, why would you think your system has been compromised?

---

### Post by Script Warlock on 2008-08-05
yah your right anyway why should i freak out...well some advises?

---

### Post by Script Warlock on 2008-08-05
any idea about the ssh keys? some kind of pairing? not sure of this term....can i have some suggestions from you?

---

### Post by jsgotangco on 2008-08-05
Sorry I meant SSH :)

[http://sial.org/howto/openssh/publickey-auth/](http://sial.org/howto/openssh/publickey-auth/)
[http://www.onlamp.com/pub/a/onlamp/excerpt/ssh_8/](http://www.onlamp.com/pub/a/onlamp/excerpt/ssh_8/)

---

### Post by loell on 2008-08-05
> **boyet said:**
> any idea about the ssh keys? some kind of pairing? not sure of this term....can i have some suggestions from you?

just adding to what sir jerome already pointed above, since you're using nomchine freenx as your client, you also need to import those generated keys

[http://www.nomachine.com/ar/view.php?ar_id=AR01C00126]("http://www.nomachine.com/ar/view.php?ar_id=AR01C00126")

---

### Post by Script Warlock on 2008-08-05
[COLOR="Blue"]another lesson to learn[/COLOR] hindi ko namalayan ang sa mga keys maraming salamat po mga bros...... :guitar:

---

