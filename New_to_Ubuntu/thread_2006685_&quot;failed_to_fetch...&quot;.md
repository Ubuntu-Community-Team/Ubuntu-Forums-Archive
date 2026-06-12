---
title: "&quot;failed to fetch...&quot;"
date: 2012-06-19
forum: New to Ubuntu
---

### Post by dougcumiskey123 on 2012-06-19
My machine was downloading updates and I seen theis report. will it sort itself out or do I have to do something about it?


"Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.6.3-2ubuntu2.3_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.6.3-2ubuntu2.3_all.deb) Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10). - connect (110: Connection timed out)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common-bin_3.6.3-2ubuntu2.3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common-bin_3.6.3-2ubuntu2.3_i386.deb) Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-settings-daemon/gnome-settings-daemon_3.4.2-0ubuntu0.1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-settings-daemon/gnome-settings-daemon_3.4.2-0ubuntu0.1_i386.deb) Unable to connect to gb.archive.ubuntu.com:http:"

---

### Post by rukiaEnix on 2012-06-19
First, make sure you are connected to Internet. 
And second try pinging those repos, maybe they're down, and if they're down try looking for other source where to download those packages.

---

### Post by dougcumiskey123 on 2012-06-19
> **rukiaEnix said:**
> First, make sure you are connected to Internet. 
And second try pinging those repos, maybe they're down, and if they're down try looking for other source where to download those packages.

Yes I am connected.

and this is what I got back of the ping

doug@doug-ThinkPad-T400:~$ ping [http://gb.archive.ubuntu.com/ubuntu/...ntu2.3_all.deb](http://gb.archive.ubuntu.com/ubuntu/...ntu2.3_all.deb)

ping: unknown host [http://gb.archive.ubuntu.com/ubuntu/...ntu2.3_all.deb](http://gb.archive.ubuntu.com/ubuntu/...ntu2.3_all.deb)
doug@doug-ThinkPad-T400:~$ ping [http://gb.archive.ubuntu.com/ubuntu/...tu2.3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/...tu2.3_i386.deb)

ping: unknown host [http://gb.archive.ubuntu.com/ubuntu/...tu2.3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/...tu2.3_i386.deb)
doug@doug-ThinkPad-T400:~$ ping [http://gb.archive.ubuntu.com/ubuntu/...tu0.1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/...tu0.1_i386.deb) 

ping: unknown host [http://gb.archive.ubuntu.com/ubuntu/...tu0.1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/...tu0.1_i386.deb)
doug@doug-ThinkPad-T400:~$

---

### Post by wilee-nilee on 2012-06-19
> **dougcumiskey123 said:**
> My machine was downloading updates and I seen theis report. will it sort itself out or do I have to do something about it?


"Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.6.3-2ubuntu2.3_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.6.3-2ubuntu2.3_all.deb) Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10). - connect (110: Connection timed out)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common-bin_3.6.3-2ubuntu2.3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common-bin_3.6.3-2ubuntu2.3_i386.deb) Unable to connect to gb.archive.ubuntu.com:http:
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-settings-daemon/gnome-settings-daemon_3.4.2-0ubuntu0.1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-settings-daemon/gnome-settings-daemon_3.4.2-0ubuntu0.1_i386.deb) Unable to connect to gb.archive.ubuntu.com:http:"

You have 10.10 in your information is this what you are running, it is end of life.

Those 3 run links run here.
[http://fridge.ubuntu.com/2012/04/10/ubuntu-10-10-maverick-meerkat-end-of-life-reached-on-april-10-2012/](http://fridge.ubuntu.com/2012/04/10/ubuntu-10-10-maverick-meerkat-end-of-life-reached-on-april-10-2012/)
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by dougcumiskey123 on 2012-06-19
> **wilee-nilee said:**
> You have 10.10 in your information is this what you are running, it is end of life.

Those 3 run links run here.
[http://fridge.ubuntu.com/2012/04/10/ubuntu-10-10-maverick-meerkat-end-of-life-reached-on-april-10-2012/](http://fridge.ubuntu.com/2012/04/10/ubuntu-10-10-maverick-meerkat-end-of-life-reached-on-april-10-2012/)
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Yes I have not found a way of updateing my details! I am running 12.04, and thanks for the response.

---

### Post by dougcumiskey123 on 2012-06-19
I have just run update manager again, thinking it would try again but update manager reports that there are no updated to download, does that mean the I now have them?

Also I have opened all three of the ULR's and they where available for down loading, Confused!

---

### Post by jmfal on 2012-06-19
You can run 
```
 sudo apt-get update   
```

anytime.  The servers may be busy.

OR, you can go to Update Manager and selsct another server

To  edit you user info click "User CP" .

---

### Post by dougcumiskey123 on 2012-06-19
> **jmfal said:**
> You can run 
```
 sudo apt-get update   
```

anytime.  The servers may be busy.

OR, you can go to Update Manager and selsct another server

To  edit you user info click "User CP" .

I did as you sugested and its getting more complicated, below is the error reports.

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_GB](http://gb.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_GB)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en](http://gb.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en_GB](http://gb.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en_GB)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en](http://gb.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en_GB](http://gb.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en_GB)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en](http://gb.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en_GB](http://gb.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en_GB)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en](http://gb.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en_GB](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en_GB)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en_GB](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en_GB)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en_GB](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en_GB)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en_GB](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en_GB)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en_GB](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en_GB)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Translation-en)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en_GB](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en_GB)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Translation-en)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en_GB](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en_GB)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Translation-en)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en_GB](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en_GB)  Unable to connect to gb.archive.ubuntu.com:http:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Translation-en)  Unable to connect to gb.archive.ubuntu.com:http:

E: Some index files failed to download. They have been ignored, or old ones used instead.
doug@doug-ThinkPad-T400:~$

---

