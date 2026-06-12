---
title: "What does the red stop sign like icon at the top mean...?"
date: 2019-01-06
forum: New to Ubuntu
---

### Post by jaabdullah on 2019-01-06
Hi, 

I woke up yesterday morning and found this little red icon on my laptop and I have no idea what it means, There is an error message and I need help solving this problems.

Please help! I am new to Ubuntu and I have no idea what this means and if it is something very very serious. 

Here is the error message:

```
sudo apt-get update
[sudo] password for juwariyah: 
Hit:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
Ign:2 [http://dell.archive.canonical.com/updates](http://dell.archive.canonical.com/updates) xenial-dell-service InRelease
Hit:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease                        
Hit:4 [http://ppa.launchpad.net/inameiname/stable/ubuntu](http://ppa.launchpad.net/inameiname/stable/ubuntu) xenial InRelease       
Ign:5 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Hit:6 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Ign:7 [http://dell.archive.canonical.com/updates](http://dell.archive.canonical.com/updates) xenial-dell InRelease          
Hit:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease                
Get:9 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release [943 B]             
Hit:10 [http://dell.archive.canonical.com/updates](http://dell.archive.canonical.com/updates) xenial-dell-service Release   
Get:12 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release.gpg [819 B]        
Hit:13 [http://dell.archive.canonical.com/updates](http://dell.archive.canonical.com/updates) xenial-dell Release           
Get:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports InRelease [107 kB]
Err:14 [http://dell.archive.canonical.com/updates](http://dell.archive.canonical.com/updates) xenial-dell-service Release.gpg
  The following signatures were invalid: BADSIG F9FDA6BED73CDC22 Canonical Archive Automatic Signing Key <ftpmaster@canonical.com>
Err:15 [http://dell.archive.canonical.com/updates](http://dell.archive.canonical.com/updates) xenial-dell Release.gpg
  The following signatures were invalid: BADSIG F9FDA6BED73CDC22 Canonical Archive Automatic Signing Key <ftpmaster@canonical.com>
Get:16 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/main amd64 Packages [7,280 B]
Get:17 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/main i386 Packages [7,288 B]
Get:18 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/main Translation-en [4,456 B]
Get:19 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/main amd64 DEP-11 Metadata [3,324 B]
Get:20 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/main DEP-11 64x64 Icons [29 B]
Hit:21 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/restricted amd64 DEP-11 Metadata
Err:21 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/restricted amd64 DEP-11 Metadata
  Hash Sum mismatch
Get:22 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 Packages [7,804 B]
Get:23 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/universe i386 Packages [7,488 B]
Get:24 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/universe Translation-en [4,184 B]
Get:25 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 DEP-11 Metadata [5,104 B]
Get:26 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/universe DEP-11 64x64 Icons [1,789 B]
Hit:27 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/multiverse amd64 DEP-11 Metadata
Hit:28 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/multiverse DEP-11 64x64 Icons
Fetched 155 kB in 2s (61.2 kB/s)


(appstreamcli:6145): GLib-GIO-CRITICAL **: g_converter_input_stream_new: assertion 'G_IS_INPUT_STREAM (base_stream)' failed


(appstreamcli:6145): GLib-GIO-CRITICAL **: g_output_stream_splice: assertion 'G_IS_INPUT_STREAM (source)' failed


** (appstreamcli:6145): WARNING **: No origin found for file archive.ubuntu.com_ubuntu_dists_xenial-backports_main_dep11_Components-amd64.yml.gz


** (appstreamcli:6145): WARNING **: No origin found for file archive.ubuntu.com_ubuntu_dists_xenial-backports_restricted_dep11_Components-amd64.yml.gz


(appstreamcli:6145): GLib-GIO-CRITICAL **: g_converter_input_stream_new: assertion 'G_IS_INPUT_STREAM (base_stream)' failed


(appstreamcli:6145): GLib-GIO-CRITICAL **: g_output_stream_splice: assertion 'G_IS_INPUT_STREAM (source)' failed


** (appstreamcli:6145): WARNING **: No origin found for file archive.ubuntu.com_ubuntu_dists_xenial-backports_universe_dep11_Components-amd64.yml.gz


** (appstreamcli:6145): WARNING **: No origin found for file archive.ubuntu.com_ubuntu_dists_xenial-backports_multiverse_dep11_Components-amd64.yml.gz
AppStream cache update completed, but some metadata was ignored due to errors.
Reading package lists... Error!
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list.d/xenial-partner.list:4
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://dell.archive.canonical.com/updates](http://dell.archive.canonical.com/updates) xenial-dell-service Release: The following signatures were invalid: BADSIG F9FDA6BED73CDC22 Canonical Archive Automatic Signing Key <ftpmaster@canonical.com>
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://dell.archive.canonical.com/updates](http://dell.archive.canonical.com/updates) xenial-dell Release: The following signatures were invalid: BADSIG F9FDA6BED73CDC22 Canonical Archive Automatic Signing Key <ftpmaster@canonical.com>
W: Failed to fetch [http://dell.archive.canonical.com/updates/dists/xenial-dell-service/Release.gpg](http://dell.archive.canonical.com/updates/dists/xenial-dell-service/Release.gpg)  The following signatures were invalid: BADSIG F9FDA6BED73CDC22 Canonical Archive Automatic Signing Key <ftpmaster@canonical.com>
W: Failed to fetch [http://dell.archive.canonical.com/updates/dists/xenial-dell/Release.gpg](http://dell.archive.canonical.com/updates/dists/xenial-dell/Release.gpg)  The following signatures were invalid: BADSIG F9FDA6BED73CDC22 Canonical Archive Automatic Signing Key <ftpmaster@canonical.com>
E: Failed to fetch store:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_xenial-backports_restricted_dep11_Components-amd64.yml.gz  Hash Sum mismatch
W: Some index files failed to download. They have been ignored, or old ones used instead.
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list.d/xenial-partner.list:4
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial-backports_main_binary-all_Packages
E: The package lists or status file could not be parsed or opened.
```

---

### Post by ajgreeny on 2019-01-06
It looks as if you have a problem with your /etc/apt/sources.list file which is used for the update process so please show us the output of command ```
cat /etc/apt/sources.list
```

Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by oldos2er on 2019-01-06
For BADSIG errors try the solution here: [https://ubuntuforums.org/showthread.php?t=1366214](https://ubuntuforums.org/showthread.php?t=1366214)

---

