---
title: "Boot time iwlwifi and acpi object errors"
date: 2016-06-15
forum: New to Ubuntu
---

### Post by Saket_Jhunjhunwala on 2016-06-15
I am getting boot time errors in ubuntu 14.04. After booting it works without any problem. Errors displayed are:
        
     0.669116] dmar: Failed to find handle for ACPI object \ SB.PCI0SD

After SD some numbers are also displayed( I could not capture them). This error is displayed in black screen.[Next this error is shown([http://http://i.stack.imgur.com/Ybg0M.jpg](http://http://i.stack.imgur.com/Ybg0M.jpg))]
Also its written 'ubuntu 14.04' rather than 'ubuntu' while starting as can be seen in image. These all happened suddenly.  
Output of dmesg |grep iwl is:

    [   16.302012] iwlwifi 0000:03:00.0: loaded firmware version 25.17.12.0 op_mode iwlmvm
    [   18.182318] iwlwifi 0000:03:00.0: Unsupported splx structure
    [   18.268492] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 3160, REV=0x164
    [   18.268837] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
    [   18.269360] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
    [   18.490087] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
    [   22.183698] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
    [   22.185198] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled

Changes done today can be seen in this image[https://drive.google.com/file/d/0B7vu6OdU_CbuQ1laWHJXSnFRUHc/view?usp=sharing](https://drive.google.com/file/d/0B7vu6OdU_CbuQ1laWHJXSnFRUHc/view?usp=sharing)
I am new to ubuntu. Please help. Thanks in advance.

---

### Post by jeremy31 on 2016-06-16
Those iwlwifi messages are normal

---

