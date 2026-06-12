---
title: "JBL Wave Flex Bluetooth Headphone Connect in Mono on Ubuntu Until Manually Disconnect"
date: 2024-10-19
forum: New to Ubuntu
---

### Post by cirocristhian on 2024-10-19
Hello guys,

I'm encountering an issue with my JBL Wave Flex Bluetooth headphones on Ubuntu. Upon connection, they default to mono (HFP) mode, significantly degrading audio quality. However, if I manually disconnect and reconnect the headphones, they switch to stereo (A2DP) mode, and the sound improves noticeably.

I've tried multiple solutions, including scripts and udev rules, to force the A2DP profile on connection, but nothing seems to work consistently. Here&#8217;s what I&#8217;ve attempted so far:

**Changing Profile with pavucontrol: **Using pavucontrol, I can manually switch the profile to "High Fidelity Playback (A2DP)", but this setting doesn't persist after disconnecting and reconnecting the headphones.

**Scripts and udev Rules: **I created a script to automatically change the audio profile when the headphones connect:

```
bash

#!/bin/bash
LOGFILE="/home/federico/set_a2dp.log"
DEVICE_ID="bluez_card.70_50_E7_52_7C_DE"
MAX_RETRIES=10

echo "$(date) - Script started" >> $LOGFILE

# Function to check if PulseAudio is ready
is_pulseaudio_ready() {
    pacmd stat >/dev/null 2>&1
    return $?
}

# Wait for PulseAudio to be ready
for i in $(seq 1 $MAX_RETRIES); do
    if is_pulseaudio_ready; then
        echo "$(date) - PulseAudio is ready" >> $LOGFILE
        break
    fi
done

```

**Udev Rule:**To trigger the script when the headphones connect:

```
bash

sudo nano /etc/udev/rules.d/99-bt-a2dp.rules

```

[B]Rule Content:
[/B]
```
makefile
ACTION=="add", SUBSYSTEM=="bluetooth", KERNEL=="hci0:512|hci0:513", RUN+="/home/federico/set_a2dp.sh"


```

[B]Permissions:
[/B]
```
bash

chmod +x /home/federico/set_a2dp.sh

```

**Log Verification: **Despite my efforts, the logs show PulseAudio isn't ready when the script runs:

```
yaml

Sat Oct 19 11:22:04 -03 2024 - Script started
Sat Oct 19 11:22:04 -03 2024 - Waiting for PulseAudio (attempt 1/10)
...
Sat Oct 19 11:22:24 -03 2024 - Changing profile to A2DP for bluez_card.70_50_E7_52_7C_DE
No PulseAudio daemon running, or not running as a session daemon.

```

**Manual Connection: **At the moment, the only way to ensure stereo mode is to manually disconnect and reconnect the headphones via the Bluetooth interface.
I don&#8217;t think I should need to use a script to handle this. Ideally, Bluetooth should connect in stereo by default. If anyone has a more efficient solution or any suggestions to automate this, I&#8217;d greatly appreciate your input!
Thanks in advance for your help.
Best regards,
Cristhian [RIGHT][SIZE=1][[COLOR=#ebece4]tubidy[/COLOR]]("https://tubidycom.org.za") [[COLOR=#ebece4]tubidy[/COLOR]]("https://tubidymobi.org.za")[/SIZE][/RIGHT]

---

