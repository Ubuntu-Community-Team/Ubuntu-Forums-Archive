---
title: "Exploring the b2k telbox driver"
date: 2010-09-12
forum: Outdated Tutorials &amp; Tips
---

### Post by brian_p on 2010-09-12
The b2k telbox is a USB device which is marketed as allowing an ordinary telephone handset to make and receive phone calls via a VoIP program running on a computer. The program which most people have in mind to use is Skype.

The device also has the ability to connect to the public telephone system (the PSTN) so that phone calls can be made independently of the computer.

**Why you might find this HOWTO useful**

[LIST]
[*]You have a telbox and are curious to discover how it is controlled.

[*]The software you are using with the telbox and driver isn't behaving itself and you wish to find out if the telbox/driver is the cause of the problem.

[*]You are intending to write a program which links the telbox with your VoIP application.
[/LIST]

**The Linux driver**

Fortunately there is a driver, usbb2k-api, which runs as a daemon listening for commands going in and coming out of the telbox. It is maintained by Marcos Diez (marcos_at_unitron.com.br) and a Debian binary may be downloaded from

[https://launchpad.net/~alatariel/+archive/ppa/+packages](https://launchpad.net/~alatariel/+archive/ppa/+packages).

While you are there get the source package too - it contains some very useful information.

Before you install the binary on your system let's try to head off a little bit of possible trouble. Use your favourite editor to add the line

```
blacklist yealink
```

to the end of the file blacklist or blacklist.conf in /etc/modprobe.d/. Also remove any running yealink module with

```
rmmod -v yealink
```
The editing and module removal have to be done as root or using sudo.

Having yealink and usbb2k-api running at the same time is not necessarily disastrous but it can lead to an annoying stream of 1s being echoed to the console when processes are restarted. Leave doing it 'til later if you wish and see how it goes. The telbox Power and Line LEDs are both lit when the computer boots. Loading usbb2k-api should not change this.

Proceed with installing your chosen flavour of binary:

```
sudo dpkg -i usbb2k-api-mod_2.8-1_i386.deb

```

Don't try uninstalling the package with the usual apt-get purge method alone as there is a bug in a removal script. You can work round it with:

```
mkdir /etc/rc.d
apt-get purge usbb2k-api-mod
rmdir /etc/rc.d
```

One way of checking the daemon is in operation is to

```
ls -l /tmp/usbb2k.sock
```

This socket file is created by usbb2k-api and is used to send commands to the daemon and receive data from it. The socket is accessible to a normal user. Should you want to stop the daemon (which removes the socket) then

```
sudo /etc/init.d/usbb2k-api-mod stop
```

is the command. Substituting "start" for "stop" does what you would expect it to.

**Other software to get**

[LIST]
[*]alsa-utils
[*]netcat-openbsd
[*]empty-expect
[/LIST]

These are all obtainable using your package manager. I use

```
apt-get install <package_name>
```

The second and third packages are not strictly required but they provide alternative ways of manipulating the driver which may interest you.

**Control commands for the telbox**

Extract the files from usbb2k-api-mod_2.8.orig.tar.gz as you would do normally. I use Midnight Commander (mc) but

```
tar zvxf usbb2k-api-mod_2.8.orig.tar.gz

```
is as good as anything.

You want two files: fifoApi.h and cmdServer.c. Both are in the src directory of the unpacked archive. The first file has a list of the commands understood by the telbox and processed by the usbb2k-api driver. The second has a short description of the TONE command.

The input commands to the telbox are:
```

        SWITCH U
        SWITCH P
        RING
        TONE
        DIALTONE OFF
        DIALTONE ON
        PICKUP_PSTN
        HANGUP_PSTN

```
The telbox can output:
```

        HANDSET OFF
        HANDSET ON
        KEY 0n          (where n is an integer in the range 0-9)
        PSTN_RING
        USB NOT FOUND
        USB DEVICE FOUND
        USB DEVICE INIT ERROR
        DEVICE REMOVED
        DAEMON SHUTDOWN
        USBB2K          (plus information about your telbox)

```
The driver package also comes with a program, api_connect, to connect to the socket file.

This shows a telbox being found on USB bus 5 and registered as device 85:

```
brian@desktop:~$ api_connect /tmp/usbb2k.sock
Trying to connect...
Connected.
SEND> RECV> USB DEVICE FOUND 5/85
RECV> HANDSET OFF

```
Lifting the handset off its rest, pressing a few buttons, replacing the handset and disconnecting the telbox from the USB bus produces:

```
RECV> HANDSET ON
RECV> KEY  01
RECV> KEY  09
RECV> KEY  05
RECV> KEY  0b
RECV> KEY  0c
RECV> HANDSET OFF
RECV> DEVICE REMOVED
```

You now need to get out of api_connect with ctrl-C and restart it after reconnecting the telbox. If you start api_connect without connecting the telbox you'll see:

```
brian@desktop:~$ api_connect /tmp/usbb2k.sock
Trying to connect...
Connected.
SEND> RECV> USB NOT FOUND

```
Hopefully you will never see USB DEVICE INIT ERROR!

Now for instructing the telbox to do something:

```
brian@desktop:~$ api_connect /tmp/usbb2k.sock
Trying to connect...
Connected.
SEND> RECV> USB DEVICE FOUND 5/92
RECV> HANDSET OFF
SWITCH U
SEND> RING 1
SEND> RECV> HANDSET ON
DIALTONE ON
SEND> DIALTONE OFF
SEND> RECV> HANDSET OFF
RING 2
SEND> RING 0
SEND> SWITCH P
SEND>
```

I cannot distinguish between RING 1 and RING 2, and neither can Marcos Diez! But the TONE command is available. Nothing fancy, you understand, only the ringing cadence can be altered.

```
brian@desktop:~$ api_connect /tmp/usbb2k.sock
Trying to connect...
Connected.
SEND> RECV> USB DEVICE FOUND 5/92
RECV> HANDSET OFF
SWITCH U
SEND> TONE AxAt
SEND> RING 1
SEND> RING 0
SEND> SWITCH P
SEND>
```

**Testing audio**

You will need a device notation to use with ALSA. One way is to first do

```
cat /proc/asound/cards
```

I get

```
 0 [V8237          ]: VIA8237 - VIA 8237
                      VIA 8237 with ALC850 at 0xd800, irq 22
 1 [Headset        ]: USB-Audio - USB Headset
                      GENERIC USB Headset at usb-0000:00:10.4-1.3, full speed
 2 [default        ]: USB-Audio - VOIP USB Phone
                      Yealink Network Technology Ltd. VOIP USB Phone            at usb-0000:00:10.2-1
 3 [U0x4710x311    ]: USB-Audio - USB Device 0x471:0x311
                      USB Device 0x471:0x311 at usb-0000:00:10.3-2, full speed
```

The telbox is card 2 and identifies itself as "default". I don't know why it gets this ID but I don't think it means card 2 is the default for the system.

Now for

```
aplay -l
```

The output is:

```

**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 3/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: default [VOIP USB Phone           ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

The card 2 line says the VOIP USB Phone is device 0 so for sound to get to the handset earpiece the ALSA device is either hw:default,0 or plughw:default,0. I'd use the card ID, default, rather than the card number because the latter can change if devices are unattached from and then reattached to the USB bus in a different order. There is also the matter of which is seen first when the computer is rebooted.

Volume adjustments are next:

```
alsamixer -c default -V all
```

Unmute the PCM channels with the "m" key if necessary and push all four gains up to 100%.

Now put the telbox in USB mode with SWITCH U and send sound to it:

```
cat /dev/urandom | aplay -D plughw:default,0
```

For something more exciting get a .wav file. There might be a few on your machine

```
locate '*.wav'
```

or use the internet. Then

```
aplay -D plughw:default,0 <your_wav_file>

```
Check the device to use for capturing sound with

```
arecord -l
```

Still with the telbox in USB mode run the command

```
arecord -D plughw:default,0 <testsoundin>

```
and speak or sing into the handset mouthpiece. Success will be indicated by the result of

```
aplay -D plughw:default,0 <testsoundin>
```

**Shedding the load**

Hopefully your telbox funtions as advertised and you didn't spend too much time playing with the TONE command! Have you got time to look at the result of

```
top
```

This is mine:

```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 3642 brian     20   0  1616  368  312 R 95.2  0.0   0:14.54 api_connect
```

The very high CPU usage makes api_connect an unsuitable candidate for monitoring a telbox over an extended period of time, such as a few months. An alternative is to use netcat:

```
nc -U /tmp/usbb2k.sock

```
All the previous experimentation can be carried out with this command. The CPU load is negligible.

Let's take a look at empty-expect. It can interact with netcat (which has access to usbb2k-api through /tmp/isbb2k.sock) by creating input and output named pipes (FIFOs).

Here's how:

```
empty -f -i /tmp/telbox.in -o /tmp/telbox.out nc -U /tmp/usbb2k.sock
```

In one terminal run

```
echo "SWITCH U" > /tmp/telbox.in
```

or echo any other telbox input command.

The telbox output can be seen in another terminal with

```
cat /tmp/telbox.out

```
**Where to from here?**

The only program I'm aware of which uses usbb2k-api is b2kskype. However, it does pull in a lot of dependencies which take a lot of storage space (80 MB or so on a minimal Debian system when I last looked). This is far too much for a project I have in mind where the total storage space available is about 180-200 MB.

Those FIFOs created by empty begin to look very attractive beause they could be accessed by a script. Basically. this is what I have done. The result will be submitted here (after some documentation polishing) in a week or so.

---

### Post by dmizer on 2010-09-22
Courtesy bump. Thank you for posting this.

---

### Post by Ripfox on 2010-10-01
I am currently successfully using kb2kskype and the api_mod described above happily with Pulse Audio. It took a whole night to track it all down and figure it out, but it works with my Tel-box and Skype on Ubuntu 10.04.

I am very interested in your project, good luck to you.

Rip

---

### Post by brian_p on 2010-10-22
> **Ripfox said:**
> I am currently successfully using kb2kskype and the api_mod described above happily with Pulse Audio. It took a whole night to track it all down and figure it out, but it works with my Tel-box and Skype on Ubuntu 10.04.

I am very interested in your project, good luck to you. 

Thank you for your encouragement, Rip. The result of my labours is now at

[http://ubuntuforums.org/showthread.php?p=9944695#post9944695](http://ubuntuforums.org/showthread.php?p=9944695#post9944695)

Not a GUI in sight I fear, but it suits me for the purposes I have in mind.

---

