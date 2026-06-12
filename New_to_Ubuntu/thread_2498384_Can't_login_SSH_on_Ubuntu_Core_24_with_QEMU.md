---
title: "Can't login SSH on Ubuntu Core 24 with QEMU"
date: 2024-06-11
forum: New to Ubuntu
---

### Post by rafael-ricardo on 2024-06-11
I'm new in linux and i'm trying  to use the IoT Ubuntu Core, so i created my own Ubuntu Core 24 image  with this tutorial [https://ubuntu.com/core/docs/build-an-image](https://ubuntu.com/core/docs/build-an-image) and tried to visualize this image with QEMU following this tutorial [https://ubuntu.com/core/docs/testing-with-qemu](https://ubuntu.com/core/docs/testing-with-qemu)
 But when my QEMU vm runs with ubuntu core 24 it just asks me for   “localhost login” I tried my ubuntu username+pass, tried my machine   local user and password and every time I get denied. Tried to open a new   terminal and ssh login ```
ssh -vT -i ~/.ssh/id_ubuntucore  rafael-ricardo@localhost -p 8022”
```and ```
ssh -vT -i  ~/.ssh/id_ubuntucore rafael@localhost -p 8022 
```but it says:

 ```
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: get_agent_identities: bound agent to hostkey
debug1: get_agent_identities: agent returned 1 keys
debug1: Will attempt key: /home/rafael/.ssh/id_ubuntucore RSA SHA256:
debug1: Offering public key: /home/rafael/.ssh/id_ubuntucore RSA
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: password
rafael@localhost’s password:
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
rafael@localhost’s password:
debug1: Authentications that can continue: publickey
debug1: No more authentication methods to try.
rafael@localhost: Permission denied (publickey).

``` [URL="https://i.sstatic.net/3s2x2hlD.png"]QEMU Screenshot

[/URL]

 my QEMU launch commands:

 ```
qemu-system-x86_64
-enable-kvm
-smp 1
-m 2048
-machine q35
-cpu host
-global ICH9-LPC.disable_s3=1
-net nic,model=virtio
-net user,hostfwd=tcp::8022-:22,hostfwd=tcp::8090-:80
-drive file=OVMF/OVMF_CODE_4M.secboot.fd,if=pflash,format=raw,unit=0,readonly=on
-drive file=OVMF/OVMF_VARS_4M.ms.fd,if=pflash,format=raw,unit=1
-drive “file=pc.img”,if=none,format=raw,id=disk1
-device virtio-blk-pci,drive=disk1,bootindex=1
-serial mon:stdio

```


My JSON file used to build my ubuntu core image:
```

{
    "type": "model",
    "series": "16",
    "model": "ubuntu-core-24-amd64",
    "architecture": "amd64",
    "authority-id": <id removed>,
    "brand-id": <id removed>,
    "timestamp": "2024-06-11T12:37:57+00:00",
    "base": "core24",
    "grade": "signed",
    "snaps": [
        {
            "name": "pc",
            "type": "gadget",
            "default-channel": "24/stable",
            "id": "UqFziVZDHLSyO3TqSWgNBoAdHbLI4dAH"
        },
        {
            "name": "pc-kernel",
            "type": "kernel",
            "default-channel": "24/stable",
            "id": "pYVQrBcKmBa0mZ4CCN7ExT6jH8rY1hza"
        },
        {
            "name": "core24",
            "type": "base",
            "default-channel": "latest/stable",
            "id": "dwTAh7MZZ01zyriOZErqd1JynQLiOGvM"
        },
        {
            "name": "snapd",
            "type": "snapd",
            "default-channel": "latest/stable",
            "id": "PMrrV4ml8uWuEUDBT8dSGnKUYbevVhc4"
        },
        {
            "name": "console-conf",
            "type": "app",
            "default-channel": "24/stable",
            "id": "ASctKBEHzVt3f1pbZLoekCvcigRjtuqw",
            "presence": "optional"
        }
    ]
}


``` 

Could someone help me, please?

---

### Post by rafael-ricardo on 2024-06-11
I found the problem myself. The problem is the json archive I got from the library. The snap "console-conf" was set to "presence: optional," i removed it and then I could insert my sso email into my ubuntu-core to the ssh server and find the ssh keys.

---

