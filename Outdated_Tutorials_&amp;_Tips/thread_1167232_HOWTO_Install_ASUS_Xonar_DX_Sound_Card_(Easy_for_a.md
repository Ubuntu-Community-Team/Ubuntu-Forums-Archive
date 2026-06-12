---
title: "HOWTO: Install ASUS Xonar DX Sound Card (Easy for absolute beginners)"
date: 2009-05-22
forum: Outdated Tutorials &amp; Tips
---

### Post by Francewhoa on 2009-05-22
**Requirements:**

[LIST]
[*]Ubuntu 8.0.4.2 Desktop 32 bits
[*]SOUNDCORE compiled as a module. Find below step 1.
[*]The ASUS XONAR DX power cord must be connected to your computer motherboard. The card needs additional power to work properly. Find your Xonar DX user manual for details.
[/LIST]
 **Tested with:**
Headphones plug in FRONT OUT back port.

**Steps for absolute beginner:**
1. To check that you have SOUNDCORE compiled as a module navigate to menu APPLICATIONS > ACCESORIES > TERMINAL

Type in the following command

```
modinfo soundcore
```Press ENTER key

If the Terminal returns a few lines of informations starting with “filename: ...” continue to next step. If Terminal returns a error message you need to recompile your kernel before continuing. 

2. [Click here to download the installation script file (AlsaUpgrade-1.0.x-rev-1.17.tar)]("http://ubuntuforums.org/attachment.php?attachmentid=114681&stc=1&d=1243021538"). Download this file to your Ubuntu Desktop. 

3. To run the following commands as ROOT navigate to menu APPLICATIONS > ACCESORIES > TERMINAL
Type in the following command.

    ```
sudo -s
```TERMINAL will ask for your Ubuntu password. Type it in. Press ENTER key.

4. You must replace the below xxxxxxxxxxxx with your Ubuntu username.

Type in the following 3 commands. Press ENTER key after each command. 

        ```
cd /home/xxxxxxxxxxxx/Desktop/
tar xvf AlsaUpgrade-1.0.x-rev-1.17.tar
./AlsaUpgrade-1.0.x-rev-1.17.sh -di
```5. TERMINAL will display the following line: *Choose Alsa Package (1) 1.0.20 default[1]: *

Type in the following command. Then press ENTER key. 

```
1
```6. TERMINAL will display the following line: *Upgrade in progress..The process can take up to 15minutes.....Be patient! *

The installation is in progress. Leave the TERMINAL window open.

Wait. The process can take up to 15 minutes.

When TERMINAL is done installing it will display the following line: *root@xxxxxxxxxxxxx:~/Desktop#*

7. Restart your computer. 

8. Testing if ALSA is working using the Alsa player application:

In the same TERMINAL type in the following command. Then press ENTER key. 

        ```
aplay -l
```TERMINAL will return information about your sound card.

9. To test your sound card. 

Plug-in your headphones in FRONT OUT back port of the sound card.

Navigate to Ubuntu menu SYSTEM > PREFERENCES > SOUNDS

A new window will open.

Click on the Sound Events TEST button. You should ear a sound in your headphone.

Click on the Music and Movies TEST button. You should ear a sound in your headphone.

Click on the Audio Conferencing TEST button. You should ear a sound in your headphone.

If you don't ear a sound make sure your sound isn't mute.                                  And navigate to Ubuntu menu SYSTEM > PREFERENCES > SOUNDS to raise all volumes to maximum. 

Enjoy:guitar::-({|=:popcorn:\\:D/

---------------------------------------------
**Source:** soundcheck's script [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

**Latest soundcheck's script can be found at the bottom of this post: **[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

**Please report bugs with the installation script to [*soundcheck*]("http://ubuntuforums.org/member.php?u=343879")**** at:** [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

---

