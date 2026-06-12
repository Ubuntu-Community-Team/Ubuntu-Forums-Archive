---
title: "RKhunter log file"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by nishanvincent on 2008-09-05
Please can someone check this rkhunter log file and tell me if there is anything wrong. I am getting many waring messages.

[18:01:46] /bin/ip                                           [ Warning ]
[18:01:46] Warning: The file properties have changed:
[18:01:46]          File: /bin/ip
[18:01:46]          Current inode: 485012    Stored inode: 483375
[18:01:46]          Current file modification time: 1215618519
[18:01:46]          Stored file modification time : 1207985171
[18:01:46] /bin/kill                                         [ Warning ]
[18:01:46] Warning: The file properties have changed:
[18:01:46]          File: /bin/kill
[18:01:46]          Current hash: 5f85ce91eafbd85f79441f71ecad0f0db722c1bf
[18:01:46]          Stored hash : 18e7cde8dfbeac32608ae47f857d2b168cfc72cb
[18:01:46]          Current inode: 484137    Stored inode: 483377
[18:01:46]          Current file modification time: 1215682114
[18:01:46]          Stored file modification time : 1205447087
[18:01:47] /bin/ps                                           [ Warning ]
[18:01:47] Warning: The file properties have changed:
[18:01:47]          File: /bin/ps
[18:01:47]          Current hash: 62c7d1839f644c5dfb6179015e7e3017ac6a6afa
[18:01:47]          Stored hash : 7cbcd8aa6df2ffbfbe783ae7fe7d1ea5a790ed81
[18:01:47]          Current inode: 484204    Stored inode: 483413
[18:01:47]          Current file modification time: 1215682114
[18:01:47]          Stored file modification time : 1205447087
[18:01:54] /usr/bin/top                                      [ Warning ]
[18:01:54] Warning: The file properties have changed:
[18:01:54]          File: /usr/bin/top
[18:01:54]          Current hash: 44a0ffadc915dbfee905ddf267eec4d4a00ddc0a
[18:01:54]          Stored hash : 2bdb1ac9ff1361716edf86da5946e7bd3facd39e
[18:01:54]          Current inode: 365316    Stored inode: 361488
[18:01:55]          Current file modification time: 1215682114
[18:01:55]          Stored file modification time : 1205447087
[18:01:55] /usr/bin/vmstat                                   [ Warning ]
[18:01:55] Warning: The file properties have changed:
[18:01:55]          File: /usr/bin/vmstat
[18:01:55]          Current hash: d1cd4f460631b3da1d1591d21cce213fff21bfcf
[18:01:55]          Stored hash : 202013298ba7b465c485db690c81b51a094b2484
[18:01:55]          Current inode: 365317    Stored inode: 361564
[18:01:55]          Current file modification time: 1215682114
[18:01:55]          Stored file modification time : 1205447087
[18:01:55] /usr/bin/w                                        [ Warning ]
[18:01:55] Warning: The file properties have changed:
[18:01:55]          File: /usr/bin/w
[18:01:55]          Current hash: fb2819df7d1c7a261311a105100fcae1333b71e7
[18:01:55]          Stored hash : 1afb9e68b386be6926900bf05585f9d8fff4ecf2
[18:01:56] /usr/bin/watch                                    [ Warning ]
[18:01:56] Warning: The file properties have changed:
[18:01:56]          File: /usr/bin/watch
[18:01:56]          Current hash: 11794147771ea0c82010a929013d620ab555f067
[18:01:56]          Stored hash : 4c674887699b7866e1325b190bcf40183e439b5d
[18:01:56]          Current inode: 365318    Stored inode: 361573
[18:01:56]          Current file modification time: 1215682114
[18:01:56]          Stored file modification time : 1205447087
[18:01:57] Info: Found file '/usr/bin/lwp-request': it is whitelisted for the 'script replacement' check.
[18:01:57] /usr/bin/w.procps                                 [ Warning ]
[18:01:57] Warning: The file properties have changed:
[18:01:57]          File: /usr/bin/w.procps
[18:01:57]          Current hash: fb2819df7d1c7a261311a105100fcae1333b71e7
[18:01:57]          Stored hash : 1afb9e68b386be6926900bf05585f9d8fff4ecf2
[18:01:57]          Current inode: 365324    Stored inode: 361569
[18:01:57]          Current file modification time: 1215682114
[18:01:57]          Stored file modification time : 1205447087
[18:01:58] /sbin/ip                                          [ Warning ]
[18:01:58] Warning: The file properties have changed:
[18:01:58]          File: /sbin/ip
[18:01:58]          Current inode: 245836    Stored inode: 245817
[18:01:58]          Current file modification time: 1217960359
[18:01:58]          Stored file modification time : 1216890406
[18:01:59] /sbin/sysctl                                      [ Warning ]
[18:01:59] Warning: The file properties have changed:
[18:01:59]          File: /sbin/sysctl
[18:01:59]          Current hash: 766ec5bbeaff6678203d5e78b2b173a5026c8870
[18:01:59]          Stored hash : d212033ab99f586e64725af5770d0eaeed172ffe
[18:01:59]          Current inode: 245777    Stored inode: 245910
[18:01:59]          Current file modification time: 1215682114
[18:01:59]          Stored file modification time : 1205447087
[18:02:35] Performing filesystem checks
[18:02:35] Info: Starting test name 'filesystem'
[18:02:35] Info: SCAN_MODE_DEV set to 'THOROUGH'
[18:02:46]   Checking /dev for suspicious file types         [ Warning ]
[18:02:46] Warning: Suspicious file types found in /dev:
[18:02:46]          /dev/shm/pulse-shm-2287382856: data
[18:02:47]   Checking for hidden files and directories       [ Warning ]
[18:02:47] Warning: Hidden directory found: /etc/.java
[18:02:47] Warning: Hidden directory found: /dev/.static
[18:02:47] Warning: Hidden directory found: /dev/.udev
[18:02:47] Warning: Hidden directory found: /dev/.initramfs

---

### Post by gandaran on 2008-09-05
no, theres nothing wrong there, the file properties change are due to updates.
run the file update command to stop getting the warnings,
code: **sudo rkhunter --propupd** 
for the hidden files found, edit rkhunter
code: **sudo gedit /etc/rkhunter.conf**

---

### Post by nishanvincent on 2008-09-05
Thanks for the reply..... 
The first command helped but need some help with the second command
Could you please also tell me what exactly should i change afer executing 
code: sudo gedit /etc/rkhunter.conf
thanks again

This is warning message now. Little concerned about one of those.
[23:24:29] Warning: Suspicious file types found in /dev:
[23:24:29]          /dev/shm/pulse-shm-1746895747: data

---------------------------------------------------

[23:24:18] Performing filesystem checks
[23:24:18] Info: Starting test name 'filesystem'
[23:24:18] Info: SCAN_MODE_DEV set to 'THOROUGH'
[23:24:29]   Checking /dev for suspicious file types         [ Warning ]
[23:24:29] Warning: Suspicious file types found in /dev:
[23:24:29]          /dev/shm/pulse-shm-1746895747: data
[23:24:30]   Checking for hidden files and directories       [ Warning ]
[23:24:30] Warning: Hidden directory found: /etc/.java
[23:24:30] Warning: Hidden directory found: /dev/.static
[23:24:30] Warning: Hidden directory found: /dev/.udev
[23:24:30] Warning: Hidden directory found: /dev/.initramfs

---

### Post by gandaran on 2008-09-05
scroll down to the hidden directory section and uncomment the corresponding warnings line, you can add any line if it's not there.
in the ALLOWDEVFILE section add this line: ALLOWDEVFILE=/dev/shm/pulse-shm-*

---

### Post by nishanvincent on 2008-09-06
Thanks for the help.

---

### Post by Diabolis on 2008-10-26
This is not a fix actually, you are just hiding the warnings by telling to rkhunter to skip them in subsequent scans. It is good if you are sure about the legitimity of the files tho.

---

