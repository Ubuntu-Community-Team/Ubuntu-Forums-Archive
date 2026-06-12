---
title: "duplicate sources"
date: 2012-06-26
forum: New to Ubuntu
---

### Post by cmcanulty on 2012-06-26
I keet getting the duplicate sources error and had checked my etc/apt/sources.list and etc/apt/sources.list.d  and found no duplicates. Then I noticed it was referring to var/lib/apt/lists I still see no duplicates there. Some are for difeerent versions ie-64 bit, i386, and .gpg. Can someone help and tell me what I can safely deklete from /etc/lib/apt/lists? Below I am pasting the errors from updateing and the the contents of my var/lib/apt/lists

first the errors
```

W: Duplicate sources.list entry http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_gnome3-team_gnome3_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ precise/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_gnome3-team_gnome3_ubuntu_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/transmissionbt/ppa/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_transmissionbt_ppa_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/transmissionbt/ppa/ubuntu/ precise/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_transmissionbt_ppa_ubuntu_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ precise/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ precise/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_precise_main_binary-i386_Packages)

```


and now my var/lib/apt/lists


```

/var/lib/apt/lists/partial
/var/lib/apt/lists/apt.spideroak.com_ubuntu-spideroak-hardy_dists_release_Release
/var/lib/apt/lists/apt.spideroak.com_ubuntu-spideroak-hardy_dists_release_Release.gpg
/var/lib/apt/lists/apt.spideroak.com_ubuntu-spideroak-hardy_dists_release_restricted_binary-amd64_Packages
/var/lib/apt/lists/apt.spideroak.com_ubuntu-spideroak-hardy_dists_release_restricted_binary-i386_Packages
/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages
/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages
/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_source_Sources
/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_Release
/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_Release.gpg
/var/lib/apt/lists/deb.opera.com_opera_dists_lenny_non-free_binary-amd64_Packages
/var/lib/apt/lists/deb.opera.com_opera_dists_lenny_non-free_binary-i386_Packages
/var/lib/apt/lists/deb.opera.com_opera_dists_lenny_Release
/var/lib/apt/lists/deb.opera.com_opera_dists_lenny_Release.gpg
/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages
/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages
/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_Release
/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_Release.gpg
/var/lib/apt/lists/download.virtualbox.org_virtualbox_debian_dists_precise_contrib_binary-amd64_Packages
/var/lib/apt/lists/download.virtualbox.org_virtualbox_debian_dists_precise_contrib_binary-i386_Packages
/var/lib/apt/lists/download.virtualbox.org_virtualbox_debian_dists_precise_InRelease
/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages
/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages
/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_source_Sources
/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_Release
/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_Release.gpg
/var/lib/apt/lists/lock
/var/lib/apt/lists/ppa.launchpad.net_bimsebasse_cinnamonextras_ubuntu_dists_precise_main_binary-amd64_Packages
/var/lib/apt/lists/ppa.launchpad.net_bimsebasse_cinnamonextras_ubuntu_dists_precise_main_binary-i386_Packages
/var/lib/apt/lists/ppa.launchpad.net_bimsebasse_cinnamonextras_ubuntu_dists_precise_main_source_Sources
/var/lib/apt/lists/ppa.launchpad.net_bimsebasse_cinnamonextras_ubuntu_dists_precise_Release
/var/lib/apt/lists/ppa.launchpad.net_bimsebasse_cinnamonextras_ubuntu_dists_precise_Release.gpg
/var/lib/apt/lists/ppa.launchpad.net_chromium-daily_stable_ubuntu_dists_precise_main_binary-amd64_Packages
/var/lib/apt/lists/ppa.launchpad.net_chromium-daily_stable_ubuntu_dists_precise_main_binary-i386_Packages
/var/lib/apt/lists/ppa.launchpad.net_chromium-daily_stable_ubuntu_dists_precise_Release
/var/lib/apt/lists/ppa.launchpad.net_chromium-daily_stable_ubuntu_dists_precise_Release.gpg
/var/lib/apt/lists/ppa.launchpad.net_danielrichter2007_grub-customizer_ubuntu_dists_precise_main_binary-amd64_Packages
/var/lib/apt/lists/ppa.launchpad.net_danielrichter2007_grub-customizer_ubuntu_dists_precise_main_binary-i386_Packages
/var/lib/apt/lists/ppa.launchpad.net_danielrichter2007_grub-customizer_ubuntu_dists_precise_main_source_Sources
/var/lib/apt/lists/ppa.launchpad.net_danielrichter2007_grub-customizer_ubuntu_dists_precise_Release
/var/lib/apt/lists/ppa.launchpad.net_danielrichter2007_grub-customizer_ubuntu_dists_precise_Release.gpg
/var/lib/apt/lists/ppa.launchpad.net_diesch_testing_ubuntu_dists_precise_main_binary-amd64_Packages
/var/lib/apt/lists/ppa.launchpad.net_diesch_testing_ubuntu_dists_precise_main_binary-i386_Packages
/var/lib/apt/lists/ppa.launchpad.net_diesch_testing_ubuntu_dists_precise_main_source_Sources
/var/lib/apt/lists/ppa.launchpad.net_diesch_testing_ubuntu_dists_precise_Release
/var/lib/apt/lists/ppa.launchpad.net_diesch_testing_ubuntu_dists_precise_Release.gpg
/var/lib/apt/lists/ppa.launchpad.net_eugenesan_java_ubuntu_dists_precise_main_binary-amd64_Packages
/var/lib/apt/lists/ppa.launchpad.net_eugenesan_java_ubuntu_dists_precise_main_binary-i386_Packages
/var/lib/apt/lists/ppa.launchpad.net_eugenesan_java_ubuntu_dists_precise_main_source_Sources
/var/lib/apt/lists/ppa.launchpad.net_eugenesan_java_ubuntu_dists_precise_Release
/var/lib/apt/lists/ppa.launchpad.net_eugenesan_java_ubuntu_dists_precise_Release.gpg
/var/lib/apt/lists/ppa.launchpad.net_gnome3-team_gnome3_ubuntu_dists_precise_main_binary-amd64_Packages
/var/lib/apt/lists/ppa.launchpad.net_gnome3-team_gnome3_ubuntu_dists_precise_main_binary-i386_Packages
/var/lib/apt/lists/ppa.launchpad.net_gnome3-team_gnome3_ubuntu_dists_precise_main_source_Sources
/var/lib/apt/lists/ppa.launchpad.net_gnome3-team_gnome3_ubuntu_dists_precise_Release
/var/lib/apt/lists/ppa.launchpad.net_gnome3-team_gnome3_ubuntu_dists_precise_Release.gpg
/var/lib/apt/lists/ppa.launchpad.net_gwendal-lebihan-dev_cinnamon-stable_ubuntu_dists_precise_main_binary-amd64_Packages
/var/lib/apt/lists/ppa.launchpad.net_gwendal-lebihan-dev_cinnamon-stable_ubuntu_dists_precise_main_binary-i386_Packages
/var/lib/apt/lists/ppa.launchpad.net_gwendal-lebihan-dev_cinnamon-stable_ubuntu_dists_precise_main_source_Sources
/var/lib/apt/lists/ppa.launchpad.net_gwendal-lebihan-dev_cinnamon-stable_ubuntu_dists_precise_Release
/var/lib/apt/lists/ppa.launchpad.net_gwendal-lebihan-dev_cinnamon-stable_ubuntu_dists_precise_Release.gpg
/var/lib/apt/lists/ppa.launchpad.net_jwigley_window-list_ubuntu_dists_precise_main_binary-amd64_Packages
/var/lib/apt/lists/ppa.launchpad.net_jwigley_window-list_ubuntu_dists_precise_main_binary-i386_Packages
/var/lib/apt/lists/ppa.launchpad.net_jwigley_window-list_ubuntu_dists_precise_main_source_Sources
/var/lib/apt/lists/ppa.launchpad.net_jwigley_window-list_ubuntu_dists_precise_Release
/var/lib/apt/lists/ppa.launchpad.net_jwigley_window-list_ubuntu_dists_precise_Release.gpg
/var/lib/apt/lists/ppa.launchpad.net_krytarik_tuxgarage_ubuntu_dists_precise_main_binary-amd64_Packages
/var/lib/apt/lists/ppa.launchpad.net_krytarik_tuxgarage_ubuntu_dists_precise_main_binary-i386_Packages
/var/lib/apt/lists/ppa.launchpad.net_krytarik_tuxgarage_ubuntu_dists_precise_main_source_Sources
/var/lib/apt/lists/ppa.launchpad.net_krytarik_tuxgarage_ubuntu_dists_precise_Release
/var/lib/apt/lists/ppa.launchpad.net_krytarik_tuxgarage_ubuntu_dists_precise_Release.gpg
/var/lib/apt/lists/ppa.launchpad.net_liferea_ppa_ubuntu_dists_precise_main_binary-amd64_Packages
/var/lib/apt/lists/ppa.launchpad.net_liferea_ppa_ubuntu_dists_precise_main_binary-i386_Packages
/var/lib/apt/lists/ppa.launchpad.net_liferea_ppa_ubuntu_dists_precise_Release
/var/lib/apt/lists/ppa.launchpad.net_liferea_ppa_ubuntu_dists_precise_Release.gpg
/var/lib/apt/lists/ppa.launchpad.net_midori_ppa_ubuntu_dists_precise_main_binary-amd64_Packages
/var/lib/apt/lists/ppa.launchpad.net_midori_ppa_ubuntu_dists_precise_main_binary-i386_Packages
/var/lib/apt/lists/ppa.launchpad.net_midori_ppa_ubuntu_dists_precise_Release
/var/lib/apt/lists/ppa.launchpad.net_midori_ppa_ubuntu_dists_precise_Release.gpg
/var/lib/apt/lists/ppa.launchpad.net_mscore-ubuntu_mscore-stable_ubuntu_dists_precise_main_binary-amd64_Packages
/var/lib/apt/lists/ppa.launchpad.net_mscore-ubuntu_mscore-stable_ubuntu_dists_precise_main_binary-i386_Packages
/var/lib/apt/lists/ppa.launchpad.net_mscore-ubuntu_mscore-stable_ubuntu_dists_precise_main_source_Sources
/var/lib/apt/lists/ppa.launchpad.net_mscore-ubuntu_mscore-stable_ubuntu_dists_precise_Release
/var/lib/apt/lists/ppa.launchpad.net_mscore-ubuntu_mscore-stable_ubuntu_dists_precise_Release.gpg
/var/lib/apt/lists/ppa.launchpad.net_nilarimogard_webupd8_ubuntu_dists_precise_main_binary-amd64_Packages
/var/lib/apt/lists/ppa.launchpad.net_nilarimogard_webupd8_ubuntu_dists_precise_main_binary-i386_Packages
/var/lib/apt/lists/ppa.launchpad.net_nilarimogard_webupd8_ubuntu_dists_precise_Release
/var/lib/apt/lists/ppa.launchpad.net_nilarimogard_webupd8_ubuntu_dists_precise_Release.gpg
/var/lib/apt/lists/ppa.launchpad.net_otto-kesselgulasch_gimp_ubuntu_dists_precise_main_binary-amd64_Packages
/var/lib/apt/lists/ppa.launchpad.net_otto-kesselgulasch_gimp_ubuntu_dists_precise_main_binary-i386_Packages
/var/lib/apt/lists/ppa.launchpad.net_otto-kesselgulasch_gimp_ubuntu_dists_precise_main_source_Sources
/var/lib/apt/lists/ppa.launchpad.net_otto-kesselgulasch_gimp_ubuntu_dists_precise_Release
/var/lib/apt/lists/ppa.launchpad.net_otto-kesselgulasch_gimp_ubuntu_dists_precise_Release.gpg
/var/lib/apt/lists/ppa.launchpad.net_ricotz_testing_ubuntu_dists_precise_main_binary-amd64_Packages
/var/lib/apt/lists/ppa.launchpad.net_ricotz_testing_ubuntu_dists_precise_main_binary-i386_Packages
/var/lib/apt/lists/ppa.launchpad.net_ricotz_testing_ubuntu_dists_precise_main_source_Sources
/var/lib/apt/lists/ppa.launchpad.net_ricotz_testing_ubuntu_dists_precise_Release
/var/lib/apt/lists/ppa.launchpad.net_ricotz_testing_ubuntu_dists_precise_Release.gpg
/var/lib/apt/lists/ppa.launchpad.net_team-xbmc_ppa_ubuntu_dists_precise_main_binary-amd64_Packages
/var/lib/apt/lists/ppa.launchpad.net_team-xbmc_ppa_ubuntu_dists_precise_main_binary-i386_Packages
/var/lib/apt/lists/ppa.launchpad.net_team-xbmc_ppa_ubuntu_dists_precise_main_source_Sources
/var/lib/apt/lists/ppa.launchpad.net_team-xbmc_ppa_ubuntu_dists_precise_Release
/var/lib/apt/lists/ppa.launchpad.net_team-xbmc_ppa_ubuntu_dists_precise_Release.gpg
/var/lib/apt/lists/ppa.launchpad.net_transmissionbt_ppa_ubuntu_dists_precise_main_binary-amd64_Packages
/var/lib/apt/lists/ppa.launchpad.net_transmissionbt_ppa_ubuntu_dists_precise_main_binary-i386_Packages
/var/lib/apt/lists/ppa.launchpad.net_transmissionbt_ppa_ubuntu_dists_precise_Release
/var/lib/apt/lists/ppa.launchpad.net_transmissionbt_ppa_ubuntu_dists_precise_Release.gpg
/var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_precise_main_binary-amd64_Packages
/var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_precise_main_binary-i386_Packages
/var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_precise_main_source_Sources
/var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_precise_Release
/var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_precise_Release.gpg
/var/lib/apt/lists/ppa.launchpad.net_ubuntu-tweak-testing_ppa_ubuntu_dists_precise_main_binary-amd64_Packages
/var/lib/apt/lists/ppa.launchpad.net_ubuntu-tweak-testing_ppa_ubuntu_dists_precise_main_binary-i386_Packages
/var/lib/apt/lists/ppa.launchpad.net_ubuntu-tweak-testing_ppa_ubuntu_dists_precise_main_source_Sources
/var/lib/apt/lists/ppa.launchpad.net_ubuntu-tweak-testing_ppa_ubuntu_dists_precise_Release
/var/lib/apt/lists/ppa.launchpad.net_ubuntu-tweak-testing_ppa_ubuntu_dists_precise_Release.gpg
/var/lib/apt/lists/ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_precise_main_binary-amd64_Packages
/var/lib/apt/lists/ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_precise_main_binary-i386_Packages
/var/lib/apt/lists/ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_precise_Release
/var/lib/apt/lists/ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_precise_Release.gpg
/var/lib/apt/lists/ppa.launchpad.net_webupd8team_java_ubuntu_dists_precise_main_binary-amd64_Packages
/var/lib/apt/lists/ppa.launchpad.net_webupd8team_java_ubuntu_dists_precise_main_binary-i386_Packages
/var/lib/apt/lists/ppa.launchpad.net_webupd8team_java_ubuntu_dists_precise_main_source_Sources
/var/lib/apt/lists/ppa.launchpad.net_webupd8team_java_ubuntu_dists_precise_Release
/var/lib/apt/lists/ppa.launchpad.net_webupd8team_java_ubuntu_dists_precise_Release.gpg
/var/lib/apt/lists/ppa.launchpad.net_webupd8team_themes_ubuntu_dists_precise_main_binary-amd64_Packages
/var/lib/apt/lists/ppa.launchpad.net_webupd8team_themes_ubuntu_dists_precise_main_binary-i386_Packages
/var/lib/apt/lists/ppa.launchpad.net_webupd8team_themes_ubuntu_dists_precise_main_source_Sources
/var/lib/apt/lists/ppa.launchpad.net_webupd8team_themes_ubuntu_dists_precise_Release
/var/lib/apt/lists/ppa.launchpad.net_webupd8team_themes_ubuntu_dists_precise_Release.gpg
/var/lib/apt/lists/ppa.launchpad.net_webupd8team_y-ppa-manager_ubuntu_dists_precise_main_binary-amd64_Packages
/var/lib/apt/lists/ppa.launchpad.net_webupd8team_y-ppa-manager_ubuntu_dists_precise_main_binary-i386_Packages
/var/lib/apt/lists/ppa.launchpad.net_webupd8team_y-ppa-manager_ubuntu_dists_precise_main_source_Sources
/var/lib/apt/lists/ppa.launchpad.net_webupd8team_y-ppa-manager_ubuntu_dists_precise_Release
/var/lib/apt/lists/ppa.launchpad.net_webupd8team_y-ppa-manager_ubuntu_dists_precise_Release.gpg
/var/lib/apt/lists/ppa.launchpad.net_yannubuntu_boot-repair_ubuntu_dists_precise_main_binary-amd64_Packages
/var/lib/apt/lists/ppa.launchpad.net_yannubuntu_boot-repair_ubuntu_dists_precise_main_binary-i386_Packages
/var/lib/apt/lists/ppa.launchpad.net_yannubuntu_boot-repair_ubuntu_dists_precise_Release
/var/lib/apt/lists/ppa.launchpad.net_yannubuntu_boot-repair_ubuntu_dists_precise_Release.gpg
/var/lib/apt/lists/ppa.launchpad.net_yorba_ppa_ubuntu_dists_precise_main_binary-amd64_Packages
/var/lib/apt/lists/ppa.launchpad.net_yorba_ppa_ubuntu_dists_precise_main_binary-i386_Packages
/var/lib/apt/lists/ppa.launchpad.net_yorba_ppa_ubuntu_dists_precise_main_source_Sources
/var/lib/apt/lists/ppa.launchpad.net_yorba_ppa_ubuntu_dists_precise_Release
/var/lib/apt/lists/ppa.launchpad.net_yorba_ppa_ubuntu_dists_precise_Release.gpg
/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_binary-amd64_Packages
/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_binary-i386_Packages
/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Index
/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Translation-en
/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_source_Sources
/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_binary-amd64_Packages
/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_binary-i386_Packages
/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_i18n_Index
/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_i18n_Translation-en
/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_source_Sources
/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_Release
/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_Release.gpg
/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-amd64_Packages
/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-i386_Packages
/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Index
/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Translation-en
/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_source_Sources
/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_binary-amd64_Packages
/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_binary-i386_Packages
/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Index
/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-en
/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_source_Sources
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_main_binary-amd64_Packages
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_main_binary-i386_Packages
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_main_i18n_Index
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_main_i18n_Translation-en
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_main_source_Sources
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_binary-amd64_Packages
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_binary-i386_Packages
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_i18n_Index
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_i18n_Translation-en
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_source_Sources
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_Release
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_Release.gpg
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_binary-amd64_Packages
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_binary-i386_Packages
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_i18n_Index
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_i18n_Translation-en
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_source_Sources
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_binary-amd64_Packages
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_binary-i386_Packages
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_i18n_Index
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_i18n_Translation-en
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_source_Sources
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Index
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_source_Sources
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-amd64_Packages
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-i386_Packages
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Index
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Translation-en
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_source_Sources
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_Release
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_Release.gpg
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-amd64_Packages
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-i386_Packages
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_restricted_i18n_Index
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_restricted_i18n_Translation-en
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_restricted_source_Sources
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-amd64_Packages
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Index
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Translation-en
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_universe_source_Sources
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-amd64_Packages
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-i386_Packages
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Index
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Translation-en
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_main_source_Sources
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_binary-amd64_Packages
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_binary-i386_Packages
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_i18n_Index
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_i18n_Translation-en
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_source_Sources
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_Release
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_Release.gpg
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-amd64_Packages
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-i386_Packages
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_i18n_Index
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_i18n_Translation-en
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_source_Sources
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-amd64_Packages
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-i386_Packages
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_i18n_Index
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_i18n_Translation-en
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_source_Sources
```

---

### Post by ikt on 2012-06-26
Maybe try

```
cd /var/lib/apt/
sudo mv lists listsold
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by cortman on 2012-06-26
Yeah, or just

```
sudo rm -r /var/lib/apt/lists/*
sudo mkdir /var/lib/apt/lists/partial
sudo apt-get update
```

---

### Post by cmcanulty on 2012-06-26
Same errors after all those commands

---

### Post by cortman on 2012-06-26
Ok, please post the full output of

```
cat /etc/apt/sources.list
```

and the full output of

```
ls -l /etc/apt/sources.list.d/
```

Thanks.

---

### Post by NikTh on 2012-06-26
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
``` 
post results of last command *inside code tags* (# on message edit panel)

---

### Post by cmcanulty on 2012-06-26
here are the first commands
```

cmcanulty@Darcy25:~$ cat /etc/apt/sources.list
# deb cdrom:[Lubuntu 12.04 _Precise Pangolin_ - Release amd64 (20120423)]/ dists/precise/main/binary-i386/

# deb cdrom:[Lubuntu 12.04 _Precise Pangolin_ - Release amd64 (20120423)]/ dists/precise/multiverse/binary-i386/
# deb cdrom:[Lubuntu 12.04 _Precise Pangolin_ - Release amd64 (20120423)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Lubuntu 12.04 _Precise Pangolin_ - Release amd64 (20120423)]/ dists/precise/universe/binary-i386/
# deb cdrom:[Lubuntu 12.04 _Precise Pangolin_ - Release amd64 (20120423)]/ precise main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
#Addedby software-properties
deb-src http://us.archive.ubuntu.com/ubuntu/ precise restricted main multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
#Addedby software-properties
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates restricted main multiverse universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
#Addedby software-properties
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu/ precise-security main restricted
#Addedby software-properties
deb-src http://security.ubuntu.com/ubuntu/ precise-security restricted main multiverse universe
deb http://security.ubuntu.com/ubuntu/ precise-security universe
deb http://security.ubuntu.com/ubuntu/ precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu/ precise partner
deb-src http://archive.canonical.com/ubuntu/ precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu/ precise main
deb-src http://extras.ubuntu.com/ubuntu/ precise main

# deb http://download.virtualbox.org/virtualbox/debian/ precise contrib


cmcanulty@Darcy25:~$ ls -l /etc/apt/sources.list.d/
total 248
-rw-r--r-- 1 root root 157 Jun 25 07:27 bimsebasse-cinnamonextras-precise.list
-rw-r--r-- 1 root root 154 Jun 19 08:43 bimsebasse-cinnamonextras-precise.list.save
-rw-r--r-- 1 root root 110 Jun 25 07:27 chromium-daily-stable-precise.list
-rw-r--r-- 1 root root 109 Jun 19 08:43 chromium-daily-stable-precise.list.save
-rw-r--r-- 1 root root 173 Jun 25 07:27 danielrichter2007-grub-customizer-precise.list
-rw-r--r-- 1 root root 170 Jun 19 08:43 danielrichter2007-grub-customizer-precise.list.save
-rw-r--r-- 1 root root 135 Jun 25 07:27 diesch-testing-precise.list
-rw-r--r-- 1 root root 132 Jun 19 08:43 diesch-testing-precise.list.save
-rw-r--r-- 1 root root 135 Jun 25 07:27 eugenesan-java-precise.list
-rw-r--r-- 1 root root 132 Jun 19 08:43 eugenesan-java-precise.list.save
-rw-r--r-- 1 root root 224 Jun 25 07:27 gnome3-team-gnome3-precise.list
-rw-r--r-- 1 root root 140 Jun 19 08:43 gnome3-team-gnome3-precise.list.save
-rw-r--r-- 1 root root 181 Jun 25 07:27 google-chrome.list
-rw-r--r-- 1 root root 176 Jun 19 08:43 google-chrome.list.save
-rw-r--r-- 1 root root 177 Jun 25 07:27 gwendal-lebihan-dev-cinnamon-stable-precise.list
-rw-r--r-- 1 root root 174 Jun 19 08:43 gwendal-lebihan-dev-cinnamon-stable-precise.list.save
-rw-r--r-- 1 root root 145 Jun 25 07:27 jwigley-window-list-precise.list
-rw-r--r-- 1 root root 142 Jun 19 08:43 jwigley-window-list-precise.list.save
-rw-r--r-- 1 root root 143 Jun 25 07:27 krytarik-tuxgarage-precise.list
-rw-r--r-- 1 root root 140 Jun 19 08:43 krytarik-tuxgarage-precise.list.save
-rw-r--r-- 1 root root 169 Jun 25 07:27 libreoffice-ppa-precise.list
-rw-r--r-- 1 root root  82 Jun 19 08:43 libreoffice-ppa-precise.list.save
-rw-r--r-- 1 root root  81 Jun 25 07:27 liferea-ppa-precise.list
-rw-r--r-- 1 root root  73 Jun 25 07:27 midori-ppa-precise.list
-rw-r--r-- 1 root root  72 Jun 19 08:43 midori-ppa-precise.list.save
-rw-r--r-- 1 root root 161 Jun 25 07:27 mscore-ubuntu-mscore-stable-precise.list
-rw-r--r-- 1 root root 158 Jun 19 08:43 mscore-ubuntu-mscore-stable-precise.list.save
-rw-r--r-- 1 root root  81 Jun 25 07:27 nilarimogard-webupd8-precise.list
-rw-r--r-- 1 root root  79 Jun 19 08:43 nilarimogard-webupd8-precise.list.save
-rw-r--r-- 1 root root  70 Jun 25 07:27 opera.list
-rw-r--r-- 1 root root  70 Jun 19 08:43 opera.list.save
-rw-r--r-- 1 root root 153 Jun 25 07:27 otto-kesselgulasch-gimp-precise.list
-rw-r--r-- 1 root root 150 Jun 19 08:43 otto-kesselgulasch-gimp-precise.list.save
-rw-r--r-- 1 root root  82 Jun 25 07:27 repo-for-scribus.list
-rw-r--r-- 1 root root  82 Jun 19 08:43 repo-for-scribus.list.save
-rw-r--r-- 1 root root 135 Jun 25 07:27 ricotz-testing-precise.list
-rw-r--r-- 1 root root 132 Jun 19 08:43 ricotz-testing-precise.list.save
-rw-r--r-- 1 root root  75 Jun 25 07:27 skype.list
-rw-r--r-- 1 root root  74 Jun 25 07:27 spideroak.com.sources.list
-rw-r--r-- 1 root root  73 Jun 19 08:43 spideroak.com.sources.list.save
-rw-r--r-- 1 root root 133 Jun 25 07:27 team-xbmc-ppa-precise.list
-rw-r--r-- 1 root root 130 Jun 19 08:43 team-xbmc-ppa-precise.list.save
-rw-r--r-- 1 root root 193 Jun 25 07:27 transmissionbt-ppa-precise.list
-rw-r--r-- 1 root root  96 Jun 19 08:43 transmissionbt-ppa-precise.list.save
-rw-r--r-- 1 root root 221 Jun 25 07:27 tualatrix-ppa-precise.list
-rw-r--r-- 1 root root 130 Jun 19 08:43 tualatrix-ppa-precise.list.save
-rw-r--r-- 1 root root 155 Jun 25 07:27 ubuntu-tweak-testing-ppa-precise.list
-rw-r--r-- 1 root root 152 Jun 19 08:43 ubuntu-tweak-testing-ppa-precise.list.save
-rw-r--r-- 1 root root 175 Jun 25 07:27 ubuntu-wine-ppa-precise.list
-rw-r--r-- 1 root root  87 Jun 19 08:43 ubuntu-wine-ppa-precise.list.save
-rw-r--r-- 1 root root  97 Jun 25 07:27 virtualbox-offical-source.list
-rw-r--r-- 1 root root  98 Jun 19 08:43 virtualbox-offical-source.list.save
-rw-r--r-- 1 root root 139 Jun 25 07:27 webupd8team-java-precise.list
-rw-r--r-- 1 root root 136 Jun 19 08:43 webupd8team-java-precise.list.save
-rw-r--r-- 1 root root 143 Jun 25 07:27 webupd8team-themes-precise.list
-rw-r--r-- 1 root root 140 Jun 19 08:43 webupd8team-themes-precise.list.save
-rw-r--r-- 1 root root 157 Jun 25 07:27 webupd8team-y-ppa-manager-precise.list
-rw-r--r-- 1 root root 154 Jun 19 08:43 webupd8team-y-ppa-manager-precise.list.save
-rw-r--r-- 1 root root  74 Jun 25 07:27 yannubuntu-boot-repair-precise.list
-rw-r--r-- 1 root root 148 Jun 19 08:43 yannubuntu-boot-repair-precise.list.save
-rw-r--r-- 1 root root 125 Jun 25 07:27 yorba-ppa-precise.list
-rw-r--r-- 1 root root 122 Jun 19 08:43 yorba-ppa-precise.list.save
cmcanulty@Darcy25:~$ 
```

and the 2nd ones

```
cmcanulty@Darcy25:~$ sudo rm -rf /var/lib/apt/lists/*
[sudo] password for cmcanulty: 
cmcanulty@Darcy25:~$ sudo apt-get update
Ign http://dl.google.com stable InRelease
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Get:2 http://download.virtualbox.org precise InRelease [5,626 B]               
Ign http://archive.canonical.com precise InRelease                             
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://us.archive.ubuntu.com precise InRelease                             
Ign http://us.archive.ubuntu.com precise-updates InRelease                     
Ign http://us.archive.ubuntu.com precise-backports InRelease                   
Ign http://extras.ubuntu.com precise InRelease                                 
Get:3 http://dl.google.com stable Release [1,347 B]                            
Ign http://security.ubuntu.com precise-security InRelease                      
Get:4 http://archive.canonical.com precise Release.gpg [198 B]                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Get:5 http://dl.google.com stable/main amd64 Packages [1,234 B]                
Get:6 http://us.archive.ubuntu.com precise Release.gpg [198 B]                 
Get:7 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Get:8 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Get:9 http://download.virtualbox.org precise/contrib amd64 Packages [977 B]    
Get:10 http://security.ubuntu.com precise-security Release.gpg [198 B]         
Ign http://deb.opera.com lenny InRelease                                       
Get:11 http://archive.canonical.com precise Release [7,078 B]                  
Get:12 http://download.virtualbox.org precise/contrib i386 Packages [986 B]    
Get:13 http://us.archive.ubuntu.com precise-backports Release.gpg [198 B]      
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Get:14 http://extras.ubuntu.com precise Release [11.9 kB]                      
Get:15 http://security.ubuntu.com precise-security Release [49.6 kB]           
Ign http://download.virtualbox.org precise/contrib TranslationIndex            
Get:16 http://deb.opera.com lenny Release.gpg [189 B]                          
Get:17 http://us.archive.ubuntu.com precise Release [49.6 kB]                  
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Get:18 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:19 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Ign http://apt.spideroak.com release InRelease                                 
Get:20 http://deb.opera.com lenny Release [634 B]                              
Get:21 http://archive.canonical.com precise/partner Sources [3,430 B]          
Get:22 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:23 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:24 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:25 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:26 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:27 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:28 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:29 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:30 http://archive.canonical.com precise/partner amd64 Packages [4,314 B]   
Get:31 http://archive.canonical.com precise/partner i386 Packages [4,982 B]    
Get:32 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]          
Get:33 http://deb.opera.com lenny/non-free amd64 Packages [808 B]              
Get:34 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:35 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:36 http://apt.spideroak.com release Release.gpg [189 B]                    
Get:37 http://extras.ubuntu.com precise/main Sources [1,020 B]                 
Get:38 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:39 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:40 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:41 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:42 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:43 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:44 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Ign http://archive.canonical.com precise/partner TranslationIndex              
Get:45 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:46 http://deb.opera.com lenny/non-free i386 Packages [813 B]               
Ign http://deb.opera.com lenny/non-free TranslationIndex                       
Get:47 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:48 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:49 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:50 http://extras.ubuntu.com precise/main amd64 Packages [1,232 B]          
Get:51 http://extras.ubuntu.com precise/main i386 Packages [1,229 B]           
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:52 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:53 http://us.archive.ubuntu.com precise-backports Release [49.6 kB]        
Get:54 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:55 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:56 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:57 http://security.ubuntu.com precise-security/restricted Sources [14 B]   
Ign http://download.virtualbox.org precise/contrib Translation-en_US           
Get:58 http://apt.spideroak.com release Release [1,052 B]                      
Get:59 http://us.archive.ubuntu.com precise/restricted Sources [5,470 B]       
Ign http://download.virtualbox.org precise/contrib Translation-en              
Get:60 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:61 http://us.archive.ubuntu.com precise/main Sources [934 kB]              
Get:62 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:63 http://security.ubuntu.com precise-security/main Sources [21.1 kB]      
Get:64 http://security.ubuntu.com precise-security/multiverse Sources [713 B]  
Get:65 http://security.ubuntu.com precise-security/universe Sources [7,120 B]  
Get:66 http://ppa.launchpad.net precise Release [11.8 kB]                      
Get:67 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:68 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:69 http://security.ubuntu.com precise-security/main amd64 Packages [64.3 kB]
Get:70 http://apt.spideroak.com release/restricted amd64 Packages [657 B]      
Get:71 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:72 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:73 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:74 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:75 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:76 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:77 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:78 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:79 http://security.ubuntu.com precise-security/restricted amd64 Packages [14 B]
Get:80 http://security.ubuntu.com precise-security/universe amd64 Packages [17.2 kB]
Get:81 http://security.ubuntu.com precise-security/multiverse amd64 Packages [1,155 B]
Get:82 http://security.ubuntu.com precise-security/main i386 Packages [65.9 kB]
Get:83 http://apt.spideroak.com release/restricted i386 Packages [657 B]       
Ign http://apt.spideroak.com release/restricted TranslationIndex               
Get:84 http://ppa.launchpad.net precise Release [11.8 kB]                      
Get:85 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:86 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:87 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:88 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:89 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]
Get:90 http://security.ubuntu.com precise-security/universe i386 Packages [17.4 kB]
Get:91 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:92 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:93 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:94 http://ppa.launchpad.net precise Release [11.9 kB]                      
Get:95 http://ppa.launchpad.net precise Release [11.8 kB]                      
Get:96 http://ppa.launchpad.net precise/main Sources [9,458 B]                 
Get:97 http://security.ubuntu.com precise-security/multiverse i386 Packages [1,394 B]
Get:98 http://security.ubuntu.com precise-security/main TranslationIndex [73 B]
Get:99 http://security.ubuntu.com precise-security/multiverse TranslationIndex [71 B]
Get:100 http://security.ubuntu.com precise-security/restricted TranslationIndex [70 B]
Get:101 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Get:102 http://ppa.launchpad.net precise/main amd64 Packages [6,044 B]         
Get:103 http://ppa.launchpad.net precise/main i386 Packages [6,044 B]          
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:104 http://ppa.launchpad.net precise/main amd64 Packages [2,138 B]         
Ign http://archive.canonical.com precise/partner Translation-en_US             
Get:105 http://ppa.launchpad.net precise/main i386 Packages [2,158 B]          
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:106 http://ppa.launchpad.net precise/main Sources [720 B]                  
Get:107 http://ppa.launchpad.net precise/main amd64 Packages [739 B]           
Get:108 http://ppa.launchpad.net precise/main i386 Packages [731 B]            
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://deb.opera.com lenny/non-free Translation-en_US                      
Get:109 http://security.ubuntu.com precise-security/main Translation-en [33.5 kB]
Get:110 http://security.ubuntu.com precise-security/multiverse Translation-en [587 B]
Get:111 http://security.ubuntu.com precise-security/restricted Translation-en [14 B]
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Get:112 http://ppa.launchpad.net precise/main Sources [1,126 B]                
Get:113 http://ppa.launchpad.net precise/main amd64 Packages [1,287 B]         
Get:114 http://dl.google.com stable/main i386 Packages [1,250 B]               
Get:115 http://ppa.launchpad.net precise/main i386 Packages [1,287 B]          
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:116 http://us.archive.ubuntu.com precise/multiverse Sources [155 kB]       
Ign http://deb.opera.com lenny/non-free Translation-en                         
Get:117 http://security.ubuntu.com precise-security/universe Translation-en [11.9 kB]
Ign http://extras.ubuntu.com precise/main Translation-en                       
Get:118 http://ppa.launchpad.net precise/main Sources [550 B]                  
Get:119 http://ppa.launchpad.net precise/main amd64 Packages [1,376 B]         
Get:120 http://ppa.launchpad.net precise/main i386 Packages [1,376 B]          
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:121 http://ppa.launchpad.net precise/main Sources [6,484 B]                
Get:122 http://ppa.launchpad.net precise/main amd64 Packages [12.5 kB]         
Get:123 http://us.archive.ubuntu.com precise/universe Sources [5,019 kB]       
Get:124 http://ppa.launchpad.net precise/main i386 Packages [12.5 kB]          
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:125 http://ppa.launchpad.net precise/main Sources [1,566 B]                
Get:126 http://ppa.launchpad.net precise/main amd64 Packages [2,885 B]         
Get:127 http://ppa.launchpad.net precise/main i386 Packages [2,884 B]          
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:128 http://ppa.launchpad.net precise/main Sources [482 B]                  
Get:129 http://ppa.launchpad.net precise/main amd64 Packages [451 B]           
Get:130 http://ppa.launchpad.net precise/main i386 Packages [451 B]            
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:131 http://ppa.launchpad.net precise/main Sources [510 B]                  
Get:132 http://ppa.launchpad.net precise/main amd64 Packages [457 B]           
Get:133 http://ppa.launchpad.net precise/main i386 Packages [457 B]            
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:134 http://ppa.launchpad.net precise/main amd64 Packages [1,258 B]         
Get:135 http://ppa.launchpad.net precise/main i386 Packages [1,257 B]          
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:136 http://ppa.launchpad.net precise/main amd64 Packages [1,086 B]         
Get:137 http://ppa.launchpad.net precise/main i386 Packages [1,083 B]          
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:138 http://ppa.launchpad.net precise/main Sources [853 B]                  
Get:139 http://ppa.launchpad.net precise/main amd64 Packages [1,749 B]         
Get:140 http://ppa.launchpad.net precise/main i386 Packages [1,759 B]          
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:141 http://ppa.launchpad.net precise/main amd64 Packages [16.3 kB]         
Get:142 http://ppa.launchpad.net precise/main i386 Packages [16.3 kB]          
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:143 http://ppa.launchpad.net precise/main Sources [2,476 B]                
Get:144 http://ppa.launchpad.net precise/main amd64 Packages [7,208 B]         
Get:145 http://ppa.launchpad.net precise/main i386 Packages [7,219 B]          
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:146 http://ppa.launchpad.net precise/main Sources [9,629 B]                
Get:147 http://ppa.launchpad.net precise/main amd64 Packages [16.7 kB]         
Get:148 http://ppa.launchpad.net precise/main i386 Packages [16.7 kB]          
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:149 http://ppa.launchpad.net precise/main Sources [323 B]                  
Get:150 http://ppa.launchpad.net precise/main amd64 Packages [398 B]           
Get:151 http://ppa.launchpad.net precise/main i386 Packages [398 B]            
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:152 http://ppa.launchpad.net precise/main amd64 Packages [1,906 B]         
Get:153 http://ppa.launchpad.net precise/main i386 Packages [1,907 B]          
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:154 http://ppa.launchpad.net precise/main Sources [546 B]                  
Get:155 http://ppa.launchpad.net precise/main amd64 Packages [649 B]           
Get:156 http://ppa.launchpad.net precise/main i386 Packages [649 B]            
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:157 http://ppa.launchpad.net precise/main Sources [577 B]                  
Get:158 http://ppa.launchpad.net precise/main amd64 Packages [665 B]           
Get:159 http://ppa.launchpad.net precise/main i386 Packages [665 B]            
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:160 http://ppa.launchpad.net precise/main amd64 Packages [3,834 B]         
Get:161 http://ppa.launchpad.net precise/main i386 Packages [3,823 B]          
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:162 http://ppa.launchpad.net precise/main Sources [555 B]                  
Get:163 http://ppa.launchpad.net precise/main amd64 Packages [1,589 B]         
Get:164 http://ppa.launchpad.net precise/main i386 Packages [1,589 B]          
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:165 http://ppa.launchpad.net precise/main Sources [3,442 B]                
Get:166 http://ppa.launchpad.net precise/main amd64 Packages [4,143 B]         
Ign http://apt.spideroak.com release/restricted Translation-en_US              
Get:167 http://ppa.launchpad.net precise/main i386 Packages [4,143 B]          
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:168 http://ppa.launchpad.net precise/main Sources [1,056 B]                
Get:169 http://ppa.launchpad.net precise/main amd64 Packages [1,396 B]         
Get:170 http://ppa.launchpad.net precise/main i386 Packages [1,389 B]          
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:171 http://ppa.launchpad.net precise/main amd64 Packages [2,164 B]         
Get:172 http://ppa.launchpad.net precise/main i386 Packages [2,164 B]          
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:173 http://ppa.launchpad.net precise/main Sources [1,185 B]                
Ign http://apt.spideroak.com release/restricted Translation-en                 
Get:174 http://ppa.launchpad.net precise/main amd64 Packages [1,696 B]         
Get:175 http://ppa.launchpad.net precise/main i386 Packages [1,698 B]          
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:176 http://us.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]    
Get:177 http://us.archive.ubuntu.com precise/restricted amd64 Packages [8,452 B]
Get:178 http://us.archive.ubuntu.com precise/universe amd64 Packages [4,786 kB]
Ign http://dl.google.com stable/main TranslationIndex                          
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Get:179 http://us.archive.ubuntu.com precise/multiverse amd64 Packages [119 kB]
Get:180 http://us.archive.ubuntu.com precise/main i386 Packages [1,274 kB]     
Get:181 http://us.archive.ubuntu.com precise/restricted i386 Packages [8,431 B]
Get:182 http://us.archive.ubuntu.com precise/universe i386 Packages [4,796 kB] 
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en         
Ign http://ppa.launchpad.net precise/main Translation-en_US      
Ign http://ppa.launchpad.net precise/main Translation-en         
Ign http://ppa.launchpad.net precise/main Translation-en_US      
Ign http://ppa.launchpad.net precise/main Translation-en         
Ign http://ppa.launchpad.net precise/main Translation-en_US      
Ign http://ppa.launchpad.net precise/main Translation-en         
Ign http://ppa.launchpad.net precise/main Translation-en_US      
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US      
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Get:183 http://us.archive.ubuntu.com precise/multiverse i386 Packages [121 kB] 
Get:184 http://us.archive.ubuntu.com precise/main TranslationIndex [3,706 B]   
Get:185 http://us.archive.ubuntu.com precise/multiverse TranslationIndex [2,676 B]
Get:186 http://us.archive.ubuntu.com precise/restricted TranslationIndex [2,596 B]
Get:187 http://us.archive.ubuntu.com precise/universe TranslationIndex [2,922 B]
Get:188 http://us.archive.ubuntu.com precise-updates/restricted Sources [1,379 B]
Get:189 http://us.archive.ubuntu.com precise-updates/main Sources [117 kB]     
Get:190 http://us.archive.ubuntu.com precise-updates/multiverse Sources [1,058 B]
Get:191 http://us.archive.ubuntu.com precise-updates/universe Sources [28.2 kB]
Get:192 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [297 kB]
Get:193 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [2,417 B]
Get:194 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [81.1 kB]
Get:195 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [1,825 B]
Get:196 http://us.archive.ubuntu.com precise-updates/main i386 Packages [299 kB]
Get:197 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [2,439 B]
Get:198 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [81.6 kB]
Get:199 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [2,049 B]
Get:200 http://us.archive.ubuntu.com precise-updates/main TranslationIndex [74 B]
Get:201 http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex [71 B]
Get:202 http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex [71 B]
Get:203 http://us.archive.ubuntu.com precise-updates/universe TranslationIndex [73 B]
Get:204 http://us.archive.ubuntu.com precise-backports/main Sources [1,346 B]  
Get:205 http://us.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:206 http://us.archive.ubuntu.com precise-backports/universe Sources [6,873 B]
Get:207 http://us.archive.ubuntu.com precise-backports/multiverse Sources [1,383 B]
Get:208 http://us.archive.ubuntu.com precise-backports/main amd64 Packages [929 B]
Get:209 http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]
Get:210 http://us.archive.ubuntu.com precise-backports/universe amd64 Packages [6,114 B]
Get:211 http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages [996 B]
Get:212 http://us.archive.ubuntu.com precise-backports/main i386 Packages [929 B]
Get:213 http://us.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:214 http://us.archive.ubuntu.com precise-backports/universe i386 Packages [6,117 B]
Get:215 http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages [999 B]
Get:216 http://us.archive.ubuntu.com precise-backports/main TranslationIndex [71 B]
Get:217 http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex [71 B]
Get:218 http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex [70 B]
Get:219 http://us.archive.ubuntu.com precise-backports/universe TranslationIndex [72 B]
Get:220 http://us.archive.ubuntu.com precise/main Translation-en [726 kB]      
Get:221 http://us.archive.ubuntu.com precise/multiverse Translation-en [93.4 kB]
Get:222 http://us.archive.ubuntu.com precise/restricted Translation-en [2,395 B]
Get:223 http://us.archive.ubuntu.com precise/universe Translation-en [3,341 kB]
Get:224 http://us.archive.ubuntu.com precise-updates/main Translation-en [136 kB]
Get:225 http://us.archive.ubuntu.com precise-updates/multiverse Translation-en [912 B]
Get:226 http://us.archive.ubuntu.com precise-updates/restricted Translation-en [798 B]
Get:227 http://us.archive.ubuntu.com precise-updates/universe Translation-en [48.4 kB]
Get:228 http://us.archive.ubuntu.com precise-backports/main Translation-en [731 B]
Get:229 http://us.archive.ubuntu.com precise-backports/multiverse Translation-en [422 B]
Get:230 http://us.archive.ubuntu.com precise-backports/restricted Translation-en [14 B]
Get:231 http://us.archive.ubuntu.com precise-backports/universe Translation-en [4,352 B]
Fetched 24.8 MB in 20s (1,224 kB/s)                                            
Reading package lists... Done
W: Duplicate sources.list entry http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_gnome3-team_gnome3_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ precise/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_gnome3-team_gnome3_ubuntu_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/transmissionbt/ppa/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_transmissionbt_ppa_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/transmissionbt/ppa/ubuntu/ precise/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_transmissionbt_ppa_ubuntu_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ precise/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ precise/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_precise_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
cmcanulty@Darcy25:~$ 




```

---

### Post by NikTh on 2012-06-26
Go to Update manager --> settings --> other software and untick all those ppa's 

[URL="http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/"]```
[/URL][http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/) 
[http://ppa.launchpad.net/transmissionbt/ppa/ubuntu/](http://ppa.launchpad.net/transmissionbt/ppa/ubuntu/) 
[http://ppa.launchpad.net/transmissionbt/ppa/ubuntu/](http://ppa.launchpad.net/transmissionbt/ppa/ubuntu/) 
 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) 
[http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) 
[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) 
 [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/)

```

Then try again 
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

---

### Post by d4m1r on 2012-06-26
> **NikTh said:**
> Go to Update manager --> settings --> other software and untick all those ppa's 
 
```
[http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/) 
[http://ppa.launchpad.net/transmissionbt/ppa/ubuntu/](http://ppa.launchpad.net/transmissionbt/ppa/ubuntu/) 
[http://ppa.launchpad.net/transmissionbt/ppa/ubuntu/](http://ppa.launchpad.net/transmissionbt/ppa/ubuntu/) 
 [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) 
[http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) 
[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) 
 [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/)

```
 
Then try again 
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```
 
 
Thanks! Helped me too....

---

### Post by cmcanulty on 2012-06-27
that finally did it thanks. What I don't understand is I thought if I use transmission, ubuntu tweak, etc I should have those repositories in my sources list, please explain so I can fix future errors like this.

---

### Post by NikTh on 2012-06-27
No , i think its not necessary to have them in to sources.list. 
Apt can read also from sources.list.d 
Those repositories are in sources.list.d take a look with 
```
ls /etc/apt/sources.list.d/ 
```and then for example 
```
cat /etc/apt/sources.list.d/webupd8team-java-precise.list
``` and you will see the ppa in there. :)

If problem solved you can **mark thread as solved** from **thread tools**

---

### Post by cmcanulty on 2012-06-27
OK thanks, I just don't understand there are 3 locations of sources and it is OK that they are all different? ie the etc/apt/sources.list.d, etc/apt/sources.list, and var/lib/apt/lists

---

### Post by cortman on 2012-06-27
> **cmcanulty said:**
> OK thanks, I just don't understand there are 3 locations of sources and it is OK that they are all different? ie the etc/apt/sources.list.d, etc/apt/sources.list, and var/lib/apt/lists

/etc/apt/sources.list is the main repository list. This is what contains the default repository addresses.
/etc/apt/sources.list.d/ is a folder container individual files with repository information. If you added third-party repositories with add-apt-repository, this is where that info will be.
/var/lib/apt/lists contains the lists (text files) of all available packages on the repositories. This is refreshed whenever you run apt-get update.

---

### Post by cmcanulty on 2012-06-28
OK thank  you, solved

---

