---
title: "Not sure what my issue is with YAML"
date: 2024-09-27
forum: New to Ubuntu
---

### Post by wordizbon on 2024-09-27
I'm new to Ubuntu, Linux, and YAML and trying to configure my network interface and have the changes stay on a reboot. I saw that I needed to edit the YAML file so when I attempted to I get this error. See below:


# network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    ethernets:
        ens2:
          addresses:
            - 192.168.10.10/24
          routes:
            - to: default
              via: 192.168.10.1
          nameservers:
            addresses:
            - 8.8.4.4
        version: 2 
            match:
                macaddress: 52:54:00:08:cc:63
            set-name: ens2


"/etc/netplan/50-cloud-init.yaml" 29L, 800B written
cisco@inserthostname-here:~$ sudo netplan apply
/etc/netplan/50-cloud-init.yaml:4:11: Invalid YAML: did not find expected '-' indicator:
          gateway4: 192.168.10.1

---

### Post by deadflowr on 2024-09-27
Re-post it copy/paste into code tags.
Code tags will retain the proper formatting.
As it is the current output is wrong, but that's probably just because it's not formatted correctly.

Good walkthrough on code tags here: [https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

---

### Post by The Cog on 2024-09-27
Yes, we need the exact content, indentation is critical in yaml.

---

