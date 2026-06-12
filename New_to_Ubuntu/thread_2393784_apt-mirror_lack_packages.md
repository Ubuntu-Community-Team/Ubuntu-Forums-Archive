---
title: "apt-mirror lack packages"
date: 2018-06-07
forum: New to Ubuntu
---

### Post by whubug on 2018-06-07
I installed a ubuntu local repo.
I used apt-mirror and with  mirror.list content
  
```
root@paasaptvlk:/etc/apt# cat mirror.list
############# config ##################
#
set base_path    /var/spool/apt-mirror
#
# set mirror_path  $base_path/mirror
# set skel_path    $base_path/skel
# set var_path     $base_path/var
# set cleanscript $var_path/clean.sh
# set defaultarch  <running host architecture>
# set postmirror_script $var_path/postmirror.sh
# set run_postmirror 0
set nthreads     20
set _tilde 0
#
############# end config ##############

deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") xenial main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") xenial-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") xenial-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") xenial-proposed main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") xenial-backports main restricted universe multiverse

deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") xenial main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") xenial-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") xenial-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") xenial-proposed main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") xenial-backports main restricted universe multiverse

clean [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") 
```

and I excute 
apt-mirror without error. the location of /var/spool/apt-mirror  is 195GB now

when I configure a client using the following sources.list
```
root@yzpaasco02vlk:/etc/apt# cat sources.list
# 

# deb cdrom:[Ubuntu-Server 16.04.4 LTS _Xenial Xerus_ - Release amd64 (20180228)]/ xenial main restricted

#deb cdrom:[Ubuntu-Server 16.04.4 LTS _Xenial Xerus_ - Release amd64 (20180228)]/ xenial main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes]("http://help.ubuntu.com/community/UpgradeNotes") for how to upgrade to
# newer versions of the distribution.
deb [http://10.21.42.160/ubuntu/]("http://10.21.42.160/ubuntu/") xenial main restricted
# deb-src [http://cn.archive.ubuntu.com/ubuntu/]("http://cn.archive.ubuntu.com/ubuntu/") xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://10.21.42.160/ubuntu/]("http://10.21.42.160/ubuntu/") xenial-updates main restricted
# deb-src [http://cn.archive.ubuntu.com/ubuntu/]("http://cn.archive.ubuntu.com/ubuntu/") xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://10.21.42.160/ubuntu/]("http://10.21.42.160/ubuntu/") xenial universe
# deb-src [http://cn.archive.ubuntu.com/ubuntu/]("http://cn.archive.ubuntu.com/ubuntu/") xenial universe
deb [http://10.21.42.160/ubuntu/]("http://10.21.42.160/ubuntu/") xenial-updates universe
# deb-src [http://cn.archive.ubuntu.com/ubuntu/]("http://cn.archive.ubuntu.com/ubuntu/") xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://10.21.42.160/ubuntu/]("http://10.21.42.160/ubuntu/") xenial multiverse
# deb-src [http://cn.archive.ubuntu.com/ubuntu/]("http://cn.archive.ubuntu.com/ubuntu/") xenial multiverse
deb [http://10.21.42.160/ubuntu/]("http://10.21.42.160/ubuntu/") xenial-updates multiverse
# deb-src [http://cn.archive.ubuntu.com/ubuntu/]("http://cn.archive.ubuntu.com/ubuntu/") xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb [http://cn.archive.ubuntu.com/ubuntu/]("http://cn.archive.ubuntu.com/ubuntu/") xenial-backports main restricted universe multiverse
# deb-src [http://cn.archive.ubuntu.com/ubuntu/]("http://cn.archive.ubuntu.com/ubuntu/") xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu]("http://archive.canonical.com/ubuntu") xenial partner
# deb-src [http://archive.canonical.com/ubuntu]("http://archive.canonical.com/ubuntu") xenial partner

deb [http://10.21.42.160/ubuntu]("http://10.21.42.160/ubuntu") xenial-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") xenial-security main restricted
deb [http://10.21.42.160/ubuntu]("http://10.21.42.160/ubuntu") xenial-security universe
# deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") xenial-security universe
deb [http://10.21.42.160/ubuntu]("http://10.21.42.160/ubuntu") xenial-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") xenial-security multiverse 
```

I excute apt-get update and then I search a pkg like this
```
root@yzpaasco02vlk:/etc/apt# apt-cache search libcurl4
python3-pycurl - Python bindings to libcurl (Python 3) 
```

however, when i configure my sources.list as default
```

root@paasaptvlk:/etc/apt# apt-cache search libcurl4
libcurl3-dbg - debugging symbols for libcurl (OpenSSL, GnuTLS and NSS flavours)
libcurl4-doc - documentation for libcurl
libcurl4-gnutls-dev - development files and documentation for libcurl (GnuTLS flavour)
libcurl4-nss-dev - development files and documentation for libcurl (NSS flavour)
libcurl4-openssl-dev - development files and documentation for libcurl (OpenSSL flavour)
python-pycurl - Python bindings to libcurl
python-pycurl-dbg - Python bindings to libcurl (debug extension)
python-pycurl-doc - Python bindings to libcurl (documentation)
python3-pycurl - Python bindings to libcurl (Python 3)
python3-pycurl-dbg - Python bindings to libcurl (debug extension, Python 3)
libwww-curl-perl - Perl bindings to libcurl
tclcurl - Tcl bindings to libcurl 
```


can anyone help me to solve this problem?

---

