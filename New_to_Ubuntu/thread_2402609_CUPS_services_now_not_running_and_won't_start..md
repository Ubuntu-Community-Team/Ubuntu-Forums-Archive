---
title: "CUPS services now not running and won't start."
date: 2018-10-02
forum: New to Ubuntu
---

### Post by rocketshiptech on 2018-10-02
Trying to install my 1st Linux printer:

I go to Settings, printers, install a new printer. It scans, and it wants to install a "CUPS printer". I don't know what CUPS is, and this is a Cannon. So I say No. (I'm expecting it to want to install a Cannon printer) I try again, It says CUPS again, I'm confused. We go around 3 or 4 times like this.

I go google CUPS (oh!) go back in but now I get "Sorry! The system printing service doesn't seem to be available."

Now that I know what CUPS is, I go look in Webmin, and all of my CUPS services are off. I tried restarting them, (fails) I tried reinstalling CUPS in Terminal (reinstalls, still won't start), I've rebooted several times. I have no printer services now.

What have I done?

---

### Post by ajgreeny on 2018-10-02
Let's see the output of command ```
dpkg -l *cups*
``` to show exactly which cups packages you already have installed and we can take it forward from there.

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by rocketshiptech on 2018-10-02
Sure here:

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                     Version           Architecture      Description
+++-========================-=================-=================-=====================================================
ii  bluez-cups               5.48-0ubuntu3.1   amd64             Bluetooth printer driver for CUPS
ii  cups                     2.2.7-1ubuntu2.1  amd64             Common UNIX Printing System(tm) - PPD/driver support,
ii  cups-browsed             1.20.2-0ubuntu3   amd64             OpenPrinting CUPS Filters - cups-browsed
ii  cups-bsd                 2.2.7-1ubuntu2.1  amd64             Common UNIX Printing System(tm) - BSD commands
ii  cups-client              2.2.7-1ubuntu2.1  amd64             Common UNIX Printing System(tm) - client programs (Sy
ii  cups-common              2.2.7-1ubuntu2.1  all               Common UNIX Printing System(tm) - common files
ii  cups-core-drivers        2.2.7-1ubuntu2.1  amd64             Common UNIX Printing System(tm) - driverless printing
ii  cups-daemon              2.2.7-1ubuntu2.1  amd64             Common UNIX Printing System(tm) - daemon
ii  cups-filters             1.20.2-0ubuntu3   amd64             OpenPrinting CUPS Filters - Main Package
ii  cups-filters-core-driver 1.20.2-0ubuntu3   amd64             OpenPrinting CUPS Filters - Driverless printing
un  cups-filters-ippusbxd    <none>            <none>            (no description available)
ii  cups-ipp-utils           2.2.7-1ubuntu2.1  amd64             Common UNIX Printing System(tm) - IPP developer/admin
un  cups-pdf                 <none>            <none>            (no description available)
ii  cups-pk-helper           0.2.6-1ubuntu1.2  amd64             PolicyKit helper to configure cups with fine-grained 
ii  cups-ppdc                2.2.7-1ubuntu2.1  amd64             Common UNIX Printing System(tm) - PPD manipulation ut
ii  cups-server-common       2.2.7-1ubuntu2.1  all               Common UNIX Printing System(tm) - server common files
un  ghostscript-cups         <none>            <none>            (no description available)
un  hplip-cups               <none>            <none>            (no description available)
ii  libcups2:amd64           2.2.7-1ubuntu2.1  amd64             Common UNIX Printing System(tm) - Core library
ii  libcupscgi1:amd64        2.2.7-1ubuntu2.1  amd64             Common UNIX Printing System(tm) - CGI library
ii  libcupsfilters1:amd64    1.20.2-0ubuntu3   amd64             OpenPrinting CUPS Filters - Shared library
ii  libcupsimage2:amd64      2.2.7-1ubuntu2.1  amd64             Common UNIX Printing System(tm) - Raster image librar
ii  libcupsmime1:amd64       2.2.7-1ubuntu2.1  amd64             Common UNIX Printing System(tm) - MIME library
ii  libcupsppdc1:amd64       2.2.7-1ubuntu2.1  amd64             Common UNIX Printing System(tm) - PPD manipulation li
ii  printer-driver-hpcups    3.17.10+repack0-5 amd64             HP Linux Printing and Imaging - CUPS Raster driver (h
un  python-cupshelpers       <none>            <none>            (no description available)
ii  python3-cups             1.9.73-2          amd64             Python3 bindings for CUPS
ii  python3-cupshelpers      1.5.11-1ubuntu2   all               Python utility modules around the CUPS printing syste
un  python3.6-cups      
```

---

### Post by deadflowr on 2018-10-02
What do:
```
sudo systemctl restart cups.service
and
systemctl status cups.service
```
show?

(You can also change restart to start and/or try it with enable to see if those do anything)

---

### Post by rocketshiptech on 2018-10-02
```
&#9679; cups.service - CUPS Scheduler
   Loaded: loaded (/lib/systemd/system/cups.service; enabled; vendor preset: enabled)
   Active: failed (Result: start-limit-hit) since Tue 2018-10-02 18:29:45 EDT; 11s ago
     Docs: man:cupsd(8)
  Process: 7628 ExecStart=/usr/sbin/cupsd -l (code=killed, signal=TERM)
 Main PID: 7628 (code=killed, signal=TERM)

Oct 02 18:29:45 SasdfxA systemd[1]: cups.service: Service hold-off time over, scheduling restart.
Oct 02 18:29:45 SasdfxA systemd[1]: cups.service: Scheduled restart job, restart counter is at 5.
Oct 02 18:29:45 SasdfxA systemd[1]: Stopped CUPS Scheduler.
Oct 02 18:29:45 SasdfxA systemd[1]: cups.service: Start request repeated too quickly.
Oct 02 18:29:45 SasdfxA systemd[1]: cups.service: Failed with result 'start-limit-hit'.
Oct 02 18:29:45 SasdfxA systemd[1]: Failed to start CUPS Scheduler.

```

I saw "start-limit-hit" this AM in Webmin, but couldn't find anything on google w/ that and CUPS

---

### Post by rocketshiptech on 2018-10-05
Hi guys,

Ok I'm not getting anywhere here.  And I need to print.

So now I'm thinking of nuking the site from orbit and starting over.  So I may start a new thread about that.

---

### Post by deadflowr on 2018-10-05
Don't start a new thread.

Digging I found this which is eerily similar:
[https://ubuntu-mate.community/t/cups-service-stopped-um-18-04/17381]("https://ubuntu-mate.community/t/cups-service-stopped-um-18-04/17381")
copy the cupsd.conf file
```
sudo cp /usr/share/cups/cupsd.conf.default /etc/cups/cupsd.conf
sudo systemctl restart cups
```
See if that does anything.

---

### Post by rocketshiptech on 2018-10-05
No,  Thanks dead.

That guy does have the same problem, but that didn't fix me. The correct thing to do to here is to start over. 
I wanted a nice clean install and this is already a mess. The questions I have about that involve moving RAID stacks and VMs. So that is a different topic. 

Thanks for trying.

---

