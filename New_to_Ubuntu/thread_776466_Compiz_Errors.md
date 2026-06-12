---
title: "Compiz Errors"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by X Driver on 2008-04-30
I could use a little help with Compiz in the new Hardy Heron.

1) I lost the script for having Compiz start up automatically on boot. Does anyone have the Script?

2) When I run "Compiz" in terminal, I get these messages.

sam@sam-laptop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

I've reloded Compiz several times and differnt ways trying to fix various problems and it seem to store my old settings.

This all started when I was trying to get "My Video" to work in Skype (It turns to a blue screen when I start my video. It still sends images, I just can't see it on my end).

I really don't want to start over to fix it, as it did work right in the beginning, except for Skype. If I turn off all the stuff in Compiz, the camera works.

Any help would be appreciated.

Thanks,
Sam

---

### Post by Paqmann on 2008-05-01
What hardware are you using? 

Somebody correct me if I'm wrong, but I'm pretty sure that Compiz runs on startup by default in Hardy. You shouldn't need a script to turn it on. If you look in System->Preferences->Appearance->Visual Effects and choose 'Normal' or 'Extra', that activates Compiz and should remember your settings (provided you have hardware that can run it and the proper drivers for that hardware).

---

### Post by X Driver on 2008-05-01
Paqmann,

Don't I feel like an ***. I have reloaded Compiz a dozen times trying to fix a Skype problem. I messed with all the settings, including the ones above, and I must have switched it to off, causing me more headaches than I needed. Thank you. I know it was simple, but I was already committed to the line of thought that it was a major problem. I also thought that those settings didn't apply to Compiz. I had it selected on my original install, and changed it somewhere down the line.

Now, if you have any ideas on how I can fix this, I'd appreciate it.
[http://ubuntuforums.org/showthread.php?t=773099](http://ubuntuforums.org/showthread.php?t=773099)

Trying to fix this is how I got so lost.

Thanks again,
Sam

---

