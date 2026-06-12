---
title: "ubuntu-doesnt-install-lxc-centos-template"
date: 2021-09-20
forum: New to Ubuntu
---

### Post by it4545454545 on 2021-09-20
```
sudo lxc-create -n centos_lxc -t centos
[sudo] password for ubuntu:
Host CPE ID from /etc/os-release:
‘yum’ command is missing
lxc-create: centos_lxc: lxccontainer.c: create_run_template: 1616 Failed to create container from template
lxc-create: centos_lxc: tools/lxc_create.c: main: 319 Failed to create container centos_lxc
 sudo lxc-create -n centos_lxc -t centos
[sudo] password for ubuntu:
Host CPE ID from /etc/os-release:
‘yum’ command is missing
lxc-create: centos_lxc: lxccontainer.c: create_run_template: 1616 Failed to create container from template
lxc-create: centos_lxc: tools/lxc_create.c: main: 319 Failed to create container centos_lxc



ubuntu@primary:~$ ls /usr/share/lxc/templates/
lxc-alpine     lxc-cirros         lxc-gentoo        lxc-oracle     lxc-sparclinux
lxc-altlinux   lxc-debian         lxc-local         lxc-plamo      lxc-sshd
lxc-archlinux  lxc-download       lxc-oci           lxc-pld        lxc-ubuntu
lxc-busybox    lxc-fedora         lxc-openmandriva  lxc-sabayon    lxc-ubuntu-cloud
lxc-centos     lxc-fedora-legacy  lxc-opensuse      lxc-slackware  lxc-voidlinux
 ubuntu@primary:~$ apt list | grep lxc
 WARNING: apt does not have a stable CLI interface. Use with caution in scripts.
 golang-gopkg-lxc-go-lxc.v2-dev/focal,focal 0.0+git20190625.f4822c6-1ubuntu1 all
libclxclient-dev/focal 3.9.2-1 amd64
libclxclient3/focal 3.9.2-1 amd64
liblxc-common/focal-updates,now 1:4.0.6-0ubuntu1~20.04.1 amd64 [installed,automatic]
liblxc-dev/focal-updates 1:4.0.6-0ubuntu1~20.04.1 amd64
liblxc1/focal-updates,now 1:4.0.6-0ubuntu1~20.04.1 amd64 [installed,automatic]
libvirt-daemon-driver-lxc/focal-updates 6.0.0-0ubuntu8.14 amd64
lua-lxc/focal 1:3.0.2-1ubuntu2 amd64
lxc-dev/focal-updates,focal-updates 1:4.0.6-0ubuntu1~20.04.1 all
lxc-templates/focal,now 3.0.4-3ubuntu1 amd64 [installed]
lxc-utils/focal-updates,now 1:4.0.6-0ubuntu1~20.04.1 amd64 [installed,automatic]
lxc1/focal-updates,focal-updates 1:4.0.6-0ubuntu1~20.04.1 all
lxc/focal-updates,focal-updates,now 1:4.0.6-0ubuntu1~20.04.1 all [installed]
lxcfs/focal,now 4.0.3-0ubuntu1 amd64 [installed,automatic]
lxctl/focal,focal 0.3.1+debian-4 all
nova-compute-lxc/focal-updates,focal-updates 2:21.2.1-0ubuntu1 all
python3-lxc/focal 1:3.0.4-1ubuntu6 amd64
vagrant-lxc/focal,focal 1.4.3-1 all




```

---

### Post by grahammechanical on 2021-09-20
Are you aware that development of CentOS will stop at the end of 2021? The error message may be indicating that Ubuntu no longer is providing a CentOS image for installation in LXC. Ubuntu developers may not want to take responsibility for a distribution that is going to reach end of life 31st December 2021.

Regards

---

### Post by it4545454545 on 2021-09-20
No, I dont. I am just started to learn linux as administrator.
It could be very likely reason to stop providing template. But if u look at the errors u will see that reason seems in a bit of a side way of your idea. No yum in repo's as first error.

---

### Post by ActionParsnip on 2021-09-21
You tried to use 'yum'. Ubuntu doesn't use the yum command. As stated earlier, CentOS is dead. I suggest you switch to a supported distribution

---

### Post by grahammechanical on 2021-09-21
The information on Linux Containers says this:

> lxc comes with a special *download* template, which downloads pre-built container images from a central lxc server

[https://ubuntu.com/server/docs/containers-lxc](https://ubuntu.com/server/docs/containers-lxc)

The template for CentOS is on your system. The command you used should pull up a menu from which you choose a particular version of the distribution.

> The download template will show you a list of distributions, versions and architectures to choose from

This is not happening for you. So, you cannot even try CentOS 7 which is supported until 2023. As suggested above, try another distribution as part of learning.

Regards

---

### Post by it4545454545 on 2021-09-21
> **ActionParsnip said:**
> You tried to use 'yum'. Ubuntu doesn't use the yum command. As stated earlier, CentOS is dead. I suggest you switch to a supported distribution

please, show me the line where i v been trying "yum".
I never used it

---

### Post by it4545454545 on 2021-09-21
> **grahammechanical said:**
> The information on Linux Containers says this:



[https://ubuntu.com/server/docs/containers-lxc](https://ubuntu.com/server/docs/containers-lxc)

The template for CentOS is on your system. The command you used should pull up a menu from which you choose a particular version of the distribution.



This is not happening for you. So, you cannot even try CentOS 7 which is supported until 2023. As suggested above, try another distribution as part of learning.

Regards

I suggest you to stop it (if you know what I am saying) cuz:
sudo lxc-create -n centos_lxc -t download

with
       [TABLE="class: diff-table js-diff-table tab-size"]
[TR]
[TD="class: blob-code blob-code-context"]     

        [TABLE="class: diff-table js-diff-table tab-size"]
[TR]
[TD="class: blob-code blob-code-context"]     LXC_ROOTFS=
[/TD]
 [/TR]
        [TR]
     [/TR]
[/TABLE]
[TABLE="class: diff-table js-diff-table tab-size"]
[TR]
[TD="class: blob-code blob-code-context"]     if [ -z "${DOWNLOAD_KEYSERVER:-}" ]; then[/TD]
 [/TR]
        [TR]
     [/TR]
[/TABLE]
[TABLE="class: diff-table js-diff-table tab-size"]
[TR]
[TD="class: blob-code blob-code-deletion"]       DOWNLOAD_KEYSERVER="hkp://pool.sks-keyservers.net"[/TD]
 [/TR]
        [TR]
     [/TR]
[/TABLE]
[TABLE="class: diff-table js-diff-table tab-size"]
[TR]
[TD="class: blob-code blob-code-addition"]       DOWNLOAD_KEYSERVER="hkp://keyserver.ubuntu.com"[/TD]
 [/TR]
        [TR]
     [/TR]
[/TABLE]
[TABLE="class: diff-table js-diff-table tab-size"]
[TR]
[TD="class: blob-code blob-code-context"]     
[/TD]
 [/TR]
        [TR]
     [/TR]
[/TABLE]
[TABLE="class: diff-table js-diff-table tab-size"]
[TR]
[TD="class: blob-code blob-code-context"]       # Deal with GPG over http proxy[/TD]
 [/TR]
        [TR]
     [/TR]
[/TABLE]
[TABLE="class: diff-table js-diff-table tab-size"]
[TR]
[TD="class: blob-code blob-code-context"]       if [ -n "${http_proxy:-}" ]; then[/TD]
 [/TR]
        [TR]
     [/TR]
[/TABLE]
[TABLE="class: diff-table js-diff-table tab-size"]
[TR]
[TD="class: blob-code blob-code-deletion"]         DOWNLOAD_KEYSERVER="hkp://p80.pool.sks-keyservers.net:80"[/TD]
 [/TR]
        [TR]
     [/TR]
[/TABLE]
[TABLE="class: diff-table js-diff-table tab-size"]
[TR]
[TD="class: blob-code blob-code-addition"]         DOWNLOAD_KEYSERVER="hkp://keyserver.ubuntu.com:80"[/TD]
 [/TR]
        [TR]
     [/TR]
[/TABLE]
[TABLE="class: diff-table js-diff-table tab-size"]
[TR]
[TD="class: blob-code blob-code-context"]         DOWNLOAD_GPG_PROXY="--keyserver-options http-proxy=\"${http_proxy}\""[/TD]
 [/TR]
        [TR]
     [/TR]
[/TABLE]
[TABLE="class: diff-table js-diff-table tab-size"]
[TR]
[TD="class: blob-code blob-code-context"]       fi[/TD]
 [/TR]
        [TR]
     [/TR]
[/TABLE]
     fi[TABLE="class: diff-table js-diff-table tab-size"]
[TR]
[TD="class: blob-code blob-code-context"]
HAS WORKED OUT


close the topic
[/TD]
 [/TR]
[TR]
     [/TR]
[/TABLE]
[/TD]
 [/TR]
        [TR]
     [/TR]
[/TABLE]
[TABLE="class: diff-table js-diff-table tab-size"]
[TR]
 
[/TR]
        [TR]
     [/TR]
[/TABLE]
[TABLE="class: diff-table js-diff-table tab-size"]
[TR]

[/TR]
[TR]
[/TR]
[/TABLE]
[TABLE="class: diff-table js-diff-table tab-size"]
[TR]
[TD="class: blob-code blob-code-context"][/TD]
 [/TR]
[TR]
     [/TR]
[/TABLE]

---

