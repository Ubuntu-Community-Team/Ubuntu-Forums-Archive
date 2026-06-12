---
title: "Support for HUION 1409 pen Tablet"
date: 2016-11-04
forum: Programming Talk
---

### Post by checoimg on 2016-11-04
I'm looking for the configuration file about supporting this one and the configuration i s apparently changed after I used it.


I tried setting the code as I understood was in place but still get compiling errors, and here are the original files amd my modified version along with screenshots. The screenshots can be viewed in order by clicking the image viewer to the left.
 
**Guide**

[URL="https://drive.google.com/file/d/0Byz2eP79s2XmTWw3SDAxLTk5dXM/view?usp=sharing"]Modified

Original[/URL]


***************************************************************
**ls /etc**
***************************************************************
```
acpi                    hosts            popularity-contest.conf
adduser.conf            hosts.allow      ppp
alternatives            hosts.deny       profile
anacrontab              hp               profile.d
apache2                 ifplugd          protocols
apg.conf                iftab            pulse
apm                     ImageMagick-6    python
apparmor                init             python2.7
apparmor.d              init.d           python3
apport                  initramfs-tools  python3.5
appstream.conf          inputrc          rc0.d
apt                     insserv          rc1.d
aptdaemon               insserv.conf     rc2.d
at-spi2                 insserv.conf.d   rc3.d
avahi                   iproute2         rc4.d
bash.bashrc             issue            rc5.d
bash_completion         issue.net        rc6.d
bash_completion.d       java-8-openjdk   rc.local
bindresvport.blacklist  jython           rcS.d
binfmt.d                kbd              resolvconf
bluetooth               kernel           resolv.conf
bogofilter.cf           kernel-img.conf  rmt
bonobo-activation       kerneloops.conf  rpc
brlapi.key              ldap             rsyslog.conf
brltty                  ld.so.cache      rsyslog.d
brltty.conf             ld.so.conf       sane.d
ca-certificates         ld.so.conf.d     securetty
ca-certificates.conf    legal            security
calendar                libao.conf       selinux
chatscripts             libaudit.conf    sensors3.conf
chromium-browser        libgda-5.0       sensors.d
clamav                  libnl-3          services
compizconfig            libpaper.d       sgml
console-setup           libreoffice      shadow
cpufreqd.conf           lightdm          shadow-
cracklib                lighttpd         shells
cron.d                  lintianrc        signond.conf
cron.daily              locale.alias     signon-ui
cron.hourly             locale.gen       skel
cron.monthly            localtime        smi.conf
crontab                 logcheck         sound
cron.weekly             login.defs       speech-dispatcher
cups                    logrotate.conf   ssh
cupshelpers             logrotate.d      ssl
dbus-1                  lsb-release      subgid
dconf                   ltrace.conf      subgid-
debconf.conf            machine-id       subuid
debian_version          magic            subuid-
default                 magic.mime       sudoers
deluser.conf            mail             sudoers.d
depmod.d                mailcap          sysctl.conf
dhcp                    mailcap.order    sysctl.d
dictionaries-common     manpath.config   systemd
dnsmasq.d               mime.types       terminfo
doc-base                mke2fs.conf      texmf
dpkg                    modprobe.d       thermald
drirc                   modules          thunderbird
eclipse.ini             modules-load.d   timezone
emacs                   mono             timidity
environment             mpv              tmpfiles.d
ffserver.conf           mtab             ucf.conf
firefox                 mtools.conf      udev
fish                    mysql            udisks2
fonts                   nanorc           ufw
fstab                   netscsid.conf    updatedb.conf
fuse.conf               network          update-manager
fwupd.conf              NetworkManager   update-motd.d
gai.conf                networks         update-notifier
gconf                   newt             UPower
gdb                     nsswitch.conf    upstart-xsessions
ghostscript             ODBCDataSources  usb_modeswitch.conf
gimp                    odbc.ini         usb_modeswitch.d
gnome                   odbcinst.ini     vdpau_wrapper.cfg
gnome-app-install       openal           vim
gnome-vfs-2.0           opt              vtrgb
groff                   os-release       wgetrc
group                   pam.conf         wildmidi
group-                  pam.d            wireshark
grub.d                  papersize        wodim.conf
gshadow                 passwd           wordpress
gshadow-                passwd-          wpa_supplicant
gss                     pcmcia           X11
gtk-2.0                 perl             xdg
gtk-3.0                 php              xml
guest-session           pki              xul-ext
hdparm.conf             pm               zsh_command_not_found
host.conf               pnm2ppa.conf
hostname                polkit-1
```
*************************************************************18

---

### Post by checoimg on 2016-11-14
I modified the Guide from HUION. I also want to see If i can get it packaged with make dep-pkg

```
/***********************/
Preparation


Install libncurses
/***********************/


Copy huiontablet.c to /drivers/hid


Open Makefile ,before the end of file ,you can write
  
obj-$(CONFIG_HID_HUIONTABLET)    += huiontablet.


Open Kconfig,after "drivers/hid/usbhid/Kconfig" (about Line 60),add


config HID_HUIONTABLET
    tristate "Huion tablet"    
    depends on INPUT
    ---help---
    Support for Huion tablet.
    
Open driver/hid/hid-ids.h,before endif(about Line 675),add


#define USB_VENDOR_ID_HUIONTABLET 0x256C
#define USB_DEVICE_ID_HUIONTABLET 0x0005
#define USB_DEVICE_ID_HUIONTABLET2 0x006E


Enter the folder /drivers/hid/usbhid,open hid-quirks.c,in hid_blacklist struct,before { 0, 0 }


{ USB_VENDOR_ID_HUIONTABLET,USB_DEVICE_ID_HUIONTABLET, HID_QUIRK_IGNORE},
{ USB_VENDOR_ID_HUIONTABLET,USB_DEVICE_ID_HUIONTABLET2, HID_QUIRK_IGNORE},


do  make menuconfig


Go into


Device Drivers-> HID Devices-> Huion tablet//Needs updating


make

make modules_install //Will this step install anything ?

make install
```

---

### Post by checoimg on 2016-11-19
I left the changes on the Kernel to the 4.4.0 version which is the ubuntu source code

I did ```
apt-get source linux
```

And after that I haven't compiled the kernel yet.


This is the ourput when I try make menuconfig

```


make menuconfig
  HOSTCC  scripts/kconfig/mconf.o
In file included from scripts/kconfig/mconf.c:23:0:
scripts/kconfig/lxdialog/dialog.h:38:20: fatal error: curses.h: No such file or directory
compilation terminated.
scripts/Makefile.host:108: recipe for target 'scripts/kconfig/mconf.o' failed
make[1]: *** [scripts/kconfig/mconf.o] Error 1
Makefile:551: recipe for target 'menuconfig' failed
make: *** [menuconfig] Error 2


```

---

### Post by checoimg on 2017-02-04
**This is form XINPUT**


```
&#9116;   &#8627; HUION Huion Tablet Consumer Control         id=17    [slave  pointer  (2)]
&#9116;   &#8627; HUION Huion Tablet Mouse                    id=19    [slave  pointer  (2)]
&#9116;   &#8627; HUION Huion Tablet Pen                      id=20    [slave  pointer  (2)]
    &#8627; HUION Huion Tablet Keyboard                 id=16    [slave  keyboard (3)]
    &#8627; HUION Huion Tablet System Control           id=18    [slave  keyboard (3)]

```
```
[B]
16[/B]

1 class :
KeyClass
    key[0]=up
    key[1]=up
    key[2]=up
    key[3]=up
    key[4]=up
    key[5]=up
    key[6]=up
    key[7]=up
    key[8]=up
    key[9]=up
    key[10]=up
    key[11]=up
    key[12]=up
    key[13]=up
    key[14]=up
    key[15]=up
    key[16]=up
    key[17]=up
    key[18]=up
    key[19]=up
    key[20]=up
    key[21]=up
    key[22]=up
    key[23]=up
    key[24]=up
    key[25]=up
    key[26]=up
    key[27]=up
    key[28]=up
    key[29]=up
    key[30]=up
    key[31]=up
    key[32]=up
    key[33]=up
    key[34]=up
    key[35]=up
    key[36]=up
    key[37]=up
    key[38]=up
    key[39]=up
    key[40]=up
    key[41]=up
    key[42]=up
    key[43]=up
    key[44]=up
    key[45]=up
    key[46]=up
    key[47]=up
    key[48]=up
    key[49]=up
    key[50]=up
    key[51]=up
    key[52]=up
    key[53]=up
    key[54]=up
    key[55]=up
    key[56]=up
    key[57]=up
    key[58]=up
    key[59]=up
    key[60]=up
    key[61]=up
    key[62]=up
    key[63]=up
    key[64]=up
    key[65]=up
    key[66]=up
    key[67]=up
    key[68]=up
    key[69]=up
    key[70]=up
    key[71]=up
    key[72]=up
    key[73]=up
    key[74]=up
    key[75]=up
    key[76]=up
    key[77]=up
    key[78]=up
    key[79]=up
    key[80]=up
    key[81]=up
    key[82]=up
    key[83]=up
    key[84]=up
    key[85]=up
    key[86]=up
    key[87]=up
    key[88]=up
    key[89]=up
    key[90]=up
    key[91]=up
    key[92]=up
    key[93]=up
    key[94]=up
    key[95]=up
    key[96]=up
    key[97]=up
    key[98]=up
    key[99]=up
    key[100]=up
    key[101]=up
    key[102]=up
    key[103]=up
    key[104]=up
    key[105]=up
    key[106]=up
    key[107]=up
    key[108]=up
    key[109]=up
    key[110]=up
    key[111]=up
    key[112]=up
    key[113]=up
    key[114]=up
    key[115]=up
    key[116]=up
    key[117]=up
    key[118]=up
    key[119]=up
    key[120]=up
    key[121]=up
    key[122]=up
    key[123]=up
    key[124]=up
    key[125]=up
    key[126]=up
    key[127]=up
    key[128]=up
    key[129]=up
    key[130]=up
    key[131]=up
    key[132]=up
    key[133]=up
    key[134]=up
    key[135]=up
    key[136]=up
    key[137]=up
    key[138]=up
    key[139]=up
    key[140]=up
    key[141]=up
    key[142]=up
    key[143]=up
    key[144]=up
    key[145]=up
    key[146]=up
    key[147]=up
    key[148]=up
    key[149]=up
    key[150]=up
    key[151]=up
    key[152]=up
    key[153]=up
    key[154]=up
    key[155]=up
    key[156]=up
    key[157]=up
    key[158]=up
    key[159]=up
    key[160]=up
    key[161]=up
    key[162]=up
    key[163]=up
    key[164]=up
    key[165]=up
    key[166]=up
    key[167]=up
    key[168]=up
    key[169]=up
    key[170]=up
    key[171]=up
    key[172]=up
    key[173]=up
    key[174]=up
    key[175]=up
    key[176]=up
    key[177]=up
    key[178]=up
    key[179]=up
    key[180]=up
    key[181]=up
    key[182]=up
    key[183]=up
    key[184]=up
    key[185]=up
    key[186]=up
    key[187]=up
    key[188]=up
    key[189]=up
    key[190]=up
    key[191]=up
    key[192]=up
    key[193]=up
    key[194]=up
    key[195]=up
    key[196]=up
    key[197]=up
    key[198]=up
    key[199]=up
    key[200]=up
    key[201]=up
    key[202]=up
    key[203]=up
    key[204]=up
    key[205]=up
    key[206]=up
    key[207]=up
    key[208]=up
    key[209]=up
    key[210]=up
    key[211]=up
    key[212]=up
    key[213]=up
    key[214]=up
    key[215]=up
    key[216]=up
    key[217]=up
    key[218]=up
    key[219]=up
    key[220]=up
    key[221]=up
    key[222]=up
    key[223]=up
    key[224]=up
    key[225]=up
    key[226]=up
    key[227]=up
    key[228]=up
    key[229]=up
    key[230]=up
    key[231]=up
    key[232]=up
    key[233]=up
    key[234]=up
    key[235]=up
    key[236]=up
    key[237]=up
    key[238]=up
    key[239]=up
    key[240]=up
    key[241]=up
    key[242]=up
    key[243]=up
    key[244]=up
    key[245]=up
    key[246]=up
    key[247]=up
[B]
17[/B]

3 classes :
KeyClass
    key[0]=up
    key[1]=up
    key[2]=up
    key[3]=up
    key[4]=up
    key[5]=up
    key[6]=up
    key[7]=up
    key[8]=up
    key[9]=up
    key[10]=up
    key[11]=up
    key[12]=up
    key[13]=up
    key[14]=up
    key[15]=up
    key[16]=up
    key[17]=up
    key[18]=up
    key[19]=up
    key[20]=up
    key[21]=up
    key[22]=up
    key[23]=up
    key[24]=up
    key[25]=up
    key[26]=up
    key[27]=up
    key[28]=up
    key[29]=up
    key[30]=up
    key[31]=up
    key[32]=up
    key[33]=up
    key[34]=up
    key[35]=up
    key[36]=up
    key[37]=up
    key[38]=up
    key[39]=up
    key[40]=up
    key[41]=up
    key[42]=up
    key[43]=up
    key[44]=up
    key[45]=up
    key[46]=up
    key[47]=up
    key[48]=up
    key[49]=up
    key[50]=up
    key[51]=up
    key[52]=up
    key[53]=up
    key[54]=up
    key[55]=up
    key[56]=up
    key[57]=up
    key[58]=up
    key[59]=up
    key[60]=up
    key[61]=up
    key[62]=up
    key[63]=up
    key[64]=up
    key[65]=up
    key[66]=up
    key[67]=up
    key[68]=up
    key[69]=up
    key[70]=up
    key[71]=up
    key[72]=up
    key[73]=up
    key[74]=up
    key[75]=up
    key[76]=up
    key[77]=up
    key[78]=up
    key[79]=up
    key[80]=up
    key[81]=up
    key[82]=up
    key[83]=up
    key[84]=up
    key[85]=up
    key[86]=up
    key[87]=up
    key[88]=up
    key[89]=up
    key[90]=up
    key[91]=up
    key[92]=up
    key[93]=up
    key[94]=up
    key[95]=up
    key[96]=up
    key[97]=up
    key[98]=up
    key[99]=up
    key[100]=up
    key[101]=up
    key[102]=up
    key[103]=up
    key[104]=up
    key[105]=up
    key[106]=up
    key[107]=up
    key[108]=up
    key[109]=up
    key[110]=up
    key[111]=up
    key[112]=up
    key[113]=up
    key[114]=up
    key[115]=up
    key[116]=up
    key[117]=up
    key[118]=up
    key[119]=up
    key[120]=up
    key[121]=up
    key[122]=up
    key[123]=up
    key[124]=up
    key[125]=up
    key[126]=up
    key[127]=up
    key[128]=up
    key[129]=up
    key[130]=up
    key[131]=up
    key[132]=up
    key[133]=up
    key[134]=up
    key[135]=up
    key[136]=up
    key[137]=up
    key[138]=up
    key[139]=up
    key[140]=up
    key[141]=up
    key[142]=up
    key[143]=up
    key[144]=up
    key[145]=up
    key[146]=up
    key[147]=up
    key[148]=up
    key[149]=up
    key[150]=up
    key[151]=up
    key[152]=up
    key[153]=up
    key[154]=up
    key[155]=up
    key[156]=up
    key[157]=up
    key[158]=up
    key[159]=up
    key[160]=up
    key[161]=up
    key[162]=up
    key[163]=up
    key[164]=up
    key[165]=up
    key[166]=up
    key[167]=up
    key[168]=up
    key[169]=up
    key[170]=up
    key[171]=up
    key[172]=up
    key[173]=up
    key[174]=up
    key[175]=up
    key[176]=up
    key[177]=up
    key[178]=up
    key[179]=up
    key[180]=up
    key[181]=up
    key[182]=up
    key[183]=up
    key[184]=up
    key[185]=up
    key[186]=up
    key[187]=up
    key[188]=up
    key[189]=up
    key[190]=up
    key[191]=up
    key[192]=up
    key[193]=up
    key[194]=up
    key[195]=up
    key[196]=up
    key[197]=up
    key[198]=up
    key[199]=up
    key[200]=up
    key[201]=up
    key[202]=up
    key[203]=up
    key[204]=up
    key[205]=up
    key[206]=up
    key[207]=up
    key[208]=up
    key[209]=up
    key[210]=up
    key[211]=up
    key[212]=up
    key[213]=up
    key[214]=up
    key[215]=up
    key[216]=up
    key[217]=up
    key[218]=up
    key[219]=up
    key[220]=up
    key[221]=up
    key[222]=up
    key[223]=up
    key[224]=up
    key[225]=up
    key[226]=up
    key[227]=up
    key[228]=up
    key[229]=up
    key[230]=up
    key[231]=up
    key[232]=up
    key[233]=up
    key[234]=up
    key[235]=up
    key[236]=up
    key[237]=up
    key[238]=up
    key[239]=up
    key[240]=up
    key[241]=up
    key[242]=up
    key[243]=up
    key[244]=up
    key[245]=up
    key[246]=up
    key[247]=up
ButtonClass
    button[1]=up
    button[2]=up
    button[3]=up
    button[4]=up
    button[5]=up
    button[6]=up
    button[7]=up
ValuatorClass Mode=Relative Proximity=In
    valuator[0]=960
    valuator[1]=540
    valuator[2]=0
[B]
18[/B]

1 class :
KeyClass
    key[0]=up
    key[1]=up
    key[2]=up
    key[3]=up
    key[4]=up
    key[5]=up
    key[6]=up
    key[7]=up
    key[8]=up
    key[9]=up
    key[10]=up
    key[11]=up
    key[12]=up
    key[13]=up
    key[14]=up
    key[15]=up
    key[16]=up
    key[17]=up
    key[18]=up
    key[19]=up
    key[20]=up
    key[21]=up
    key[22]=up
    key[23]=up
    key[24]=up
    key[25]=up
    key[26]=up
    key[27]=up
    key[28]=up
    key[29]=up
    key[30]=up
    key[31]=up
    key[32]=up
    key[33]=up
    key[34]=up
    key[35]=up
    key[36]=up
    key[37]=up
    key[38]=up
    key[39]=up
    key[40]=up
    key[41]=up
    key[42]=up
    key[43]=up
    key[44]=up
    key[45]=up
    key[46]=up
    key[47]=up
    key[48]=up
    key[49]=up
    key[50]=up
    key[51]=up
    key[52]=up
    key[53]=up
    key[54]=up
    key[55]=up
    key[56]=up
    key[57]=up
    key[58]=up
    key[59]=up
    key[60]=up
    key[61]=up
    key[62]=up
    key[63]=up
    key[64]=up
    key[65]=up
    key[66]=up
    key[67]=up
    key[68]=up
    key[69]=up
    key[70]=up
    key[71]=up
    key[72]=up
    key[73]=up
    key[74]=up
    key[75]=up
    key[76]=up
    key[77]=up
    key[78]=up
    key[79]=up
    key[80]=up
    key[81]=up
    key[82]=up
    key[83]=up
    key[84]=up
    key[85]=up
    key[86]=up
    key[87]=up
    key[88]=up
    key[89]=up
    key[90]=up
    key[91]=up
    key[92]=up
    key[93]=up
    key[94]=up
    key[95]=up
    key[96]=up
    key[97]=up
    key[98]=up
    key[99]=up
    key[100]=up
    key[101]=up
    key[102]=up
    key[103]=up
    key[104]=up
    key[105]=up
    key[106]=up
    key[107]=up
    key[108]=up
    key[109]=up
    key[110]=up
    key[111]=up
    key[112]=up
    key[113]=up
    key[114]=up
    key[115]=up
    key[116]=up
    key[117]=up
    key[118]=up
    key[119]=up
    key[120]=up
    key[121]=up
    key[122]=up
    key[123]=up
    key[124]=up
    key[125]=up
    key[126]=up
    key[127]=up
    key[128]=up
    key[129]=up
    key[130]=up
    key[131]=up
    key[132]=up
    key[133]=up
    key[134]=up
    key[135]=up
    key[136]=up
    key[137]=up
    key[138]=up
    key[139]=up
    key[140]=up
    key[141]=up
    key[142]=up
    key[143]=up
    key[144]=up
    key[145]=up
    key[146]=up
    key[147]=up
    key[148]=up
    key[149]=up
    key[150]=up
    key[151]=up
    key[152]=up
    key[153]=up
    key[154]=up
    key[155]=up
    key[156]=up
    key[157]=up
    key[158]=up
    key[159]=up
    key[160]=up
    key[161]=up
    key[162]=up
    key[163]=up
    key[164]=up
    key[165]=up
    key[166]=up
    key[167]=up
    key[168]=up
    key[169]=up
    key[170]=up
    key[171]=up
    key[172]=up
    key[173]=up
    key[174]=up
    key[175]=up
    key[176]=up
    key[177]=up
    key[178]=up
    key[179]=up
    key[180]=up
    key[181]=up
    key[182]=up
    key[183]=up
    key[184]=up
    key[185]=up
    key[186]=up
    key[187]=up
    key[188]=up
    key[189]=up
    key[190]=up
    key[191]=up
    key[192]=up
    key[193]=up
    key[194]=up
    key[195]=up
    key[196]=up
    key[197]=up
    key[198]=up
    key[199]=up
    key[200]=up
    key[201]=up
    key[202]=up
    key[203]=up
    key[204]=up
    key[205]=up
    key[206]=up
    key[207]=up
    key[208]=up
    key[209]=up
    key[210]=up
    key[211]=up
    key[212]=up
    key[213]=up
    key[214]=up
    key[215]=up
    key[216]=up
    key[217]=up
    key[218]=up
    key[219]=up
    key[220]=up
    key[221]=up
    key[222]=up
    key[223]=up
    key[224]=up
    key[225]=up
    key[226]=up
    key[227]=up
    key[228]=up
    key[229]=up
    key[230]=up
    key[231]=up
    key[232]=up
    key[233]=up
    key[234]=up
    key[235]=up
    key[236]=up
    key[237]=up
    key[238]=up
    key[239]=up
    key[240]=up
    key[241]=up
    key[242]=up
    key[243]=up
    key[244]=up
    key[245]=up
    key[246]=up
    key[247]=up
[B]
19[/B]

2 classes :
ButtonClass
    button[1]=up
    button[2]=up
    button[3]=up
    button[4]=up
    button[5]=up
    button[6]=up
    button[7]=up
    button[8]=up
    button[9]=up
    button[10]=up
    button[11]=up
    button[12]=up
    button[13]=up
ValuatorClass Mode=Relative Proximity=In
    valuator[0]=960
    valuator[1]=540
    valuator[2]=0
    valuator[3]=0
[B]
20
[/B]
2 classes :
ButtonClass
    button[1]=up
    button[2]=up
    button[3]=up
    button[4]=up
    button[5]=up
    button[6]=up
    button[7]=up
ValuatorClass Mode=Absolute Proximity=In
    valuator[0]=960
    valuator[1]=540
    valuator[2]=0
```

---

### Post by wildmanne39 on 2017-02-04
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by checoimg on 2017-07-12
[B](for future reference)
Install Digimend driver via DKMS:[/B]

I wanted to be sure to get the latest source code compiled for the Digimend project, in case more could work with more recent development. Unfortunately, I had to make many test and trial to compile the source of the project. Impossible to do the make/make install, 'deb' package not working... I had to search a long time how I could do. After many research, it appear all Ubuntu-based 16.04 can't compile custom module this way. It's prohibited (but the error message wasn't very obvious about it).

The only option is to install the DKMS way. The README.md file of the project doesn't explain how. After research, I learned the joy of DKMS. To install via DKMS, you'll need Git, and DKMS.
```
sudo apt install dkms git-core then we will put the source code inside a specific directory with the structure /usr/src/<PROJECTNAME>-<VERSION> , then build it using this time <PROJECTNAME>/<VERSION> :
sudo git clone [https://github.com/DIGImend/digimend-kernel-drivers.git](https://github.com/DIGImend/digimend-kernel-drivers.git) /usr/src/digimend-6
sudo dkms build digimend/6
sudo dkms install digimend/6Reboot your computer. The tablet should now start to work better, smoother and being listed as "TABLET Pen Tablet Pen stylus" when entering this command in a terminal:
xinput --listThe digimend driver should be listed among other modules after typing:
dkms statusIcing on the cake, you can now remove the USB cable (used to charge the tablet), connect the wireless USB dongle, and use the tablet in wireless. The tablet is still here with lsusb.
```

**Add a custom X11 rules:**

We need a way to now configure the tablet, the buttons. We will add a X11 custom rule to make the Digimend driver use the Wacom driver command line tool to setup our non-named <TABLET>.

Call your text-editor in admin mode:
```
sudo xed /usr/share/X11/xorg.conf.d/50-huion.confThen paste this inside, save and close.
# Huion tablets
Section "InputClass"
Identifier "Huion class"
MatchProduct "TABLET"
MatchIsTablet "on"
MatchDevicePath "/dev/input/event*"
Driver "wacom"
EndSection

Section "InputClass"
Identifier "Huion buttons"
MatchProduct "TABLET"
MatchIsKeyboard "on"
MatchDevicePath "/dev/input/event*"
Driver "evdev"
EndSection

Section "InputClass"
Identifier "Huion scroll"
MatchProduct "TABLET"
MatchIsPointer "off"
MatchIsKeyboard "off"
MatchIsTouchpad "off"
MatchIsTablet "off"
MatchIsTouchscreen "off"
MatchDevicePath "/dev/input/event*"
Driver "evdev"
EndSection
Reboot your computer. After that, the tablet should appear in the configuration tool xsetwacom:
xsetwacom --list
Congratulation! You're done with the driver part. 

**User preference, buttons, settings.**

Now, let configure the tablet with xsetwacom.
For this, we can load xsetwacom command. But they are not persistent avec restarting computer.
So we need to store this collections of commands in a bash script and call this bash script when the system open. 
mkdir scripts
xed ~/scripts/Huion_WH1409.sh... and inside paste and customize the script under. To know the list of special "key" you can map on buttons, look at [this list]("https://pastebin.com/aXGDkJTU"). Don't forget to change the screen size to your screen size (the tablet is not 100% same ratio than 1920x1080, it needs code to force good vertical and horizontal ratio so when you trace a circle on your tablet, a circle appear on the screen, and not an ellipse potato ). And comment or delete all the line you are not interested.
#! /bin/bash
# Setup HUION WH1409, after bridged to wacom driver with Digimend Kernel module.
# License: CC-0/Public-Domain license
# author: deevad

# Tablet definition
tabletstylus="TABLET Pen Tablet Pen stylus"
tabletpad="TABLET Pen Tablet Pad pad"

# Reset
xsetwacom --set "$tabletstylus" ResetArea
xsetwacom --set "$tabletstylus" RawSample 4

# Mapping
# get maximum size geometry with:
# xsetwacom --get "$tabletstylus" Area
# 0 0 55200 34500
tabletX=55200
tabletY=34500
# screen size:
screenX=1920
screenY=1080
# map to good screen (dual nvidia)
xsetwacom --set "$tabletstylus" MapToOutput "HEAD-0"
# setup ratio :
newtabletY=$(( $screenY * $tabletX / $screenX ))
xsetwacom --set "$tabletstylus" Area 0 0 "$tabletX" "$newtabletY"


# Buttons
# =======
xsetwacom --set "$tabletstylus" Button 2 2 
xsetwacom --set "$tabletstylus" Button 3 3
# ---------
# | 1 | 2 |
# |---|---|
# | 3 | 8 |
# |=======|
# | 9 |10 |
# |---|---|
# |11 |12 |
# |=======|
# |13 | ? |
# |---|---|
# | ? | ? |
# |=======|
xsetwacom --set "$tabletpad" Button 1 "key Control_L" # color picker on ring
xsetwacom --set "$tabletpad" Button 2 "key Shift_L" # resize brush
xsetwacom --set "$tabletpad" Button 3 "key KP_Divide" # switch /
xsetwacom --set "$tabletpad" Button 8 "key e" # eraser
xsetwacom --set "$tabletpad" Button 9 "key z" # undo
xsetwacom --set "$tabletpad" Button 10 "key y"
xsetwacom --set "$tabletpad" Button 11 "key tab"
xsetwacom --set "$tabletpad" Button 12 "key r"
xsetwacom --set "$tabletpad" Button 13 "key m"


# Xinput option
# =============
# for the list:
# xinput --list

# xinput list-props 'TABLET Pen Tablet Mouse'
xinput set-prop 'TABLET Pen Tablet Mouse' "Evdev Middle Button Emulation" 0
# alternate way to map to a single screen
# execute "xrander" in a terminal to get the screen name ( DVI-D-0 in this example )
# xinput set-prop 'TABLET Pen Tablet Pen stylus' DVI-D-0
```

[Source]("https://www.davidrevoy.com/article331/setup-huion-giano-wh1409-tablet-on-linux-mint-18-1-ubuntu-16-04")

---

