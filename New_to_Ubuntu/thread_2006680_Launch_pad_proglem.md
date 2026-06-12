---
title: "Launch pad proglem"
date: 2012-06-19
forum: New to Ubuntu
---

### Post by Baul on 2012-06-19
I want to send this to Ubuntu Bug reporting system "Launchpad - I think" but not really sure hoe to do it (I know nwbie) - I have tried to submit

I have been having this problem with update - I waould be very obliged if some one could help me - thanks in advance B


Problem below:


An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by NikTh on 2012-06-19
I don't think that is a bug of update-manager. Maybe something from your sources.list is corrupted. 
Open a terminal (ctrl+alt+t) and paste this command inside
```
find /etc/apt/ -iname "*.list" -exec echo "FILE: {}" \; -exec cat "{}" \;
```[B]Copy the entire out put and paste between ```
 brackets by clicking on # at the top of the message pane.

[/B]Also give these commands in terminal and see if problem fixed , 
copy-paste them from here to your terminal _one - at- time _(**do not write by hand**) for better accuracy[B].
[/B][code]sudo rm -rf /var/lib/apt/lists/*
sudo apt-get install -f
sudo dpkg --configure -a 
sudo apt-get update 
```copy the entire out put _of_ _last command_[B] between [CODE] brackets by clicking on # at the top of the message pane.
[/B]

---

