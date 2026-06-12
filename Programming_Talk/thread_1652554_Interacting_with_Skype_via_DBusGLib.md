---
title: "Interacting with Skype via DBus/GLib"
date: 2010-12-25
forum: Programming Talk
---

### Post by moma on 2010-12-25
Hello and [COLOR="SeaGreen"]Merry Christmas[/COLOR].

I have created an audio-recording application in Linux. It can be automatically controlled by various MediaPlayers via the DBus. Now I want to add Skype interaction to that application.

But I have problems with setting the "Notify" signal right for Skype. The example code below (t1.c) never receives notifications from the Skype.

I have done a test code (t1.c) that uses GLib bindings to DBus.
The example is here: [http://www.futuredesktop.com/tmp/t1.c](http://www.futuredesktop.com/tmp/t1.c)

First, t1.c sends "NAME Audio-Recorder" string to the Skype. Skype will show a dialog box, and the user must accept the DBus connection. This is OK.
Then it sends "PROTOCOL 7" (or eg. "PROTOCOL 2") string to the Skype and Skype accepts it.

But t1.c never receives notification signals/messages from the Skype! This is how I set the notification signal. See the t1.c.

As far I know, the data from the Skype should be pure G_TYPE_STRING.

void skype_connect_dbus_signals() {
  DBusGConnection *dbus_conn = dbus_player_connect_to_dbus();

  proxy_receive = dbus_g_proxy_new_for_name(dbus_conn,
                                            "com.Skype.API",
                                            "/com/Skype/Client",
                                         "com.Skype.API.Client");

  dbus_g_proxy_add_signal(proxy_receive, "Notify", G_TYPE_STRING, G_TYPE_INVALID);

  dbus_g_proxy_connect_signal(proxy_receive, "Notify", G_CALLBACK(notify_handler), NULL, NULL);
}
--------------

I have found a Python scripts that works fine with Skype over DBus. 
The script is here: [http://www.futuredesktop.com/tmp/py-test1.py](http://www.futuredesktop.com/tmp/py-test1.py)
Start Skype first, then run python py-test1.py.

When running the Python test "py-test1.py", dbus_monitor shows this information. I can see correct data coming from the Skype.
$ dbus_monitor

 method call sender=:1.121 -> dest=:1.124 serial=20 path=/com/Skype/Client; interface=com.Skype.API.Client; member=Notify
 string "CALL 64  XXX"

 method call sender=:1.121 -> dest=:1.124 serial=21 path=/com/Skype/Client; interface=com.Skype.API.Client; member=Notify
 string "CALL 64 STATUS XXX"
--------------

How to setup the "Notify" signal in t1.c (using DBUs/Glib binding)?

The t1.c has instructions for how to compile and run it in Linux.  My system is Ubuntu Linux 10.10. In Linux you will need libgtk2.0-dev, libdbus-1-dev and libdbus-glib-1-dev packages.

The t1.c also initiates the GDK threads library but that's nothing to do with this sample.

I've also sent this question to [http://lists.freedesktop.org/archives/dbus/2010-December/013910.html](http://lists.freedesktop.org/archives/dbus/2010-December/013910.html)

---

### Post by moma on 2010-12-25
Re-hello,
Ok, I got very good help on [email]dbus@lists.freedesktop.org[/email].

Now the Skype interface works very well.

I created a SkypeService object and registered it with
         
dbus_g_object_type_install_info(G_TYPE_FROM_INSTANCE(service_object), &dbus_glib_server_object_object_info);

dbus_g_connection_register_g_object(dbus_conn, "/com/Skype/Client", (GObject*)service_object);
calls.

This following XML defines the skype_service_notify_callback(...) method and its argumets (it has only one).
See the skype-service-object.xml file.

```
<?xml version="1.0" encoding="UTF-8" ?>
 <node>
   <interface name="com.Skype.API.Client">
    <method name="Notify">
      <annotation name="org.freedesktop.DBus.GLib.CSymbol" value="skype_service_notify_callback"/>
      <arg type="s" name="message" direction="in"/>
    </method>
   </interface>
 </node>
```
I converted it to skype-service-object-glue.h with the dbus-binding-tool.
$ [COLOR="DarkGreen"]dbus-binding-tool --prefix=server_object --mode=glib-server skype-service-object.xml > skype-service-object-glue.h[/COLOR]

The SkypeService object is described by skype-service.[hc]

Here is the source code and test for this Skype - GLib/DBus interface.
[http://www.futuredesktop.com/tmp/skype-test.tar.gz](http://www.futuredesktop.com/tmp/skype-test.tar.gz)

Unpack the files, then compile and link with it
$ ./m.sh

Run
$ ./t1

Study the t1.c  for more information.

Read also the replies on dbus @ lists.freedesktop.org:
[http://lists.freedesktop.org/archives/dbus/2010-December/013922.html](http://lists.freedesktop.org/archives/dbus/2010-December/013922.html)

Python users should try: [http://sourceforge.net/projects/skype4py/](http://sourceforge.net/projects/skype4py/)
See also the attached py-test1.py.

Get also the Skype API (command reference) from [http://developer.skype.com/accessories](http://developer.skype.com/accessories)
Ref: [http://developer.skype.com/resources/public_api_ref.zip](http://developer.skype.com/resources/public_api_ref.zip)

Again, thanks and happy holidays :-)

[COLOR="Red"]EDIT:[/COLOR] One important thing. Should we g_free() the message in skype_service_notify_callback()?  
See skype-service.c.
Skype sends a lot of string messages, so this can be a major memory leak.
[COLOR="Red"]EDIT:[/COLOR] It seems that the message (string) is owner by DBus/Skype and cannot be freed.

---

