---
title: "Customising right-click menus"
date: 2013-06-22
forum: New to Ubuntu
---

### Post by Barney-R on 2013-06-22
Hello all. I've been using Ubuntu for 2 or 3 years now, but I'm still a comparative newbie in a lot of ways.

I'd like to be able to edit right-click menus to remove certain options, partly because, in Ubuntu, the mouse - any mouse - is much more sensitive than it ever was in Windows, and some of those options are potentially "dangerous".

In case it's relevant, I'm running 12.04 (64-bit) with the Gnome desktop because I find it much easier to use than Unity.

One item I'd particularly like to get rid of is "Format" when I right click on a mounted partition or external device displayed on the desktop. I choose to show any mounted drives in this way, both as a visual reminder and as a quick way of unmounting when they're no longer needed (I use a number of partitions and a few removable devices).

The mouse often responds as if I'd left-clicked where I had no intention of clicking. I'm aware that after accidentally clicking "format" I'm then prompted to choose a file system, giving me a "second chance" to abort the operation, but there are other ways to format a device if I really want to, so I'd rather not have it as an option in the right-click menu.

There's also a risk that a visitor (I've got a couple in mind here) might accidentally format a device without understanding what happened.

Sorry it's such a long post over a fairly simple matter, but with 1.75TB of HD space, I've got a lot to lose.

One final point. If I need to enter code into the terminal, please try to keep it simple. I'm more comfortable with graphical solutions.

---

### Post by Barney-R on 2013-06-26
Hello??? Anyone?

---

### Post by Frogs Hair on 2013-06-26
The link should point you in the riight direction.   [http://askubuntu.com/questions/21953/how-to-customize-the-context-menu-in-nautilus](http://askubuntu.com/questions/21953/how-to-customize-the-context-menu-in-nautilus)

---

### Post by mc4man on 2013-06-26
In 12.04 that option is built-in, don't see you removing thru any available config option.

what you could do is require the admin password to modify a device, currently it;s set to "yes" for any active user
2 ways - 
edit /usr/share/polkit-1/actions/org.freedesktop.udisks.policy in the section shown below, the default yes is changed to auth_admin (blue

```
<action id="org.freedesktop.udisks.change">
    <description>Modify a device</description>
    <description xml:lang="da">Modificér en enhed</description>
    <description xml:lang="de">Gerät ändern</description>
    <description xml:lang="pt_BR">Modificar um dispositivo</description>
    <message>Authentication is required to modify the device</message>
    <message xml:lang="da">Autorisering er påkrævet for at ændre en enhed</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um das Gerät zu ändern</message>
    <message xml:lang="pt_BR">Autenticação é requerida para modificar o dispositivo</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>[COLOR="#000080"]auth_admin[/COLOR]</allow_active>
    </defaults>
  </action>
```

That file can be overwritten by an update (not that likely after release but possible

Or you can create a .pkla override, it will never be overwritten 

```
sudo nano /var/lib/polkit-1/localauthority/50-local.d/udisks.pkla
```

copy & paste below code  in, then on keyboard, 
ctrl+o
enter
ctrl+x

(or use gksudo gedit if desired instead of sudo nano, ignore that dumb "Untitled Document 1"

```
[Modify a device]
Identity=unix-user:*
Action=org.freedesktop.udisks.change
ResultActive=auth_admin
```

---

### Post by Barney-R on 2013-06-27
Thank you both. I've got a lot to learn where the terminal is concerned, but I'll work my way through that lot and see what happens. Not a lot of time today though, unfortunately.

---

