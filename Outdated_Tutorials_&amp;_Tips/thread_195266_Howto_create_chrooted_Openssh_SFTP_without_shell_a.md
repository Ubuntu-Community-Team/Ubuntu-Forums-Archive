---
title: "Howto create chrooted Openssh SFTP without shell access through rssh for Dapper"
date: 2006-06-12
forum: Outdated Tutorials &amp; Tips
---

### Post by jchau on 2006-06-12
The instructions for [Howto create chrooted Openssh SFTP without shell access through rssh.]("http://ubuntuforums.org/showthread.php?t=128206") should still work for Dapper as well as they did for Breezy.  However, those who updated to Dapper after they setup rssh for Breezy probably will notice that the setup does not work anymore.  

The following instructions are for those who had the rssh setup before upgrading to Dapper.  If you never setup the chrooted sftp access without shell access through rssh, the old instructions should work fine for a fresh Dapper install.  





After the upgrade to Dapper, I found that my chrooted sftp using rssh setup no longer allowed users to log in.  In order to remedy this problems several steps need to be done.

First, since the Dapper upgrade updated many packages including rssh and OpenSSH, your mkchroot.sh script needs to be re-run. 

If you still have the modified script you made for the rssh setup in Breezy, you can use that one without further.  However, if you do not have the modified script, you can get the original by "gunzip"ing "/usr/share/doc/rssh/examples/mkchroot.sh.gz".  You can move your new mkchroot anywhere you like.  Now open (not run) it and modify the line
```
sftp_server_path="/usr/lib/sftp-server"
```
to become
```
sftp_server_path="/usr/lib/openssh/sftp-server"
```
because that is where the sftp-server is located.

Make sure the mkchroot.sh script is executable, and execute the following command in directory containing the modified mkchroot.sh script:
```
sudo ./mkchroot /home/chroot
```
where "/home/chroot" is the chroot directory you created in the Breezy install.  

As before, this script will give an error when copying "linux-gate.so.1" and "/lib/ld-linux.so.2" over to the chroot directory.  To fix this again, simply execute the command:
```
sudo cp /lib/ld-linux.so.2 /home/chroot/lib/ld-linux.so.2
```
You should not need to copy "linux-gate.so.1".  For more information about this, consult the instructions for chrooted sftp using rssh for Breezy.

As in Breezy, rssh_chroot_helper in /usr/lib/rssh/rssh_chroot_helper will need to be suid root.  To accomplish this,
```
sudo chmod u+s /usr/lib/rssh/rssh_chroot_helper
```

[color=green]As an extra precaution

Unlike Breezy however, rssh now knows the correct location of sftp-server.  So "/etc/ssh/sshd_config" needs to be changed back.  The line
```
Subsystem sftp /usr/lib/sftp-server
```
needs to be changed back to 
```
Subsystem sftp /usr/lib/openssh/sftp-server
```
You can also delete the symbolic link from "/usr/lib/sftp-server" to "/usr/lib/openssh/sftp-server" if you like, but I left the link there.

If during the upgrade to Dapper, you allowed "/etc/init.d/sysklogd" to be changed, you will need to modify the line:
```
SYSLOGD="-u syslog"
```
to become
```
SYSLOGD="-a /home/chroot/dev/log -u syslog"
```

Finally, the /home/chroot/etc/passwd file will need to be created/modified, if it has not been created or modified.  By modification, I mean removing the users who do not need to be there.  See the instructions for the Breezy setup for more information.

If I missed anything, please feel free to add to this thread.

---

