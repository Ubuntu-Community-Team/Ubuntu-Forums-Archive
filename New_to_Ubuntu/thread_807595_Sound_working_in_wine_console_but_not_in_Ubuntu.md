---
title: "Sound working in wine console but not in Ubuntu"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Lizard787 on 2008-05-25
Well there's this game Ragnarok 2 that I was going to play and it requires a .bat file to run so after a little digging around i found to use wineconsole in Terminal. So it launches the game and I somehow have sound. But I shouldn't have sound. I have a Satellite P105-S6024 it's somthing with the ACPI but i've kept it on because i need to know battery life. But how is it I have sound when running somthing through wineconsole. And wine says I don't even have a sound card. 
PS: Card:HDA Intel
Chip:Conexant CX20551
With that is there a way of having sound in Ubuntu because wouldn't the ACPI still mess up the sound or not?

---

### Post by ZabiGG on 2008-05-26
Right-click on the speaker icon in your panel and select Volume control. Check if the volume of  every relevant option is activated.

If everything checks out, go in System > Preferences > Sound
Set the first three options to Autodetect
Set the device appropriate for your system (Alsa mixer is your best bet)
Click each test button to see if you hear sound. 

If you don't hear anything, follow the instructions presented in the post below:

[http://ubuntuforums.org/showpost.php?p=4450631&postcount=5](http://ubuntuforums.org/showpost.php?p=4450631&postcount=5)

Hope this helps,

Z.

---

### Post by Lizard787 on 2008-05-26
Updating alsa didn't work however now i hear very quiet static noise. Now however the sound in the game doesn't play anymore. For configuring alsabase I couldn't find my codec listed a Conexant CX20551. And when I go into system>Preferencs>sound when I try testing on them they all fail. Here is the Error Message:
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

It says I have two device's one is an HDA Intel(Alsa mixer) and the other is Conexant CX20551 (Waikiki) (OSS Mixer). Neither work and i looked in alsa mixer and they all are unmuted. I also just tried this: [https://answers.launchpad.net/ubuntu/+source/linux-source-2.6.22/+question/21847](https://answers.launchpad.net/ubuntu/+source/linux-source-2.6.22/+question/21847)
the very bottom fix but I can't find the line in /etc/modprobe.d/alsa-base
The sound Preferences sound works. When i play videos in Totem music player I hear sound fine but when I try and use like youtube which uses flash I get no sound.

---

### Post by ZabiGG on 2008-05-27
Did you install ALSA mixer?

---

