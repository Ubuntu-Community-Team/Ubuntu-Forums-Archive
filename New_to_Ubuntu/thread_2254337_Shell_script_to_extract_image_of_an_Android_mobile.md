---
title: "Shell script to extract image of an Android mobile"
date: 2014-11-26
forum: New to Ubuntu
---

### Post by abhishek18 on 2014-11-26
Hello All,

So I am trying to extract the image of an Android mobile to do some forensic analysis using the adb tool. I have been able to successfully extract the image. But what I am trying now is to make a shell script for the whole extraction process. The script is as follows:--
```
#!/bin/bash
sudo adb start-server
adb shell
su
dd if=/dev/block/mmcblk0p12 of=/storage/extSdCard/I1.img bs=4096
exit
exit
adb pull /storage/extSdCard/I1.img Desktop/img/
sudo adb kill-server
sudo mount -o loop Desktop/img/I1.img /mnt/a501/
```

Now after the adb shell command, I get access to the android device shell and post which the script gets suspended. Is there anyway I can still run the script form the android shell?

---

### Post by sotiris2 on 2014-11-29
[FONT=verdana]If I I understand [this]("http://developer.android.com/tools/help/adb.html#shellcommands") right you need to pass the command you want to run on the phone as an argument to the adb shell. I.E. ```
adb shell [COLOR=#000000]dd if=/dev/block/mmcblk0p12 of=/storage/extSdCard/I1.img bs=4096[/COLOR]
```[/FONT][COLOR=#000000][FONT=Ubuntu Mono][FONT=verdana] [SIZE=2]Otherwise you are just running an interactive shell and since there is nothing to exit from it it stays there. In fact if it somehow got out of adbs hell, su and dd would run on your host. [/SIZE][/FONT]
[/FONT][/COLOR]

---

### Post by abhishek18 on 2014-11-29
Thanks but I managed to resolve it 

```

#!/bin/bashsudo adb start-server
echo starting to extract the phone image
adb shell<<EOF
su
dd if=/dev/block/mmcblk0p12 of=/storage/extSdCard/H3.img bs=4096
exit
exit
EOF
echo pulling the image from the phone to the system
adb pull /storage/extSdCard/H3.img Desktop/img/
sudo adb kill-server
sudo mount -o loop Desktop/img/H3.img /mnt/a501/
```

---

