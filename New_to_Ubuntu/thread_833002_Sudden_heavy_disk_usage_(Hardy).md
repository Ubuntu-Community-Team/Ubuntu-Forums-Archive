---
title: "Sudden heavy disk usage (Hardy)"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by abhiroopb on 2008-06-18
Suddenly the time it takes from login to usability has slowed down, then at weird times (for no apparent reason) disk activity jumps (I can see the led for the hard drive flashing). I'll be on firefox and everything slows down because of heavy disk activity. This has JUST started today. The only major thing I've done recently is followed a guide for pulse audio, after which I reverted all changes and uninstalled all packages (as I did not see it doing anything useful). [http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

---

### Post by Chr0mis on 2008-06-18
Why don't you post a screenshot of everything you've got running about? Just run the following command in a fullscreen terminal: 
```
pstree
```
and post a screenshot.

---

### Post by ruffEdgz on 2008-06-18
This might seem like a stupid question but, any unusual activity when you run 'top' in your terminal?

I'm just thinking that maybe some kind of daemon is running that you don't know about in the background that is spiking your disk usage or whatnot.

That's always the first place I check when I feel like my hardware showing some hostility.

---

### Post by abhiroopb on 2008-06-18
Output of pstree:
```

abhiroop@vanimo:~$ pstree
init&#9472;&#9516;&#9472;NetworkManager&#9472;&#9472;&#9472;3*[{NetworkManager}]
     &#9500;&#9472;NetworkManagerD
     &#9500;&#9472;acpid
     &#9500;&#9472;amarokapp&#9472;&#9516;&#9472;python&#9472;&#9472;&#9472;sh
     &#9474;           &#9500;&#9472;ruby
     &#9474;           &#9492;&#9472;6*[{amarokapp}]
     &#9500;&#9472;atd
     &#9500;&#9472;avahi-daemon&#9472;&#9472;&#9472;avahi-daemon
     &#9500;&#9472;bonobo-activati&#9472;&#9472;&#9472;{bonobo-activati}
     &#9500;&#9472;console-kit-dae&#9472;&#9472;&#9472;61*[{console-kit-dae}]
     &#9500;&#9472;cron
     &#9500;&#9472;cupsd
     &#9500;&#9472;2*[dbus-daemon]
     &#9500;&#9472;dcopserver
     &#9500;&#9472;dd
     &#9500;&#9472;deluge&#9472;&#9472;&#9472;5*[{deluge}]
     &#9500;&#9472;dhcdbd&#9472;&#9472;&#9472;dhclient
     &#9500;&#9472;drivemount_appl
     &#9500;&#9472;evolution-data-&#9472;&#9472;&#9472;{evolution-data-}
     &#9500;&#9472;evolution-excha&#9472;&#9472;&#9472;{evolution-excha}
     &#9500;&#9472;firefox&#9472;&#9472;&#9472;11*[{firefox}]
     &#9500;&#9472;gconfd-2
     &#9500;&#9472;gdm&#9472;&#9472;&#9472;gdm&#9472;&#9516;&#9472;Xorg
     &#9474;           &#9492;&#9472;x-session-manag&#9472;&#9516;&#9472;gnome-do&#9472;&#9472;&#9472;3*[{gnome-do}]
     &#9474;                             &#9500;&#9472;gnome-panel&#9472;&#9472;&#9472;{gnome-panel}
     &#9474;                             &#9500;&#9472;gnome-settings-&#9472;&#9472;&#9472;{gnome-settings-}
     &#9474;                             &#9500;&#9472;metacity
     &#9474;                             &#9500;&#9472;nautilus&#9472;&#9472;&#9472;{nautilus}
     &#9474;                             &#9500;&#9472;nm-applet
     &#9474;                             &#9500;&#9472;seahorse-agent
     &#9474;                             &#9500;&#9472;tomboy&#9472;&#9472;&#9472;2*[{tomboy}]
     &#9474;                             &#9500;&#9472;update-notifier
     &#9474;                             &#9492;&#9472;{x-session-manag}
     &#9500;&#9472;6*[getty]
     &#9500;&#9472;gnome-keyboard-
     &#9500;&#9472;gnome-keyring-d
     &#9500;&#9472;gnome-power-man
     &#9500;&#9472;gnome-screensav
     &#9500;&#9472;gnome-terminal&#9472;&#9516;&#9472;bash&#9472;&#9472;&#9472;pstree
     &#9474;                &#9500;&#9472;gnome-pty-helpe
     &#9474;                &#9492;&#9472;{gnome-terminal}
     &#9500;&#9472;gnome-vfs-daemo
     &#9500;&#9472;gvfs-fuse-daemo&#9472;&#9472;&#9472;3*[{gvfs-fuse-daemo}]
     &#9500;&#9472;gvfsd
     &#9500;&#9472;gvfsd-burn
     &#9500;&#9472;gvfsd-trash
     &#9500;&#9472;hald&#9472;&#9472;&#9472;hald-runner&#9472;&#9516;&#9472;hald-addon-acpi
     &#9474;                    &#9500;&#9472;hald-addon-cpuf
     &#9474;                    &#9500;&#9472;hald-addon-inpu
     &#9474;                    &#9492;&#9472;hald-addon-stor
     &#9500;&#9472;kded
     &#9500;&#9472;kdeinit&#9472;&#9516;&#9472;kio_file
     &#9474;         &#9492;&#9472;klauncher
     &#9500;&#9472;klogd
     &#9500;&#9472;liferea-bin&#9472;&#9472;&#9472;7*[{liferea-bin}]
     &#9500;&#9472;mount.ntfs-3g
     &#9500;&#9472;mysqld_safe&#9472;&#9516;&#9472;logger
     &#9474;             &#9492;&#9472;mysqld&#9472;&#9472;&#9472;9*[{mysqld}]
     &#9500;&#9472;nmbd
     &#9500;&#9472;ntpd
     &#9500;&#9472;pidgin&#9472;&#9472;&#9472;3*[{pidgin}]
     &#9500;&#9472;portmap
     &#9500;&#9472;preload
     &#9500;&#9472;python
     &#9500;&#9472;rpc.statd
     &#9500;&#9472;skype&#9472;&#9472;&#9472;8*[{skype}]
     &#9500;&#9472;smbd&#9472;&#9472;&#9472;smbd
     &#9500;&#9472;soffice.bin&#9472;&#9472;&#9472;2*[{soffice.bin}]
     &#9500;&#9472;syslogd
     &#9500;&#9472;system-tools-ba
     &#9500;&#9472;udevd
     &#9500;&#9472;wpa_supplicant
     &#9492;&#9472;xinetd

```

I can check top, I usually use gnome system monitor. The thing is I always have this stuff running. I mean FX, Amarok, etc...

---

### Post by kaibob on 2008-06-18
Your circumstances appear different, but Firefox 3 can cause a lot of hard drive activity when fetching updates to the site-forgery and malware lists contained in the file, urlclassifier3.sqlite. To see if this is the case, you can temporarily disable this feature by unchecking the following Firefox security preferences:

* Tell me if the site I'm visiting is a suspected attack site

* Tell me if the site I'm visiting is a suspected forgery

---

### Post by abhiroopb on 2008-06-18
Ok thanks and any ideas why the login has become so slow?

---

### Post by mobyu on 2008-06-18
My PC has the same problem from today.

```

% df -H      
Filesystem             Size   Used  Avail Use% 
/dev/sda6              5.2G   5.0G    64M  99% /
varrun                 996M   107k   996M   1% /var/run
varlock                996M      0   996M   0% /var/lock
udev                   996M    70k   996M   1% /dev
devshm                 996M    46k   996M   1% /dev/shm
lrm                    996M    40M   957M   4% /lib/modules/2.6.24-16-generic/volatile
overflow               1.1M    37k   1.1M   4% /tmp
gvfs-fuse-daemon       5.2G   5.0G    64M  99% /home/yuu/.gvfs

```

What is "gvfs-fuse-daemon"?

---

### Post by abhiroopb on 2008-06-18
there were a LOT of updates for ubuntu yesterday, could it be one of those? I'm not sure what gvfs is but I think its a file system of some sort, wouldn't really worry about it though.

---

