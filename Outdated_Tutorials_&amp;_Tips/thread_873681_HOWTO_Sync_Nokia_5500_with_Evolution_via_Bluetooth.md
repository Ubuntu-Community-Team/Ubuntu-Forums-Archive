---
title: "HOWTO: Sync Nokia 5500 with Evolution via Bluetooth"
date: 2008-07-29
forum: Outdated Tutorials &amp; Tips
---

### Post by michi.la on 2008-07-29
This is a howto for syncing a Nokia 5500 Sport Smartphone with Evolution. Testsystem: Kubuntu Hardy (8.04).

Read this Thread and do what it tells you

[I]"HOWTO: Sync Nokia E-series Phone with Evolution via Bluetooth"
[http://ubuntuforums.org/showthread.php?t=260676](http://ubuntuforums.org/showthread.php?t=260676)
[/I]
but adjust it as told here:

**2. Install required software**
It should work with the recommended tools
(I used these: "opensync-plugin-evolution opensync-plugin-file opensync-plugin-syncml opensyncutils multisync-tools multisync0.90")

**3. Configure msynctool**

Plugin evo2-sync: leave default

Plugin syncml-obex-client:
```
<?xml version="1.0"?>
<config>
  <!-- (Only for bluetooth) The bluetooth address if the bluetooth mode is selected -->
  <bluetooth_address>xx:xx:xx:xx:xx:xx</bluetooth_address>
  
  <!-- (Only for bluetooth) The bluetooth channel to use. `sdptool browse $MAC` to search for the correct channel -->
  <bluetooth_channel>13</bluetooth_channel>
  
  <!-- (Only for USB) The usb interface number of the SYNCML-SYNC target. use syncml-obex-client -u (you will need access to the USB raw device) to find it. -->
  <interface>0</interface>
  
  <!-- The string that the plugin will use to identify itself. Some devices need a special string here. -->
  <identifier>PC Suite</identifier>
  
  <!-- The syncml version to use: 0 for 1.0, 1 for 1.1 and 2 for 1.2 -->
  <version>1</version>
  
  <!-- if the plugin should use wbxml -->
  <wbxml>1</wbxml>
  
  <!-- The username to use. Leave empty to not require a username -->
  <username></username>
  
  <!-- the password for the username -->
  <password></password>
  
  <!-- sets the connection type to use. 5 means obex over usb, 2 means obex over bluetooth -->
  <type>2</type>
  
  <!-- If wbxml is enabled, defines wether the wbxml should use string tables -->
  <usestringtable>1</usestringtable>
  
  <!-- Never send ADD command, but send REPLACE (not needed normally) -->
  <onlyreplace>0</onlyreplace>

  <!-- Workaround around for mobile phones which only use local timestamps and _no_ UTC timestamps! -->
  <onlyLocaltime>0</onlyLocaltime>
  
  <!-- Sets the maximum allowed size in bytes of incoming messages (some device need this option set). Example: 10000 -->
  <recvLimit>10000</recvLimit>
  
  <maxObjSize>0</maxObjSize>
  
  <!-- The name of the contacts db. Must be the same as the phones sends -->
  <contact_db>Contacts</contact_db>
  
  <!-- The name of the calendar db. Must be the same as the phones sends -->
  <calendar_db>Calendar</calendar_db>
  
  <!-- The name of the note db. Must be the same as the phones sends -->
  <note_db>Notes</note_db>
</config>

```

That should match the Phones default sync settings.

Note: You can edit the config file via Multisync-qad Gui
Note: To get your MAC Address using hcitool you have to make your Phone visible, once you got the Address everything works in hidden mode.

**4. Sync!**
I used (Shell):
msynctool --sync nokia --conflict 2 --filter-objtype note --filter-objtype todo

Note: the Option "--conflict 2" is in my case the only way it works properly. (see "man msynctool")


-----
Thanks to Nailor

---

