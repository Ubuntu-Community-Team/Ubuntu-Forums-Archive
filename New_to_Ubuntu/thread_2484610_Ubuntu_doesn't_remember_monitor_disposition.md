---
title: "Ubuntu doesn't remember monitor disposition"
date: 2023-03-04
forum: New to Ubuntu
---

### Post by cyrusraziel on 2023-03-04
Hello 

I use an hdmi switch for using the same monitor on two computers.
When I switch back to ubuntu it doesn't recognize the monitor risposition and i have to settings the screen again.

Also when the pc becomes blocked the first monitor disconnect and I have to set it again.
What I have to do to fix this?

Thanks

---

### Post by MAFoElffen on 2023-03-04
Use Xorg X11, and use setting for noedid and set the resolution to a preferred mode.

The reason for this is that the computer uses what it is connect to to set the resolution, if not connected then it doesn't think it is connected to a display at all. Sometimes even turning off the port. The EDID table is inside the display, and tells what it is connected to what it can display. If you tell it not to pole for an EDID, and tell it what resolution to set to, then it will always be at that resolution and doesn't have a chance to be confused. 

There are many documents on the web on setting up an xorg.conf file to do that... Including some in my sticky in my Sinatureline (graphics resolution), see the modeline links in second post....

In the Device Section, use this option:
```

[Device]
Option "UseEdid" "False"

```

---

### Post by cyrusraziel on 2023-03-04
> **MAFoElffen said:**
> Use Xorg X11, and use setting for noedid and set the resolution to a preferred mode.

The reason for this is that the computer uses what it is connect to to set the resolution, if not connected then it doesn't think it is connected to a display at all. Sometimes even turning off the port. The EDID table is inside the display, and tells what it is connected to what it can display. If you tell it not to pole for an EDID, and tell it what resolution to set to, then it will always be at that resolution and doesn't have a chance to be confused. 

There are many documents on the web on setting up an xorg.conf file to do that... Including some in my sticky in my Sinatureline (graphics resolution), see the modeline links in second post....

In the Device Section, use this option:
```

[Device]
Option "UseEdid" "False"

```

Thanks a lot but i have troubles finding xorg.conf file where i can find it?
I tryed to read the guide but its too hard for me to understand it

Thanks a lot

---

### Post by MAFoElffen on 2023-03-04
Please run the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info") from that machine. Please post the URL of where it uploads the report to.

That will give me the information needed to be able to assist you.

---

### Post by cyrusraziel on 2023-03-04
Thanks a lot

Here is the link

Regards

---

### Post by MAFoElffen on 2023-03-04
> **cyrusraziel said:**
> Thanks a lot

Here is the link

Regards
I don't see a link in your post...

---

### Post by cyrusraziel on 2023-03-04
Sorry im an idiot

[https://u.pcloud.link/publink/show?code=XZlPwPVZEYUGxusLfj8iStAV0afbvRNU3wVX](https://u.pcloud.link/publink/show?code=XZlPwPVZEYUGxusLfj8iStAV0afbvRNU3wVX)

---

### Post by MAFoElffen on 2023-03-04
That link contained the "original script" (LOL), but not the report that it creates when it is run... We need to see the results of the report that script generates.

You can run it 2 different ways:
Terminal; Open a terminal session. Go to the directory you downloaded the script to. Type in these commands.
```

chmod +x ./system-info
./system-info

```
OR...

GUI: Open your File Manager. Go to the folder you downloaded the script. Right-click on the script > Properties > Security/permissions > Allow file to 'Execute'. Close the Properties dialog. Double-click on the script. It will open a terminal session with the script running.

Note: I am the author of that script and the head of that project. I also am the admin for that GitHub Reposotroy for the Forum. I have many copies of the script already. (LOL) That was entertaining. Thank you.

Follow the prompts and fill out the info asked. It will first present/display an eyes-only version of the results. To end viewing it, press the <Q> key. It will then prepare the sanitized version of the report. 

It will ask you if you want to upload it to a Pastebin. Select the <Y> key for yes, and press <Enter>. It will upload the report... At the end of that, it will tell you the URL of where it uploaded. *** Copy down that URL to post in a post so we can review it.

Tell me how it goes...

---

### Post by cyrusraziel on 2023-03-05
sorry again 

here is the link [https://paste.ubuntu.com/p/b6cn44nVgp/](https://paste.ubuntu.com/p/b6cn44nVgp/)

---

### Post by MAFoElffen on 2023-03-05
Here is an 'xorg.conf" file to try at '/etc/X11/xorg.conf'
```

# /etc/X11/xorg.conf
Section "Device"
        Identifier      "Configured Video Device"
        Option "UseEdid" "False"
        Driver "nvidia"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        # 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
        Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Option "PreferredMode" "1920x1080_60.00"
        EndSubSection
EndSection

```

---

### Post by cyrusraziel on 2023-03-06
I think I resolved in another way. It Seems that the open source kernel even if tested doesn't work properly. With the proprietary kernel I don't have any issue

thanks a lot for your assistance

---

### Post by MAFoElffen on 2023-03-06
You are welcome.

---

