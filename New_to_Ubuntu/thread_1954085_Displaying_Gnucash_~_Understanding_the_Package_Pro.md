---
title: "Displaying Gnucash ~ Understanding the Package Process"
date: 2012-04-07
forum: New to Ubuntu
---

### Post by Andavane on 2012-04-07
Whilst the current known bug with Unity and java is sorted (hopefully fixed by 12.04) I decided to use Gnucash as Moneydance had unstable issues with Ubuntu after the introduction of Unity. I wanted Gnucash in earlier years but at the time there was no Gnucash for Windows. Now it's there for Windows I thought things were sorted and I could share account data with friends, irrespective of which Operating System is used.

Everything loaded fine, and the behaviour was perfect. However when I drop into Ubuntu 11.10 Oneiric, the grip bars will not adjust the panels so I can't see the info I want. The handles appear, I drag them over then WHOOSH as soon as I let go they jump back.

Now I understand that Gnucash likes to be updated, and that it should be updated. I even have the latest  file called: gnucash_2.4.10-1_amd64.deb.
But how to proceed, and what it might do to the existing Gnucash files in /etc I am very unsure about going ahead.

Any advice much appreciated.

One way or another, some annoying thing keeps taking me back to Windows :-( and I love Ubuntu.

Regards, John

PS: The ridiculously wide screenshot of what I currently see in ubuntu is attached.

---

### Post by Andavane on 2012-04-15
Oh dear, one week after posting this, and no suggestion or pointer.
My own searches suggest to me that an issue may be the databases each version (linux and windows) uses, although I can't see how this affects display.

Interestingly, I installed a more recent version of Gnucash in Ubuntu on another, much older machine and that has displayed fine. It's this dual-boot machine, the Lenovo Thinkpad, which is having the display/re-sizing problem, in Ubuntu only.

This Absolute Beginner forum is surely not the best platform for this type of issue.

If anyone knows a mor suitable place to air it, I'd be very grateful! :)

Regards,


John

---

### Post by r-senior on 2012-04-15
If you run this command on your .deb file, it will show you what files it installs:

```
dpkg -c <deb-name>
```

That might give you some clues about whether it overwrites anything in /etc/ I'd be surprised if it did. I think it stores all your local configuration in ~/.gnucash.

---

### Post by Jose Catre-Vandis on 2012-04-15
Might be 64 bit issues, works fine on 32 bit install of 11.10 here (with W7 also 32 bit, dualboot). This on 64 bit capable machine.

---

### Post by Andavane on 2012-04-15
> **Jose Catre-Vandis said:**
> Might be 64 bit issues, works fine on 32 bit install of 11.10 here (with W7 also 32 bit, dualboot). This on 64 bit capable machine.

> **r-senior said:**
> If you run this command on your .deb file, it will show you what files it installs:

```
dpkg -c <deb-name>
```

That might give you some clues about whether it overwrites anything in /etc/ I'd be surprised if it did. I think it stores all your local configuration in ~/.gnucash.

This is returned: > andavane@andavane-think:~$ dpkg -c <gnucash>
bash: syntax error near unexpected token `newline'
andavane@andavane-think:~$ dpkg -c gnucash
dpkg-deb: error: failed to read archive `gnucash': No such file or directory
andavane@andavane-think:~$ 

I instaled it from synaptic, so not saure how to 'run the command on the command on deb file' when it's in synaptic.

> **r-senior said:**
> If you run this command on your .deb file, it will show you what files it installs:

```
dpkg -c <deb-name>
```

That might give you some clues about whether it overwrites anything in /etc/ I'd be surprised if it did. I think it stores all your local configuration in ~/.gnucash.

> **Jose Catre-Vandis said:**
> Might be 64 bit issues, works fine on 32 bit install of 11.10 here (with W7 also 32 bit, dualboot). This on 64 bit capable machine.

Indeed. the old laptop which displayed fine was 32-bit. This Thinkpad is 64-bit.

regards

john

---

### Post by r-senior on 2012-04-15
Don't you have a .deb file that you downloaded from somewhere? This is what I was thinking:

```
dpkg -c gnucash_2.4.10-1_amd64.deb
```

It will show you the files that would be overwritten if you were to install it from the .deb file.

It would be an odd design if it overwrote any of your data on upgrade. Do you have specific reasons for believing it will?

---

### Post by Andavane on 2012-04-17
> **r-senior said:**
> Don't you have a .deb file that you downloaded from somewhere? This is what I was thinking:

```
dpkg -c gnucash_2.4.10-1_amd64.deb
```

It will show you the files that would be overwritten if you were to install it from the .deb file.

It would be an odd design if it overwrote any of your data on upgrade. Do you have specific reasons for believing it will?

Doh! Silly me what was I thinking.
Yes that's it indeed, in downloads, and it returns this:

> andavane@andavane-think:~$ cd Downloads
andavane@andavane-think:~/Downloads$ dpkg -c gnucash_2.4.10-1_amd64.deb
drwxr-xr-x root/root         0 2012-02-12 11:54 ./
drwxr-xr-x root/root         0 2012-02-12 11:54 ./usr/
drwxr-xr-x root/root         0 2012-02-12 11:54 ./usr/lib/
drwxr-xr-x root/root         0 2012-02-12 11:54 ./usr/lib/gnucash/
-rw-r--r-- root/root    279344 2012-02-12 11:54 ./usr/lib/gnucash/libgnc-qof.so.1.0.4
-rw-r--r-- root/root     78256 2012-02-12 11:54 ./usr/lib/gnucash/libgnc-core-utils.so.0.0.0
-rw-r--r-- root/root     32408 2012-02-12 11:54 ./usr/lib/gnucash/libgnc-module.so.0.0.0
drwxr-xr-x root/root         0 2012-02-12 11:55 ./usr/lib/gnucash/gnucash/
-rw-r--r-- root/root   1245224 2012-02-12 11:55 ./usr/lib/gnucash/gnucash/libgncmod-engine.so
-rw-r--r-- root/root     31368 2012-02-12 11:55 ./usr/lib/gnucash/gnucash/libgncmod-backend-xml.so
-rw-r--r-- root/root     60288 2012-02-12 11:55 ./usr/lib/gnucash/gnucash/libgncmod-backend-dbi.so
-rw-r--r-- root/root     34864 2012-02-12 11:55 ./usr/lib/gnucash/gnucash/libgncmod-calculation.so
-rw-r--r-- root/root      6064 2012-02-12 11:55 ./usr/lib/gnucash/gnucash/libgncmod-tax-us.so
-rw-r--r-- root/root    259456 2012-02-12 11:55 ./usr/lib/gnucash/gnucash/libgncmod-app-utils.so
-rw-r--r-- root/root    983616 2012-02-12 11:55 ./usr/lib/gnucash/gnucash/libgncmod-gnome-utils.so
-rw-r--r-- root/root     87056 2012-02-12 11:55 ./usr/lib/gnucash/gnucash/libgncmod-html.so
-rw-r--r-- root/root     93968 2012-02-12 11:55 ./usr/lib/gnucash/gnucash/libgncmod-gnome-search.so
-rw-r--r-- root/root     32144 2012-02-12 11:55 ./usr/lib/gnucash/gnucash/libgncmod-report-system.so
-rw-r--r-- root/root      6064 2012-02-12 11:55 ./usr/lib/gnucash/gnucash/libgncmod-standard-reports.so
-rw-r--r-- root/root      6064 2012-02-12 11:55 ./usr/lib/gnucash/gnucash/libgncmod-utility-reports.so
-rw-r--r-- root/root     10176 2012-02-12 11:55 ./usr/lib/gnucash/gnucash/libgncmod-locale-reports-us.so
-rw-r--r-- root/root    133272 2012-02-12 11:55 ./usr/lib/gnucash/gnucash/libgncmod-report-gnome.so
-rw-r--r-- root/root     10432 2012-02-12 11:55 ./usr/lib/gnucash/gnucash/libgncmod-stylesheets.so
-rw-r--r-- root/root     76224 2012-02-12 11:55 ./usr/lib/gnucash/gnucash/libgncmod-register-core.so
-rw-r--r-- root/root    176680 2012-02-12 11:55 ./usr/lib/gnucash/gnucash/libgncmod-register-gnome.so
-rw-r--r-- root/root    181192 2012-02-12 11:55 ./usr/lib/gnucash/gnucash/libgncmod-ledger-core.so
-rw-r--r-- root/root     89808 2012-02-12 11:55 ./usr/lib/gnucash/gnucash/libgncmod-generic-import.so
-rw-r--r-- root/root     60168 2012-02-12 11:55 ./usr/lib/gnucash/gnucash/libgncmod-qif.so.0.0.0
-rw-r--r-- root/root     94584 2012-02-12 11:55 ./usr/lib/gnucash/gnucash/libgncmod-qif-import.so
-rw-r--r-- root/root     35640 2012-02-12 11:55 ./usr/lib/gnucash/gnucash/libgncmod-ofx.so
-rw-r--r-- root/root    145552 2012-02-12 11:55 ./usr/lib/gnucash/gnucash/libgncmod-aqbanking.so
-rw-r--r-- root/root     27352 2012-02-12 11:55 ./usr/lib/gnucash/gnucash/libgncmod-log-replay.so
-rw-r--r-- root/root     69408 2012-02-12 11:55 ./usr/lib/gnucash/gnucash/libgncmod-csv.so
-rw-r--r-- root/root      6064 2012-02-12 11:55 ./usr/lib/gnucash/gnucash/libgncmod-business-core.so
-rw-r--r-- root/root      6056 2012-02-12 11:55 ./usr/lib/gnucash/gnucash/libgncmod-business-utils.so
-rw-r--r-- root/root     45448 2012-02-12 11:55 ./usr/lib/gnucash/gnucash/libgncmod-dialog-tax-table.so
-rw-r--r-- root/root    282160 2012-02-12 11:55 ./usr/lib/gnucash/gnucash/libgncmod-business-gnome.so
-rw-r--r-- root/root     48480 2012-02-12 11:55 ./usr/lib/gnucash/gnucash/libgncmod-bi_import.so
-rw-r--r-- root/root    302560 2012-02-12 11:54 ./usr/lib/gnucash/libgnc-backend-xml-utils.so.0.0.0
-rw-r--r-- root/root    233304 2012-02-12 11:54 ./usr/lib/gnucash/libgnc-backend-sql.so.0.0.0
-rw-r--r-- root/root    603992 2012-02-12 11:54 ./usr/lib/gnucash/libgnc-gnome.so.0.0.0
-rw-r--r-- root/root     79128 2012-02-12 11:54 ./usr/lib/gnucash/libgnc-business-ledger.so.0.0.0
drwxr-xr-x root/root         0 2012-02-12 11:54 ./usr/lib/gnucash/overrides/
-rwxr-xr-x root/root       757 2012-02-12 11:54 ./usr/lib/gnucash/overrides/gnucash-env
-rwxr-xr-x root/root       781 2012-02-12 11:54 ./usr/lib/gnucash/overrides/gnucash-make-guids
-rwxr-xr-x root/root       100 2012-02-12 11:54 ./usr/lib/gnucash/overrides/guile
drwxr-xr-x root/root         0 2012-02-12 11:55 ./usr/bin/
-rwxr-xr-x root/root     40224 2012-02-12 11:55 ./usr/bin/gnucash
-rwxr-xr-x root/root      2733 2012-02-12 11:54 ./usr/bin/gnc-fq-check
-rwxr-xr-x root/root     12616 2012-02-12 11:54 ./usr/bin/gnc-fq-helper
-rwxr-xr-x root/root      5964 2012-02-12 11:54 ./usr/bin/gnc-fq-dump
drwxr-xr-x root/root         0 2012-02-12 11:54 ./usr/share/
drwxr-xr-x root/root         0 2012-02-12 11:54 ./usr/share/applications/
-rw-r--r-- root/root      2452 2012-02-12 11:54 ./usr/share/applications/gnucash.desktop
drwxr-xr-x root/root         0 2012-02-12 11:54 ./usr/share/pixmaps/
-rw-r--r-- root/root      4534 2012-02-12 11:54 ./usr/share/pixmaps/gnucash-icon-32x32.xpm
drwxr-xr-x root/root         0 2012-02-12 11:54 ./usr/share/doc/
drwxr-xr-x root/root         0 2012-02-12 11:55 ./usr/share/doc/gnucash/
-rw-r--r-- root/root     34474 2012-02-06 00:24 ./usr/share/doc/gnucash/NEWS.gz
-rw-r--r-- root/root      1713 2012-02-06 00:24 ./usr/share/doc/gnucash/TODO
-rw-r--r-- root/root      2669 2012-02-06 00:24 ./usr/share/doc/gnucash/README.german.gz
-rw-r--r-- root/root      3804 2012-02-06 00:24 ./usr/share/doc/gnucash/README.HBCI.gz
-rw-r--r-- root/root      4890 2012-02-06 00:24 ./usr/share/doc/gnucash/README.OFX.gz
-rw-r--r-- root/root      2464 2012-02-12 11:55 ./usr/share/doc/gnucash/changelog.Debian.gz
-rw-r--r-- root/root       635 2011-09-23 19:35 ./usr/share/doc/gnucash/README.Debian
-rw-r--r-- root/root      2421 2012-01-24 16:30 ./usr/share/doc/gnucash/copyright
-rw-r--r-- root/root       385 2012-01-24 16:30 ./usr/share/doc/gnucash/NEWS.Debian.gz
-rw-r--r-- root/root      8313 2012-02-06 00:24 ./usr/share/doc/gnucash/AUTHORS.gz
-rw-r--r-- root/root      6249 2012-02-06 00:24 ./usr/share/doc/gnucash/README.gz
-rw-r--r-- root/root      5665 2012-02-06 00:24 ./usr/share/doc/gnucash/README.francais.gz
drwxr-xr-x root/root         0 2012-02-12 11:54 ./usr/share/man/
drwxr-xr-x root/root         0 2012-02-12 11:54 ./usr/share/man/man1/
-rw-r--r-- root/root      1233 2012-02-12 11:54 ./usr/share/man/man1/gnucash.1.gz
drwxr-xr-x root/root         0 2012-02-12 11:54 ./usr/share/menu/
-rw-r--r-- root/root       325 2012-01-24 16:30 ./usr/share/menu/gnucash
drwxr-xr-x root/root         0 2012-02-12 11:54 ./etc/
drwxr-xr-x root/root         0 2012-02-12 11:54 ./etc/gnucash/
-rw-r--r-- root/root        82 2012-02-12 11:54 ./etc/gnucash/config
-rw-r--r-- root/root      2431 2012-02-12 11:54 ./etc/gnucash/environment
drwxr-xr-x root/root         0 2012-02-12 11:54 ./etc/gconf/
drwxr-xr-x root/root         0 2012-02-12 11:54 ./etc/gconf/gconf.xml.defaults/
lrwxrwxrwx root/root         0 2012-02-12 11:54 ./usr/lib/gnucash/libgnc-qof.so.1 -> libgnc-qof.so.1.0.4
lrwxrwxrwx root/root         0 2012-02-12 11:54 ./usr/lib/gnucash/libgnc-qof.so -> libgnc-qof.so.1.0.4
lrwxrwxrwx root/root         0 2012-02-12 11:54 ./usr/lib/gnucash/libgnc-core-utils.so.0 -> libgnc-core-utils.so.0.0.0
lrwxrwxrwx root/root         0 2012-02-12 11:54 ./usr/lib/gnucash/libgnc-core-utils.so -> libgnc-core-utils.so.0.0.0
lrwxrwxrwx root/root         0 2012-02-12 11:54 ./usr/lib/gnucash/libgnc-module.so.0 -> libgnc-module.so.0.0.0
lrwxrwxrwx root/root         0 2012-02-12 11:54 ./usr/lib/gnucash/libgnc-module.so -> libgnc-module.so.0.0.0
lrwxrwxrwx root/root         0 2012-02-12 11:54 ./usr/lib/gnucash/gnucash/libgncmod-qif.so.0 -> libgncmod-qif.so.0.0.0
lrwxrwxrwx root/root         0 2012-02-12 11:54 ./usr/lib/gnucash/gnucash/libgncmod-qif.so -> libgncmod-qif.so.0.0.0
lrwxrwxrwx root/root         0 2012-02-12 11:54 ./usr/lib/gnucash/libgnc-backend-xml-utils.so.0 -> libgnc-backend-xml-utils.so.0.0.0
lrwxrwxrwx root/root         0 2012-02-12 11:54 ./usr/lib/gnucash/libgnc-backend-xml-utils.so -> libgnc-backend-xml-utils.so.0.0.0
lrwxrwxrwx root/root         0 2012-02-12 11:54 ./usr/lib/gnucash/libgnc-backend-sql.so.0 -> libgnc-backend-sql.so.0.0.0
lrwxrwxrwx root/root         0 2012-02-12 11:54 ./usr/lib/gnucash/libgnc-backend-sql.so -> libgnc-backend-sql.so.0.0.0
lrwxrwxrwx root/root         0 2012-02-12 11:54 ./usr/lib/gnucash/libgnc-gnome.so.0 -> libgnc-gnome.so.0.0.0
lrwxrwxrwx root/root         0 2012-02-12 11:54 ./usr/lib/gnucash/libgnc-gnome.so -> libgnc-gnome.so.0.0.0
lrwxrwxrwx root/root         0 2012-02-12 11:54 ./usr/lib/gnucash/libgnc-business-ledger.so.0 -> libgnc-business-ledger.so.0.0.0
lrwxrwxrwx root/root         0 2012-02-12 11:54 ./usr/lib/gnucash/libgnc-business-ledger.so -> libgnc-business-ledger.so.0.0.0
andavane@andavane-think:~/Downloads$ 


As a matter of interest I went to that older 32-bit machine, and used their gnucash program and it all worked and resized properly.

Looking forward to your diagnosis.

Regards

John

---

