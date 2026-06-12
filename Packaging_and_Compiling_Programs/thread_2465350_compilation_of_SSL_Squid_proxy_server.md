---
title: "compilation of SSL Squid proxy server"
date: 2021-07-30
forum: Packaging and Compiling Programs
---

### Post by jobe77x on 2021-07-30
Hi all!

I hope  that I'm in the right forum.
I've just finished following the instructions from this site: [https://techexpert.tips/squid/install-squid-with-https-ssl-decryption-ubuntu-linux/](https://techexpert.tips/squid/install-squid-with-https-ssl-decryption-ubuntu-linux/) Except I used 4.16. instead of 4.5 in the article.

Now, I'm a first time "compiler", and I didn't see anything alarming during the compilation (a lot of text scrolling fast), but I found out at the end that squid never got installed, and I can't find any packages.

Anybody knows what to do next?
where to see what went wrong?

I'm running Ubuntu server 18.04LTS

---

### Post by SeijiSensei on 2021-07-30
First, before you can compile something you need to download the source code that connects your package to the various libraries it needs to use (so-called "dependencies").  On Ubuntu that is easily accomplished by running the command:
```
sudo apt update; sudo apt-get build-dep squid
```
Now go to the directory where the source code is stored and run "sudo make clean".  This should remove any remnant of your earlier attempts. Then run "./configure" and look carefully at what it reports. Does it mention any missing libraries or other code?

---

### Post by jobe77x on 2021-07-30
> **SeijiSensei said:**
> Does it mention any missing libraries or other code?



I just tested, and there was a lot of "no":
```

checking for dlltool... no
checking for sysroot... no
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dld_link in -ldld... no
checking for _ prefix in compiled symbols... no
checking for dl.h... no
checking for sys/dl.h... no
checking for dld.h... no
checking for mach-o/dyld.h... no
checking for strlcat... no
checking for strlcpy... no
checking for dld_link in -ldld... (cached) no
checking whether to support eCAP... no, implicitly
checking for windows.h... no
checking for sys/sockio.h... no
checking for net/if_dl.h... no
checking for sys/sysctl.h... no
checking for MD5Init in -lmd5... no
checking for SSL_CTX_set_tmp_rsa_callback in -lssl... no
checking for krb5_get_err_text in -lkrb5... no
checking for krb5_free_error_string in -lkrb5... no

checking for krb5_get_max_time_skew in -lkrb5... no
checking for krb5_principal_get_realm in -lkrb5... no
checking mozldap/ldap.h usability... no
checking mozldap/ldap.h presence... no
checking for mozldap/ldap.h... no
checking for Sun LDAP SDK... no
checking for Mozilla LDAP SDK... no
checking for LDAP_REBINDPROC_CALLBACK... no
checking for LDAP_REBIND_FUNCTION... no
checking for ldapssl_client_init in -lldap... no
checking sys/event.h usability... no
checking sys/event.h presence... no
checking for sys/event.h... no
checking for kqueue... no
configure: enabling kqueue for net I/O: no
checking sys/devpoll.h usability... no
checking sys/devpoll.h presence... no
checking for sys/devpoll.h... no
configure: Leak Finder enabled: no
checking winldap.h usability... no
checking winldap.h presence... no
checking for winldap.h... no
checking sasl.h usability... no
checking sasl.h presence... no
checking for sasl.h... no
checking for smbclient... no
configure: Basic auth helper SMB_LM ... found but cannot be built
checking w32api/windows.h usability... no
checking w32api/windows.h presence... no
checking for w32api/windows.h... no
checking for windows.h... (cached) no
configure: Basic auth helper SSPI ... found but cannot be built
checking for winldap.h... (cached) no
checking for w32api/windows.h... (cached) no
configure: Negotiate auth helper SSPI ... found but cannot be built
configure: NTLM auth helper SMB_LM ... found but cannot be built
configure: NTLM auth helper SSPI ... found but cannot be built
configure: NTLM auth helpers to be built:  fake
checking machine/byte_swap.h usability... no
checking machine/byte_swap.h presence... no
checking for machine/byte_swap.h... no
checking sys/bswap.h usability... no
checking sys/bswap.h presence... no
checking for sys/bswap.h... no
checking sys/endian.h usability... no
checking sys/endian.h presence... no
checking for sys/endian.h... no
checking for bswap_16... no
checking for bswap16... no
checking for bswap_32... no
checking for bswap32... no
checking for htole16... no
checking for __htole16... no
checking for htole32... no
checking for __htole32... no
checking for le16toh... no
checking for __le16toh... no
checking for le32toh... no
checking for __le32toh... no
configure: Log daemon helpers to be built:  DB file
configure: external acl helper AD_group ... found but cannot be built
configure: external acl helper LM_group ... found but cannot be built
checking for sasl.h... (cached) no
checking for wbinfo... no
checking bstring.h usability... no
checking bstring.h presence... no
checking for bstring.h... no
checking direct.h usability... no
checking direct.h presence... no
checking for direct.h... no
checking gnumalloc.h usability... no
checking gnumalloc.h presence... no
checking for gnumalloc.h... no
checking ipl.h usability... no
checking ipl.h presence... no
checking for ipl.h... no
checking libc.h usability... no
checking libc.h presence... no
checking for libc.h... no
checking mount.h usability... no
checking mount.h presence... no
checking for mount.h... no
checking siginfo.h usability... no
checking siginfo.h presence... no
checking for siginfo.h... no
checking sys/ipc.cc usability... no
checking sys/ipc.cc presence... no
checking for sys/ipc.cc... no
checking sys/md5.h usability... no
checking sys/md5.h presence... no
checking for sys/md5.h... no
checking varargs.h usability... no
checking varargs.h presence... no
checking for varargs.h... no
checking glib.h usability... no
checking glib.h presence... no
checking for glib.h... no
checking for netinet/ipl.h... no
checking for net/pf/pfvar.h... no
checking for net/pfvar.h... no
checking for pad128_t... no
checking for upad128_t... no
checking for mtyp_t... no
checking for library containing res_init... no
checking for library containing opcom_stack_trace... no
checking for library containing strlcpy... no
checking for malloc in -lgnumalloc... no
checking for main in -lmalloc... no
checking for sin6_len field in struct sockaddr_in6... no
checking for ss_len field in struct sockaddr_storage... no
checking for sin_len field in struct sockaddr_in... no
checking for eui64_aton... no
checking for mallocblksize... no
checking for mstats... no
checking for pthread_sigmask... no
checking for res_init... no
checking whether InetNtopA is declared... no
checking whether InetPtonA is declared... no
checking mswsock.h usability... no
checking mswsock.h presence... no
checking for mswsock.h... no
checking if strnstr is well implemented... no
checking for regexec in -lregex... no
checking for libresolv _dns_ttl_ hack... no
checking for _res_ext.nsaddr_list... no
checking for _res._u._ext.nsaddrs... no
checking for _res.ns_list... no
 Warning samba snbclient not found...  basic_smb_auth  may not work on this machine
Warning wbinfo  not found...  ext_wbinfo_group_acl  may not work on this machine
```

---

### Post by jobe77x on 2021-07-31
I've been looking around for the last 12 hours, and I'm slowly getting somewhere, it was much more complicated than I first thought, and no guide have a complete step by step description,but it was definitely dependencies that was/is the main bad guy .

---

### Post by jobe77x on 2021-07-31
Sometimes I wish there was an undo button in life...
it was an ibk error (idiot behind keyboard).. the compilation works with the right dependencies.

---

