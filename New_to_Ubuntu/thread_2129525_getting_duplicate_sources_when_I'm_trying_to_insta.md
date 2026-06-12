---
title: "getting duplicate sources when I'm trying to install virtual machine."
date: 2013-03-26
forum: New to Ubuntu
---

### Post by Keshav2050 on 2013-03-26
I'm actually getting a warning when I run sudo apt-get update as:

W: Duplicate sources.list entry [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) precise/contrib i386 Packages (/var/lib/apt/lists/download.virtualbox.org_virtualbox_debian_dists_precise_contrib_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

I was actually trying to install virtual machine as in [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

Can anyone please help me.

---

### Post by ibjsb4 on 2013-03-26
Just have to remove one from your sources list.  In terminal enter:

gksudo gedit /etc/apt/sources.list

If your unsure, please post your sources list.

---

### Post by Keshav2050 on 2013-03-26
Oh, thank you very much.
```

# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release i386 (20130213)]/ precise main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
# deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib
```

---

### Post by ibjsb4 on 2013-03-26
In terminal:

```
sudo rm -r /var/lib/apt/lists/*
sudo mkdir /var/lib/apt/lists/partial
sudo apt-get update
```

---

### Post by Keshav2050 on 2013-03-26
I got the output for the first command as:

rm: cannot remove `/var/lib/apt/lists/partial': Is a directory

---

### Post by ibjsb4 on 2013-03-26
Sorry, my mistake.  I have edited my last post.  Please try again.

---

### Post by Keshav2050 on 2013-03-27
Thank you, but I'm still getting the same :

Reading package lists... Done
W: Duplicate sources.list entry [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) precise/contrib i386 Packages (/var/lib/apt/lists/download.virtualbox.org_virtualbox_debian_dists_precise_contrib_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

---

### Post by ibjsb4 on 2013-03-28
Would of thought that was the fix.  Please post the following.

```
ls /var/lib/apt/lists
ls /etc/apt/sources.list.d
```

Thank you

---

### Post by Keshav2050 on 2013-03-30
I'm sorry, I didn't check the forum,
the output for the first line '[COLOR=#000000][FONT=Ubuntu Mono]ls /var/lib/apt/lists[/FONT][/COLOR]' is :


```
dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages
dl.google.com_linux_chrome_deb_dists_stable_Release
dl.google.com_linux_chrome_deb_dists_stable_Release.gpg
download.virtualbox.org_virtualbox_debian_dists_precise_contrib_binary-i386_Packages
download.virtualbox.org_virtualbox_debian_dists_precise_non-free_binary-i386_Packages
download.virtualbox.org_virtualbox_debian_dists_precise_Release
download.virtualbox.org_virtualbox_debian_dists_precise_Release.gpg
extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages
extras.ubuntu.com_ubuntu_dists_precise_main_source_Sources
extras.ubuntu.com_ubuntu_dists_precise_Release
extras.ubuntu.com_ubuntu_dists_precise_Release.gpg
in.archive.ubuntu.com_ubuntu_dists_precise-backports_main_binary-i386_Packages
in.archive.ubuntu.com_ubuntu_dists_precise-backports_main_i18n_Index
in.archive.ubuntu.com_ubuntu_dists_precise-backports_main_i18n_Translation-en
in.archive.ubuntu.com_ubuntu_dists_precise-backports_main_source_Sources
in.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_binary-i386_Packages
in.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_i18n_Index
in.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_i18n_Translation-en
in.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_source_Sources
in.archive.ubuntu.com_ubuntu_dists_precise-backports_Release
in.archive.ubuntu.com_ubuntu_dists_precise-backports_Release.gpg
in.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_binary-i386_Packages
in.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_i18n_Index
in.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_i18n_Translation-en
in.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_source_Sources
in.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_binary-i386_Packages
in.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_i18n_Index
in.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_i18n_Translation-en
in.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_source_Sources
in.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages
in.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Index
in.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en
in.archive.ubuntu.com_ubuntu_dists_precise_main_source_Sources
in.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-i386_Packages
in.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Index
in.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Translation-en
in.archive.ubuntu.com_ubuntu_dists_precise_multiverse_source_Sources
in.archive.ubuntu.com_ubuntu_dists_precise_Release
in.archive.ubuntu.com_ubuntu_dists_precise_Release.gpg
in.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-i386_Packages
in.archive.ubuntu.com_ubuntu_dists_precise_restricted_i18n_Index
in.archive.ubuntu.com_ubuntu_dists_precise_restricted_i18n_Translation-en
in.archive.ubuntu.com_ubuntu_dists_precise_restricted_source_Sources
in.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages
in.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Index
in.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Translation-en
in.archive.ubuntu.com_ubuntu_dists_precise_universe_source_Sources
in.archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-i386_Packages
in.archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Index
in.archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Translation-en
in.archive.ubuntu.com_ubuntu_dists_precise-updates_main_source_Sources
in.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_binary-i386_Packages
in.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_i18n_Index
in.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_i18n_Translation-en
in.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_source_Sources
in.archive.ubuntu.com_ubuntu_dists_precise-updates_Release
in.archive.ubuntu.com_ubuntu_dists_precise-updates_Release.gpg
in.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-i386_Packages
in.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_i18n_Index
in.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_i18n_Translation-en
in.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_source_Sources
in.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-i386_Packages
in.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_i18n_Index
in.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_i18n_Translation-en
in.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_source_Sources
lock
packages.medibuntu.org_dists_precise_free_binary-i386_Packages
packages.medibuntu.org_dists_precise_non-free_binary-i386_Packages
packages.medibuntu.org_dists_precise_Release
packages.medibuntu.org_dists_precise_Release.gpg
partial
ppa.launchpad.net_apt-fast_stable_ubuntu_dists_precise_main_binary-i386_Packages
ppa.launchpad.net_apt-fast_stable_ubuntu_dists_precise_main_source_Sources
ppa.launchpad.net_apt-fast_stable_ubuntu_dists_precise_Release
ppa.launchpad.net_apt-fast_stable_ubuntu_dists_precise_Release.gpg
ppa.launchpad.net_atareao_atareao_ubuntu_dists_precise_main_binary-i386_Packages
ppa.launchpad.net_atareao_atareao_ubuntu_dists_precise_main_source_Sources
ppa.launchpad.net_atareao_atareao_ubuntu_dists_precise_Release
ppa.launchpad.net_atareao_atareao_ubuntu_dists_precise_Release.gpg
ppa.launchpad.net_deluge-team_ppa_ubuntu_dists_precise_main_binary-i386_Packages
ppa.launchpad.net_deluge-team_ppa_ubuntu_dists_precise_main_source_Sources
ppa.launchpad.net_deluge-team_ppa_ubuntu_dists_precise_Release
ppa.launchpad.net_deluge-team_ppa_ubuntu_dists_precise_Release.gpg
ppa.launchpad.net_fossfreedom_rhythmbox-plugins_ubuntu_dists_precise_main_binary-i386_Packages
ppa.launchpad.net_fossfreedom_rhythmbox-plugins_ubuntu_dists_precise_main_source_Sources
ppa.launchpad.net_fossfreedom_rhythmbox-plugins_ubuntu_dists_precise_Release
ppa.launchpad.net_fossfreedom_rhythmbox-plugins_ubuntu_dists_precise_Release.gpg
ppa.launchpad.net_indicator-multiload_stable-daily_ubuntu_dists_precise_main_binary-i386_Packages
ppa.launchpad.net_indicator-multiload_stable-daily_ubuntu_dists_precise_main_source_Sources
ppa.launchpad.net_indicator-multiload_stable-daily_ubuntu_dists_precise_Release
ppa.launchpad.net_indicator-multiload_stable-daily_ubuntu_dists_precise_Release.gpg
ppa.launchpad.net_jonoomph_openshot-edge_ubuntu_dists_precise_main_binary-i386_Packages
ppa.launchpad.net_jonoomph_openshot-edge_ubuntu_dists_precise_main_source_Sources
ppa.launchpad.net_jonoomph_openshot-edge_ubuntu_dists_precise_Release
ppa.launchpad.net_jonoomph_openshot-edge_ubuntu_dists_precise_Release.gpg
ppa.launchpad.net_scopes-packagers_ppa_ubuntu_dists_precise_main_binary-i386_Packages
ppa.launchpad.net_scopes-packagers_ppa_ubuntu_dists_precise_main_source_Sources
ppa.launchpad.net_scopes-packagers_ppa_ubuntu_dists_precise_Release
ppa.launchpad.net_scopes-packagers_ppa_ubuntu_dists_precise_Release.gpg
ppa.launchpad.net_team-xbmc_ppa_ubuntu_dists_precise_main_binary-i386_Packages
ppa.launchpad.net_team-xbmc_ppa_ubuntu_dists_precise_main_source_Sources
ppa.launchpad.net_team-xbmc_ppa_ubuntu_dists_precise_Release
ppa.launchpad.net_team-xbmc_ppa_ubuntu_dists_precise_Release.gpg
ppa.launchpad.net_webupd8team_y-ppa-manager_ubuntu_dists_precise_main_binary-i386_Packages
ppa.launchpad.net_webupd8team_y-ppa-manager_ubuntu_dists_precise_main_source_Sources
ppa.launchpad.net_webupd8team_y-ppa-manager_ubuntu_dists_precise_Release
ppa.launchpad.net_webupd8team_y-ppa-manager_ubuntu_dists_precise_Release.gpg
security.ubuntu.com_ubuntu_dists_precise-security_main_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Index
security.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Translation-en
security.ubuntu.com_ubuntu_dists_precise-security_main_source_Sources
security.ubuntu.com_ubuntu_dists_precise-security_multiverse_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_precise-security_multiverse_i18n_Index
security.ubuntu.com_ubuntu_dists_precise-security_multiverse_i18n_Translation-en
security.ubuntu.com_ubuntu_dists_precise-security_multiverse_source_Sources
security.ubuntu.com_ubuntu_dists_precise-security_Release
security.ubuntu.com_ubuntu_dists_precise-security_Release.gpg
security.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Index
security.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Translation-en
security.ubuntu.com_ubuntu_dists_precise-security_restricted_source_Sources
security.ubuntu.com_ubuntu_dists_precise-security_universe_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Index
security.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-en
security.ubuntu.com_ubuntu_dists_precise-security_universe_source_Sources

```

and the output for the second line '[COLOR=#000000][FONT=Ubuntu Mono]ls /etc/apt/sources.list.d[/FONT][/COLOR]' is :

```
apt-fast-stable-precise.list
apt-fast-stable-precise.list.save
atareao-atareao-precise.list
atareao-atareao-precise.list.save
deluge-team-ppa-precise.list
deluge-team-ppa-precise.list.save
fossfreedom-rhythmbox-plugins-precise.list
fossfreedom-rhythmbox-plugins-precise.list.save
google-chrome.list
google-chrome.list.save
indicator-multiload-stable-daily-precise.list
indicator-multiload-stable-daily-precise.list.save
jonoomph-openshot-edge-precise.list
jonoomph-openshot-edge-precise.list.save
medibuntu.list
medibuntu.list.save
scopes-packagers-ppa-precise.list
scopes-packagers-ppa-precise.list.save
team-xbmc-ppa-precise.list
team-xbmc-ppa-precise.list.save
virtualbox.list
virtualbox.list.save
webupd8team-y-ppa-manager-precise.list



```

thank you for replying.

---

### Post by ibjsb4 on 2013-03-30
[COLOR=#ff0000]My /var/lib/apt/lists[/COLOR]
download.virtualbox.org_virtualbox_debian_dists_precise_contrib_binary-i386_Packages
download.virtualbox.org_virtualbox_debian_dists_precise_InRelease

[COLOR=#ff0000]Yours[/COLOR]
download.virtualbox.org_virtualbox_debian_dists_precise_contrib_binary-i386_Packages
download.virtualbox.org_virtualbox_debian_dists_precise_non-free_binary-i386_Packages
download.virtualbox.org_virtualbox_debian_dists_precise_Release
download.virtualbox.org_virtualbox_debian_dists_precise_Release.gpg
--------------------------
[COLOR=#ff0000]My /etc/apt/sources.list.d[/COLOR]
Nothing

[COLOR=#ff0000]Yours[/COLOR]
virtualbox.list
virtualbox.list.save
--------------------------
[COLOR=#ff0000]My /etc/apt/sources.list[/COLOR]
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib

[COLOR=#ff0000]Yours[/COLOR]
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib

As you can see, we both run precise.  Yet only our "sources.list" are the same.

How did you download vBox and what version are you running?  Do you have guest currently running?

Sorry for more questions than answers, but at the moment I am confused and thinking you need to remove vBox and reinstall.

---

### Post by Keshav2050 on 2013-03-31
Actually I wasn't able to use virtual box, I tried to install it 2 to 3 times but it didn't work, I tried to follow the instructions as in [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

thanks for replying.

---

### Post by ibjsb4 on 2013-04-01
Ok, back with you :)

I need you to remove the virtualbox entries from /var/lib/apt/lists and 
/etc/apt/sources.list.d

Leave the one in /etc/apt/sources.list

You can remove those entries by using nautilus as root and navigating to the proper folder.  The command for nautilus root is:

```
gksudo nautilus
```

Then ..

```
sudo apt-get purge virtualbox && sudo apt-get update
```

I hope it updated this time, let me know :)

---

### Post by Keshav2050 on 2013-04-01
Oh, thank you. It worked perfectly. Can I please know how to install virtualbox. I already tried a few times on my own and failed.

---

### Post by ibjsb4 on 2013-04-01
Yep :)  

```
sudo apt-get install dkms build-essential
```

Then if you have a vBox start icon, let me know.  If you do not have a start icon ..

```
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install virtualbox
```

Let me know if that worked.

---

### Post by Keshav2050 on 2013-04-01
I got Oracle VM VirtualBox icon when I searched in dash.

---

### Post by ibjsb4 on 2013-04-01
And you can pull up vBox?  If not, follow post #14.

---

### Post by Keshav2050 on 2013-04-02
Can we use virtual box even after upgrading ubuntu? And can you please tell me how to add guest OS in the virtual box.

---

### Post by ibjsb4 on 2013-04-02
You can create a guest by clicking on "New" when you open vBox.  No need to burn a CD/DVD, just download the iso to the host.

You also need to install the **Extension Pack **to your host.

[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

[URL="https://www.virtualbox.org/manual/ch01.html#intro-installing"]https://www.virtualbox.org/manual/ch01.html#intro-installing


[ATTACH=CONFIG]240891[/ATTACH]
[/URL]

---

### Post by Keshav2050 on 2013-04-02
Thank you I've downloaded all supported platforms file for 4.2.10 from [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads) can you please tell me how to mount it. I've already installed the extension pack.

---

### Post by ibjsb4 on 2013-04-02
Like I said, click the vBox icon and on the first and screen select "New".  The will start the process of creating a guest.  After that is created, it will show up on the left side of the vBox screen.  You can then mount it by clicking on the "Start" icon.

You can then install the guest system by either using CD/DVD or iso file from the host.

---

