---
title: "glib dbus signals with custom datatype/structure as parameter"
date: 2012-01-26
forum: Programming Talk
---

### Post by sruthihsr on 2012-01-26
i am using glib binding tool for implementation

i have the following in my xml

  <signal name="MainSinkSoundPropertyChanged">
             <arg name="sourceID" type="q" direction="out"/>
             <arg name="SoundProperty" type="(nn)" direction="out"/>
     </signal>
where sound property is a structure.
I am doing the client implementation..
Please tell me how do i define
 dbus_g_proxy_add_signal and dbus_g_proxy_connect_signal

---

