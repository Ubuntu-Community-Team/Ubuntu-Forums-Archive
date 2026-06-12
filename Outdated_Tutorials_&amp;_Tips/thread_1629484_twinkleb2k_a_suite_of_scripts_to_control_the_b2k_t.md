---
title: "twinkleb2k: a suite of scripts to control the b2k telbox and Twinkle."
date: 2010-11-23
forum: Outdated Tutorials &amp; Tips
---

### Post by brian_p on 2010-11-23
Take a b2k telbox and the right kind of VoIP software and the potential exists to use a standard telephone handset to make and receive calls without the inconvenience of having to click on anything or be in frontof a computer. Twinkle is the right kind of software: its designer, Michel de Boer, provided a command line interface and scripting support to his program, giving it the ability to communicate with the telbox.

But even that is not sufficient without a driver for the telbox which can accept commands from and output commands to other software such as Twinkle and twinkleb2k. Fortunately there is usbb2k_api, which provides a very nice foundation for devising a system which facilitates communication between Twinkle and the telbox using twinkleb2k and Twinkle's scripting ability.


**Software required.**

[LIST]
[*]usbb2k-api-mod (Provides usbb2k_api)
[*]  netcat-openbsd (Provides netcat with the -U option)
[*]  empty-expect   (Provides empty)
[*]  alsa-utils     (Provides amixer, aplay and alsamixer)
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

Some background to the telbox driver and the genesis of twinkle2k is [[COLOR="Blue"]here.[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1573326")

**The twinkleb2k script.**

Installing usbb2k-api-mod starts usbb2k_api running in daemon mode, sending commands to the telbox and listening to what it outputs. It also creates /tmp/usbb2k.sock, a unix socket. The socket is the gateway to the daemon and netcat connects to it to stream data to and from it.  Two named pipes (FIFOs), telbox.in and telbox.out, are created by empty to give access to netcat. Control of the telbox involves Twinkle and twinkleb2k sending commands to it via telbox.in and twinkleb2k reading its output via telbox.out.

When Twinkle detects an incoming call it requests the telbox (through telbox.in) to cause the phone to ring. It also tells twinkleb2k about the event by placing the file RINGING in /tmp.

Listening on telbox.out twinkleb2k can detect when the handset is switched on or off and send commands to Twinkle to answer or end a call. Key presses appearing at telbox.out are recorded by twinkleb2k to form a phone number to send to Twinkle and, using telbox.in, twinkleb2k can instruct the telbox to switch to PSTN or USB mode.

```
#!/bin/bash

# Connect to the socket provided by usbb2k_api in /tmp and create named
# pipes to communicate with the telbox. Check usbb2k_api is running and
# telbox is connected.
DRIVER=$(pgrep usbb2k_api)
if [ -z "$DRIVER" ] ; then
   echo "Check if telbox driver is running."
   exit
else
   empty -f -p /tmp/telbox.pid -i /tmp/telbox.in -o /tmp/telbox.out nc -U /tmp/usbb2k.sock
   PID1=$(cat /tmp/telbox.pid)
   sleep 1.0 ; fi

if [ ! -f /tmp/telbox.pid ] ; then
   echo "Telbox not connected to USB bus."
   exit ; fi

# Location of resource configuration and contacts files.
RC=$HOME/.twinkleb2k/telboxrc
CONTACTS=$HOME/.twinkleb2k/contacts
F2="cut -d= -f2"

# Obtain telboxrc settings. Changes require twinkleb2k to be restarted
# for them to take effect.
MIX=$(grep ^mixer $RC | $F2)
PCM=$(grep ^pcm $RC | $F2)
MIC=$(grep ^mic $RC | $F2)
CARD=$(grep ^card $RC | $F2)
PLAY=$(grep ^play $RC | $F2)
WAV=$(grep ^ringwav $RC | $F2)
DEVICE=$(grep ^device $RC | $F2)
USECODES=$(grep ^usecodes $RC | $F2)
CODE1=$(grep ^code1 $RC | $F2)
CODE2=$(grep ^code2 $RC | $F2)
TONE=$(grep ^tone $RC | $F2)

# Set mixer controls.
$MIX $CARD set PCM,0 $PCM
$MIX $CARD set PCM,1 $PCM
$MIX $CARD set Mic,0 $MIC
$MIX $CARD set Mic,1 $MIC

# Inform the telbox what tone to use for an incoming call.
if [ -n "$TONE" ] ; then
   echo "TONE $TONE" > /tmp/telbox.in ; fi

# Clear up when ctrl-C is used to exit the script.
trap "kill $PID1 ; exit" exit SIGINT SIGTERM

# Start keeping track of events appearing at telbox.out.
n=0

# Monitor output from the telbox to get handset status and keys pressed.
# Keep an eye on the health of the USB connection
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
for var in A B C D E F G H I J K L M N O P Q R X Y Z a i m s NAME PROFILE
do
    unset $var
done
}

# Blank line in contacts. No setting for usecodes. usecodes=y and code1
# in telboxrc empty. 0 after + or 00 in a PSTN number.
failedcall ()
{
echo "DIALTONE ON" > /tmp/telbox.in
n=99
}

# Send an entry in $HOME/.twinkleb2k/contacts to Twinkle when the # key
# is pressed. Announce the call is taking place by playing a sound file.
sendout1 ()
{
if [ -n "$NAME" ] ; then
   if [ -n "$WAV" ] ; then
      $PLAY $DEVICE $WAV  > /dev/null 2>&1 ; fi
      twinkle --cmd "call $NAME" ; n=0 ; i=INCALL
else failedcall ; fi
}

# Send a phone number to a SIP provider. Indicate this by playing a
# sound file. Either send the number as dialled or process it beforehand
# to remove a * at the end or prepend codes.
sendout2 ()
{
if [ -n "$WAV" ] ; then
   $PLAY $DEVICE $WAV  > /dev/null 2>&1 ; fi

case $USECODES in
   n) twinkle --call "$Z"
      n=0 ; i=INCALL
                ;;
   y) case $Z in
         [01][1-9]*) if [ -n "$CODE1" ] ; then
                        Z=$(echo $Z | sed 's/^[01]//')
                        twinkle --call "$CODE1$Z"
                        n=0 ; i=INCALL
                     else failedcall ; fi
                                ;;
          [1-9]*[b]) Z=$(echo $Z | sed 's/\(.*\)./\1/')
                     twinkle --call "$Z"
                     n=0 ; i=INCALL ; Y=bc
                                ;;
             [1-9]*) if [ -n "$CODE2" ] ; then
                        twinkle --call "$CODE2$Z"
                        n=0 ; i=INCALL
                     else twinkle --call "$Z"
                          n=0 ; i=INCALL ; Y=bc ; fi
                                ;;
           00[1-9]*) twinkle --call "$Z"
                     n=0 ; i=INCALL
                                ;;
                  *) failedcall
                                ;;
      esac
                ;;
   *) failedcall
                ;;
esac
}

# *1, *2 etc to choose a SIP service and switch into USB mode. Stay in
# PSTN mode (with no dialtone) if PROFILE doesn't exist.
switch1 ()
{
if [[ "$KEY" = [0-9bc] && "$s" = STARS ]] ; then
   echo "DIALTONE OFF" > /tmp/telbox.in
   A=$KEY ; dialplan
elif [ "$KEY" = b ] ; then A=$KEY
fi
}

switch2 ()
{
if [[ "$KEY" = [0-9bc] && "$s" = STARS ]] ; then
   B=$KEY ; dialplan
else case "$A$KEY" in
        b[0-9]) PROFILE=$(grep "^profile$KEY" $RC | $F2)
                if [ -n "$PROFILE" ] ; then
                   twinkle --cmd "user $PROFILE"
                   echo "SWITCH U" > /tmp/telbox.in
                   echo "PICKUP_PSTN" > /tmp/telbox.in
                   echo "DIALTONE ON" > /tmp/telbox.in
                   n=1 ; s=STARS
                fi
                ;;
     esac
fi
}

# Put key presses together to get a SIP phone number. Get the number of
# digits in the number to determine whether to use the contacts file or
# send to the same network or the PSTN.
dialplan ()
{
if [ "$s" = STARS ] ; then
case $A$B$C$D$E$F$G$H$I$J$K$L$M$N$O$P$Q$R$S in
    *) X=$A$B$C$D$E$F$G$H$I$J$K$L$M$N$O$P$Q$R$S
       m=$(echo -n $X | wc -c)
       Z=$(echo $X | tr -d c)
                        ;;
esac

if [ "$KEY" = c ] ; then
case $m in
             2) NAME=$(grep "^$A " "$CONTACTS" | cut -d" " -f2-)
                a=$(echo "$NAME" | grep @)
                sendout1
                        ;;
             3) NAME=$(grep "^$A$B " "$CONTACTS" | cut -d" " -f2-)
                a=$(echo "$NAME" | grep @)
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

# Record keys pressed to get either an entry in contacts or a PSTN
# number.
#
# After a call is set up the keys are for DTMF purposes only. A same
# network call or a SIP-to-SIP call is handled by RFC 2833 DTMF. With
# PSTN calls the tones are sent within the audio stream.
if [ "$i" != INCALL ] ; then
   case $n in
         2) if [ "$HSET" != "ANDSET OFF" ] ; then switch1 ; fi
                ;;
         3) switch2
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
elif [[ "$i" = INCALL && "$KEY" && (-n $a || "$Y" = bc) ]] ; then
        if [ "$KEY" = b ] ; then KEY=$(echo $KEY | tr [b] [*]) ; fi
        if [ "$KEY" = c ] ; then KEY=$(echo $KEY | tr [c] [#]) ; fi
      twinkle --cmd "dtmf $KEY"
fi

# Answer, end or abort a call.
case $HSET in
   "ANDSET ON") if [ -f "/tmp/RINGING" ] ; then
                   echo "PICKUP_PSTN" > /tmp/telbox.in
                   twinkle --cmd answer
                   rm /tmp/RINGING > /dev/null 2>&1
                   i=INCALL ; fi
                        ;;
  "ANDSET OFF") if [ "$i" = INCALL ] ; then
                   twinkle --cmd bye
                   echo "SWITCH P" > /tmp/telbox.in
                   echo "HANGUP_PSTN" > /tmp/telbox.in
                   echo "DIALTONE OFF" > /tmp/telbox.in
                   unsetvars ; n=0
                elif [ "$s" = STARS ] ; then
                     echo "SWITCH P" > /tmp/telbox.in
                     echo "HANGUP_PSTN" > /tmp/telbox.in
                     echo "DIALTONE OFF" > /tmp/telbox.in
                     unsetvars ; n=0
                else n=0
                fi
                        ;;
esac
done

```

Four scripts to use with Twinkle are also provided. The comments in them should make it clear what they do. A fifth script, tonetest, is for testing a tone string. Rather than increase the length of this article I've put them in the attached tarball, twinkleb2k-1.0.tar.gz.

[LIST]
[*]twinkleb2k
[*]twinklecall-detect    (Action taken by Twinkle when a call comes in).
[*]twinklecall-infailed  (Action taken by Twinkle when an incoming call is not answered).
[*]twinklecall-outfailed (Action taken by Twinkle when an outgoing call fails).
[*]twinklecall-inended   (Action taken when the caller ends a call.)
[*]tonetest              (Test a tone string.)
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

may be useful. A way to test your audio setup is described in
tonetest.

**The contacts file**.

Make the directory .twinkleb2k in your home directory and create a contacts file in it:

```
mkdir $HOME/.twinkleb2k

touch $HOME/.twinkleb2k/contacts
```

You can use your usual text editor to edit the contents of contacts. Each entry must be on a separate line and begin with a digit in the range 0-99 followed by a single space. As an example:

```
  0 600@voxalot.com
  1 ben@example.com
  5 +3491xxxxxxx
  7 0044201234567
  15 7909360

```

With an existing Twinkle address book (not the KDE variety) you'll probably want to do:

```
cat $HOME/.twinkle/twinkle.ab | cut -d'|' -f4 | nl -v0 -ba -s' ' -w1 > contacts
```

**The resource configuration file.**

First

```
touch $HOME/.twinkleb2k/telboxrc
```

then make entries in the form option=value with nothing else on the same line. Here is mine:

```

  # Program to adjust the handest gains when twinkleb2k starts.
  mixer=amixer -q -c

  # pcm and mic are the handset gains. Alter to suit.
  pcm=75% unmute
  mic=78% cap

  # Number or ID of the sound card.
  card=default

  # Program to play a .wav file.
  play=aplay -D

  # Needed to play a .wav file when a call fails or when a call is made.
  device=plughw:default,0

  # Ringing cadence. Test with tonetest.
  tone=AaAx

  # Lets you know the call is going out. May be empty or commented out.
  ringwav=/usr/share/twinkle/ringtone.wav

  # Lets you know the call has failed. May be empty or commented out.
  failwav=

  # Lets you know when a number is engaged. May be empty or commented out.
  busywav=

  # Your SIP providers. Profiles are set up in Twinkle.
  profile1=voiptalk
  #profile2=sipgate

  # Send number as dialled or preprocess. 'y' or 'n'.
  usecodes=y

  # May be empty or commented out.
  code1=+44
  code2=+44161

```

tone is a usbb2k_api feature and may be empty. It alters the ringing cadence of the phone. From the source code:

>         ringing_tone[] contains, eg, DbDt, where letter A/a=0.1s, Y/y=2.5s,
        UPPER=ring, lower=no ring Z/z is 'stop here', ie, only do one ring loop
        Try AaAaAx :-)

The default is DbDt.

**Installation and preparation of the software.**

Install netcat-openbsd and empty-expect. Extract the scripts from twinkleb2k-1.0.tar.gz, put them in /usr/local/bin and give them appropriate ownership and permissions:

```
chown root.staff <script_name>
chmod  755 <script_name>

```
Edit/User profile/Scripts is the place to tell Twinkle about twinklecall-detect, twinklecall-inended, twinklecall-infailed and twinklecall-outfailed. In Edit/System settings/Audio have Speaker, Microphone and Ring tone use the ALSA device for the telbox sound card.

Install usbb2k-api-mod and check usbb2k_api is running. The yealink module may interact with usbb2k_api in an irritating way so remove it if it's loaded:

```
rmmod -v yealink

```
It's as well not ever to have it loaded; use your favourite editor to add the line

```
blacklist yealink
```

to the end of blacklist or blacklist.conf in /etc/modprobe.d/.

The commands in this section have to be carried out as root or using sudo.

**Making phone calls.**

In one terminal start twinkle with:

```
twinkle -c
```

and in another terminal start twinkleb2k and background it with:

```
twinkleb2k &
```

Choose a SIP provider to make a call with and switch to USB mode with *1 or *2 etc on the telephone keypad. You will get dialtone. Dial the number you want. The dialtone disappears on pressing the first digit of the number. Send the number to the provider with the # key. If for some reason the call fails or the number is engaged suitable .wav files can be played and the telbox is left in USB mode. Switch the handset off and on to redial.

**Calls to the PSTN.**

A SIP provider will always accept PSTN numbers in international format, for example, +44151xxxxxxx, but isn't going to be unhappy if you dial 0044151xxxxxxx. The 00 will be replaced with a +. This has nothing to do with the country you are phoning from but is a recognition that most telephone keypads do not allow a + to be entered.

If you phone a particular country or area of a country very often or exclusively twinkleb2k can handle that with code1 and code2 in telboxrc. code1 is intended for countries which have a trunk (long-distance) code of 0 or 1 or which have numbers beginning with a zero which isn't used in international dialling. Dialling the number with a leading 0 or 1 will get either one replaced by + and the country code. For example:

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
I expect the two codes don't cater for everyone but the script can be adjusted if needs be. In any case, the number can always be dialled with 00 and the country code.

**usecodes=y and usecodes=n.**

Having usecodes set to 'y' and both code1 and code2 not empty will get you the dialplan described above and the ability to phone a number in the contacts file. You can also ring a same network number but have to add a * at the end to distinguish it from a call to the PSTN. For example, 6601234*# to send to 6601234.

Maybe you do not want to jump through this little hoop and code2 is of no interest to you. Well, leave code2 empty or comment it out and simply do 6601234#.

Some providers will process what you dial in a similar way to code1. For example, VoipTalk and Sipgate do this for UK calls. You may prefer to have the provider, rather than twinkleb2k, deal with this aspect of your calls by putting usecodes=n in telboxrc. A same network call would then be dialled as 6601234# and PSTN calls are sent exactly as dialled.

**Dealing with DTMF.**

The handling of DTMF when a call is in progress depends on whether the call is to the PSTN or a SIP-to-SIP call. If it's a PSTN number the tone you hear when a key is pressed will be sent inband over the audio channel. I find this works well for me as presumably the SIP provider's PSTN gateway will forward the tone on and it gets recognised by the far end.

Perhaps I should mention I use the G.711 codec but some testing (not very extensive) gives similar good behaviour with the GSM, G.726-32 and speex-nb codecs. Whether this can be relied on is debatable as the advice usually given is to only use inband DTMF with the G.711 codec.

With SIP-to-SIP calls an out-of-band method is generally expected so twinkleb2k uses the RFC 2833 protocol to transmit the tone.

**Failed calls.**

A call arriving on a SIP provider's network may fail due a variety of reasons and the quality of the feedback given will vary from provider to provider. Some have quite detailed error messages (for example, "Your account does not have enough credit to make this call") while others just inform you to "dial again". The optional playing of a failwav file by twinkleb2k followed by the dailtone` is a catchall alert for all failure conditions except an engaged line. Apart from that one case you'll have to determine the cause of the failed call yourself.

There are four circumstances in which twinkleb2k will not forward a call to Twinkle at all but give dialtone instead:

[LIST]
[*]The request corresponds to a blank line in the contacts file.

[*]A call is made using code1 but there is no entry in telboxrc.

[*]A value for usecodes is not specified.

[*]The digit after + or 00 is 0. This is an invalid PSTN number.
[/LIST]

---

