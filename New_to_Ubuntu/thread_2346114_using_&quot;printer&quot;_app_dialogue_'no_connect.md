---
title: "using &quot;printer&quot; app dialogue 'no connection' start cups; cups is started"
date: 2016-12-11
forum: New to Ubuntu
---

### Post by nu2u904 on 2016-12-11
cups starts on startup yet when using "printer" app error  dialogue 'no connection'  start cups.
Doesn't get to the printer detect and recognition phase. Should I remove printer" app?

---

### Post by nu2u904 on 2016-12-11
> **nu2u904 said:**
> cups starts on startup yet when using "printer" app error  dialogue 'no connection'  start cups.
Doesn't get to the printer detect and recognition phase. Should I remove printer" app?

code
```
donald@donald-HP-Z400-Workstation:~$ service cups status
cups.service
   Loaded: masked (/dev/null; bad)
   Active: inactive (dead)
donald@donald-HP-Z400-Workstation:~$ 

donald@donald-HP-Z400-Workstation:~$ sudo service cups start
[sudo] password for donald: 
Failed to start cups.service: Unit cups.service is masked.
donald@donald-HP-Z400-Workstation:~$

```
How do I unmask cups.service such that the status is ok and I can start it?

How did it get masked in the first place? What is this masdk?

I have run update and restarted the computer to no avail.

---

### Post by SeijiSensei on 2016-12-11
What Ubuntu version is this?  If it's 16.04 or later, it uses systemd.  To start a service use "sudo systemctl start cups".

---

### Post by nu2u904 on 2016-12-11
code
```
donald@donald-HP-Z400-Workstation:~$ sudo systemctl start cups
Failed to start cups.service: Unit cups.service is masked.
donald@donald-HP-Z400-Workstation:~$
```

---

### Post by SeijiSensei on 2016-12-11
According to [http://www.tecmint.com/manage-services-using-systemd-and-systemctl-in-linux/](http://www.tecmint.com/manage-services-using-systemd-and-systemctl-in-linux/), you might be able to solve this problem with 
```
sudo systemctl unmask cups.service
```
Even though you failed to tell us what version of Ubuntu you're running, I'm guessing it's 16.04 or later.  There was no "masking" of services using the older SysV method of handling services. That seems to be a systemd thing.

---

### Post by nu2u904 on 2016-12-12
Thank you. Running  ubuntu 16.04

code
```
Failed to start cups.service: Unit cups.service is masked.
donald@donald-HP-Z400-Workstation:~$ sudo systemctl unmask cups service
Removed symlink /etc/systemd/system/cups.service.
donald@donald-HP-Z400-Workstation:~$ status systemctl cups service
status: Unknown job: systemctl
donald@donald-HP-Z400-Workstation:~$ sudo systemctl start cups
donald@donald-HP-Z400-Workstation:~$ status systemctl cups service
status: Unknown job: systemctl
donald@donald-HP-Z400-Workstation:~$ sudo systemctl start cups
donald@donald-HP-Z400-Workstation:~$ 
```

I don't get a response from start cups; no request for my password.

Here is dialogue from 'printers:
.'Printing service is not available.Start the service or connect to another computer.
'Not connected'

---

### Post by Geoffrey_Arndt on 2016-12-12
If you're using Firefox, you might want to take a look at "localhost:631" and see if you can delete current driver and reinstall after running a new scan in the CUPS online mgmt web-app.

---

### Post by nu2u904 on 2016-12-12
Tried this.
code
```
donald@donald-HP-Z400-Workstation:~$ sudo systemctl start cups
donald@donald-HP-Z400-Workstation:~$ sudo service cups start
[sudo] password for donald: 
donald@donald-HP-Z400-Workstation:~$ service cups status
&#9679; cups.service - LSB: CUPS Printing spooler and server
   Loaded: loaded (/etc/init.d/cups; bad; vendor preset: enabled)
   Active: active (exited) since Sun 2016-12-11 23:56:03 EST; 28min ago
     Docs: man:systemd-sysv-generator(8)
  Process: 8798 ExecStart=/etc/init.d/cups start (code=exited, status=0/SUCCESS)

Dec 11 23:56:03 donald-HP-Z400-Workstation systemd[1]: Starting LSB: CUPS Printi
Dec 11 23:56:03 donald-HP-Z400-Workstation systemd[1]: Started LSB: CUPS Printin
Dec 12 00:01:44 donald-HP-Z400-Workstation systemd[1]: Started LSB: CUPS Printin
Dec 12 00:24:25 donald-HP-Z400-Workstation systemd[1]: Started LSB: CUPS Printin
lines 1-10/10 (END)
```

'Printers' still returned same not connected dialogue

Attempted to print directly from document without using 'printers', didn't work, showed only a generic printer.

---

### Post by nu2u904 on 2016-12-12
Thank you. Please give me  recipe/steps for how to do what you are suggesting. This is new territory for me.

---

### Post by nu2u904 on 2016-12-15
Synaptic showed cups not installed for 16.04 ; installed cups latest vsn.
 Got this error message. What do I do with it?

W: Can't drop privileges for downloading as file '/root/.synaptic/tmp//tmp_cl' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)

---

### Post by Geoffrey_Arndt on 2016-12-16
For the Ubuntu desktop version (all flavors), CUPS is part of the base system install.    Did you do a custom install or did you install Ubuntu Server versus desktop?   In general, what system modifications have you implemented (did you enable root account or change user or group permissions?) . .

---

### Post by nu2u904 on 2016-12-16
Solved  I ran synaptic manager for cups. Surprise cups not installed on 16.04. Installed  cups , successfully with latest version. Except got this error message:

W: Can't drop privileges for downloading as file '/root/.synaptic/tmp//tmp_cl' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)

What does this mean? What do I do now?

I will remove and install again cups.

Why wasn't cups included in the installation packages for Ubuntu 16.04?

Why did certain cups files exist so all my actions seemed normal, and cups not being installed

---

### Post by nu2u904 on 2016-12-16
code
```
Added additional packages ; installed successfully, no error.
Printers show hp laser-jet 2205 with ! mark
"There is a missing print filter for printer 'HP-Color-LaserJet-CP20025dn'.

Printer  above requires the '/usr/lib/cups/filter/hpps' program, but is not currently installed
ls -l /usr/lib/cups/filter/hpps
ls: cannot access '/usr/lib/cups/filter/hpps': No such file or director

sudo apt install /usr/lib/cups/filter/hpps
Reading package lists... Done
E: Unsupported file /usr/lib/cups/filter/hpps given on commandline
donald@donald-HP-Z400-Workstation:~$ ls -l /usr/lib/cups/filter/hpps
ls: cannot access '/usr/lib/cups/filter/hpps': No such file or directory
```
/code

Did several searches no luck. How do I obtain this file 'hpps'.
Queried hp web site  no mention of filters

---

### Post by Geoffrey_Arndt on 2016-12-16
Couple things, . . . is hplip installed?  If not, install it (suggest you also install Synaptic package manager if not already done as it provides a better view of what is installed and not).

Then start Firefox and again, input "localhost:631" in the url field to start the web Cups printer services.   Try to do the install via CUPS (just read the screen, find the add/install printer option and complete the dialog)

---

### Post by nu2u904 on 2016-12-16
code
Added additional packages ; installed successfully, no error.
Printers show hp laser-jet 2205 with ! mark
"There is a missing print filter for printer 'HP-Color-LaserJet-CP20025dn'.

Printer  above requires the '/usr/lib/cups/filter/hpps' program, but is not currently installed
```
ls -l /usr/lib/cups/filter/hpps
ls: cannot access '/usr/lib/cups/filter/hpps': No such file or directory
```

```
sudo apt install /usr/lib/cups/filter/hpps
Reading package lists... Done
E: Unsupported file /usr/lib/cups/filter/hpps given on commandline
donald@donald-HP-Z400-Workstation:~$ ls -l /usr/lib/cups/filter/hpps
ls: cannot access '/usr/lib/cups/filter/hpps': No such file or directory

```
Added additional packages ; installed successfully, no error.
Printers show hp laser-jet 2205 with ! mark
"There is a missing print filter for printer 'HP-Color-LaserJet-CP20025dn'.

Printer  above requires the '/usr/lib/cups/filter/hpps' program, but is not currently installed
```
ls -l /usr/lib/cups/filter/hpps
ls: cannot access '/usr/lib/cups/filter/hpps': No such file or director
```

```
sudo apt install /usr/lib/cups/filter/hpps
Reading package lists... Done
E: Unsupported file /usr/lib/cups/filter/hpps given on commandline
donald@donald-HP-Z400-Workstation:~$ ls -l /usr/lib/cups/filter/hpps
ls: cannot access '/usr/lib/cups/filter/hpps': No such file or directory
```

Did several searches no luck. How do I obtain this file 'hpps'.
Queried hp web site  no mention of filters
/code

---

### Post by DuckHook on 2016-12-16
...please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

*hpps* stands for "Hewlett Packard PostScript" and is a library file that does not come standalone because it is useless on its own without further supporting files and apps. To install it, you must install the package, *hplip*

*hplip* comes preinstalled in a default Ubuntu install, so I'm surprised that it's (presumably) missing. Did you remove some packages while trying to get your printer working?

In any case, please post output of:```
apt-cache policy hplip
```You should see something like this:```
hplip:
  Installed: 3.16.3+repack0-1
  Candidate: 3.16.3+repack0-1
  Version table:
 *** 3.16.3+repack0-1 500
        500 http://mirrors.accretive-networks.net/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
```If the section after "Installed:" reads "(none)", then you don't have it installed.

If not installed, then:```
sudo apt update && sudo apt install hplip
```*hpps* should install automatically once you install *hplip*.

It is also possible that your install is corrupted. Let's cross that bridge only if we come to it.

---

### Post by DuckHook on 2016-12-16
Please don't duplicate post. It confuses helpers and dilutes community effort.

***Threads merged.***

---

### Post by DuckHook on 2016-12-16
@nu2u904

Now that I see more of the background behind your various issues on this other (now merged) thread, it is becoming clearer that you have an incomplete and/or wonky install. Please answer Geoffrey_Arndt's questions. They are ***very important***. Otherwise, we are just spinning our wheels and wasting everybody's time.> **Geoffrey_Arndt said:**
> For the Ubuntu desktop version (all flavors), CUPS is part of the base system install.   *** Did you do a custom install or did you install Ubuntu Server versus desktop?   In general, what system modifications have you implemented (did you enable root account or change user or group permissions?)*** . .

---

### Post by nu2u904 on 2016-12-17
SOLVED

> **DuckHook said:**
> @nu2u904

Now that I see more of the background behind your various issues on this other (now merged) thread, it is becoming clearer that you have an incomplete and/or wonky install. Please answer Geoffrey_Arndt's questions. They are ***very important***. Otherwise, we are just spinning our wheels and wasting everybody's time.

Thank you Duckworth. As my prior code indicates I found cups missinf when I searched synaptic manager. I did complete install as indicated. I got an error message ; added additional packages, installed successfully. 'Printers' displayed my printer with a green check mark and a!; opening printer queue saw y jobs listed and the message also in the previous code filter missing. I followed your instructions code below:

```

donald@donald-HP-Z400-Workstation:~$ apt-cache policy hplip
hplip:
  Installed: (none)
  Candidate: 3.16.3+repack0-1
  Version table:
     3.16.3+repack0-1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main i386 Packages
        100 /var/lib/dpkg/status
donald@donald-HP-Z400-Workstation:~$ sudo apt update && sudo apt install hplip
[sudo] password for donald: 
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]    
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]  
Get:4 [http://ppa.launchpad.net/rednotebook/daily/ubuntu](http://ppa.launchpad.net/rednotebook/daily/ubuntu) xenial InRelease [17.5 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [433 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 DEP-11 Metadata [303 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [188 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 DEP-11 Metadata [121 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [145 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/multiverse i386 DEP-11 Metadata [2,520 B]
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/main i386 DEP-11 Metadata [208 B]
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe i386 DEP-11 Metadata [212 B]
Get:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/multiverse i386 DEP-11 Metadata [212 B]
Get:14 [http://ppa.launchpad.net/rednotebook/daily/ubuntu](http://ppa.launchpad.net/rednotebook/daily/ubuntu) xenial/main i386 Packages [556 B]
Get:15 [http://ppa.launchpad.net/rednotebook/daily/ubuntu](http://ppa.launchpad.net/rednotebook/daily/ubuntu) xenial/main Translation-en [312 B]
Get:16 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]    
Get:17 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main i386 DEP-11 Metadata [68.0 kB]
Get:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [43.0 kB]
Get:19 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe i386 DEP-11 Metadata [19.4 kB]
Get:20 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse i386 DEP-11 Metadata [212 B]
Fetched 1,649 kB in 3s (465 kB/s)                       
AppStream cache update completed, but some metadata was ignored due to errors.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  hplip-data libhpmud0 libsane-hpaio libsnmp-base libsnmp30
  printer-driver-hpcups printer-driver-postscript-hp python3-pexpect
  python3-pil python3-ptyprocess python3-renderpm python3-reportlab
  python3-reportlab-accel
Suggested packages:
  hplip-doc hplip-gui python3-notify2 system-config-printer
  snmp-mibs-downloader python-pexpect-doc python-pil-doc python3-pil-dbg
  python3-renderpm-dbg python3-egenix-mxtexttools python-reportlab-doc
The following NEW packages will be installed:
  hplip hplip-data libhpmud0 libsane-hpaio libsnmp-base libsnmp30
  printer-driver-hpcups printer-driver-postscript-hp python3-pexpect
  python3-pil python3-ptyprocess python3-renderpm python3-reportlab
  python3-reportlab-accel
0 upgraded, 14 newly installed, 0 to remove and 1 not upgraded.
Need to get 9,899 kB of archives.
After this operation, 24.3 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main i386 hplip-data all 3.16.3+repack0-1 [6,393 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main i386 libsnmp-base all 5.7.3+dfsg-1ubuntu4 [224 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main i386 libsnmp30 i386 5.7.3+dfsg-1ubuntu4 [830 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main i386 libhpmud0 i386 3.16.3+repack0-1 [114 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main i386 libsane-hpaio i386 3.16.3+repack0-1 [119 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main i386 printer-driver-hpcups i386 3.16.3+repack0-1 [256 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main i386 python3-ptyprocess all 0.5-1 [13.0 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main i386 python3-pexpect all 4.0.1-1 [41.2 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main i386 python3-pil i386 3.1.2-0ubuntu1 [319 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main i386 python3-reportlab-accel i386 3.3.0-1 [19.3 kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main i386 python3-reportlab all 3.3.0-1 [460 kB]
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main i386 hplip i386 3.16.3+repack0-1 [67.0 kB]
Get:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main i386 printer-driver-postscript-hp all 3.16.3+repack0-1 [1,009 kB]
Get:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main i386 python3-renderpm i386 3.3.0-1 [35.5 kB]
Fetched 9,899 kB in 1s (9,509 kB/s)          
Selecting previously unselected package hplip-data.
(Reading database ... 309675 files and directories currently installed.)
Preparing to unpack .../hplip-data_3.16.3+repack0-1_all.deb ...
Unpacking hplip-data (3.16.3+repack0-1) ...
Selecting previously unselected package libsnmp-base.
Preparing to unpack .../libsnmp-base_5.7.3+dfsg-1ubuntu4_all.deb ...
Unpacking libsnmp-base (5.7.3+dfsg-1ubuntu4) ...
Selecting previously unselected package libsnmp30:i386.
Preparing to unpack .../libsnmp30_5.7.3+dfsg-1ubuntu4_i386.deb ...
Unpacking libsnmp30:i386 (5.7.3+dfsg-1ubuntu4) ...
Selecting previously unselected package libhpmud0:i386.
Preparing to unpack .../libhpmud0_3.16.3+repack0-1_i386.deb ...
Unpacking libhpmud0:i386 (3.16.3+repack0-1) ...
Selecting previously unselected package libsane-hpaio:i386.
Preparing to unpack .../libsane-hpaio_3.16.3+repack0-1_i386.deb ...
Unpacking libsane-hpaio:i386 (3.16.3+repack0-1) ...
Selecting previously unselected package printer-driver-hpcups.
Preparing to unpack .../printer-driver-hpcups_3.16.3+repack0-1_i386.deb ...
Unpacking printer-driver-hpcups (3.16.3+repack0-1) ...
Selecting previously unselected package python3-ptyprocess.
Preparing to unpack .../python3-ptyprocess_0.5-1_all.deb ...
Unpacking python3-ptyprocess (0.5-1) ...
Selecting previously unselected package python3-pexpect.
Preparing to unpack .../python3-pexpect_4.0.1-1_all.deb ...
Unpacking python3-pexpect (4.0.1-1) ...
Selecting previously unselected package python3-pil:i386.
Preparing to unpack .../python3-pil_3.1.2-0ubuntu1_i386.deb ...
Unpacking python3-pil:i386 (3.1.2-0ubuntu1) ...
Selecting previously unselected package python3-reportlab-accel:i386.
Preparing to unpack .../python3-reportlab-accel_3.3.0-1_i386.deb ...
Unpacking python3-reportlab-accel:i386 (3.3.0-1) ...
Selecting previously unselected package python3-reportlab.
Preparing to unpack .../python3-reportlab_3.3.0-1_all.deb ...
Unpacking python3-reportlab (3.3.0-1) ...
Selecting previously unselected package hplip.
Preparing to unpack .../hplip_3.16.3+repack0-1_i386.deb ...
Unpacking hplip (3.16.3+repack0-1) ...
Selecting previously unselected package printer-driver-postscript-hp.
Preparing to unpack .../printer-driver-postscript-hp_3.16.3+repack0-1_all.deb ...
Unpacking printer-driver-postscript-hp (3.16.3+repack0-1) ...
Selecting previously unselected package python3-renderpm:i386.
Preparing to unpack .../python3-renderpm_3.3.0-1_i386.deb ...
Unpacking python3-renderpm:i386 (3.3.0-1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Processing triggers for cups (2.1.3-4) ...
Processing triggers for dbus (1.10.6-1ubuntu3.1) ...
Setting up hplip-data (3.16.3+repack0-1) ...
Setting up libsnmp-base (5.7.3+dfsg-1ubuntu4) ...
Setting up libsnmp30:i386 (5.7.3+dfsg-1ubuntu4) ...
Setting up libhpmud0:i386 (3.16.3+repack0-1) ...
Setting up libsane-hpaio:i386 (3.16.3+repack0-1) ...
Setting up printer-driver-hpcups (3.16.3+repack0-1) ...
Setting up python3-ptyprocess (0.5-1) ...
Setting up python3-pexpect (4.0.1-1) ...
Setting up python3-pil:i386 (3.1.2-0ubuntu1) ...
Setting up python3-reportlab-accel:i386 (3.3.0-1) ...
Setting up python3-reportlab (3.3.0-1) ...
Setting up hplip (3.16.3+repack0-1) ...
Creating/updating hplip user account...
Setting up printer-driver-postscript-hp (3.16.3+repack0-1) ...
Setting up python3-renderpm:i386 (3.3.0-1) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
donald@donald-HP-Z400-Workstation:~$ apt-cache policy hplip
hplip:
  Installed: 3.16.3+repack0-1
  Candidate: 3.16.3+repack0-1
  Version table:
 *** 3.16.3+repack0-1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main i386 Packages
        100 /var/lib/dpkg/status

donald@donald-HP-Z400-Workstation:~$ ls -l /usr/lib/cups/filter/hpps
-rwxr-xr-x 1 root root 12675 Mar 29  2016 /usr/lib/cups/filter/hpps
donald@donald-HP-Z400-Workstation:~$ 

```


'printers' showed my printer same green check and!; queue showed y jobs and same missing filter message.

Then I printed document from Libre Writer. Success. No  problem 'printers' shows only green check mark.
Thank you for your help. This haws been an very educational experience.

The question remains why was not cups and hplip installed in 16.04 as it was in 14.04..

---

### Post by DuckHook on 2016-12-17
So glad it worked out for you. I too am mystified why your install was missing the whole printing subsystem. I've only encountered that once before on these forums and it remained a mystery that time too.

My only other thought would be: if your printing subsystem was missing, then other subsystems may be missing too. Hopefully not, but if you run into further issues and start other threads, it is a good idea to briefly mention that it was a new default install and it was missing the printing subsystem (with a link to this thread).

Good Luck and Happy Ubuntuing!

---

