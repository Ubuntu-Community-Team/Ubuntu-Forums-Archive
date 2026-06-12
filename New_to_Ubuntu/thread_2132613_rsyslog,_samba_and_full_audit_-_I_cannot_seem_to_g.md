---
title: "rsyslog, samba and full_audit - I cannot seem to get it to work; please help!"
date: 2013-04-05
forum: New to Ubuntu
---

### Post by RiotSloth on 2013-04-05
Hi guys

Sorry, this is a real noob question I'm sure.  I am trying to log full_audit on my samba windows shares so I know who is creating, deleting, renaming, moving etc. files and directories in the samba/windows share.

In my etc/samba/smb.conf file, under [global] I have:


[FONT=courier new][I][COLOR=#666666]# Audit settings
[/COLOR]full_audit: prefix = [COLOR=#000000]**%**[/COLOR]u[COLOR=#000000]**|%**[/COLOR]I[COLOR=#000000]**|%**[/COLOR]S
full_audit:failure = connect
full_audit:success = connect disconnect opendir [COLOR=#C20CB9]**mkdir**[/COLOR] [COLOR=#C20CB9]**rmdir**[/COLOR] closedir open close [COLOR=#C20CB9]**read**[/COLOR] pread [COLOR=#C20CB9]**write**[/COLOR] pwrite sendfile rename [COLOR=#C20CB9]**unlink**[/COLOR] [COLOR=#C20CB9]**chmod**[/COLOR]fchmod [COLOR=#C20CB9]**chown**[/COLOR] fchown chdir ftruncate lock symlink [COLOR=#C20CB9]**readlink**[/COLOR] [COLOR=#C20CB9]**link**[/COLOR] [COLOR=#C20CB9]**mknod**[/COLOR] realpath
full_audit:facility = local5
full_audit: priority = notice[/I][/FONT]

And under my [file share name] I have:

[FONT=courier new][I]vfs object = full_audit
[/I][/FONT]
I created a new file in etc/rsyslog.d called [FONT=courier new]*[COLOR=#110000]00-samba-audit.conf[/COLOR]*[/FONT] with these two lines in:

[FONT=courier new][I]local5.notice /var/log/samba/audit.log
&~[/I][/FONT]

And in the file /etc/rsyslog.d/50-default.conf I changed the following line:

[FONT=courier new]**.*;auth,authpriv.none           -/var/log/syslog*[/FONT]

to read:

[FONT=courier new]**.*;local5,auth,authpriv.none           -/var/log/syslog*[/FONT]

with this below it:

[FONT=courier new]*local5.notice /var/log/samba/audit.log*[/FONT]

I then restarted samba and rsyslog.  (This all comes from this web page: [http://a32.me/2009/10/samba-audit-trail/](http://a32.me/2009/10/samba-audit-trail/))It creates the audit.log file in my /var/log/samba/ directory but nothing else   [FONT=Verdana]happens;[/FONT][FONT=Verdana] it remains empty.[/FONT]
What am I doing wrong?!  I would be really grateful if someone could help me to audit my windows/samba share so I know who is creating, moving, deleting, renaming files etc.

Many thanks 
 
:)

RiotSloth

---

### Post by RiotSloth on 2013-04-08
Anyone?  Or even a suggestion to post elsewhere? Please? :)

---

