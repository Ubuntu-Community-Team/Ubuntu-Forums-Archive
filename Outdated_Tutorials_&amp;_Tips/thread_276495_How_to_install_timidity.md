---
title: "How to install timidity"
date: 2006-10-13
forum: Outdated Tutorials &amp; Tips
---

### Post by ekravche on 2006-10-13
Look at this link [http://www.cs.cornell.edu/~djm/ubuntu/#timidity](http://www.cs.cornell.edu/~djm/ubuntu/#timidity)

here is what it says if it ever goes down


> 
Install TiMidity (MIDI player/software synthesizer)

(See also the Midi Software Synthesis How-To.)

   1. Install Timidity:

      sudo apt-get install timidity timidity-interfaces-extra

   2. (optional) Start software synthesis by loading the appropriate modules and starting Timidity as the MIDI server:

      sudo modprobe snd-seq-device
      sudo modprobe snd-seq-midi
      sudo modprobe snd-seq-oss
      sudo modprobe snd-seq-midi-event
      sudo modprobe snd-seq
      timidity -iA -B2,8 -Os1l -s 44100

      To make software synthesis start automatically in future, first make the appropriate modules load automatically:

      sudo gedit /etc/modules

      Append the following:

      snd-seq-device
      snd-seq-midi
      snd-seq-oss
      snd-seq-midi-event
      snd-seq

      Then inform Timidity to start automatically:

      sudo gedit /etc/default/timidity

      Uncomment the line to enable the sequencer. That is, change:

      #TIM_ALSASEQ=true

      to:

      TIM_ALSASEQ=true

   3. Add a desktop entry for Timidity:

      sudo gedit /usr/share/applications/timidity.desktop

      Add:

      [Desktop Entry]
      Encoding=UTF-8
      Name=Timidity MIDI Player
      Comment=Play MIDI audio files
      Exec=timidity -ig
      Terminal=false
      Type=Application
      StartupNotify=false
      MimeType=audio/midi;
      Categories=Application;AudioVideo;
      Icon=
      #NoDisplay=true

   4. (optional) Make Timidity the default MIDI player (after first having added a desktop entry as in the previous step):

      sudo cp /usr/share/applications/defaults.list /usr/share/applications/defaults.list.backup.midi
      sudo gedit /usr/share/applications/defaults.list

      Insert/replace the audio/midi entry as follows:

      audio/midi=timidity.desktop

   5. (optional) Install high quality sound fonts:

      wget -c -O /tmp/timidity-patches-eaw [http://www.fbriere.net/debian/dists/etch/misc/deb/timidity-patches-eaw_12-0fbriere.1_all.deb](http://www.fbriere.net/debian/dists/etch/misc/deb/timidity-patches-eaw_12-0fbriere.1_all.deb)
      sudo dpkg -i /tmp/timidity-patches-eaw.deb
      sudo gedit /etc/timidity/timidity.cfg

      Change:

      source /etc/timidity/freepats.cfg

      to:

      source /usr/share/doc/timidity-patches-eaw/examples/timidity.cfg

   6. (optional) Reduce Timidity's CPU usage:

      sudo gedit /etc/timidity/timidity.cfg

      Add:

      opt EFresamp=d          #disable resampling (or "opt EFresamp=l" for linear resampling)
      opt EFvlpf=d            #disable VLPF
      opt EFreverb=d          #disable reverb
      opt EFchorus=d          #disable chorus
      opt EFdelay=d           #disable delay

      Save and close the file.

Here is a script to do steps 1 - 5 for automatically:

sudo apt-get install timidity timidity-interfaces-extra
(printf '[Desktop Entry]\nEncoding=UTF-8\nName=Timidity MIDI Player\nComment=Play MIDI audio files\nExec=timidity -ig\nTerminal=false\nType=Application\nStartupNotify=false\nMimeType=audio/midi;\nCategories=Application;AudioVideo;\n#Icon=???\n#NoDisplay=true\n') | sudo tee /usr/share/applications/timidity.desktop
sudo cp /usr/share/applications/defaults.list /usr/share/applications/defaults.list.backup.midi
if ! cat /usr/share/applications/defaults.list | grep "audio/midi"; then (printf 'audio/midi=timidity.desktop\n') | sudo tee -a /usr/share/applications/defaults.list; else sudo sed -i -e's@audio/midi.*$@audio/midi=timidity.desktop@g' /usr/share/applications/defaults.list; fi;
wget -c -O /tmp/timidity-patches-eaw [http://www.fbriere.net/debian/dists/etch/misc/deb/timidity-patches-eaw_12-0fbriere.1_all.deb](http://www.fbriere.net/debian/dists/etch/misc/deb/timidity-patches-eaw_12-0fbriere.1_all.deb)
sudo dpkg -i /tmp/timidity-patches-eaw.deb
sudo sed -i.backup -e's@source /etc/timidity/freepats.cfg@source /usr/share/doc/timidity-patches-eaw/examples/timidity.cfg@g' /etc/timidity/timidity.cfg
sudo modprobe snd-seq-device
sudo modprobe snd-seq-midi
sudo modprobe snd-seq-oss
sudo modprobe snd-seq-midi-event
sudo modprobe snd-seq
timidity -iA -B2,8 -Os1l -s 44100
(printf 'snd-seq-device\nsnd-seq-midi\nsnd-seq-oss\nsnd-seq-midi-event\nsnd-seq\n') | sudo tee -a /etc/modules
sudo sed -i -e's@#TIM_ALSASEQ=true@TIM_ALSASEQ=true@g' /etc/default/timidity


---

### Post by scunc_dvl on 2006-10-24
This looks like it's using OSS, could ALSA be used instead?

---

