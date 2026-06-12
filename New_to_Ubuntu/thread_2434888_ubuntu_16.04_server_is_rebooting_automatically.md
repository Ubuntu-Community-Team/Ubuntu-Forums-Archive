---
title: "ubuntu 16.04 server is rebooting automatically"
date: 2020-01-13
forum: New to Ubuntu
---

### Post by humminganurag on 2020-01-13
Hello All,

we have a HPE server(ProLiant DL580 Gen10) which is rebooting intermittently . Is it something do be done with auto update issue ?

I couldn't see any hardware issues in mcelog and syslog

```
[EMAIL="root@gamma-csoc1:/etc/apt/apt.conf"]root@gamma-csoc1:/etc/apt/apt.conf[/EMAIL].d# cat 50unattended-upgrades
// Automatically upgrade packages from these (origin:archive) pairs
Unattended-Upgrade::Allowed-Origins {
    "${distro_id}:${distro_codename}";
    "${distro_id}:${distro_codename}-security";
    // Extended Security Maintenance; doesn't necessarily exist for
    // every release and this system may not have it installed, but if
    // available, the policy for updates is such that unattended-upgrades
    // should also install from here by default.
    "${distro_id}ESM:${distro_codename}";
//    "${distro_id}:${distro_codename}-updates";
//    "${distro_id}:${distro_codename}-proposed";
//    "${distro_id}:${distro_codename}-backports";
};


// List of packages to not update (regexp are supported)
Unattended-Upgrade::Package-Blacklist {
//    "vim";
//    "libc6";
//    "libc6-dev";
//    "libc6-i686";
};


// This option allows you to control if on a unclean dpkg exit
// unattended-upgrades will automatically run 
//   dpkg --force-confold --configure -a
// The default is true, to ensure updates keep getting installed
//Unattended-Upgrade::AutoFixInterruptedDpkg "false";


// Split the upgrade into the smallest possible chunks so that
// they can be interrupted with SIGUSR1. This makes the upgrade
// a bit slower but it has the benefit that shutdown while a upgrade
// is running is possible (with a small delay)
//Unattended-Upgrade::MinimalSteps "true";


// Install all unattended-upgrades when the machine is shuting down
// instead of doing it in the background while the machine is running
// This will (obviously) make shutdown slower
//Unattended-Upgrade::InstallOnShutdown "true";


// Send email to this address for problems or packages upgrades
// If empty or unset then no email is sent, make sure that you
// have a working mail setup on your system. A package that provides
// 'mailx' must be installed. E.g. "user@example.com"
//Unattended-Upgrade::Mail "root";


// Set this value to "true" to get emails only on errors. Default
// is to always send a mail if Unattended-Upgrade::Mail is set
//Unattended-Upgrade::MailOnlyOnError "true";


// Do automatic removal of new unused dependencies after the upgrade
// (equivalent to apt-get autoremove)
//Unattended-Upgrade::Remove-Unused-Dependencies "false";


// Automatically reboot *WITHOUT CONFIRMATION*
//  if the file /var/run/reboot-required is found after the upgrade 
//Unattended-Upgrade::Automatic-Reboot "false";


// If automatic reboot is enabled and needed, reboot at the specific
// time instead of immediately
//  Default: "now"
//Unattended-Upgrade::Automatic-Reboot-Time "02:00";


// Use apt bandwidth limit feature, this example limits the download
// speed to 70kb/sec
//Acquire::http::Dl-Limit "70";




[EMAIL="root@gamma-csoc1:/etc/apt/apt.conf"]root@gamma-csoc1:/etc/apt/apt.conf[/EMAIL].d# cat 20auto-upgrades
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Unattended-Upgrade "1";


```
PLease let me know any log outputs are required. Thank you very much in advance


Regards,
Anurag

---

### Post by wildmanne39 on 2020-01-13
*Thread moved to **New to Ubuntu a more appropriate sub-forum**.* 

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end, if you are editing a post to add code tags click the edit button then click the go advanced button, highlight the code then select the # symbol from the tool bar.

---

### Post by mastablasta on 2020-01-13
no it has nothing to do with updates
you have reboot disabled:
```
//Unattended-Upgrade::Automatic-Reboot "false";
```

check logs in /var/log to see why the reboot occurs. it could still be a hardware failure. 

Things on hardware  that can cause reboot rather than a hung system: CPU overheating, GPU overheating, bad GPU, bad capacitors, bad PSU, bad capacitors on PSU...

various software issues can also cause reboot. though this is rare these days.

---

### Post by humminganurag on 2020-01-13
Okay I will dig into other aspects.  Thanks for your suggestion

---

