---
title: "ASUS ROG STRIX audio problem"
date: 2024-09-12
forum: New to Ubuntu
---

### Post by ydnas77 on 2024-09-12
Hi all, I am new to Ubuntu and i encountered audio problem on my ASUS ROG device. I followed these steps which was given on the forum : [https://askubuntu.com/questions/1276428/no-sound-alc294-asus-rog-strix-512-ubuntu-20-04-01](https://askubuntu.com/questions/1276428/no-sound-alc294-asus-rog-strix-512-ubuntu-20-04-01) and [https://www.reddit.com/r/linuxaudio/comments/u0rnmr/no_sound_asus_g15_please_help/](https://www.reddit.com/r/linuxaudio/comments/u0rnmr/no_sound_asus_g15_please_help/)  but the problem still exists. My device informations are:

**inxi -Fxxxz**

System:
  Kernel: 6.8.0-44-generic arch: x86_64 bits: 64 compiler: gcc v: 13.2.0
    clocksource: tsc
  Desktop: GNOME v: 46.0 tk: GTK v: 3.24.41 wm: gnome-shell
    tools: gsd-screensaver-proxy dm: GDM3 v: 46.0 Distro: Ubuntu 24.04.1 LTS
    (Noble Numbat)
Machine:
  Type: Laptop System: ASUSTeK product: ROG Strix G512LV_G512LV v: 1.0
    serial: <superuser required>
  Mobo: ASUSTeK model: G512LV v: 1.0 serial: <superuser required>
    uuid: <superuser required> UEFI: American Megatrends v: G512LV.314
    date: 04/27/2021
Battery:
  ID-1: BAT0 charge: 23.7 Wh (55.9%) condition: 42.4/66.0 Wh (64.2%)
    power: 14.2 W volts: 15.7 min: 15.7 model: ASUSTeK ASUS Battery type: Li-ion
    serial: N/A status: discharging cycles: 287
CPU:
  Info: 6-core model: Intel Core i7-10750H bits: 64 type: MT MCP smt: enabled
    arch: Comet Lake rev: 2 cache: L1: 384 KiB L2: 1.5 MiB L3: 12 MiB
  Speed (MHz): avg: 800 high: 801 min/max: 800/5000 cores: 1: 800 2: 800
    3: 800 4: 800 5: 800 6: 800 7: 800 8: 801 9: 800 10: 800 11: 800 12: 800
    bogomips: 62399
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel CometLake-H GT2 [UHD Graphics] vendor: ASUSTeK driver: i915
    v: kernel arch: Gen-9.5 ports: active: eDP-1 empty: none bus-ID: 00:02.0
    chip-ID: 8086:9bc4 class-ID: 0300
  Device-2: NVIDIA TU106M [GeForce RTX 2060 Mobile] vendor: ASUSTeK
    driver: nvidia v: 550.107.02 arch: Turing pcie: speed: 8 GT/s lanes: 8
    ports: active: none empty: DP-1,HDMI-A-1 bus-ID: 01:00.0
    chip-ID: 10de:1f15 class-ID: 0300
  Display: wayland server: X.org v: 1.21.1.11 with: Xwayland v: 23.2.6
    compositor: gnome-shell driver: X: loaded: modesetting,nvidia
    unloaded: fbdev,nouveau,vesa dri: iris gpu: i915 display-ID: 0
  Monitor-1: eDP-1 model: Najing CEC Panda 0x004d res: 1920x1080 dpi: 142
    size: 344x194mm (13.54x7.64") diag: 395mm (15.5") modes: 1920x1080
  API: EGL v: 1.5 hw: drv: intel iris drv: nvidia platforms: device: 0
    drv: nvidia device: 1 drv: iris device: 3 drv: swrast surfaceless:
    drv: nvidia wayland: drv: iris x11: drv: iris inactive: gbm,device-2
  API: OpenGL v: 4.6.0 compat-v: 4.5 vendor: intel mesa v: 24.0.9-0ubuntu0.1
    glx-v: 1.4 direct-render: yes renderer: Mesa Intel UHD Graphics (CML GT2)
    device-ID: 8086:9bc4 display-ID: :0.0
Audio:
  Device-1: Intel Comet Lake PCH cAVS vendor: ASUSTeK driver: snd_hda_intel
    v: kernel bus-ID: 00:1f.3 chip-ID: 8086:06c8 class-ID: 0403
  Device-2: NVIDIA TU106 High Definition Audio vendor: ASUSTeK
    driver: snd_hda_intel v: kernel pcie: speed: 8 GT/s lanes: 8 bus-ID: 01:00.1
    chip-ID: 10de:10f9 class-ID: 0403
  API: ALSA v: k6.8.0-44-generic status: kernel-api with: aoss
    type: oss-emulator
  Server-1: PipeWire v: 1.0.5 status: active with: 1: pipewire-pulse
    status: active 2: wireplumber status: active 3: pw-jack type: plugin
  Server-2: PulseAudio v: 16.1 status: off (using pipewire-pulse)
Network:
  Device-1: Intel Comet Lake PCH CNVi WiFi driver: iwlwifi v: kernel
    bus-ID: 00:14.3 chip-ID: 8086:06f0 class-ID: 0280
  IF: wlo1 state: up mac: <filter>
  Device-2: Realtek RTL8111/8168/8211/8411 PCI Express Gigabit Ethernet
    vendor: ASUSTeK RTL8111/8168/8411 driver: r8169 v: kernel pcie:
    speed: 2.5 GT/s lanes: 1 port: 3000 bus-ID: 03:00.0 chip-ID: 10ec:8168
    class-ID: 0200
  IF: eno2 state: down mac: <filter>
  IF-ID-1: docker0 state: down mac: <filter>
  IF-ID-2: virbr0 state: down mac: <filter>
Bluetooth:
  Device-1: Intel AX201 Bluetooth driver: btusb v: 0.8 type: USB rev: 2.0
    speed: 12 Mb/s lanes: 1 bus-ID: 1-14:3 chip-ID: 8087:0026 class-ID: e001
  Report: hciconfig ID: hci0 rfk-id: 0 state: down
    bt-service: enabled,running rfk-block: hardware: no software: yes
    address: <filter>
Drives:
  Local Storage: total: 476.94 GiB used: 55.73 GiB (11.7%)
  ID-1: /dev/nvme0n1 vendor: Intel model: SSDPEKNW512G8 size: 476.94 GiB
    speed: 31.6 Gb/s lanes: 4 tech: SSD serial: <filter> fw-rev: 002C
    temp: 31.9 C scheme: GPT
Partition:
  ID-1: / size: 467.89 GiB used: 55.73 GiB (11.9%) fs: ext4
    dev: /dev/nvme0n1p2
  ID-2: /boot/efi size: 511 MiB used: 6.1 MiB (1.2%) fs: vfat
    dev: /dev/nvme0n1p1
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) priority: -2
    file: /swapfile
Sensors:
  System Temperatures: cpu: 39.0 C pch: 45.0 C mobo: N/A
  Fan Speeds (rpm): cpu: 2500
Info:
  Memory: total: 16 GiB available: 15.41 GiB used: 3.52 GiB (22.9%)
  Processes: 368 Power: uptime: 19m states: freeze,mem,disk suspend: s2idle
    wakeups: 0 hibernate: platform Init: systemd v: 255 target: graphical (5)
    default: graphical
  Packages: 2624 pm: dpkg pkgs: 2612 pm: snap pkgs: 12 Compilers:
    gcc: 13.2.0 alt: 11 Shell: Bash v: 5.2.21 running-in: x-terminal-emul
    inxi: 3.3.34

[B]
pulseaudio --dump-conf[/B]


### Read from configuration file: /etc/pulse/daemon.conf ###
daemonize = no
fail = yes
high-priority = yes
nice-level = -11
realtime-scheduling = yes
realtime-priority = 5
allow-module-loading = yes
allow-exit = yes
use-pid-file = yes
system-instance = no
local-server-type = user
cpu-limit = no
enable-shm = yes
flat-volumes = no
rescue-streams = yes
lock-memory = no
exit-idle-time = 20
scache-idle-time = 20
dl-search-path = /usr/lib/pulse-16.1+dfsg1/modules
default-script-file = /etc/pulse/default.pa
load-default-script-file = yes
log-target = 
log-level = notice
resample-method = auto
avoid-resampling = no
enable-remixing = yes
remixing-use-all-sink-channels = yes
remixing-produce-lfe = no
remixing-consume-lfe = no
lfe-crossover-freq = 0
default-sample-format = s16le
default-sample-rate = 44100
alternate-sample-rate = 48000
default-sample-channels = 2
default-channel-map = front-left,front-right
default-fragments = 4
default-fragment-size-msec = 25
enable-deferred-volume = yes
deferred-volume-safety-margin-usec = 1
deferred-volume-extra-delay-usec = 0
shm-size-bytes = 0
log-meta = no
log-time = no
log-backtrace = 0
rlimit-fsize = -1
rlimit-data = -1
rlimit-stack = -1
rlimit-core = -1
rlimit-rss = -1
rlimit-as = -1
rlimit-nproc = -1
rlimit-nofile = 256
rlimit-memlock = -1
rlimit-locks = -1
rlimit-sigpending = -1
rlimit-msgqueue = -1
rlimit-nice = 31
rlimit-rtprio = 9
rlimit-rttime = 200000

[B]
pactl-info

[/B]Server String: /run/user/1000/pulse/native
Library Protocol Version: 35
Server Protocol Version: 35
Is Local: yes
Client Index: 256
Tile Size: 65472
User Name: sandy
Host Name: ydnas
Server Name: PulseAudio (on PipeWire 1.0.5)
Server Version: 15.0.0
Default Sample Specification: float32le 2ch 48000Hz
Default Channel Map: front-left,front-right
Default Sink: alsa_output.pci-0000_00_1f.3.analog-stereo
Default Source: alsa_input.pci-0000_00_1f.3.analog-stereo
Cookie: 093d:c296

**systemctl --user status pulseaudio.service**
&#9675; pulseaudio.service - Sound Service
     Loaded: loaded (/usr/lib/systemd/user/pulseaudio.service; enabled; preset: enabled)
     Active: inactive (dead)
TriggeredBy: &#9675; pulseaudio.socket

**systemctl --user status pipewire.service**
&#9679; pipewire.service - PipeWire Multimedia Service
     Loaded: loaded (/usr/lib/systemd/user/pipewire.service; enabled; preset: enabled)
     Active: active (running) since Fri 2024-09-13 13:23:20 AEST; 25min ago
TriggeredBy: &#9679; pipewire.socket
   Main PID: 2403 (pipewire)
      Tasks: 3 (limit: 18842)
     Memory: 11.4M (peak: 12.1M)
        CPU: 856ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/pipewire.service
             &#9492;&#9472;2403 /usr/bin/pipewire


Sep 13 13:23:20 ydnas systemd[2387]: Started pipewire.service - PipeWire Multimedia Service.
Sep 13 13:23:20 ydnas pipewire[2403]: mod.jackdbus-detect: Failed to receive jackdbus reply: or>

---

### Post by TheFu on 2024-09-13
But you never say what the problem is?  Well, what's the problem?

I'm on a 
```
System:    Host: hadar Kernel: 5.15.0-119-generic x86_64 bits: 64 Desktop: FVWM2 2.6.8 
           Distro: Ubuntu 20.04.6 LTS (Focal Fossa) 
Machine:   Type: Desktop Mobo: ASUSTeK model: ROG STRIX B450-F GAMING v: Rev 1.xx
...
Audio:
  Device-1: AMD vendor: ASUSTeK driver: snd_hda_intel v: kernel bus ID: 0a:00.1 chip ID: 1002:1637 
  Device-2: AMD Family 17h HD Audio vendor: ASUSTeK driver: snd_hda_intel   v: kernel bus ID: 0a:00.6 chip ID: 1022:15e3 
  Sound Server: ALSA v: k5.15.0-119-generic 


```using built-in audio and everythi8ng works with the analog audio connections.  Those are the 3-5 colored audio plugs on the back of the motherboard so I get 5.1 surround audio.  Just a few weeks ago, I used 5.1 audio test files to validate it all worked 
```
$ ls -1
AAC_5.1.mp4
Dolby_Atmos_E-AC-3_5.1.2.mp4
Dolby_Digital_AC-3_5.1.mp4
DTS_5.1.wav
FLAC_5.1.flac

```
They did.
I don't use HDMI audio connections. Sorry.
On another identical motherboard, I use the analog front-panel stereo audio jack connected to just 2 speakers and it works too.

Have you installed **pavucontrol** and ensured that just the audio devices you specifically need are enabled, but no others?  Checked the gain and output settings to ensure they aren't disabled/muted?  In short, start from the right-most tab and work left, one tab at a time.

---

### Post by ydnas77 on 2024-09-13
Hi, I am so sorry for the confusion. The problem is I dont get audio from the in-built speaker and when i connect to the wireless airpods through bluetooth. However when i connect my wired audio earphones they work fine. I have tried installing pavucontrol and see what was wrong but the audio doesnot work even though i select the right speaker. I tried seeing in alsamixer as well to see if there was anything wrong but could not find one. 

Thank you.

---

### Post by TheFu on 2024-09-13
I've never used bluetooth and never plan to.  Terrible security and not worth the risks to me.  I forgot to disable bluetooth after doing a fresh Ubuntu install and patching, then attended a tech conference. The first day, my laptop was hacked via bluetooth.  I'd not connected to any network either wired or with wifi. Discovered that Ubuntu had enabled BT during install. That was how they got in.

I think you have a BT issue, not an audio issue.

---

### Post by ydnas77 on 2024-09-14
Nah i have audio issue as well. My laptop's inbuilt speaker is not working even though I did everything in the link above. And I tried everything but no luck.

---

