---
title: "HOWTO: Install any Sound Card (Easy for absolute beginners)"
date: 2009-05-22
forum: Outdated Tutorials &amp; Tips
---

### Post by Francewhoa on 2009-05-22
If your sound card isn't automatically detected by Ubuntu 8.04.2 this is the easiest way that I know of to install & configure your sound card. It's a script made by *soundcheck*. It does all the hard manual setup process for you. If you find an easier way to do that you're welcome to share it by opening a new thread.
[B]
Requirements:[/B]

[LIST]
[*]Ubuntu 8.04.2 Desktop 32 bits
[*]SOUNDCORE compiled as a module. Find below step 1.
[/LIST]
 **Tested with:**

[LIST]
[*] ASUS XONAR DX Sound Card. Connect in a PCI Express (PCIe) expansion card.
[*] Headphones plug in FRONT OUT back port.
[/LIST]
 
**Steps for absolute beginner:**
1. To check that you have SOUNDCORE compiled as a module navigate to menu APPLICATIONS > ACCESORIES > TERMINAL

Type in the following command

```
modinfo soundcore
```Press ENTER key

If the Terminal returns a few lines of informations starting with &#8220;filename: ...&#8221; continue to next step. If Terminal returns a error message you need to recompile your kernel before continuing. 

2. [Click here to download the installation script file (AlsaUpgrade-1.0.x-rev-1.17.tar)]("http://ubuntuforums.org/attachment.php?attachmentid=114686&d=1243023514"). Download this file to your Ubuntu Desktop. 

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

7. Restart your computer by typing the following command line in TERMINAL.
```
sudo shutdown -r 0
```

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

If you don't ear a sound make sure your sound isn't mute. And navigate to Ubuntu menu SYSTEM > PREFERENCES > SOUNDS to raise all volumes to maximum. 

Enjoy:guitar::-({|=:popcorn:\\:D/

---------------------------------------------
**Source:** soundcheck's script [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

**Latest soundcheck's script can be found at the bottom of this post: **[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

**Please report bugs with the installation script to [*soundcheck*]("http://ubuntuforums.org/member.php?u=343879")**** at:** [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

---

