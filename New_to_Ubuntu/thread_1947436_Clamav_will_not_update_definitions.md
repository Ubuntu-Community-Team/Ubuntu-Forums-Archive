---
title: "Clamav will not update definitions"
date: 2012-03-26
forum: New to Ubuntu
---

### Post by Roger49 on 2012-03-26
Hi there,
I've installed ClamAV from the repository.
I was worried when it told me it was outdated, but I've looked around at other threads, and found it was nothing to worry about. The problem is that "sudo freshclam" has never worked for me.
I get this:
```

ClamAV update process started at Mon Mar 26 20:05:26 2012
main.cvd is up to date (version: 54, sigs: 1044387, f-level: 60, builder: sven)
WARNING: Current functionality level = 58, recommended = 60
Please check if ClamAV tools are linked against the proper version of libclamav
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
WARNING: getpatch: Can't download daily-14528.cdiff from db.local.clamav.net
WARNING: getpatch: Can't download daily-14528.cdiff from db.local.clamav.net
WARNING: getpatch: Can't download daily-14528.cdiff from db.local.clamav.net
WARNING: getpatch: Can't download daily-14528.cdiff from db.local.clamav.net
WARNING: getpatch: Can't download daily-14528.cdiff from db.local.clamav.net
WARNING: Incremental update failed, trying to download daily.cvd
WARNING: Can't download daily.cvd from db.local.clamav.net
Trying again in 5 secs...
```I've installed ClamTK, and the first three items, Antivirus engine, GUI Version and Virus Definitions have red "No Entry" signs against them.

Looking elsewhere on this site, someone had a similar problem in 2009, but the remedy, (stop the daemon, run clamscan -v, restart the daemon) does not work.

I get this:
```

roger@roger-desktop:~$ sudo freshclam -v
Current working dir is /var/lib/clamav
Max retries == 5
ClamAV update process started at Mon Mar 26 20:17:14 2012
Using IPv6 aware code
Querying current.cvd.clamav.net
TTL: 900
Software version from DNS: 0.97.4
main.cvd version from DNS: 54
main.cvd is up to date (version: 54, sigs: 1044387, f-level: 60, builder: sven)
WARNING: Current functionality level = 58, recommended = 60
Please check if ClamAV tools are linked against the proper version of libclamav
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
daily.cvd version from DNS: 14703
Retrieving [http://db.local.clamav.net/daily-14528.cdiff](http://db.local.clamav.net/daily-14528.cdiff)
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
Ignoring mirror 193.1.193.64 (has connected too many times with an outdated version)
Ignoring mirror 163.1.3.8 (has connected too many times with an outdated version)
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
Ignoring mirror 193.1.193.64 (has connected too many times with an outdated version)
Ignoring mirror 163.1.3.8 (has connected too many times with an outdated version)
WARNING: getpatch: Can't download daily-14528.cdiff from db.local.clamav.net
Retrieving [http://db.local.clamav.net/daily-14528.cdiff](http://db.local.clamav.net/daily-14528.cdiff)

```I also get this:
```

roger@roger-desktop:~$ sudo /etc/init.d/clamav-freshclam start
 * Starting ClamAV virus database updater freshclam                                                                                   [ OK ] 
roger@roger-desktop:~$ freshclam -v
ERROR: Can't open /var/log/clamav/freshclam.log in append mode (check permissions!).
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).
roger@roger-desktop:~$ 

```I would be grateful for any suggestions, I have to swap emails with Windows users on a fairly regular basis.
Best regards,
Roger49

---

### Post by EzioAuditore on 2012-03-26
sorry not much of help here but have you tried manually downloading the update (signature) files from their site? As far as I remember, you just have to overwrite the previous sig. files with the downloaded ones.
Just search for the file names similar to the download files, replace them and reload Clam.

[http://www.clamav.net/lang/en/](http://www.clamav.net/lang/en/)

You can download all 4 if you wish but above two are must.

> ClamAV Virus Databases:
main.cvd ver. 54 released on 11 Oct 2011 10:34 :0400 (sig count: 1044387)
daily.cvd ver. 14703 released on 26 Mar 2012 11:22 :0400 (sig count: 140468)
bytecode.cvd ver. 168 released on 08 Mar 2012 15:53 :0500 (sig count: 38)
safebrowsing.cvd ver. 37191 released on 26 Mar 2012 15:00 :0400 (sig count: 1099229)

---

### Post by NikTh on 2012-03-26
Hello , 
> **Roger49 said:**
> 
[SIZE=3]I've installed ClamAV from the repository.
[/SIZE]
What repository ? 



> **Roger49 said:**
> [SIZE=3]I also get this:[/SIZE]
```

roger@roger-desktop:~$ sudo /etc/init.d/clamav-freshclam start
 * Starting ClamAV virus database updater freshclam                                                                                   [ OK ] 
roger@roger-desktop:~$ freshclam -v
ERROR: Can't open /var/log/clamav/freshclam.log in append mode **(check permissions!).**
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).
roger@roger-desktop:~$ 

```[SIZE=3]
[/SIZE]
As for this error i think you missed it. It wants "**sudo** freshclam -v"


Also try this to see if works 
```
sudo freshclam -v --no-dns
``` 
Thanks

---

### Post by Roger49 on 2012-03-27
Hi Ezio,
Thanks for the link.
I will keep that course of action in reserve.
Regards,
Roger.

---

### Post by Roger49 on 2012-03-27
Hi NikTh,
Sorry, I installed Clam via Synaptic.

"sudo freshclam -v" produced this:

```

roger@roger-desktop:~$ sudo freshclam -v
[sudo] password for roger: 
Current working dir is /var/lib/clamav
Max retries == 5
ClamAV update process started at Tue Mar 27 21:00:43 2012
Using IPv6 aware code
Querying current.cvd.clamav.net
TTL: 749
Software version from DNS: 0.97.4
main.cvd version from DNS: 54
main.cvd is up to date (version: 54, sigs: 1044387, f-level: 60, builder: sven)
WARNING: Current functionality level = 58, recommended = 60
Please check if ClamAV tools are linked against the proper version of libclamav
DON'T PANIC! Read http://www.clamav.net/support/faq
daily.cvd version from DNS: 14710
Retrieving http://db.local.clamav.net/daily-14528.cdiff
Trying to download http://db.local.clamav.net/daily-14528.cdiff (IP: 81.91.100.173)
WARNING: getfile: daily-14528.cdiff not found on remote server (IP: 81.91.100.173)
WARNING: getpatch: Can't download daily-14528.cdiff from db.local.clamav.net
Retrieving http://db.local.clamav.net/daily-14528.cdiff
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
Trying to download http://db.local.clamav.net/daily-14528.cdiff (IP: 217.135.32.99)
WARNING: getfile: daily-14528.cdiff not found on remote server (IP: 217.135.32.99)
WARNING: getpatch: Can't download daily-14528.cdiff from db.local.clamav.net
Retrieving http://db.local.clamav.net/daily-14528.cdiff
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
Trying to download http://db.local.clamav.net/daily-14528.cdiff (IP: 193.1.193.64)
WARNING: getfile: daily-14528.cdiff not found on remote server (IP: 193.1.193.64)
WARNING: getpatch: Can't download daily-14528.cdiff from db.local.clamav.net
Retrieving http://db.local.clamav.net/daily-14528.cdiff
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
Ignoring mirror 193.1.193.64 (has connected too many times with an outdated version)
Trying to download http://db.local.clamav.net/daily-14528.cdiff (IP: 163.1.3.8)
WARNING: getfile: daily-14528.cdiff not found on remote server (IP: 163.1.3.8)
WARNING: getpatch: Can't download daily-14528.cdiff from db.local.clamav.net
Retrieving http://db.local.clamav.net/daily-14528.cdiff
Ignoring mirror 193.1.193.64 (has connected too many times with an outdated version)
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
Ignoring mirror 163.1.3.8 (has connected too many times with an outdated version)
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
Ignoring mirror 193.1.193.64 (has connected too many times with an outdated version)
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
Ignoring mirror 163.1.3.8 (has connected too many times with an outdated version)
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
WARNING: getpatch: Can't download daily-14528.cdiff from db.local.clamav.net
WARNING: Incremental update failed, trying to download daily.cvd
Whitelisting short-term blacklisted mirrors
Retrieving http://db.local.clamav.net/daily.cvd
Ignoring mirror 163.1.3.8 (has connected too many times with an outdated version)
Ignoring mirror 193.1.193.64 (has connected too many times with an outdated version)
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
Ignoring mirror 163.1.3.8 (has connected too many times with an outdated version)
Ignoring mirror 193.1.193.64 (has connected too many times with an outdated version)
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
WARNING: Can't download daily.cvd from db.local.clamav.net
Trying again in 5 secs...

```"sudo freshclam -v --no-dns" produced this:

```

roger@roger-desktop:~$ sudo freshclam -v --no-dns
Current working dir is /var/lib/clamav
Max retries == 5
ClamAV update process started at Tue Mar 27 21:05:05 2012
Using IPv6 aware code
If-Modified-Since: Tue, 11 Oct 2011 14:34:20 GMT
Reading CVD header (main.cvd): Connected to db.local.clamav.net (IP: 193.1.193.64).
Trying to retrieve CVD header of http://db.local.clamav.net/main.cvd
OK
main.cvd is up to date (version: 54, sigs: 1044387, f-level: 60, builder: sven)
WARNING: Current functionality level = 58, recommended = 60
Please check if ClamAV tools are linked against the proper version of libclamav
DON'T PANIC! Read http://www.clamav.net/support/faq
If-Modified-Since: Sat, 25 Feb 2012 20:44:32 GMT
Reading CVD header (daily.cvd): Connected to db.local.clamav.net (IP: 193.1.193.64).
Trying to retrieve CVD header of http://db.local.clamav.net/daily.cvd
OK
Retrieving http://db.local.clamav.net/daily-14528.cdiff
Trying to download http://db.local.clamav.net/daily-14528.cdiff (IP: 193.1.193.64)
WARNING: getfile: daily-14528.cdiff not found on remote server (IP: 193.1.193.64)
WARNING: getpatch: Can't download daily-14528.cdiff from db.local.clamav.net
Retrieving http://db.local.clamav.net/daily-14528.cdiff
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
Ignoring mirror 193.1.193.64 (has connected too many times with an outdated version)
Ignoring mirror 163.1.3.8 (has connected too many times with an outdated version)
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
Ignoring mirror 193.1.193.64 (has connected too many times with an outdated version)
Ignoring mirror 163.1.3.8 (has connected too many times with an outdated version)
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
WARNING: getpatch: Can't download daily-14528.cdiff from db.local.clamav.net
Retrieving http://db.local.clamav.net/daily-14528.cdiff
Ignoring mirror 193.1.193.64 (has connected too many times with an outdated version)
Ignoring mirror 163.1.3.8 (has connected too many times with an outdated version)
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
Ignoring mirror 193.1.193.64 (has connected too many times with an outdated version)
Ignoring mirror 163.1.3.8 (has connected too many times with an outdated version)
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
WARNING: getpatch: Can't download daily-14528.cdiff from db.local.clamav.net
Retrieving http://db.local.clamav.net/daily-14528.cdiff
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
Ignoring mirror 163.1.3.8 (has connected too many times with an outdated version)
Ignoring mirror 193.1.193.64 (has connected too many times with an outdated version)
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
Ignoring mirror 163.1.3.8 (has connected too many times with an outdated version)
Ignoring mirror 193.1.193.64 (has connected too many times with an outdated version)
WARNING: getpatch: Can't download daily-14528.cdiff from db.local.clamav.net
Retrieving http://db.local.clamav.net/daily-14528.cdiff
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
Ignoring mirror 163.1.3.8 (has connected too many times with an outdated version)
Ignoring mirror 193.1.193.64 (has connected too many times with an outdated version)
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
Ignoring mirror 163.1.3.8 (has connected too many times with an outdated version)
Ignoring mirror 193.1.193.64 (has connected too many times with an outdated version)
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
WARNING: getpatch: Can't download daily-14528.cdiff from db.local.clamav.net
WARNING: Incremental update failed, trying to download daily.cvd
Whitelisting short-term blacklisted mirrors
Retrieving http://db.local.clamav.net/daily.cvd
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
Ignoring mirror 163.1.3.8 (has connected too many times with an outdated version)
Ignoring mirror 193.1.193.64 (has connected too many times with an outdated version)
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
Ignoring mirror 163.1.3.8 (has connected too many times with an outdated version)
Ignoring mirror 193.1.193.64 (has connected too many times with an outdated version)
WARNING: Can't download daily.cvd from db.local.clamav.net
Trying again in 5 secs...
ClamAV update process started at Tue Mar 27 21:05:15 2012
Using IPv6 aware code
If-Modified-Since: Tue, 11 Oct 2011 14:34:20 GMT
Reading CVD header (main.cvd): ^CUpdate process interrupted

```Any suggestions?

Regards,
Roger.

---

### Post by NuahHuan on 2012-03-27
Roger - I seem to have a similar problem and I don't know how to update the clamav engine 

appreciate anyone having any suggestions how do this

---

### Post by EzioAuditore on 2012-03-27
> **Roger49 said:**
> Hi NikTh,
Sorry, I installed Clam via Synaptic.

"sudo freshclam -v" produced this:

```

roger@roger-desktop:~$ sudo freshclam -v
[sudo] password for roger: 
Current working dir is /var/lib/clamav
Max retries == 5
ClamAV update process started at Tue Mar 27 21:00:43 2012
Using IPv6 aware code
Querying current.cvd.clamav.net
TTL: 749
Software version from DNS: 0.97.4
main.cvd version from DNS: 54
main.cvd is up to date (version: 54, sigs: 1044387, f-level: 60, builder: sven)
WARNING: Current functionality level = 58, recommended = 60
Please check if ClamAV tools are linked against the proper version of libclamav
DON'T PANIC! Read http://www.clamav.net/support/faq
daily.cvd version from DNS: 14710
Retrieving http://db.local.clamav.net/daily-14528.cdiff
Trying to download http://db.local.clamav.net/daily-14528.cdiff (IP: 81.91.100.173)
WARNING: getfile: daily-14528.cdiff not found on remote server (IP: 81.91.100.173)
WARNING: getpatch: Can't download daily-14528.cdiff from db.local.clamav.net
Retrieving http://db.local.clamav.net/daily-14528.cdiff
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
Trying to download http://db.local.clamav.net/daily-14528.cdiff (IP: 217.135.32.99)
WARNING: getfile: daily-14528.cdiff not found on remote server (IP: 217.135.32.99)
WARNING: getpatch: Can't download daily-14528.cdiff from db.local.clamav.net
Retrieving http://db.local.clamav.net/daily-14528.cdiff
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
Trying to download http://db.local.clamav.net/daily-14528.cdiff (IP: 193.1.193.64)
WARNING: getfile: daily-14528.cdiff not found on remote server (IP: 193.1.193.64)
WARNING: getpatch: Can't download daily-14528.cdiff from db.local.clamav.net
Retrieving http://db.local.clamav.net/daily-14528.cdiff
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
Ignoring mirror 193.1.193.64 (has connected too many times with an outdated version)
Trying to download http://db.local.clamav.net/daily-14528.cdiff (IP: 163.1.3.8)
WARNING: getfile: daily-14528.cdiff not found on remote server (IP: 163.1.3.8)
WARNING: getpatch: Can't download daily-14528.cdiff from db.local.clamav.net
Retrieving http://db.local.clamav.net/daily-14528.cdiff
Ignoring mirror 193.1.193.64 (has connected too many times with an outdated version)
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
Ignoring mirror 163.1.3.8 (has connected too many times with an outdated version)
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
Ignoring mirror 193.1.193.64 (has connected too many times with an outdated version)
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
Ignoring mirror 163.1.3.8 (has connected too many times with an outdated version)
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
WARNING: getpatch: Can't download daily-14528.cdiff from db.local.clamav.net
WARNING: Incremental update failed, trying to download daily.cvd
Whitelisting short-term blacklisted mirrors
Retrieving http://db.local.clamav.net/daily.cvd
Ignoring mirror 163.1.3.8 (has connected too many times with an outdated version)
Ignoring mirror 193.1.193.64 (has connected too many times with an outdated version)
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
Ignoring mirror 163.1.3.8 (has connected too many times with an outdated version)
Ignoring mirror 193.1.193.64 (has connected too many times with an outdated version)
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
WARNING: Can't download daily.cvd from db.local.clamav.net
Trying again in 5 secs...

```"sudo freshclam -v --no-dns" produced this:

```

roger@roger-desktop:~$ sudo freshclam -v --no-dns
Current working dir is /var/lib/clamav
Max retries == 5
ClamAV update process started at Tue Mar 27 21:05:05 2012
Using IPv6 aware code
If-Modified-Since: Tue, 11 Oct 2011 14:34:20 GMT
Reading CVD header (main.cvd): Connected to db.local.clamav.net (IP: 193.1.193.64).
Trying to retrieve CVD header of http://db.local.clamav.net/main.cvd
OK
main.cvd is up to date (version: 54, sigs: 1044387, f-level: 60, builder: sven)
WARNING: Current functionality level = 58, recommended = 60
Please check if ClamAV tools are linked against the proper version of libclamav
DON'T PANIC! Read http://www.clamav.net/support/faq
If-Modified-Since: Sat, 25 Feb 2012 20:44:32 GMT
Reading CVD header (daily.cvd): Connected to db.local.clamav.net (IP: 193.1.193.64).
Trying to retrieve CVD header of http://db.local.clamav.net/daily.cvd
OK
Retrieving http://db.local.clamav.net/daily-14528.cdiff
Trying to download http://db.local.clamav.net/daily-14528.cdiff (IP: 193.1.193.64)
WARNING: getfile: daily-14528.cdiff not found on remote server (IP: 193.1.193.64)
WARNING: getpatch: Can't download daily-14528.cdiff from db.local.clamav.net
Retrieving http://db.local.clamav.net/daily-14528.cdiff
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
Ignoring mirror 193.1.193.64 (has connected too many times with an outdated version)
Ignoring mirror 163.1.3.8 (has connected too many times with an outdated version)
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
Ignoring mirror 193.1.193.64 (has connected too many times with an outdated version)
Ignoring mirror 163.1.3.8 (has connected too many times with an outdated version)
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
WARNING: getpatch: Can't download daily-14528.cdiff from db.local.clamav.net
Retrieving http://db.local.clamav.net/daily-14528.cdiff
Ignoring mirror 193.1.193.64 (has connected too many times with an outdated version)
Ignoring mirror 163.1.3.8 (has connected too many times with an outdated version)
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
Ignoring mirror 193.1.193.64 (has connected too many times with an outdated version)
Ignoring mirror 163.1.3.8 (has connected too many times with an outdated version)
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
WARNING: getpatch: Can't download daily-14528.cdiff from db.local.clamav.net
Retrieving http://db.local.clamav.net/daily-14528.cdiff
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
Ignoring mirror 163.1.3.8 (has connected too many times with an outdated version)
Ignoring mirror 193.1.193.64 (has connected too many times with an outdated version)
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
Ignoring mirror 163.1.3.8 (has connected too many times with an outdated version)
Ignoring mirror 193.1.193.64 (has connected too many times with an outdated version)
WARNING: getpatch: Can't download daily-14528.cdiff from db.local.clamav.net
Retrieving http://db.local.clamav.net/daily-14528.cdiff
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
Ignoring mirror 163.1.3.8 (has connected too many times with an outdated version)
Ignoring mirror 193.1.193.64 (has connected too many times with an outdated version)
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
Ignoring mirror 163.1.3.8 (has connected too many times with an outdated version)
Ignoring mirror 193.1.193.64 (has connected too many times with an outdated version)
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
WARNING: getpatch: Can't download daily-14528.cdiff from db.local.clamav.net
WARNING: Incremental update failed, trying to download daily.cvd
Whitelisting short-term blacklisted mirrors
Retrieving http://db.local.clamav.net/daily.cvd
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
Ignoring mirror 163.1.3.8 (has connected too many times with an outdated version)
Ignoring mirror 193.1.193.64 (has connected too many times with an outdated version)
Ignoring mirror 81.91.100.173 (has connected too many times with an outdated version)
Ignoring mirror 217.135.32.99 (has connected too many times with an outdated version)
Ignoring mirror 163.1.3.8 (has connected too many times with an outdated version)
Ignoring mirror 193.1.193.64 (has connected too many times with an outdated version)
WARNING: Can't download daily.cvd from db.local.clamav.net
Trying again in 5 secs...
ClamAV update process started at Tue Mar 27 21:05:15 2012
Using IPv6 aware code
If-Modified-Since: Tue, 11 Oct 2011 14:34:20 GMT
Reading CVD header (main.cvd): ^CUpdate process interrupted

```Any suggestions?

Regards,
Roger.

Have you tried replacing the files as I said earlier ?

---

### Post by Roger49 on 2012-03-31
[SIZE=3]Hi All,
I've downloaded the files which are newer than the ones which were installed. I think I've fixed it, but here is what I have done, for the record, and, of course, for any comments.

I found the location of the old files:

[/SIZE]```

[SIZE=3]/var/lib/clamav
[/SIZE]
```[SIZE=3]
I was unable to drag and drop the new files in Gnome, so 
(Gulp) RTFM and open a terminal.

[/SIZE]```
[SIZE=3]sudo cp -f filename /var/lib/clamav[/SIZE]

```[SIZE=3](I don't think it would work without the -f)[/SIZE]

[SIZE=3]Then, to check it had been changed from the destination folder,

[/SIZE]```
[SIZE=3]sudo ls -l[/SIZE] [SIZE=3]daily.cvd[/SIZE]

```[SIZE=3]This shows the date associated with the file in question.

Any comments?

Regards,
Roger.
[/SIZE]

---

### Post by EzioAuditore on 2012-04-01
> **Roger49 said:**
> [SIZE=3]Hi All,
I've downloaded the files which are newer than the ones which were installed. I think I've fixed it, but here is what I have done, for the record, and, of course, for any comments.

I found the location of the old files:

[/SIZE]```

[SIZE=3]/var/lib/clamav
[/SIZE]
```[SIZE=3]
I was unable to drag and drop the new files in Gnome, so 
(Gulp) RTFM and open a terminal.

[/SIZE]```
[SIZE=3]sudo cp -f filename /var/lib/clamav[/SIZE]

```[SIZE=3](I don't think it would work without the -f)[/SIZE]

[SIZE=3]Then, to check it had been changed from the destination folder,

[/SIZE]```
[SIZE=3]sudo ls -l[/SIZE] [SIZE=3]daily.cvd[/SIZE]

```[SIZE=3]This shows the date associated with the file in question.

Any comments?

Regards,
Roger.
[/SIZE]

That's fine. You weren't able to directly replace via gui (file manager) due to the permission thingy.
You can run 'gksudo nautilus' from the run box (alt+f2) to open a file manager window with root privileges to copy file outside home directory. Though command line is way efficient and faster. :p

---

### Post by Roger49 on 2012-04-01
[SIZE=3]Thanks Ezio,
Marking this as SOLVED now (if I can remember how to)
Regards,
Roger.
[/SIZE]

---

