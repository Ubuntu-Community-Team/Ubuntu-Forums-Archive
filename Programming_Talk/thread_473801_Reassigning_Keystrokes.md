---
title: "Reassigning Keystrokes"
date: 2007-06-14
forum: Programming Talk
---

### Post by josesanders on 2007-06-14
I have a saa7134 tv card which I never got to work in MythTV, so I am using it just for the remote control.  The remote keystrokes are compiled into the driver, and so they are just seen as normal keystrokes, as if they were from a keyboard.  I would like to reassign their functionality without changing the function of the keys on the actual keyboard, so I have decided to try to recompile the driver.  Below, I have included the relevent section from the file ir-common.c:

```
IR_KEYTAB_TYPE ir_codes_rc5_tv[IR_KEYTAB_SIZE] = {
	[ 0x00 ] = KEY_KP0,             // 0
	[ 0x01 ] = KEY_KP1,             // 1
	[ 0x02 ] = KEY_KP2,             // 2
	[ 0x03 ] = KEY_KP3,             // 3
	[ 0x04 ] = KEY_KP4,             // 4
	[ 0x05 ] = KEY_KP5,             // 5
	[ 0x06 ] = KEY_KP6,             // 6
	[ 0x07 ] = KEY_KP7,             // 7
	[ 0x08 ] = KEY_KP8,             // 8
	[ 0x09 ] = KEY_KP9,             // 9

	[ 0x0b ] = KEY_CHANNEL,         // channel / program (japan: 11)
	[ 0x0c ] = KEY_POWER,           // standby
	[ 0x0d ] = KEY_MUTE,            // mute / demute
	[ 0x0f ] = KEY_TV,              // display
	[ 0x10 ] = KEY_VOLUMEUP,        // volume +
	[ 0x11 ] = KEY_VOLUMEDOWN,      // volume -
	[ 0x12 ] = KEY_BRIGHTNESSUP,    // brightness +
	[ 0x13 ] = KEY_BRIGHTNESSDOWN,  // brightness -
	[ 0x1e ] = KEY_SEARCH,          // search +
	[ 0x20 ] = KEY_CHANNELUP,       // channel / program +
	[ 0x21 ] = KEY_CHANNELDOWN,     // channel / program -
	[ 0x22 ] = KEY_CHANNEL,         // alt / channel
	[ 0x23 ] = KEY_LANGUAGE,        // 1st / 2nd language
	[ 0x26 ] = KEY_SLEEP,           // sleeptimer
	[ 0x2e ] = KEY_MENU,            // 2nd controls (USA: menu)
	[ 0x30 ] = KEY_PAUSE,           // pause
	[ 0x32 ] = KEY_REWIND,          // rewind
	[ 0x33 ] = KEY_GOTO,            // go to
	[ 0x35 ] = KEY_PLAY,            // play
	[ 0x36 ] = KEY_STOP,            // stop
	[ 0x37 ] = KEY_RECORD,          // recording
```

Some of the KEY_xx constants are defined in the ir-common.h file that was included with the saa7134 source code, but I believe that most are already defined in the linux kernel headers.  Does anyone know where these are defined?  I assume that, for example, if I want the remote key 1 to function like the up arrow key on the keyboard, I would change the KEY_KP1 to something like KEY_UP, but where are these constants defined?

---

### Post by Toxe on 2007-06-14
/usr/include/linux/input.h :-)

---

### Post by josesanders on 2007-06-14
Thanks, that's what I needed.

---

