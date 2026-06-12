---
title: "Grub can't update kernel list"
date: 2020-06-03
forum: New to Ubuntu
---

### Post by raducoc-a on 2020-06-03
Hi. My first post here. I do have a problem with an Ubuntu 20.04 installation into a ZFS file-system. More exactly the Grub it is getting-me a lot of errors and is unable to update the kernel list, as I do installed the Liquorix one and an updated generic one. Even so I do only have the option to boot the 5.4.0.31-generic and 5.4.0-26-generic kernel at boot time. By default it is booting the 5.4.0.31 one and it is unable to see the 5.4.0.33 and 5.6.0-15.2-liquorix ones.

Here is the output from sudo update-grub:


```
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
grub-probe: error: unknown filesystem.
Found linux image: vmlinuz-5.4.0-26-generic in rpool/ROOT/ubuntu_9aw43l
Found initrd image: initrd.img-5.4.0-26-generic in rpool/ROOT/ubuntu_9aw43l
Found linux image: vmlinuz-5.4.0-31-generic in rpool/ROOT/ubuntu_9aw43l
Found initrd image: initrd.img-5.4.0-31-generic in rpool/ROOT/ubuntu_9aw43l
Found linux image: vmlinuz-5.4.0-26-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_fkyhna
Found initrd image: initrd.img-5.4.0-26-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_fkyhna
Found linux image: vmlinuz-5.4.0-31-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_fkyhna
Found initrd image: initrd.img-5.4.0-31-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_fkyhna
cannot open 'bpool/BOOT/ubuntu_9aw43l@autozsys_hvcjor': dataset does not exist
Warning: didn't find any valid initrd or kernel.
cannot open 'bpool/BOOT/ubuntu_9aw43l@autozsys_yw8pqu': dataset does not exist
Warning: didn't find any valid initrd or kernel.
cannot open 'bpool/BOOT/ubuntu_9aw43l@autozsys_b5yce9': dataset does not exist
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_b5yce9
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_b5yce9
cannot open 'bpool/BOOT/ubuntu_9aw43l@autozsys_ls23ws': dataset does not exist
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_ls23ws
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_ls23ws
cannot open 'bpool/BOOT/ubuntu_9aw43l@autozsys_jt6xdg': dataset does not exist
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_jt6xdg
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_jt6xdg
cannot open 'bpool/BOOT/ubuntu_9aw43l@autozsys_47hg7t': dataset does not exist
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_47hg7t
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_47hg7t
cannot open 'bpool/BOOT/ubuntu_9aw43l@autozsys_lm2v2x': dataset does not exist
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_lm2v2x
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_lm2v2x
cannot open 'bpool/BOOT/ubuntu_9aw43l@autozsys_f59dy1': dataset does not exist
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_f59dy1
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_f59dy1
cannot open 'bpool/BOOT/ubuntu_9aw43l@autozsys_nzppei': dataset does not exist
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_nzppei
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_nzppei
cannot open 'bpool/BOOT/ubuntu_9aw43l@autozsys_0woq01': dataset does not exist
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_0woq01
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_0woq01
cannot open 'bpool/BOOT/ubuntu_9aw43l@autozsys_a2qmnw': dataset does not exist
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_a2qmnw
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_a2qmnw
cannot open 'bpool/BOOT/ubuntu_9aw43l@autozsys_uy0n9x': dataset does not exist
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_uy0n9x
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_uy0n9x
cannot open 'bpool/BOOT/ubuntu_9aw43l@autozsys_atk8xx': dataset does not exist
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_atk8xx
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_atk8xx
cannot open 'bpool/BOOT/ubuntu_9aw43l@autozsys_jgga7q': dataset does not exist
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_jgga7q
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_jgga7q
cannot open 'bpool/BOOT/ubuntu_9aw43l@autozsys_aic6k0': dataset does not exist
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_aic6k0
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_aic6k0
cannot open 'bpool/BOOT/ubuntu_9aw43l@autozsys_wgqsiy': dataset does not exist
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_wgqsiy
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_wgqsiy
cannot open 'bpool/BOOT/ubuntu_9aw43l@autozsys_9okgj8': dataset does not exist
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_9okgj8
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_9okgj8
cannot open 'bpool/BOOT/ubuntu_9aw43l@autozsys_qxauo3': dataset does not exist
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_qxauo3
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_qxauo3
Found linux image: vmlinuz-5.6.0-15.2-liquorix-amd64 in rpool/ROOT/ubuntu_9aw43l@autozsys_qxauo3
Found initrd image: initrd.img-5.6.0-15.2-liquorix-amd64 in rpool/ROOT/ubuntu_9aw43l@autozsys_qxauo3
cannot open 'bpool/BOOT/ubuntu_9aw43l@autozsys_peb8un': dataset does not exist
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_peb8un
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_peb8un
Found linux image: vmlinuz-5.6.0-15.2-liquorix-amd64 in rpool/ROOT/ubuntu_9aw43l@autozsys_peb8un
Found initrd image: initrd.img-5.6.0-15.2-liquorix-amd64 in rpool/ROOT/ubuntu_9aw43l@autozsys_peb8un
cannot open 'bpool/BOOT/ubuntu_9aw43l@autozsys_wis7l1': dataset does not exist
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_wis7l1
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_wis7l1
Found linux image: vmlinuz-5.6.0-15.2-liquorix-amd64 in rpool/ROOT/ubuntu_9aw43l@autozsys_wis7l1
Found initrd image: initrd.img-5.6.0-15.2-liquorix-amd64 in rpool/ROOT/ubuntu_9aw43l@autozsys_wis7l1
cannot open 'bpool/BOOT/ubuntu_9aw43l@autozsys_air3az': dataset does not exist
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_air3az
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_air3az
Found linux image: vmlinuz-5.6.0-15.2-liquorix-amd64 in rpool/ROOT/ubuntu_9aw43l@autozsys_air3az
Found initrd image: initrd.img-5.6.0-15.2-liquorix-amd64 in rpool/ROOT/ubuntu_9aw43l@autozsys_air3az
cannot open 'bpool/BOOT/ubuntu_9aw43l@autozsys_rfmd50': dataset does not exist
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_rfmd50
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_rfmd50
Found linux image: vmlinuz-5.6.0-15.2-liquorix-amd64 in rpool/ROOT/ubuntu_9aw43l@autozsys_rfmd50
Found initrd image: initrd.img-5.6.0-15.2-liquorix-amd64 in rpool/ROOT/ubuntu_9aw43l@autozsys_rfmd50
cannot open 'bpool/BOOT/ubuntu_9aw43l@autozsys_y9lo4i': dataset does not exist
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_y9lo4i
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_y9lo4i
Found linux image: vmlinuz-5.6.0-15.2-liquorix-amd64 in rpool/ROOT/ubuntu_9aw43l@autozsys_y9lo4i
Found initrd image: initrd.img-5.6.0-15.2-liquorix-amd64 in rpool/ROOT/ubuntu_9aw43l@autozsys_y9lo4i
cannot open 'bpool/BOOT/ubuntu_9aw43l@autozsys_0xfkbf': dataset does not exist
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_0xfkbf
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_0xfkbf
Found linux image: vmlinuz-5.6.0-15.2-liquorix-amd64 in rpool/ROOT/ubuntu_9aw43l@autozsys_0xfkbf
Found initrd image: initrd.img-5.6.0-15.2-liquorix-amd64 in rpool/ROOT/ubuntu_9aw43l@autozsys_0xfkbf
cannot open 'bpool/BOOT/ubuntu_9aw43l@autozsys_3pjul9': dataset does not exist
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_3pjul9
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_3pjul9
Found linux image: vmlinuz-5.6.0-15.2-liquorix-amd64 in rpool/ROOT/ubuntu_9aw43l@autozsys_3pjul9
Found initrd image: initrd.img-5.6.0-15.2-liquorix-amd64 in rpool/ROOT/ubuntu_9aw43l@autozsys_3pjul9
cannot open 'bpool/BOOT/ubuntu_9aw43l@autozsys_d1qzz6': dataset does not exist
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_d1qzz6
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_d1qzz6
Found linux image: vmlinuz-5.6.0-15.2-liquorix-amd64 in rpool/ROOT/ubuntu_9aw43l@autozsys_d1qzz6
Found initrd image: initrd.img-5.6.0-15.2-liquorix-amd64 in rpool/ROOT/ubuntu_9aw43l@autozsys_d1qzz6
cannot open 'bpool/BOOT/ubuntu_9aw43l@autozsys_1v1se8': dataset does not exist
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_1v1se8
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_9aw43l@autozsys_1v1se8
Found linux image: vmlinuz-5.6.0-15.2-liquorix-amd64 in rpool/ROOT/ubuntu_9aw43l@autozsys_1v1se8
Found initrd image: initrd.img-5.6.0-15.2-liquorix-amd64 in rpool/ROOT/ubuntu_9aw43l@autozsys_1v1se8
/usr/sbin/grub-probe: error: unknown filesystem.
device-mapper: reload ioctl on osprober-linux-sda4  failed: Device or resource busy
Command failed.
done

```

Please help to fix this issue.

---

### Post by dino99 on 2020-06-03
If you have dual or + installs, then you have a grub as 'master' which need to be reinstalled (or update-grub) to pick-up the other kernel(s)

---

### Post by raducoc-a on 2020-06-03
Yes, I do had two Ubuntu installations in two separate hard-disks but deleted one of them and now I do have only one install.

---

