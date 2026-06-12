---
title: "Troubles with amdgpu"
date: 2018-01-02
forum: New to Ubuntu
---

### Post by barbera85 on 2018-01-02
I'm struggling to get my fresh Ubuntu installation (16.04.3 LTS) working with amdgpu-pro. I've installed Ubuntu with a NVIDIA gpu installed at PCI port 1. I haven't installed any drivers for that gpu, but display worked so I guess Ubuntu did that automatically. My screen is connected to that card. Now I've installed an AMD RX 470 card to PCI port 2 and installed the amdgpu package following the installation instructions provided here: [http://support.amd.com/en-us/kb-articles/Pages/Installation-Instructions-for-amdgpu-Graphics-Stacks.aspx](http://support.amd.com/en-us/kb-articles/Pages/Installation-Instructions-for-amdgpu-Graphics-Stacks.aspx).

Sadly after a reboot Xorg doesn't start anymore. I'm getting the following error message:

```
X.Org X Server 1.19.3
Release Date: 2017-03-15
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-97-generic x86_64 Ubuntu
Current Operating System: Linux minion01 4.10.0-42-generic #46~16.04.1-Ubuntu SMP Mon Dec 4 15:57:59 UTC 2017 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.10.0-42-generic.efi.signed root=UUID=68b3a5ef-9413-47ac-99d7-ad9486493389 ro quiet splash vt.handoff=7
Build Date: 13 October 2017  02:11:50PM
[FONT=inherit]xorg-server 2:1.19.3-1ubuntu1~16.04.4 (For technical support please see [/FONT][http://www.ubuntu.com/support]("https://community.amd.com/external-link.jspa?url=http%3A%2F%2Fwww.ubuntu.com%2Fsupport")[FONT=inherit])[/FONT]
Current version of pixman: 0.33.6
[FONT=inherit]        Before reporting problems, check [/FONT][http://wiki.x.org]("https://community.amd.com/external-link.jspa?url=http%3A%2F%2Fwiki.x.org")
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan  2 22:38:01 2018
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(II) [KMS] Kernel modesetting enabled.
amdgpu_device_initialize: DRM version is 1.3.1 but this driver is only compatible with 3.x.x.
amdgpu_device_initialize: DRM version is 1.3.1 but this driver is only compatible with 3.x.x.
(EE)
(EE) Backtrace:
(EE) 0: /usr/lib/xorg/Xorg (xorg_backtrace+0x4e) [0x5633bb503a9e]
(EE) 1: /usr/lib/xorg/Xorg (0x5633bb352000+0x1b57f9) [0x5633bb5077f9]
(EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7fd058926000+0x11390) [0x7fd058937390]
(EE) 3: /opt/amdgpu/lib/x86_64-linux-gnu/libdrm_amdgpu.so.1 (amdgpu_get_marketing_name+0xc) [0x7fd05480a994]
(EE) 4: /usr/lib/x86_64-linux-gnu/dri/amdgpu_dri.so (0x7fd04f95f000+0x25b181d) [0x7fd051f1081d]
(EE) 5: /usr/lib/x86_64-linux-gnu/dri/amdgpu_dri.so (0x7fd04f95f000+0x25b1f61) [0x7fd051f10f61]
(EE) 6: /usr/lib/x86_64-linux-gnu/dri/amdgpu_dri.so (0x7fd04f95f000+0x25b62a0) [0x7fd051f152a0]
(EE) 7: /usr/lib/x86_64-linux-gnu/dri/amdgpu_dri.so (0x7fd04f95f000+0x192d698) [0x7fd05128c698]
(EE) 8: /usr/lib/x86_64-linux-gnu/dri/amdgpu_dri.so (0x7fd04f95f000+0x18d8af2) [0x7fd051237af2]
(EE) 9: /usr/lib/x86_64-linux-gnu/dri/amdgpu_dri.so (0x7fd04f95f000+0x540a71) [0x7fd04fe9fa71]
(EE) 10: /usr/lib/x86_64-linux-gnu/dri/amdgpu_dri.so (0x7fd04f95f000+0x1463a67) [0x7fd050dc2a67]
(EE) 11: /usr/lib/x86_64-linux-gnu/dri/amdgpu_dri.so (0x7fd04f95f000+0x1463d37) [0x7fd050dc2d37]
(EE) 12: /usr/lib/x86_64-linux-gnu/dri/amdgpu_dri.so (0x7fd04f95f000+0x1478a2c) [0x7fd050dd7a2c]
(EE) 13: /usr/lib/x86_64-linux-gnu/dri/amdgpu_dri.so (0x7fd04f95f000+0x1478fa6) [0x7fd050dd7fa6]
(EE) 14: /usr/lib/x86_64-linux-gnu/dri/amdgpu_dri.so (0x7fd04f95f000+0x2574340) [0x7fd051ed3340]
(EE) 15: /usr/lib/x86_64-linux-gnu/dri/amdgpu_dri.so (0x7fd04f95f000+0x25744e4) [0x7fd051ed34e4]
(EE) 16: /opt/amdgpu-pro/lib/xorg/modules/extensions/libglx.so (0x7fd056d2b000+0x45a7f) [0x7fd056d70a7f]
(EE) 17: /opt/amdgpu-pro/lib/xorg/modules/extensions/libglx.so (GlxExtensionInit+0x138) [0x7fd056d6e8f1]
(EE) 18: /usr/lib/xorg/Xorg (InitExtensions+0x43) [0x5633bb418313]
(EE) 19: /usr/lib/xorg/Xorg (0x5633bb352000+0x581cc) [0x5633bb3aa1cc]
(EE) 20: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf0) [0x7fd05857c830]
(EE) 21: /usr/lib/xorg/Xorg (_start+0x29) [0x5633bb394329]
(EE)
(EE) Segmentation fault at address 0x18
(EE)
Fatal server error:
(EE) Caught signal 11 (Segmentation fault). Server aborting
(EE)
(EE)
Please consult the The X.Org Foundation support
       at [http://wiki.x.org]("https://community.amd.com/external-link.jspa?url=http%3A%2F%2Fwiki.x.org")
for help.
(EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
(EE)
(EE) Server terminated with error (1). Closing log file.
```

I've googled a lot and found many similar issues but none of the threads provided an answer on how to fix this. Can anyone help me please out? Thank you!

---

### Post by QIII on 2018-01-02
Hello!

Please use the default font, weight and color unless you otherwise need to clarify or draw attention to particular points of your post.

---

### Post by mastablasta on 2018-01-04
what happens if you remove the nvidia card?

---

