---
title: "nvidia and intel graphic card not detected or unkown"
date: 2022-06-28
forum: New to Ubuntu
---

### Post by derekismcdreamy on 2022-06-28
Hello everyone, I am pretty new to ubuntu (2 monthes), I got this dell workstation with nvidia T1200 and intel graphic card for my lab research work and the driver just kept crashing and they never detect the graphic card models. I do not know what was wrong about it and I have attached the page on additional drivers (The nvidia driver was manually installed, and I believe the last Unkown: Unkown is suppose to be my real nvidia graphic card)

---

### Post by Bashing-om on 2022-06-28
Hello derekismcdreamy - Welcome to the Forum.

I can not work from an image due to my poor eyes,
Please activate a terminal and in this terminal execute terminal commands:
```

lspci -k | grep -iEA5 'vga|3d'
dpkg -l | grep -i nvidia
loginctl session-status

```
 and place these outputs into the thread here using code tags to maintain the formatting  -
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

With these we get an idea of what we are working with - and perhaps a hint of where we go next.

[INDENT][INDENT]there is a process
[/INDENT][/INDENT]

---

### Post by derekismcdreamy on 2022-06-30
Hello Bashing-om,

I spent a day on diagnosing the hardware issue and it seems a proper(130W) adapter must be connected for the laptop to detect the T1200 GPU, however, the driver issue persists. Attached with the output in terminal.

For the first command, the output is
```

(base) macrobotics@macrobotics-Precision-3561:~$ lspci -k | grep -iEA5 'vga|3d'
00:02.0 VGA compatible controller: Intel Corporation TigerLake-H GT1 [UHD Graphics] (rev 01)
	Subsystem: Dell Device 0a68
	Kernel driver in use: i915
	Kernel modules: i915
00:04.0 Signal processing controller: Intel Corporation TigerLake-LP Dynamic Tuning Processor Participant (rev 05)
	Subsystem: Dell Device 0a68
--
00:17.0 SATA controller: Intel Corporation Device 43d3 (rev 11)
	Subsystem: Dell Device 0a68
	Kernel driver in use: ahci
	Kernel modules: ahci
00:1c.0 PCI bridge: Intel Corporation Device 43ba (rev 11)
	Kernel driver in use: pcieport
--
01:00.0 3D controller: NVIDIA Corporation TU117GLM [T1200 Laptop GPU] (rev ff)
	Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
72:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS525A PCI Express Card Reader (rev 01)
	Subsystem: Dell RTS525A PCI Express Card Reader
	Kernel driver in use: rtsx_pci
	Kernel modules: rtsx_pci

```
and for second command, the output is
```

(base) macrobotics@macrobotics-Precision-3561:~$ dpkg -l | grep -i nvidia
ii  libnvidia-cfg1-515:amd64                   515.43.04-0ubuntu1                  amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-515                       515.43.04-0ubuntu1                  all          Shared files used by the NVIDIA libraries
rc  libnvidia-compute-418-server:amd64         418.226.00-0ubuntu0.20.04.2         amd64        NVIDIA libcompute package
rc  libnvidia-compute-470:amd64                470.129.06-0ubuntu0.20.04.1         amd64        NVIDIA libcompute package
rc  libnvidia-compute-470-server:amd64         470.129.06-0ubuntu0.20.04.1         amd64        NVIDIA libcompute package
rc  libnvidia-compute-510:amd64                510.73.05-0ubuntu0.20.04.1          amd64        NVIDIA libcompute package
rc  libnvidia-compute-510-server:amd64         510.73.08-0ubuntu0.20.04.1          amd64        NVIDIA libcompute package
ii  libnvidia-compute-515:amd64                515.43.04-0ubuntu1                  amd64        NVIDIA libcompute package
ii  libnvidia-compute-515:i386                 515.43.04-0ubuntu1                  i386         NVIDIA libcompute package
ii  libnvidia-decode-515:amd64                 515.43.04-0ubuntu1                  amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-515:i386                  515.43.04-0ubuntu1                  i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-515:amd64                 515.43.04-0ubuntu1                  amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-515:i386                  515.43.04-0ubuntu1                  i386         NVENC Video Encoding runtime library
ii  libnvidia-extra-515:amd64                  515.43.04-0ubuntu1                  amd64        Extra libraries for the NVIDIA driver
ii  libnvidia-fbc1-515:amd64                   515.43.04-0ubuntu1                  amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-515:i386                    515.43.04-0ubuntu1                  i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-515:amd64                     515.43.04-0ubuntu1                  amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
rc  linux-modules-nvidia-470-5.14.0-1011-oem   5.14.0-1011.11                      amd64        Linux kernel nvidia modules for version 5.14.0-1011
rc  linux-modules-nvidia-510-5.14.0-1036-oem   5.14.0-1036.40+1                    amd64        Linux kernel nvidia modules for version 5.14.0-1036
rc  linux-objects-nvidia-470-5.14.0-1011-oem   5.14.0-1011.11                      amd64        Linux kernel nvidia modules for version 5.14.0-1011 (objects)
rc  linux-objects-nvidia-470-5.14.0-1036-oem   5.14.0-1036.40+1                    amd64        Linux kernel nvidia modules for version 5.14.0-1036 (objects)
rc  linux-objects-nvidia-510-5.14.0-1036-oem   5.14.0-1036.40+1                    amd64        Linux kernel nvidia modules for version 5.14.0-1036 (objects)
ii  nvidia-compute-utils-515                   515.43.04-0ubuntu1                  amd64        NVIDIA compute utilities
ii  nvidia-dkms-515                            515.43.04-0ubuntu1                  amd64        NVIDIA DKMS package
ii  nvidia-driver-515                          515.43.04-0ubuntu1                  amd64        NVIDIA driver metapackage
ii  nvidia-kernel-common-515                   515.43.04-0ubuntu1                  amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-515                   515.43.04-0ubuntu1                  amd64        NVIDIA kernel source package
ii  nvidia-prime                               0.8.16~0.20.04.2                    all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                            515.43.04-0ubuntu1                  amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-515                           515.43.04-0ubuntu1                  amd64        NVIDIA driver support binaries
ii  screen-resolution-extra                    0.18build1                          all          Extension for the nvidia-settings control panel
ii  xserver-xorg-video-nvidia-515              515.43.04-0ubuntu1                  amd64        NVIDIA binary Xorg driver

```
and for the last command, the output gave:
```

(base) macrobotics@macrobotics-Precision-3561:~$ loginctl session-status
2 - macrobotics (1001)
           Since: Thu 2022-06-30 10:43:18 EDT; 3min 57s ago
          Leader: 2758 (gdm-session-wor)
            Seat: seat0; vc2
             TTY: tty2
         Service: gdm-password; type x11; class user
           State: active
            Unit: session-2.scope
                  &#9500;&#9472;2758 gdm-session-worker [pam/gdm-password]
                  &#9500;&#9472;2788 /usr/bin/gnome-keyring-daemon --daemonize --login
                  &#9500;&#9472;2868 /usr/lib/gdm3/gdm-x-session --run-script env GNOME_SHELL_SESSION_MODE=ubuntu /usr/bin/gnome-session --systemd --session=ubuntu
                  &#9500;&#9472;2870 /usr/lib/xorg/Xorg vt2 -displayfd 3 -auth /run/user/1001/gdm/Xauthority -background none -noreset -keeptty -verbose 3
                  &#9500;&#9472;2892 /usr/libexec/gnome-session-binary --systemd --systemd --session=ubuntu
                  &#9492;&#9472;2959 /usr/bin/ssh-agent /usr/bin/im-launch env GNOME_SHELL_SESSION_MODE=ubuntu /usr/bin/gnome-session --systemd --session=ubuntu


Jun 30 10:44:18 macrobotics-Precision-3561 /usr/lib/gdm3/gdm-x-session[2870]: See https://wayland.freedesktop.org/libinput/doc/1.15.5/touchpad-jumping-cursors.html for details
Jun 30 10:45:51 macrobotics-Precision-3561 /usr/lib/gdm3/gdm-x-session[2870]: (EE) event12 - DELL0A68:00 06CB:CE65 Touchpad: kernel bug: Touch jump detected and discarded.
Jun 30 10:45:51 macrobotics-Precision-3561 /usr/lib/gdm3/gdm-x-session[2870]: See https://wayland.freedesktop.org/libinput/doc/1.15.5/touchpad-jumping-cursors.html for details
Jun 30 10:45:51 macrobotics-Precision-3561 /usr/lib/gdm3/gdm-x-session[2870]: (EE) event12 - DELL0A68:00 06CB:CE65 Touchpad: kernel bug: Touch jump detected and discarded.
Jun 30 10:45:51 macrobotics-Precision-3561 /usr/lib/gdm3/gdm-x-session[2870]: See https://wayland.freedesktop.org/libinput/doc/1.15.5/touchpad-jumping-cursors.html for details
Jun 30 10:46:02 macrobotics-Precision-3561 /usr/lib/gdm3/gdm-x-session[2870]: (EE) event12 - DELL0A68:00 06CB:CE65 Touchpad: kernel bug: Touch jump detected and discarded.
Jun 30 10:46:02 macrobotics-Precision-3561 /usr/lib/gdm3/gdm-x-session[2870]: See https://wayland.freedesktop.org/libinput/doc/1.15.5/touchpad-jumping-cursors.html for details
Jun 30 10:46:12 macrobotics-Precision-3561 /usr/lib/gdm3/gdm-x-session[2870]: (EE) event12 - DELL0A68:00 06CB:CE65 Touchpad: kernel bug: Touch jump detected and discarded.
Jun 30 10:46:12 macrobotics-Precision-3561 /usr/lib/gdm3/gdm-x-session[2870]: See https://wayland.freedesktop.org/libinput/doc/1.15.5/touchpad-jumping-cursors.html for details
Jun 30 10:46:12 macrobotics-Precision-3561 /usr/lib/gdm3/gdm-x-session[2870]: (EE) event12 - DELL0A68:00 06CB:CE65 Touchpad: WARNING: log rate limit exceeded (5 msgs per 7200000ms). Dis>
lines 1-25/25 (END)...skipping...
2 - macrobotics (1001)
           Since: Thu 2022-06-30 10:43:18 EDT; 3min 57s ago
          Leader: 2758 (gdm-session-wor)
            Seat: seat0; vc2
             TTY: tty2
         Service: gdm-password; type x11; class user
           State: active
            Unit: session-2.scope
                  &#9500;&#9472;2758 gdm-session-worker [pam/gdm-password]
                  &#9500;&#9472;2788 /usr/bin/gnome-keyring-daemon --daemonize --login
                  &#9500;&#9472;2868 /usr/lib/gdm3/gdm-x-session --run-script env GNOME_SHELL_SESSION_MODE=ubuntu /usr/bin/gnome-session --systemd --session=ubuntu
                  &#9500;&#9472;2870 /usr/lib/xorg/Xorg vt2 -displayfd 3 -auth /run/user/1001/gdm/Xauthority -background none -noreset -keeptty -verbose 3
                  &#9500;&#9472;2892 /usr/libexec/gnome-session-binary --systemd --systemd --session=ubuntu
                  &#9492;&#9472;2959 /usr/bin/ssh-agent /usr/bin/im-launch env GNOME_SHELL_SESSION_MODE=ubuntu /usr/bin/gnome-session --systemd --session=ubuntu


Jun 30 10:44:18 macrobotics-Precision-3561 /usr/lib/gdm3/gdm-x-session[2870]: See https://wayland.freedesktop.org/libinput/doc/1.15.5/touchpad-jumping-cursors.html for details
Jun 30 10:45:51 macrobotics-Precision-3561 /usr/lib/gdm3/gdm-x-session[2870]: (EE) event12 - DELL0A68:00 06CB:CE65 Touchpad: kernel bug: Touch jump detected and discarded.
Jun 30 10:45:51 macrobotics-Precision-3561 /usr/lib/gdm3/gdm-x-session[2870]: See https://wayland.freedesktop.org/libinput/doc/1.15.5/touchpad-jumping-cursors.html for details
Jun 30 10:45:51 macrobotics-Precision-3561 /usr/lib/gdm3/gdm-x-session[2870]: (EE) event12 - DELL0A68:00 06CB:CE65 Touchpad: kernel bug: Touch jump detected and discarded.
Jun 30 10:45:51 macrobotics-Precision-3561 /usr/lib/gdm3/gdm-x-session[2870]: See https://wayland.freedesktop.org/libinput/doc/1.15.5/touchpad-jumping-cursors.html for details
Jun 30 10:46:02 macrobotics-Precision-3561 /usr/lib/gdm3/gdm-x-session[2870]: (EE) event12 - DELL0A68:00 06CB:CE65 Touchpad: kernel bug: Touch jump detected and discarded.
Jun 30 10:46:02 macrobotics-Precision-3561 /usr/lib/gdm3/gdm-x-session[2870]: See https://wayland.freedesktop.org/libinput/doc/1.15.5/touchpad-jumping-cursors.html for details
Jun 30 10:46:12 macrobotics-Precision-3561 /usr/lib/gdm3/gdm-x-session[2870]: (EE) event12 - DELL0A68:00 06CB:CE65 Touchpad: kernel bug: Touch jump detected and discarded.
Jun 30 10:46:12 macrobotics-Precision-3561 /usr/lib/gdm3/gdm-x-session[2870]: See https://wayland.freedesktop.org/libinput/doc/1.15.5/touchpad-jumping-cursors.html for details
Jun 30 10:46:12 macrobotics-Precision-3561 /usr/lib/gdm3/gdm-x-session[2870]: (EE) event12 - DELL0A68:00 06CB:CE65 Touchpad: WARNING: log rate limit exceeded (5 msgs per 7200000ms). Discarding future messages.
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
lines 1-25/25 (END)

```

---

### Post by Bashing-om on 2022-06-30
derekismcdreamy; Hummm ...

We can see from the lspci output that the Nvidia card is recognized, BUT the driver is not loaded.

As you appear to have made several attempts to install Nvidia drivers - does OEM install play a part ?
what shows for terminal command:
```

sudo find / -name "NVIDIA-Linux-*"

```
where sudo == Super-User-DO and will require your password to execute elevated commands. Be aware for security when you enter the password there will be no response to the screen - enter your password blindly and hit the enter key.

Next is to see if the GPU Manager has any hints on why the drivers fails.
show:
```

cat /var/log/gpu-manager.log

```

[INDENT]the hunt to know
[INDENT][INDENT]is on
[/INDENT][/INDENT][/INDENT]

---

