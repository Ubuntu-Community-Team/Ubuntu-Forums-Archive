---
title: "Fn Keys Not working Ubuntu 16.04 Asus FX553Vd"
date: 2017-08-15
forum: New to Ubuntu
---

### Post by iam4war on 2017-08-15
Hi,

I have an ASUS FX553VD machne. Some of my Fn keys are not working. For example, 
Fn+F5/F6 to increase/decrease the brightness and Fn+F3/F4 to adjust the keyboard LED brightness and Fn+F2(Airplane Mode). I have tried a couple of methods available online,
[https://askubuntu.com/questions/471847/brightness-fn-key-shortcut-doesnt-work-on-asus-laptop](https://askubuntu.com/questions/471847/brightness-fn-key-shortcut-doesnt-work-on-asus-laptop) but it didn't work.

sudo dmidecode -s bios-version
GL553VD.302

uname-a
Linux mlp-GL553VD 4.4.0-91-generic #114-Ubuntu SMP Tue Aug 8 11:56:56 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

dmesg | grep -i asus

[    0.000000] ACPI: RSDP 0x000000007AAA4000 000024 (v02 _ASUS_)
[    0.000000] ACPI: XSDT 0x000000007AAA40B8 0000F4 (v01 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 0x000000007AAD3618 000114 (v06 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 0x000000007AAA4240 02F3D8 (v02 _ASUS_ Notebook 01072009 INTL 20160422)
[    0.000000] ACPI: APIC 0x000000007AAD3730 0000BC (v03 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 0x000000007AAD37F0 000044 (v01 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 0x000000007AAD3838 00003C (v01 _ASUS_ Notebook 01072009 MSFT 00000097)
[    0.000000] ACPI: FIDT 0x000000007AAD3B70 00009C (v01 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.000000] ACPI: BGRT 0x000000007AADE938 000038 (v01 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.046989] Hardware name: ASUSTeK COMPUTER INC. GL553VD/GL553VD, BIOS GL553VD.302 03/06/2017
[    3.113648] asus_wmi: ASUS WMI generic driver loaded
[    3.114634] asus_wmi: Initialization: 0x1
[    3.114680] asus_wmi: BIOS WMI version: 8.1
[    3.114732] asus_wmi: SFUN value: 0x4a0061
[    3.115047] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input9
[    3.115210] asus_wmi: Number of fans: 1

---

