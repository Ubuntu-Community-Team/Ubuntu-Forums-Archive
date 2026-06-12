---
title: "&quot;Software&quot; not working (Clamav, Torbrowser etc not working properly)"
date: 2017-11-02
forum: New to Ubuntu
---

### Post by smith73 on 2017-11-02
I'm running dual boot Windows 8.1 and Ubuntu Mate 16.04 and now the following problems emerged.
(Donno if this is relevant, but I was unable to install Ubuntu Mate manually in dual boot (although ok in single boot), so it has been installed automatically
and basically the load time is the same or slower that Windows).

Around a several weeks ago while updating and upgrading some errors regarding LibreOffice installation had been displayed. Now checking with clamtk several dozen
possible threats PUA.Doc.Tool.LibreOfficeMacro-2 and one PUA.Win.Exploit.CVE_2012_0110-1 are displayed, however by recursive clamscan via terminal it displays the following:

```
SCAN SUMMARY -----------
 Known viruses: 6328587
 Engine version: 0.99.2
 Scanned directories: 62397
 Scanned files: 262943
 Infected files: 0
 Total errors: 21894
 Data scanned: 18633.91 MB
 Data read: 63838.83 MB (ratio 0.29:1)
 Time: 7072.735 sec (117 m 52 s)
```

Also by running freshclam as root it shows the following in the terminal:
```
ERROR: /var/log/clamav/freshclam.log is locked by another process
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).
```
and basically never shows updating in terminal.
By opening this log via GUI as root some recent clam updates have been registered.

 
 
The following Clamav error has also once been displayed by running verbose recursive clamscan:
```
LibClamavWarning: fmap_readpage: pread_fail asked for 4077 bytes @ offset 19, got 0
Warning: can't open file sys/module/snd_soc_sst_match/uevent Permission denied
```

Also while updating and upgrading via terminal the following had been displayed once:
```
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1_01.bin for module i915 
```
(same message for kbl_guc_ver9_14.bin and kbl_guc_ver8_7.bin)


By running updates via terminal the following is displayed each time after updating:
```
W: The repository 'http://ppa.launchpad.net/jonls/redshift-ppa/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://ppa.launchpad.net/jonls/redshift-ppa/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/jonls/redshift-ppa/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found
 E: Some index files failed to download. They have been ignored, or old ones used instead.
```

I installed Tor browser via Software boutique and it is not opened via Applications->Internet (any time while opening
it downloads and installs Tor browser afresh and shows a message that signature verification failed and there may be
networking or security issues, so I open it from the files of direct download).

Now the main problem is that "Software" from "Applications" in menu bar can't be launched (after clicking the cursor is busy for a while
and then returns to previous basic state with no installed software window opened.).
Any help on what's happening and how to fix it?

Thanks

---

### Post by smith73 on 2017-11-02
I do not have Wine installed and am running Windows 8 via Virtual Box for Remote Desktop connectivity which had failed to establish via Ubuntu Remmina app. 
I've set RAM value to 2048 mb (having in total of 4 GB on the ASUS machine), but VM displays incorrect settings message that more RAM is used (3,75 GB) 
which may not be sufficient for the host machine, though 2048 mb is displayed as set for Win8 settings.

---

### Post by smith73 on 2017-11-04
Can anyone please help on how to fix the "Software Center" in "Applications" to display the list of apps installed? And preferentially how to fix
the VM incorrect RAM settings message? 

Or at least what commands to use to get more information? I'll try clamscan with extended settings to see what these 21894 errors are.

---

