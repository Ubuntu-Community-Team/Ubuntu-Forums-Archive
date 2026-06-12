---
title: "Howto: Pulseadio and VMWare with 2 soundcards"
date: 2009-03-02
forum: Outdated Tutorials &amp; Tips
---

### Post by bobdevis on 2009-03-02
Ok this is for everyone who had no luck with other Pulseaudio + VMWare solutions or who doesn't want to mess too much with the default settings.
I have done this with Ubuntu 8.10, but this solution should apply to any Linux running Pulseadio and is very easy to reverse, so there is little chance of breaking more then you solve.
Also, trouble with any other app that can not work with Pulseadio is solved with this setup.

You need a free PCI (or PCIe 1x) slot, so this is not for laptops.
This will cost you between 20 and 0 bucks depending on how much extra hardware you have lying around and how cheap you can get stuff.

You are going to need one extra soundcard and a cable to loop the audio-out (green) of one of the cards to the line-in (blue) of the other. This cable has 2 identical audio jacks at both ends.

1. Install the extra soundcard.

2. Boot back into your system and check what you have when you type 'ls /dev/dsp*' into the console. You should have a dsp and a dsp1 or some such.
If you don't see 2 audio devises, your other card is not recognized yet and you'll have to figure out why.

3. Go to your package manager and install the 'pavucontrol' and 'padevchooser' packages if they aren't there already.
Close the package manager window.

4. Start padevchooser. You will have a little audio jack icon in your systray now. Click on it and go to the 'Configure Local Sound Server' option. You will have a window with 3 tabs. Uncheck all boxes in all tabs.
Close the window.
Close padevchooser.

5. Start pavucontrol and go to the 'Output Devises' tab. Set your primary audio card as default with the little down arrow icon.
Close pavucontrol.

6. Close all apps that make sound and kill Pulseaudio with with the 'killall pulseaudio' command.
 
7.  Start VMWare. Now you can figure out witch of your cards is dsp or dsp1 with directing the virtual sound to either dsp or dsp1 and checking it with your speakers when you play a sound inside your virtual machine.
Leave the settings directing the sound to your secondary soundcard.

8. Now use the audio loop cable to loop from the audio-out of your secondary card to the line-in of your primary one.
Leave the mic-in and audio-out cables of your primary card just the way they were when you started this guide.

9. Start 'pulseadio' while your VM is still playing music. Pulseadio will fail to hook on your secondary soundcard and just uses the primary one.
(Don't close the console window you started Pulseadio in until you reboot)

10. It should all work now. Pulse only hooks on your primary card and the sound feed from the VM goes to your secondary (and is looped to your primary one though the line-in).
Even after reboot, Pulseadio should leave your secondary card alone now.

11. If your virtual OS is Windows, go to Control Panel>Sound and Audio> Audio>Sound Playback>Advanced>Performance 
Set the hardware acceleration to None and the Sample rate conversion quality to Low. This should remove/reduce the sound stutter.

I hope this guide helps!
Cheers!
Bob.

---

