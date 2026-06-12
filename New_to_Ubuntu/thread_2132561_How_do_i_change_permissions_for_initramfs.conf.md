---
title: "How do i change permissions for initramfs.conf"
date: 2013-04-05
forum: New to Ubuntu
---

### Post by Darkishjace on 2013-04-05
hello im fairly new to lubuntu and everytime ive installed something through terminal it says ```
update-initramfs: deferring update (hook will be called later)
``` for approximately 2 days minimum if i leave it alone i found another forum thread that said if i change ```
MODULE=most 
```
to 
```
MODULE=dep
``` it would solve the problem yet i changed it with a program yet i cant save it need help soon cuz im about to go to sleep ive been up all night trying to make changes to my OS 
thankyou in advance

---

### Post by Bashing-om on 2013-04-05
Darkishjace; Hi !

It is really difficult to respond to this in a manner that is acceptable as to your question. Much more info would be required. As the problem appears to be package management related, Let's take an alternate path for resolution and look at the errors that the package manager generates.
Post the output of terminal codes:
```
sudo apt-get update
sudo apt-get upgrade
``` If you get hung up in the completion of "Updating Initramfs"; try this -> key combo ctl+c to terminate the process;else try prt scrn +r s e i r b to bring the system down safely (after you have transfered the requested output).[INDENT=2]
we will have a looksee

[/INDENT]

---

### Post by Darkishjace on 2013-04-05
after i ran ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get update[/FONT][/COLOR]
``` i it hanged again so i did as you said and > [COLOR=#000000]try this -> key combo ctl+c to terminate the process;else try prt scrn +r s e i r b to bring the system down safely[/COLOR] im currently doing ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get upgrade[/FONT][/COLOR]
``` heres what happened while i ran  the first process ```
lubuntu@lubuntu:~$ sudo rm /var/lib/dpkg/locklubuntu@lubuntu:~$ sudo dpkg --configure -a
Setting up linux-image-3.5.0-26-generic (3.5.0-26.42) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
^CFailed to create initrd image.
dpkg: error processing linux-image-3.5.0-26-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-3.5.0-26-generic:
 linux-image-extra-3.5.0-26-generic depends on linux-image-3.5.0-26-generic; however:
  Package linux-image-3.5.0-26-generic is not configured yet.


dpkg: error processing linux-image-extra-3.5.0-26-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.5.0-26-generic; however:
  Package linux-image-3.5.0-26-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.5.0-26-generic; however:
  Package linux-image-extra-3.5.0-26-generic is not configured yet.


dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic; however:
  Package linux-image-generic is not configured yet.


dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.5.0-26-generic
 linux-image-extra-3.5.0-26-generic
 linux-image-generic
 linux-generic
lubuntu@lubuntu:~$ prt scrn +r s e i r b
No command 'prt' found, did you mean:
 Command 'rt' from package 'rt3.8-clients' (universe)
 Command 'rt' from package 'rt4-clients' (universe)
 Command 'ppt' from package 'bsdgames' (universe)
 Command 'pr' from package 'coreutils' (main)
 Command 'pat' from package 'dist' (universe)
prt: command not found

```

---

### Post by Darkishjace on 2013-04-05
heres the whole terminal information ```
lubuntu@lubuntu:~$ sudo rm /var/lib/dpkg/locklubuntu@lubuntu:~$ sudo dpkg --configure -a
Setting up linux-image-3.5.0-26-generic (3.5.0-26.42) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
^CFailed to create initrd image.
dpkg: error processing linux-image-3.5.0-26-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-3.5.0-26-generic:
 linux-image-extra-3.5.0-26-generic depends on linux-image-3.5.0-26-generic; however:
  Package linux-image-3.5.0-26-generic is not configured yet.


dpkg: error processing linux-image-extra-3.5.0-26-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.5.0-26-generic; however:
  Package linux-image-3.5.0-26-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.5.0-26-generic; however:
  Package linux-image-extra-3.5.0-26-generic is not configured yet.


dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic; however:
  Package linux-image-generic is not configured yet.


dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.5.0-26-generic
 linux-image-extra-3.5.0-26-generic
 linux-image-generic
 linux-generic
lubuntu@lubuntu:~$ prt scrn +r s e i r b
No command 'prt' found, did you mean:
 Command 'rt' from package 'rt3.8-clients' (universe)
 Command 'rt' from package 'rt4-clients' (universe)
 Command 'ppt' from package 'bsdgames' (universe)
 Command 'pr' from package 'coreutils' (main)
 Command 'pat' from package 'dist' (universe)
prt: command not found
lubuntu@lubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  firefox-locale-ar firefox-locale-bn firefox-locale-ca firefox-locale-cs
  firefox-locale-de firefox-locale-el firefox-locale-en firefox-locale-es
  firefox-locale-fi firefox-locale-fr firefox-locale-hi firefox-locale-hu
  firefox-locale-it firefox-locale-ja firefox-locale-nl firefox-locale-pl
  firefox-locale-pt firefox-locale-ru firefox-locale-sv firefox-locale-zh-hans
  libavcodec53 libavformat53 libavutil51 libpoppler-glib8 libpoppler28
  libpostproc52 libswscale2 libxslt1.1 poppler-utils runescape wine1.5
  wine1.5-i386
32 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 42.1 MB of archives.
After this operation, 1,619 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://security.ubuntu.com/ubuntu/ quantal-security/main libavutil51 i386 6:0.8.6-0ubuntu0.12.10.1 [132 kB]
Get:2 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ quantal/main wine1.5 i386 1.5.27-0ubuntu1 [1,109 kB]
Get:3 http://security.ubuntu.com/ubuntu/ quantal-security/main libavcodec53 i386 6:0.8.6-0ubuntu0.12.10.1 [6,052 kB]
Get:4 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ quantal/main wine1.5-i386 i386 1.5.27-0ubuntu1 [24.1 MB]
Get:5 http://security.ubuntu.com/ubuntu/ quantal-security/main libavformat53 i386 6:0.8.6-0ubuntu0.12.10.1 [1,065 kB]
Get:6 http://security.ubuntu.com/ubuntu/ quantal-security/main libpoppler28 i386 0.20.4-0ubuntu1.2 [854 kB]
Get:7 http://security.ubuntu.com/ubuntu/ quantal-security/main libpoppler-glib8 i386 0.20.4-0ubuntu1.2 [96.3 kB]
Get:8 http://security.ubuntu.com/ubuntu/ quantal-security/main libpostproc52 i386 6:0.8.6-0ubuntu0.12.10.1 [114 kB]
Get:9 http://security.ubuntu.com/ubuntu/ quantal-security/main libswscale2 i386 6:0.8.6-0ubuntu0.12.10.1 [203 kB]
Get:10 http://security.ubuntu.com/ubuntu/ quantal-security/main libxslt1.1 i386 1.1.26-14ubuntu0.1 [165 kB]
Get:11 http://security.ubuntu.com/ubuntu/ quantal-security/main firefox-locale-ar i386 20.0+build1-0ubuntu0.12.10.3 [309 kB]
Get:12 http://security.ubuntu.com/ubuntu/ quantal-security/main firefox-locale-bn i386 20.0+build1-0ubuntu0.12.10.3 [694 kB]
Get:13 http://security.ubuntu.com/ubuntu/ quantal-security/main firefox-locale-ca i386 20.0+build1-0ubuntu0.12.10.3 [293 kB]
Get:14 http://security.ubuntu.com/ubuntu/ quantal-security/main firefox-locale-cs i386 20.0+build1-0ubuntu0.12.10.3 [289 kB]
Get:15 http://security.ubuntu.com/ubuntu/ quantal-security/main firefox-locale-de i386 20.0+build1-0ubuntu0.12.10.3 [272 kB]
Get:16 http://security.ubuntu.com/ubuntu/ quantal-security/main firefox-locale-el i386 20.0+build1-0ubuntu0.12.10.3 [316 kB]
Get:17 http://security.ubuntu.com/ubuntu/ quantal-security/main firefox-locale-en i386 20.0+build1-0ubuntu0.12.10.3 [509 kB]
Get:18 http://security.ubuntu.com/ubuntu/ quantal-security/main firefox-locale-es i386 20.0+build1-0ubuntu0.12.10.3 [983 kB]
Get:19 http://security.ubuntu.com/ubuntu/ quantal-security/main firefox-locale-fi i386 20.0+build1-0ubuntu0.12.10.3 [284 kB]
Get:20 http://security.ubuntu.com/ubuntu/ quantal-security/main firefox-locale-fr i386 20.0+build1-0ubuntu0.12.10.3 [289 kB]
Get:21 http://security.ubuntu.com/ubuntu/ quantal-security/main firefox-locale-hi i386 20.0+build1-0ubuntu0.12.10.3 [329 kB]
Get:22 http://security.ubuntu.com/ubuntu/ quantal-security/main firefox-locale-hu i386 20.0+build1-0ubuntu0.12.10.3 [297 kB]
Get:23 http://security.ubuntu.com/ubuntu/ quantal-security/main firefox-locale-it i386 20.0+build1-0ubuntu0.12.10.3 [231 kB]
Get:24 http://security.ubuntu.com/ubuntu/ quantal-security/main firefox-locale-ja i386 20.0+build1-0ubuntu0.12.10.3 [322 kB]
Get:25 http://security.ubuntu.com/ubuntu/ quantal-security/main firefox-locale-nl i386 20.0+build1-0ubuntu0.12.10.3 [284 kB]
Get:26 http://security.ubuntu.com/ubuntu/ quantal-security/main firefox-locale-pl i386 20.0+build1-0ubuntu0.12.10.3 [294 kB]
Get:27 http://security.ubuntu.com/ubuntu/ quantal-security/main firefox-locale-pt i386 20.0+build1-0ubuntu0.12.10.3 [547 kB]
Get:28 http://security.ubuntu.com/ubuntu/ quantal-security/main firefox-locale-ru i386 20.0+build1-0ubuntu0.12.10.3 [282 kB]
Get:29 http://security.ubuntu.com/ubuntu/ quantal-security/main firefox-locale-sv i386 20.0+build1-0ubuntu0.12.10.3 [282 kB]
Get:30 http://security.ubuntu.com/ubuntu/ quantal-security/main firefox-locale-zh-hans i386 20.0+build1-0ubuntu0.12.10.3 [303 kB]
Get:31 http://security.ubuntu.com/ubuntu/ quantal-security/main poppler-utils i386 0.20.4-0ubuntu1.2 [157 kB]
Get:32 http://ppa.launchpad.net/hikariknight/unix-runescape-client/ubuntu/ quantal/main runescape all 201304051439~git-master~quantal1 [624 kB]
Fetched 42.1 MB in 5min 20s (131 kB/s)                                         
Extracting templates from packages: 100%
(Reading database ... 169872 files and directories currently installed.)
Preparing to replace libavutil51:i386 6:0.8.5-0ubuntu0.12.10.1 (using .../libavutil51_6%3a0.8.6-0ubuntu0.12.10.1_i386.deb) ...
Unpacking replacement libavutil51:i386 ...
Preparing to replace libavcodec53:i386 6:0.8.5-0ubuntu0.12.10.1 (using .../libavcodec53_6%3a0.8.6-0ubuntu0.12.10.1_i386.deb) ...
Unpacking replacement libavcodec53:i386 ...
Preparing to replace libavformat53:i386 6:0.8.5-0ubuntu0.12.10.1 (using .../libavformat53_6%3a0.8.6-0ubuntu0.12.10.1_i386.deb) ...
Unpacking replacement libavformat53:i386 ...
Preparing to replace libpoppler28:i386 0.20.4-0ubuntu1.1 (using .../libpoppler28_0.20.4-0ubuntu1.2_i386.deb) ...
Unpacking replacement libpoppler28:i386 ...
Preparing to replace libpoppler-glib8:i386 0.20.4-0ubuntu1.1 (using .../libpoppler-glib8_0.20.4-0ubuntu1.2_i386.deb) ...
Unpacking replacement libpoppler-glib8:i386 ...
Preparing to replace libpostproc52:i386 6:0.8.5-0ubuntu0.12.10.1 (using .../libpostproc52_6%3a0.8.6-0ubuntu0.12.10.1_i386.deb) ...
Unpacking replacement libpostproc52:i386 ...
Preparing to replace libswscale2:i386 6:0.8.5-0ubuntu0.12.10.1 (using .../libswscale2_6%3a0.8.6-0ubuntu0.12.10.1_i386.deb) ...
Unpacking replacement libswscale2:i386 ...
Preparing to replace libxslt1.1:i386 1.1.26-14 (using .../libxslt1.1_1.1.26-14ubuntu0.1_i386.deb) ...
Unpacking replacement libxslt1.1:i386 ...
Preparing to replace wine1.5 1.5.26-0ubuntu1 (using .../wine1.5_1.5.27-0ubuntu1_i386.deb) ...
Unpacking replacement wine1.5 ...
Preparing to replace wine1.5-i386 1.5.26-0ubuntu1 (using .../wine1.5-i386_1.5.27-0ubuntu1_i386.deb) ...
Unpacking replacement wine1.5-i386 ...
Preparing to replace firefox-locale-ar 19.0.2+build1-0ubuntu0.12.10.1 (using .../firefox-locale-ar_20.0+build1-0ubuntu0.12.10.3_i386.deb) ...
Unpacking replacement firefox-locale-ar ...
Preparing to replace firefox-locale-bn 19.0.2+build1-0ubuntu0.12.10.1 (using .../firefox-locale-bn_20.0+build1-0ubuntu0.12.10.3_i386.deb) ...
Unpacking replacement firefox-locale-bn ...
Preparing to replace firefox-locale-ca 19.0.2+build1-0ubuntu0.12.10.1 (using .../firefox-locale-ca_20.0+build1-0ubuntu0.12.10.3_i386.deb) ...
Unpacking replacement firefox-locale-ca ...
Preparing to replace firefox-locale-cs 19.0.2+build1-0ubuntu0.12.10.1 (using .../firefox-locale-cs_20.0+build1-0ubuntu0.12.10.3_i386.deb) ...
Unpacking replacement firefox-locale-cs ...
Preparing to replace firefox-locale-de 19.0.2+build1-0ubuntu0.12.10.1 (using .../firefox-locale-de_20.0+build1-0ubuntu0.12.10.3_i386.deb) ...
Unpacking replacement firefox-locale-de ...
Preparing to replace firefox-locale-el 19.0.2+build1-0ubuntu0.12.10.1 (using .../firefox-locale-el_20.0+build1-0ubuntu0.12.10.3_i386.deb) ...
Unpacking replacement firefox-locale-el ...
Preparing to replace firefox-locale-en 19.0.2+build1-0ubuntu0.12.10.1 (using .../firefox-locale-en_20.0+build1-0ubuntu0.12.10.3_i386.deb) ...
Unpacking replacement firefox-locale-en ...
Preparing to replace firefox-locale-es 19.0.2+build1-0ubuntu0.12.10.1 (using .../firefox-locale-es_20.0+build1-0ubuntu0.12.10.3_i386.deb) ...
Unpacking replacement firefox-locale-es ...
Preparing to replace firefox-locale-fi 19.0.2+build1-0ubuntu0.12.10.1 (using .../firefox-locale-fi_20.0+build1-0ubuntu0.12.10.3_i386.deb) ...
Unpacking replacement firefox-locale-fi ...
Preparing to replace firefox-locale-fr 19.0.2+build1-0ubuntu0.12.10.1 (using .../firefox-locale-fr_20.0+build1-0ubuntu0.12.10.3_i386.deb) ...
Unpacking replacement firefox-locale-fr ...
Preparing to replace firefox-locale-hi 19.0.2+build1-0ubuntu0.12.10.1 (using .../firefox-locale-hi_20.0+build1-0ubuntu0.12.10.3_i386.deb) ...
Unpacking replacement firefox-locale-hi ...
Preparing to replace firefox-locale-hu 19.0.2+build1-0ubuntu0.12.10.1 (using .../firefox-locale-hu_20.0+build1-0ubuntu0.12.10.3_i386.deb) ...
Unpacking replacement firefox-locale-hu ...
Preparing to replace firefox-locale-it 19.0.2+build1-0ubuntu0.12.10.1 (using .../firefox-locale-it_20.0+build1-0ubuntu0.12.10.3_i386.deb) ...
Unpacking replacement firefox-locale-it ...
Preparing to replace firefox-locale-ja 19.0.2+build1-0ubuntu0.12.10.1 (using .../firefox-locale-ja_20.0+build1-0ubuntu0.12.10.3_i386.deb) ...
Unpacking replacement firefox-locale-ja ...
Preparing to replace firefox-locale-nl 19.0.2+build1-0ubuntu0.12.10.1 (using .../firefox-locale-nl_20.0+build1-0ubuntu0.12.10.3_i386.deb) ...
Unpacking replacement firefox-locale-nl ...
Preparing to replace firefox-locale-pl 19.0.2+build1-0ubuntu0.12.10.1 (using .../firefox-locale-pl_20.0+build1-0ubuntu0.12.10.3_i386.deb) ...
Unpacking replacement firefox-locale-pl ...
Preparing to replace firefox-locale-pt 19.0.2+build1-0ubuntu0.12.10.1 (using .../firefox-locale-pt_20.0+build1-0ubuntu0.12.10.3_i386.deb) ...
Unpacking replacement firefox-locale-pt ...
Preparing to replace firefox-locale-ru 19.0.2+build1-0ubuntu0.12.10.1 (using .../firefox-locale-ru_20.0+build1-0ubuntu0.12.10.3_i386.deb) ...
Unpacking replacement firefox-locale-ru ...
Preparing to replace firefox-locale-sv 19.0.2+build1-0ubuntu0.12.10.1 (using .../firefox-locale-sv_20.0+build1-0ubuntu0.12.10.3_i386.deb) ...
Unpacking replacement firefox-locale-sv ...
Preparing to replace firefox-locale-zh-hans 19.0.2+build1-0ubuntu0.12.10.1 (using .../firefox-locale-zh-hans_20.0+build1-0ubuntu0.12.10.3_i386.deb) ...
Unpacking replacement firefox-locale-zh-hans ...
Preparing to replace poppler-utils 0.20.4-0ubuntu1.1 (using .../poppler-utils_0.20.4-0ubuntu1.2_i386.deb) ...
Unpacking replacement poppler-utils ...
Preparing to replace runescape 201303292047~git-master~quantal1 (using .../runescape_201304051439~git-master~quantal1_all.deb) ...
Unpacking replacement runescape ...
Processing triggers for mime-support ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Setting up linux-image-3.5.0-26-generic (3.5.0-26.42) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)

```

---

### Post by Darkishjace on 2013-04-05
[FONT=garamond]my current objectives happen to be making my > **NETGEAR 3100V2** wireless networking device work because right now im currently tethered to my internet with a **Samsung Galaxy SII** as the connection and its limiting what i can and cant to the Bare Minimum and > get a working runescape client so i can play it because everytime it starts loading in **Chromium IcedTea** Crashes after about 1-2 mins and > how to use the full extent of my **Ram cards** because i was forced to clear 3 gb of space on my hard drive to make room for a **LinuxSwap Partition** wich is doing a little better then what i had to deal with before [/FONT]

---

### Post by Bashing-om on 2013-04-05
Darkishjace;

We can not do anything about your want-to's until the package manager is happy and your system is stable.

To that end let's reduce to simplest terms and work on getting the kernel updated.
In ubuntu Software Center disable all 3rd part sources, after stability is achieved will see about enabling them.
For now let's look at what we are working with; Post the output of terminal codes:
```
lsb_release -a
uname -r
```
and now lets see what the errors are:
```

sudo apt-get update
sudo apt-get upgrade
```making sure at this time all that we have to cope with is the kernel configuration problem.[INDENT=3]
sound good ?

[/INDENT]

---

### Post by matt_symes on 2013-04-05
Hi

Let's look at your first error first.

From the terminal, type

```
depmod -n
```

It will take a moment and then display symbols and dependencies on the terminal.

Does it display any errors or hang ? If so then post the last output back here.

After that type

```
sudo dkpg --purge --pending
```

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

Do you still get the same error after the upgrade command ?

If so then post the output of

```
dpkg -l | grep "linux-image.*26-generic"
```

```
df -h
```

```
df -i
```

and finally...

```
ls /boot/initrd*
```

That'll do for a start and will us a place to start looking.

Kind regards

---

### Post by Darkishjace on 2013-04-05
Answer to:Bashing-om
for first code input 
```
lubuntu@lubuntu:~$ lsb_release -aNo LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal
lubuntu@lubuntu:~$ uname -r
3.5.0-26-generic
lubuntu@lubuntu:~$ 

``` 
First Answer for: Matt_symes 
```
alias symbol:dccp_connect dccp
alias symbol:nf_ct_expect_register_notifier nf_conntrack
alias symbol:isdnhdlc_encode isdnhdlc
alias symbol:rtl92c_dm_init_edca_turbo rtl8192c_common
alias symbol:snd_wss_mce_down snd_wss_lib
alias symbol:iio_trigger_poll_chained industrialio
alias symbol:osd_req_add_get_attr_page libosd
alias symbol:nf_conntrack_untracked nf_conntrack
alias symbol:ieee80211_request_smps mac80211
alias symbol:snd_soc_cache_read snd_soc_core
alias symbol:snd_soc_info_volsw_ext snd_soc_core
alias symbol:memstick_register_driver memstick
alias symbol:scsi_tgt_cmd_to_host scsi_tgt
alias symbol:kvm_exit kvm
alias symbol:l3_write snd_soc_l3
alias symbol:cx25821_sram_channel_dump_audio cx25821
alias symbol:lirc_dev_fop_close lirc_dev
alias symbol:rt2800_set_rts_threshold rt2800lib
alias symbol:drm_mode_debug_printmodeline drm
alias symbol:gss_mech_put auth_rpcgss
alias symbol:rpc_max_payload sunrpc
alias symbol:pi_write_regr paride
alias symbol:cx8802_buf_prepare cx8802
alias symbol:cfg80211_mgmt_tx_status cfg80211
alias symbol:nfnl_acct_update nfnetlink_acct
alias symbol:snd_major snd
alias symbol:vme_lm_count vme
alias symbol:cfi_qry_present cfi_util
alias symbol:videobuf_read_stop videobuf_core
alias symbol:il_get_cmd_string iwlegacy
alias symbol:srp_release_transport scsi_transport_srp
alias symbol:rtllib_act_scanning rtllib
alias symbol:videobuf_waiton videobuf_core
alias symbol:register_sja1000dev sja1000
alias symbol:z8530_nop z85230
alias symbol:drm_edid_is_valid drm
alias symbol:viafb_release_dma viafb
alias symbol:hci_le_start_enc bluetooth
alias symbol:mISDN_FsmAddTimer mISDN_core
alias symbol:atbm8830_attach atbm8830
alias symbol:freq_reg_info cfg80211
alias symbol:snd_soc_get_volsw_sx snd_soc_core
alias symbol:snd_soc_put_volsw_sx snd_soc_core
alias symbol:snd_soc_get_volsw_s8 snd_soc_core
alias symbol:snd_soc_put_volsw_s8 snd_soc_core
alias symbol:tda10048_attach tda10048
alias symbol:tda10045_attach tda1004x
alias symbol:tda10046_attach tda1004x
alias symbol:rtl_usb_suspend rtlwifi
alias symbol:o2hb_register_callback ocfs2_nodemanager
alias symbol:nfsacl_encode nfs_acl
alias symbol:nfsacl_decode nfs_acl
alias symbol:p9_client_getattr_dotl 9pnet
alias symbol:il_send_bt_config iwlegacy
alias symbol:spi_bitbang_setup spi_bitbang
alias symbol:fc_get_host_port_state libfc
alias symbol:rpc_call_null sunrpc
alias symbol:brcmf_sdio_remove brcmfmac
alias symbol:fc_exch_mgr_alloc libfc
alias symbol:sm501_misc_control sm501
alias symbol:drm_platform_init drm
alias symbol:drm_platform_exit drm
alias symbol:sunrpc_cache_lookup sunrpc
alias symbol:snd_opl3_init snd_opl3_lib
alias symbol:parport_ieee1284_interrupt parport
alias symbol:af9033_attach af9033
alias symbol:af9013_attach af9013
alias symbol:v4l2_ctrl_add_ctrl videodev
alias symbol:p9_client_create_dotl 9pnet
alias symbol:xdr_encode_opaque_fixed sunrpc
alias symbol:xt_unregister_match x_tables
alias symbol:rdma_translate_ip ib_addr
alias symbol:pi_read_block paride
alias symbol:recv_Bchannel mISDN_core
alias symbol:acpiphp_unregister_attention acpiphp
alias symbol:cfg80211_testmode_reply cfg80211
alias symbol:ip_vs_conn_in_get_proto ip_vs
alias symbol:gspca_coarse_grained_expo_autogain gspca_main
alias symbol:em28xx_tuner_callback em28xx
alias symbol:iscsi_prep_data_out_pdu libiscsi
alias symbol:drm_master_get drm
alias symbol:matrox_millennium matroxfb_Ti3026
alias symbol:ceph_osdc_cancel_event libceph
alias symbol:snd_soc_jack_add_gpios snd_soc_core
alias symbol:gigaset_freecs gigaset
alias symbol:lirc_dev_fop_read lirc_dev
alias symbol:mptscsih_suspend mptscsih
alias symbol:rtl_usb_probe rtlwifi
alias symbol:drbd_role_str drbd
alias symbol:ttm_read_unlock ttm
alias symbol:drm_agp_acquire drm
alias symbol:mc13xxx_fixed_regulator_set_voltage mc13xxx_regulator_core
alias symbol:lrw_crypt lrw
alias symbol:__nf_conntrack_find nf_conntrack
alias symbol:wm8996_detect snd_soc_wm8996
alias symbol:hid_add_device hid
alias symbol:go7007_boot_encoder go7007
alias symbol:rtl2830_attach rtl2830
alias symbol:usbnet_cdc_bind cdc_ether
alias symbol:dm_btree_remove dm_persistent_data
alias symbol:il_rd_prph iwlegacy
alias symbol:il_wr_prph iwlegacy
alias symbol:mlx4_db_free mlx4_core
alias symbol:cxgb4_alloc_atid cxgb4
alias symbol:cxgb4_alloc_stid cxgb4
alias symbol:cxgb3_alloc_atid cxgb3
alias symbol:cxgb3_alloc_stid cxgb3
alias symbol:drm_mm_dump_table drm
alias symbol:gf128mul_bbe gf128mul
alias symbol:snd_interval_refine snd_pcm
alias symbol:videobuf_dvb_dealloc_frontends videobuf_dvb
alias symbol:p54_parse_firmware p54common
alias symbol:hostap_master_start_xmit hostap
alias symbol:rtsx_pci_start_run rtsx_pci
alias symbol:drm_mm_remove_node drm
alias symbol:nfc_allocate_device nfc
alias symbol:nfnetlink_subsys_unregister nfnetlink
alias symbol:ir_raw_event_store_with_filter rc_core
alias symbol:hdlc_change_mtu hdlc
alias symbol:mlx4_qp_to_ready mlx4_core
alias symbol:cnic_unregister_driver cnic
alias symbol:scsi_dh_activate scsi_dh
alias symbol:p9_client_create 9pnet
alias symbol:flexcop_dma_config b2c2_flexcop
alias symbol:eeprom_93cx6_wren eeprom_93cx6
alias symbol:drm_core_reclaim_buffers drm
alias symbol:kvm_set_cr3 kvm
alias symbol:nat_callforwarding_hook nf_conntrack_h323
alias symbol:snd_ctl_find_numid snd
alias symbol:mite_setup mite
alias symbol:vb2_get_vma videobuf2_memops
alias symbol:qlogicfas408_biosparam qlogicfas408
alias symbol:drm_format_num_planes drm
alias symbol:drm_vblank_offdelay drm
alias symbol:nf_ct_helper_ext_add nf_conntrack
alias symbol:snd_hda_sequence_write_cache snd_hda_codec
alias symbol:edac_device_handle_ce edac_core
alias symbol:edac_device_handle_ue edac_core
alias symbol:usb_stor_reset_resume usb_storage
alias symbol:il_init_scan_params iwlegacy
alias symbol:o2hb_stop_all_regions ocfs2_nodemanager
alias symbol:rate_control_send_low mac80211
alias symbol:ieee80211_radiotap_iterator_next cfg80211
alias symbol:snd_gf1_i_look16 snd_gus_lib
alias symbol:cx88_risc_buffer cx88xx
alias symbol:mlx4_unregister_interface mlx4_core
alias symbol:hci_recv_stream_fragment bluetooth
alias symbol:twl6040_get_clk_id snd_soc_twl6040
alias symbol:snd_rawmidi_kernel_read snd_rawmidi
alias symbol:ib_register_mad_snoop ib_mad
alias symbol:mlx4_SET_PORT_general mlx4_core
alias symbol:cxgbi_conn_xmit_pdu libcxgbi
alias symbol:iscsi_host_remove libiscsi
alias symbol:fscache_io_error fscache
alias symbol:is_noslot_pfn kvm
alias symbol:snd_soc_dai_set_tristate snd_soc_core
alias symbol:snd_emux_new snd_emux_synth
alias symbol:iio_update_demux industrialio
alias symbol:ib_register_device ib_core
alias symbol:il_get_active_dwell_time iwlegacy
alias symbol:iscsi_destroy_conn scsi_transport_iscsi
alias symbol:sm501_find_clock sm501
alias symbol:nfc_shdlc_allocate hci
alias symbol:ib_register_event_handler ib_core
alias symbol:ivtv_udma_alloc ivtv
alias symbol:alloc_c_can_dev c_can
alias symbol:il_set_flags_for_band iwlegacy
alias symbol:ipmi_unregister_for_cmd ipmi_msghandler
alias symbol:ni_tio_cancel ni_tiocmd
alias symbol:hsi_event hsi
alias symbol:drm_gem_object_init drm
alias symbol:dccp_v4_request_recv_sock dccp_ipv4
alias symbol:rpcb_getport_async sunrpc
alias symbol:hci_unregister_dev bluetooth
alias symbol:oxygen_write16_masked snd_oxygen_lib
alias symbol:oxygen_write32_masked snd_oxygen_lib
alias symbol:mantis_frontend_power mantis_core
alias symbol:mpt_findImVolumes mptbase
alias symbol:kvm_cpu_get_interrupt kvm
alias symbol:isdn_ppp_unregister_compressor isdn
alias symbol:dm_btree_insert dm_persistent_data
alias symbol:rt2x00mac_configure_filter rt2x00lib
alias symbol:libipw_rx_any libipw
alias symbol:wlcore_boot_run_firmware wlcore
alias symbol:cxgbi_conn_alloc_pdu libcxgbi
alias symbol:viafb_pm_unregister viafb
alias symbol:snd_hda_jack_detect snd_hda_codec
alias symbol:comedi_get_n_channels kcomedilib
alias symbol:dm_btree_find_highest_key dm_persistent_data
alias symbol:cx231xx_set_alt_setting cx231xx
alias symbol:fcoe_queue_timer libfcoe
alias symbol:rpc_pipefs_notifier_register sunrpc
alias symbol:cx24116_attach cx24116
alias symbol:cx88_set_scale cx88xx
alias symbol:i2c_pca_add_numbered_bus i2c_algo_pca
alias symbol:adxl34x_resume adxl34x
alias symbol:wlcore_free_hw wlcore
alias symbol:drm_sysfs_hotplug_event drm
alias symbol:lcd_device_register lcd
alias symbol:svc_auth_unregister sunrpc
alias symbol:snd_info_register snd
alias symbol:kvm_vcpu_uninit kvm
alias symbol:snd_hda_load_patch snd_hda_codec
alias symbol:_snd_pcm_hw_params_any snd_pcm
alias symbol:memstick_free_host memstick
alias symbol:wm97xx_config_gpio wm97xx_ts
alias symbol:uwb_rc_vcmd uwb
alias symbol:dm_rh_region_to_sector dm_region_hash
alias symbol:radio_isa_remove radio_isa
alias symbol:videobuf_dqbuf videobuf_core
alias symbol:rt2x00mac_stop rt2x00lib
alias symbol:libipw_freq_to_channel libipw
alias symbol:osd_req_write_sg_kern libosd
alias symbol:fc_change_queue_type libfc
alias symbol:drm_mm_debug_table drm
alias symbol:ipmi_register_for_cmd ipmi_msghandler
alias symbol:cs5535_gpio_isset gpio_cs5535
alias symbol:irias_new_object irda
alias symbol:nf_conntrack_helper_unregister nf_conntrack
alias symbol:umc_bus_type umc
alias symbol:edac_device_add_device edac_core
alias symbol:edac_device_del_device edac_core
alias symbol:tm6000_tuner_callback tm6000
alias symbol:mpt_put_msg_frame_hi_pri mptbase
alias symbol:mpt_free_msg_frame mptbase
alias symbol:ar9003_mci_setup ath9k_hw
alias symbol:srp_iu_get libsrp
alias symbol:srp_iu_put libsrp
alias symbol:vme_slot_get vme
alias symbol:rtl92c_download_fw rtl8192c_common
alias symbol:osd_start_request libosd
alias symbol:drm_gem_prime_handle_to_fd drm
alias symbol:drm_sysfs_connector_remove drm
alias symbol:cryptd_free_ahash cryptd
alias symbol:rpc_pipe_generic_upcall sunrpc
alias symbol:xprt_unregister_transport sunrpc
alias symbol:snd_opl3_reset snd_opl3_lib
alias symbol:mISDN_FsmInitTimer mISDN_core
alias symbol:iscsi_conn_failure libiscsi
alias symbol:drm_mm_search_free_in_range drm
alias symbol:dccp_insert_option dccp
alias symbol:wiphy_new cfg80211
alias symbol:snd_hda_query_supported_pcm snd_hda_codec
alias symbol:snd_pcm_mmap_data snd_pcm
alias symbol:hid_dump_input hid
alias symbol:ieee80211_reset_queue_rsl r8192u_usb
alias symbol:gigaset_m10x_send_skb gigaset
alias symbol:v4l2_int_ioctl_1 v4l2_int_device
alias symbol:matrix_keypad_build_keymap matrix_keymap
alias symbol:wusbhc_rh_start_port_reset wusbcore
alias symbol:wl1251_init_ieee80211 wl1251
alias symbol:snd_ac97_tune_hardware snd_ac97_codec
alias symbol:w1_write_8 wire
alias symbol:ath9k_hw_btcoex_init_mci ath9k_hw
alias symbol:rt2x00queue_start_queue rt2x00lib
alias symbol:restore_vga vgastate
alias symbol:nfs4_schedule_stateid_recovery nfs
alias symbol:ip_set_nfnl_get ip_set
alias symbol:ip_set_nfnl_put ip_set
alias symbol:snd_soc_unregister_card snd_soc_core
alias symbol:vme_irq_free vme
alias symbol:proc_net_eicon divadidd
alias symbol:dm_bufio_client_create dm_bufio
alias symbol:vid_from_reg hwmon_vid
alias symbol:tda8261_attach tda8261
alias symbol:fw_iso_context_flush_completions firewire_core
alias symbol:ieee80211_bss_get_ie cfg80211
alias symbol:comedi_error comedi
alias symbol:isac_setup hisax_isac
alias symbol:ath9k_hw_set_txq_props ath9k_hw
alias symbol:ath9k_hw_get_txq_props ath9k_hw
alias symbol:rt2x00mac_set_tim rt2x00lib
alias symbol:il_queue_space iwlegacy
alias symbol:ttm_tt_fini ttm
alias symbol:drm_connector_attach_property drm
alias symbol:drm_vblank_post_modeset drm
alias symbol:drm_fb_helper_blank drm_kms_helper
alias symbol:dvb_usb_generic_rw dvb_usb
alias symbol:sas_ssp_task_response libsas
alias symbol:ceph_con_close libceph
alias symbol:tt_msgs edac_mce_amd
alias symbol:dibusb_pid_filter dvb_usb_dibusb_common
alias symbol:isl6405_attach isl6405
alias symbol:unregister_wan_device wanrouter
alias symbol:nf_conntrack_tuple_taken nf_conntrack
alias symbol:wm_hubs_handle_analogue_pdata snd_soc_wm_hubs
alias symbol:snd_device_register snd
alias symbol:rdma_copy_addr ib_addr
alias symbol:ib_find_cached_pkey ib_core
alias symbol:b1_load_config b1
alias symbol:i2o_msg_post_wait_mem i2o_core
alias symbol:__serpent_decrypt serpent_generic
alias symbol:rds_message_put rds
alias symbol:sunrpc_init_cache_detail sunrpc
alias symbol:xdr_encode_word sunrpc
alias symbol:auth_domain_find sunrpc
alias symbol:ip_set_range_to_cidr ip_set
alias symbol:register_mtd_user mtd
alias symbol:ieee80211_wx_set_encode_ext_rsl r8192u_usb
alias symbol:ieee80211_wx_get_encode_ext_rsl r8192u_usb
alias symbol:usb_wwan_ioctl usb_wwan
alias symbol:eip_set_multicast_list 8390p
alias symbol:drm_mode_config_reset drm
alias symbol:acpi_smbus_register_callback sbshc
alias symbol:rds_send_get_message rds
alias symbol:rpc_restart_call_prepare sunrpc
alias symbol:snd_ctl_find_id snd
alias symbol:__uio_register_device uio
alias symbol:ks0108_page ks0108
alias symbol:il_hdl_pm_debug_stats iwlegacy
alias symbol:p9_idpool_destroy 9pnet
alias symbol:ibnl_remove_client ib_core
alias symbol:memstick_remove_host memstick
alias symbol:iTCO_vendor_check_noreboot_on iTCO_vendor_support
alias symbol:il_hdl_csa iwlegacy
alias symbol:ttm_bo_clean_mm ttm
alias symbol:ipmi_get_maintenance_mode ipmi_msghandler
alias symbol:kvm_mmu_page_fault kvm
alias symbol:memstick_unregister_driver memstick
alias symbol:v4l2_fh_init videodev
alias symbol:v4l2_fh_exit videodev
alias symbol:z8530_shutdown z85230
alias symbol:irda_setup_dma irda
alias symbol:llc_build_and_send_ui_pkt llc
alias symbol:core_tpg_del_initiator_node_acl target_core_mod
alias symbol:hostap_remove_interface hostap
alias symbol:eip_netdev_ops 8390p
alias symbol:pcf50633_adc_async_read pcf50633_adc
alias symbol:ttpci_budget_debiwrite budget_core
alias symbol:videobuf_queue_sg_init videobuf_dma_sg
alias symbol:rt2800_get_tsf rt2800lib
alias symbol:__alloc_ei_netdev 8390
alias symbol:read_bytes_from_xdr_buf sunrpc
alias symbol:xt_register_matches x_tables
alias symbol:roccat_report_event hid_roccat
alias symbol:comedi_pci_auto_config comedi
alias symbol:comedi_usb_auto_config comedi
alias symbol:cx24123_get_tuner_i2c_adapter cx24123
alias symbol:fcoe_fc_crc libfcoe
alias symbol:ttm_bo_unlock_delayed_workqueue ttm
alias symbol:matroxfb_wait_for_sync matroxfb_base
alias symbol:dccp_parse_options dccp
alias symbol:ssb_driver_unregister ssb
alias symbol:ib_copy_ah_attr_to_user ib_uverbs
alias symbol:ib_copy_qp_attr_to_user ib_uverbs
alias symbol:wmi_install_notify_handler wmi
alias symbol:v4l2_m2m_dqbuf v4l2_mem2mem
alias symbol:ar9003_paprd_setup_gain_table ath9k_hw
alias symbol:raid_component_add raid_class
alias symbol:async_xor async_xor
alias symbol:snd_ice1712_akm4xxx_free snd_ice17xx_ak4xxx
alias symbol:pcmcia_release_window pcmcia
alias symbol:ni_tio_init_counter ni_tio
alias symbol:usbip_recv usbip_core
alias symbol:hisax_init_pcmcia hisax
alias symbol:dm_rh_dec dm_region_hash
alias symbol:dm_tm_dec dm_persistent_data
alias symbol:i2400m_release i2400m
alias symbol:kvm_emulate_halt kvm
alias symbol:dccp_feat_list_purge dccp
alias symbol:svc_addsock sunrpc
alias symbol:ipcomp_output xfrm_ipcomp
alias symbol:nf_ct_expect_related_report nf_conntrack
alias symbol:snd_hda_ch_mode_get snd_hda_codec
alias symbol:__nand_correct_data nand_ecc
alias symbol:ni_tio_rinsn ni_tio
alias symbol:ni_tio_winsn ni_tio
alias symbol:b1pcmcia_delcard b1pcmcia
alias symbol:usb_stor_bulk_transfer_buf usb_storage
alias symbol:snd_seq_device_register_driver snd_seq_device
alias symbol:iio_kfifo_allocate kfifo_buf
alias symbol:iio_st_channel_get industrialio
alias symbol:mtd_read mtd
alias symbol:dvb_dmx_release dvb_core
alias symbol:orinoco_change_mtu orinoco
alias symbol:cxgbi_cleanup_task libcxgbi
alias symbol:config_group_find_item configfs
alias symbol:ceph_monc_do_statfs libceph
alias symbol:snd_array_new snd_hda_codec
alias symbol:lpddr_cmdset lpddr_cmds
alias symbol:go7007_snd_init go7007
alias symbol:sms_board_power smsmdtv
alias symbol:brcmu_pkt_buf_free_skb brcmutil
alias symbol:srp_target_free libsrp
alias symbol:hashbin_lock_find irda
alias symbol:snd_rawmidi_transmit snd_rawmidi
alias symbol:paride_unregister paride
alias symbol:fw_cancel_transaction firewire_core
alias symbol:z8530_dead_port z85230
alias symbol:iscsi_tcp_cleanup_task libiscsi_tcp
alias symbol:enclosure_find enclosure
alias symbol:af_alg_unregister_type af_alg
alias symbol:qtree_delete_dquot quota_tree
alias symbol:iio_scan_mask_query industrialio
alias symbol:ib_query_qp ib_core
alias symbol:capi_cmsg2str kernelcapi
alias symbol:v4l2_ctrl_log_status videodev
alias symbol:usb_gadget_unregister_driver udc_core
alias symbol:iscsi_conn_send_pdu libiscsi
alias symbol:rds_conn_drop rds
alias symbol:gre_add_protocol gre
alias symbol:ip_vs_proto_name ip_vs
alias symbol:vb2_dma_contig_memops videobuf2_dma_contig
alias symbol:fc_fabric_login libfc
alias symbol:ieee80211_tx_status mac80211
alias symbol:dccp_v4_do_rcv dccp_ipv4
alias symbol:snd_wss_chip_id snd_wss_lib
alias symbol:snd_seq_set_queue_tempo snd_seq
alias symbol:ib_dispatch_event ib_core
alias symbol:mtd_write_user_prot_reg mtd
alias symbol:v4l2_video_std_construct videodev
alias symbol:usbnet_defer_kevent usbnet
alias symbol:rt2800_probe_hw_mode rt2800lib
alias symbol:cxgb4_create_server cxgb4
alias symbol:ttm_bo_unreserve ttm
alias symbol:drm_agp_info drm
alias symbol:dccp_sync_mss dccp
alias symbol:_copy_from_pages sunrpc
alias symbol:snd_soc_dapm_disable_pin snd_soc_core
alias symbol:hostap_get_porttype hostap
alias symbol:osd_req_read_sg_kern libosd
alias symbol:pti_release_masterchannel pti
alias symbol:drm_mode_vrefresh drm
alias symbol:drm_mode_set_crtcinfo drm
alias symbol:fx_init kvm
alias symbol:nf_conntrack_alloc nf_conntrack
alias symbol:snd_wss_overrange snd_wss_lib
alias symbol:__ssb_driver_register ssb
alias symbol:__umc_driver_register umc
alias symbol:uwb_notifs_register uwb
alias symbol:ipack_driver_unregister ipack
alias symbol:dib7000p_set_wbd_ref dib7000p
alias symbol:tda827x_attach tda827x
alias symbol:mlx4_bf_alloc mlx4_core
alias symbol:iscsi_host_free libiscsi
alias symbol:drxd_config_i2c drxd
alias symbol:stb0899_attach stb0899
alias symbol:stv0299_attach stv0299
alias symbol:wpan_phy_for_each ieee802154
alias symbol:xfrm_aalg_get_byname xfrm_algo
alias symbol:snd_aci_get_aci snd_miro
alias symbol:snd_interval_list snd_pcm
alias symbol:ib_dealloc_pd ib_core
alias symbol:cfag12864b_buffer cfag12864b
alias symbol:drm_fb_helper_fill_var drm_kms_helper
alias symbol:snd_trident_write_voice_regs snd_trident
alias symbol:snd_vx_load_boot_image snd_vx_lib
alias symbol:iio_trigger_free industrialio
alias symbol:register_cc770dev cc770
alias symbol:mwifiex_write_data_complete mwifiex
alias symbol:sm501_unit_power sm501
alias symbol:snd_ctl_make_virtual_master snd
alias symbol:hdlc_ioctl hdlc
alias symbol:ttm_base_object_lookup ttm
alias symbol:wm8350_register_led wm8350_regulator
alias symbol:ieee80211_probereq_get mac80211
alias symbol:ieee80211_send_bar mac80211
alias symbol:hci_alloc_dev bluetooth
alias symbol:snd_hda_parse_pin_defcfg snd_hda_codec
alias symbol:ib_send_cm_req ib_cm
alias symbol:ib_send_cm_rep ib_cm
alias symbol:ib_send_cm_rtu ib_cm
alias symbol:ib_send_cm_rej ib_cm
alias symbol:hdlcdrv_arbitrate hdlcdrv
alias symbol:dw_spi_add_host spi_dw
alias symbol:lm3533_ctrlbank_set_pwm lm3533_ctrlbank
alias symbol:lm3533_ctrlbank_get_pwm lm3533_ctrlbank
alias symbol:drm_timestamp_precision drm
alias symbol:svc_reserve sunrpc
alias symbol:cx88_wakeup cx88xx
alias symbol:fw_device_enable_phys_dma firewire_core
alias symbol:snd_soc_cnew snd_soc_core
alias symbol:snd_ice1712_akm4xxx_init snd_ice17xx_ak4xxx
alias symbol:nand_scan_ident nand
alias symbol:iscsi_host_for_each_session scsi_transport_iscsi
alias symbol:drm_format_vert_chroma_subsampling drm
alias symbol:ieee80211_rate_control_unregister mac80211
alias symbol:snd_soc_update_bits_locked snd_soc_core
alias symbol:snd_pcm_format_linear snd_pcm
alias symbol:doc_decode_ecc docecc
alias symbol:ves1820_attach ves1820
alias symbol:rt2x00usb_watchdog rt2x00usb
alias symbol:hostap_setup_dev hostap
alias symbol:osd_req_add_set_attr_list libosd
alias symbol:osd_req_add_get_attr_list libosd
alias symbol:drm_property_create_range drm
alias symbol:rt2x00mac_start rt2x00lib
alias symbol:drm_mm_search_free_generic_hsw drm
alias symbol:ieee80211_iter_keys mac80211
alias symbol:ip6t_register_table ip6_tables
alias symbol:ib_ud_header_init ib_core
alias symbol:cx8800_ctrl_query cx8800
alias symbol:tveeprom_hauppauge_analog tveeprom
alias symbol:mlx4_qp_alloc mlx4_core
alias symbol:try_test_sas_gpio_gp_bit libsas
alias symbol:drm_usb_init drm_usb
alias symbol:drm_usb_exit drm_usb
alias symbol:is_hwpoison_pfn kvm
alias symbol:caif_disconnect_client caif
alias symbol:cfg80211_send_unprot_deauth cfg80211
alias symbol:tda10071_attach tda10071
alias symbol:cx22702_attach cx22702
alias symbol:lbs_process_rxed_packet libertas
alias symbol:mlx4_replace_mac mlx4_core
alias symbol:nsc_gpio_dump nsc_gpio
alias symbol:dccp_recvmsg dccp
alias symbol:unregister_mtd_user mtd
alias symbol:FsmEvent hisax
alias symbol:videobuf_to_dma_contig videobuf_dma_contig
alias symbol:ahci_dev_classify libahci
alias symbol:ipmi_get_my_address ipmi_msghandler
alias symbol:xdr_init_decode_pages sunrpc
alias symbol:iio_dealloc_pollfunc industrialio
alias symbol:memstick_init_req_sg memstick
alias symbol:usb_stor_pre_reset usb_storage
alias symbol:mwifiex_init_shutdown_fw mwifiex
alias symbol:il_setup_rx_scan_handlers iwlegacy
alias symbol:lbs_queue_event libertas
alias symbol:hostap_set_antsel hostap
alias symbol:snd_hda_multi_out_dig_open snd_hda_codec
alias symbol:snd_pcm_format_name snd_pcm
alias symbol:cx88_dsp_detect_stereo_sap cx88xx
alias symbol:rt2x00queue_start_queues rt2x00lib
alias symbol:llc_sap_list_lock llc
alias symbol:tifm_has_ms_pif tifm_core
alias symbol:drm_mm_scan_remove_block_hsw drm
alias symbol:cfg80211_inform_bss cfg80211
alias symbol:xfrm_ealg_get_byid xfrm_algo
alias symbol:sms_board_lna_control smsmdtv
alias symbol:ath9k_hw_set_rx_bufsize ath9k_hw
alias symbol:ttm_bo_device_init ttm
alias symbol:nfnetlink_has_listeners nfnetlink
alias symbol:ahci_ops libahci
alias symbol:__fscache_attr_changed fscache
alias symbol:ax25_header_ops ax25
alias symbol:snd_pcm_suspend_all snd_pcm
alias symbol:mt2063_attach mt2063
alias symbol:i2o_driver_notify_device_add_all i2o_core
alias symbol:rtl92c_phy_sw_chnl_callback rtl8192c_common
alias symbol:unregister_sound_mixer soundcore
alias symbol:edac_pci_create_generic_ctl edac_core
alias symbol:gigaset_isdn_rcv_err gigaset
alias symbol:sas_port_get_phy scsi_transport_sas
alias symbol:ieee80211_ap_probereq_get mac80211
alias symbol:snd_pcm_lib_write snd_pcm
alias symbol:parport_pc_unregister_port parport_pc
alias symbol:cfpkt_tonative caif
alias symbol:ieee80211_resume_disconnect mac80211
alias symbol:bt_accept_enqueue bluetooth
alias symbol:ieee80211_data_to_8023 cfg80211
alias symbol:nf_nat_sdp_session_hook nf_conntrack_sip
alias symbol:pcmcia_parse_events pcmcia_core
alias symbol:onenand_scan onenand
alias symbol:sms_board_led_feedback smsmdtv
alias symbol:lgdt3305_attach lgdt3305
alias symbol:lgdt330x_attach lgdt330x
alias symbol:v4l2_device_register_subdev videodev
alias symbol:usb_wwan_startup usb_wwan
alias symbol:orinoco_if_add orinoco
alias symbol:fc_host_post_vendor_event scsi_transport_fc
alias symbol:ceph_monc_validate_auth libceph
alias symbol:rpc_protocol sunrpc
alias symbol:register_8022_client p8022
alias symbol:dm_tm_create_non_blocking_clone dm_persistent_data
alias symbol:sms_board_event smsmdtv
alias symbol:bcm3510_attach bcm3510
alias symbol:em28xx_read_reg em28xx
alias symbol:kvm_read_guest_page kvm
alias symbol:ceph_pg_poolid_by_name libceph
alias symbol:snd_soc_info_enum_double snd_soc_core
alias symbol:__uwb_addr_print uwb
alias symbol:unregister_capictr_notifier kernelcapi
alias symbol:wusb_et_name wusbcore
alias symbol:_rtl92c_phy_fw_rf_serial_read rtl8192c_common
alias symbol:ceph_destroy_client libceph
alias symbol:snd_hda_add_nid snd_hda_codec
alias symbol:btmrvl_remove_card btmrvl
alias symbol:videobuf_dvb_alloc_frontend videobuf_dvb
alias symbol:fw_core_add_descriptor firewire_core
alias symbol:il_mac_bss_info_changed iwlegacy
alias symbol:osd_req_read_kern libosd
alias symbol:oxygen_read8 snd_oxygen_lib
alias symbol:hidinput_report_event hid
alias symbol:isl6423_attach isl6423
alias symbol:cx2341x_log_status cx2341x
alias symbol:videocodec_attach videocodec
alias symbol:tveeprom_read tveeprom
alias symbol:rt2x00mac_get_ringparam rt2x00lib
alias symbol:iscsi_conn_get_addr_param libiscsi
alias symbol:ttm_bo_acc_size ttm
alias symbol:rpc_call_async sunrpc
alias symbol:snd_hda_codec_new snd_hda_codec
alias symbol:extcon_dev_register extcon_class
alias symbol:get_var speakup
alias symbol:t1pci_detect b1dma
alias symbol:read_dst dst
alias symbol:NCR_700_intr 53c700
alias symbol:snd_hda_get_conn_index snd_hda_codec
alias symbol:btmrvl_send_hscfg_cmd btmrvl
alias symbol:__uwb_rc_try_get uwb
alias symbol:btcx_sort_clips btcx_risc
alias symbol:ath9k_cmn_update_txpow ath9k_common
alias symbol:af_alg_make_sg af_alg
alias symbol:af_alg_free_sg af_alg
alias symbol:range_bipolar2_5 comedi
alias symbol:dib0090_get_wbd_offset dib0090
alias symbol:rtl_cam_mark_invalid rtlwifi
alias symbol:snd_cs4236_ext_out snd_wss_lib
alias symbol:pcmcia_read_config_byte pcmcia
alias symbol:ath_printk ath
alias symbol:ath9k_hw_disable ath9k_hw
alias symbol:rt2800_gain_calibration rt2800lib
alias symbol:eip_tx_timeout 8390p
alias symbol:eip_poll 8390p
alias symbol:iscsi_register_transport scsi_transport_iscsi
alias symbol:snd_wss_get_pcm_ops snd_wss_lib
alias symbol:snd_gf1_ctrl_stop snd_gus_lib
alias symbol:dm_tm_create_with_sm dm_persistent_data
alias symbol:v4l2_event_unsubscribe_all videodev
alias symbol:ath9k_hw_resettxqueue ath9k_hw
alias symbol:orinoco_set_multicast_list orinoco
alias symbol:mlx4_put_eth_qp mlx4_core
alias symbol:iscsi_session_failure libiscsi
alias symbol:uwb_rsv_create uwb
alias symbol:vid_which_vrm hwmon_vid
alias symbol:v4l2_event_queue_fh videodev
alias symbol:libipw_rx libipw
alias symbol:fb_sys_read fb_sys_fops
alias symbol:wpan_phy_unregister ieee802154
alias symbol:ircomm_connect_response ircomm
alias symbol:snd_oss_info_register snd
alias symbol:comedi_buf_write_free comedi
alias symbol:v4l2_prio_open videodev
alias symbol:i2c_dw_xfer i2c_designware_core
alias symbol:orinoco_interrupt orinoco
alias symbol:cxgbi_sock_closed libcxgbi
alias symbol:fc_lport_bsg_request libfc
alias symbol:drm_find_cea_extension drm
alias symbol:ip_set_add ip_set
alias symbol:ip_set_del ip_set
alias symbol:ttm_bo_move_ttm ttm
alias symbol:__tracepoint_iwlwifi_dev_ucode_event iwlwifi
alias symbol:gspca_resume gspca_main
alias symbol:videobuf_dvb_get_frontend videobuf_dvb
alias symbol:em28xx_read_ac97 em28xx
alias symbol:arcnet_interrupt arcnet
alias symbol:pcf50633_read_block pcf50633
alias symbol:ttm_bo_global_release ttm
alias symbol:ssb_chipco_gpio_control ssb
alias symbol:__mtd_next_device mtd
alias symbol:comedi_pci_driver_unregister comedi
alias symbol:comedi_usb_driver_unregister comedi
alias symbol:altera_pid_feed_control altera_ci
alias symbol:ttm_page_alloc_debugfs ttm
alias symbol:cfpkt_set_prio caif
alias symbol:snd_rawmidi_output_params snd_rawmidi
alias symbol:mite_bytes_written_to_memory_lb mite
alias symbol:__pata_platform_remove pata_platform
alias symbol:drm_dp_get_adjust_request_voltage drm_kms_helper
alias symbol:ieee80211_ctstoself_get mac80211
alias symbol:nf_conntrack_htable_size nf_conntrack
alias symbol:snd_hda_add_imux_item snd_hda_codec
alias symbol:nand_manuf_ids nand_ids
alias symbol:tm6000_xc5000_callback tm6000
alias symbol:em28xx_register_extension em28xx
alias symbol:saa7134_ts_qops saa7134
alias symbol:il_set_rxon_channel iwlegacy
alias symbol:cxgb3_queue_tid_release cxgb3
alias symbol:dw_spi_xfer_done spi_dw
alias symbol:mc13xxx_common_init mc13xxx_core
alias symbol:kvm_read_guest_virt kvm
alias symbol:need_ipv4_conntrack nf_conntrack_ipv4
alias symbol:cfi_varsize_frob cfi_util
alias symbol:subdev_700_cleanup ni_daq_700
alias symbol:v4l2_m2m_job_finish v4l2_mem2mem
alias symbol:drm_mm_scan_add_block drm
alias symbol:irias_insert_object irda
alias symbol:ax25_register_pid ax25
alias symbol:snd_opl3_find_patch snd_opl3_lib
alias symbol:snd_pcm_lib_preallocate_pages snd_pcm
alias symbol:tm6000_debug tm6000
alias symbol:rt2800_conf_tx rt2800lib
alias symbol:ceph_osdc_stop libceph
alias symbol:ax25_linkfail_register ax25
alias symbol:snd_soc_dpcm_fe_can_update snd_soc_core
alias symbol:snd_soc_dpcm_be_can_update snd_soc_core
alias symbol:mISDN_register_Bprotocol mISDN_core
alias symbol:dm_tm_read_lock dm_persistent_data
alias symbol:dm_bm_read_lock dm_persistent_data
alias symbol:wusbhc_destroy wusbcore
alias symbol:parport_ieee1284_read_byte parport
alias symbol:parport_claim_or_block parport
alias symbol:isac_init hisax_isac
alias symbol:tm6000_set_reg tm6000
alias symbol:tm6000_get_reg tm6000
alias symbol:usb_stor_sense_invalidCDB usb_storage
alias symbol:_rtl92c_phy_dbm_to_txpwr_Idx rtl8192c_common
alias symbol:mc13xxx_irq_ack mc13xxx_core
alias symbol:ocfs2_dlm_lvb_valid ocfs2_stackglue
alias symbol:ceph_monc_got_mdsmap libceph
alias symbol:ieee80211_get_key_tx_seq mac80211
alias symbol:ieee80211_get_key_rx_seq mac80211
alias symbol:nf_ct_insert_dying_list nf_conntrack
alias symbol:recv_Bchannel_skb mISDN_core
alias symbol:dccp_send_sync dccp
alias symbol:snd_lookup_minor_data snd
alias symbol:uwb_rsv_destroy uwb
alias symbol:il_apm_stop iwlegacy
alias symbol:drm_mm_pre_get_hsw drm
alias symbol:ttpci_budget_deinit budget_core
alias symbol:saa7146_stop_preview saa7146_vv
alias symbol:i2400m_reset i2400m
alias symbol:rtl92c_bt_rssi_state_change rtl8192c_common
alias symbol:drm_fb_helper_set_par drm_kms_helper
alias symbol:ulist_reinit btrfs
alias symbol:ieee80211_get_operstate mac80211
alias symbol:cfg80211_wext_giwname cfg80211
alias symbol:cfg80211_wext_siwmode cfg80211
alias symbol:cfg80211_wext_giwmode cfg80211
alias symbol:cfg80211_send_auth_timeout cfg80211
alias symbol:amdtp_out_stream_init snd_firewire_lib
alias symbol:spk_synth_immediate speakup
alias symbol:regulatory_hint cfg80211
alias symbol:wiphy_rfkill_start_polling cfg80211
alias symbol:snd_soc_dapm_mixer_update_power snd_soc_core
alias symbol:ib_cm_init_qp_attr ib_cm
alias symbol:oslec_hpf_tx echo
alias symbol:videobuf_vmalloc_free videobuf_vmalloc
alias symbol:osd_req_read libosd
alias symbol:bt_sock_link bluetooth
alias symbol:xt_register_target x_tables
alias symbol:ili9320_write ili9320
alias symbol:ip_vs_proto_data_get ip_vs
alias symbol:ib_get_cached_pkey ib_core
alias symbol:dvb_unregister_device dvb_core
alias symbol:videobuf_to_dma videobuf_dma_sg
alias symbol:rndis_command rndis_host
alias symbol:g450_mnp2f g450_pll
alias symbol:rpc_free_iostats sunrpc
alias symbol:rpc_destroy_wait_queue sunrpc
alias symbol:iio_triggered_buffer_predisable industrialio
alias symbol:btmrvl_process_event btmrvl
alias symbol:saa7146_start_preview saa7146_vv
alias symbol:i2400m_post_reset i2400m
alias symbol:kvm_set_cr8 kvm
alias symbol:kvm_get_cr8 kvm
alias symbol:svcauth_unix_purge sunrpc
alias symbol:wiphy_apply_custom_regulatory cfg80211
alias symbol:rtllib_rx rtllib
alias symbol:cx24113_agc_callback cx24113
alias symbol:mpt_event_deregister mptbase
alias symbol:brcmu_pktq_init brcmutil
alias symbol:rtl92c_fill_h2c_cmd rtl8192c_common
alias symbol:xprt_lookup_rqst sunrpc
alias symbol:ct_sip_parse_header_uri nf_conntrack_sip
alias symbol:snd_hda_power_up_d3wait snd_hda_codec
alias symbol:gameport_set_phys gameport
alias symbol:mite_prep_dma mite
alias symbol:xfrm_ealg_get_byidx xfrm_algo
alias symbol:v4l2_prio_check videodev
alias symbol:mdio45_ethtool_spauseparam_an mdio
alias symbol:NS8390_init 8390
alias symbol:gfn_to_memslot kvm
alias symbol:irlmp_register_client irda
alias symbol:nf_ct_expect_alloc nf_conntrack
alias symbol:ath9k_hw_intrpend ath9k_hw
alias symbol:ttm_dma_page_alloc_debugfs ttm
alias symbol:drm_kms_helper_poll_init drm_kms_helper
alias symbol:ceph_copy_to_page_vector libceph
alias symbol:hpi_send_recv snd_asihpi
alias symbol:ib_modify_qp ib_core
alias symbol:p54_init_common p54common
alias symbol:ttm_bo_kunmap ttm
alias symbol:drm_mm_dump_table_hsw drm
alias symbol:drm_put_minor drm
alias symbol:drm_calc_timestamping_constants drm
alias symbol:o2hb_fill_node_map ocfs2_nodemanager
alias symbol:ocfs2_dlm_unlock ocfs2_stackglue
alias symbol:ore_create libore
alias symbol:snd_timer_global_free snd_timer
alias symbol:smscore_register_client smsmdtv
alias symbol:flexcop_dma_allocate b2c2_flexcop
alias symbol:usb_ftdi_elan_edset_flush ftdi_elan
alias symbol:cxgbi_hbas_remove libcxgbi
alias symbol:apple_bl_unregister apple_bl
alias symbol:kvm_release_pfn_dirty kvm
alias symbol:snd_sb8dsp_interrupt snd_sb8_dsp
alias symbol:snd_pcm_lib_writev snd_pcm
alias symbol:usbip_alloc_iso_desc_pdu usbip_core
alias symbol:mISDN_FsmChangeState mISDN_core
alias symbol:saa7146_unregister_device saa7146_vv
alias symbol:cxgb4_dbfifo_count cxgb4
alias symbol:sas_target_destroy libsas
alias symbol:drm_mode_connector_list_update drm
alias symbol:dccp_rcv_state_process dccp
alias symbol:irlmp_get_discoveries irda
alias symbol:__nf_ct_expect_find nf_conntrack
alias symbol:garp_init_applicant garp
alias symbol:usbnet_generic_cdc_bind cdc_ether
alias symbol:snd_vx_suspend snd_vx_lib
alias symbol:vme_dma_request vme
alias symbol:IsLegalChannel r8192u_usb
alias symbol:bt878_start bt878
alias symbol:tm6000_register_extension tm6000
alias symbol:ipv6_find_hdr ip6_tables
alias symbol:uPD98402_init uPD98402
alias symbol:hashbin_new irda
alias symbol:ib_get_client_data ib_core
alias symbol:ib_set_client_data ib_core
alias symbol:flexcop_dma_control_size_irq b2c2_flexcop
alias symbol:dvb_ringbuffer_free dvb_core
alias symbol:dvb_dmxdev_init dvb_core
alias symbol:mlx4_cq_free mlx4_core
alias symbol:sas_bios_param libsas
alias symbol:sas_attach_transport scsi_transport_sas
alias symbol:ioc4_unregister_submodule ioc4
alias symbol:drm_core_ioremap_wc drm
alias symbol:uwb_rsv_state_str uwb
alias symbol:ubi_is_mapped ubi
alias symbol:osd_req_flush_partition libosd
alias symbol:irda_qos_bits_to_value irda
alias symbol:snd_opl3_interrupt snd_opl3_lib
alias symbol:fcoe_libfc_config libfcoe
alias symbol:ax25cmp ax25
alias symbol:snd_soc_dapm_mux_update_power snd_soc_core
alias symbol:vme_dma_pattern_attribute vme
alias symbol:rt2800_mcu_request rt2800lib
alias symbol:iscsi_conn_bind libiscsi
alias symbol:pcf50633_gpio_invert_set pcf50633_gpio
alias symbol:pcf50633_gpio_invert_get pcf50633_gpio
alias symbol:snd_ctl_free_one snd
alias symbol:iw_cm_reject iw_cm
alias symbol:bt878_num bt878
alias symbol:lm3533_read lm3533_core
alias symbol:scx200_gpio_base scx200
alias symbol:oxygen_write_uart snd_oxygen_lib
alias symbol:vme_master_request vme
alias symbol:iio_st_read_channel_raw industrialio
alias symbol:rtllib_wx_set_encode_ext rtllib
alias symbol:go7007_register_encoder go7007
alias symbol:v4l2_fh_open videodev
alias symbol:unregister_candev can_dev
alias symbol:cxgbi_iscsi_cleanup libcxgbi
alias symbol:dlm_print_one_lock ocfs2_dlm
alias symbol:nf_ct_helper_expectfn_register nf_conntrack
alias symbol:alloc_dca_provider dca
alias symbol:ib_find_pkey ib_core
alias symbol:videobuf_stop videobuf_core
alias symbol:mpt_resume mptbase
alias symbol:_rtl92c_phy_bb8192c_config_parafile rtl8192c_common
alias symbol:xprt_alloc sunrpc
alias symbol:rdma_addr_cancel ib_addr
alias symbol:labpc_1200_is_unipolar ni_labpc
alias symbol:dm_rh_recovery_end dm_region_hash
alias symbol:usb_stor_CB_transport usb_storage
alias symbol:il_restore_stations iwlegacy
alias symbol:drm_connector_init drm
alias symbol:ieee802154_nl_start_confirm ieee802154
alias symbol:cx231xx_send_usb_command cx231xx
alias symbol:v4l2_device_put videodev
alias symbol:i2o_driver_notify_controller_add_all i2o_core
alias symbol:ioc_list mptbase
alias symbol:sirdev_raw_write sir_dev
alias symbol:mdio45_probe mdio
alias symbol:rt2x00pci_probe rt2x00pci
alias symbol:svc_pool_stats_open sunrpc
alias symbol:target_splice_sess_cmd_list target_core_mod
alias symbol:comedi_dio_bitfield kcomedilib
alias symbol:ath_gen_timer_isr ath9k_hw
alias symbol:snd_pcm_rate_to_rate_bit snd_pcm
alias symbol:ib_modify_device ib_core
alias symbol:cfag12864b_getrate cfag12864b
alias symbol:sas_target_alloc libsas
alias symbol:ceph_calc_file_object_mapping libceph
alias symbol:snd_hda_set_vmaster_tlv snd_hda_codec
alias symbol:snd_wss_mixer snd_wss_lib
alias symbol:ubi_get_device_info ubi
alias symbol:rndis_unbind rndis_host
alias symbol:z8530_queue_xmit z85230
alias symbol:mlx4_buf_free mlx4_core
alias symbol:snd_hda_jack_report_sync snd_hda_codec
alias symbol:target_fabric_configfs_init target_core_mod
alias symbol:dib7000p_set_gpio dib7000p
alias symbol:vb2_queue_release videobuf2_core
alias symbol:ttm_bo_evict_mm ttm
alias symbol:cfg80211_rx_unexpected_4addr_frame cfg80211
alias symbol:iio_buffer_unregister industrialio
alias symbol:vb2_vmalloc_memops videobuf2_vmalloc
alias symbol:ttm_base_object_init ttm
alias symbol:ceph_parse_options libceph
alias symbol:dccp_ackvec_parsed_cleanup dccp
alias symbol:wm8350_mic_jack_detect snd_soc_wm8350
alias symbol:mtd_read_fact_prot_reg mtd
alias symbol:dm_rh_get_region_size dm_region_hash
alias symbol:dib7000p_pid_filter dib7000p
alias symbol:dib7000m_pid_filter dib7000m
alias symbol:lis3lv02d_remove_fs lis3lv02d
alias symbol:drm_mm_get_block_generic_hsw drm
alias symbol:ore_calc_stripe_info libore
alias symbol:nfc_shdlc_free hci
alias symbol:snd_soc_jack_get_type snd_soc_core
alias symbol:snd_emux_register snd_emux_synth
alias symbol:ib_dealloc_xrcd ib_core
alias symbol:b1_register_appl b1
alias symbol:ivtv_udma_unmap ivtv
alias symbol:ceph_copy_page_vector_to_user libceph
alias symbol:cfg80211_michael_mic_failure cfg80211
alias symbol:ipt_do_table ip_tables
alias symbol:snd_seq_dump_var_event snd_seq
alias symbol:_snd_ctl_add_slave snd
alias symbol:ib_create_ah ib_core
alias symbol:xt_find_target x_tables
alias symbol:snd_opl4_write_memory snd_opl4_lib
alias symbol:rtllib_legal_channel rtllib
alias symbol:FsmNew hisax
alias symbol:ath6kl_core_tx_complete ath6kl_core
alias symbol:ath6kl_core_rx_complete ath6kl_core
alias symbol:drm_mode_object_find drm
alias symbol:drm_clflush_sg drm
alias symbol:nfs_request_remove_commit_list nfs
alias symbol:rpc_proc_register sunrpc
alias symbol:rpc_queue_empty sunrpc
alias symbol:snd_hda_sequence_write snd_hda_codec
alias symbol:fcoe_wwn_to_str libfcoe
alias symbol:c2port_device_register core
alias symbol:nfc_alloc_recv_skb nfc
alias symbol:snd_hda_bind_sw snd_hda_codec
alias symbol:snd_emu10k1_ptr_write snd_emu10k1
alias symbol:uwb_ie_next uwb
alias symbol:bttv_read_gpio bttv
alias symbol:il_init_channel_map iwlegacy
alias symbol:xprt_alloc_slot sunrpc
alias symbol:snd_pcm_hw_param_value snd_pcm
alias symbol:rdma_destroy_qp rdma_cm
alias symbol:rdma_destroy_id rdma_cm
alias symbol:dst_error_bailout dst
alias symbol:nf_nat_follow_master nf_nat
alias symbol:fw_iso_buffer_init firewire_core
alias symbol:srp_rport_add scsi_transport_srp
alias symbol:fc_remote_port_rolechg scsi_transport_fc
alias symbol:lm3533_ctrlbank_set_max_current lm3533_ctrlbank
alias symbol:ocfs2_stack_glue_register ocfs2_stackglue
alias symbol:p9_idpool_check 9pnet
alias symbol:p9_client_symlink 9pnet
alias symbol:svc_bind sunrpc
alias symbol:snd_use_lock_sync_helper snd_seq
alias symbol:snd_jack_new snd
alias symbol:cm_class ib_cm
alias symbol:comedi_buf_memcpy_to comedi
alias symbol:sdhci_pltfm_free sdhci_pltfm
alias symbol:dst_comm_init dst
alias symbol:dib8090p_get_dc_power dib8000
alias symbol:cx8802_register_driver cx8802
alias symbol:kvm_mmu_load kvm
alias symbol:rpc_peeraddr sunrpc
alias symbol:lib80211_crypt_delayed_deinit lib80211
alias symbol:FsmInitTimer hisax
alias symbol:sirdev_get_instance sir_dev
alias symbol:sirdev_put_instance sir_dev
alias symbol:il_clear_ucode_stations iwlegacy
alias symbol:viafb_irq_enable viafb
alias symbol:crc32c libcrc32c
alias symbol:xt_register_targets x_tables
alias symbol:snd_gus_create snd_gus_lib
alias symbol:wm9712_codec wm97xx_ts
alias symbol:snd_timer_pause snd_timer
alias symbol:ni_gpct_device_destroy ni_tio
alias symbol:dib8000_attach dib8000
alias symbol:xor_blocks xor
alias symbol:ieee80211_iterate_active_interfaces mac80211
alias symbol:nf_nat_pptp_hook_outbound nf_conntrack_pptp
alias symbol:snd_trident_free_voice snd_trident
alias symbol:snd_hda_jack_detect_enable snd_hda_codec
alias symbol:rtllib_get_beacon rtllib
alias symbol:free_candev can_dev
alias symbol:macvlan_start_xmit macvlan
alias symbol:mlx4_alloc_hwq_res mlx4_core
alias symbol:qlogicfas408_disable_ints qlogicfas408
alias symbol:drm_mode_legacy_fb_format drm
alias symbol:isdnhdlc_out_init isdnhdlc
alias symbol:mpt_send_handshake_request mptbase
alias symbol:fc_exch_recv libfc
alias symbol:nat_t120_hook nf_conntrack_h323
alias symbol:unregister_sound_dsp soundcore
alias symbol:spk_serial_release speakup
alias symbol:hci_send_acl bluetooth
alias symbol:alloc_irdadev irda
alias symbol:inet_sk_diag_fill inet_diag
alias symbol:arpt_unregister_table arp_tables
alias symbol:rc_map_af9005_table_size dvb_usb_af9005_remote
alias symbol:stv0367ter_attach stv0367
alias symbol:stv0367cab_attach stv0367
# Device nodes to trigger on-demand module loading.
microcode cpu/microcode c10:184
autofs4 autofs c10:235
btrfs btrfs-control c10:234
vhost_net vhost-net c10:238
snd_timer snd/timer c116:33
snd_seq snd/seq c116:1
lubuntu@lubuntu:~$ 

``` i dont know wich of your suggestions to do next first

---

### Post by matt_symes on 2013-04-05
Hi

The output from depmod looks fine.

so please now run

```
sudo dpkg --purge --pending
```

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

How does that go ?

Kind regards

---

### Post by Darkishjace on 2013-04-05
k so i noticed that matts had one code to do before you both were in the same place so i ran it and got ```
lubuntu@lubuntu:~$ sudo dkpg --purge --pendingsudo: dkpg: command not found
lubuntu@lubuntu:~$ 

```

---

### Post by Darkishjace on 2013-04-05
opps i noticed a mistake in the code so i ran it again with the fix in it and got ```
lubuntu@lubuntu:~$ sudo dpkg --purge --pending
dpkg: error: dpkg status database is locked by another process
lubuntu@lubuntu:~$ 

```

---

### Post by matt_symes on 2013-04-05
Hi

Do you have update manager or software center open. 

If you do then close them and re-run the commands in my last post.

If they are not open then please post the output of

```
ps aux | egrep "dpkg|apt|cent|manager"
```

and 

```
sudo lsof /var/lib/dpkg/status
```

Something has a lock on your dpkg status database

Kind regards

---

### Post by Darkishjace on 2013-04-05
```
lubuntu@lubuntu:~$ ps aux | egrep "dpkg|apt|cent|manager"root        66  0.0  0.0      0     0 ?        S<   13:44   0:00 [charger_manager]
root      2600  0.0  0.3   7428  1600 ?        Ss   13:45   0:00 /usr/sbin/modem-manager
lubuntu   4062  0.0  0.3  29656  1852 ?        Ssl  13:45   0:00 xfce4-power-manager
root      4308  0.0  0.1   5492   616 ?        S    13:45   0:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/sendsigs.omit.d/network-manager.dhclient-usb0.pid -lf /var/lib/dhcp/dhclient-6ba03832-bafc-4a44-99ea-69e17e8836e0-usb0.lease -cf /var/run/nm-dhclient-usb0.conf usb0
nobody    4313  0.0  0.1   5720   972 ?        S    13:45   0:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/var/run/sendsigs.omit.d/network-manager.dnsmasq.pid --listen-address=127.0.1.1 --conf-file=/var/run/nm-dns-dnsmasq.conf --cache-size=0 --proxy-dnssec --enable-dbus=org.freedesktop.NetworkManager.dnsmasq --conf-dir=/etc/NetworkManager/dnsmasq.d
root      7786  0.0  0.1   7852   900 ?        S    14:27   0:00 sudo apt-get upgrade
root      7787  0.0  0.1  34680   908 ?        S    14:27   0:05 apt-get upgrade
root      8619  0.0  0.1   7708   624 pts/0    Ss+  14:35   0:00 /usr/bin/dpkg --status-fd 39 --configure linux-image-3.5.0-26-generic:i386 linux-image-extra-3.5.0-26-generic:i386 linux-image-generic:i386 linux-generic:i386 libavutil51:i386 libavcodec53:i386 libavformat53:i386 libpoppler28:i386 libpoppler-glib8:i386 libpostproc52:i386 libswscale2:i386 libxslt1.1:i386 wine1.5:i386 wine1.5-i386:i386 firefox-locale-ar:i386 firefox-locale-bn:i386 firefox-locale-ca:i386 firefox-locale-cs:i386 firefox-locale-de:i386 firefox-locale-el:i386 firefox-locale-en:i386 firefox-locale-es:i386 firefox-locale-fi:i386 firefox-locale-fr:i386 firefox-locale-hi:i386 firefox-locale-hu:i386 firefox-locale-it:i386 firefox-locale-ja:i386 firefox-locale-nl:i386 firefox-locale-pl:i386 firefox-locale-pt:i386 firefox-locale-ru:i386 firefox-locale-sv:i386 firefox-locale-zh-hans:i386 poppler-utils:i386 runescape:all
root      8620  0.0  0.1   7184   540 pts/0    S+   14:35   0:00 /usr/bin/perl /var/lib/dpkg/info/linux-image-3.5.0-26-generic.postinst configure 
lubuntu   9884  0.0  0.1   4644   800 pts/3    S+   16:33   0:00 egrep --color=auto dpkg|apt|cent|manager
lubuntu@lubuntu:~$ 

```

---

### Post by Darkishjace on 2013-04-05
```
lubuntu@lubuntu:~$ sudo lsof /var/lib/dpkg/statuslsof: WARNING: can't stat() ext2 file system /cow
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/lubuntu/gvfs
      Output information may be incomplete.
lubuntu@lubuntu:~$ 

```

---

### Post by Darkishjace on 2013-04-05
when i installed Lubuntu i had issues with mounting my harddrive and had to input a code to create the folder for it to beable to mount idk if their is any other folders i might happen to be missing wich might be the cause of all my woes

---

### Post by matt_symes on 2013-04-05
Hi

You have number of apt and dpkg instances running.

From the terminal

```
sudo kill 34680 7852 7708 7184
```

```
sudo dpkg --purge --pending
```

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

Post back errors and results.

Kind regards

---

### Post by Darkishjace on 2013-04-05
k did what u said and i got this far before another error ```
lubuntu@lubuntu:~$ sudo kill 34680 7852 7708 7184 
lubuntu@lubuntu:~$ sudo dpkg --purge --pending
dpkg: error: dpkg status database is locked by another process
lubuntu@lubuntu:~$ 

```

---

### Post by Darkishjace on 2013-04-05
tried it as separate codes and still got ```
lubuntu@lubuntu:~$ sudo kill 34680 
lubuntu@lubuntu:~$ sudo kill 7852
lubuntu@lubuntu:~$ sudo kill 7708
lubuntu@lubuntu:~$ sudo kill 7184
lubuntu@lubuntu:~$ sudo dpkg --purge --pending
dpkg: error: dpkg status database is locked by another process
lubuntu@lubuntu:~$ 

```

---

### Post by matt_symes on 2013-04-05
Hi

Sorry i was looking at the wrong column. Been a long day here.

Try this

```
sudo kill 7786 7787 8619 8620
```

Then run those other command again.

Kind regards

---

### Post by Darkishjace on 2013-04-05
k it came up clean this time ```
lubuntu@lubuntu:~$ sudo kill 7786 7787 8619 8620 
lubuntu@lubuntu:~$ sudo dpkg --purge --pending 
lubuntu@lubuntu:~$ 
```

---

### Post by matt_symes on 2013-04-05
Hi

Next run

```
sudo apt-get clean
```

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

Post back any errors.

Sorry bashing-om. I did not realise you had replied back into this thread otherwise i would have left you to continue it. I did not see your post #6.

Kind regards

---

### Post by Bashing-om on 2013-04-05
@ Matt, Hey It is always my pleasure to watch an 'buntu Master at work ! Thanks again.
I have been monitoring this thread, and caught the column error, was just verifying before I spoke.

@ 		Darkishjace; Awaiting Matt's last directive, to see what the status is now.
[INDENT=2]
watch'n and wait'n

[/INDENT]

---

### Post by Darkishjace on 2013-04-05
k so i got to the part where u told me to put ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get upgrade[/FONT][/COLOR]
``` and it reached the part where it initiates ```
update-initramfs: deferring update (hook will be called later)
``` just outta curiosity how long is this process supposed to take cuz it has taken me about 1-2 days everytime it comes up

---

### Post by Darkishjace on 2013-04-05
@Bashing-om thank you very much for standing by i need all the help i can get to insure my problems are fixed. 

i appreciate both of your guys help with my problems thank you very much

---

### Post by Bashing-om on 2013-04-05
Darkishjace;

update-initramfs should only take a matter of seconds.

Matt, what about trying to update initramfs with
```
sudo update-initramfs -u
``` see what errors we get.(??)

---

### Post by matt_symes on 2013-04-05
Hi

> **Bashing-om said:**
> It is always my pleasure to watch an 'buntu Master at work

Not exactly a master, just a regular user but thanks for the compliment. :KS

> **Darkishjace said:**
> ```
update-initramfs: deferring update (hook will be called later)
``` just outta curiosity how long is this process supposed to take cuz it has taken me about 1-2 days everytime it comes up

It should take a minute or two to run.

Let's see what happens when we create it manually.

From the terminal

```
sudo update-initramfs -v -c -k 3.5.0-26-generic
```

Post any output back here. Does it hang still ?

Kind regards

---

### Post by Darkishjace on 2013-04-05
its still running at the moment how do i stop it so i can do as u asked

---

### Post by matt_symes on 2013-04-05
Hi

> **Darkishjace said:**
> its still running at the moment how do i stop it so i can do as u asked

Press ctrl + c in the terminal where it's running.

The command to manually create the initramfs will give us alot more information about what it's done/ doing and where it's hanging as it's using the -v switch (at least this is the hope).

Kind regards

---

### Post by Darkishjace on 2013-04-05
unfortunately it didnt do anything is their another way other then closing the terminal (ive noticed just closing the terminal causes more problems then good)

---

### Post by matt_symes on 2013-04-05
Hi

> **Darkishjace said:**
> unfortunately it didnt do anything is their another way other then closing the terminal (ive noticed just closing the terminal causes more problems then good)

Pressing ctrl and c at the same time did not kill it ?

Alright. Please run this command again from another terminal and post back the results.

```
ps aux | egrep "dpkg|apt|cent|manager|update"
```

Post the results back here. 

We're not making to much progress at the moment but hopefully that will change.

@bashng-om. Good idea about manually generating initramfs. 

Kind regards

---

### Post by Darkishjace on 2013-04-05
```
lubuntu@lubuntu:~$ ps aux | egrep "dpkg|apt|cent|manager|update" 
root        66  0.0  0.0      0     0 ?        S<   13:44   0:00 [charger_manager]
root      2600  0.0  0.3   7428  1668 ?        Ss   13:45   0:00 /usr/sbin/modem-manager
lubuntu   4056  0.0  0.6 186420  3140 ?        Sl   13:45   0:01 update-notifier
lubuntu   4062  0.0  0.4  29656  2068 ?        Ssl  13:45   0:00 xfce4-power-manager
root      4308  0.0  0.1   5492   616 ?        S    13:45   0:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/sendsigs.omit.d/network-manager.dhclient-usb0.pid -lf /var/lib/dhcp/dhclient-6ba03832-bafc-4a44-99ea-69e17e8836e0-usb0.lease -cf /var/run/nm-dhclient-usb0.conf usb0
nobody    4313  0.0  0.1   5720   904 ?        S    13:45   0:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/var/run/sendsigs.omit.d/network-manager.dnsmasq.pid --listen-address=127.0.1.1 --conf-file=/var/run/nm-dns-dnsmasq.conf --cache-size=0 --proxy-dnssec --enable-dbus=org.freedesktop.NetworkManager.dnsmasq --conf-dir=/etc/NetworkManager/dnsmasq.d
root      8626  0.0  0.0   2232   380 ?        S    14:37   0:00 sh -c /usr/sbin/update-initramfs -c -k 3.5.0-26-generic >&2
root      8627  0.0  0.0   2232   380 ?        S    14:37   0:00 /bin/sh /usr/sbin/update-initramfs -c -k 3.5.0-26-generic
root     10385  0.0  0.1   7852   932 pts/2    S+   17:31   0:00 sudo apt-get upgrade
root     10386  0.0  0.1  13824   844 pts/2    S+   17:31   0:00 apt-get upgrade
root     10396  0.0  0.1   7708   656 pts/3    Ss+  17:31   0:00 /usr/bin/dpkg --status-fd 19 --configure libavutil51:i386 libavcodec53:i386 libavformat53:i386 libpoppler28:i386 libpoppler-glib8:i386 libpostproc52:i386 libswscale2:i386 libxslt1.1:i386 linux-image-3.5.0-26-generic:i386 wine1.5-i386:i386 wine1.5:i386 firefox-locale-ar:i386 firefox-locale-bn:i386 firefox-locale-ca:i386 firefox-locale-cs:i386 firefox-locale-de:i386 firefox-locale-el:i386 firefox-locale-en:i386 firefox-locale-es:i386 firefox-locale-fi:i386 firefox-locale-fr:i386 firefox-locale-hi:i386 firefox-locale-hu:i386 firefox-locale-it:i386 firefox-locale-ja:i386 firefox-locale-nl:i386 firefox-locale-pl:i386 firefox-locale-pt:i386 firefox-locale-ru:i386 firefox-locale-sv:i386 firefox-locale-zh-hans:i386 linux-image-extra-3.5.0-26-generic:i386 linux-image-generic:i386 linux-generic:i386 poppler-utils:i386 runescape:all
root     10437  0.0  0.1   7184   536 pts/3    S+   17:31   0:00 /usr/bin/perl /var/lib/dpkg/info/linux-image-3.5.0-26-generic.postinst configure 
root     10441  0.0  0.0   2232   380 pts/3    S+   17:32   0:00 sh -c /usr/sbin/update-initramfs -c -k 3.5.0-26-generic >&2
root     10442  0.0  0.0   2232   380 pts/3    S+   17:32   0:00 /bin/sh /usr/sbin/update-initramfs -c -k 3.5.0-26-generic
lubuntu  10765  0.0  0.1   4644   796 pts/4    S+   18:28   0:00 egrep --color=auto dpkg|apt|cent|manager|update
lubuntu@lubuntu:~$ 

```

---

### Post by Bashing-om on 2013-04-05
Waiting to see what results we get back//maybe redo the /boot/initrd.img… file ??

It has been slow going, but getting to the bottom of things and making progress.[INDENT]
once upon a time

[/INDENT]

---

### Post by matt_symes on 2013-04-05
Hi

Copy and paste these command into the terminal

```
sudo kill 8626 8627 10385 10386 10396 10437 10441 10442
```

```
sudo update-initramfs -d -k 3.5.0-26-generic
```

The above command may give an error. If it does then don't worry. It will just ensure it has deleted that initramfs.

The command below will try to recreate it again.

```
sudo update-initramfs -v -c -k 3.5.0-26-generic
```

On the last command you should get plenty of output. When it hangs post the last 15 or so lines into your next post.

Kind regards

---

### Post by Darkishjace on 2013-04-05
```
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/micrel/ks8851.koAdding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/micrel/ks8851_mll.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/micrel/ksz884x.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/hp/hp100.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/natsemi/ns83820.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/natsemi/natsemi.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/adaptec/starfire.ko
Adding binary /lib/firmware/adaptec/starfire_tx.bin
Adding firmware adaptec/starfire_tx.bin
Adding binary /lib/firmware/adaptec/starfire_rx.bin
Adding firmware adaptec/starfire_rx.bin
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/mellanox/mlx4/mlx4_core.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/mellanox/mlx4/mlx4_en.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/alteon/acenic.ko
Adding binary /lib/firmware/3.5.0-26-generic/acenic/tg2.bin
Adding firmware acenic/tg2.bin
Adding binary /lib/firmware/3.5.0-26-generic/acenic/tg1.bin
Adding firmware acenic/tg1.bin
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/cirrus/cs89x0.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/microchip/enc28j60.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/xircom/xirc2ps_cs.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/dlink/de600.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/dlink/sundance.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/dlink/de620.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/dlink/dl2k.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/brocade/bna/bna.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/marvell/sky2.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/marvell/skge.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/chelsio/cxgb4/cxgb4.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/chelsio/cxgb4vf/cxgb4vf.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/chelsio/cxgb3/cxgb3.ko
Adding binary /lib/firmware/cxgb3/ael2020_twx_edc.bin
Adding firmware cxgb3/ael2020_twx_edc.bin
Adding binary /lib/firmware/cxgb3/ael2005_twx_edc.bin
Adding firmware cxgb3/ael2005_twx_edc.bin
Adding binary /lib/firmware/cxgb3/ael2005_opt_edc.bin
Adding firmware cxgb3/ael2005_opt_edc.bin
Adding binary /lib/firmware/cxgb3/t3c_psram-1.1.0.bin
Adding firmware cxgb3/t3c_psram-1.1.0.bin
Adding binary /lib/firmware/cxgb3/t3b_psram-1.1.0.bin
Adding firmware cxgb3/t3b_psram-1.1.0.bin
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/chelsio/cxgb/cxgb.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/nvidia/forcedeth.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/smsc/smsc9420.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/smsc/epic100.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/smsc/smc91c92_cs.ko
Adding binary /lib/firmware/ositech/Xilinx7OD.bin
Adding firmware ositech/Xilinx7OD.bin
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/smsc/smc9194.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/cisco/enic/enic.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/i825xx/znet.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/i825xx/3c507.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/i825xx/3c505.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/i825xx/82596.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/i825xx/ni52.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/i825xx/eexpress.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/i825xx/eepro.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/i825xx/lp486e.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/via/via-rhine.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/lib/crc-ccitt.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/via/via-velocity.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/stmicro/stmmac/stmmac.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/sis/sis900.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/sis/sis190.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/packetengines/yellowfin.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/packetengines/hamachi.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/sun/cassini.ko
Adding binary /lib/firmware/sun/cassini.bin
Adding firmware sun/cassini.bin
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/sun/niu.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/sun/sunhme.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/sungem_phy.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/sun/sungem.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/neterion/s2io.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/neterion/vxge/vxge.ko
Adding binary /lib/firmware/vxge/X3fw.ncf
Adding firmware vxge/X3fw.ncf
Adding binary /lib/firmware/vxge/X3fw-pxe.ncf
Adding firmware vxge/X3fw-pxe.ncf
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/atheros/atl1c/atl1c.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/atheros/atl1e/atl1e.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/atheros/atlx/atl1.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/atheros/atlx/atl2.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/wiznet/w5100.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/wiznet/w5300.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/icplus/ipg.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/qlogic/qla3xxx.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/qlogic/netxen/netxen_nic.ko
Adding binary /lib/firmware/phanfw.bin
Adding firmware phanfw.bin
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/qlogic/qlge/qlge.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/qlogic/qlcnic/qlcnic.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/jme.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/seeq/seeq8005.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/rdc/r6040.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/oki-semi/pch_gbe/pch_gbe.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/tehuti/tehuti.ko
Adding binary /lib/firmware/tehuti/bdx.bin
Adding firmware tehuti/bdx.bin
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/3com/3c509.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/3com/3c501.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/3com/3c589_cs.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/3com/3c574_cs.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/3com/typhoon.ko
Adding binary /lib/firmware/3com/typhoon.bin
Adding firmware 3com/typhoon.bin
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/3com/3c59x.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/3com/3c515.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/myricom/myri10ge/myri10ge.ko
Adding binary /lib/firmware/myri10ge_rss_eth_z8e.dat
Adding firmware myri10ge_rss_eth_z8e.dat
Adding binary /lib/firmware/myri10ge_rss_ethp_z8e.dat
Adding firmware myri10ge_rss_ethp_z8e.dat
Adding binary /lib/firmware/myri10ge_eth_z8e.dat
Adding firmware myri10ge_eth_z8e.dat
Adding binary /lib/firmware/myri10ge_ethp_z8e.dat
Adding firmware myri10ge_ethp_z8e.dat
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/i2c/algos/i2c-algo-bit.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/mtd/mtd.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/sfc/sfc.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/silan/sc92031.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/ti/tlan.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/broadcom/bnx2.ko
Adding binary /lib/firmware/3.5.0-26-generic/bnx2/bnx2-rv2p-09ax-6.0.17.fw
Adding firmware bnx2/bnx2-rv2p-09ax-6.0.17.fw
Adding binary /lib/firmware/3.5.0-26-generic/bnx2/bnx2-rv2p-09-6.0.17.fw
Adding firmware bnx2/bnx2-rv2p-09-6.0.17.fw
Adding binary /lib/firmware/3.5.0-26-generic/bnx2/bnx2-mips-09-6.2.1b.fw
Adding firmware bnx2/bnx2-mips-09-6.2.1b.fw
Adding binary /lib/firmware/3.5.0-26-generic/bnx2/bnx2-rv2p-06-6.0.15.fw
Adding firmware bnx2/bnx2-rv2p-06-6.0.15.fw
Adding binary /lib/firmware/3.5.0-26-generic/bnx2/bnx2-mips-06-6.2.3.fw
Adding firmware bnx2/bnx2-mips-06-6.2.3.fw
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/broadcom/tg3.ko
Adding binary /lib/firmware/3.5.0-26-generic/tigon/tg3_tso5.bin
Adding firmware tigon/tg3_tso5.bin
Adding binary /lib/firmware/3.5.0-26-generic/tigon/tg3_tso.bin
Adding firmware tigon/tg3_tso.bin
Adding binary /lib/firmware/3.5.0-26-generic/tigon/tg3.bin
Adding firmware tigon/tg3.bin
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/uio/uio.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/broadcom/cnic.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/broadcom/bnx2x/bnx2x.ko
Adding binary /lib/firmware/3.5.0-26-generic/bnx2x/bnx2x-e2-7.2.51.0.fw
Adding firmware bnx2x/bnx2x-e2-7.2.51.0.fw
Adding binary /lib/firmware/3.5.0-26-generic/bnx2x/bnx2x-e1h-7.2.51.0.fw
Adding firmware bnx2x/bnx2x-e1h-7.2.51.0.fw
Adding binary /lib/firmware/3.5.0-26-generic/bnx2x/bnx2x-e1-7.2.51.0.fw
Adding firmware bnx2x/bnx2x-e1-7.2.51.0.fw
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ssb/ssb.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/broadcom/b44.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/emulex/benet/be2net.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ethernet/fealnx.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ppp/ppp_deflate.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ppp/bsd_comp.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ppp/ppp_mppe.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ppp/pppox.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ppp/pppoe.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ppp/ppp_async.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/net/ipv4/gre.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ppp/pptp.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/ppp/ppp_synctty.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/vmxnet3/vmxnet3.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/slip/slip.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/parport/parport.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/plip/plip.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/sb1000.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/caif/caif_serial.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/caif/cfspi_slave.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/caif/caif_hsi.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/net/dsa/dsa_core.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/dsa/mv88e6060.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/dsa/mv88e6xxx_drv.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/rionet.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/fddi/defxx.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/net/fddi/skfp/skfp.ko
Copying module directory kernel/drivers/scsi
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/scsi_transport_iscsi.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/libiscsi.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/scsi_tgt.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/raid_class.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/scsi_wait_scan.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/libiscsi_tcp.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/scsi_transport_sas.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/scsi_transport_fc.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/libfc/libfc.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/fcoe/libfcoe.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/fcoe/fcoe.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/BusLogic.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/libsas/libsas.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/qla1280.ko
Adding binary /lib/firmware/3.5.0-26-generic/qlogic/12160.bin
Adding firmware qlogic/12160.bin
Adding binary /lib/firmware/3.5.0-26-generic/qlogic/1280.bin
Adding firmware qlogic/1280.bin
Adding binary /lib/firmware/3.5.0-26-generic/qlogic/1040.bin
Adding firmware qlogic/1040.bin
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/vmw_pvscsi.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/hv_storvsc.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/iscsi_tcp.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/aha152x.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/53c700.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/bnx2i/bnx2i.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/aha1542.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/ips.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/osst.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/aic94xx/aic94xx.ko
Adding binary /lib/firmware/aic94xx-seq.fw
Adding firmware aic94xx-seq.fw
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/dc395x.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/virtio_scsi.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/scsi_transport_srp.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/eata.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/dmx3191d.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/hptiop.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/iscsi_boot_sysfs.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/qla4xxx/qla4xxx.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/tmscsim.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/gdth.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/ultrastor.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/mvsas/mvsas.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/bfa/bfa.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/NCR53c406a.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/ufs/ufshcd.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/3w-sas.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/ch.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/nsp32.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/wd7000.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/sim710.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/in2000.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/device_handler/scsi_dh.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/device_handler/scsi_dh_alua.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/device_handler/scsi_dh_hp_sw.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/device_handler/scsi_dh_rdac.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/device_handler/scsi_dh_emc.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/cxgbi/libcxgbi.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/cxgbi/cxgb3i/cxgb3i.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/cxgbi/cxgb4i/cxgb4i.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/aha1740.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/qlogicfas408.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/qlogicfas.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/fnic/fnic.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/dtc.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/3w-9xxx.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/mvumi.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/mpt2sas/mpt2sas.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/sym53c416.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/a100u2w.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/advansys.ko
Adding binary /lib/firmware/advansys/38C1600.bin
Adding firmware advansys/38C1600.bin
Adding binary /lib/firmware/advansys/38C0800.bin
Adding firmware advansys/38C0800.bin
Adding binary /lib/firmware/advansys/3550.bin
Adding firmware advansys/3550.bin
Adding binary /lib/firmware/advansys/mcode.bin
Adding firmware advansys/mcode.bin
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/u14-34f.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/imm.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/t128.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/stex.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/pas16.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/scsi_debug.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/ipr.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/g_NCR5380.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/fdomain.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/megaraid/megaraid_sas.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/megaraid/megaraid_mm.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/megaraid/megaraid_mbox.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/arcmsr/arcmsr.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/pm8001/pm8001.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/misc/enclosure.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/ses.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/qla2xxx/qla2xxx.ko
Adding binary /lib/firmware/ql2500_fw.bin
Adding firmware ql2500_fw.bin
Adding binary /lib/firmware/ql2400_fw.bin
Adding firmware ql2400_fw.bin
Adding binary /lib/firmware/ql2322_fw.bin
Adding firmware ql2322_fw.bin
Adding binary /lib/firmware/ql2300_fw.bin
Adding firmware ql2300_fw.bin
Adding binary /lib/firmware/ql2200_fw.bin
Adding firmware ql2200_fw.bin
Adding binary /lib/firmware/ql2100_fw.bin
Adding firmware ql2100_fw.bin
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/target/target_core_mod.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/qla2xxx/tcm_qla2xxx.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/atp870u.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/3w-xxxx.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/lpfc/lpfc.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/isci/isci.ko
Adding binary /lib/firmware/isci/isci_firmware.bin
Adding firmware isci/isci_firmware.bin
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/megaraid.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/ppa.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/g_NCR5380_mmio.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/initio.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/st.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/sym53c8xx_2/sym53c8xx.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/dpt_i2o.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/hpsa.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/libsrp.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/be2iscsi/be2iscsi.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/aic7xxx/aic7xxx.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/aic7xxx/aic79xx.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/aacraid/aacraid.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/bnx2fc/bnx2fc.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/pcmcia/nsp_cs.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/pcmcia/aha152x_cs.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/pcmcia/sym53c500_cs.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/pcmcia/fdomain_cs.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/pcmcia/qlogic_cs.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/pmcraid.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/osd/libosd.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/scsi/osd/osd.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/message/fusion/mptbase.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/message/fusion/mptscsih.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/message/fusion/mptfc.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/message/fusion/mptsas.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/message/fusion/mptspi.ko
Copying module directory kernel/drivers/block
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/nbd.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/floppy.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/osdblk.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/pktcdvd.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/cryptoloop.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/umem.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/paride/paride.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/paride/aten.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/paride/ktti.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/paride/on26.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/paride/pf.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/paride/friq.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/paride/on20.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/paride/pg.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/paride/pt.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/paride/fit3.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/paride/kbic.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/paride/pd.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/paride/frpw.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/paride/bpck.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/paride/bpck6.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/paride/epia.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/paride/dstr.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/paride/epat.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/paride/comm.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/paride/pcd.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/paride/fit2.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/cciss.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/nvme.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/DAC960.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/lib/lru_cache.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/drbd/drbd.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/cpqarray.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/aoe/aoe.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/sx8.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/ub.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/xen-blkback/xen-blkback.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/mtip32xx/mtip32xx.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/net/ceph/libceph.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/block/rbd.ko
Copying module directory kernel/drivers/ata
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/libahci.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/acard-ahci.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/ahci.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/ahci_platform.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_it8213.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_triflex.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_rdc.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_cs5530.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_hpt366.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_cs5536.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/sata_uli.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_sc1200.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_hpt3x3.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_legacy.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_cs5520.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_cmd64x.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_serverworks.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_via.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/sata_promise.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_oldpiix.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_cypress.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/sata_sil.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_sch.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_radisys.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_pdc202xx_old.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_opti.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_pcmcia.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_platform.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/sata_sil24.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/sata_vsc.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_ninja32.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_sl82c105.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_cmd640.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_jmicron.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_ali.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_ns87415.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_hpt37x.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_hpt3x2n.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_atp867x.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_efar.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_optidma.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pdc_adma.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/sata_nv.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/sata_inic162x.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/sata_sis.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_cs5535.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_it821x.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_arasan_cf.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_isapnp.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_sil680.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_ns87410.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_rz1000.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/sata_via.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_netcell.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_piccolo.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_atiixp.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/sata_sx4.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/sata_mv.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/sata_svw.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_amd.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/sata_qstor.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_artop.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_marvell.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_mpiix.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/ata/pata_pdc2027x.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/message/i2o/i2o_core.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/message/i2o/i2o_block.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/firewire/firewire-core.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/firewire/firewire-ohci.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/firewire/firewire-sbp2.ko
Copying module directory kernel/drivers/mmc
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/mmc/card/mmc_block.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/mmc/card/sdio_uart.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/mmc/host/sdhci.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/mmc/host/sdhci-pci.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/mfd/rtsx_pci.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/mmc/host/rtsx_pci_sdmmc.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/mmc/host/via-sdmmc.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/mmc/host/ushc.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/misc/cb710/cb710.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/mmc/host/cb710-mmc.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/misc/tifm_core.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/mmc/host/tifm_sd.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/mmc/host/sdricoh_cs.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/mmc/host/vub300.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/mmc/host/wbsd.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/mmc/host/sdhci-pltfm.ko
Copying module directory kernel/drivers/usb/storage
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/usb/storage/usb-storage.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/usb/storage/ums-freecom.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/usb/storage/ums-sddr55.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/usb/storage/ums-eneub6250.ko
Adding binary /lib/firmware/ene-ub6250/ms_rdwr.bin
Adding firmware ene-ub6250/ms_rdwr.bin
Adding binary /lib/firmware/ene-ub6250/msp_rdwr.bin
Adding firmware ene-ub6250/msp_rdwr.bin
Adding binary /lib/firmware/ene-ub6250/ms_init.bin
Adding firmware ene-ub6250/ms_init.bin
Adding binary /lib/firmware/ene-ub6250/sd_rdwr.bin
Adding firmware ene-ub6250/sd_rdwr.bin
Adding binary /lib/firmware/ene-ub6250/sd_init2.bin
Adding firmware ene-ub6250/sd_init2.bin
Adding binary /lib/firmware/ene-ub6250/sd_init1.bin
Adding firmware ene-ub6250/sd_init1.bin
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/usb/storage/ums-usbat.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/usb/storage/ums-jumpshot.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/usb/storage/ums-alauda.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/usb/storage/ums-karma.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/usb/storage/ums-isd200.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/usb/storage/ums-realtek.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/usb/storage/ums-onetouch.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/usb/storage/ums-cypress.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/usb/storage/ums-sddr09.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/usb/storage/ums-datafab.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/hv/hv_utils.ko
Adding binary /usr/lib/initramfs-tools/bin/wait-for-root
Adding library /lib/i386-linux-gnu/libudev.so.0
Adding library /lib/i386-linux-gnu/libc.so.6
Adding library /lib/i386-linux-gnu/librt.so.1
Adding library /lib/ld-linux.so.2
Adding library /lib/i386-linux-gnu/libpthread.so.0
Adding binary /sbin/modprobe
Adding binary /sbin/rmmod
Adding binary /sbin/blkid
Adding library /lib/i386-linux-gnu/libblkid.so.1
Adding library /lib/i386-linux-gnu/libuuid.so.1
Calling hook casper
Adding module /lib/modules/3.5.0-26-generic/kernel/ubuntu/aufs/aufs.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/fs/overlayfs/overlayfs.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/crypto/md4.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/crypto/des_generic.ko
Adding binary /sbin/losetup
Adding binary /usr/share/casper/casper-reconfigure
Adding binary /usr/share/casper/casper-preseed
Adding binary /usr/share/casper/casper-set-selections
Adding binary /lib/udev/cdrom_id
Adding binary /usr/bin/eject
Adding binary /sbin/mount.cifs
Adding module /lib/modules/3.5.0-26-generic/kernel/fs/cifs/cifs.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/fs/squashfs/squashfs.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/fs/nls/nls_utf8.ko
Adding binary /usr/lib/casper/casper-md5check
Adding library /lib/libply-boot-client.so.2
Adding library /lib/libply.so.2
Adding library /lib/i386-linux-gnu/libdl.so.2
Copying module directory kernel/drivers/net
(excluding appletalk arcnet bonding can hamradio irda pcmcia tokenring usb wan wimax wireless)
Calling hook compcache
Calling hook cryptroot
cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab
Adding module /lib/modules/3.5.0-26-generic/kernel/arch/x86/crypto/aes-i586.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/crypto/gf128mul.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/crypto/xts.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/md/dm-crypt.ko
Adding binary /sbin/cryptsetup
Adding library /lib/libcryptsetup.so.4
Adding library /lib/i386-linux-gnu/libpopt.so.0
Adding library /lib/i386-linux-gnu/libdevmapper.so.1.02.1
Adding library /lib/i386-linux-gnu/libgcrypt.so.11
Adding library /lib/i386-linux-gnu/libselinux.so.1
Adding library /lib/i386-linux-gnu/libgpg-error.so.0
Adding binary /sbin/dmsetup
Adding binary /lib/cryptsetup/askpass
Calling hook dmraid
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/md/dm-log.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/md/dm-region-hash.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/md/dm-mirror.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/crypto/xor.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/ubuntu/dm-raid4-5/dm-raid45.ko
Adding binary /sbin/dmraid
Adding library /lib/libdmraid.so.1.0.0.rc16
Adding binary /sbin/dmraid-activate
Calling hook fixrtc
Adding binary /bin/date
Adding binary /sbin/hwclock
Adding binary /sbin/dumpe2fs
Adding library /lib/i386-linux-gnu/libext2fs.so.2
Adding library /lib/i386-linux-gnu/libcom_err.so.2
Adding library /lib/i386-linux-gnu/libe2p.so.2
Calling hook framebuffer
Copying module directory kernel/drivers/char/agp
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/char/agp/efficeon-agp.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/char/agp/ati-agp.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/char/agp/sworks-agp.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/char/agp/ali-agp.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/char/agp/sis-agp.ko
Copying module directory kernel/drivers/gpu
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/gpu/drm/drm.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/gpu/drm/drm_kms_helper.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/gpu/drm/ttm/ttm.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/gpu/drm/radeon/radeon.ko
Adding binary /lib/firmware/radeon/R520_cp.bin
Adding firmware radeon/R520_cp.bin
Adding binary /lib/firmware/radeon/RS600_cp.bin
Adding firmware radeon/RS600_cp.bin
Adding binary /lib/firmware/radeon/RS690_cp.bin
Adding firmware radeon/RS690_cp.bin
Adding binary /lib/firmware/radeon/R420_cp.bin
Adding firmware radeon/R420_cp.bin
Adding binary /lib/firmware/radeon/R300_cp.bin
Adding firmware radeon/R300_cp.bin
Adding binary /lib/firmware/radeon/R200_cp.bin
Adding firmware radeon/R200_cp.bin
Adding binary /lib/firmware/radeon/R100_cp.bin
Adding firmware radeon/R100_cp.bin
Adding binary /lib/firmware/radeon/RV710_me.bin
Adding firmware radeon/RV710_me.bin
Adding binary /lib/firmware/radeon/RV710_pfp.bin
Adding firmware radeon/RV710_pfp.bin
Adding binary /lib/firmware/radeon/RV730_me.bin
Adding firmware radeon/RV730_me.bin
Adding binary /lib/firmware/radeon/RV730_pfp.bin
Adding firmware radeon/RV730_pfp.bin
Adding binary /lib/firmware/radeon/RV770_me.bin
Adding firmware radeon/RV770_me.bin
Adding binary /lib/firmware/radeon/RV770_pfp.bin
Adding firmware radeon/RV770_pfp.bin
Adding binary /lib/firmware/radeon/RS780_me.bin
Adding firmware radeon/RS780_me.bin
Adding binary /lib/firmware/radeon/RS780_pfp.bin
Adding firmware radeon/RS780_pfp.bin
Adding binary /lib/firmware/radeon/RV670_me.bin
Adding firmware radeon/RV670_me.bin
Adding binary /lib/firmware/radeon/RV670_pfp.bin
Adding firmware radeon/RV670_pfp.bin
Adding binary /lib/firmware/radeon/RV635_me.bin
Adding firmware radeon/RV635_me.bin
Adding binary /lib/firmware/radeon/RV635_pfp.bin
Adding firmware radeon/RV635_pfp.bin
Adding binary /lib/firmware/radeon/RV620_me.bin
Adding firmware radeon/RV620_me.bin
Adding binary /lib/firmware/radeon/RV620_pfp.bin
Adding firmware radeon/RV620_pfp.bin
Adding binary /lib/firmware/radeon/RV630_me.bin
Adding firmware radeon/RV630_me.bin
Adding binary /lib/firmware/radeon/RV630_pfp.bin
Adding firmware radeon/RV630_pfp.bin
Adding binary /lib/firmware/radeon/RV610_me.bin
Adding firmware radeon/RV610_me.bin
Adding binary /lib/firmware/radeon/RV610_pfp.bin
Adding firmware radeon/RV610_pfp.bin
Adding binary /lib/firmware/radeon/R600_me.bin
Adding firmware radeon/R600_me.bin
Adding binary /lib/firmware/radeon/R600_pfp.bin
Adding firmware radeon/R600_pfp.bin
Adding binary /lib/firmware/radeon/SUMO2_me.bin
Adding firmware radeon/SUMO2_me.bin
Adding binary /lib/firmware/radeon/SUMO2_pfp.bin
Adding firmware radeon/SUMO2_pfp.bin
Adding binary /lib/firmware/radeon/SUMO_me.bin
Adding firmware radeon/SUMO_me.bin
Adding binary /lib/firmware/radeon/SUMO_pfp.bin
Adding firmware radeon/SUMO_pfp.bin
Adding binary /lib/firmware/radeon/SUMO_rlc.bin
Adding firmware radeon/SUMO_rlc.bin
Adding binary /lib/firmware/radeon/PALM_me.bin
Adding firmware radeon/PALM_me.bin
Adding binary /lib/firmware/radeon/PALM_pfp.bin
Adding firmware radeon/PALM_pfp.bin
Adding binary /lib/firmware/radeon/CYPRESS_rlc.bin
Adding firmware radeon/CYPRESS_rlc.bin
Adding binary /lib/firmware/radeon/CYPRESS_me.bin
Adding firmware radeon/CYPRESS_me.bin
Adding binary /lib/firmware/radeon/CYPRESS_pfp.bin
Adding firmware radeon/CYPRESS_pfp.bin
Adding binary /lib/firmware/radeon/JUNIPER_rlc.bin
Adding firmware radeon/JUNIPER_rlc.bin
Adding binary /lib/firmware/radeon/JUNIPER_me.bin
Adding firmware radeon/JUNIPER_me.bin
Adding binary /lib/firmware/radeon/JUNIPER_pfp.bin
Adding firmware radeon/JUNIPER_pfp.bin
Adding binary /lib/firmware/radeon/REDWOOD_rlc.bin
Adding firmware radeon/REDWOOD_rlc.bin
Adding binary /lib/firmware/radeon/REDWOOD_me.bin
Adding firmware radeon/REDWOOD_me.bin
Adding binary /lib/firmware/radeon/REDWOOD_pfp.bin
Adding firmware radeon/REDWOOD_pfp.bin
Adding binary /lib/firmware/radeon/CEDAR_rlc.bin
Adding firmware radeon/CEDAR_rlc.bin
Adding binary /lib/firmware/radeon/CEDAR_me.bin
Adding firmware radeon/CEDAR_me.bin
Adding binary /lib/firmware/radeon/CEDAR_pfp.bin
Adding firmware radeon/CEDAR_pfp.bin
Adding binary /lib/firmware/radeon/R700_rlc.bin
Adding firmware radeon/R700_rlc.bin
Adding binary /lib/firmware/radeon/R600_rlc.bin
Adding firmware radeon/R600_rlc.bin
Adding binary /lib/firmware/radeon/ARUBA_rlc.bin
Adding firmware radeon/ARUBA_rlc.bin
Adding binary /lib/firmware/radeon/ARUBA_me.bin
Adding firmware radeon/ARUBA_me.bin
Adding binary /lib/firmware/radeon/ARUBA_pfp.bin
Adding firmware radeon/ARUBA_pfp.bin
Adding binary /lib/firmware/radeon/CAYMAN_rlc.bin
Adding firmware radeon/CAYMAN_rlc.bin
Adding binary /lib/firmware/radeon/CAYMAN_mc.bin
Adding firmware radeon/CAYMAN_mc.bin
Adding binary /lib/firmware/radeon/CAYMAN_me.bin
Adding firmware radeon/CAYMAN_me.bin
Adding binary /lib/firmware/radeon/CAYMAN_pfp.bin
Adding firmware radeon/CAYMAN_pfp.bin
Adding binary /lib/firmware/radeon/CAICOS_mc.bin
Adding firmware radeon/CAICOS_mc.bin
Adding binary /lib/firmware/radeon/CAICOS_me.bin
Adding firmware radeon/CAICOS_me.bin
Adding binary /lib/firmware/radeon/CAICOS_pfp.bin
Adding firmware radeon/CAICOS_pfp.bin
Adding binary /lib/firmware/radeon/TURKS_mc.bin
Adding firmware radeon/TURKS_mc.bin
Adding binary /lib/firmware/radeon/TURKS_me.bin
Adding firmware radeon/TURKS_me.bin
Adding binary /lib/firmware/radeon/TURKS_pfp.bin
Adding firmware radeon/TURKS_pfp.bin
Adding binary /lib/firmware/radeon/BTC_rlc.bin
Adding firmware radeon/BTC_rlc.bin
Adding binary /lib/firmware/radeon/BARTS_mc.bin
Adding firmware radeon/BARTS_mc.bin
Adding binary /lib/firmware/radeon/BARTS_me.bin
Adding firmware radeon/BARTS_me.bin
Adding binary /lib/firmware/radeon/BARTS_pfp.bin
Adding firmware radeon/BARTS_pfp.bin
Adding binary /lib/firmware/radeon/VERDE_rlc.bin
Adding firmware radeon/VERDE_rlc.bin
Adding binary /lib/firmware/radeon/VERDE_mc.bin
Adding firmware radeon/VERDE_mc.bin
Adding binary /lib/firmware/radeon/VERDE_ce.bin
Adding firmware radeon/VERDE_ce.bin
Adding binary /lib/firmware/radeon/VERDE_me.bin
Adding firmware radeon/VERDE_me.bin
Adding binary /lib/firmware/radeon/VERDE_pfp.bin
Adding firmware radeon/VERDE_pfp.bin
Adding binary /lib/firmware/radeon/PITCAIRN_rlc.bin
Adding firmware radeon/PITCAIRN_rlc.bin
Adding binary /lib/firmware/radeon/PITCAIRN_mc.bin
Adding firmware radeon/PITCAIRN_mc.bin
Adding binary /lib/firmware/radeon/PITCAIRN_ce.bin
Adding firmware radeon/PITCAIRN_ce.bin
Adding binary /lib/firmware/radeon/PITCAIRN_me.bin
Adding firmware radeon/PITCAIRN_me.bin
Adding binary /lib/firmware/radeon/PITCAIRN_pfp.bin
Adding firmware radeon/PITCAIRN_pfp.bin
Adding binary /lib/firmware/radeon/TAHITI_rlc.bin
Adding firmware radeon/TAHITI_rlc.bin
Adding binary /lib/firmware/radeon/TAHITI_mc.bin
Adding firmware radeon/TAHITI_mc.bin
Adding binary /lib/firmware/radeon/TAHITI_ce.bin
Adding firmware radeon/TAHITI_ce.bin
Adding binary /lib/firmware/radeon/TAHITI_me.bin
Adding firmware radeon/TAHITI_me.bin
Adding binary /lib/firmware/radeon/TAHITI_pfp.bin
Adding firmware radeon/TAHITI_pfp.bin
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/acpi/video.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/gpu/drm/gma500/gma500_gfx.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/gpu/drm/r128/r128.ko
Adding binary /lib/firmware/r128/r128_cce.bin
Adding firmware r128/r128_cce.bin
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/gpu/drm/i810/i810.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/video/syscopyarea.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/video/sysfillrect.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/video/sysimgblt.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/gpu/drm/drm_usb.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/gpu/drm/udl/udl.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/gpu/drm/via/via.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/video/sis/sisfb.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/gpu/drm/sis/sis.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/gpu/drm/tdfx/tdfx.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/gpu/drm/vmwgfx/vmwgfx.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/gpu/drm/mga/mga.ko
Adding binary /lib/firmware/matrox/g400_warp.fw
Adding firmware matrox/g400_warp.fw
Adding binary /lib/firmware/matrox/g200_warp.fw
Adding firmware matrox/g200_warp.fw
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/gpu/drm/i915/i915.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/gpu/drm/i2c/ch7006.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/gpu/drm/i2c/sil164.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/gpu/drm/savage/savage.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/platform/x86/wmi.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/platform/x86/mxm-wmi.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/gpu/drm/nouveau/nouveau.ko
Adding module /lib/modules/3.5.0-26-generic/initrd/vesafb.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/video/vgastate.ko
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/video/vga16fb.ko
Calling hook fuse
Adding binary /sbin/mount.fuse
Calling hook klibc
Calling hook mountall
Calling hook thermal
Calling hook udev
Adding binary /sbin/udevd
Adding binary /sbin/udevadm
Adding binary /lib/udev/firmware
Adding binary /lib/udev/ata_id
Adding binary /sbin/blkid
Adding binary /lib/udev/scsi_id
Calling hook lupin_casper
Calling hook cryptpassdev
Calling hook cryptopensc
Calling hook cryptopenct
Calling hook cryptkeyctl
Calling hook cryptgnupg
Calling hook plymouth
Adding binary /sbin/plymouthd
Adding library /lib/libply-splash-core.so.2
Adding library /lib/i386-linux-gnu/libm.so.6
Adding binary /bin/plymouth
Adding binary /lib/plymouth/details.so
Adding binary /lib/plymouth/ubuntu-text.so
Adding binary /lib/plymouth/script.so
Adding library /lib/libply-splash-graphics.so.2
Adding library /lib/i386-linux-gnu/libpng12.so.0
Adding library /lib/i386-linux-gnu/libz.so.1
Adding binary /lib/plymouth/label.so
Adding library /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0
Adding library /usr/lib/i386-linux-gnu/libpango-1.0.so.0
Adding library /usr/lib/i386-linux-gnu/libcairo.so.2
Adding library /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
Adding library /lib/i386-linux-gnu/libglib-2.0.so.0
Adding library /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0
Adding library /usr/lib/i386-linux-gnu/libfreetype.so.6
Adding library /usr/lib/i386-linux-gnu/libfontconfig.so.1
Adding library /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0
Adding library /usr/lib/i386-linux-gnu/libpixman-1.so.0
Adding library /usr/lib/i386-linux-gnu/libxcb-shm.so.0
Adding library /usr/lib/i386-linux-gnu/libxcb-render.so.0
Adding library /usr/lib/i386-linux-gnu/libxcb.so.1
Adding library /usr/lib/i386-linux-gnu/libXrender.so.1
Adding library /usr/lib/i386-linux-gnu/libX11.so.6
Adding library /usr/lib/i386-linux-gnu/libffi.so.6
Adding library /lib/i386-linux-gnu/libpcre.so.3
Adding library /lib/i386-linux-gnu/libexpat.so.1
Adding library /usr/lib/i386-linux-gnu/libXau.so.6
Adding library /usr/lib/i386-linux-gnu/libXdmcp.so.6
Adding binary /lib/i386-linux-gnu/libnss_files-2.15.so
Adding binary /lib/i386-linux-gnu/libnss_files.so.2
Adding binary /lib/plymouth/renderers/frame-buffer.so
Adding binary /lib/plymouth/renderers/drm.so
Adding library /usr/lib/i386-linux-gnu/libdrm_intel.so.1
Adding library /usr/lib/i386-linux-gnu/libdrm_radeon.so.1
Adding library /usr/lib/i386-linux-gnu/libdrm_nouveau.so.1
Adding library /usr/lib/i386-linux-gnu/libdrm.so.2
Adding library /usr/lib/i386-linux-gnu/libkms.so.1
Adding library /usr/lib/i386-linux-gnu/libpciaccess.so.0
Adding binary /lib/plymouth/renderers/vga16fb.so
Calling hook ntfs_3g
Adding binary /bin/ntfs-3g
Adding library /lib/i386-linux-gnu/libfuse.so.2
Adding library /lib/i386-linux-gnu/libntfs-3g.so.835
Calling hook console_setup
Calling hook kbd
Adding binary /bin/setfont
Adding binary /bin/kbd_mode
Adding binary /bin/loadkeys
Calling hook busybox
Adding binary /usr/lib/initramfs-tools/bin/busybox
Calling hook watershed
Adding binary /lib/udev/watershed
Calling hook lvm2
Adding binary /sbin/lvm
Adding library /lib/i386-linux-gnu/libdevmapper-event.so.1.02.1
Adding library /lib/i386-linux-gnu/libreadline.so.5
Adding library /lib/i386-linux-gnu/libtinfo.so.5
Adding module /lib/modules/3.5.0-26-generic/kernel/drivers/md/dm-snapshot.ko
Calling hook kpartx
Adding binary /sbin/kpartx
Adding binary /lib/udev/dmsetup_env
Adding binary /lib/udev/kpartx_id
Calling hook dmsetup
Building cpio /boot/initrd.img-3.5.0-26-generic.new initramfs

```

---

### Post by matt_symes on 2013-04-05
Hi

From your last post.

> Building cpio /boot/initrd.img-3.5.0-26-generic.new initramfs

This above is the last stage in creating the initramfs.

Here is mine running the same command and this completed.

```
Calling hook dmsetup
Building cpio /boot/initrd.img-3.9.0-030900rc5-generic.new initramfs
matthew-S206:/home/matthew % 

```

So did that last command you typed hang or did it run to completion and take you to the command prompt ? I cannot tell from the output you posted.

Can you post the output of

```
ls -l /boot/initrd*
```

Kind regards

---

### Post by Darkishjace on 2013-04-05
yes it did hang and still is currently hanging should i run ```
[COLOR=#000000][FONT=Ubuntu Mono]ls -l /boot/initrd*
``` rightnow or what should i do[/FONT][/COLOR]

---

### Post by matt_symes on 2013-04-05
Hi

Excellent. We knows it's definitely update-initramfs that is failing.

Let's see if we can get more info as to why.

Keep update-initramfs running in that terminal.

Open a second terminal and type

```
sudo apt-get install psmisc
```

If it's already installed then that's no problem; that's fine because we'll need it in a moment.

Next type (in the second terminal).

```
ps aux | grep initramfs
```

You'll get some output like this.

```
root     **31572**  0.5  0.0  80696  2652 pts/17   S+   03:13   0:00 **sudo** update-initramfs -v -c -k 
```

You may get a couple of entries back. Look for the one with sudo in it like i have highlighted above.

Then type

```
pstree -p XXXX
```

where XXXX is the second number you get from the last command above (that i highlighted in bold above).

In my case it would be *pstree -p 31572*. Change yours as required.

Post back the tree drawn here.

Hopefully that will give more info so to where it's hanging. If not we'll try htop and it's tree view.

Kind regards

---

### Post by Darkishjace on 2013-04-05
```
lubuntu@lubuntu:~$ sudo apt-get install psmisc
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
lubuntu@lubuntu:~$
```

---

### Post by Darkishjace on 2013-04-05
```
lubuntu@lubuntu:~$ ps aux | grep initramfs 

root     10922  0.0  0.1   7852   980 pts/4    S+   18:53   0:00 sudo update-initramfs -v -c -k 3.5.0-26-generic
root     10923  0.0  0.0   2232   376 pts/4    S+   18:53   0:00 /bin/sh /usr/sbin/update-initramfs -v -c -k 3.5.0-26-generic
lubuntu  20819  0.0  0.1   4644   816 pts/2    S+   20:38   0:00 grep --color=auto initramfs

lubuntu@lubuntu:~$ pstree -p 10922
sudo(10922)&#9472;&#9472;&#9472;update-initramf(10923)&#9472;&#9516;&#9472;gzip(20248)
                                     &#9492;&#9472;lzma(20249) 

lubuntu@lubuntu:~$
```

---

### Post by matt_symes on 2013-04-05
Hi

I was hoping for more info than that but that may be all there is.

I am looking through the scripts that create the initramfs file.

I'll post back soon.

Kind regards

---

### Post by Bashing-om on 2013-04-05
still here and now this has turned into a learning thing for me also.

---

### Post by matt_symes on 2013-04-06
Hi

update-initramfs and mkinitramfs are both scripts. 

What they do is copy kernel modules, copy and run other scripts stored in other directories and hooks and a number of other things and then generate a compressed archive.

This archive is the initrd file that becomes the early root filing system.

> Building cpio /boot/.....

From what you posted earlier it seems to be getting far enough to generate the cpio (this is the archive). 

The files are copied into the directory /tmp and the cpio archive is generated and then rename in your /boot directory.

From mkinitramfs

```

[ "${verbose}" = y ] && echo "Building cpio ${outfile} initramfs"
(
# work around lack of "set -o pipefail" for the following pipe:
# cd "${DESTDIR}" && find . | cpio --quiet -R 0:0 -o -H newc | gzip >"${outfile}" || exit 1
exec 3>&1
eval `  
        # http://cfaj.freeshell.org/shell/cus-faq-2.html
        exec 4>&1 >&3 3>&-
        cd  "${DESTDIR}"
        {
                find . 4>&-; echo "ec1=$?;" >&4
        } | {   
                cpio --quiet -R 0:0 -o -H newc 4>&-; echo "ec2=$?;" >&4
        } | ${compress} >"${outfile}"
        echo "ec3=$?;" >&4
`
<snip>
if [ -s "${__TMPCPIOGZ}" ]; then
        cat "${__TMPCPIOGZ}" >>"${outfile}" || exit 1
fi

```

I'm wondering if something odd is happening around here for some reason.

Can you post the output of

```
ls /tmp/mkinitramfs_*
```

```
find /tmp/mkinitramfs_* ! -type d -exec ls -lh {} \; > ~/tmp.txt
```

This second command will produce a file in your home directory called tmp.txt. Please post that as an attachment to your next post.

```
df -h
```

```
mount
```

```
which cpio
```

```
which lzma
```

```
sudo du -csh /tmp
```

```
ls /var/lib/initramfs-tools
```

and finally

```
ls /boot/initrd*
```

Let's see if we can work out what is going on.

> when i installed Lubuntu i had issues with mounting my harddrive and had  to input a code to create the folder for it to beable to mount idk if  their is any other folders i might happen to be missing wich might be  the cause of all my woes

Can you explain exactly what you did here please.

Kind regards

---

### Post by Darkishjace on 2013-04-06
k so heres the first part wich looks like a huge problem to me 
 ```
lubuntu@lubuntu:~$ ls /tmp/mkinitramfs_*  
ls: cannot access /tmp/mkinitramfs_*: No such file or directory 
lubuntu@lubuntu:~$ find /tmp/mkinitramfs_* ! -type d -exec ls -lh {} \; > ~/tmp.txt 
find: `/tmp/mkinitramfs_*': No such file or directory 
lubuntu@lubuntu:~$  



```

---

### Post by Darkishjace on 2013-04-06
the answer to your question highlighted by my quote is i used the mkdir command to make media/lubuntu (i think that was the one) and it fixed my problem with being unable to load any of the other drives i had dvd/1tb harddrive and various flash drives

the drive i have my lubuntu operating system on is a 8gb kingston flashdrive

---

### Post by Darkishjace on 2013-04-06
heres the second one 
```
 
lubuntu@lubuntu:~$ dh -h dh: No compatibility level specified in debian/compat 
dh: This package will soon FTBFS; time to fix it! 
Usage: dh [options] 


  dh is a part of debhelper. See debhelper(7) 
  and dh(1) for complete usage instructions. 
lubuntu@lubuntu:~$ mount 
/cow on / type overlayfs (rw) 
proc on /proc type proc (rw,noexec,nosuid,nodev) 
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev) 
udev on /dev type devtmpfs (rw,mode=0755) 
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620) 
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755) 
/dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro) 
/dev/loop0 on /rofs type squashfs (ro,noatime) 
none on /sys/fs/fuse/connections type fusectl (rw) 
none on /sys/kernel/debug type debugfs (rw) 
none on /sys/kernel/security type securityfs (rw) 
tmpfs on /tmp type tmpfs (rw,nosuid,nodev) 
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880) 
none on /run/shm type tmpfs (rw,nosuid,nodev) 
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755) 
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev) 
gvfsd-fuse on /run/user/lubuntu/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu) 
/dev/sr0 on /media/lubuntu/WNDA3100v2 type iso9660 (ro,nosuid,nodev,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks2) 
/dev/sda1 on /media/lubuntu/1.0 TB Hard Disk type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096) 
lubuntu@lubuntu:~$ which cpio 
/bin/cpio 
lubuntu@lubuntu:~$ which lzma 
/usr/bin/lzma 
lubuntu@lubuntu:~$ sudo du -csh /tmp 
16K	/tmp 
16K	total 
lubuntu@lubuntu:~$ ls /var/lib/initramfs-tools 
3.5.0-17-generic  3.5.0-26-generic 
lubuntu@lubuntu:~$ ls /boot/initrd* 
/boot/initrd.img-3.5.0-17-generic  /boot/initrd.img-3.5.0-26-generic 
lubuntu@lubuntu:~$ 

```

---

### Post by Darkishjace on 2013-04-06
now i have no clue exactly how to add a attachment to this forum matter but when i open with both abiword and leafpad 
tmp.txt comes up empty i dont know if im using the wrong program to read it or if its supposed to be empty or if by chance nothing is writing in it 
also that process that was running was hanging up until now till i accidentally clicked close tab instead of clicking copy to show the last line here 
-.- i feel like an idiot

---

### Post by Bashing-om on 2013-04-06
Darkishjace; I am back.

This has progressed beyond my level of comprehension. I do not know what Matt is looking for exactly. But to ease your mind;
> 

lubuntu@lubuntu:~$ ls /tmp/mkinitramfs_* 
  ls: cannot access /tmp/mkinitramfs_*: No such file or directory 
Those files do not exist either on my system and is the reason that tmp.txt is not written to.
Await Matt's advise on if "mkinitramfs" files are removed upon completion of the scripts, or perhaps looking in the wrong directory ? IDK ![INDENT=3]
awaiting to learn 
[/INDENT]

---

### Post by Darkishjace on 2013-04-06
k and im also back

---

### Post by Bashing-om on 2013-04-06
Never mind, my thought was miss directed, back to studying this situation.

---

### Post by Darkishjace on 2013-04-06
:P u find wich the problem might infact be

---

### Post by Darkishjace on 2013-04-06
i honestly thought that might be the part where things may be going wrong

---

### Post by Bashing-om on 2013-04-06
What I "think" is going on is that initramfs is awaiting one of the scripts to complete that is not ...so hanging up.

@ Matt; - in my role as a back seat driver ->
Will this lead to anything productive in finding that script ?
```

**[B]DEBUG**[/B]
       It  is  easy  to check the generated initramfs for its content. One may
need to double-check if it contains  the  relevant  binaries,  libs  or  modules:
mkdir tmp/initramfs
cd tmp/initramfs
gunzip -c /boot/initrd.img-2.6.18-1-686 | \
cpio -i -d -H newc --no-absolute-filenames 
```

Do we at this point even have a "generated initramfs" ?[INDENT]
remains in a study over this issue

[/INDENT]

---

### Post by Darkishjace on 2013-04-06
i tried the first line 
```
[COLOR=#000000][FONT=Ubuntu Mono]mkdir tmp/initramfs [/FONT][/COLOR]
``` 
and this is what came back 
```
lubuntu@lubuntu:~$ mkdir tmp/initramfs 
mkdir: cannot create directory `tmp/initramfs': No such file or directory
lubuntu@lubuntu:~$ 

``` 
i also tried it as a sudo and same results

---

### Post by Darkishjace on 2013-04-06
im hoping matt didnt give up on us i had messaged him a lil while ago noticing he was online because i think the two of you can get down to the bottom of this quickly by brainstorming

---

### Post by Bashing-om on 2013-04-06
Darkishjace;
That "code" is but a template and to apply it one would make adjustments to a given environment/intent.

This is a knotty situation and, Matt I bet, is at the very least thinking about where to go from last ( as I also am looking  ); soonest that he has something constructive to offer he will respond. Prompting will not induce a response sooner, leave him to think undistracted. 

We are working a number of different threads and going from one to another as time permits, devoting effort to each.
For me yours remains the more active.
[INDENT=2]
it is a puzzle 
[/INDENT]
[INDENT]


[/INDENT]

---

### Post by matt_symes on 2013-04-06
Hi

> **Darkishjace said:**
> k so heres the first part wich looks like a huge problem to me 
 ```
lubuntu@lubuntu:~$ ls /tmp/mkinitramfs_*  
ls: cannot access /tmp/mkinitramfs_*: No such file or directory 
lubuntu@lubuntu:~$ find /tmp/mkinitramfs_* ! -type d -exec ls -lh {} \; > ~/tmp.txt 
find: `/tmp/mkinitramfs_*': No such file or directory 
lubuntu@lubuntu:~$ 

```

The temp directories are deleted after the initramfs is created and that is why they are not there.

> **Darkishjace said:**
> 
lubuntu@lubuntu:~$ ls /var/lib/initramfs-tools 
3.5.0-17-generic  3.5.0-26-generic 

lubuntu@lubuntu:~$ ls /boot/initrd* 
/boot/initrd.img-3.5.0-17-generic  **/boot/initrd.img-3.5.0-26-generic **
lubuntu@lubuntu:~$ 
[/CODE]

The initramfs has been created as well so it did complete.

This is really odd as it looks to be completing quite quickly; certainly not taking 2 days.

Everything looks fine from here so can we actually time this please.

Open a terminal and type (or copy and paste)

```
time sudo update-initramfs -c -k 3.5.0-26-generic
```

When it finishes (and please leave it to finish) then please post the output back here.

When it has hung can you take a photo of the terminal and add as an attachment here.

@bashing-om. Could you please explain to the OP how to add an attachment as i have to pop out for a while.

Kind regards

---

### Post by Bashing-om on 2013-04-06
@Darkishjace;
To add an attachment:
have what you intend to attach ready. and just use the paper clip icon at the top of a current posting, click on "Add Files" in the pop-up window, -> Select Files ->your system's files -> browse to location, then click on the file you want uploaded. Drag that files name in the original Attachment window from an upper pane to the lower pane.
[INDENT=2]
I is back to googl'n and look'n

[/INDENT]

---

### Post by Darkishjace on 2013-04-06
[ATTACH=CONFIG]241023[/ATTACH]

---

### Post by Darkishjace on 2013-04-06
btw its been a hour since i took that pic

---

### Post by matt_symes on 2013-04-06
Hi

Is your hard drive or any partitions encrypted ?

Can you post the out

```
sudo blkid
```

```
ls -l /dev/disk/by-uuid/*
```

```
cat /etc/fstab
```

Kind regards

---

### Post by Darkishjace on 2013-04-06
i dont think any of my harddrives or partitions are encrypted. 
```
**lubuntu@lubuntu:~$ sudo blkid** /dev/loop0: TYPE="squashfs" 
/dev/loop1: LABEL="casper-rw" UUID="71de3610-91a8-6648-ab10-ca7e1bc74934" TYPE="ext2" 
/dev/sda1: LABEL="1.0 TB Hard Disk" UUID="51130ACB140FCB0D" TYPE="ntfs" 
/dev/sda2: UUID="f2f58d4d-4688-4f32-9704-b9a35f17f85e" TYPE="swap" 
/dev/sr0: LABEL="WNDA3100v2" TYPE="iso9660" 
/dev/sdb1: LABEL="PENDRIVE" UUID="1501-1049" TYPE="vfat" 
**lubuntu@lubuntu:~$ ls -l /dev/disk/by-uuid/*** 
lrwxrwxrwx 1 root root 10 Apr  5 20:06 /dev/disk/by-uuid/1501-1049 -> ../../sdb1 
lrwxrwxrwx 1 root root 10 Apr  5 20:06 /dev/disk/by-uuid/51130ACB140FCB0D -> ../../sda1 
lrwxrwxrwx 1 root root 11 Apr  5 20:06 /dev/disk/by-uuid/71de3610-91a8-6648-ab10-ca7e1bc74934 -> ../../loop1 
lrwxrwxrwx 1 root root 10 Apr  5 20:06 /dev/disk/by-uuid/f2f58d4d-4688-4f32-9704-b9a35f17f85e -> ../../sda2 
**lubuntu@lubuntu:~$ cat /etc/fstab** 
overlayfs / overlayfs rw 0 0 
tmpfs /tmp tmpfs nosuid,nodev 0 0 
/dev/sda2 swap swap defaults 0 0 
lubuntu@lubuntu:~$ 

```

---

### Post by matt_symes on 2013-04-06
Hi

ahhh. I think the penny may be beginning to finally drop.

You're running Lubuntu from a pen (flash) drive (storage) ?

The hard drive is for storage ?

How are you booting Lubuntu ? What PC (or other hardware) are you using to boot Lubuntu ?

Can you please explain your exact setup. Y9ou did not install onto the flash but copied a bootable iso ?

I'm not sure exactly what is causing the problem but knowing exactly what you are doing may shed some light on your problem.

Another question, how long have you had this hanging issue ? Since from when you first install Lubuntu ?

Since from when you had your first kernel update ? (i notice you have only had one).

I did notice the crypo message in the verbose output of update-initramfs but i did not think much of it as execution still continued. We can take a look at fixing it but i'm not sure it's the main cause of your problem.

Do you have the instructions you followed to install Lubuntu ?

Please supply as much information as possible. Supply even information you think is irrelevant.

Your problem has been perplexing me and i would love to be able to get to the bottom of it (if i can).

I'll take a more detailed look at the output from your last post but i may be away from keyboard for 15 hours or so.

Kind regards

---

### Post by Bashing-om on 2013-04-06
Eagerly awaiting response also. I have literally spent the day chasing my tail on this one, to little avail, just a dim possibility.
[INDENT=4]
still hang'n in there

[/INDENT]

---

### Post by Darkishjace on 2013-04-06
for the answer of your question of what meens did i install my distro of lubuntu i used [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/) i used it to install my first distro i used lucid puppy linux and when i switched i used it to run Ubuntu 10 which at a later date updated to Ubuntu 12 which made it unusable for my computer due to being unable to reach the requirements necessary so i switched to Lubuntu because i was told that every computer can run it and its only been till ive been using lubuntu that ive had to use terminal to do everything that ive wanted to (lubuntu software center doesnt have everything i used on both ubuntu 10 and puppy linux)

---

### Post by Darkishjace on 2013-04-06
as for which computer im using its a Dell OptiPlex GX620 with a Pentium 4 Processor and 512 MB Ram thats as far as i can remember im pretty sure the only thing that would be different is i replaced the drive in it that died and replaced it with the 1tb drive from my external hardrive set up (the technology running the drive crapped out but the drive its self still works Perfect)

---

### Post by Bashing-om on 2013-04-07
update: spinning my wheels and getting nowhere !
Continue to look for a method to de-bug the initramfs to understand what is happening. I often get side tracked and must refocus to this intriguing situation. Exploring feasibilities of new thoughts takes time.

I have nothing to add at this time.[INDENT=4]
a learning experience

[/INDENT]

---

### Post by steeldriver on 2013-04-07
been following this thread but not able to add anything of value - however I just came across this bug report which seems to share the same symptom

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/932663](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/932663)

> P.S. Running "sudo update-initramfs -u" produces the same symptoms for this installation as for 12.04.
That is, it displays the following two warning messages:
   cryptsetup: WARNING: failed to detect canonical device of overlayfs
   cryptsetup: WARNING: could not determine root device from /etc/fstab
and then seems to lock up (I needed to Ctrl+C out of it, although I  suppose it's possible that it was doing something, only really slowly).

I don't know whether it's relevant though since it's not clear whether it should only apply to non-persistent installations - and I don't know how overlayfs works

---

### Post by Bashing-om on 2013-04-07
@ steeldriver Thanks much (for all) I had not seen that report. // I have seen an advisory that updating "casper" might have an effect.
Presently engaged in looking for a method to log what initramfs is doing at the system level; I have seen some hints that it is possible, just don't have my head wrapped around it yet.

Hey, I am progressing from a general knowledge and getting specific !
[INDENT=4]
think'n, look'n anda search'n -> ain't ubuntu wonderful 
[/INDENT]

---

### Post by Darkishjace on 2013-04-07
Thankyou everyone for still beleiving that this is a fixable problem you've given me hope that i can still come out on top and have a normal working lubuntu distro 
the terminal i started running the other day finally finished in my sleep and here it is 
```
lubuntu@lubuntu:~$ time sudo update-initramfs -c -k 3.5.0-26-generic 
update-initramfs: Generating /boot/initrd.img-3.5.0-26-generic 
cryptsetup: WARNING: failed to detect canonical device of overlayfs 
cryptsetup: WARNING: could not determine root device from /etc/fstab 
 
real    1131m32.802s 
user    3m10.652s 
sys    9m45.597s 
lubuntu@lubuntu:~$ 

```

---

### Post by Darkishjace on 2013-04-07
Thankyou everyone for still beleiving that this is a fixable problem you've given me hope that i can still come out on top and have a normal working lubuntu distro 
the terminal i started running the other day finally finished in my sleep and here it is 
```
lubuntu@lubuntu:~$ time sudo update-initramfs -c -k 3.5.0-26-generic 
update-initramfs: Generating /boot/initrd.img-3.5.0-26-generic 
cryptsetup: WARNING: failed to detect canonical device of overlayfs 
cryptsetup: WARNING: could not determine root device from /etc/fstab 
 
real    1131m32.802s 
user    3m10.652s 
sys    9m45.597s 
lubuntu@lubuntu:~$ 

```

---

### Post by matt_symes on 2013-04-07
Hi

> **steeldriver said:**
> [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/932663](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/932663)


Very, very interesting find steeldriver. That was a bug i was not aware of.

In this case i'm not sure it's the problem as

```
sudo update-initramfs ...
```

should not call update-grub.

 Let's check though. Assumptions are the mother of all ....

@OP. Can you post back the output of

```
time sudo update-grub
```

Please post back results and the results of

```
grep "3.5.0-26-generic" /boot/grub/grub.cfg
```

The only other thing i can think of is the checksum.

Can you post the output of

```
sudo strace -o ~/tmp.txt  update-initramfs -c -k 3.5.0-26-generic
```

That will create a file called tmp.txt in your home directory when it has finished. Please let it finish.

Check how large it is and please post the last ~200 lines.

I'm really open every suggestions here.

Kind regards

---

### Post by Bashing-om on 2013-04-07
Darkishjace; Well, "update-initramfs" did complete !
I think Matt would want to know if the system updates now. Let's see.
```
sudo apt-get update
sudo apt-get upgrade
``` Post back with any errors.
We are not out of the woods yet... the "cryptsetup Warning" is cause for concern.[INDENT=2]
try'n

[/INDENT]

---

### Post by Darkishjace on 2013-04-07
```
lubuntu@lubuntu:~$ time sudo update-grub/usr/sbin/grub-probe: error: failed to get canonical path of /cow.


real    0m0.749s
user    0m0.020s
sys    0m0.168s
lubuntu@lubuntu:~$ 

``` 
```
lubuntu@lubuntu:~$ grep "3.5.0-26-generic" /boot/grub/grub.cfggrep: /boot/grub/grub.cfg: No such file or directory
lubuntu@lubuntu:~$ 

```

---

### Post by matt_symes on 2013-04-07
Hi

@bashing-om. The only thing that worries me is ....

> real    1131m32.802s  
user    3m10.652s 
 sys 9m45.597s  lubuntu@lubuntu:~$

Kind regards

---

### Post by matt_symes on 2013-04-07
Hi

@OP

```
sudo strace -o ~/tmp.txt  update-initramfs -c -k 3.5.0-26-generic
```

Left it finish and then post the last ~ 200 lines of ~/tmp.txt.

Kind regards

---

### Post by Bashing-om on 2013-04-07
@ Matt : correlation of update-initramfs and grub :

Getting deeper, and I personally do not comprehend this, you may and it may shed some light on what you related earlier in this regard.

from:[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/957262](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/957262) 

> update-initramfs: Generating /boot/initrd.img-3.2.0-18-generic
[...]
 So the grub update knows to take care of replacing the /etc/kernel-img.conf  line with a proper /etc/kernel hook, but then nothing ensures this is  called after the kernel upgrade.  The kernel postinst calls update-grub  too early, and it's not called again after upgrade.
 We should probably just have grub call update-grub in the postinst when the upgrade handling is triggered.
//

grub (0.97-29ubuntu66) precise; urgency=low
   * When we replace the /etc/kernel-img.conf hook with the
    /etc/kernel/postinst.d hook on upgrade, also call update-grub manually;
    otherwise if the kernel was upgraded before grub itself, update-grub may
    only be called before update-initramfs (due to triggerization of the
    latter), giving us an unbootable default entry in menu.lst.
    LP: [#957262]("https://bugs.launchpad.net/bugs/957262").

still looking at hooks.

---

### Post by Darkishjace on 2013-04-07
im currently in the middle of sectioning off my 1tb hard drive to have a 8 gb partition (for a new on harddrive installation of lubuntu) and a 50 gb partition for windows xp partition i started these this morning before i went to bed approx 16 hours ago because i was feeling hopeless in fixing the problems with my lubuntu on my flashdrive are the problems possibly caused by either the method or tool i used to install lubuntu on the flash drive would installing it from the program that came with lubuntu onto my soon to be new partition i started when i was giving up hope on my flashdrive or when its done should i just clear the 8gb partition and continue using the flashdrive

---

### Post by Darkishjace on 2013-04-07
i intially when started using linux was using lucid puppy linux to correct problems in my windows xp then gradually went into using ubuntu as my main operating system and when ubuntu became too complicated for my computer to use and my xp crashed i fully switched to lubuntu what i was feeling this morning when i felt i lost hope in using lubuntu fulltime as my all around operating system is that i could install windows xp onto a separate partition on my 1tb drive and also install lubuntu onto the drive also but in its own partition aswell what im wondering is can lubuntu actually become this great thing i hoped it to be and break past all these issues ive discovered along the way and become my only operating system or should i just use it as i planned this morning as my internet using/movie viewing operating system and have xp as my games system i need everyones feedback please thankyou very much

---

### Post by Bashing-om on 2013-04-07
Darkishjace;

Installing to the hard drive is preferred.. will be much faster (usb speed on pendrive)... However only 8 gigis ( symlink to a data partition ?)  for lubuntu will give you little overhead for any additions or storing of any data... most install recommends is 30 gigs for a fully functioning operating system.
You still only have 512 MB of ram... is the board fully populated with ram chips ? -> the more ram the better !

Your current problems are not hardware related.

When you do install lubuntu to hard disk, do so as a "clean" install from a verified install media. Thus the current problems are not carried over to the new install. Carefully and selectively add back in any 3rd party software ! (hint: I run 3 machines, none have any 3rd party software installed, and none have ever had a single problem). Windows wants to be in the first partition and installed prior to install 'buntu.
When 'buntu is installed make sure that grub installs to sda (NOT to any partition like sda1) and grub will pick up the windows system and chainload the bootloader to give you the choice of which system to boot.

'buntu as only operating system: I can only give you my experience - your needs will vary -; I left Windows behind about 5 years ago and have never looked back ( my back ground however was in open source - Motorolla - and gradually gravitated to ubuntu -AMD) .
Ubuntu is the answer to everything I want and expect in my operating system and is by far my operating system of choice.

It all depends on what you want out of your computer; As in all things you only get out of something what you put in to it ! Put into programming's analogy => garbage in, garbage out .
[INDENT=2]
this is my humble opinion

[/INDENT]

---

### Post by matt_symes on 2013-04-10
Hi

Was your USB stick install a persistent USB install ? I.E did it have persistent storage area ?

A hard drive install is the method you should really use or create a USB stick install with persistent storage.

I think this was the issue.

Kind regards

---

