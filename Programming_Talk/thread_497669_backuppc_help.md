---
title: "backuppc help"
date: 2007-07-10
forum: Programming Talk
---

### Post by jeff00z28 on 2007-07-10
a particular directory on a server that is being backed up keeps causing a backup job to fail. I am trying to exclude that directory from being backed up.

I will post the first few lines of the Xferlog, however the rest is pretty much more of the same

 fail because: Call timed out: server did not respond after 20000 milliseconds listing \data\cmrl\Images\hla\g\*
Call timed out: server did not respond after 20000 milliseconds listing \data\cmrl\Images\hla\g\*
Call timed out: server did not respond after 20000 milliseconds listing \data\cmrl\Images\hla\n\*
Call timed out: server did not respond after 20000 milliseconds listing \data\cmrl\Images\hla\r\*
Call timed out: server did not respond after 20000 milliseconds listing \data\cmrl\Images\hla\w\*
Call timed out: server did not respond after 20000 milliseconds listing \data\cmrl\Images\hla\y\*
Call timed out: server did not respond after 20000 milliseconds opening remote file \data\cmrl\Images\hla.bmp (\data\cmrl\Images\)
Call timed out: server did not respond after 20000 milliseconds opening remote file \data\cmrl\Images\h (\data\cmrl\Images\)
Call timed out: server did not respond after 20000 milliseconds opening remote file \data\cmrl\Images\h (\data\cmrl\Images\)
Call timed out: server did not respond after 20000 milliseconds opening remote file \data\cmrl\Images\h (\data\cmrl\Images\)
Call timed out: server did not respond after 20000 milliseconds opening remote file \data\cmrl\Images\h (\data\cmrl\Images\)
Call timed out: server did not respond after 20000 milliseconds opening remote file \data\cmrl\Images\h (\data\cmrl\Images\)

Heres us what I have entered in the config.pl for that backup job so far.

$Conf{SmbShareUserName} = 'databak';
$Conf{SmbSharePasswd} = 'FP266c2169';
$Conf{SmbShareName} = ['AccessDB','Documents', 'Share'];


$Conf{BackupFilesExclude} = ['/data/cmrl/Images/*','/data/cmrl/Images','/data/cmrl/Images/','Images', 'Images/','Images/*','data/cmrl/Images','data/cmrl/Images/*','/Images','/Images/','/Images/*'];

________
help would be appreciated

---

### Post by jeff00z28 on 2007-07-12
ttt

---

