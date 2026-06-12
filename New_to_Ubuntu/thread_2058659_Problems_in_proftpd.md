---
title: "Problems in proftpd"
date: 2012-09-16
forum: New to Ubuntu
---

### Post by kevz1337 on 2012-09-16
I got the error ProFTPD warning: cannot start neither in standalone nor in inetd/xinetd mode. Check your configuration.

And i have checked the .conf file but cant see anything wrong. what sould i do? it is anything wrong in my config file? or what else can i do?

[PHP]AllowOverwrite on
AuthAliasOnly on

UserAlias             kevz userftp

ServerName            &quot;kevzftp&quot;
ServerType             standalone
DeferWelcome            on

MultilineRFC2228         on
DefaultServer            on
ShowSymlinks            off

TimeoutNoTransfer         600
TimeoutStalled             100
TimeoutIdle             2200

DisplayFirstChdir               .message
ListOptions                    &quot;-l&quot;

RequireValidShell         off

TimeoutLogin 20

RootLogin             on

ExtendedLog             /var/log/ftp.log
TransferLog             /var/log/xferlog
SystemLog            /var/log/syslog.log

UseFtpUsers             off

AllowStoreRestart        on


Port                2121

MaxInstances 8

User                   userftp
Group                     workgroup

Umask                022    022

PersistentPasswd        off

MaxClients             8
MaxClientsPerHost         8
MaxClientsPerUser         8
MaxHostsPerUser         8

AccessGrantMsg &quot;Hei&quot;

ServerIdent                      on       &quot;you're at home&quot;

DefaultRoot             /home/FTP-shared

DefaultRoot             ~

MaxLoginAttempts            5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
    <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
    DenyAll
    </Limit>
</Directory>

<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
    <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
    DenyAll
    </Limit>
</Directory>

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
    <Limit READ RMD DELE>
          DenyAll
        </Limit>

        <Limit STOR CWD MKD>
          AllowAll
        </Limit>
</Directory>[/PHP]

---

### Post by JKyleOKC on 2012-09-16
You need to add at least these two lines at the top of your proftpd.conf file, to make it run in standalone mode:```
ServerName            "Debian"
ServerType            standalone
```Otherwise you need to modify your xinetd configuration. I can't help with that; I've used only the standalone mode for the past 10 years or so...

You can make the "ServerName" entry anything you like, this is just the default created by the repository package. The original installation creates a full proftpd.conf file with lots of comments to tell how to modify it; yours appears to be a highly edited version.

EDIT: Ooops!!! I see you already have the necessary lines, but apparently php has replaced the quote marks with the HTML entity for them, making the file unusable by proftpd.

Use a standard text editor, not php, to correct things and see if that works properly.

Sorry for not reading your file closely enough in the first place!

---

### Post by kevz1337 on 2012-09-16
I should try that, as soon as i can. Thank you :-)

---

