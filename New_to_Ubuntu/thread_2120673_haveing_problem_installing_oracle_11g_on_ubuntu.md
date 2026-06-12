---
title: "haveing problem installing oracle 11g on ubuntu"
date: 2013-02-27
forum: New to Ubuntu
---

### Post by damoojeje on 2013-02-27
pls i followed all dew process but still getting this error pls help
damie@damie-TOSHIBA-NB255:~$ su oracle
Password: 
oracle@damie-TOSHIBA-NB255:/home/damie$ cd stage
bash: cd: stage: No such file or directory
oracle@damie-TOSHIBA-NB255:/home/damie$ ls
Desktop Downloads Music Pictures Templates Videos
Documents examples.desktop NewFolder Public Ubuntu One
oracle@damie-TOSHIBA-NB255:/home/damie$ cd ..
oracle@damie-TOSHIBA-NB255:/home$ cd ..
oracle@damie-TOSHIBA-NB255:/$ ls
bin dev initrd.img media proc sbin stage tmp var
boot etc lib mnt root selinux sys u01 vmlinuz
cdrom home lost+found opt run srv sysctl.conf usr
oracle@damie-TOSHIBA-NB255:/$ cd stage
oracle@damie-TOSHIBA-NB255:/stage$ cd database
oracle@damie-TOSHIBA-NB255:/stage/database$ ./runInstaller
Starting Oracle Universal Installer...

Checking Temp space: must be greater than 80 MB. Actual 6164 MB Passed
Checking swap space: must be greater than 150 MB. Actual 948 MB Passed
Checking monitor: must be configured to display at least 256 colors
&amp;amp;gt;&amp;amp;gt;&amp;amp;gt; Could not execute auto check for display colors using command /usr/bin/xdpyinfo. Check if the DISPLAY variable is set. Failed &amp;amp;lt;&amp;amp;lt;&amp;amp;lt;&amp;amp;lt;

Some requirement checks failed. You must fulfill these requirements before

continuing with the installation,

Continue? (y/n) [n] y


&amp;amp;gt;&amp;amp;gt;&amp;amp;gt; Ignoring required pre-requisite failures. Continuing...
Preparing to launch Oracle Universal Installer from /tmp/OraInstall2013-02-26_08-33-21PM. Please wait ...oracle@damie-TOSHIBA-NB255:/stage/database$ No protocol specified
No protocol specified
Exception in thread &amp;amp;quot;main&amp;amp;quot; java.lang.NoClassDefFoundError
at java.lang.Class.forName0(Native Method)
at java.lang.Class.forName(Class.java:164)
at java.awt.Toolkit$2.run(Toolkit.java:821)
at java.security.AccessController.doPrivileged(Native Method)
at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:804)
at com.jgoodies.looks.LookUtils.isLowResolution(Unknown Source)
at com.jgoodies.looks.LookUtils.&amp;amp;lt;clinit&amp;amp;gt;(Unknown Source)
at com.jgoodies.looks.plastic.PlasticLookAndFeel.&amp;amp;lt;clinit&amp;amp;gt;(PlasticLookAndFeel.java:122)
at java.lang.Class.forName0(Native Method)
at java.lang.Class.forName(Class.java:242)
at javax.swing.SwingUtilities.loadSystemClass(SwingUtilities.java:1783)
at javax.swing.UIManager.setLookAndFeel(UIManager.java:480)
at oracle.install.commons.util.Application.startup(Application.java:758)
at oracle.install.commons.flow.FlowApplication.startup(FlowApplication.java:164)
at oracle.install.commons.flow.FlowApplication.startup(FlowApplication.java:181)
at oracle.install.commons.base.driver.common.Installer.startup(Installer.java:265)
at oracle.install.ivw.db.driver.DBInstaller.startup(DBInstaller.java:114)
at oracle.install.ivw.db.driver.DBInstaller.main(DBInstaller.java:132)
[EMAIL="oracle@damie-TOSHIBA-NB255:/stage/database$"]oracle@damie-TOSHIBA-NB255:/stage/database$[/EMAIL]
 
and also how can I fix this problem of "Checking monitor: must be configured to display at least 256 colors
&amp;amp;gt;&amp;amp;gt;&amp;amp;gt; Could not execute auto check for display colors using command /usr/bin/xdpyinfo. Check if the DISPLAY variable is set. Failed "

---

