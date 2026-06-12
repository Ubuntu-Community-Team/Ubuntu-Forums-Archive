---
title: "Bluetooth JBL Wave Flex Headphones Connect in Mono on Ubuntu Until Manually Disconnec"
date: 2024-06-02
forum: New to Ubuntu
---

### Post by fedef098 on 2024-06-02
[FONT=Verdana]Hello everyone,[/FONT]
[FONT=Verdana]I'm experiencing an issue with my Bluetooth JBL Wave Flex headphones on Ubuntu. When I connect them, they automatically set to mono (HFP) mode, which affects the audio quality. However, if I manually disconnect the headphones from Bluetooth and reconnect them, they correctly switch to stereo (A2DP) mode, and the audio quality improves significantly.[/FONT]
[FONT=Verdana]I've tried several solutions, including creating scripts and udev rules to force the connection in A2DP mode, but I haven't found a definitive solution. Below are the steps I've taken and the configurations I've tried:[/FONT][FONT=Verdana]
[/FONT][FONT=Verdana]
[/FONT][FONT=Verdana]Using pavucontrol, I was able to change the profile to "High Fidelity Playback (A2DP)", but this setting doesn't persist after disconnecting and reconnecting the headphones.[/FONT][FONT=Verdana]
[/FONT][FONT=Verdana]
[/FONT][FONT=Verdana]Scripts and udev rules:[/FONT]
[FONT=Verdana]I created a script to automatically change the audio profile when the headphones are connected:[/FONT][FONT=Verdana]

[/FONT]
[FONT=Verdana]#!/bin/bash[/FONT]
[FONT=Verdana]LOGFILE="/home/federico/set_a2dp.log"[/FONT]
[FONT=Verdana]DEVICE_ID="bluez_card.70_50_E7_52_7C_DE"[/FONT]
[FONT=Verdana]MAX_RETRIES=10[/FONT]

[FONT=Verdana]echo "$(date) - Script started" >> $LOGFILE[/FONT]

[FONT=Verdana]# Function to check if PulseAudio is ready[/FONT]
[FONT=Verdana]is_pulseaudio_ready() {[/FONT]
[FONT=Verdana]    pacmd stat >/dev/null 2>&1[/FONT]
[FONT=Verdana]    return $?[/FONT]
[FONT=Verdana]}[/FONT]

[FONT=Verdana]# Wait for PulseAudio to be ready[/FONT]
[FONT=Verdana]for i in $(seq 1 $MAX_RETRIES); do[/FONT]
[FONT=Verdana]    if is_pulseaudio_ready; then[/FONT]
[FONT=Verdana]        echo "$(date) - PulseAudio is ready" >> $LOGFILE[/FONT]
[FONT=Verdana]        break[/FONT]

[FONT=Verdana]The udev rule to run the script when the headphones are connected.[/FONT][FONT=Verdana]

[/FONT]
[FONT=Verdana]sudo nano /etc/udev/rules.d/99-bt-a2dp.rules[/FONT]

[FONT=Verdana]Content:[/FONT]

[FONT=Verdana]ACTION=="add", SUBSYSTEM=="bluetooth", KERNEL=="hci0:512|hci0:513", RUN+="/home/federico/set_a2dp.sh"[/FONT]


[FONT=Verdana]Checking permissions:[/FONT]

[FONT=Verdana]chmod +x /home/federico/set_a2dp.sh[/FONT]

[FONT=Verdana]Log verification:[/FONT]
[FONT=Verdana]Despite these attempts, the log shows that PulseAudio is not ready when the script runs:[/FONT]

[FONT=Verdana]Fri May 31 21:16:04 -03 2024 - Script started[/FONT]
[FONT=Verdana]Fri May 31 21:16:04 -03 2024 - Waiting for PulseAudio (attempt 1/10)[/FONT]
[FONT=Verdana]...[/FONT]
[FONT=Verdana]Fri May 31 21:16:24 -03 2024 - Changing profile to A2DP for bluez_card.70_50_E7_52_7C_DE[/FONT]
[FONT=Verdana]No PulseAudio daemon running, or not running as a session daemon.[/FONT]

[FONT=Verdana]Manual connection:[/FONT]
[FONT=Verdana]Currently, the only way to get the headphones to connect in stereo mode is to manually disconnect them from the Bluetooth interface and reconnect them.[/FONT]

[FONT=Verdana]I don't think I should have to use a script to disconnect and reconnect the headphones. Bluetooth should connect in stereo by default.[/FONT]
[FONT=Verdana]If anyone has a solution or any suggestions to resolve this issue automatically, I would greatly appreciate it![/FONT]
[FONT=Verdana]Thanks in advance for any help you can provide.[/FONT]
[FONT=Verdana]Best regards,[/FONT][FONT=Verdana]
[/FONT][FONT=Verdana]Federico[/FONT]

---

