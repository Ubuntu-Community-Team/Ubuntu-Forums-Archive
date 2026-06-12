---
title: "Noob dumb question"
date: 2010-09-20
forum: Philippine Team
---

### Post by fatboy07 on 2010-09-20
Hello mga sir can you help me with my problem on my optical drive? my drive works fine when putting a audio cd and it works fine, but when I put my data cd I can explore it, is there I need to type to access manually?
hope you can help me po.. TIA!:)

---

### Post by dirghrabadia on 2010-09-20
>  when I put my data cd I can explore it, is there I need to type to access manually?

I assume you meant 'you can't explore it'. If thats the case, go to Places in the top panel, and you would see that your data CD is mounted, waiting for you to access it :)

---

### Post by JCyberinux on 2010-09-20
usually automatic mounted yan ng ubuntu. in my case, automatic sya. Can you check your data cd/dvd disk kung may scratches? Or your dvdrom/cdrom drives, baka maayos yung copy ng music disc mo kaya n-read nakakapag-play ng audio cd. Just check either on the two.

---

### Post by fatboy07 on 2010-09-20
> **dirghrabadia said:**
> I assume you meant 'you can't explore it'. If thats the case, go to Places in the top panel, and you would see that your data CD is mounted, waiting for you to access it :)

Sorry for the typo error, I tried it already but no response.
By the way thanks for the reply. :)


@jcyberinux Thanks! Check ko...

---

### Post by fatboy07 on 2010-09-20
Still no luck for me.. meron po ba kinalaman d2 yun way ng pag install ko ng usb modem ko..kasi po gumawa po ako ng rule to activate it hindi po tulad ng usb-modeswitch.

eto po yun rules:

ACTION!="add", GOTO="huawei_zerocd_end"

SUBSYSTEM=="usb", ATTR{bDeviceClass}!="ff", ENV{DEVTYPE}=="usb_device", GOTO="huawei_zerocd_disable"
SUBSYSTEM=="scsi", ENV{DEVTYPE}=="scsi_device", GOTO="huawei_zerocd_disable"
GOTO="huawei_zerocd_end"
LABEL="huawei_zerocd_disable"
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1446", RUN+="modem-modeswitch -v 0x%s{idVendor} -p 0x%s{idProduct} -t option-zerocd"

LABEL="huawei_zerocd_end"

---

### Post by jmazaredo on 2010-10-16
> **fatboy07 said:**
> Hello mga sir can you help me with my problem on my optical drive? my drive works fine when putting a audio cd and it works fine, but when I put my data cd I can explore it, is there I need to type to access manually?
hope you can help me po.. TIA!:)

Na bobrowse mo yung audio files? kasi kung na bobrowse mo yung audio files baka yung ibang cd lang talaga problem.

Try booting ubuntu installers or any bootable media like windows installer

---

