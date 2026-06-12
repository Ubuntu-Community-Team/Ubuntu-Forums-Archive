---
title: "Trouble Navigating in Terminal"
date: 2013-04-15
forum: New to Ubuntu
---

### Post by Garrett87 on 2013-04-15
Hello I am hoping someone can help me out, I just did a fresh install of Ubuntu 12.10 64-bit, and I'm having an issue in terminal. I cannot access some folders (even as root). ```
root@GarrettPC:/etc# ls
acpi                    hdparm.conf          polkit-1
adduser.conf            host.conf            popularity-contest.conf
adjtime                 hostname             ppp
alternatives            hosts                printcap
anacrontab              hosts.allow          profile
apg.conf                hosts.deny           profile.d
apm                     hp                   protocols
apparmor                ifplugd              pulse
apparmor.d              ImageMagick          python
apport                  init                 python2.7
apt                     init.d               python3
aptdaemon               initramfs-tools      python3.2
at.deny                 inputrc              rc0.d
at-spi2                 insserv              rc1.d
avahi                   insserv.conf         rc2.d
avserver.conf           insserv.conf.d       rc3.d
bash.bashrc             iproute2             rc4.d
bash_completion         issue                rc5.d
bash_completion.d       issue.net            rc6.d
bindresvport.blacklist  kbd                  rc.local
blkid.conf              kernel               rcS.d
blkid.tab               kernel-img.conf      remote-login-service.conf
bluetooth               kerneloops.conf      resolvconf
brlapi.key              landscape            resolv.conf
brltty                  ldap                 rmt
brltty.conf             ld.so.cache          rpc
ca-certificates         ld.so.conf           rsyslog.conf
ca-certificates.conf    ld.so.conf.d         rsyslog.d
calendar                legal                samba
chatscripts             libnl-3              sane.d
checkbox.d              libpaper.d           securetty
colord.conf             libreoffice          security
compizconfig            lightdm              sensors3.conf
ConsoleKit              lintianrc            sensors.d
console-setup           locale.alias         services
cracklib                localtime            sgml
cron.d                  logcheck             shadow
cron.daily              login.defs           shadow-
cron.hourly             logrotate.conf       shells
cron.monthly            logrotate.d          signond.conf
crontab                 lsb-base             signon-ui
cron.weekly             lsb-base-logging.sh  skel
cups                    lsb-release          snmp
cupshelpers             ltrace.conf          speech-dispatcher
dbus-1                  lvm                  ssh
debconf.conf            magic                ssl
debian_version          magic.mime           sudoers
default                 mailcap              sudoers.d
deluser.conf            mailcap.order        sysctl.conf
depmod.d                manpath.config       sysctl.d
dhcp                    mime.types           systemd
dhcp3                   mke2fs.conf          terminfo
dictionaries-common     modprobe.d           thunderbird
dnsmasq.d               modules              timezone
doc-base                motd                 timidity
dpkg                    mplayer              ts.conf
emacs                   mtab                 ucf.conf
environment             mtab.fuselock        udev
esound                  mtools.conf          udisks2
firefox                 nanorc               ufw
fonts                   netscsid.conf        updatedb.conf
foomatic                network              update-manager
fstab                   NetworkManager       update-motd.d
fstab.d                 networks             update-notifier
fuse.conf               newt                 UPower
gai.conf                nsswitch.conf        usb_modeswitch.conf
gconf                   obex-data-server     usb_modeswitch.d
gdb                     ODBCDataSources      vdpau_wrapper.cfg
ghostscript             odbc.ini             vga
gimp                    odbcinst.ini         vim
gnome                   openal               vlc
gnome-app-install       opt                  vtrgb
gnome-settings-daemon   os-release           wgetrc
gnome-system-tools      pam.conf             wildmidi
groff                   pam.d                wodim.conf
group                   papersize            wpa_supplicant
group-                  passwd               X11
grub.d                  passwd-              xdg
gshadow                 pcmcia               xml
gshadow-                perl                 xul-ext
gtk-2.0                 pkcs11               zsh_command_not_found
gtk-3.0                 pm
gufw                    pnm2ppa.conf
root@GarrettPC:/etc# cd /network
-bash: cd: /network: No such file or directory
```
I don't understand why I can access these directories through the GUI but not in terminal, and what I need to do to fix this?

---

### Post by Derek Karpinski on 2013-04-15
You can't 'cd /network' because there is no such directory.

You are in /etc.

/ is the starting point, root directory. /etc is the etc directory in the / directory.

if you were in /etc, and wanted to change to network, you could either:

```

cd ./network

```

```

cd network

```

or

```

cd /etc/network

```

[http://en.wikipedia.org/wiki/Unix_directory_structure](http://en.wikipedia.org/wiki/Unix_directory_structure)

---

### Post by Garrett87 on 2013-05-02
Ok so that makes sense, I haven't been using Ubuntu long and thought you had to use / to seperate directories. Thanks for the help.

---

