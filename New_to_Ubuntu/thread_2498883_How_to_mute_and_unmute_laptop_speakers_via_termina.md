---
title: "How to mute and unmute laptop speakers via terminal"
date: 2024-07-02
forum: New to Ubuntu
---

### Post by bhubunt on 2024-07-02
Hi,
How can one mute and unmute laptop speakers via the terminal? Am using Ubuntu 22.04.4 LTS on a Lenovo Thinkpad x240.

I'd appreciate learning what the code lines are,

Thanks

---

### Post by ActionParsnip on 2024-07-02
```

amixer set Master toggle

```
Will un/mute

---

### Post by bhubunt on 2024-07-02
That doesn't work.

I got this return

```
 amixer: Unable to find simple control 'Master',0


```

---

### Post by #&amp;thj^% on 2024-07-02
So Close:
```
amixer -q -D pulse sset Master toggle
```

---

### Post by bhubunt on 2024-07-02
result I got:

```
  ALSA lib pulse.c:242:(pulse_connect) PulseAudio: Unable to connect: Connection refused

amixer: Mixer attach pulse error: Connection refused
 
```

---

### Post by #&amp;thj^% on 2024-07-02
> **bhubunt said:**
> result I got:

```
  ALSA lib pulse.c:242:(pulse_connect) PulseAudio: Unable to connect: Connection refused

amixer: Mixer attach pulse error: Connection refused
 
```

Show me all of that terminal window Please don't just paste what you think we want to see ie:
```
&#9492;&#9472;> amixer -q -D pulse sset Master toggle
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> 


```
I have no return from that command, but volume is muted until I toggle it again.

---

### Post by bhubunt on 2024-07-02
post deleted because duplicate

---

### Post by bhubunt on 2024-07-02
```
 ThinkPad-X240:~$ sudo amixer -q -D pulse sset Master toggle
[sudo] password for me: 
ALSA lib pulse.c:242:(pulse_connect) PulseAudio: Unable to connect: Connection refused

amixer: Mixer attach pulse error: Connection refused  
```

---

### Post by #&amp;thj^% on 2024-07-02
*sudo* is not needed just to control volume

---

### Post by bhubunt on 2024-07-02
I see what you mean. I put in the command without sudo and the sound icon on the top right went on, when I entered the command again the loudspeaker icon top right was crossed out. But when I entered the command a 3rd time and the volume was supposed to be on, there is no sound from the speakers.  The speakers are not blown because there was sound when I turned on the laptop. After a few minutes, the sound disappeared. Has been like this for 2 days. Sound on and off. Ogres?

---

### Post by #&amp;thj^% on 2024-07-02
IDK, but I'll try for bit to help though.
Please show:
```
 systemctl status --user wireplumber|grep Active

```

---

### Post by bhubunt on 2024-07-02
```
 me-ThinkPad-X240:~$ systemctl status --user wireplumber|grep Active
Unit wireplumber.service could not be found.
me-ThinkPad-X240:~$ sudo systemctl status --user wireplumber|grep Active
[sudo] password for me: 
Failed to connect to bus: $DBUS_SESSION_BUS_ADDRESS and $XDG_RUNTIME_DIR not defined (consider using --machine=<user>@.host --user to connect to bus of other user) 
```

---

### Post by #&amp;thj^% on 2024-07-02
Plese try:
```
 systemctl start --user wireplumber
```

---

### Post by bhubunt on 2024-07-02
```
 me-ThinkPad-X240:~$ systemctl start --user wireplumber
Failed to start wireplumber.service: Unit wireplumber.service not found.
me-ThinkPad-X240:~$ sudo systemctl start --user wireplumber
Failed to connect to bus: $DBUS_SESSION_BUS_ADDRESS and $XDG_RUNTIME_DIR not defined (consider using --machine=<user>@.host --user to connect to bus of other user)
```

---

### Post by #&amp;thj^% on 2024-07-02
Are you opposed to installing "pipewire" and "wireplumber"?

I'm sure your running pluseaudio currently.
```
systemctl status --user pusleaudio wireplumber pipewire

```
Mine will show:
```
Unit pusleaudio.service could not be found.
&#9679; wireplumber.service - Multimedia Service Session Manager
     Loaded: loaded (/usr/lib/systemd/user/wireplumber.service; enabled; preset>
    Drop-In: /home/me/.config/systemd/user/wireplumber.service.d
             &#9492;&#9472;override.conf
     Active: active (running) since Tue 2024-07-02 10:25:54 MDT; 4h 15min ago
    Process: 2804 ExecStartPre=/bin/sleep 5 (code=exited, status=0/SUCCESS)
   Main PID: 3624 (wireplumber)
      Tasks: 6 (limit: 16309)
     Memory: 10.8M (peak: 11.2M)
        CPU: 365ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/wirepl>
             &#9492;&#9472;3624 /usr/bin/wireplumber

Jul 02 10:25:49 me-Legion-5-zfs systemd[2777]: Starting wireplumber.service - M>
Jul 02 10:25:54 me-Legion-5-zfs systemd[2777]: Started wireplumber.service - Mu>
Jul 02 10:25:55 me-Legion-5-zfs wireplumber[3624]: wp-device: SPA handle 'api.l>
Jul 02 10:25:55 me-Legion-5-zfs wireplumber[3624]: s-monitors-libcamera: PipeWi>

&#9679; pipewire.service - PipeWire Multimedia Service
     Loaded: loaded (/usr/lib/systemd/user/pipewire.service; enabled; preset: e>
     Active: active (running) since Tue 2024-07-02 10:25:49 MDT; 4h 15min ago
TriggeredBy: &#9679; pipewire.socket

```

---

### Post by bhubunt on 2024-07-02
```
 ThinkPad-X240:~$ systemctl status --user pusleaudio wireplumber pipewire
Unit pusleaudio.service could not be found.
Unit wireplumber.service could not be found.
&#9679; pipewire.service - PipeWire Multimedia Service
     Loaded: loaded (/usr/lib/systemd/user/pipewire.service; enabled; vendor pr>
     Active: active (running) since Tue 2024-07-02 20:36:58 CEST; 2h 15min ago
TriggeredBy: &#9679; pipewire.socket
   Main PID: 1888 (pipewire)
      Tasks: 2 (limit: 4384)
     Memory: 368.0K
        CPU: 100ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/pipewi>
             &#9492;&#9472;1888 /usr/bin/pipewire


```

---

### Post by bhubunt on 2024-07-02
I powered off. When I powered on again a weird long scrolling code list showed up before the login screen came on... Too fast for me to read what it said.

I entered the same command again and now got this:

```
 ThinkPad-X240:~$ systemctl status --user pusleaudio wireplumber pipewire
Unit pusleaudio.service could not be found.
Unit wireplumber.service could not be found.
&#9679; pipewire.service - PipeWire Multimedia Service
     Loaded: loaded (/usr/lib/systemd/user/pipewire.service; enabled; vendor pr>
     Active: active (running) since Tue 2024-07-02 22:59:21 CEST; 1min 56s ago
TriggeredBy: &#9679; pipewire.socket
   Main PID: 1894 (pipewire)
      Tasks: 2 (limit: 4384)
     Memory: 1.4M
        CPU: 54ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/pipewi>
             &#9492;&#9472;1894 /usr/bin/pipewire

Jul 02 22:59:21 me-ThinkPad-X240 systemd[1887]: Started PipeWire Multimedi> 
```

---

### Post by #&amp;thj^% on 2024-07-02
Pipewire is good but I find it incomplete.
Please have a look here, and decide for yourself if this is wanted: [https://gist.github.com/the-spyke/2de98b22ff4f978ebf0650c90e82027e?permalink_comment_id=3976215](https://gist.github.com/the-spyke/2de98b22ff4f978ebf0650c90e82027e?permalink_comment_id=3976215)
This line is not needed from that link above.
```

sudo cp /usr/share/doc/pipewire/examples/alsa.conf.d/99-pipewire-default.conf /etc/alsa/conf.d/
```
Please do all the rest of those suggestions, they are needed.

I'm going offline in a short time so good luck.

---

### Post by bhubunt on 2024-07-02
I'm in a different time zone so signing off now. Back tomorrow.

---

### Post by bhubunt on 2024-07-03
Hi, I installed wireplumber using the simple install command. When I  checked to see if it worked the following came up. What is a leaked  proxy? I am not using a proxy.  Nor am I using a VPN!

```
 ThinkPad-X240:~$ wireplumber
C 08:40:34.088737               GLib (null):(null):(null): Failed to set scheduler settings: Operation not permitted
^CM 08:41:04.159424        wireplumber ../src/main.c:354:signal_handler: stopped by signal: Interrupt
M 08:41:04.160334            pw.core ../src/pipewire/core.c:190:destroy_proxy: 0x5825bdaf0250: leaked proxy 0x5825bdb7a0f0 id:11
M 08:41:04.160359            pw.core ../src/pipewire/core.c:190:destroy_proxy: 0x5825bdaf0250: leaked proxy 0x5825bdb89580 id:12
M 08:41:04.160375            pw.core ../src/pipewire/core.c:190:destroy_proxy: 0x5825bdaf0250: leaked proxy 0x5825bdb8f180 id:13
M 08:41:04.160389            pw.core ../src/pipewire/core.c:190:destroy_proxy: 0x5825bdaf0250: leaked proxy 0x5825bdb970a0 id:14
M 08:41:04.160402            pw.core ../src/pipewire/core.c:190:destroy_proxy: 0x5825bdaf0250: leaked proxy 0x5825bdb97120 id:15
M 08:41:04.160416            pw.core ../src/pipewire/core.c:190:destroy_proxy: 0x5825bdaf0250: leaked proxy 0x5825bdb971a0 id:16
M 08:41:04.160429            pw.core ../src/pipewire/core.c:190:destroy_proxy: 0x5825bdaf0250: leaked proxy 0x5825bdb97220 id:17
M 08:41:04.160442            pw.core ../src/pipewire/core.c:190:destroy_proxy: 0x5825bdaf0250: leaked proxy 0x5825bdb972a0 id:18
M 08:41:04.160455            pw.core ../src/pipewire/core.c:190:destroy_proxy: 0x5825bdaf0250: leaked proxy 0x5825bdb97320 id:19
M 08:41:04.160470            pw.core ../src/pipewire/core.c:190:destroy_proxy: 0x5825bdaf0250: leaked proxy 0x5825bdb92a80 id:20
M 08:41:04.160483            pw.core ../src/pipewire/core.c:190:destroy_proxy: 0x5825bdaf0250: leaked proxy 0x5825bdb92b00 id:21
M 08:41:04.160704        wireplumber ../src/main.c:346:on_disconnected: disconnected from pipewire 
```

---

### Post by #&amp;thj^% on 2024-07-03
You keep me on my toes for sure...LOL
Any way it appears to me you did not follow that link, but just installed wireplumber. Is that correct.

When posting or replying back Details are very important. But you do  not start wireplumber with how you showed.

Instead use:
```
 systemctl --user --now enable wireplumber.service
```

So my question to you is did you follow that link line for line? I need to know before proceeding with any more advise.

My install for pipewire and wireplumber is this:
```
 apt policy pipewire-media-session wireplumber  pipewire-audio-client-libraries libldacbt-{abr,enc}2 libspa-0.2-bluetooth pulseaudio-module-bluetooth
pipewire-media-session:
  Installed: (none)
  Candidate: (none)
  Version table:
wireplumber:
  Installed: 0.5.5-1
  Candidate: 0.5.5-1
  Version table:
 *** 0.5.5-1 500
        500 http://archive.ubuntu.com/ubuntu oracular/main amd64 Packages
        100 /var/lib/dpkg/status
pipewire-audio-client-libraries:
  Installed: 1.2.0-1
  Candidate: 1.2.0-1
  Version table:
 *** 1.2.0-1 500
        500 http://archive.ubuntu.com/ubuntu oracular/universe amd64 Packages
        100 /var/lib/dpkg/status
libldacbt-abr2:
  Installed: 2.0.2.3+git20200429+ed310a0-4ubuntu2
  Candidate: 2.0.2.3+git20200429+ed310a0-4ubuntu2
  Version table:
 *** 2.0.2.3+git20200429+ed310a0-4ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu oracular/main amd64 Packages
        100 /var/lib/dpkg/status
libldacbt-enc2:
  Installed: 2.0.2.3+git20200429+ed310a0-4ubuntu2
  Candidate: 2.0.2.3+git20200429+ed310a0-4ubuntu2
  Version table:
 *** 2.0.2.3+git20200429+ed310a0-4ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu oracular/main amd64 Packages
        100 /var/lib/dpkg/status
libspa-0.2-bluetooth:
  Installed: 1.2.0-1
  Candidate: 1.2.0-1
  Version table:
 *** 1.2.0-1 500
        500 http://archive.ubuntu.com/ubuntu oracular/main amd64 Packages
        100 /var/lib/dpkg/status
pulseaudio-module-bluetooth:
  Installed: (none)
  Candidate: 1:16.1+dfsg1-5.1ubuntu1
  Version table:
     1:16.1+dfsg1-5.1ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu oracular/universe amd64 Packages


```

---

### Post by bhubunt on 2024-07-03
> **1fallen said:**
> You keep me on my toes for sure...LOL
Any way it appears to me you did not follow that link, but just installed wireplumber. Is that correct.

When posting or replying back Details are very important. But you do  not start wireplumber with how you showed.

Instead use:
```
 systemctl --user --now enable wireplumber.service
```

So my question to you is did you follow that link line for line? I need to know before proceeding with any more advise. 

Hi,
I tried the first line and then got this ```
 -ThinkPad-X240:~$ $ sudo apt install pipewire-media-session- wireplumber
$: command not found

```

Then the terminal suggested using ```
 sudo apt-get install wireplumber 
``` which I entered.

Then I checked to see and typed in wireplumber and got the "leaked proxy" references. As mentioned, I do not use a VPN nor a proxy.  I have had weird proxy messages show up in the past, online and have mentioned that in another thread.

Curious to know why the leaked proxy references showed up.

---

### Post by bhubunt on 2024-07-03
```
ThinkPad-X240:~$ systemctl --user --now enable wireplumber.service
Created symlink /home/me/.config/systemd/user/pipewire-session-manager.service &#8594; /usr/lib/systemd/user/wireplumber.service.
Created symlink /home/me/.config/systemd/user/pipewire.service.wants/wireplumber.service &#8594; /usr/lib/systemd/user/wireplumber.service.


```

---

### Post by #&amp;thj^% on 2024-07-03
Please re-read my posts and and answer those questions.
EDIT I see now you posted twice.

Not much time again today so a heads up on me going offline.

---

### Post by bhubunt on 2024-07-03
```
ThinkPad-X240:~$ sudo apt install pipewire-media-session- wireplumber
[sudo] password for me: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package 'pipewire-media-session' is not installed, so not removed
wireplumber is already the newest version (0.4.8-4).
0 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.
```

---

### Post by bhubunt on 2024-07-03
Can you paste the unanswered questions in a new post? I'm afraid I've lost track. Sorry, it's been a long day. I will try to answer the new post.

---

### Post by #&amp;thj^% on 2024-07-03
This seems to be missing:
```
sudo apt install pipewire-audio-client-libraries
```
And don't worry about nothing found with:
```
sudo cp /usr/share/doc/pipewire/examples/alsa.conf.d/99-pipewire-default.conf /etc/alsa/conf.d/
```
But copy and paste this one in the terminal with the trailing"-"
```
 sudo apt install libldacbt-{abr,enc}2 libspa-0.2-bluetooth pulseaudio-module-bluetooth-
```
Now reboot.

---

### Post by bhubunt on 2024-07-03
> **1fallen said:**
> This seems to be missing:

But copy and paste this one in the terminal with the trailing"-"
```
 sudo apt install libldacbt-{abr,enc}2 libspa-0.2-bluetooth pulseaudio-module-bluetooth-
```
Now reboot.


I don't understand what you mean by 'with the trailing'  Do you mean quotation marks?

I don't have bluetooth, removed the bluetooth card.  Do you want me to enter that line even if I can't use bluetooth?

---

### Post by bhubunt on 2024-07-03
```
   sudo apt install pipewire-audio-client-libraries
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following NEW packages will be installed:
  pipewire-audio-client-libraries
0 upgraded, 1 newly installed, 0 to remove and 23 not upgraded.
Need to get 145 kB of archives.
After this operation, 714 kB of additional disk space will be used.
Get:1 http://de.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 pipewire-audio-client-libraries amd64 0.3.48-1ubuntu3 [145 kB]
Fetched 145 kB in 0s (552 kB/s)                         
Selecting previously unselected package pipewire-audio-client-libraries:amd64.
(Reading database ... 251192 files and directories currently installed.)
Preparing to unpack .../pipewire-audio-client-libraries_0.3.48-1ubuntu3_amd64.de
b ...
Unpacking pipewire-audio-client-libraries:amd64 (0.3.48-1ubuntu3) ...
Setting up pipewire-audio-client-libraries:amd64 (0.3.48-1ubuntu3) ...
Processing triggers for man-db (2.10.2-1) ..
```

---

### Post by #&amp;thj^% on 2024-07-03
> **bhubunt said:**
> I don't understand what you mean by 'with the trailing'  Do you mean quotation marks?
Nope this:
```
pulseaudio-module-bluetooth[COLOR="#FF0000"]-[/COLOR]
```
In Red
> **bhubunt said:**
> 
I don't have bluetooth, removed the bluetooth card.  Do you want me to enter that line even if I can't use bluetooth?

It would help in your case just for today, and it will not enable bluetooth.
You'll have to that manually if you ever need it again.

---

### Post by bhubunt on 2024-07-03
Hi 
I copied the code line into the terminal and rebooted. 

```
sudo apt install libldacbt-{abr,enc}2 libspa-0.2-bluetooth pulseaudio-module-bluetooth-
```

---

### Post by bhubunt on 2024-07-03
Here you go. Now I am curious to know where all of this is leading. (Still wondering about the results I got earlier -- the leaked proxy...)

```
  apt policy pipewire-media-session wireplumber  pipewire-audio-client-libraries libldacbt-{abr,enc}2 libspa-0.2-bluetooth pulseaudio-module-bluetooth
pipewire-media-session:
  Installed: (none)
  Candidate: 0.4.1-2ubuntu1
  Version table:
     0.4.1-2ubuntu1 500
        500 http://de.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status
wireplumber:
  Installed: 0.4.8-4
  Candidate: 0.4.8-4
  Version table:
 *** 0.4.8-4 500
        500 http://de.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status
pipewire-audio-client-libraries:
  Installed: 0.3.48-1ubuntu3
  Candidate: 0.3.48-1ubuntu3
  Version table:
 *** 0.3.48-1ubuntu3 500
        500 http://de.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     0.3.48-1ubuntu1 500
        500 http://de.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
libldacbt-abr2:
  Installed: 2.0.2.3+git20200429+ed310a0-4
  Candidate: 2.0.2.3+git20200429+ed310a0-4
  Version table:
 *** 2.0.2.3+git20200429+ed310a0-4 500
        500 http://de.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status
libldacbt-enc2:
  Installed: 2.0.2.3+git20200429+ed310a0-4
  Candidate: 2.0.2.3+git20200429+ed310a0-4
  Version table:
 *** 2.0.2.3+git20200429+ed310a0-4 500
        500 http://de.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status
libspa-0.2-bluetooth:
  Installed: 0.3.48-1ubuntu3
  Candidate: 0.3.48-1ubuntu3
  Version table:
 *** 0.3.48-1ubuntu3 500
        500 http://de.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     0.3.48-1ubuntu1 500
        500 http://de.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
pulseaudio-module-bluetooth:
  Installed: (none)
  Candidate: 1:15.99.1+dfsg1-1ubuntu2.2
  Version table:
     1:15.99.1+dfsg1-1ubuntu2.2 500
        500 http://de.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
     1:15.99.1+dfsg1-1ubuntu1 500
        500 http://de.archive.ubuntu.com/ubuntu jammy/main amd64 Packages

 
```

---

### Post by bhubunt on 2024-07-03
And I also just typed in wireplumber again and now I got the following weird results, below. 
In addition, the icons in the top right corner are in motion. The volume icon keeps disappearing and popping back up.  The live patch icon, wired connection  icon keep jumping along. Never seen anything like it. 

```
 ~$ wireplumber
C 21:49:27.774062               GLib (null):(null):(null): Failed to set scheduler settings: Operation not permitted
M 21:49:28.032674    m-lua-scripting ../modules/module-lua-scripting/api.c:338:object_activate_done: <WpSiAudioAdapter:0x57fa7ae112c0> Object activation aborted: proxy destroyed
M 21:49:28.032716 script/create-item create-item.lua:74:chunk: <WpSiAudioAdapter:0x57fa7ae112c0> failed to activate item: Object activation aborted: proxy destroyed
M 21:49:28.033290    m-lua-scripting ../modules/module-lua-scripting/api.c:338:object_activate_done: <WpSiAudioAdapter:0x57fa7ae110e0> Object activation aborted: proxy destroyed
M 21:49:28.033328 script/create-item create-item.lua:74:chunk: <WpSiAudioAdapter:0x57fa7ae110e0> failed to activate item: Object activation aborted: proxy destroyed
W 21:49:28.192344              wplua ../lib/wplua/wplua.c:49:_wplua_errhandler: [string "policy-bluetooth.lua"]:121: bad argument #1 to 'find' (string expected, got nil)
stack traceback:
    [C]: in function 'string.find'
    [string "policy-bluetooth.lua"]:121: in upvalue 'isBluez5AudioSink'
    [string "policy-bluetooth.lua"]:389: in function <[string "policy-bluetooth.lua"]:387>
W 21:49:28.369257           GLib-GIO (null):(null):(null): Unexpected reply 3 when releasing name org.freedesktop.ReserveDevice1.Audio1
M 21:49:28.540326    m-lua-scripting ../modules/module-lua-scripting/api.c:338:object_activate_done: <WpSiAudioAdapter:0x57fa7ae114a0> Object activation aborted: proxy destroyed
M 21:49:28.540382 script/create-item create-item.lua:74:chunk: <WpSiAudioAdapter:0x57fa7ae114a0> failed to activate item: Object activation aborted: proxy destroyed
W 21:49:28.932444           GLib-GIO (null):(null):(null): Unexpected reply 3 when releasing name org.freedesktop.ReserveDevice1.Audio0
W 21:49:28.942960              wplua ../lib/wplua/wplua.c:49:_wplua_errhandler: [string "policy-bluetooth.lua"]:121: bad argument #1 to 'find' (string expected, got nil)
stack traceback:
    [C]: in function 'string.find'
    [string "policy-bluetooth.lua"]:121: in upvalue 'isBluez5AudioSink'
    [string "policy-bluetooth.lua"]:389: in function <[string "policy-bluetooth.lua"]:387>
M 21:49:29.468009    m-lua-scripting ../modules/module-lua-scripting/api.c:338:object_activate_done: <WpSiAudioAdapter:0x57fa7ae11680> Object activation aborted: proxy destroyed
M 21:49:29.468053 script/create-item create-item.lua:74:chunk: <WpSiAudioAdapter:0x57fa7ae11680> failed to activate item: Object activation aborted: proxy destroyed
M 21:49:29.499634    m-lua-scripting ../modules/module-lua-scripting/api.c:338:object_activate_done: <WpSiAudioAdapter:0x57fa7ae11680> Object activation aborted: proxy destroyed
M 21:49:29.499718 script/create-item create-item.lua:74:chunk: <WpSiAudioAdapter:0x57fa7ae11680> failed to activate item: Object activation aborted: proxy destroyed
M 21:49:29.500238    m-lua-scripting ../modules/module-lua-scripting/api.c:338:object_activate_done: <WpSiAudioAdapter:0x57fa7ae114a0> Object activation aborted: proxy destroyed

 
```

---

### Post by #&amp;thj^% on 2024-07-03
You don't type in wireplumber, instead use:
```
systemctl --user status wireplumber
&#9679; wireplumber.service - Multimedia Service Session Manager
     Loaded: loaded (/usr/lib/systemd/user/wireplumber.service; enabled; preset>
    Drop-In: /home/me/.config/systemd/user/wireplumber.service.d
             &#9492;&#9472;override.conf
     Active: active (running) since Wed 2024-07-03 10:02:05 MDT; 6h ago
    Process: 2774 ExecStartPre=/bin/sleep 5 (code=exited, status=0/SUCCESS)
   Main PID: 3540 (wireplumber)
      Tasks: 6 (limit: 16309)
     Memory: 10.9M (peak: 11.3M)
        CPU: 358ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/wirepl>
             &#9492;&#9472;3540 /usr/bin/wireplumber

```
Mine is running, and you can also check with:
```
wpctl status
PipeWire 'pipewire-0' [1.2.0, me@me-Legion-5-zfs, cookie:2321409611]
 &#9492;&#9472; Clients:
        33. WirePlumber                         [1.2.0, me@me-Legion-5-zfs, pid:3540]
        38. pipewire                            [1.2.0, me@me-Legion-5-zfs, pid:3541]
        40. WirePlumber [export]                [1.2.0, me@me-Legion-5-zfs, pid:3540]
        42. xfce4-pulseaudio-plugin             [1.2.0, me@me-Legion-5-zfs, pid:3187]
        44. pipewire                            [1.2.0, me@me-Legion-5-zfs, pid:3541]
        45. pipewire                            [1.2.0, me@me-Legion-5-zfs, pid:3541]
        46. pipewire                            [1.2.0, me@me-Legion-5-zfs, pid:3541]
        47. pipewire                            [1.2.0, me@me-Legion-5-zfs, pid:3541]
        56. xdg-desktop-portal                  [1.2.0, me@me-Legion-5-zfs, pid:3573]
       241. Blueman                             [1.2.0, me@me-Legion-5-zfs, pid:3247]
       242. wpctl                               [1.2.0, me@me-Legion-5-zfs, pid:503285]

Audio
 &#9500;&#9472; Devices:
 &#9474;      57. HDA NVidia                          [alsa]
 &#9474;      58. UOEOS Laptop Dock                   [alsa]
 &#9474;      59. Family 17h/19h HD Audio Controller  [alsa]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;      63. HDA NVidia Pro                      [vol: 1.00]
 &#9474;      65. UOEOS Laptop Dock Analog Surround 4.1 [vol: 0.80]
 &#9474;      66. Family 17h/19h HD Audio Controller Analog Stereo [vol: 0.40]
 &#9474;      83. HDA NVidia Pro 7                    [vol: 1.00]
 &#9474;      84. HDA NVidia Pro 8                    [vol: 1.00]
 &#9474;      85. HDA NVidia Pro 9                    [vol: 1.00]
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  *   67. Family 17h/19h HD Audio Controller Analog Stereo [vol: 1.30 MUTED]
 &#9474;  
 &#9500;&#9472; Filters:
 &#9474;    - combine-sink-3541-13                                        
 &#9474;      39. output.combined_combined                                     [Stream/Output/Audio]
 &#9474;  *   49. combined                                                     [Audio/Sink]
 &#9474;      73. output.combined_alsa_output.pci-0000_01_00.1.pro-output-7    [Stream/Output/Audio]
 &#9474;      75. output.combined_alsa_output.pci-0000_06_00.6.analog-stereo   [Stream/Output/Audio]
 &#9474;      76. output.combined_alsa_output.pci-0000_01_00.1.pro-output-3    [Stream/Output/Audio]
 &#9474;      77. output.combined_alsa_output.usb-DisplayLink_UOEOS_Laptop_Dock_4307293310436-02.analog-surround-41 [Stream/Output/Audio]
 &#9474;      86. output.combined_alsa_output.pci-0000_01_00.1.pro-output-8    [Stream/Output/Audio]
 &#9474;      87. output.combined_alsa_output.pci-0000_01_00.1.pro-output-9    [Stream/Output/Audio]
 &#9474;    - combine-sink-3541-14                                        
 &#9474;      50. combined                                                     [Audio/Sink]
 &#9474;      53. output.combined_combined                                     [Stream/Output/Audio]
 &#9474;      74. output.combined_alsa_output.usb-DisplayLink_UOEOS_Laptop_Dock_4307293310436-02.analog-surround-41 [Stream/Output/Audio]
 &#9474;      78. output.combined_alsa_output.pci-0000_06_00.6.analog-stereo   [Stream/Output/Audio]
 &#9474;      88. output.combined_alsa_output.pci-0000_01_00.1.pro-output-3    [Stream/Output/Audio]
 &#9474;      89. output.combined_alsa_output.pci-0000_01_00.1.pro-output-7    [Stream/Output/Audio]
 &#9474;      90. output.combined_alsa_output.pci-0000_01_00.1.pro-output-8    [Stream/Output/Audio]
 &#9474;      91. output.combined_alsa_output.pci-0000_01_00.1.pro-output-9    [Stream/Output/Audio]
 &#9474;  
 &#9492;&#9472; Streams:

Video
 &#9500;&#9472; Devices:
 &#9474;      68. Integrated Camera                   [v4l2]
 &#9474;      69. Integrated Camera                   [v4l2]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  *  239. Integrated Camera (V4L2)           
 &#9474;  
 &#9500;&#9472; Filters:
 &#9474;  
 &#9492;&#9472; Streams:

Settings
 &#9492;&#9472; Default Configured Devices:
         0. Audio/Sink    combined

```

Do you have sound yet?

---

### Post by bhubunt on 2024-07-04
Thanks very much for your help. I appreciate your continued help! 

No, alas, no speaker sound.  The laptop also doesn't make a sound when I power it up like it used to.

Comparing my output below to yours, I'd say mine doesn't look right. 

```
 PipeWire 'pipewire-0' [0.3.48, me-ThinkPad-X240, cookie:279969347]
 &#9492;&#9472; Clients:
        31. WirePlumber                         [0.3.48, me-ThinkPad-X240, pid:2023]
        32. WirePlumber [export]                [0.3.48, -ThinkPad-X240, pid:2023]
        34. pipewire                            [0.3.48, -ThinkPad-X240, pid:2024]
        49. GNOME Shell Volume Control          [0.3.48, x240, pid:2193]
        50. GNOME Volume Control Media Keys     [0.3.48,-ThinkPad-X240, pid:2339]
        51. xdg-desktop-portal                  [0.3.48, ThinkPad-X240, pid:2669]
        52. gnome-shell                         [0.3.48, -ThinkPad-X240, pid:2193]
        53. wpctl                               [0.3.48, -ThinkPad-X240, pid:10423]

Audio
 &#9500;&#9472; Devices:
 &#9474;      40. Built-in Audio                      [alsa]
 &#9474;      41. Built-in Audio                      [alsa]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  *   42. Built-in Audio Analog Stereo        [vol: 0.37]
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  *   43. Built-in Audio Analog Stereo        [vol: 0.74]
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:

Video
 &#9500;&#9472; Devices:
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:

Settings
 &#9492;&#9472; Default Configured Node Names:  
```

---

### Post by bhubunt on 2024-07-04
And this output sure also doesn't look right compared to yours.

 The proxy ref keeps returning. As noted, I do not use a proxy, nor do I use a VPN.

Operation not permitted is in yellow.

There is no process line after "Active" like in your output.

What does the > mean after Object activation aborted? Is there supposed to be more info following? Probably: proxy destroyed.

```
  systemctl --user status wireplumber
&#9679; wireplumber.service - Multimedia Service Session Manager
     Loaded: loaded (/usr/lib/systemd/user/wireplumber.service; enabled; vendor preset: enabled)
     Active: active (running) since Thu 2024-07-04 08:06:10 CEST; 1h 11min ago
   Main PID: 2023 (wireplumber)
      Tasks: 4 (limit: 4384)
     Memory: 4.2M
        CPU: 545ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/wireplumber.service
             &#9492;&#9472;2023 /usr/bin/wireplumber

Jul 04 08:06:10 me-ThinkPad-X240 systemd[2013]: Started Multimedia Service Session Manager.
Jul 04 08:06:11 me-ThinkPad-X240 wireplumber[2023]: Failed to set scheduler settings: Operation not permitted
Jul 04 08:06:12 -ThinkPad-X240 wireplumber[2023]: <WpSiAudioAdapter:0x5c329fa6d0a0> Object activation aborted: proxy destroyed
Jul 04 08:06:12 -ThinkPad-X240 wireplumber[2023]: <WpSiAudioAdapter:0x5c329fa6d0a0> failed to activate item: Object activation aborted: >
lines 1-14/14 (END)
 
```

---

### Post by bhubunt on 2024-07-04
Just an update: I was offline for 2 hours, x240 powered off. 

I just powered on again: the welcoming sound was back when I typed in my laptop password. So was the sound on my speakers, proving that they work fine. But the sound disappeared within the space of a minute. 

What other commands do I enter into the terminal to detect the cause?

---

### Post by #&amp;thj^% on 2024-07-04
> **bhubunt said:**
> 
What other commands do I enter into the terminal to detect the cause?

```
alsa-info
```
Post that link it gives you back here.

I find Ubuntu 22.04 thru 24.04 the worst for sound problems I've yet to encounter.

Debian is fine and much better for multimedia sound/video.

And you may want to join this bug: [https://bugs.launchpad.net/ubuntu/+source/pipewire/+bug/2063150](https://bugs.launchpad.net/ubuntu/+source/pipewire/+bug/2063150)

---

### Post by bhubunt on 2024-07-04
```
  alsa-info
ALSA Information Script v 0.5.1
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  aplay
  amixer
  alsactl
  rpm, dpkg
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See '/usr/sbin/alsa-info --help' for command line options.

/usr/sbin/alsa-info: line 661: tree: command not found
/usr/sbin/alsa-info: line 661: tree: command not found
dmesg: read kernel buffer failed: Operation not permitted
Automatically upload ALSA information to www.alsa-project.org? [y/N] : y
Uploading information to www.alsa-project.org ... Done!

Your ALSA information is located at http://alsa-project.org/db/?f=57873a7b22ff4a23f4d0
Please inform the person helping you.

```

I'd like to know who "the person helping you" is supposed to be....So you think it's a bug? What do I do to unbug? I am not familiar with bug issues, but why the sudden appearance of the sound problem? It's worked fine for quite a while: I'd understand if I had recently upgraded like it seems the persons on the bug link did. No? And the bug link is about 24.04, which I am not using. I am on Ubuntu 22.04.4 LTS

---

### Post by #&amp;thj^% on 2024-07-04
> **bhubunt said:**
> 
I'd like to know who "the person helping you" is supposed to be....  Wonder what yours looks like.

Well so far that person is me....lol>>> unless you join that bug link i posted earlier.

Mine is a Lenovo Legion with a dock and a few extra gadgets, so my output would be a bit larger file to post but I will if you just have to see it.

I'm on Arch ATM so you'll have to wait till I boot to that first. :)

I'm still reading the report, so if I find any possible suggestions I'll post back.

---

### Post by bhubunt on 2024-07-04
No need to post yours, as I am not knowledgeable enough to read it.

No, I am not on the bug link because that's for people who upgraded to 24.04.  

You are indeed helping me, but why did that sentence show up on my terminal?????? Is there any indication I am not in charge of my laptop and need someone's assistance that I am dependent on?

---

### Post by #&amp;thj^% on 2024-07-04
> **bhubunt said:**
> 
You are indeed helping me, but why did that sentence show up on my terminal?????? Is there any indication I am not in charge of my laptop and need someone's assistance that I am dependent on?

Nothing to worry about, every one sees that. They just worded it to say that in a neutralist fashion.

---

### Post by bhubunt on 2024-07-04
OK. 

Several code lines I have posted on this thread often say 'permission denied.' Or else 'operation not permitted'

```
 dmesg: read kernel buffer failed: Operation not permitted 
```  

Or 

```
 Jul 04 08:06:11 me-ThinkPad-X240 wireplumber[2023]: Failed to set scheduler settings: Operation not permitted 
```

---

### Post by #&amp;thj^% on 2024-07-04
> **bhubunt said:**
> OK. 

Several code lines I have posted on this thread often say 'permission denied.' Or else 'operation not permitted'

```
 dmesg: read kernel buffer failed: Operation not permitted   
that messge came from "alsa-info"
> **bhubunt said:**
> 
Or 

[code] Jul 04 08:06:11 me-ThinkPad-X240 wireplumber[2023]: Failed to set scheduler settings: Operation not permitted 
```

And I already told you you don't run "wireplumber" in the terminal, it's a system service now.
Mine
```
wireplumber |grep "Failed to set scheduler settings" 
^CN 14:25:02.664903        wireplumber ../wireplumber/src/main.c:79:signal_handler: stopped by signal: Interrupt
W 14:25:02.665430            pw.core ../pipewire/src/pipewire/core.c:183:destroy_proxy: 0x636eb85d2860: leaked proxy 0x636eb867bbc0 id:10
W 14:25:02.665442            pw.core ../pipewire/src/pipewire/core.c:183:destroy_proxy: 0x636eb85d2860: leaked proxy 0x636eb86d8110 id:39
N 14:25:02.665544        wireplumber ../wireplumber/src/main.c:71:on_disconnected: disconnected from pipewire

```
Will you try this before I bow out here:
```
systemctl --user restart wireplumber.service
```
I would not mind seeing that output.

---

### Post by bhubunt on 2024-07-07
Hi,
Sorry, I was offline for a few days. I will answer your latest requests but first wanted to post snippets from my current morning session. When I powered on and logged in, the sound was on for a glorious few minutes, then it disappeared again. 

Perhaps there are indications as to why in the following 2 snippets from my log?

```
 07:56:50 wireplumber: [string "policy-bluetooth.lua"]:121: bad argument #1 to 'find' (string expected, got nil)
stack traceback:
    [C]: in function 'string.find'
    [string "policy-bluetooth.lua"]:121: in upvalue 'isBluez5AudioSink'
    [string "policy-bluetooth.lua"]:389: in function <[string "policy-bluetooth.lua"]:387>
07:53:23 systemd: Closed PipeWire PulseAudio.
07:53:23 systemd: Closed PipeWire PulseAudio.
07:53:23 systemd: Stopped PipeWire PulseAudio.
07:53:23 systemd: Stopping PipeWire PulseAudio...
07:53:23 wireplumber: [string "policy-bluetooth.lua"]:121: bad argument #1 to 'find' (string expected, got nil)
stack traceback:
    [C]: in function 'string.find'
    [string "policy-bluetooth.lua"]:121: in upvalue 'isBluez5AudioSink'
    [string "policy-bluetooth.lua"]:389: in function <[string "policy-bluetooth.lua"]:387>
07:53:23 wireplumber: [string "policy-bluetooth.lua"]:121: bad argument #1 to 'find' (string expected, got nil)
stack traceback:
    [C]: in function 'string.find'
    [string "policy-bluetooth.lua"]:121: in upvalue 'isBluez5AudioSink'
    [string "policy-bluetooth.lua"]:389: in function <[string "policy-bluetooth.lua"]:387>
07:53:07 wireplumber: <WpSiAudioAdapter:0x64df77c460b0> failed to activate item: Object activation aborted: proxy destroyed
07:53:07 wireplumber: <WpSiAudioAdapter:0x64df77c460b0> Object activation aborted: proxy destroyed
07:53:06 wireplumber: [string "policy-bluetooth.lua"]:121: bad argument #1 to 'find' (string expected, got nil)
stack traceback:
    [C]: in function 'string.find'
    [string "policy-bluetooth.lua"]:121: in upvalue 'isBluez5AudioSink'
    [string "policy-bluetooth.lua"]:389: in function <[string "policy-bluetooth.lua"]:387>
07:53:06 systemd: Started PipeWire PulseAudio.
07:52:53 wireplumber: <WpSiAudioAdapter:0x6281397c4080> failed to activate item: Object activation aborted: proxy destroyed
07:52:53 wireplumber: <WpSiAudioAdapter:0x6281397c4080> failed to activate item: Object activation aborted: proxy destroyed
07:52:53 wireplumber: <WpSiAudioAdapter:0x6281397c4080> Object activation aborted: proxy destroyed
07:52:52 systemd: Started PipeWire PulseAudio.
07:52:52 systemd: Started PipeWire PulseAudio.
07:52:52 systemd: Listening on PipeWire PulseAudio.
07:52:48 kernel: snd_hda_codec_realtek hdaudioC1D0:      Internal Mic=0x12
07:52:48 kernel: snd_hda_codec_realtek hdaudioC1D0:      Internal Mic=0x12
07:52:48 kernel: snd_hda_codec_realtek hdaudioC1D0:      Mic=0x1a
07:52:48 kernel: snd_hda_codec_realtek hdaudioC1D0:      Dock Mic=0x19
07:52:48 kernel: snd_hda_codec_realtek hdaudioC1D0:    inputs:
07:52:48 kernel: snd_hda_codec_realtek hdaudioC1D0:    mono: mono_out=0x0
07:52:48 kernel: snd_hda_codec_realtek hdaudioC1D0:    hp_outs=2 (0x16/0x15/0x0/0x0/0x0)
07:52:48 kernel: snd_hda_codec_realtek hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
07:52:48 kernel: snd_hda_codec_realtek hdaudioC1D0: autoconfig for ALC3232: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
07:52:48 kernel: snd_hda_intel 0000:00:03.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
```

---

### Post by bhubunt on 2024-07-07
Snippet #2: More code from the same log of the session currently still running

```
 07:53:23 systemd: Closed PipeWire Multimedia System Socket.
07:53:23 systemd: Closed PipeWire Multimedia System Socket.
07:53:23 systemd: Closed PipeWire PulseAudio.
07:53:23 systemd: Stopped PipeWire Multimedia Service.
07:53:23 systemd: Stopping PipeWire Multimedia Service...
07:53:23 systemd: Stopped PipeWire PulseAudio.
07:53:23 wireplumber: disconnected from pipewire
07:53:23 systemd: Stopping PipeWire PulseAudio...
07:53:23 systemd: Stopping PipeWire PulseAudio...
07:53:06 systemd: Started PipeWire PulseAudio.
07:53:06 systemd: Started PipeWire Multimedia Service.
07:53:06 systemd: Listening on PipeWire Multimedia System Socket.
07:53:06 systemd: Listening on PipeWire PulseAudio.
07:52:52 systemd: Started PipeWire PulseAudio.
07:52:52 systemd: Started PipeWire Multimedia Service.
07:52:52 systemd: Listening on PipeWire Multimedia System Socket.
07:52:52 systemd: Listening on PipeWire PulseAudio.
07:52:52 systemd: pipewire-session-manager.service: Cannot add dependency job, ignoring: Unit pipewire-session-manager.service failed to load properly, please adjust/correct and reload service manager: File exists 
```

---

### Post by bhubunt on 2024-07-07
And here's another snippet from the same log of the session still running, relating to wireplumber, which, as you reminded me, is a system service. 

```
  08:20:26 pipewire-pulse: mod.protocol-pulse: client 0x6086e877fb30 [Chromium]: ERROR command:-1 (invalid) tag:4294967295 error:25 (Input/output error)
08:20:26 wireplumber: <WpSiAudioAdapter:0x5edf0418d040> failed to activate item: Object activation aborted: proxy destroyed
07:53:25 NetworkManager: <info>  [1720331605.8603] policy: set 'Wired connection 1' (enp0s25) as default for IPv4 routing and DNS
07:53:23 systemd: Closed PipeWire Multimedia System Socket.
07:53:23 wireplumber: disconnected from pipewire
07:53:23 systemd: Stopping PipeWire PulseAudio...
07:53:23 wireplumber: [string "policy-bluetooth.lua"]:121: bad argument #1 to 'find' (string expected, got nil)
stack traceback:
    [C]: in function 'string.find'
    [string "policy-bluetooth.lua"]:121: in upvalue 'isBluez5AudioSink'
    [string "policy-bluetooth.lua"]:389: in function <[string "policy-bluetooth.lua"]:387>
07:53:21 NetworkManager: <info>  [1720331601.5237] device (enp0s25): Activation: starting connection 'Wired connection 1' (7222c1a3-7bf2-3431-a7e1-1a7af06ecc0f)
07:53:21 NetworkManager: <info>  [1720331601.5237] device (enp0s25): Activation: starting connection 'Wired connection 1' (7222c1a3-7bf2-3431-a7e1-1a7af06ecc0f)
07:53:21 NetworkManager: <info>  [1720331601.5227] policy: auto-activating connection 'Wired connection 1' (7222c1a3-7bf2-3431-a7e1-1a7af06ecc0f)
07:53:07 wireplumber: <WpSiAudioAdapter:0x64df77c460b0> failed to activate item: Object activation aborted: proxy destroyed
07:53:06 systemd: Started PipeWire PulseAudio.
07:52:53 wireplumber: <WpSiAudioAdapter:0x6281397c4080> failed to activate item: Object activation aborted: proxy destroyed
07:52:52 dbus-daemon: [system] Activating via systemd: service name='org.freedesktop.RealtimeKit1' unit='rtkit-daemon.service' requested by ':1.34' (uid=126 pid=1353 comm="/usr/bin/wireplumber " label="unconfined")
07:52:52 systemd: Started PipeWire PulseAudio. 
```

---

### Post by bhubunt on 2024-07-07
Here's the output you requested

```

me-ThinkPad-X240:~$ systemctl --user restart wireplumber.service
me-ThinkPad-X240:~$ 

```

And here is the output saying wireplumber could not be found

```
 me-ThinkPad-X240:~$ systemctl  status wireplumber
Unit wireplumber.service could not be found.

  
```

I looked at this page [https://gist.github.com/the-spyke/2de98b22ff4f978ebf0650c90e82027e?permalink_comment_id=4116017](https://gist.github.com/the-spyke/2de98b22ff4f978ebf0650c90e82027e?permalink_comment_id=4116017) , followed all steps, then entered the following command line -- but there is still no sound from the speakers.... 

```
  ThinkPad-X240:~$ LANG=C pactl info | grep '^Server Name'
Server Name: PulseAudio (on PipeWire 0.3.48)


```

And this: 

```
 -ThinkPad-X240:~$ systemctl --user restart wireplumber.service
me-ThinkPad-X240:~$ 
 
```

And this (I only entered the command line of step 7, explained on this site, not the other steps: [https://linuxconfig.org/how-to-install-pipewire-on-ubuntu-linux](https://linuxconfig.org/how-to-install-pipewire-on-ubuntu-linux)). Speaker sound still not working, though:
```
 $ pactl info
Server String: /run/user/1000/pulse/native
Library Protocol Version: 35
Server Protocol Version: 35
Is Local: yes
Client Index: 95
Tile Size: 65472
User Name: me
Host Name: mer-ThinkPad-X240
Server Name: PulseAudio (on PipeWire 0.3.48)
Server Version: 15.0.0
Default Sample Specification: float32le 2ch 48000Hz
Default Channel Map: front-left,front-right
Default Sink: alsa_output.pci-0000_00_1b.0.analog-stereo
Default Source: alsa_input.pci-0000_00_1b.0.analog-stereo
Cookie: 4e47:f89b

 
```

---

