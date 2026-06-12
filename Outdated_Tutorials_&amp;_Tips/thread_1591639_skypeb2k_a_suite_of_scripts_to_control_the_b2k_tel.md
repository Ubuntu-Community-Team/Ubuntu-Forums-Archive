---
title: "skypeb2k: a suite of scripts to control the b2k telbox and Skype."
date: 2010-10-09
forum: Outdated Tutorials &amp; Tips
---

### Post by brian_p on 2010-10-09
A b2k telbox is designed to allow a standard telephone handset to control VoIP software running on a computer. The Linux driver for the telbox is usbb2k_api and, in co-operation with other software, it can be the basis for building a customised system where calls can be made and received with Skype using a corded or cordless handset.

**Software required**.
[LIST]
[*]usbb2k-api-mod    (Provides usbb2k_api and api_connect.)
[*]netcat-openbsd (Provides netcat with the -U option.)
[*]empty-expect   (Provides empty.)
[*]alsa-utils     (Provides amixer and alsamixer.)
[*]python-skype   (Provides skype4py, a scripting interface with Skype.)
[*]pavucontrol    (Provides a sound mixer for PulseAudio. Optional.)
[/LIST]
The first package on the list can be downloaded from [[COLOR="Blue"]this ppa[/COLOR]]("https://launchpad.net/~alatariel/+archive/ppa/+packages") and installed with

```
dpkg -i usbb2k-api-mod_2.8-1_i386.deb
```

The remaining packages should be available via your package manager, which can also be used to remove them from the system. The usbb2k-api-mod package has a bug in one of its scripts and doesn't uninstall cleanly. It is necessary to do:

```
mkdir /etc/rc.d
```

before purging the package and, afterwards

```
rmdir  /etc/rc.d
```

Some background to the telbox driver and the genesis of skypeb2k is [[COLOR="Blue"]here.[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1573326")

**The skypeb2k script.**

Installing usbb2k-api-mod starts usbb2k_api running in daemon mode, sending commands to the telbox and listening to what it outputs. It also creates /tmp/usbb2k.sock, a unix socket. The socket is the gateway to the daemon and netcat connects to it to stream data to and from it.  Two named pipes (FIFOs), telbox.in and telbox.out, are created by empty to give access to netcat. Control of the telbox involves Skype and skypeb2k sending commands to it via telbox.in and skypeb2k reading its output via telbox.out.

When Skype detects an incoming call it requests the telbox (through skype4py and telbox.in) to cause the phone to ring. It also tells skypeb2k about the event by placing the file RINGING in /tmp.

Listening on telbox.out skypeb2k can detect when the handset is switched on or off and send commands to Skype (again using skype4py) to answer or end a call. Key presses appearing at telbox.out are recorded by skypeb2k to form a phone number to send to Skype and, using telbox.in, skypeb2k can instruct the telbox to switch to PSTN or USB mode.

```
#!/bin/bash

# Connect to the socket provided by usbb2ki_api in /tmp and create named
# pipes to communicate with the telbox.
DRIVER=$(pgrep usbb2k_api)
if [ -z "$DRIVER" ] ; then
   echo "Check telbox driver is running."
   exit
else
   empty -f -p /tmp/telbox.pid -i /tmp/telbox.in -o /tmp/telbox.out nc -U /tmp/usbb2k.sock
   PID1=$(cat /tmp/telbox.pid)
   sleep 1.0 ; fi

if [ ! -f /tmp/telbox.pid ] ; then
   echo "Telbox not connected to USB bus."
   exit ; fi

# Be on the lookout for an incoming call to Skype.
skypecall-detect > /dev/null 2>&1 &
PID2=$!

# Clear up when ctrl-C is used to exit the script.
trap "kill $PID1 $PID2 ; exit" exit SIGINT SIGTERM

# Location of resource configuration and contacts files.
RC=$HOME/.skypeb2k/telboxrc
CONTACTS=$HOME/.skypeb2k/contacts
F2="cut -d= -f2"

# Changes to settings in telboxrc require skypeb2k to be restarted for
# them to take effect.
MIX=$(grep ^mixer $RC | $F2)
PCM=$(grep ^pcm $RC | $F2)
MIC=$(grep ^mic $RC | $F2)
CARD=$(grep ^card $RC | $F2)
TONE=$(grep ^tone $RC | $F2)
CODE1=$(grep ^code1 $RC | $F2)
CODE2=$(grep ^code2 $RC | $F2)
SC=skypecall-contact

$MIX $CARD set PCM,0 $PCM
$MIX $CARD set PCM,1 $PCM
$MIX $CARD set Mic,0 $MIC
$MIX $CARD set Mic,1 $MIC

if [ -n "$TONE" ] ; then
   echo "TONE $TONE" > /tmp/telbox.in ; fi

# Start keeping track of events appearing at telbox.out.
n=0

# Monitor output from the telbox to get handset status and the keys
# pressed. Keep an eye on the health of the telbox.
while read B2KOUT < /tmp/telbox.out ; do
        HSET=$(echo "$B2KOUT" | cut -s -dH -f2)
        KEY=$(echo "$B2KOUT" | cut -s -dY -f2 | sed 's/^...//')
        USB1=$(echo "$B2KOUT" | grep REMOVED)
        USB2=$(echo "$B2KOUT" | grep SHUTDOWN)

if [ -n "$USB1" ] ; then
   echo "The telbox has been disconnected from the USB bus." ; exit
elif [ -n "$USB2" ] ; then
   echo "The usbb2k_api daemon has been shut down." ; exit
fi

# Continue keeping track of the events seen at telbox.out.
n=$((n+1))

# Leaving non-empty variables lying around leads to trouble.
unsetvars ()
{
for var in A B C D E F G H I J K L M N O P Q R S X Z i m s NAME
do
    unset $var
done
}

# * in a PSTN number. 0 as first digit after +. No code1 or code2 in
# telboxrc.
failedcall ()
{
echo "DIALTONE ON" > /tmp/telbox.in
n=99
}

# Send a contact name to Skype when the # key is pressed. The call is
# terminated if $NAME contains a * or a # or it matches a blank line in
# $HOME/.skypeb2k/contacts.
sendout1 ()
{
if [ -n "$NAME" ] ; then
   skypecall-contact $NAME > /dev/null 2>&1
   n=0 ; i=INCALL
else failedcall ; fi
}

# Calls to the PSTN. No *s allowed.
sendout2 ()
{
if [ -n "$Y" ] ; then failedcall ; else
case $Z in
   [01][1-9][0-9]*) if [ -n "$CODE1" ] ; then
                       Z=$(echo $Z | sed 's/^[01]//')
                       $SC "$CODE1$Z" > /dev/null 2>&1
                       n=0 ; i=INCALL
                    else failedcall ; fi
                        ;;
       [1-9][0-9]*) if [ -n "$CODE2" ] ; then
                       $SC "$CODE2$Z" > /dev/null 2>&1
                       n=0 ; i=INCALL
                    else failedcall ; fi
                        ;;
     00[1-9][0-9]*) $SC "$Z" > /dev/null 2>&1
                    n=0 ; i=INCALL
                        ;;
                 *) failedcall
                        ;;
esac
fi
}

# Switch to USB mode or record the key pressed.
switch ()
{
if [[ "$KEY" = [0-9bc] && "$s" = STARS ]] ; then
   echo "DIALTONE OFF" > /tmp/telbox.in
   A=$KEY ; dialplan
elif [ "$KEY" = b ] ; then
   echo "SWITCH U" > /tmp/telbox.in
   echo "PICKUP_PSTN" > /tmp/telbox.in
   echo "DIALTONE ON" > /tmp/telbox.in
   n=1 ; s=STARS
fi
}

# Put key presses together to get a contact name or phone number to send
# to Skype.
dialplan ()
{
if [ "$s" = STARS ] ; then
case $A$B$C$D$E$F$G$H$I$J$K$L$M$N$O$P$Q$R$R in
         *) X=$A$B$C$D$E$F$G$H$I$J$K$L$M$N$O$P$Q$R$S
            Y=$(echo $X | tr -d [0-9c])
            m=$(echo -n $X | wc -c)
            Z=$(echo $X | tr -d c)
                        ;;
esac

if [ "$KEY" = c ] ; then
case $m in
            2) NAME=$(grep "^$A " $CONTACTS | cut -d " " -f2-)
               sendout1
                        ;;
            3) NAME=$(grep "^$A$B " $CONTACTS | cut -d " " -f2-)
               sendout1
                        ;;
 [4-9]|1[0-8]) sendout2
                        ;;
           19) failedcall
                        ;;
esac
fi
fi
}

# Record keys pressed. Otherwise do DTMF.
if [ "$i" != INCALL ] ; then
case $n in
         2) switch
                ;;
         3) B=$KEY
            dialplan
                ;;
         4) C=$KEY
            dialplan
                ;;
         5) D=$KEY
            dialplan
                ;;
         6) E=$KEY
            dialplan
                ;;
         7) F=$KEY
            dialplan
                ;;
         8) G=$KEY
            dialplan
                ;;
         9) H=$KEY
            dialplan
                ;;
        10) I=$KEY
            dialplan
                ;;
        11) J=$KEY
            dialplan
                ;;
        12) K=$KEY
            dialplan
                ;;
        13) L=$KEY
            dialplan
                ;;
        14) M=$KEY
            dialplan
                ;;
        15) N=$KEY
            dialplan
                ;;
        16) O=$KEY
            dialplan
                ;;
        17) P=$KEY
            dialplan
                ;;
        18) Q=$KEY
            dialplan
                ;;
        19) R=$KEY
            dialplan
                ;;
        20) S=$KEY
            dialplan
                ;;
esac
fi

# Answer, end or abort a call.
case $HSET in
   "ANDSET ON") if [ -f /tmp/RINGING ] ; then
                   echo "PICKUP_PSTN" > /tmp/telbox.in
                   skypecall-answer -a > /dev/null 2>&1
                   rm /tmp/RINGING > /dev/null 2>&1
                   i=INCALL ; fi
                        ;;
  "ANDSET OFF") if [ "$i" = INCALL ] ; then
                   skypecall-answer -e > /dev/null 2>&1
                   echo "HANGUP_PSTN" > /tmp/telbox.in
                   echo "SWITCH P" > /tmp/telbox.in
                   unsetvars ; n=0
                elif [ "$s" = STARS ] ; then
                   echo "HANGUP_PSTN" > /tmp/telbox.in
                   echo "SWITCH P" > /tmp/telbox.in
                   echo "DIALTONE OFF" > /tmp/telbox.in
                   unsetvars ; n=0
                else n=0
                fi
                        ;;
esac
done
```

Three scripts to use with Skype and skype4py are also available. They give skypeb2k access to Skype to start and end a call and to detect incoming calls. Rather than increase the length of this article I've put them in the attached tarball, skypeb2k-1.0.tar.gz. The comments in them should make it clear what they do. Apart from documentation the contents of the .tar.gz are:

[LIST]
[*]skypeb2k
[*]skypecall-detect   (Actions taken when a call comes in.)
[*]skypecall-contact  (Request Skype to make a call.)
[*]skypecall-answer   (Instruct Skype to answer or end a call.)
[*]skypeb2k-contacts  (Import a list of contacts from Skype.)
[*]tonetest           (Test a tone string.)
[/LIST]

**Using audio on the telbox.**

To adjust the gains of the handset's earpiece and mouthpiece you'll need the card number or card ID of the telbox's sound card. So

```
cat /proc/asound/cards
```

I get:

```
 0 [V8237          ]: VIA8237 - VIA 8237
                      VIA 8237 with ALC850 at 0xd800, irq 22
 1 [Headset        ]: USB-Audio - USB Headset
                      GENERIC USB Headset at usb-0000:00:10.4-1.3, full speed
 2 [default        ]: USB-Audio - VOIP USB Phone
                      Yealink Network Technology Ltd. VOIP USB Phone at usb-0000:00:10.2-1
 3 [U0x4710x311    ]: USB-Audio - USB Device 0x471:0x311
                      USB Device 0x471:0x311 at usb-0000:00:10.3-2, full speed
```

The telbox is card 2 and has an ID of "default".

It is better to use the card ID rather than the card number because the latter can change if devices are unattached and then reattached to the USB bus in a different order. There is also the matter of which is seen first when the computer is booted.

```
alsamixer -c default -V all
```

may be useful to view the state of card's channels.

**The contacts file.**

Make the directory .skypeb2k in your home directory and create a
contacts file in it:

```
mkdir $HOME/.skypeb2k

touch $HOME/.skypeb2k/contacts
```

You can use your usual text editor to edit the contents of contacts. Each entry must be on a separate line and begin with a number in the range 0-99 followed by a single space. As an example:

```
0 echo123
1 skypeb2khq
5 +3491123456
7 0044201234567
15 7909360
```

With an existing Skype contacts list you'll probably want to use skypeb2k-contacts.

**The resource configuration file.**

First

```
touch $HOME/.skypeb2k/telboxrc
```

then make entries in the form option=value with nothing else on the same line. Here is mine:

```
# Program to adjust the handest gains when skypeb2k starts.
mixer=amixer -q -c

# pcm and mic are the handset gains. Alter to suit.
pcm=75% unmute
mic=78% unmute

# Number or ID of the sound card.
card=default

# Ringing cadence. Test with tonetest.
tone=TONE AaAx

# May be empty or commented out.
code1=+44
code2=+44161
```

tone is a usbb2k_api feature and may be empty. It alters the ringing cadence of the phone. From the source code:

> ringing_tone[] contains, eg, DbDt, where letter A/a=0.1s, Y/y=2.5s,
UPPER=ring, lower=no ring Z/z is 'stop here', ie, only do one ring loop
Try AaAaAx :-)
The default is DbDt.

**Audio between Skype and the telbox.**

Without PulseAudio choose one of the VOIP USB Phone offerings from Options/Sound Devices in skype. default:CARD=default works for me. Older versions of Skype may have something like hw:default,0 or plughw:default,0 as choices. Untick the option to have Skype manage the mixer settings.

With PulseAudio install and run pavucontrol. While making a Skype call set the input and output from the Playback and Recording tabs to VOIP Phone Analog Mono.

Audio between Skype and the telbox can be tested with tonetest.

**Installation and preparation of the software.**

Install netcat-openbsd, empty-expect and python-skype. Extract the scripts from skypeb2k-1.0.tar.gz, put them in /usr/local/bin and give them appropriate ownership and permissions:

```
chown root.staff <script_name>

chmod  755 <script_name>
```

Install usbb2k-api-mod and check usbb2k_api is running. The yealink module may interact with usbb2k_api in an irritating way so remove it if it's loaded:

```
rmmod -v yealink
```

Its as well not ever to have it loaded; use your editor to add the line

```
blacklist yealink
```

to the end of blacklist or blacklist.conf in /etc/modprobe.d/.

The commands above have to be carried out as root or using sudo.

**Making phone calls**.

Start skypeb2k in a terminal and background it with:

```
skypeb2k &
```

Skype will also start and ask if you want to allow another program to connect with it. Alternatively, Skype can started first.

Switch to USB mode with a press of the * key and dial a number. Dialtone disappears on pressing the first digit of the number. Send the number to Skype with the # key. If for some reason skypeb2k declines to forward the call to Skype dialtone is returned and the telbox is left in USB mode. Switch the handset off and on to redial.

Skype will only handle PSTN numbers in international format, for example, +44151xxxxxxx; but it will be very happy if you dial 0044151xxxxxxx. It will replace the 00 with a +.

If you are in the habit of phoning a particular country or area of a country skypeb2k can handle that with code1 and code2 in telboxrc. code1 is intended for countries which have a trunk (long-distance) code of 0 or 1 or which have numbers beginning with a zero which isn't used in international dialling. Dialling the number with a leading 0 or 1 will get either one replaced by + and the country code. For example:

```
code1=+44: 02012345678 becomes +442012345678  (UK)
code1=+1: 18014245301 becomes +18014245301    (Canada, USA)
```

This will probably cause calls to numbers in Italy to fail because the leading 0 is not a trunk code and should not be removed. A way round the problem is to have code1 as +390 instead of +39 so that the 0 gets re-inserted.

The intention of code2 is to process area codes or numbers in countries which do not use trunk codes. For example:

```
code2=+441772 : 885660 becomes +441772885660  (Preston, UK)
code2=+8621: 22817664 becomes +862122817664   (Shanghai, China)
code2=+34: 9131112222 becomes +349131112222   (Spain)
```

I expect the two codes don't cater for everyone but the script can be adjusted if needs be.

There are four circumstances in which skypeb2k will not forward a call to Skype but give dialtone instead:

[LIST]
[*]The request corresponds to a blank line in the contacts file or you try to match * or # with a contact name.

[*]The digit after + or 00 is 0.

[*]A PSTN number contains a *. Apart from making the number invalid it is likely to be translated by Skype to the digit 2, which would add an extra dimension to misdialling!

[*]A call is made using code1 or code2 but there is no entry in telboxrc.
[/LIST]

---

