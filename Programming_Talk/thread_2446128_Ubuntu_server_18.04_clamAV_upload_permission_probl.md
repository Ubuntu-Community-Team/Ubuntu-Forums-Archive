---
title: "Ubuntu server 18.04: clamAV upload permission problem"
date: 2020-06-25
forum: Programming Talk
---

### Post by erotavlas on 2020-06-25
Hi,
I  have ubuntu 18.04.4 64 bit with ClamAV 0.102.3/25850, apache 2.4.43 (installed from [third party repositories]("https://launchpad.net/~ondrej/+archive/ubuntu/apache2")) and PHP 7.2.24-0ubuntu0.18.04.6 with Zend OPcache v7.2.24-0ubuntu0.18.04.6.

If I configure the web server with PHP apache handler (file /etc/php/7.2/apache2/php.ini), whenever there is an upload of a file, clamAV fails:
```
*/tmp/phpzk3YWh: lstat() failed: No such file or directory. ERROR*
```
ClamAV user has write access to web server folders and is member of www-data group (the membership status does not change anything).
If I configure the web server with PHP fast-cgi (file /etc/php/7.2/fpm/php.ini), I do not have any problem with clamAV. Both files /etc/php/7.2/apache2/php.ini and /etc/php/7.2/fpm/php.ini are practically equal.
The server dir is default one, I changed memory parameters and opcache parameters:
```

; Defaults to the system default (see sys_get_temp_dir)
;sys_temp_dir = "/tmp"

memory_limit=128M
post_max_size=128M
upload_max_filesize=128M
max_execution_time=600

[opcache]
opcache.enable=1
opcache.memory_consumption=128
opcache.max_accelerated_files=10000
opcache.use_cwd=1
opcache.validate_timestamps=1
opcache.revalidate_freq=60
opcache.save_comments=1
opcache.enable_file_override=0
```

/etc/clamav/clamd.conf modified according to this [https://www.clamav.net/documents/on-access-scanning](https://www.clamav.net/documents/on-access-scanning)
```

LocalSocket /var/run/clamav/clamd.ctl
FixStaleSocket true
# TemporaryDirectory is not set to its default /tmp here to make overriding
# the default with environment variables TMPDIR/TMP/TEMP possible
User root
ScanMail true
ScanArchive true
ArchiveBlockEncrypted false
MaxDirectoryRecursion 15
FollowDirectorySymlinks false
FollowFileSymlinks false
ReadTimeout 180
MaxThreads 12
MaxConnectionQueueLength 15
StreamMaxLength 10M
LogFileMaxSize 0
LogSyslog false
LogFacility LOG_LOCAL6
LogClean false
LogVerbose true
PidFile /var/run/clamav/clamd.pid
DatabaseDirectory /var/lib/clamav
SelfCheck 3600
Foreground false
Debug false
ScanPE true
ScanOLE2 true
ScanHTML true
AlertBrokenExecutables false
ExitOnOOM false
LeaveTemporaryFiles false
AlgorithmicDetection true
ScanELF true
IdleTimeout 30
PhishingSignatures true
PhishingScanURLs true
PhishingAlwaysBlockSSLMismatch false
PhishingAlwaysBlockCloak false
DetectPUA false
ScanPartialMessages false
HeuristicScanPrecedence false
StructuredDataDetection false
CommandReadTimeout 5
SendBufTimeout 200
MaxQueue 100
LogFile /var/log/clamav/clamav.log
LogTime true
LogFileUnlock false
LogFileMaxSize 0
Bytecode true
BytecodeSecurity TrustSigned
BytecodeTimeout 60000
OfficialDatabaseOnly false
CrossFilesystems true
ScanArchive true
```

---

