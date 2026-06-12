---
title: "Python, PolicyKit and DBus: an example"
date: 2009-12-19
forum: Programming Talk
---

### Post by Flimm on 2009-12-19
I've spent the last day or two trying to study PolicyKit on Python. I finally managed to create a proof-of-concept demo. Documentation is really scarce at the moment, so I thought I'd share it with everyone here.

**[SIZE="5"]Part 1: quick tour of the example code[/SIZE]**
To see my demo in action, download the .tar.gz, extract it, and type ```
sudo python setup.py install
```It's important that you install it as root, otherwise, the demo won't work.
Then run the code: (yes, I left out ./ intentionally)
```
example-client.py
```
You should get a PolicyKit authentication request. Type your password in. You should get the following printed in the console. The output is just debugging information, if you like.```
dbus.Array([dbus.String(u'Hello'), dbus.String(u' from example-service.py'), dbus.String(u'with unique name'), dbus.String(u':1.66')], signature=dbus.Signature('s'))
dbus.Struct((dbus.String(u'Hello Tuple'), dbus.String(u' from example-service.py')), signature=None)
dbus.Dictionary({dbus.String(u'second'): dbus.String(u' from example-service.py'), dbus.String(u'first'): dbus.String(u'Hello Dict')}, signature=dbus.Signature('ss'))
com.example.DemoException: The RaiseException method does what you might expect
<!DOCTYPE node PUBLIC "-//freedesktop//DTD D-BUS Object Introspection 1.0//EN"
"http://www.freedesktop.org/standards/dbus/1.0/introspect.dtd">
<node name="/SomeObject">
  <interface name="org.freedesktop.DBus.Introspectable">
    <method name="Introspect">
      <arg direction="out" type="s" />
    </method>
  </interface>
  <interface name="com.example.SampleInterface">
    <method name="GetDict">
      <arg direction="out" type="a{ss}" />
    </method>
    <method name="Exit">
    </method>
    <method name="RaiseException">
    </method>
    <method name="GetTuple">
      <arg direction="out" type="(ss)" />
    </method>
    <method name="HelloWorld">
      <arg direction="in"  type="s" name="hello_message" />
      <arg direction="out" type="as" />
    </method>
  </interface>
</node>

example-client terminated successfully
```

Each execution of example-client.py is logged in /tmp/example-service-log, even though it's a read-only file owned by root, as you can see. PolicyKit has worked!
```
$ tail /tmp/example-service-log 
Sat Dec 19 19:03:54 2009 : Hello from example-client.py!
Sat Dec 19 19:19:14 2009 : Hello from example-client.py!
Sat Dec 19 19:20:06 2009 : Hello from example-client.py!
Sat Dec 19 19:20:47 2009 : Hello from example-client.py!
$ ls -l /tmp/example-service-log 
-rw-r--r-- 1 root root 228 2009-12-19 19:20 /tmp/example-service-log
```

[SIZE="5"]**Part 2: A tour-guide of DBus and PolicyKit**[/SIZE]
This is how I understand the system at present. Please be aware that I've only studied PolicyKit for two or three days now, and so it's quite likely that I've got one or two three wrong, and that I've missed out a lot of information. Documentation concerning PolicyKit and Python is so scarce that I'm going to ignore my own warnings! ;)

Before understanding PolicyKit, you need to understand DBus. There's a nice [DBus tutorial for Python here](http://dbus.freedesktop.org/doc/dbus-python/doc/tutorial.html), which sadly, is still unfinished after three years. You can download the example code for that tutorial in the package by installing the package python-dbus-docs and exploring /usr/share/docs/python-dbus-docs/examples/.
As far as DBus is concerned, there are two types of applications: services and clients. Services generally run in the background, waiting for requests from clients. Clients can ask for information, or ask the services to do something. For example: ```
dbus-send --session --print-reply --dest=org.bansheeproject.Banshee /org/bansheeproject/Banshee/PlayerEngine org.bansheeproject.Banshee.PlayerEngine.Pause

```That will make Banshee pause playback. To do the same in python:[php]import dbus
bus = dbus.SessionBus()
player_engine = bus.get_object("org.bansheeproject.Banshee","/org/bansheeproject/Banshee/PlayerEngine")
player_engine.Pause()[/php]
The beauty of DBus is that the service does not have to be running in the background already for you to launch it. Just requesting something from it will automatically run it. So running player_engine.Open("file:///home/user/music.ogg") will open Banshee and play that file for you. This only works when the appropriate .service file is installed in /usr/share/dbus-1/services (or ../system-services/), in this case org.bansheeproject.Banshee.service.
In this example:
[list][*]org.bansheeproject.Banshee is called the *bus name*. It's a unique name for the service.
[*]/org/bansheeproject/Banshee/PlayerEngine is called the *object path* of an *interface*. An interface is a collection of methods, basically.
[*]org.bansheeproject.Banshee.PlayerEngine.Pause is a method, which can optionally return information.[/list]
More info at the [dbus-python tutorial](http://dbus.freedesktop.org/doc/dbus-python/doc/tutorial.html). A handy application for exploring session and system services is d-feet ([click to install](apt://d-feet)), you can have endless fun with this one!

There two types of services: system and session. Session services, like Banshee, are run by the user in the background. System services are run by root (usually). They work just like session services: clients can call methods in them, launching them automatically if they're not running in the background already. The configuration files under /etc/dbus-1/system.d/ control who has permission to run the system services and to access them ([more info here](http://blog.nouse.net/?p=21)).
This is important to understand: DBus is the magic that lets users do certain things as root, not PolicyKit. PolicyKit is a way of managing authorisations, but no DBus service is obliged to use it. You could program an application that could access root without ever asking for the password. (That's not a security vulnerability necessarily, as you would need to be root to install that application in the first place) That's not what sys-admins want, however. Sys-admins want to be able to control which users can do what easily. Enter PolicyKit.

There is no PolicyKit python package (which might explain why there is so little documentation about PolicyKit on Python). You can use PolicyKit entirely through DBus.
Let's say you have an application with a DBus system service and a DBus client. You want to use PolicyKit to tighten security. To do so, you'll need to modify the service, not the client. Every method should call org.freedesktop.PolicyKit1.Authority.CheckAuthorization, passing the client's pid as an argument and a PolicyKit action identifier (identifying the method). PolicyKit will automatically display a dialog box asking for a password if appropriate. Your service will then perform the method if authorisation was granted, or refuse to perform it if not.
For this to work, an appropriate configuration file under /usr/share/polkit-1/actions (or /usr/share/PolicyKit/policy for older versions of PolicyKit) needs to be installed. See the [official documentation for PolicyKit configuration files](http://hal.freedesktop.org/docs/PolicyKit/polkit-conf.html).
Confusingly, PolicyKit action identifiers are quite similar to DBus identifers. One quick way to distinguish them is that PolicyKit action identifiers are always lower-case, for example: org.gnome.clockapplet.mechanism.configurehwclock

That's it. You can find out more by exploring the code and by putting your favourite search engine to use. Questions are welcome, if I don't know the answer, somebody else probably will. Corrections are even more welcome!

---

### Post by Flimm on 2009-12-28
Just found a useful command for debugging system services:
```
sudo -u messagebus /lib/dbus-1.0/dbus-daemon-launch-helper com.example.SampleService
```
This will test the file installed in /usr/share/dbus-1/system-services by launching the specified service.

---

### Post by marievere on 2009-12-29
Data files are missing in the tarball..

```

running install_data
error: can't copy 'com.example.SampleService.service': doesn't exist or not a regular file

```

---

### Post by Flimm on 2009-12-31
> **marievere said:**
> Data files are missing in the tarball..
Sorry about that, I've fixed it now.

---

### Post by growlf on 2010-02-20
Where would I look for specifics on connecting to a particular service such as gconf for example, as the gdm user?  I am currently using gksudo to accomplish the action - and that just seems like a bad plan for so many reasons.

---

### Post by Flimm on 2010-02-23
> **growlf said:**
> Where would I look for specifics on connecting to a particular service such as gconf for example, as the gdm user?  I am currently using gksudo to accomplish the action - and that just seems like a bad plan for so many reasons.
As far as I can tell, DBus is only used to launch the GConf daemon, there is no DBus service that lets you read and write GConf settings.

If you want to change a GConf setting as gdm user, using DBus, you need to write a DBus service yourself that modifies the gconf key.

To look at what DBus services exist already on your system, use the program: d-feet.

---

### Post by marquinos on 2010-10-01
@Flimm: Thanks! Great tutorial! :)
I have an issue in Ubuntu 10.04, If I do nothing in the password window, in 20" a get a DBus exception.
Any idea for control this exception, please?
Thanks in advance!

---

### Post by Flimm on 2010-10-01
This is the output you would get:
```
Traceback (most recent call last):
  File "/usr/local/bin/example-client.py", line 46, in main
    dbus_interface = "com.example.SampleInterface")
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

You could modify the code in /usr/local/bin/example-client.py to look like this around line 37:

[php]def main():
    bus = dbus.SystemBus()
    
    while 1:
        try:
            remote_object = bus.get_object("com.example.SampleService",
                                           "/SomeObject")

            # you can either specify the dbus_interface in each call...
            hello_reply_list = remote_object.HelloWorld("Hello from example-client.py!",
                dbus_interface = "com.example.SampleInterface")
            break
        except dbus.DBusException, ex:
            if ex.get_dbus_name() == "org.freedesktop.DBus.Error.NoReply":
                print "timed out"
            else:
                print_exc()
                sys.exit(1)
    
    print "Got reply:"
    print (hello_reply_list)
[/php]

Wait for twenty seconds or so until "timed out" is printed in the terminal, and then type your password in the PolicyKit authentication dialog. It worked on my system. There is a risk of an infinite loop though, as org.freedesktop.DBus.Error.NoReply doesn't necessarily mean a timeout has occurred.

---

### Post by Fabioamd87 on 2012-05-13
this code write in /tmp a file but on my system you don't need to be root to do that! :confused:

---

### Post by Flimm on 2012-11-11
> **Fabioamd87 said:**
> this code write in /tmp a file but on my system you don't need to be root to do that! :confused:
No, you don't need to be root to do that. But you do need to be root to own a file in /tmp. You can check the permissions of the file by running: ```
ls -l /tmp
```

---

### Post by Fabioamd87 on 2012-11-18
and when I create the file who own that?

---

