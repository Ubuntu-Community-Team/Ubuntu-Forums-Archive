---
title: "Access your Mobile phone using USB cable"
date: 2006-07-08
forum: Outdated Tutorials &amp; Tips
---

### Post by revenant_org on 2006-07-08
Hello, I hope this guide will help someone out there. I spent almost the whole day trying to run [ openobex]("http://openobex.triq.net/") on my Dapper. 

This guide describes the steps needed to get your [mobile phone]("http://openobex.triq.net/devices/devices") working under (Ubuntu Dapper)linux using USB cable.


[B]
A. Openobex  [/B]

The problem is openobex couldn't see my Nokia N70 mobile as a USB device. I tried to test the usb interfaces using the following command:
```
$obex_test -u
```
and I got the following output
```

Using USB transport, querying available interfaces
Use 'obex_test -u interface_number' to run interactive OBEX test client

```
not quite the expected one. :shock: 

While "Google"ing around I found a guide on [this forum (pl) ]("http://www.symbianos.pl/Artyku%B3y/Porady/Przesy%B3anie_plik%F3w_z_i_do_Nokii_pod_Linuksem/"), I didn't understand what is written there, I just followed the steps listed there and guess what :-$.
It worked :-({|= .

So, I will try to illustrate what I have done exactly. 

1. download the cvs version of [ openobex]("http://openobex.triq.net/").
```

$ cvs -d:pserver: anonymous@openobex.cvs.sourceforge.net  :/cvsroot/openobex login
$ cvs -z3 -d:pserver: anonymous@openobex.cvs.sourceforge.net   /cvsroot/openobex co -P openobex 

```

2. Install some essential packages.

```

$ sudo apt-get install gcc make automake1.4 autoconf libusb-dev libtool 
```


3. Compiling & Installing openobex package.

```

$ mkdir ~/usbobex
$ cd openobex
$ ./bootstrap
$ ./configure --prefix=$HOME/usbobex --enable-apps
$ make
$ make install 

```

4. Testing the usb interfaces.

```

$ ~/usbobex/bin/obex_test -u 

```

The output should be something like that
```

Using USB transport, querying available interfaces
Interface 0: Nokia Nokia N70 SYNCML-SYNC
Interface 1: Nokia Nokia N70 PC Suite Services
Use '/home/tiger/usbobex/bin/obex_test -u interface_number' to run interactive OBEX test client

```

:cool: Done

*Note: I tried to install openobex using dapper's backports but unfortunately it didn't work at least for me. *



**B. Fixing udev permissions**

1. Identify your mobile's Vendor, and Product id.
```

$ lsusb

```
you will get somthing like that
```
Bus 004 Device 003: ID 0421:043a Nokia Mobile Phones
```
=> Vendor id = 0421
=> Product id = 043a 

2. Fix udev permissions
```
$ sudo gedit /etc/udev/rules.d/040_permissions.rules
```
then append the following line at the bottom
```

BUS=="usb", SYSFS{idVendor}=="*VendorId*", SYSFS{idProduct}=="*ProductId*", GROUP="plugdev", USER="*yourUserNname*"
```


**C. Obexftp **
I am using [obexftp]("http://openobex.triq.net/obexftp/obexftp") to download & upload music, video, etc from/to my mobile phone. It is a great utility and the only one that worked with my mobile.

So let's get started with the installation.

1. download the source
```

$wget http://triq.net/obexftp/obexftp-0.20.tar.gz
$tar -xvf obexftp-0.20.tar.gz
$cd obexftp-0.20

```

2. Compile and install
```

$ aclocal -I $HOME/usbobex/share/aclocal && autoheader && automake --copy --add-missing && autoconf
$ ./configure --prefix=$HOME/usbobex OPENOBEX_CONFIG=$HOME/usbobex/bin/openobex-config --disable-perl --disable-python --disable-tcl
$ make
$ make install

```
 
3. Test it 
```
$ ~/usbobex/bin/obexftp -u 1 -c C:/ -l
```
The output should be something like the following:
```

If USB doesn't work setup permissions in udev or run as superuser.
Connecting...done
Sending "C:"... done
Receiving "(null)"... <?xml version="1.0"?>
<!DOCTYPE folder-listing SYSTEM "obex-folder-listing.dtd"
  [ <!ATTLIST folder mem-type CDATA #IMPLIED>
  <!ATTLIST folder label CDATA #IMPLIED> ]>
<folder-listing version="1.0">
   <parent-folder />
   <folder name="cache" modified="20060408T123426Z" user-perm="RWD" mem-type="DEV"/>
   <folder name="Nokia" modified="20050101T010010Z" user-perm="RWD" mem-type="DEV"/>
   <file name="DSPROFILEEDITOR.EXE" size="3881" modified="20060408T151420Z" user-perm="RWD"/>
   <file name="o2 Music" size="51" modified="20060408T130430Z" user-perm="RWD"/>
</folder-listing>done
Disconnecting...done


```


For more information plz check [opexftp site]("http://openobex.triq.net/obexftp/obexftp")


That's All .. Have fun
:D
*Plz don't mind my english *:rolleyes:

---

### Post by kb3hkg on 2006-07-10
for my phone Motorolla V360, it worked through usb including file transfers flawlessly right out of the box.

---

### Post by GBlin on 2007-02-05
Just an add to say that automake1.4 seems to be needed to compile openobex-1.3 on dapper.
compiled with automake1.9 doesn't give any usb interface available with obex_test for me on dapper.

Thanks for the tutorial !

---

### Post by Arjunanda on 2007-02-27
Thanks for this guide!

Though I did not get things working, as yet. This guide assumes that you have been using CVS, which is not the case with me. So the following created the first issue:

> **revenant_org said:**
> 
1. download the cvs version of [ openobex]("http://openobex.triq.net/").
```

$ cvs -d:pserver: anonymous@openobex.cvs.sourceforge.net  :/cvsroot/openobex login
$ cvs -z3 -d:pserver: anonymous@openobex.cvs.sourceforge.net   /cvsroot/openobex co -P openobex 

```

I tried the command, but it returned

```
bash: cvs: command not found
```

Ok, I must install CVS:
```

sudo apt-get install cvs

```
and that started a wizard asking where the CVS repositories should be installed. I accepted the defaults. And whether CVS should be enabled, I left the box un-checked.

Then trying the command again, and got the following error:
```
~$ cvs -d:pserver: [email]anonymous@openobex.cvs.sourceforge.net[/email]  :/cvsroot/openobex login
Unknown command: `anonymous@openobex.cvs.sourceforge.net'
```

It appears there were extra spaces in your code. I removed the spaces and got it working. 

```

$ cvs -d:pserver:anonymous@openobex.cvs.sourceforge.net :/cvsroot/openobex login
$ cvs -z3 -d:pserver:anonymous@openobex.cvs.sourceforge.net/cvsroot/openobex co -P openobex 

```

BUT:

```
$ cvs -d:pserver:anonymous@openobex.cvs.sourceforge.net:/cvsroot/openobex login
Logging in to :pserver:anonymous@openobex.cvs.sourceforge.net:2401/cvsroot/openobex
CVS password:
```

What password? I have no CVS password.
Ok, try some bogus password for the anonymous user. And the result:

cvs login: CVS password file /home/myfolder/.cvspass does not exist - creating a new file

Trying again:

```
$ cvs -d:pserver:anonymous@openobex.cvs.sourceforge.net:/cvsroot/openobex login
Logging in to :pserver:anonymous@openobex.cvs.sourceforge.net:2401/cvsroot/openobex
CVS password:
```

And this time, no error. So I assume it worked.

Then the second command:

```
$ cvs -z3 -d:pserver:anonymous@openobex.cvs.sourceforge.net/cvsroot/openobex co -P openobex~ 
```

Gives some error:

```
cvs server: cannot find module `openobex~' - ignored
cvs [checkout aborted]: cannot expand modules
```

Now I am stuck here. Any ideas? I would love to get my N70-1 (Music Edition) connected to my laptop...

---

### Post by Arjunanda on 2007-02-27
Oh now issuing the command again I got further:
```
$ cvs -z3 -d:pserver:anonymous@openobex.cvs.sourceforge.net/cvsroot/openobex co -P openobex
[...]
U openobex/lib/usbobex.h
U openobex/lib/win32compat.c
cvs checkout: Updating openobex/lib/doc
cvs checkout: Updating openobex/lib/m4macros
cvs checkout: Updating openobex/lib/src

```

So I guess the CVS download went fine.

Going further:
```

$ mkdir ~/usbobex
$ cd openobex
$ ./bootstrap
configure.in:24: warning: AC_CANONICAL_HOST invoked multiple times
automake: configure.in: installing `./install-sh'
automake: configure.in: installing `./mkinstalldirs'
automake: configure.in: installing `./missing'
automake: glib/Makefile.am: warning: automake does not support libopenobex_glib_la_LDFLAGS being defined conditionally
glib/Makefile.am:17: invalid unused variable name: `nodist_libopenobex_glib_la_SOURCES'

~/openobex$ ./configure --prefix=$HOME/usbobex --enable-apps
bash: ./configure: No such file or directory

```

I see there is no configure -file. So perhaps the bootstrap script failed?

Here is what is in the directory:
```

$ ls
acinclude.m4         config.h.in   INSTALL        NEWS
aclocal.m4           config.sub    install-sh     openobex-glib.pc.in
apps                 configure.in  ircp           openobex.m4
AUTHORS              COPYING       lib            openobex.pc.in
autom4te.cache       COPYING.LIB   ltmain.sh      README
bootstrap            CVS           Makefile.am    stamp-h.in
bootstrap-configure  doc           Makefile.in
ChangeLog            glib          missing
config.guess         include       mkinstalldirs

```

---

### Post by Arjunanda on 2007-02-27
Found OpenOBEX 1.3 pre-compiled binaries for Ubuntu Dapper at
[http://www.in.fh-merseburg.de/~jahn/opensync-svn/dapper.php](http://www.in.fh-merseburg.de/~jahn/opensync-svn/dapper.php)

Get & install the files:
```

mkdir ~/obex_binaries
cd ~/obex_binaries
wget http://www.in.fh-merseburg.de/~jahn/opensync-svn/pool/main/libo/libopenobex/libopenobex1_1.3-dapper1_i386.deb
wget http://www.in.fh-merseburg.de/~jahn/opensync-svn/pool/main/libo/libopenobex/openobex-apps_1.3-dapper1_i386.deb
wget http://www.in.fh-merseburg.de/~jahn/opensync-svn/pool/main/o/obexftp/obexftp_0.19-5ubuntu1_i386.deb
dpkg -i  libopenobex1_1.3-dapper1_i386.deb
dpkg -i obexftp_0.19-5ubuntu1_i386.deb
dpkg -i openobex-apps_1.3-dapper1_i386.deb

```

And now I can see my phone detected with dmesg:
```

$ dmesg
[...]
[17293630.836000] usb 4-2: new full speed USB device using uhci_hcd and address 14
[17293631.592000] cdc_acm 4-2:1.8: ttyACM0: USB ACM device
[17293631.596000] usbcore: registered new driver cdc_acm
[17293631.596000] drivers/usb/class/cdc-acm.c: v0.23:USB Abstract Control Model driver for USB modems and ISDN adapters

$ lsusb
Bus 004 Device 016: ID 0421:043a Nokia Mobile Phones

```

but:
```

$ obex_test -u
Using USB transport, querying available interfaces
Interface 0:
Interface 1:
Use 'obex_test -u interface_number' to run interactive OBEX test client

```

No phone interface detected. So that did not work either..

---

### Post by celticbhoy on 2007-03-21
will this work for edgy !!!!!

---

### Post by dipasqum on 2007-04-13
Here is what I've learned so far:

This older package conflicts with one that works

Bad:
libopenobex-1.0-0

Good:
libopenobex1  1.3-dapper1

Also testing with CLIs requires sudo

without sudo=

syncml-obex-client -u
Superuser privileges are required to access complete USB information.
Found 4 USB OBEX interfaces
Interface 0:
        Manufacturer:
        Product:
        Interface description:
Interface 1:
        Manufacturer:
        Product:
        Interface description:
Interface 2:
        Manufacturer:
        Product:
        Interface description:
Interface 3:
        Manufacturer:
        Product:
        Interface description:
Use '-u interface_number' to connect
macro@shale:~$ obex_test -u
Using IrDA transport
OBEX Interactive test client/server.


WIth sudo:

sudo syncml-obex-client -u
Found 4 USB OBEX interfaces
Interface 0:
        Manufacturer: Nokia
        Product: Nokia E70
        Interface description: SYNCML-SYNC
Interface 1:
        Manufacturer: Nokia
        Product: Nokia E70
        Interface description: PC Suite Services
Interface 2:
        Manufacturer: Nokia
        Product: Nokia E70
        Interface description: SYNCML-DM
Interface 3:
        Manufacturer: Nokia
        Product: Nokia E70
        Interface description: SYNCML-SYNC-CLIENT-INIT
Use '-u interface_number' to connect

sudo obex_test -u
Using USB transport, querying available interfaces
Interface 0: Nokia Nokia E70 SYNCML-SYNC
Interface 1: Nokia Nokia E70 PC Suite Services
Interface 2: Nokia Nokia E70 SYNCML-DM
Interface 3: Nokia Nokia E70 SYNCML-SYNC-CLIENT-INIT
Use 'obex_test -u interface_number' to run interactive OBEX test client

---

### Post by celticbhoy on 2007-04-14
Just bought a card reader.

but might be of use to someone else

---

### Post by Arjunanda on 2007-04-15
> **dipasqum said:**
> 
Also testing with CLIs requires sudo

Thanks, this was my problem. Now my phone is detected nicely:
```
sudo obex_test -
Password:
Using USB transport, querying available interfaces
Interface 0: Nokia Nokia N70 SYNCML-SYNC
Interface 1: Nokia Nokia N70 PC Suite Services

```

Just have to read the thread once more to learn how to tranfer files and how to connect it with KMobileTools.

---

### Post by Arjunanda on 2007-04-15
obexftp.. Ok, not particularly intuitive user interface. Of course I can use that if there is nothing else.. Is there a way to mount the phone to the filesystem as a usb-storage device?

Anybody been able to use any GUI tool, or KMobileTools with openobex?

---

### Post by Soarer on 2007-04-15
I can connect to my Nokia E70 with [wammu]("http://wammu.eu") but I can then only get information about the phone, no contacts or texts etc.

This phone (REALLY) needs a firmware upgrade, so I'll try it again after I have had that done, but I don't hold out much hope.

I installed multisync from the repos but have no idea how to use it - it just says 'command not found' in a terminal.

And no joy with obexftp either - sudo obexftp -u lists the device, but giving an interface number (e.g. sudo obexftp -u 1) it just says 'nothing to do'

---

### Post by abadi2005 on 2007-04-15
I have a siemens C55 and a DCA-510 Usb Cable; which identified in my ubuntu 6.06 as

> 
~$ lsusb
...........
Bus 004 Device 002: ID 6547:0232
...........


> 
~$ dmesg
...........
[17184116.524000] usb 4-1: new full speed USB device using uhci_hcd and address 2
...........


I will use that with gnokii, and I can't find it connected to any /dev/tty*

Please help me to make it useful on my ubuntu.

Thanks.

---

### Post by diskotek on 2007-04-21
are there any software like kmobiletools for Gnome?

---

### Post by brunomiguel on 2007-04-21
Anyone managed to do it on Feisty??

---

### Post by PhilJ on 2007-05-26
Just plugged my wife's new Nokia 6288 in using Fiesty and it showed up as a removeable drive.All I did was choose data transfer mode from the phone menu

Philj

---

### Post by Arjunanda on 2007-05-26
does not happen with Nokia N70

---

### Post by celticbhoy on 2007-05-29
Just tried with theN80 and it allows me to access the memory card as though it is a card reader. All I need is instructions on how to access the phone memory.

---

### Post by ziofil on 2007-07-14
> **brunomiguel said:**
> Anyone managed to do it on Feisty??

It worked for me om feisty, I followed the steps, except fot the cvs part, there are some spaces between the : and the url/login name that shouldnt be there, and I used automake 1.9
Now i can see my N70 plugged on the usb port.
Is there any program with some useful graphic interface that can take advantage from this guide?
I'd like to save all my contacts, I have 1500+, if I loose them in some way... I don't want to imagine!
any precious help? thanks a lot

---

### Post by Arjunanda on 2007-07-23
I have not heard any news about any GUI tools utilizing the OpenOBEX protocol. This is what is needed: inclusion of OBEX transport in KMobileTools and other similar tools. If you find some info, please post here. I am also eaerly waiting that the will be solved.

---

### Post by Sandsound on 2007-07-25
> **Arjunanda said:**
> I have not heard any news about any GUI tools utilizing the OpenOBEX protocol. This is what is needed: inclusion of OBEX transport in KMobileTools and other similar tools. If you find some info, please post here. I am also eaerly waiting that the will be solved.

Just found this one : [http://www.ohloh.net/projects/6729](http://www.ohloh.net/projects/6729)

Its a straightforward gui and it works fine with my Ericsson z520i.
And I was SO proud that I finaly had ObexFtp working in a terminal... well at least I learned a few things on the way :-)

---

### Post by Arjunanda on 2007-08-16
Thanks for this tip: I have downloaded it and trying to get it working. However, I am stuck in Configuration dialog/OBEX FTP settings/Device information/Transport
Wehere I select "USB". What should I fill in the "value" field? I suppose I should fill in the USB port number. So I have tried all values between 0 and 6, and also combinations such as "0-6" etc. What did you fill in?

---

### Post by Arjunanda on 2007-08-16
> 1. Cannot connect to the device
*******************************
If you are experiencing connection errors when trying to access the device, in most of the times the reason is that you don't have the needed permission to access it. This issue can be solved by:
a) adding your user to the group used by the device (ex: uucp); or
b) executing this application as root. This is the easy solution, but avoid it
as much as you can. We DO NOT recommend this workaround due to security reasons.


Oh yes finally!

---

### Post by mpgarate on 2007-08-16
think this will work with samsung t509? windows explorer would not open it.. had to use 3rd party software (back before ubuntu....)

---

### Post by Sandsound on 2007-08-16
> **Arjunanda said:**
> What should I fill in the "value" field? I suppose I should fill in the USB port number. So I have tried all values between 0 and 6, and also combinations such as "0-6" etc. What did you fill in?

Mine is 0 but looks like your problem is with permissions ?
You should be able to see it if you run
$ obexftp -u

[QUOTE=mpgarate]think this will work with samsung t509?[/QUOTE]

Give it a try, it's easy to install and configure.

---

### Post by mpgarate on 2007-08-16
no luck, didnt show up in the usb test

---

### Post by Sandsound on 2007-08-16
> **mpgarate said:**
> no luck, didnt show up in the usb test

I have made a wery simple how-to, for useing obexftp from the terminal (just for my own personal use), I'm no expert, but maybe it can be of some help to others.

******************************

**Howto transfer photos from your Ericsson z520i via USB datacable.**

Install Wammu and Obexftp from repros.

Open Wammu and in the menu you select "wammu/search phone", this will give you the id you'll need to connect, just look for /dev/****, mine was /dev/ttyACM0.

In a terminal write the folowing to list all folders :

$ obexftp  -t /dev/ttyACM0  -l /

This should give you something like this :

Connecting...done
Receiving "/"... Sending ""... done
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE folder-listing SYSTEM "obex-folder-listing.dtd">
<!--
 XML Coder, Nov 14 2005, 19:22:32, (C) 2001 Sony Ericsson Mobile Communications AB 
-->
<folder-listing version="1.0"><folder name="Billeder"/>
<folder name="Lyde"/>
<folder name="Temaer"/>
<folder name="Videoer"/>
<folder name="Anden"/>
</folder-listing>
done
Disconnecting...done

List all pictures in the folder "Billeder" :

$ obexftp  -t /dev/ttyACM0  -l /Billeder

Transfer the picture jul2006.jpg from the folder /Billeder to your home-dir :

$ obexftp  -t /dev/ttyACM0  -c /Billeder -g jul2006.jpg

**ObexFtp Frontend**

[IMG]http://www.sandgreen.dk/img/obexftp.jpg[/IMG]

If you want a nice gui to ObexFtp you can download it here :
[http://www.ohloh.net/projects/6729](http://www.ohloh.net/projects/6729)

It's simple to use, even I can figure it out :-)

Just extract the file to a folder in your home-dir.

Rightclick the Run.sh file and look under permissions, make shure the "Allow executing file as a program" is checked.

Run the file Run.sh by doubleclicking it.

Fill out the ObexFtp path, mine is /usr/bin/obexftp

Select USB transport

Fill out the interface value, mine is 0 but you can get yours by typing the folowing in a terminal:
$ obexftp -u

When you have filled out these three fields, you click "OK" and you should ready.
Click the magnifying glas icon to retreve the folders, and you have access to all pictures, sounds and what else you might have in your memory.

Notes :
Remember to connect your phone to the USB cable ;-)
I'm using Wammu version 0.17-1 and ObexFtp 0.19-7

---

### Post by CyberSDF on 2007-08-16
Unfortunately, nothing work for SAMSUNG SGH E900 and SGH E880 :(

```
$ obex_test -u
Using USB transport, querying available interfaces
Use 'obex_test -u interface_number' to run interactive OBEX test client
```
```
$ sudo obexftp -u
Found 0 USB OBEX interfaces
Use '-u interface_number' to connect
Nothing to do. Use --help for help. 
```
I've try with feisty packages of obex* and last snapshot :cry:

---

### Post by Sandsound on 2007-08-16
> **CyberSDF said:**
> Unfortunately, nothing work for SAMSUNG SGH E900 and SGH E880 :( 

Can you access you phone using Wammu ?

btw. if you use "obex_test -u" you have to include your interface number, just running the test without it wont do anything.


EDIT: Did a little googleing and found this :

```

Samsung E900 -- working

* If you want use the command:

    obexftp -b xxxx -l path You must put the path in a -c option, however only folders are listed, not plain files (except files uploaded via obexftp).

Examples: obexftp -b 00:16:DB:E1:60:C5 -B 9 -c "DownLoaded Images" -l

* If you want to use the command:

    obexftp -b XXXXX -p file The cellphone will choose automaticly the location of the destination file so you can't provide dest path.

* If you want to use the command:

    obexftp - b XXXX -c path -g file This only works for files that are explicitly marked as "Visible for Bluetooth". A marked file will be shown with a blue bluetooth icon.

```

So your phone should be supported by ObexFtp at least.

---

### Post by DemoN3x on 2007-08-25
I tried several solutions for connecting various models of nokia phones and had difficulties with the ones using pop-port's.

However while googling I came across this: [http://news.softpedia.com/news/Transfer-Files-To-And-From-Your-Nokia-Phone-63116.shtml](http://news.softpedia.com/news/Transfer-Files-To-And-From-Your-Nokia-Phone-63116.shtml)

I followed the advice and got it working perfect.  There is just one thing I want to change.  I edited the permissions for myself but how do I enable it so that any user of the pc can connect to the device.

---

### Post by life2.0 on 2008-01-08
Hello Guys,

Lately I have been *unsuccessfully* trying to install Wammu (wammu_0.13-1_all.deb) on my Ubuntu 7.10. The package installer when run comes up with this error message:
Error: Dependency is not satisfiable: python-gammu

Could someone pls help me with this? Thanks in advance.

---

