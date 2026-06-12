---
title: "blueman see's bluetooth device but won't pair"
date: 2016-08-08
forum: New to Ubuntu
---

### Post by Chris1965 on 2016-08-08
I've installed a minimal ubuntu 14.04 x64 with a xfce4 DE. All works well however 1 thing seems not to and that is blueman. I open the program (bluetooth manager), have it search for Oontz XL and it finds it with no problems however it refuses to pair. I've made several attempts at adding and removing blueman and the result is always the same. I even went to blueman site and double checked the dependencies files list to make sure it installed everything and it did.

The computer is a dell m6400 workstation and the card is a mini dell wireless 370.

I am at wits end here trying to figure this one out, any help would be most appreciated. I even downloaded live distro Cd's and the bluetooth works fine off of it so I can only guess I am missing some files in the default xfce4 or similar. The xfce4 guide I followed was: [from this site. ]("https://xpressubuntu.wordpress.com/2014/02/22/how-to-install-a-minimal-ubuntu-desktop/")

---

### Post by Chris1965 on 2016-08-08
This is what showed when I opened it in terminal:

```
Using gconf config backend
_________
Load (/usr/lib/python2.7/dist-packages/blueman/main/PluginManager.py:54)
['Services', 'PulseAudioProfile'] 
_________
__load_plugin (/usr/lib/python2.7/dist-packages/blueman/main/PluginManager.py:127)
loading <class 'blueman.plugins.manager.Services.Services'> 
_________
__load_plugin (/usr/lib/python2.7/dist-packages/blueman/main/PluginManager.py:127)
loading <class 'blueman.plugins.manager.PulseAudioProfile.PulseAudioProfile'> 
_________
pa_context_event (/usr/lib/python2.7/dist-packages/blueman/main/PulseAudioUtils.py:306)
1 
blueman-manager version 1.23 starting
_________
pa_context_event (/usr/lib/python2.7/dist-packages/blueman/main/PulseAudioUtils.py:306)
2 
_________
on_bluez_name_owner_changed (/usr/bin/blueman-manager:112)
org.bluez owner changed to  :1.2 
Using gconf config backend
_________
SetAdapter (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:276)
None 
_________
on_adapter_changed (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerToolbar.py:70)
toolbar adapter /org/bluez/766/hci0 
_________
pa_context_event (/usr/lib/python2.7/dist-packages/blueman/main/PulseAudioUtils.py:306)
3 
_________
pa_context_event (/usr/lib/python2.7/dist-packages/blueman/main/PulseAudioUtils.py:306)
4 
_________
on_pa_ready (/usr/lib/python2.7/dist-packages/blueman/plugins/manager/PulseAudioProfile.py:27)
connected 
_________
<lambda> (/usr/lib/python2.7/dist-packages/blueman/main/PulseAudioUtils.py:318)
1 
_________
on_property_changed (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:158)
adapter propery changed Discovering 1 
_________
on_device_found (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:134)
Device discovered A0:E9 DB:18:24:1F 
_________
__init__ (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:16)
caching initial properties 
_________
add_device (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:330)
adding new device 
_________
do_cache (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:522)
Caching new device A0:E9 DB:18:24:1F 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:286)
row update event Fake True 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:286)
row update event Trusted 0 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:286)
row update event Paired 0 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:286)
row update event RSSI -63 
opacity 201
RSSI: -63
_________
on_property_changed (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:158)
adapter propery changed Discovering 0 
_________
on_property_changed (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:158)
adapter propery changed Discovering 1 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
on_device_created (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:258)
created /org/bluez/766/hci0/dev_A0_E9_DB_18_24_1F 
_________
__init__ (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:16)
caching initial properties 
_________
do_cache (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:522)
Caching new device A0:E9 DB:18:24:1F 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:286)
row update event Fake False 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:286)
row update event Trusted 0 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:286)
row update event Paired 0 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
Generate (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceMenu.py:215)
OontZ XL 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:286)
row update event Fake False 
_________
on_property_changed (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:158)
adapter propery changed Devices dbus.Array([dbus.ObjectPath('/org/bluez/766/hci0/dev_A0_E9_DB_18_24_1F')], signature=dbus.Signature('o'), variant_level=1) 
_________
on_property_changed (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:158)
adapter propery changed Discovering 0 
_________
err (/usr/bin/blueman-manager:251)
(DBusException(dbus.String(u'Connection Timeout'),),) 
_________
on_property_changed (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:158)
adapter propery changed Devices dbus.Array([], signature=dbus.Signature('o'), variant_level=1) 
_________
RemoveDevice (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:441)
<Device object at 0x7f6ab0911b90 (blueman+main+Device+Device at 0x1728360)> 
_________
RemoveDevice (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:441)
converting to fake 
_________
__init__ (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:16)
caching initial properties 
_________
add_device (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:330)
converting: real to discovered 
_________
do_cache (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:522)
Caching new device A0:E9 DB:18:24:1F 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:286)
row update event Fake True 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:286)
row update event Trusted 0 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:286)
row update event Paired 0 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:286)
row update event Fake True 
_________
__del__ (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:60)
deleting device /org/bluez/766/hci0/dev_A0_E9_DB_18_24_1F 
_________
Destroy (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:95)
invalidating device /org/bluez/766/hci0/dev_A0_E9_DB_18_24_1F 
/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerProgressbar.py:174: Warning: Source ID 684 was not found when attempting to remove it
  gobject.source_remove(self.gsource)
Loading configuration plugins
Using gconf config backend
_________
SetAdapter (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:276)
None 

(blueman-assistant:2354): IBUS-WARNING **: The owner of /home/z/.config/ibus/bus is not root!
Traceback (most recent call last):
  File "/usr/bin/blueman-assistant", line 175, in next_page_fn
    if len(self.Device.Services) == 0:
AttributeError: FakeDevice instance has no attribute 'Services'
_________
on_device_created (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:258)
created /org/bluez/766/hci0/dev_A0_E9_DB_18_24_1F 
_________
__init__ (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:16)
caching initial properties 
_________
on_device_created (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:258)
created /org/bluez/766/hci0/dev_A0_E9_DB_18_24_1F 
_________
__init__ (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:16)
caching initial properties 
_________
add_device (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:330)
adding new device 
_________
do_cache (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:522)
Caching new device A0:E9 DB:18:24:1F 
_________
on_property_changed (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:158)
adapter propery changed Devices dbus.Array([dbus.ObjectPath('/org/bluez/766/hci0/dev_A0_E9_DB_18_24_1F')], signature=dbus.Signature('o'), variant_level=1) 
_________
do_cache (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:522)
Caching new device A0:E9 DB:18:24:1F 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:286)
row update event Fake False 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:286)
row update event Trusted 0 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:286)
row update event Paired 0 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
Generate (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceMenu.py:215)
OontZ XL 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:286)
row update event Fake False 
_________
__del__ (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:60)
deleting device None 
_________
Destroy (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:95)
invalidating device None 
_________
on_property_changed (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:158)
adapter propery changed Devices dbus.Array([dbus.ObjectPath('/org/bluez/766/hci0/dev_A0_E9_DB_18_24_1F')], signature=dbus.Signature('o'), variant_level=1) 
org.bluez.Error.ConnectionAttemptFailed: Connection Timeout
_________
Release (/usr/lib/python2.7/dist-packages/blueman/bluez/Agent.py:76)
Release 
_________
on_property_changed (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:158)
adapter propery changed Devices dbus.Array([], signature=dbus.Signature('o'), variant_level=1) 
_________
RemoveDevice (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:441)
<Device object at 0x7fec01c757d0 (blueman+main+Device+Device at 0x1edd980)> 
_________
RemoveDevice (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:441)
converting to fake 
_________
on_property_changed (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:158)
adapter propery changed Devices dbus.Array([], signature=dbus.Signature('o'), variant_level=1) 
_________
RemoveDevice (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:441)
<Device object at 0x7f6ab0911a00 (blueman+main+Device+Device at 0x1728000)> 
_________
__init__ (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:16)
caching initial properties 
_________
add_device (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:330)
converting: real to discovered 
_________
RemoveDevice (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:441)
converting to fake 
_________
do_cache (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:522)
Caching new device A0:E9 DB:18:24:1F 
_________
_________
__init__ (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:16)
caching initial properties 
__del__ (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:60)
_________
add_device (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:330)
converting: real to discovered 
deleting device /org/bluez/766/hci0/dev_A0_E9_DB_18_24_1F 
_________
do_cache (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:522)
Caching new device A0:E9 DB:18:24:1F 
_________
Destroy (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:95)
invalidating device /org/bluez/766/hci0/dev_A0_E9_DB_18_24_1F 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:286)
row update event Fake True 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:286)
row update event Trusted 0 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:286)
row update event Paired 0 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:286)
row update event Fake True 
_________
__del__ (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:60)
deleting device /org/bluez/766/hci0/dev_A0_E9_DB_18_24_1F 
_________
Destroy (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:95)
invalidating device /org/bluez/766/hci0/dev_A0_E9_DB_18_24_1F 
z@BR549:~$ clear

z@BR549:~$ sudo blueman-manager
Loading configuration plugins
Using gconf config backend
_________
Load (/usr/lib/python2.7/dist-packages/blueman/main/PluginManager.py:54)
['Services', 'PulseAudioProfile'] 
_________
__load_plugin (/usr/lib/python2.7/dist-packages/blueman/main/PluginManager.py:127)
loading <class 'blueman.plugins.manager.Services.Services'> 
_________
__load_plugin (/usr/lib/python2.7/dist-packages/blueman/main/PluginManager.py:127)
loading <class 'blueman.plugins.manager.PulseAudioProfile.PulseAudioProfile'> 
_________
pa_context_event (/usr/lib/python2.7/dist-packages/blueman/main/PulseAudioUtils.py:306)
1 
blueman-manager version 1.23 starting
_________
pa_context_event (/usr/lib/python2.7/dist-packages/blueman/main/PulseAudioUtils.py:306)
2 
_________
on_bluez_name_owner_changed (/usr/bin/blueman-manager:112)
org.bluez owner changed to  :1.2 
Using gconf config backend
_________
SetAdapter (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:276)
None 
_________
on_adapter_changed (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerToolbar.py:70)
toolbar adapter /org/bluez/766/hci0 
_________
pa_context_event (/usr/lib/python2.7/dist-packages/blueman/main/PulseAudioUtils.py:306)
3 
_________
pa_context_event (/usr/lib/python2.7/dist-packages/blueman/main/PulseAudioUtils.py:306)
4 
_________
on_pa_ready (/usr/lib/python2.7/dist-packages/blueman/plugins/manager/PulseAudioProfile.py:27)
connected 
_________
<lambda> (/usr/lib/python2.7/dist-packages/blueman/main/PulseAudioUtils.py:318)
1 
_________
on_property_changed (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:158)
adapter propery changed Discovering 1 
_________
on_device_found (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:134)
Device discovered A0:E9 DB:18:24:1F 
_________
__init__ (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:16)
caching initial properties 
_________
add_device (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:330)
adding new device 
_________
do_cache (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:522)
Caching new device A0:E9 DB:18:24:1F 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:286)
row update event Fake True 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:286)
row update event Trusted 0 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:286)
row update event Paired 0 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:286)
row update event RSSI -60 
opacity 210
RSSI: -60
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py", line 169, in on_event_clicked
    self.menu = ManagerDeviceMenu(self.Blueman)
  File "/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceMenu.py", line 42, in __init__
    self.Generate()
  File "/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceMenu.py", line 223, in Generate
    device = self.Blueman.List.get(self.Blueman.List.selected(), "device")["device"]
TypeError: 'bool' object has no attribute '__getitem__'
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
on_property_changed (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:158)
adapter propery changed Discovering 0 
_________
on_property_changed (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:158)
adapter propery changed Discovering 1 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
on_property_changed (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:158)
adapter propery changed Discovering 0 
Loading configuration plugins
Using gconf config backend
_________
SetAdapter (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:276)
None 

(blueman-assistant:2907): IBUS-WARNING **: The owner of /home/z/.config/ibus/bus is not root!
Traceback (most recent call last):
  File "/usr/bin/blueman-assistant", line 175, in next_page_fn
    if len(self.Device.Services) == 0:
AttributeError: FakeDevice instance has no attribute 'Services'
_________
on_device_created (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:258)
created /org/bluez/766/hci0/dev_A0_E9_DB_18_24_1F 
_________
__init__ (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:16)
caching initial properties 
_________
on_device_created (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:258)
created /org/bluez/766/hci0/dev_A0_E9_DB_18_24_1F 
_________
__init__ (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:16)
caching initial properties 
_________
do_cache (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:522)
Caching new device A0:E9 DB:18:24:1F 
_________
_________
add_device (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:330)
adding new device 
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:286)
row update event Fake False 
_________
do_cache (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:522)
Caching new device A0:E9 DB:18:24:1F 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:286)
row update event Trusted 0 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:286)
row update event Paired 0 
_________
on_property_changed (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:158)
adapter propery changed Devices dbus.Array([dbus.ObjectPath('/org/bluez/766/hci0/dev_A0_E9_DB_18_24_1F')], signature=dbus.Signature('o'), variant_level=1) 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
Generate (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceMenu.py:215)
OontZ XL 
_________
Generate (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceMenu.py:215)
OontZ XL 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:286)
row update event Fake False 
_________
on_property_changed (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:158)
adapter propery changed Devices dbus.Array([dbus.ObjectPath('/org/bluez/766/hci0/dev_A0_E9_DB_18_24_1F')], signature=dbus.Signature('o'), variant_level=1) 
org.bluez.Error.ConnectionAttemptFailed: Connection Timeout
_________
on_property_changed (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:158)
adapter propery changed Devices dbus.Array([], signature=dbus.Signature('o'), variant_level=1) 
_________
RemoveDevice (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:441)
<Device object at 0x7f129cf94aa0 (blueman+main+Device+Device at 0x15402c0)> 
_________
RemoveDevice (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:441)
converting to fake 
_________
Release (/usr/lib/python2.7/dist-packages/blueman/bluez/Agent.py:76)
Release 
_________
on_property_changed (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:158)
adapter propery changed Devices dbus.Array([], signature=dbus.Signature('o'), variant_level=1) 
_________
RemoveDevice (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:441)
<Device object at 0x7f11e85137d0 (blueman+main+Device+Device at 0x1668a40)> 
_________
RemoveDevice (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:441)
converting to fake 
_________
__init__ (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:16)
caching initial properties 
_________
add_device (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:330)
converting: real to discovered 
_________
do_cache (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:522)
Caching new device A0:E9 DB:18:24:1F 
_________
__init__ (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:16)
caching initial properties 
_________
add_device (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:330)
converting: real to discovered 
_________
do_cache (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:522)
Caching new device A0:E9 DB:18:24:1F 
_________
__del__ (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:60)
deleting device /org/bluez/766/hci0/dev_A0_E9_DB_18_24_1F 
_________
Destroy (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:95)
invalidating device /org/bluez/766/hci0/dev_A0_E9_DB_18_24_1F 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:286)
row update event Fake True 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:286)
row update event Trusted 0 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:286)
row update event Paired 0 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
init_services (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:73)
Loading services 
_________
row_update_event (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceList.py:286)
row update event Fake True 
_________
__del__ (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:60)
deleting device /org/bluez/766/hci0/dev_A0_E9_DB_18_24_1F 
_________
Destroy (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:95)
invalidating device /org/bluez/766/hci0/dev_A0_E9_DB_18_24_1F 
_________
child_closed (/usr/lib/python2.7/dist-packages/blueman/Functions.py:153)
['/usr/bin/blueman-assistant', u'--device=A0:E9 DB:18:24:1F'] closed 

```

---

### Post by mook765 on 2016-08-08
Did you add your user to the lp-group?
See here> [https://wiki.archlinux.org/index.php/Blueman](https://wiki.archlinux.org/index.php/Blueman)

---

### Post by wildmanne39 on 2016-08-08
*Thread moved to **New to Ubuntu**.*

---

### Post by Chris1965 on 2016-08-09
> **mook765 said:**
> Did you add your user to the lp-group?
See here

```
z@BR549:~$ cat /etc/group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:syslog,z
tty:x:5:
disk:x:6:
lp:x:7:z    <-------------------------
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:
fax:x:21:
voice:x:22:
cdrom:x:24:z
floppy:x:25:
tape:x:26:
sudo:x:27:z
audio:x:29:pulse
dip:x:30:z
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:z
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
netdev:x:102:z
crontab:x:103:
syslog:x:104:
messagebus:x:105:
fuse:x:106:
mlocate:x:107:
ssh:x:108:
z:x:1000:
lpadmin:x:109:z
sambashare:x:110:z
scanner:x:112:
colord:x:113:
pulse:x:114:
pulse-access:x:115:
rtkit:x:116:
lightdm:x:117:
nopasswdlogin:x:118:
bluetooth:x:119:z
avahi:x:111:
usermetrics:x:120:
clickpkg:x:121:
```

---

### Post by Chris1965 on 2016-08-09
I just don't get it, I read the 370 card had a broadcom chipset so I installed the brcm-patchram-plus-nexus7 and I installed all file requirements posted off [this]("https://pkgs.org/ubuntu-14.04/ubuntu-universe-amd64/blueman_1.23-git201403102151-1ubuntu1_amd64.deb.html") site. Surely this isn't supposed to be rocket science? Just today I ran a live version of linux lite which runs xfce4 x64 and their bluetooth runs smoothly without hickups on this computer. I've even tried to compare what they have installed vs what's on my computer.

---

### Post by mook765 on 2016-08-09
It might be some thing simple and i hope so.
please read this:
> [h=2]5) Pairing the OontZ XL to your Bluetooth Device[/h] It is quick and easy to pair and connect wirelessly to your Bluetooth device by following these steps:
 **Step 1 **&#8211; Make sure your OontZ XL has a sufficient charge or is plugged into the power adapter.
 **Step 2 **&#8211; Turn on the OontZ XL. The Bluetooth  indicator will illuminate solid white. After about 15 seconds, the  Bluetooth indicator light will either:
 [INDENT] [INDENT] **(a)** Begin to softly flash, indicating the OontZ XL  is in pairing mode and that it is ready to be paired and connected to  your device.
- OR -
**(b) **Remain solid white, indicating the OontZ XL has automatically connected with the last device it was connected to.
 [/INDENT] [/INDENT] In case **(b)**, you need to first disconnect that  device before you can pair to a different device. To disconnect from the  first device, press and hold the Bluetooth button on the top of the  OontZ XL for about 3 seconds. The Bluetooth indicator light will begin  to softly flash, indicating the OontZ XL is now in pairing mode and that  it is ready to be paired and connected to your device.
 **Step 3 **&#8211; Enable the Bluetooth function on your  device and then search/scan for the OontZ XL. When the OontZ XL appears  on the list, select it and your device will pair and connect with the  OontZ XL. Very few devices will request a password, if your device does  enter &#8220;0000&#8221; (four zeros).
 **Step 4** &#8211; It may take a short time to connect, and  when successfully connected the Bluetooth indicator light will stop  flashing and be a solid white.
 **Step 5** &#8211; You can now wirelessly play your music or  the audio from videos, games and movies. You can use your device and the  buttons on the OontZ XL to control your audio (see section 3, items 7 &#8211;  12).
 **IMPORTANT NOTES:**
 **-- The OontZ XL can only be connected to one device at a time.**
You  will need to disconnect the first device from the OontZ XL before  trying to pair to another device. To disconnect the OontZ XL from a  connected device, press and hold the Bluetooth button on the top of the  OontZ XL for 3 seconds. The Bluetooth indicator light will begin to  softly flash, indicating the OontZ XL is now in pairing mode, and that  it is ready to be paired and connected to the next device.
 -- **The OontZ XL will automatically try to pair to the last Bluetooth device it was connected to**  each time the OontZ XL is turned on and that device is or comes within  range. It may connect without you being aware; you can check to see if  the OontZ XL has already connected to a device, as the Bluetooth  indicator light on top will be solid white. If the light is solid white,  it indicates the OontZ XL is paired to a device and you must first  disconnect from that device. To disconnect the OontZ XL from a connected  device, press and hold the Bluetooth button on the top of the OontZ XL  for 3 seconds. The Bluetooth indicator light will begin to softly flash,  indicating the OontZ XL is now in pairing mode, and that it is ready to  be paired and connected to the next device.



---

### Post by Chris1965 on 2016-08-10
> **mook765 said:**
> It might be some thing simple and i hope so.
please read this:

That part I did to the letter because I used the manual to find the passcode "0000" in the setup mode instead of the automatic pair. Like I said I got it to pair using a live version of linux lite but when it comes to me installing the blueman on the hard drive it for some reason won't pair. I thought it might have been a dependency issue so I went to the site and found the list of files and double checked to make sure nothing got skipped. Only thing I changed in my xfce DE is I installed nautilus instead of thunar and use lxterminal instead of xterm due to personal preferences and everything else seems to work as expected.

Since I am newer to linux then the only thing I am unsure about is if there is a way to check the system for broken packages. I checked synaptic and clicked check for broken packages but it didn't appear to do anything. I do know when I did the initial install of ubuntu mini I did add the APP::Install-Recommends "0"; line to apt.conf. would that have any bearing? 

It always finds the speaker easily but ends up timing out when it comes to pairing. Not once on my install has it actually connected. Now I have not tried to connect the blueman to a network or anything else because I don't have any other devices bluetooth at the moment.

---

### Post by mook765 on 2016-08-11
I found something in the bluetooth configuration file
/etc/bluetooth/main.config:```
# How long to stay in pairable mode before going back to non-discoverable
# The value is in seconds. Default is 0.
# 0 = disable timer, i.e. stay pairable forever
#PairableTimeout = 0
```
You may check your configuration file if it is different.
Maybe you could try to establish the connection unpaired and see if it is going to work or not.
I just grabbed my daughters notebook and established an unpaired connection, was able to send and receive files...
But with audio might be different...

---

