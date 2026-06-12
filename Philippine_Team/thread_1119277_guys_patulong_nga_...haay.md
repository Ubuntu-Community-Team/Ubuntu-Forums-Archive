---
title: "guys patulong nga ...haay"
date: 2009-04-07
forum: Philippine Team
---

### Post by sanozuke02 on 2009-04-07
gsto ko kc magsend ng files gling s phone ko to ubuntu,, may bluetooth drive akong binile pero ndi ko lam pno mag send ng files,,, meron din akong usb connector ng N70 ko kso,, kinoconnect lng nia ung phone as modem,,, help nmn,,,,,,

---

### Post by loell on 2009-04-07
from [http://www.delaere.nl/blog/2008/nokia-n70-with-ubuntu/]("http://www.delaere.nl/blog/2008/nokia-n70-with-ubuntu/")

> ** Nokia N70 with Ubuntu**
Filed Under (Linux Enthousiasm) by martensson

Well well..

Since I got a brand new N70 I need to set up my Nokia N70 with Ubuntu.. So I started Googling..

    [http://cholito.org/2007/12/17/nokia-n70-and-linux](http://cholito.org/2007/12/17/nokia-n70-and-linux)

    [http://www.smokinglinux.com/tutorials/nokia-pc-suite-for-linux-with-obextool-on-ubuntu-gutsy](http://www.smokinglinux.com/tutorials/nokia-pc-suite-for-linux-with-obextool-on-ubuntu-gutsy)

And I decided to use Obextool for uploading / downloading my pictures, ring-tones games etc..

First install obexftp, obexfs en obextool

    * sudo apt-get install obexfs obexftp obextool

Well great,the tooling is present. Since I am a GUI freak, I want obextool in my Gnome menu.

    * sudo gedit /usr/share/applications/obextool.desktop

And fill it with the right information

    * [Desktop Entry]
    * Encoding=UTF-8
      Version=1.0
      Type=Application
      Exec=gksudo startobex
      Icon=/usr/share/icons/gnome/scalable/devices/phone.svg
      Terminal=false
      Name=Obextool
      GenericName=
      Comment=Browser your Mobile Phone
      Categories=Application;Utility;

As you will have noticed, I refer to an script called startobex. This is because gksudo can&#8217;t handle the &#8221; &#8221; as parameter delimiters used by obextool. I need gksudo to start the tool as root user. Below, the contents of startobex file (placed in /usr/bin)

    * obextool &#8211;obexcmd &#8220;obexftp -u 1&#8243;

Well.. Almost there ;) Now you should see your device file listing within the obextool.

When Obextool connects with an Nokia device, it still tries to get information about the memory. Sadly enough this only works with Siemens phones, so let&#8217;s turn it off!

    * sudo gedit /etc/obextool.cfg

And edit the follow params

    * set ObexConfig(config,memstatus) 0

    * set ObexConfig(config,filemove) 0

The second option (filemove) is also an Siemens Phones only option, so lets turn that off too.

By default the slashes (/) are not used by Obextool. For my Nokia N70 to work, It does need to use the slashes. So let&#8217;s turn it on! (same config file as above mentioned)

    * set ObexConfig(config,dir_slash) 1

And now.. It works as a charm.. I uploaded all my ring-tones, games etc.

Ofcourse you can also mount your Nokia Device. But, as far as I saw, only with superuser rights, so normal users cant access the mount (setting udev permissions right should fix this, but right now I don&#8217;t know how)


---

