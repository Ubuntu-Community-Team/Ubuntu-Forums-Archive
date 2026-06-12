---
title: "Google Chrome Crashing, not Displaying fonts Correctly, and unable to run flash"
date: 2013-07-17
forum: New to Ubuntu
---

### Post by Hailogon on 2013-07-17
Hi All, 

I'm trying to get google-chrome running on a fresh install of Xubuntu 13.04, however it is unable to load 'Shockwave Flash' and regularly crashes within seconds of starting up. Below is a typical error message I get from opening it from a terminal, although it varies every time I open it.

```
~$ google-chrome
[3104:3126:0717/225633:ERROR:connection.cc(742)] sqlite error 5, errno 0: database is locked
[3104:3152:0717/225633:ERROR:connection.cc(742)] sqlite error 5, errno 0: database is locked
[3104:3128:0717/225633:ERROR:object_proxy.cc(627)] Failed to get name owner. Got org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.chromium.Mtpd': no such name
[3104:3128:0717/225633:ERROR:object_proxy.cc(627)] Failed to get name owner. Got org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.chromium.Mtpd': no such name
[3104:3104:0717/225634:ERROR:object_proxy.cc(532)] Failed to call method: org.chromium.Mtpd.EnumerateStorages: object_path= /org/chromium/Mtpd: org.freedesktop.DBus.Error.ServiceUnknown: The name org.chromium.Mtpd was not provided by any .service files
[3104:3126:0717/225634:ERROR:connection.cc(742)] sqlite error 5, errno 0: database is locked
[3104:3126:0717/225634:ERROR:connection.cc(742)] sqlite error 5, errno 0: database is locked
[3104:3126:0717/225634:ERROR:web_data_service_backend.cc(54)] Cannot initialize the web database: 1
[3104:3152:0717/225634:ERROR:connection.cc(742)] sqlite error 5, errno 0: database is locked
[3104:3152:0717/225634:ERROR:connection.cc(742)] sqlite error 5, errno 0: database is locked
[3104:3104:0717/225635:ERROR:connection.cc(742)] sqlite error 5, errno 0: database is locked
[3104:3104:0717/225636:ERROR:connection.cc(742)] sqlite error 5, errno 0: database is locked
[3104:3104:0717/225636:ERROR:connection.cc(742)] sqlite error 5, errno 0: database is locked
[3104:3104:0717/225636:ERROR:password_store_factory.cc(110)] Could not initialize login database.
[3104:3165:0717/225637:ERROR:download_updates_command.cc(131)] PostClientToServerMessage() failed during GetUpdates
--2013-07-17 22:56:41--  https://clients2.google.com/cr/report
Resolving clients2.google.com (clients2.google.com)... 62.252.169.153, 62.252.169.178, 62.252.169.152, ...
Connecting to clients2.google.com (clients2.google.com)|62.252.169.153|:443... connected.
HTTP request sent, awaiting response... [7:7:0717/225642:ERROR:webplugin_delegate_proxy.cc(380)] PluginMsg_Init returned false
[7:7:0717/225642:ERROR:webplugin_impl.cc(253)] Couldn't initialize plug-in
200 OK
Length: unspecified [text/html]
Saving to: ‘/dev/fd/3’

    [<=>                                    ] 0           --.-K/s              
Crash dump id: 3d5619c0218883e1
```

I've been banging my head against this problem for a couple of hours now so any advice you could give would be greatly appreciated. 

Many thanks!

---

