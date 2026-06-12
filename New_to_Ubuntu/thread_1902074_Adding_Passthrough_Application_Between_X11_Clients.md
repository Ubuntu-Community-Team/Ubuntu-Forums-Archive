---
title: "Adding Passthrough Application Between X11 Clients and Xserver - 10.04"
date: 2011-12-29
forum: New to Ubuntu
---

### Post by stephen.bateson on 2011-12-29
(First post to this forum.)

I would like to use an application that is essentially a proxy for the xserver on the same machine. This application appears as an xserver to the normal clients, records all the X11 traffic and passes it on to the real xserver. (It is a product called XposeXrecord.)

This has been done on 8.04 machines by modifying /etc/gdm/gdm.conf. A new xserver definition is created in which the command starts the proxy xserver instead. In that command the proxy server is passed the original xserver command so that it can start it as normal.

I cannot determine how to do this in 10.04. It seems that /etc/gdm/gdm.conf is one of many files that is no longer necessary and no longer supplied. I have explored my 10.04 system but I cannot work out how to achieve the same arrangement of proxy xserver that has been done in 8.04.

I read somewhere that some of the original configuration files will still work if they are added to a 10.04 system. I tried this with a couple of variations but it seems that /etc/gdm/gdm.conf does not behave this way. (It has zero effect as far as I can tell.)

The factor that seems key to me is that I cannot find anywhere in the new configuration system of 10.04 the command that starts the xserver.

Where is the command to start the xserver, when using GDM,  configured in 10.04?

Please note. I have already determined that much of the change is due to the migration of 10.04 to upstart. But that information alone has not allowed me to solve the problem. I need more details which don't seem to be documented anywhere.

Thanks,
Steve.

---

