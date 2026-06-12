---
title: "Asus G73J subwoofer detection on 15.04"
date: 2015-08-01
forum: New to Ubuntu
---

### Post by michael305 on 2015-08-01
The G73J has an awesome sound system for a notebook...when the subwoofer works. Mine does not.

I'm new to Ubuntu (I'm just installed 15.04), and I have no idea how to diagnose the problem. I don't know if it's a hardware or driver problem. I don't know even know where to locate the driver information. I'm certainly willing to do my own research to keep up with any responses I get, but I'm excited to learn Ubuntu and would appreciate any help you can give me.

[SIZE=4]***Problem:***[/SIZE]

Where did my subwoofer go? I went into the sound settings. The speakers that are working can be Left/Right balanced, but the adjustment bar for the subwoofer isn't even lit up. Does that mean it's not detected, or that it is detected and not being included by the driver?

---

### Post by mindtab2 on 2015-10-29
[TABLE="width: 500"]
[TR]
[TD]Configuration:

Laptop: Asus Zenbook UX51VZA
OS: Ubuntu 14.04.3 (lsb_release -a), kernel: 3.019.031 (uname -r)

Problem: External subwoofer doesn't work or not recognized

Resolution:

a. Add line at the bottom of alsa-base.conf 
    
    -->sudo gedit /etc/modprobe.d/alsa-base.conf
    line at bottom-->    options snd-hda-intel model=auto

b. No need to change anything in /etc/pulse/default.pa

c. Edit daemon.conf file
    --> sudo gedit /etc/pulse/daemon.conf
    -->    take out the ";" and change to yes from this line 
            enable-lfe-remixing = yes

    -->unmark line / edit / or add as necessary in order to have
        default-channel-map = front-left,front-right,lfe

--------------------------- if you only have your internal laptop speaker and the subwoofer -------------
d. Add below block of lines to extra-hdmi.conf file
    ---> sudo -H gedit /usr/share/pulseaudio/alsa-mixer/profile-sets/extra-hdmi.conf
        [Mapping analog-surround-21]
        device-strings = surround40:%f 
        channel-map = front-left,front-right,lfe
        paths-output = analog-output analog-output-speaker analog-output-desktop-speaker
        priority = 7
        direction = output


    ---> sudo gedit /usr/share/pulseaudio/alsa-mixer/profile-sets/default.conf
        <add here same block as above>

---------------------------------------------------------------------------------------------------------
        
  
1. Install pavucontrol <advanced sound settings utility >
    --> sudo apt-get install pavucontrol

2. Install alsa-utils-gui
    --> sudo apt-get install alsa-utils-gui
    
3. Install hdajackretask
    --> sudo add-apt-repository ppa:diwic/hda && sudo apt-get update
 
     --> sudo apt-get install hda-jack-retask
    
    --> (type this command to open program from $ ) hdajackretask

    --> select/checkmark "Show unconnected pins", checkmark 'Advanced Override'
        Go down to 'Not Connected', Pin 0x16,  select Location: External, Device: Speaker, Jack:Other Analog, Channel: 5, Channel Group: 'Center (LFE). Click 'Apply Now'.

Now Unselect 'Advanced Override'. 

Go back through the list until you reach Pin 0x16. It should be checked,  but the option shows blank. Choose INTERNAL SPEAKER (LFE) from the  Drop-down list. Click Apply now and Install boot override.
        

NOTE: to check your possible pin setting for the subwoofer, get this
    --> sudo apt-get install snd-hda-tools

        then type command:  
sudo hda-jack-sense-test -as   
(first with subwoofer plugged in, ...look for a YES in the pin line, then with the subwoofer disconnected) 

NOTE2: mine showed the subwoofer when connected as being on pin 0x1e. But, I decided to leave it on pin 0x16.  

REBOOT computer.

4. Open Pavucontrol 
    - go to Configuration tab and choose 'Analog Surround 2.1 Output + Analog Input' (or if you have other configuration, like front/rear speaker, than 4.1, or front/center/rear 5.1, etc)

    - go to Output Devices and Select 'Speakers' in the dropdown option 'PORT'.  Adjust your volumes as necessary

5. Check alsamixer volumes, especially the Master and BASS ones. Move across options with right arrow key. If you see MM for a device, press 'M' to unmute. Then up arrow key to raise volume
    ---> type command :   alsamixer
[/TD]
[/TR]
[/TABLE]

---

### Post by mindtab2 on 2015-10-29
One correction:
[Mapping analog-surround-21]
        device-strings = surround40:%f 
        channel-map = front-left,front-right,lfe, lfe

Note : added another lfe to channel-map. You will have 2 subwoofer levels showing, but you can just reduce the subwoofer left to zero and work with just subwoofer right level

Also, in step 3, in advanced override, Location is Internal, not External

---

