---
title: "sudo apt-get update errors"
date: 2012-04-25
forum: New to Ubuntu
---

### Post by kootenaytara on 2012-04-25
Hello all,

Apologies in advance for my lack of knowledge - I'm just learning Linux!

I'm attempting to install Gnome and vnc4server on my Ubuntu 11.04 VPS. This is a brand new server, but when I run sudo apt-get update I get the following errors. Could someone explain to me what these are and how to go about correcting them? Thanks again for the help!

```
root@2:~# sudo apt-get update
Ign http://archive.canonical.com natty InRelease
Err http://archive.canonical.com natty Release.gpg
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Ign http://archive.canonical.com natty Release
Ign http://archive.canonical.com natty/partner TranslationIndex
Err http://archive.canonical.com natty/partner amd64 Packages
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err http://archive.canonical.com natty/partner Translation-en
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Ign http://archive.ubuntu.com natty InRelease
Ign http://archive.ubuntu.com natty-updates InRelease
Ign http://archive.ubuntu.com natty-security InRelease
Err http://archive.ubuntu.com natty Release.gpg
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty-updates Release.gpg
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty-security Release.gpg
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://archive.ubuntu.com natty Release
Ign http://archive.ubuntu.com natty-updates Release
Ign http://archive.ubuntu.com natty-security Release
Ign http://archive.ubuntu.com natty/main TranslationIndex
Ign http://archive.ubuntu.com natty/restricted TranslationIndex
Ign http://archive.ubuntu.com natty/universe TranslationIndex
Ign http://archive.ubuntu.com natty-updates/main TranslationIndex
Ign http://archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://archive.ubuntu.com natty-updates/universe TranslationIndex
Ign http://archive.ubuntu.com natty-security/main TranslationIndex
Ign http://archive.ubuntu.com natty-security/restricted TranslationIndex
Ign http://archive.ubuntu.com natty-security/universe TranslationIndex
Err http://archive.ubuntu.com natty/main amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty/restricted amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty/universe amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty-updates/main amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty-updates/restricted amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty-updates/universe amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty-security/main amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty-security/restricted amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty-security/universe amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty/main Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty/restricted Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty/universe Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty-updates/main Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty-updates/restricted Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty-updates/universe Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty-security/main Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty-security/restricted Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty-security/universe Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/Release.gpg  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/partner/binary-amd64/Packages  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/partner/i18n/Translation-en  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/Release.gpg  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/Release.gpg  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/main/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/restricted/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/universe/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/main/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/universe/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/main/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/restricted/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/universe/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/restricted/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/universe/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/main/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/universe/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/main/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/restricted/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/universe/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by sandyd on 2012-04-26
> **kootenaytara said:**
> Hello all,

Apologies in advance for my lack of knowledge - I'm just learning Linux!

I'm attempting to install Gnome and vnc4server on my Ubuntu 11.04 VPS. This is a brand new server, but when I run sudo apt-get update I get the following errors. Could someone explain to me what these are and how to go about correcting them? Thanks again for the help!

```
root@2:~# sudo apt-get update
Ign http://archive.canonical.com natty InRelease
Err http://archive.canonical.com natty Release.gpg
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Ign http://archive.canonical.com natty Release
Ign http://archive.canonical.com natty/partner TranslationIndex
Err http://archive.canonical.com natty/partner amd64 Packages
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err http://archive.canonical.com natty/partner Translation-en
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Ign http://archive.ubuntu.com natty InRelease
Ign http://archive.ubuntu.com natty-updates InRelease
Ign http://archive.ubuntu.com natty-security InRelease
Err http://archive.ubuntu.com natty Release.gpg
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty-updates Release.gpg
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty-security Release.gpg
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://archive.ubuntu.com natty Release
Ign http://archive.ubuntu.com natty-updates Release
Ign http://archive.ubuntu.com natty-security Release
Ign http://archive.ubuntu.com natty/main TranslationIndex
Ign http://archive.ubuntu.com natty/restricted TranslationIndex
Ign http://archive.ubuntu.com natty/universe TranslationIndex
Ign http://archive.ubuntu.com natty-updates/main TranslationIndex
Ign http://archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://archive.ubuntu.com natty-updates/universe TranslationIndex
Ign http://archive.ubuntu.com natty-security/main TranslationIndex
Ign http://archive.ubuntu.com natty-security/restricted TranslationIndex
Ign http://archive.ubuntu.com natty-security/universe TranslationIndex
Err http://archive.ubuntu.com natty/main amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty/restricted amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty/universe amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty-updates/main amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty-updates/restricted amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty-updates/universe amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty-security/main amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty-security/restricted amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty-security/universe amd64 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty/main Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty/restricted Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty/universe Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty-updates/main Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty-updates/restricted Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty-updates/universe Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty-security/main Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty-security/restricted Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.ubuntu.com natty-security/universe Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/Release.gpg  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/partner/binary-amd64/Packages  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/partner/i18n/Translation-en  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/Release.gpg  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/Release.gpg  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/main/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/restricted/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/universe/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/main/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/universe/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/main/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/restricted/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/universe/binary-amd64/Packages  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/restricted/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/universe/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/main/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-updates/universe/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/main/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/restricted/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/universe/i18n/Translation-en  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.

```
Setup the nameservers in /etc/resolv.conf.
```

nano /etc/resolv.conf
```
```

nameserver 208.67.222.222
nameserver 208.67.220.220
```
BTW, Ubuntu 12.04 should be out in a few hours - you should upgrade to that LTS instead of using old versions of ubuntu. You will need to upgrade to Ubuntu 11.10, then to 12.04.

---

### Post by kootenaytara on 2012-04-26
> **sandyd said:**
> Setup the nameservers in /etc/resolv.conf.
```

nano /etc/resolv.conf
```
```

nameserver 208.67.222.222
nameserver 208.67.220.220
```
BTW, Ubuntu 12.04 should be out in a few hours - you should upgrade to that LTS instead of using old versions of ubuntu. You will need to upgrade to Ubuntu 11.10, then to 12.04.

Thanks for the help! Unfortunately though, running nano (or gedit for that matter) results in "Gtk-WARNING **: cannot open display:"

I think I need to enable x11 forwarding in /etc/ssh/sshd_config, but if I can't use nano or gedit, how do I do that? (Sorry - I'm sure that's a silly question, but I'm stuck!)

Thanks in advance...

---

### Post by sandyd on 2012-04-26
> **kootenaytara said:**
> Thanks for the help! Unfortunately though, running nano (or gedit for that matter) results in "Gtk-WARNING **: cannot open display:"

I think I need to enable x11 forwarding in /etc/ssh/sshd_config, but if I can't use nano or gedit, how do I do that? (Sorry - I'm sure that's a silly question, but I'm stuck!)

Thanks in advance...
nano should not output that message.
Nano is not a graphical text editor.

---

### Post by kootenaytara on 2012-04-26
Thanks again, and sorry for the mistake. Gedit produces that error. ```
nano /etc/resolv.conf
``` gives me the following:

-bash: nano: command not found

---

### Post by kenneth.koontz on 2012-04-29
@kootenaytara

If you havn't already found out. You probably didn't have nano installed.

```
$ sudo apt-get install nano
```

---

### Post by kalmos on 2012-05-06
(Ignore my details shown on the left. I am not using 10.04 -- I am using 11.10. The forums won't let me change this because I have less than 50 posts. That doesn't make any sense, but I don't care right now.)

I'm trying to fix a "Disconnected from Plymouth" error described in detail [here]("http://askubuntu.com/questions/132742/mountall-disconnected-from-plymouth") (askubuntu.com).

I boot from a live CD and execute the following to chroot into my linux installation:

```
sudo chroot /media/linux
```Next, when I do:

```
apt-get update
```I get the following output:

```
sh: cannot create /dev/null: Permission denied
Ign http://us.archive.ubuntu.com oneiric InRelease
Ign http://us.archive.ubuntu.com oneiric-updates InRelease
Ign http://us.archive.ubuntu.com oneiric-backports InRelease
Ign http://us.archive.ubuntu.com oneiric-security InRelease
Ign http://extras.ubuntu.com oneiric InRelease
Ign http://repository.spotify.com stable InRelease
Ign http://ppa.launchpad.net lucid InRelease
Ign http://ppa.launchpad.net oneiric InRelease
Ign http://ppa.launchpad.net oneiric InRelease
Ign http://ppa.launchpad.net oneiric InRelease
Ign http://ppa.launchpad.net oneiric InRelease
Ign http://ppa.launchpad.net oneiric InRelease
Ign http://ppa.launchpad.net oneiric InRelease
Ign http://linux.dropbox.com oneiric InRelease
Ign http://streaming.stat.iastate.edu oneiric/ InRelease
Ign http://dl.google.com stable InRelease
Ign http://dl.google.com stable InRelease
Ign http://www.ksplice.com oneiric InRelease
Ign http://www.mendeley.com  InRelease
Ign http://download.toggl.com stable InRelease
Err http://us.archive.ubuntu.com oneiric Release.gpg
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-updates Release.gpg
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-backports Release.gpg
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://archive.canonical.com oneiric InRelease
Err http://extras.ubuntu.com oneiric Release.gpg
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://repository.spotify.com stable Release.gpg
  Something wicked happened resolving 'repository.spotify.com:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net lucid Release.gpg
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net oneiric Release.gpg
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net oneiric Release.gpg
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net oneiric Release.gpg
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net oneiric Release.gpg
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net oneiric Release.gpg
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://linux.dropbox.com oneiric Release.gpg
  Something wicked happened resolving 'linux.dropbox.com:http' (-5 - No address associated with hostname)
Err http://streaming.stat.iastate.edu oneiric/ Release.gpg
  Something wicked happened resolving 'streaming.stat.iastate.edu:http' (-5 - No address associated with hostname)
Ign http://extras.ubuntu.com oneiric Release
Ign http://repository.spotify.com stable Release
Ign http://linux.dropbox.com oneiric Release
Err http://dl.google.com stable Release.gpg
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Err http://www.ksplice.com oneiric Release.gpg
  Something wicked happened resolving 'www.ksplice.com:http' (-5 - No address associated with hostname)
Err http://www.mendeley.com  Release.gpg
  Something wicked happened resolving 'www.mendeley.com:http' (-5 - No address associated with hostname)
Err http://download.toggl.com stable Release.gpg
  Something wicked happened resolving 'download.toggl.com:http' (-5 - No address associated with hostname)
Ign http://streaming.stat.iastate.edu oneiric/ Release
Err http://ppa.launchpad.net oneiric Release.gpg
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Ign http://ppa.launchpad.net lucid Release
Err http://us.archive.ubuntu.com oneiric-security Release.gpg
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://archive.canonical.com oneiric Release.gpg
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Ign http://extras.ubuntu.com oneiric/main Sources/DiffIndex
Ign http://repository.spotify.com stable/non-free amd64 Packages/DiffIndex
Ign http://ppa.launchpad.net oneiric Release
Ign http://ppa.launchpad.net oneiric Release
Ign http://ppa.launchpad.net oneiric Release
Ign http://ppa.launchpad.net oneiric Release
Ign http://linux.dropbox.com oneiric/main amd64 Packages/DiffIndex
Err http://dl.google.com stable Release.gpg
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Ign http://www.ksplice.com oneiric Release
Ign http://www.mendeley.com  Release
Ign http://download.toggl.com stable Release
Ign http://us.archive.ubuntu.com oneiric Release
Ign http://us.archive.ubuntu.com oneiric-updates Release
Ign http://streaming.stat.iastate.edu oneiric/ Sources/DiffIndex
Ign http://ppa.launchpad.net oneiric Release
Ign http://ppa.launchpad.net oneiric Release
Ign http://ppa.launchpad.net lucid/main Sources/DiffIndex
Ign http://ppa.launchpad.net lucid/main amd64 Packages/DiffIndex
Ign http://ppa.launchpad.net lucid/main TranslationIndex
Ign http://ppa.launchpad.net oneiric/main Sources/DiffIndex
Ign http://ppa.launchpad.net oneiric/main amd64 Packages/DiffIndex
Ign http://ppa.launchpad.net oneiric/main TranslationIndex
Ign http://ppa.launchpad.net oneiric/main Sources/DiffIndex
Ign http://ppa.launchpad.net oneiric/main amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com oneiric-backports Release
Ign http://us.archive.ubuntu.com oneiric-security Release
Ign http://us.archive.ubuntu.com oneiric/main Sources/DiffIndex
Ign http://us.archive.ubuntu.com oneiric/restricted Sources/DiffIndex
Ign http://us.archive.ubuntu.com oneiric/universe Sources/DiffIndex
Ign http://us.archive.ubuntu.com oneiric/multiverse Sources/DiffIndex
Ign http://us.archive.ubuntu.com oneiric/main amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com oneiric/restricted amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com oneiric/universe amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com oneiric/multiverse amd64 Packages/DiffIndex
Ign http://archive.canonical.com oneiric Release
Ign http://extras.ubuntu.com oneiric/main amd64 Packages/DiffIndex
Ign http://extras.ubuntu.com oneiric/main TranslationIndex
Ign http://repository.spotify.com stable/non-free TranslationIndex
Ign http://linux.dropbox.com oneiric/main TranslationIndex
Ign http://dl.google.com stable Release
Ign http://www.ksplice.com oneiric/ksplice Sources/DiffIndex
Ign http://www.mendeley.com  Packages/DiffIndex
Ign http://download.toggl.com stable/main amd64 Packages/DiffIndex
Ign http://streaming.stat.iastate.edu oneiric/ Packages/DiffIndex
Ign http://us.archive.ubuntu.com oneiric/main TranslationIndex
Ign http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com oneiric/restricted TranslationIndex
Ign http://us.archive.ubuntu.com oneiric/universe TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-updates/main Sources/DiffIndex
Ign http://us.archive.ubuntu.com oneiric-updates/restricted Sources/DiffIndex
Ign http://us.archive.ubuntu.com oneiric-updates/universe Sources/DiffIndex
Ign http://us.archive.ubuntu.com oneiric-updates/multiverse Sources/DiffIndex
Ign http://us.archive.ubuntu.com oneiric-updates/main amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com oneiric-updates/restricted amd64 Packages/DiffIndex
Ign http://archive.canonical.com oneiric/partner Sources/DiffIndex
Ign http://ppa.launchpad.net oneiric/main TranslationIndex
Ign http://ppa.launchpad.net oneiric/main Sources/DiffIndex
Ign http://ppa.launchpad.net oneiric/main amd64 Packages/DiffIndex
Ign http://ppa.launchpad.net oneiric/main TranslationIndex
Ign http://ppa.launchpad.net oneiric/main Sources/DiffIndex
Ign http://ppa.launchpad.net oneiric/main amd64 Packages/DiffIndex
Ign http://ppa.launchpad.net oneiric/main TranslationIndex
Ign http://ppa.launchpad.net oneiric/main Sources/DiffIndex
Ign http://ppa.launchpad.net oneiric/main amd64 Packages/DiffIndex
Ign http://ppa.launchpad.net oneiric/main TranslationIndex
Ign http://dl.google.com stable Release
Ign http://www.ksplice.com oneiric/ksplice amd64 Packages/DiffIndex
Ign http://www.ksplice.com oneiric/ksplice TranslationIndex
Ign http://download.toggl.com stable/main TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-updates/universe amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-backports/main Sources/DiffIndex
Ign http://us.archive.ubuntu.com oneiric-backports/restricted Sources/DiffIndex
Ign http://us.archive.ubuntu.com oneiric-backports/universe Sources/DiffIndex
Ign http://us.archive.ubuntu.com oneiric-backports/multiverse Sources/DiffIndex
Ign http://archive.canonical.com oneiric/partner amd64 Packages/DiffIndex
Ign http://archive.canonical.com oneiric/partner TranslationIndex
Ign http://ppa.launchpad.net oneiric/main Sources/DiffIndex
Ign http://ppa.launchpad.net oneiric/main amd64 Packages/DiffIndex
Ign http://ppa.launchpad.net oneiric/main TranslationIndex
Ign http://dl.google.com stable/main amd64 Packages/DiffIndex
Ign http://dl.google.com stable/main TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-backports/main amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com oneiric-backports/restricted amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com oneiric-backports/universe amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com oneiric-backports/multiverse amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com oneiric-backports/main TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-backports/universe TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-security/main Sources/DiffIndex
Ign http://us.archive.ubuntu.com oneiric-security/restricted Sources/DiffIndex
Ign http://dl.google.com stable/main amd64 Packages/DiffIndex
Ign http://dl.google.com stable/main TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-security/universe Sources/DiffIndex
Ign http://us.archive.ubuntu.com oneiric-security/multiverse Sources/DiffIndex
Ign http://us.archive.ubuntu.com oneiric-security/main amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com oneiric-security/restricted amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com oneiric-security/universe amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com oneiric-security/multiverse amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com oneiric-security/main TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-security/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-security/restricted TranslationIndex
Ign http://us.archive.ubuntu.com oneiric-security/universe TranslationIndex
Err http://streaming.stat.iastate.edu oneiric/ Translation-en_US
  Something wicked happened resolving 'streaming.stat.iastate.edu:http' (-5 - No address associated with hostname)
Err http://extras.ubuntu.com oneiric/main Sources
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://streaming.stat.iastate.edu oneiric/ Translation-en
  Something wicked happened resolving 'streaming.stat.iastate.edu:http' (-5 - No address associated with hostname)
Err http://streaming.stat.iastate.edu oneiric/ Sources
  Something wicked happened resolving 'streaming.stat.iastate.edu:http' (-5 - No address associated with hostname)
Err http://streaming.stat.iastate.edu oneiric/ Packages
  Something wicked happened resolving 'streaming.stat.iastate.edu:http' (-5 - No address associated with hostname)
Err http://extras.ubuntu.com oneiric/main amd64 Packages
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://extras.ubuntu.com oneiric/main Translation-en_US
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://extras.ubuntu.com oneiric/main Translation-en
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://repository.spotify.com stable/non-free amd64 Packages
  Something wicked happened resolving 'repository.spotify.com:http' (-5 - No address associated with hostname)
Err http://linux.dropbox.com oneiric/main amd64 Packages
  Something wicked happened resolving 'linux.dropbox.com:http' (-5 - No address associated with hostname)
Err http://archive.canonical.com oneiric/partner Sources
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err http://repository.spotify.com stable/non-free Translation-en_US
  Something wicked happened resolving 'repository.spotify.com:http' (-5 - No address associated with hostname)
Err http://repository.spotify.com stable/non-free Translation-en
  Something wicked happened resolving 'repository.spotify.com:http' (-5 - No address associated with hostname)
Err http://linux.dropbox.com oneiric/main Translation-en_US
  Something wicked happened resolving 'linux.dropbox.com:http' (-5 - No address associated with hostname)
Err http://linux.dropbox.com oneiric/main Translation-en
  Something wicked happened resolving 'linux.dropbox.com:http' (-5 - No address associated with hostname)
Err http://dl.google.com stable/main amd64 Packages
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Err http://dl.google.com stable/main Translation-en_US
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Err http://www.ksplice.com oneiric/ksplice Sources
  Something wicked happened resolving 'www.ksplice.com:http' (-5 - No address associated with hostname)
Err http://www.mendeley.com  Translation-en_US
  Something wicked happened resolving 'www.mendeley.com:http' (-5 - No address associated with hostname)
Err http://www.mendeley.com  Translation-en
  Something wicked happened resolving 'www.mendeley.com:http' (-5 - No address associated with hostname)
Err http://archive.canonical.com oneiric/partner amd64 Packages
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err http://archive.canonical.com oneiric/partner Translation-en_US
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err http://archive.canonical.com oneiric/partner Translation-en
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err http://dl.google.com stable/main Translation-en
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Err http://dl.google.com stable/main amd64 Packages
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Err http://dl.google.com stable/main Translation-en_US
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Err http://dl.google.com stable/main Translation-en
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Err http://www.ksplice.com oneiric/ksplice amd64 Packages
  Something wicked happened resolving 'www.ksplice.com:http' (-5 - No address associated with hostname)
Err http://www.ksplice.com oneiric/ksplice Translation-en_US
  Something wicked happened resolving 'www.ksplice.com:http' (-5 - No address associated with hostname)
Err http://www.ksplice.com oneiric/ksplice Translation-en
  Something wicked happened resolving 'www.ksplice.com:http' (-5 - No address associated with hostname)
Err http://www.mendeley.com  Packages
  Something wicked happened resolving 'www.mendeley.com:http' (-5 - No address associated with hostname)
Err http://download.toggl.com stable/main amd64 Packages
  Something wicked happened resolving 'download.toggl.com:http' (-5 - No address associated with hostname)
Err http://download.toggl.com stable/main Translation-en_US
  Something wicked happened resolving 'download.toggl.com:http' (-5 - No address associated with hostname)
Err http://download.toggl.com stable/main Translation-en
  Something wicked happened resolving 'download.toggl.com:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net lucid/main Sources
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net lucid/main amd64 Packages
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net lucid/main Translation-en_US
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net lucid/main Translation-en
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net oneiric/main Sources
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net oneiric/main amd64 Packages
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net oneiric/main Translation-en_US
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net oneiric/main Translation-en
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net oneiric/main Sources
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net oneiric/main amd64 Packages
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net oneiric/main Translation-en_US
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net oneiric/main Translation-en
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net oneiric/main Sources
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net oneiric/main amd64 Packages
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net oneiric/main Translation-en_US
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net oneiric/main Translation-en
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net oneiric/main Sources
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net oneiric/main amd64 Packages
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net oneiric/main Translation-en_US
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net oneiric/main Translation-en
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net oneiric/main Sources
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net oneiric/main amd64 Packages
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net oneiric/main Translation-en_US
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net oneiric/main Translation-en
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net oneiric/main Sources
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net oneiric/main amd64 Packages
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net oneiric/main Translation-en_US
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net oneiric/main Translation-en
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric/main Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric/restricted Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric/universe Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric/multiverse Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric/main amd64 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric/restricted amd64 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric/universe amd64 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric/multiverse amd64 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric/main Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric/main Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric/multiverse Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric/multiverse Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric/restricted Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric/restricted Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric/universe Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric/universe Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-updates/main Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-updates/restricted Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-updates/universe Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-updates/multiverse Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-updates/main amd64 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-updates/restricted amd64 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-updates/universe amd64 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-updates/main Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-updates/main Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-updates/universe Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-updates/universe Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-backports/main Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-backports/restricted Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-backports/universe Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-backports/multiverse Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-backports/main amd64 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-backports/restricted amd64 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-backports/universe amd64 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-backports/multiverse amd64 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-backports/main Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-backports/main Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-backports/universe Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-backports/universe Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-security/main Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-security/restricted Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-security/universe Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-security/multiverse Sources
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-security/main amd64 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-security/restricted amd64 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-security/universe amd64 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-security/multiverse amd64 Packages
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-security/main Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-security/main Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-security/multiverse Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-security/multiverse Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-security/restricted Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-security/restricted Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-security/universe Translation-en_US
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://us.archive.ubuntu.com oneiric-security/universe Translation-en
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release.gpg  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://repository.spotify.com/dists/stable/Release.gpg  Something wicked happened resolving 'repository.spotify.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/anatol/tup/ubuntu/dists/lucid/Release.gpg  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/albertomilone/hamster-indicator/ubuntu/dists/oneiric/Release.gpg  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/alecive/antigone/ubuntu/dists/oneiric/Release.gpg  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/dists/oneiric/Release.gpg  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/p12/ppa/ubuntu/dists/oneiric/Release.gpg  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/oneiric/Release.gpg  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/oneiric/Release.gpg  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://linux.dropbox.com/ubuntu/dists/oneiric/Release.gpg  Something wicked happened resolving 'linux.dropbox.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://streaming.stat.iastate.edu/CRAN/bin/linux/ubuntu/oneiric/Release.gpg  Something wicked happened resolving 'streaming.stat.iastate.edu:http' (-5 - No address associated with hostname)

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://www.ksplice.com/apt/dists/oneiric/Release.gpg  Something wicked happened resolving 'www.ksplice.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://www.mendeley.com/repositories/ubuntu/stable/Release.gpg  Something wicked happened resolving 'www.mendeley.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://download.toggl.com/toggldesktop/deb/dists/stable/Release.gpg  Something wicked happened resolving 'download.toggl.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/oneiric/Release.gpg  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://streaming.stat.iastate.edu/CRAN/bin/linux/ubuntu/oneiric/en_US  Something wicked happened resolving 'streaming.stat.iastate.edu:http' (-5 - No address associated with hostname)

W: Failed to fetch http://streaming.stat.iastate.edu/CRAN/bin/linux/ubuntu/oneiric/en  Something wicked happened resolving 'streaming.stat.iastate.edu:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://repository.spotify.com/dists/stable/non-free/binary-amd64/Packages  Something wicked happened resolving 'repository.spotify.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://linux.dropbox.com/ubuntu/dists/oneiric/main/binary-amd64/Packages  Something wicked happened resolving 'linux.dropbox.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://www.mendeley.com/repositories/ubuntu/stable/en_US  Something wicked happened resolving 'www.mendeley.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://www.mendeley.com/repositories/ubuntu/stable/en  Something wicked happened resolving 'www.mendeley.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://streaming.stat.iastate.edu/CRAN/bin/linux/ubuntu/oneiric/Sources  Something wicked happened resolving 'streaming.stat.iastate.edu:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/anatol/tup/ubuntu/dists/lucid/main/source/Sources  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/anatol/tup/ubuntu/dists/lucid/main/binary-amd64/Packages  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/anatol/tup/ubuntu/dists/lucid/main/i18n/Translation-en_US  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/anatol/tup/ubuntu/dists/lucid/main/i18n/Translation-en  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/albertomilone/hamster-indicator/ubuntu/dists/oneiric/main/source/Sources  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/albertomilone/hamster-indicator/ubuntu/dists/oneiric/main/binary-amd64/Packages  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/albertomilone/hamster-indicator/ubuntu/dists/oneiric/main/i18n/Translation-en_US  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/albertomilone/hamster-indicator/ubuntu/dists/oneiric/main/i18n/Translation-en  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/alecive/antigone/ubuntu/dists/oneiric/main/source/Sources  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/alecive/antigone/ubuntu/dists/oneiric/main/binary-amd64/Packages  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric/universe/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-amd64/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-amd64/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-amd64/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/binary-amd64/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-amd64/Packages  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en_US  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://repository.spotify.com/dists/stable/non-free/i18n/Translation-en_US  Something wicked happened resolving 'repository.spotify.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://repository.spotify.com/dists/stable/non-free/i18n/Translation-en  Something wicked happened resolving 'repository.spotify.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://linux.dropbox.com/ubuntu/dists/oneiric/main/i18n/Translation-en_US  Something wicked happened resolving 'linux.dropbox.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://linux.dropbox.com/ubuntu/dists/oneiric/main/i18n/Translation-en  Something wicked happened resolving 'linux.dropbox.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://www.ksplice.com/apt/dists/oneiric/ksplice/source/Sources  Something wicked happened resolving 'www.ksplice.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://www.mendeley.com/repositories/ubuntu/stable/Packages  Something wicked happened resolving 'www.mendeley.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://download.toggl.com/toggldesktop/deb/dists/stable/main/binary-amd64/Packages  Something wicked happened resolving 'download.toggl.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://streaming.stat.iastate.edu/CRAN/bin/linux/ubuntu/oneiric/Packages  Something wicked happened resolving 'streaming.stat.iastate.edu:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric/universe/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric/universe/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/binary-amd64/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/binary-amd64/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/oneiric/partner/source/Sources  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/alecive/antigone/ubuntu/dists/oneiric/main/i18n/Translation-en_US  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/alecive/antigone/ubuntu/dists/oneiric/main/i18n/Translation-en  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/dists/oneiric/main/source/Sources  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/dists/oneiric/main/binary-amd64/Packages  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/dists/oneiric/main/i18n/Translation-en_US  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/dists/oneiric/main/i18n/Translation-en  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/p12/ppa/ubuntu/dists/oneiric/main/source/Sources  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/p12/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/p12/ppa/ubuntu/dists/oneiric/main/i18n/Translation-en_US  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/p12/ppa/ubuntu/dists/oneiric/main/i18n/Translation-en  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/oneiric/main/source/Sources  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/oneiric/main/binary-amd64/Packages  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/oneiric/main/i18n/Translation-en_US  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/oneiric/main/i18n/Translation-en  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://www.ksplice.com/apt/dists/oneiric/ksplice/binary-amd64/Packages  Something wicked happened resolving 'www.ksplice.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://www.ksplice.com/apt/dists/oneiric/ksplice/i18n/Translation-en_US  Something wicked happened resolving 'www.ksplice.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://www.ksplice.com/apt/dists/oneiric/ksplice/i18n/Translation-en  Something wicked happened resolving 'www.ksplice.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://download.toggl.com/toggldesktop/deb/dists/stable/main/i18n/Translation-en_US  Something wicked happened resolving 'download.toggl.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://download.toggl.com/toggldesktop/deb/dists/stable/main/i18n/Translation-en  Something wicked happened resolving 'download.toggl.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-amd64/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/binary-amd64/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/oneiric/partner/binary-amd64/Packages  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/oneiric/partner/i18n/Translation-en_US  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/oneiric/partner/i18n/Translation-en  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/oneiric/main/source/Sources  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/oneiric/main/binary-amd64/Packages  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/oneiric/main/i18n/Translation-en_US  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/oneiric/main/i18n/Translation-en  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-amd64/Packages  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en_US  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/binary-amd64/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/binary-amd64/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/binary-amd64/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/binary-amd64/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/main/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/restricted/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://dl.google.com/linux/talkplugin/deb/dists/stable/main/binary-amd64/Packages  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://dl.google.com/linux/talkplugin/deb/dists/stable/main/i18n/Translation-en_US  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://dl.google.com/linux/talkplugin/deb/dists/stable/main/i18n/Translation-en  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/universe/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/source/Sources  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/main/binary-amd64/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/restricted/binary-amd64/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/universe/binary-amd64/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/binary-amd64/Packages  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/main/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/main/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/restricted/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/restricted/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/universe/i18n/Translation-en_US  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-security/universe/i18n/Translation-en  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.
```Next, I change my /etc/resolv.conf file from this:

```
# Generated by NetworkManager

```to this:

```
# Generated by NetworkManager
nameserver 208.67.222.222
nameserver 208.67.220.220

```and then run apt-get update again:

```
sh: cannot create /dev/null: Permission denied
Ign http://download.toggl.com stable InRelease
Ign http://streaming.stat.iastate.edu oneiric/ InRelease                               
4% [Connecting to us.archive.ubuntu.com (91.189.92.184)] [Connecting to archive.canonicFATAL -> Could not set non-blocking flag Bad file descriptor
E: Method http has died unexpectedly!                                                  
E: Sub-process http returned an error code (100)

```Any ideas?

---

