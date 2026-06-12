---
title: "openvassd: /usr/local/lib/libldap_r-2.4.so.2: no version information available (requi"
date: 2013-04-30
forum: Programming Talk
---

### Post by shayno90 on 2013-04-30
Ok, my openvas4 has failed to rebuild the database for a few months now and troubleshooting it has failed to, have tried a few hacks but
no luck.

openvassd: /usr/local/lib/libldap_r-2.4.so.2: no version information available (required by /usr/lib/libopenvas_misc.so.4)

I have symlinked it:
```
ldconfig -p | grep libldap_r-2.4.so.2
    libldap_r-2.4.so.2 (libc6) => /usr/lib/libldap_r-2.4.so.2
    libldap_r-2.4.so.2 (libc6) => /usr/local/lib/libldap_r-2.4.so.2

```
and also:
```
ldconfig -p | grep liblber-2.4.so.2
    liblber-2.4.so.2 (libc6) => /usr/lib/liblber-2.4.so.2
    liblber-2.4.so.2 (libc6) => /usr/local/lib/liblber-2.4.so.2

```
Edited the location directories are pointed too:
```
nano /etc/ld.so.conf.d/libc.conf
# libc default configuration
#/usr/local/lib
/usr/lib
&&
/sbin/ldconfig -v

```
Deleted and rebuilt the openvas4 database:
```
openvasmd --rebuild -v




```

The openvas scanner cannot launch as a result of openvas database to rebuild itself:

read_from_server: failed to read from server: A TLS packet with unexpected length was received.

Any ideas to fix this?

---

### Post by shayno90 on 2013-05-17
I ended up fixing it.


The ld library path can only be defined in ~/.bashrc
and set to:
export LD_LIBRARY_PATH=/usr/lib (instead of /usr/local/lib)
ldconfig -v
echo $LD_LIBRARY_PATH
/usr/lib


Adding this elsewhere like /etc/environment, /etc/ld.so.conf.d/libc.conf or /etc/ld.so.conf fails.


Tried rebuilding the database from scratch but this fails.


Luckily I kept the previous database, moved it from a usb to /var/lib/openvas/mgr
rm -r /var/lib/openvas/mgr/tasks.db
cp -r /media/USB/tasks.db /var/lib/openvas/mgr/
ls -l /var/lib/openvas/mgr/
chmod 600 /var/lib/openvas/mgr/tasks.db
chown -r user:user /var/lib/openvas/mgr/tasks.db
ls -l /var/lib/openvas/mgr/


This time I ran all the openvas services again and it halted on openvasmd --update but it seemed to work according to the check script:
/etc/openvas/openvas-check-setup 
openvas-check-setup 2.1.5
  Test completeness and readiness of OpenVAS-4
  (add '--v5' if you want to check for OpenVAS-5)


  Please report us any non-detected problems and
  help us to improve this check routine:
  [http://lists.wald.intevation.org/mailman/listinfo/openvas-discuss](http://lists.wald.intevation.org/mailman/listinfo/openvas-discuss)


  Send us the log-file (/tmp/openvas-check-setup.log) to help analyze the problem.


  Use the parameter --server to skip checks for client tools
  like GSD and OpenVAS-CLI.


Step 1: Checking OpenVAS Scanner ... 
        OK: OpenVAS Scanner is present in version 3.2.5.
        OK: OpenVAS Scanner CA Certificate is present as /var/lib/openvas/CA/cacert.pem.
        OK: NVT collection in /var/lib/openvas/plugins contains 30607 NVTs.
        WARNING: Signature checking of NVTs is not enabled in OpenVAS Scanner.
        SUGGEST: Enable signature checking (see [http://www.openvas.org/trusted-nvts.html](http://www.openvas.org/trusted-nvts.html)).
Step 2: Checking OpenVAS Manager ... 
        OK: OpenVAS Manager is present in version 2.0.4.
        OK: OpenVAS Manager client certificate is present as /var/lib/openvas/CA/clientcert.pem.
        OK: OpenVAS Manager database found in /var/lib/openvas/mgr/tasks.db.
        OK: Access rights for the OpenVAS Manager database are correct.
        OK: sqlite3 found, extended checks of the OpenVAS Manager installation enabled.
        OK: OpenVAS Manager database is at revision 41.
        OK: OpenVAS Manager expects database at revision 41.
        OK: Database schema is up to date.
        OK: OpenVAS Manager database contains information about 28410 NVTs.
        OK: xsltproc found.
Step 3: Checking OpenVAS Administrator ... 
        OK: OpenVAS Administrator is present in version 1.1.2.
        OK: At least one user exists.
        OK: At least one admin user exists.
Step 4: Checking Greenbone Security Assistant (GSA) ... 
        OK: Greenbone Security Assistant is present in version 2.0.1.
Step 5: Checking OpenVAS CLI ... 
        OK: OpenVAS CLI version 1.1.4.SVN.
Step 6: Checking Greenbone Security Desktop (GSD) ... 
        OK: Greenbone Security Desktop is present in Version 1.2.2.
Step 7: Checking if OpenVAS services are up and running ... 
        OK: netstat found, extended checks of the OpenVAS services enabled.
        OK: OpenVAS Scanner is running and listening on all interfaces.
        OK: OpenVAS Scanner is listening on port 9391, which is the default port.
        ERROR: OpenVAS Manager is NOT running!
        FIX: Start OpenVAS Manager (openvasmd).
        ERROR: OpenVAS Administrator is NOT running!
        FIX: Start OpenVAS Administrator (openvasad).
        ERROR: Greenbone Security Assistant is NOT running!
        FIX: Start Greenbone Security Assistant (gsad).


 ERROR: Your OpenVAS-4 installation is not yet complete!


I assumed the database needed time to rebuild, after waiting a number of hours I killed the openvasmd --update and proceeded with the rest of the commands for starting openvas:
sudo killall openvassd
sleep 15
sudo /etc/init.d/openvas-scanner start
sudo /etc/init.d/openvas-manager start
sudo /etc/init.d/openvas-administrator restart
sudo /usr/sbin/gsad --listen=127.0.0.1 --port=9392 --alisten=127.0.0.1 --aport=9393 --mlisten=127.0.0.1 --mport=9390


Success, I checked the openvas check setup script:
Step 1: Checking OpenVAS Scanner ... 
        OK: OpenVAS Scanner is present in version 3.2.5.
        OK: OpenVAS Scanner CA Certificate is present as /var/lib/openvas/CA/cacert.pem.
        OK: NVT collection in /var/lib/openvas/plugins contains 30607 NVTs.
        WARNING: Signature checking of NVTs is not enabled in OpenVAS Scanner.
        SUGGEST: Enable signature checking (see [http://www.openvas.org/trusted-nvts.html](http://www.openvas.org/trusted-nvts.html)).
Step 2: Checking OpenVAS Manager ... 
        OK: OpenVAS Manager is present in version 2.0.4.
        OK: OpenVAS Manager client certificate is present as /var/lib/openvas/CA/clientcert.pem.
        OK: OpenVAS Manager database found in /var/lib/openvas/mgr/tasks.db.
        OK: Access rights for the OpenVAS Manager database are correct.
        OK: sqlite3 found, extended checks of the OpenVAS Manager installation enabled.
        OK: OpenVAS Manager database is at revision 41.
        OK: OpenVAS Manager expects database at revision 41.
        OK: Database schema is up to date.
        OK: OpenVAS Manager database contains information about 28410 NVTs.
        OK: xsltproc found.
Step 3: Checking OpenVAS Administrator ... 
        OK: OpenVAS Administrator is present in version 1.1.2.
        OK: At least one user exists.
        OK: At least one admin user exists.
Step 4: Checking Greenbone Security Assistant (GSA) ... 
        OK: Greenbone Security Assistant is present in version 2.0.1.
Step 5: Checking OpenVAS CLI ... 
        OK: OpenVAS CLI version 1.1.4.SVN.
Step 6: Checking Greenbone Security Desktop (GSD) ... 
        OK: Greenbone Security Desktop is present in Version 1.2.2.
Step 7: Checking if OpenVAS services are up and running ... 
        OK: netstat found, extended checks of the OpenVAS services enabled.
        OK: OpenVAS Scanner is running and listening only on the local interface.
        OK: OpenVAS Scanner is listening on port 9391, which is the default port.
        WARNING: OpenVAS Manager is running and listening only on the local interface. This means that you will not be able to access the OpenVAS Manager from the outside using GSD or OpenVAS CLI.
        SUGGEST: Ensure that OpenVAS Manager listens on all interfaces.
        OK: OpenVAS Manager is listening on port 9390, which is the default port.
        OK: OpenVAS Administrator is running and listening only on the local interface.
        OK: OpenVAS Administrator is listening on port 9393, which is the default port.
        WARNING: Greenbone Security Assistant is running and listening only on the local interface. This means that you will not be able to access the Greenbone Security Assistant from the outside using a web browser.
        SUGGEST: Ensure that Greenbone Security Assistant listens on all interfaces.
        OK: Greenbone Security Assistant is listening on port 9392, which is the default port.
Step 8: Checking nmap installation ...
        OK: nmap is present in version 5.51.
Step 9: Checking presence of optional tools ...
        OK: pdflatex found.
        OK: PDF generation successful. The PDF report format is likely to work.
        OK: ssh-keygen found, LSC credential generation for GNU/Linux targets is likely to work.
        OK: rpm found, LSC credential package generation for RPM based targets is likely to work.
        OK: alien found, LSC credential package generation for DEB based targets is likely to work.
        OK: nsis found, LSC credential package generation for Microsoft Windows targets is likely to work.


It seems like your OpenVAS-4 installation is OK.


Although I found this error with openvasmd:
Authentication configuration could not be loaded.
read_from_server: failed to read from server: A TLS packet with unexpected length was received.
Failed to gnutls_bye: Error in the push function.


I continued logging into gsad and it worked at last!! (I am not scanning from an external network so services are set to run on a 
localhost)


tcp        0      0 127.0.0.1:9390          0.0.0.0:*               LISTEN      13152/openvasmd 
tcp        0      0 127.0.0.1:9391          0.0.0.0:*               LISTEN      13141/openvassd: wa
tcp        0      0 127.0.0.1:9392          0.0.0.0:*               LISTEN      13222/gsad          
tcp        0      0 127.0.0.1:9393          0.0.0.0:*               LISTEN      13157/openvasad


However some things to investigate are the differences in the number of NVTs in database versus in the plugins folder, 28k~ v 30k~
Enable signature checking and change interface services are listening depending on nature of scan.

---

