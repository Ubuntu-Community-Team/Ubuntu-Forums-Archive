---
title: "no longer can mount ntfs drive"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by nutpants on 2008-05-29
i worked a few hours ago..

i have been playing with pm-suspend trying to get my laptop to suspend

now i get 

Cannot mount volume.

Error org.freedesktop.DBus.Error.AccessDenied.

A security policy is in place the prevents this sender from sending this
message to this recipient, see message bus configuration file (rejected 
message had interface "org.freedesktop.Hal.Device.Volume" member "Mount" 
error name "(unset)" destination "org.freedesktop.Hal")


when i try to mount my ntfs partition

so i looked into it and found i have to change something with
polkit-gnome-authorization 

but nothing changes and im lost..

heres a list of errors
> @linuxtop:~$ sudo polkit-gnome-authorization 
polkit-read-auth-helper: needs to be setgid polkituser
polkit-read-auth-helper: needs to be setgid polkituser
polkit-read-auth-helper: needs to be setgid polkituser
polkit-read-auth-helper: needs to be setgid polkituser
polkit-read-auth-helper: needs to be setgid polkituser
polkit-read-auth-helper: needs to be setgid polkituser
polkit-read-auth-helper: needs to be setgid polkituser
polkit-read-auth-helper: needs to be setgid polkituser
[WARN 12177] polkit-session.c:285:polkit_session_get_ck_objref(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
[WARN 12177] polkit-session.c:321:polkit_session_get_ck_is_local(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
[WARN 12177] polkit-session.c:303:polkit_session_get_ck_is_active(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
polkit-read-auth-helper: needs to be setgid polkituser
polkit-read-auth-helper: needs to be setgid polkituser
** (polkit-gnome-authorization:12177): WARNING **: Error: code=3: uid 0 is not authorized to read authorizations for uid -1 (requires org.freedesktop.policykit.read)
[WARN 12177] polkit-session.c:285:polkit_session_get_ck_objref(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
[WARN 12177] polkit-session.c:321:polkit_session_get_ck_is_local(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
[WARN 12177] polkit-session.c:303:polkit_session_get_ck_is_active(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
polkit-read-auth-helper: needs to be setgid polkituser
polkit-read-auth-helper: needs to be setgid polkituser

 



i dont want to have to reinstall again.
and fix everything all over again to get my sound and video and mic and screen and games working ...


nutz

---

### Post by nutpants on 2008-05-29
** (polkit-gnome-authorization:12177): WARNING **: Error: code=3: uid 0 is not authorized to read authorizations for uid -1 (requires org.freedesktop.policykit.read)
[WARN 12177] polkit-session.c:285:polkit_session_get_ck_objref(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
[WARN 12177] polkit-session.c:321:polkit_session_get_ck_is_local(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
[WARN 12177] polkit-session.c:303:polkit_session_get_ck_is_active(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
polkit-read-auth-helper: needs to be setgid polkituser
polkit-read-auth-helper: needs to be setgid polkituser

** (polkit-gnome-authorization:12177): WARNING **: Error: code=3: uid 0 is not authorized to read authorizations for uid -1 (requires org.freedesktop.policykit.read)
[WARN 12177] polkit-session.c:285:polkit_session_get_ck_objref(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
[WARN 12177] polkit-session.c:321:polkit_session_get_ck_is_local(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
[WARN 12177] polkit-session.c:303:polkit_session_get_ck_is_active(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
polkit-read-auth-helper: needs to be setgid polkituser
polkit-read-auth-helper: needs to be setgid polkituser



more of the error

---

### Post by sayakb on 2008-05-29
Just reboot.. After a wakeup from suspend, much of Hardy goes bizarre..

---

### Post by sayakb on 2008-05-29
Read this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/203537](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/203537)
Seems like this bug still exists.. :( :(

---

### Post by nutpants on 2008-05-29
already tried that a few times 
shut down
and reboot.

the cd/dvd still auto mounts and dismounts

the ntfs partition auto mounts if i sudo "nautilus"

and look at the drive..
(but user cannot unmount it)
but otherwise im pooched...



nutz..


i dont think it is the same bug as my file system is not damaged as far as i can tell.

---

### Post by nutpants on 2008-05-29
bump

i can find no way to fix this..
i am about an hour away from reinstalling..

nutz

---

### Post by nutpants on 2008-05-29
i found this but i can not get it to fix my problem
A security policy in place prevents mounting of volumes.

> If you happen to access a CD-ROM device or USB device which results in the following error:

    A security policy in place prevents this sender from sending this message to this recipient, see message bus configuration file (rejected message had interface &#8220;org.freedesktop.Hal.Device.Volume&#8221; member &#8220;Mount&#8221; error name &#8220;(unset)&#8221; destination &#8220;org.freedesktop.Hal&#8221;)

&#8230;.. I have a fix for you. This is caused by the hal daemon not allowing you to access the device because of a security policy. The hal daemons security policy resides in a file at &#8220;/etc/dbus-1/system.d/hal.conf&#8221;. Lets open and see whats in there.



< !DOCTYPE busconfig PUBLIC
 "-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>

  <!-- This configuration file specifies the required security policies
       for the HAL to work. -->

  <!-- Only root or user haldaemon can own the HAL service -->
  <policy user="haldaemon">
    <allow own="org.freedesktop.Hal"/>
  </policy>
  <policy user="root">
    <allow own="org.freedesktop.Hal"/>
  </policy>

  <!-- Allow anyone to invoke methods on the Manager and Device interfaces -->
  <policy context="default">
    <allow send_interface="org.freedesktop.Hal.Manager"/>
    <allow send_interface="org.freedesktop.Hal.Device"/>

    <allow receive_interface="org.freedesktop.Hal.Manager"
           receive_sender="org.freedesktop.Hal"/>
    <allow receive_interface="org.freedesktop.Hal.Device"
           receive_sender="org.freedesktop.Hal"/>
  </policy>

  <!-- Default policy for the exported interfaces -->
  <policy context="default">
    <deny send_interface="org.freedesktop.Hal.Device.SystemPowerManagement"/>
    <deny send_interface="org.freedesktop.Hal.Device.LaptopPanel"/>
    <deny send_interface="org.freedesktop.Hal.Device.Volume"/>
    <deny send_interface="org.freedesktop.Hal.Device.Volume.Crypto"/>
  </policy>

  <!-- This will not work if pam_console support is not enabled -->
  <policy at_console="true">
    <allow send_interface="org.freedesktop.Hal.Device.SystemPowerManagement"/>
    <allow send_interface="org.freedesktop.Hal.Device.LaptopPanel"/>
    <allow send_interface="org.freedesktop.Hal.Device.Volume"/>
    <allow send_interface="org.freedesktop.Hal.Device.Volume.Crypto"/>
  </policy>

  <!-- You can change this to a more suitable user, or make per-group -->
  <policy user="0">
    <allow send_interface="org.freedesktop.Hal.Device.SystemPowerManagement"/>
    <allow send_interface="org.freedesktop.Hal.Device.LaptopPanel"/>
    <allow send_interface="org.freedesktop.Hal.Device.Volume"/>
    <allow send_interface="org.freedesktop.Hal.Device.Volume.Crypto"/>
  </policy>

</busconfig>
</pre>

If you observer this config file you will see there are the following sections:

    * Owners of tha HAL service
    * Permissions for anyone to invoke the Manager and Device interfaces
    * Default policy for the exported interfaces
    * Policy for Console Interface
    * Policies for Users or Groups

In our error message, the problem was with the &#8220;org.freedesktop.Hal.Device.Volume&#8221; security policy. In our policy file shown above, we do not have a policy allowing any user to use the Volume devices. However towards the end of the policy config file, you can see there is a policy set for the &#8220;root&#8221; user. The user=&#8221;0&#8243; attribute, means that its referencing the root user. Therefore as the policy says, only the root user has access to the Volume device. It also states in the comment, that we can change this policy or add an other one to suit our needs.

So we can add a new policy for the group called &#8220;plugdev&#8221; or &#8220;cdrom&#8221; or whatever group you feel like. Make sure you have the group created before adding the policy. In my case I added the group &#8220;plugdev&#8221; and added my user account to belong to that group. Now lets add the new policy:

  <policy group="plugdev">
    <allow send_interface="org.freedesktop.Hal.Device.SystemPowerManagement"/>
    <allow send_interface="org.freedesktop.Hal.Device.LaptopPanel"/>
    <allow send_interface="org.freedesktop.Hal.Device.Volume"/>
    <allow send_interface="org.freedesktop.Hal.Device.Volume.Crypto"/>
  </policy>

Once you have added the new policy, restarting X would be a good idea to make the changes affective. I don&#8217;t know if this is in fact the case for everyone but do so if you are still get the the error. On the other hand you could also try restarting the hal daemon by executing:

/etc/init.d/haldaemon restart

Another way of fixing the problem is to just add the policies to the Permissions for anyone to invoke the Manager and Device interfaces section of the config. That way you don&#8217;t have to add a group and specify to which group you are allowing access to the Volume devices. So that section will look like:

  <!-- Allow anyone to invoke methods on the Manager and Device interfaces -->
  <policy context="default">
    <allow send_interface="org.freedesktop.Hal.Manager"/>
    <allow send_interface="org.freedesktop.Hal.Device"/>

    <allow receive_interface="org.freedesktop.Hal.Manager"
           receive_sender="org.freedesktop.Hal"/>
    <allow receive_interface="org.freedesktop.Hal.Device"
           receive_sender="org.freedesktop.Hal"/>

    <allow send_interface="org.freedesktop.Hal.Device.SystemPowerManagement"/>
    <allow send_interface="org.freedesktop.Hal.Device.LaptopPanel"/>
    <allow send_interface="org.freedesktop.Hal.Device.Volume"/>
    <allow send_interface="org.freedesktop.Hal.Device.Volume.Crypto"/>

  </policy>

I haven&#8217;t test this method of allowing Volume access. So if you have and got it working, your feedback is welcome.

from here
[http://www.jefferyfernandez.id.au/2007/07/26/a-security-policy-in-place-prevents-mounting-of-volumes/](http://www.jefferyfernandez.id.au/2007/07/26/a-security-policy-in-place-prevents-mounting-of-volumes/)


it might help someone else.. but im stuck..

looks like its part of this bug
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/164365](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/164365)

its been marked solved..
but with out an answer
nutz

---

