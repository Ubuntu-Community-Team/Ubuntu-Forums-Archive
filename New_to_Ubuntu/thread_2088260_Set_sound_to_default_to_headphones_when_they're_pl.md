---
title: "Set sound to default to headphones when they're plugged in?"
date: 2012-11-26
forum: New to Ubuntu
---

### Post by quiksilverlives on 2012-11-26
Recent fresh install of 12.10 on a Sony Vaio T Series laptop. Toz helped me solve the brightness issue that seems to plague Sony laptops. 

I've just plugged in my wireless headphones' USB connector. If I go into sound and choose them, they work fine. But if I unplug them and plug them back in, I have to go back in and choose them again.

Is there a way to tell it to always use them when they're plugged in, and to default back to the built in speakers in the absence of headphones? If it matters, they are Logitech H600 wireless headphones, and the connector appears to be USB 3.0.

---

### Post by quiksilverlives on 2012-11-26
Posted this late at night, so bumping it this morning.

---

### Post by DuckHook on 2012-11-26
Same headphones, same issue. I don't mind the inconvenience of reconfiguring, but agree that it would be nice to have the convenience. Am not on my regular machine for a few days, but a google search turned up this:

[http://askubuntu.com/questions/153438/unable-to-make-sound-play-in-headset](http://askubuntu.com/questions/153438/unable-to-make-sound-play-in-headset)

Also this:

[http://askubuntu.com/questions/113704/make-pulseaudio-prefer-external-audio-device](http://askubuntu.com/questions/113704/make-pulseaudio-prefer-external-audio-device)

Will delve further and try solution when I get home.

---

### Post by quiksilverlives on 2012-11-27
Ok, I read both of those, and it seems that the second link is closer to what I'm experiencing...but I have to be honest, I didn't understand the solution. Too much of a noob, I think.

---

### Post by DuckHook on 2012-11-27
> **quiksilverlives said:**
> ...to be honest, I didn't understand the solution

Not to worry. The thread is rather cryptic for new users. It boils down to this:

There is no "solution" and removal of the USB adapter will always shift the default audio output back to the built-in speakers. However, by running the scripts that the writer has attached, the output can be quickly rerouted to the USB device after the adapter has been inserted. Linux allows such scripts to be attached to a desktop icon or a launcher bar icon, so it can be a simple one-click process to switch outputs. Creating such icons is not hard but rather more involved than the time I currently have to explain. As mentioned, I am away from home for a few days and not using my regular machine. Will post more complete instructions next week.

If any of the resident gurus sees this post, feel free to help OP with creation of .desktop icon and script attachment.

---

### Post by BongoRongo on 2012-11-27
Don't remember exactly, but think you can use Cuttlefish to work it out.
[http://www.omgubuntu.co.uk/2012/09/automate-ubuntu-with-cuttlefish](http://www.omgubuntu.co.uk/2012/09/automate-ubuntu-with-cuttlefish)

Haven't tried the app yet, but when i read the article, I figured out it would help med in setting right audio automatically when connecting my laptop to TV with HDMI.

---

### Post by quiksilverlives on 2012-11-28
Thanks for the responses, guys. Bongorongo, that says it's only available for 12.04. Will it run on 12.10 anyway? I hesitate to do that, but I don't know, maybe it's fine.

---

### Post by stinkeye on 2012-11-29
I use this script to toggle between headphones and speakers.
The script cycles through all your output devices.
For most people its just 2...speakers and headphone.
I also have an external usb sound card for recording as well as an internal sound card and usb headphones so it cycles through all 3.

Copy into gedit and save as **audio-device-switch** to your home directory in a folder named scripts.
Create the scripts folder if you don't have one.
```
#!/bin/bash

declare -i sinks=(`pacmd list-sinks | sed -n -e 's/\**[[:space:]]index:[[:space:]]\([[:digit:]]\)/\1/p'`)
declare -i sinks_count=${#sinks[*]}
declare -i active_sink_index=`pacmd list-sinks | sed -n -e 's/\*[[:space:]]index:[[:space:]]\([[:digit:]]\)/\1/p'`
declare -i next_sink_index=${sinks[0]}

#find the next sink (not always the next index number)
declare -i ord=0
while [ $ord -lt $sinks_count ];
do
    echo ${sinks[$ord]}
    if [ ${sinks[$ord]} -gt $active_sink_index ] ; then
        next_sink_index=${sinks[$ord]}
        break
    fi
    let ord++
done

#change the default sink
pacmd "set-default-sink ${next_sink_index}"


#move all inputs to the new sink
for app in $(pacmd list-sink-inputs | sed -n -e 's/index:[[:space:]]\([[:digit:]]\)/\1/p');
do
    pacmd "move-sink-input $app $next_sink_index"
    
done

#display notification
declare -i ndx=0
pacmd list-sinks | sed -n -e 's/device.description[[:space:]]=[[:space:]]"\(.*\)"/\1/p' | while read line;
do
    if [ $(( $ord % $sinks_count )) -eq $ndx ] ; then
        notify-send -i notification-audio-volume-high --hint=string:x-canonical-private-synchronous: "Sound output switched to" "$line"
        exit
    fi
    let ndx++
done;
```

Now navigate to ~/scripts/audio-device-switch and right click on it
Properties > Permissions and mark execute.
("~" is short for your home folder. eg for me **[COLOR="Red"]~[/COLOR]/scripts/audio-device-switch**
is the same as **[COLOR="red"]/home/glen[/COLOR]/scripts/audio-device-switch**)

Now to test, left click on audio-device-switch and choose run.


If the script works you can then make a launcher.
Open gedit and copy and paste this. Dont save yet. 
```
[Desktop Entry]
Type=Application
Version=1.0
Hidden=false
Terminal=false
Icon=[COLOR="Magenta"]/home/glen/Pictures/sound.png[/COLOR]
Name=Audio-Device-Switch
Exec=/home/[COLOR="DarkOrange"]glen[/COLOR]/scripts/audio-device-switch
```

[COLOR="Magenta"]Edit this line[/COLOR] to point to an image of your choosing. (I just searched google images for sound.png)
[COLOR="DarkOrange"]Edit this line[/COLOR] to show your user name.
Now save as **Audio-Device-Switch.desktop** to **~/.local/share/applications**

You can now add to the launcher by navigating to ~/.local/share/applications
and drag and dropping **Audio-Device-Switch.desktop** to the launcher.

You can't open .desktop files directly so if you need to edit again,
open gedit and drag and drop **~/.local/share/applications/Audio-Device-Switch.desktop** into it.

---

### Post by BongoRongo on 2012-11-30
Hmm.. 
Looks like it works fine in 12.10, but without updates.
More explained here:
[https://answers.launchpad.net/cuttlefish/+question/213205](https://answers.launchpad.net/cuttlefish/+question/213205)

I also found this: How to enable indicator applet for cuttlefish
[http://www.omgubuntu.co.uk/2012/09/how-to-enable-cuttlefish-mono-indicator-icon](http://www.omgubuntu.co.uk/2012/09/how-to-enable-cuttlefish-mono-indicator-icon)

---

