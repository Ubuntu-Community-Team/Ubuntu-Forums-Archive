---
title: "Angry IP Scanner"
date: 2013-01-05
forum: New to Ubuntu
---

### Post by MyTinFoilHat on 2013-01-05
I found a cool tool on SourceForge called Angry IP Scanner (located here: [http://sourceforge.net/projects/ipscan/](http://sourceforge.net/projects/ipscan/)). I downloaded and installed via Ubuntu Software Center dialogue option. My objective was to enable my ability to see what devices are currently connected to the home network. 

When I attempted to open the app, I got a dialogue that reads, "Failed to load native code. Probably you are using a binary build for wrong OS or CPU - try downloading both 32-bit and 64-bit binaries." Okay. Fine. 

My thinking is to remove the app and find the correct one. Problem is, the app doesn't show up in my "Installed" within Software-Center. In Dash, I can alt-click the app and see the "Launch" option, but not the "Uninstall" option. 

I'm a tad concerned at the lack of ability to remove the app via gui. (I have to rely on it as my CLI skills are still in development). I could use a helpful hand in locating the app and removing it.

Honestly, I'm trying not to be overly paranoid about this... Advice will be helpful also...

Thanks in advance.

---

### Post by iMac71 on 2013-01-05
you might try to proceed as follows:
- open a Terminal window and type in it (or copy from here and paste in it) the following command:```
gksudo gedit /var/log/apt/history.log
```- after that the file has been loaded in gedit, press [CTRL]-[F] and type in the search field at least some letters of the name of the application you're looking for
- when the name has been highlighted, go back to the Terminal window and type (or, again, copy from here and paste in it) the following commands:```
sudo apt-get purge -y **[COLOR=Red]application[/COLOR]** && sudo apt-get autoremove -y
```where [COLOR=Red]**application**[/COLOR] has to be replaced by the name of application you wish to remove.

---

### Post by MyTinFoilHat on 2013-01-05
> **iMac71 said:**
> you might try to proceed as follows:
- open a Terminal window and type in it (or copy from here and paste in it) the following command:```
gksudo gedit /var/log/apt/history.log
```- after that the file has been loaded in gedit, press [CTRL]-[F] and type in the search field at least some letters of the name of the application you're looking for
- when the name has been highlighted, go back to the Terminal window and type (or, again, copy from here and paste in it) the following commands:```
sudo apt-get purge -y **[COLOR=Red]application[/COLOR]** && sudo apt-get autoremove -y
```where [COLOR=Red]**application**[/COLOR] has to be replaced by the name of application you wish to remove.

Got it! I actually ended up having a simultaneous "a-ha!" and "oh, duh!" -moment as I read your reply. I removed it via Synaptic. I checked the refreshed history log and it looks like it's completely gone now.

Thank you very much. I appreciate your help and knowledge sharing.

---

