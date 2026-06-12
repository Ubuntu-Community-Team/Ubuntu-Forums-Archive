---
title: "workflow of button press events on remote control"
date: 2013-02-15
forum: New to Ubuntu
---

### Post by issaak on 2013-02-15
i have installed ubuntu 12.10 (quantal) as part of xbmcbuntu install. i have managed to get my remote control (imon-pad) working. but what i have found was that remote control commands are translated into keyboard keys and they are passed to xbmc. what i would like to know is what is the workflow of processing the button press events on remote control and who/when is translating them into keyboard equivalent. The reason for the question is that I don't have all the buttons translated into keyboard equivalents.

what i have done so far:

tested with ir-keytable - most of the buttons are visible and responding. they are all mapped in imon-pad.xml file.

tested with xev - only few buttons are responsive and they are passed into xbmc

tested xbmc by removing .xml files to find out which translation is used for remote control commands - found it was a keyboard.xml


Thanks

---

