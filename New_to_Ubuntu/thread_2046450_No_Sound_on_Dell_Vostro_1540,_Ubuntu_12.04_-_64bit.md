---
title: "No Sound on Dell Vostro 1540, Ubuntu 12.04 - 64bit"
date: 2012-08-23
forum: New to Ubuntu
---

### Post by meophrates on 2012-08-23
Hi there Ubuntu,

I have a new Dell Vostro 1540 i3 processor computer.

It came with Ubuntu 10.10 (32-bit) pre-installed. The computer was delivered to me with the speakers functioning but my mic wasn't working. After an update, the problem reversed and now my mic works fine and my speakers doesn't work.

I've installed Ubuntu 12.04 (64-bit) and updated the system. I went to the 'sounds settings' and tested out the sound and I still have my mic working but my speakers aren't working. However when plugged into headphones, sound works fine.

I would appreciate it if you could help me, a Newbie at this.

Thanks in advance.

---

### Post by meophrates on 2012-08-23
So i came across another laptop close to mine with a similar problem on this website 
[COLOR=Blue]
[http://pricklytech.wordpress.com/2012/05/26/ubuntu-12-04-dell-vostro-3750-no-sound-when-headphones-are-plugged-in/](http://pricklytech.wordpress.com/2012/05/26/ubuntu-12-04-dell-vostro-3750-no-sound-when-headphones-are-plugged-in/)[/COLOR]

they modified their 
[COLOR=Red]analog-output-headphones.conf[/COLOR]

in a folder 
[COLOR=Red]
/usr/share/pulseaudio/alsa-mixer/paths/[/COLOR]

So i found a similar file in the same folder that I think MAY help anyone who is trying to help me.
[COLOR=Red]
analog-output-speakers-always.conf

[/COLOR](gee, i hope i was able to copy the entire file here)
hope the details help:

# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as
# published by the Free Software Foundation; either version 2.1 of the
# License, or (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

; Path for mixers that don't have a 'Speaker' control, but where we
; force enable the speaker paths nonetheless.
; Needed for some older Dell laptops.
; See analog-output.conf.common for an explanation on the directives

[General]
priority = 100
name = analog-output-speaker

[Jack Headphone]
state.plugged = no
state.unplugged = unknown

[Element Hardware Master]
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right

[Element Master Mono]
switch = off
volume = off

; This profile path is intended to control the speaker, not the
; headphones. But it should not hurt if we leave the headphone jack
; enabled nonetheless.

[Element Headphone]
switch = mute
volume = zero

[Element Headphone2]
switch = mute
volume = zero

[Element Speaker]
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right

[Element Desktop Speaker]
switch = off
volume = off

[Element Front]
switch = mute
volume = merge
override-map.1 = all-front
override-map.2 = front-left,front-right

[Element Front Speaker]
switch = mute
volume = merge
override-map.1 = all-front
override-map.2 = front-left,front-right

[Element Rear]
switch = mute
volume = merge
override-map.1 = all-rear
override-map.2 = rear-left,rear-right

[Element Surround]
switch = mute
volume = merge
override-map.1 = all-rear
override-map.2 = rear-left,rear-right

[Element Surround Speaker]
switch = mute
volume = merge
override-map.1 = all-rear
override-map.2 = rear-left,rear-right

[Element Side]
switch = mute
volume = merge
override-map.1 = all-side

[Element Center]
switch = mute
volume = merge
override-map.1 = all-center
override-map.2 = all-center,all-center

[Element Center Speaker]
switch = mute
volume = merge
override-map.1 = all-center
override-map.2 = all-center,all-center

[Element LFE]
switch = mute
volume = merge
override-map.1 = lfe
override-map.2 = lfe,lfe

[Element LFE Speaker]
switch = mute
volume = merge
override-map.1 = lfe
override-map.2 = lfe,lfe

.include analog-output.conf.common



Let me know if you need anything else to solve my problem. Sorry for the trouble and thanks in advance

---

### Post by anewguy on 2012-08-23
By any chance is your sound muted somewhere?

Also, please post back the contents of the last file the file you posted to links to:

 analog-output.conf.common

---

### Post by meophrates on 2012-08-23
thanks for getting in touch with me, 'a new guy'. I did check if it were muted. It isnt. It's playing music through the headphone's jack.

here are the contents of the requested file.


# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as
# published by the Free Software Foundation; either version 2.1 of the
# License, or (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

; Common part of all paths

; So here's generally how mixer paths are used by PA: PA goes through
; a mixer path file from top to bottom and checks if a mixer element
; described therein exists. If so it is added to the list of mixer
; elements PA will control, keeping the order it read them in. If a
; mixer element described here has set the required= or
; required-absent= directives a path might not be accepted as valid
; and is ignored in its entirety (see below). However usually if a
; element listed here is missing this one element is ignored but not
; the entire path.
;
; When a device shall be muted/unmuted *all* elements listed in a path
; file with "switch = mute" will be toggled.
;
; When a device shall change its volume, PA will got through the list
; of all elements with "volume = merge" and set the volume on the
; first element. If that element does not support dB volumes, this is
; where the story ends. If it does support dB volumes, PA divides the
; requested volume by the volume that was set on this element, and
; then go on to the next element with "volume = merge" and then set
; that there, and so on.  That way the first volume element in the
; path will be the one that does the 'biggest' part of the overall
; volume adjustment, with the remaining elements usually being set to
; some value next to 0dB. This logic makes sure we get the full range
; over all volume sliders and a very high granularity of volumes
; already in hardware.
;
; All switches and enumerations set to "select" are exposed via the
; "port" functionality of sinks/sources. Basically every possible
; switch setting and every possible enumeration setting will be
; combined and made into a "port". So make sure you don't list too
; many switches/enums for exposing, because the number of ports might
; rise exponentially.
; 
; Only one path can be selected at a time. All paths that are valid
; for an audio device will be exposed as "port" for the sink/source.


; [General]
; priority = ...                         # Priority for this path
; description = ...
; 
; [Option ...:...]                       # For each option of an enumeration or switch element
;                                        # that shall be exposed as a sink/source port. Needs to
;                                        # be named after the Element, followed by a colon, followed
;                                        # by the option name, resp. on/off if the element is a switch.
; name = ...                             # Logical name to use in the path identifier
; priority = ...                         # Priority if this is made into a device port
; required = ignore | enumeration | any            # In this element, this option must exist or the path will be invalid. ("any" is an alias fo$
; required-any = ignore | enumeration | any        # In this element, either this or another option must exist (or an element)
; required-absent = ignore | enumeration | any     # In this element, this option must not exist or the path will be invalid
; 
; [Element ...]                          # For each element that we shall control
; required = ignore | switch | volume | enumeration | any     # If set, require this element to be of this kind and available,
;                                                             # otherwise don't consider this path valid for the card
; required-any = ignore | switch | volume | enumeration | any # If set, at least one of the elements with required-any in this
;                                                             # path must be present, otherwise this path is invalid for the card
; required-absent = ignore | switch | volume                  # If set, require this element to not be of this kind and not
;                                                             # available, otherwise don't consider this path valid for the card
; 
; switch = ignore | mute | off | on | select # What to do with this switch: ignore it, make it follow mute status,
;                                            # always set it to off, always to on, or make it selectable as port.
;                                            # If set to 'select' you need to define an Option section for on
;                                            # and off
; volume = ignore | merge | off | zero | <volume step> # What to do with this volume: ignore it, merge it into the device
;                                                      # volume slider, always set it to the lowest value possible, or always
;                                                      # set it to 0 dB (for whatever that means), or always set it to
;                                                      # <volume step> (this only makes sense in path configurations where
;                                                      # the exact hardware and driver are known beforehand).
; volume-limit = <volume step>           # Limit the maximum volume by disabling the volume steps above <volume step>.
; enumeration = ignore | select          # What to do with this enumeration, ignore it or make it selectable
;                                        # via device ports. If set to 'select' you need to define an Option section
;                                        # for each of the items you want to expose
; direction = playback | capture         # Is this relevant only for playback or capture? If not set this will implicitly be
;                                        # set the direction of the PCM device is opened as. Generally this doesn't need to be set
;                                        # unless you have a broken driver that has playback controls marked for capture or vice
;                                        # versa
; direction-try-other = no | yes         # If the element does not supported what is requested, try the other direction, too?
;
; override-map.1 = ...                   # Override the channel mask of the mixer control if the control only exposes a single channel
; override-map.2 = ...                   # Override the channel masks of the mixer control if the control only exposes two channels
;                                        # Override maps should list for each element channel which high-level channels it controls via a
;                                        # channel mask. A channel mask may either be the name of a single channel, or the words "all-left",
;                                        # "all-right", "all-center", "all-front", "all-rear", and "all" to encode a specific subset of
;                                        # channels in a mask

[Element PCM]
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right

[Element External Amplifier]
switch = select

[Option External Amplifier:on]
name = output-amplifier-on
priority = 10

[Option External Amplifier:off]
name = output-amplifier-off
priority = 0

[Element Bass Boost]
switch = select

[Option Bass Boost:on]
name = output-bass-boost-on
priority = 0

[Option Bass Boost:off]
name = output-bass-boost-off
priority = 10

[Element IEC958 Optical Raw]
switch = off

;;; 'Analog Output'

[Element Analog Output]
enumeration = select

[Option Analog Output:Speakers]
name = output-speaker
priority = 10

[Option Analog Output:Headphones]
name = output-headphones
priority = 9

[Option Analog Output:FP Headphones]
name = output-headphones
priority = 8

---

### Post by meophrates on 2012-08-24
This may list my drivers. I switched to terminal and typed: 

:~ $ aplay -l
 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by meophrates on 2012-09-17
It's been three weeks and I keep checking this page everyday.  I still have the problem but noone helping out! :(

---

