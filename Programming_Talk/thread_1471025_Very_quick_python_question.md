---
title: "Very quick python question"
date: 2010-05-03
forum: Programming Talk
---

### Post by f.sardis on 2010-05-03
I have an Asus Ai Remote that I want to use on Lucid Lynx and I found a nice script on the net for it by Hogwog who only mapped half the buttons on the remote. Here is the script:
```

#!/etc/bin/python
import usb
import virtkey
from sys import exit

class KeyMapper():
    def __init__(self):
        self.map_dic = {}
        self.map_dic2 = {}
        self.v = virtkey.virtkey()
        
    def map(self, remotenr, keycode):
        self.map_dic[remotenr] = keycode
    
    def execute(self, remotenr):
        try:
            self.v.press_keycode(self.map_dic[remotenr])
            self.v.release_keycode(self.map_dic[remotenr])
        except KeyError:
            print str(remotenr)+' (not mapped)'

#what busses are available?
busses = usb.busses()

ai = None

#we only need the ASUS Ai Remote
while not ai:
    for bus in busses:
        for dev in bus.devices:
            if dev.idVendor == 0x0b05 and dev.idProduct == 0x172e:
                print 'ASUS Ai Remote found.'
                ai = dev
        
#if the remote isn't found - exit
if not ai:
    print 'No Device found!'
    exit()

#If we want our RC to do something, we should map its keys.
mapper = KeyMapper()

mapper.map(1,124)
mapper.map(3,121)
mapper.map(4,121)   #Mute
mapper.map(5,121)
mapper.map(6,121)
mapper.map(7,123)   #VolumeUp
mapper.map(8,173)   #Previous
mapper.map(9,172)   #Play/Pause
mapper.map(10,171)  #Next
mapper.map(11,122)  #VolumeDown

#we're still there so we open the device
handler = ai.open()

#we know that there is only one configuration
conf = ai.configurations[0]
#only one interface
iface = conf.interfaces[0][0]
#only one endpoint
endp = iface.endpoints[0]

#we don't want the kernel to handle this device
try:
    handler.detachKernelDriver(iface)
except usb.USBError, e:
    print e.args[0]
    if e.args != ('could not detach kernel driver from interface 0: No data available',):
        raise e

#the try...except statement in the next loop is due to a pyusb bug, that raises
#an error ('USBError: no error') where there is none.
while True:
    data = (2,0,0,0,0,0,0,0)
    try:
        data = handler.interruptRead(endp.address, endp.maxPacketSize,10)
    except usb.USBError, e:
        if e.args != ('No error',) and e.args != ('could not detach kernel driver from interface 0: No data available',): # [http://bugs.debian.org/476796](http://bugs.debian.org/476796)
            raise e
    
    if data[1] != 0:
        mapper.execute(data[1])
   #if data[1] == 4:
   #    break
```

I would like to map the remaining keys and I made an attempt to create the extra key maps but unfortunately I cannot find the functions. My programming skills are pretty basic but I am assuming that mapper.map(1,121) for example maps button 1 to function 121 which mutes the volume. Where can I find a complete list of all the functions so I can map more things? I have been searching for hours and came up with nothing. I have a feeling it is a trivial question for someone experienced in python. I am just looking to do things like hibernate and shut down the pc and hopefully, if it is simple, start an application or do other system functions.

Thanks so much for any help :D

Update-- 
I have tested the key mappings I created and they all work ie, all the buttons mute the volume when I press them, however key 4 mutes the volume and terminates the script after. Is this a bug in the code or a bug in the APIs the script is using?

Update2--
I have fixed the script termination problem by changing the last line    if data[1] == 14:
I think this way, it is looking for key 14 which does not exist, so it never breaks the script. It seems ok, but do you think I have broken something?

---

### Post by wmcbrine on 2010-05-03
Please use "code" (not "quote") tags around your code to preserve the indentation (especially important in Python). In this case, we can't even quote the message to see the original indentation (which would work if the code weren't surrounded by *any* tags), since quoted material is dropped on a re-quote.

---

### Post by f.sardis on 2010-05-03
> **wmcbrine said:**
> Please use "code" (not "quote") tags around your code to preserve the indentation (especially important in Python). In this case, we can't even quote the message to see the original indentation (which would work if the code weren't surrounded by *any* tags), since quoted material is dropped on a re-quote.

Sorry, I didn't realise there was a code tag. I have now fixed my original post. I have played around with the script a bit. I found that commenting out the last couple of lines fixes the bug I reported without adverse effects.
The second thing I discovered is that the numbers that appear in the mapper.map(1,124) lines of code are actually keyboard mappings. I found through experimentation that 124 calls the shutdown function so now my shutdown button works on the remote. Is it possible to find a key map for a qwerty keyboard? This is my new search but again, I am not lucky at all.
There are a couple of application buttons that I might be able to use by mapping a keyboard shortcut to those applications but I was wondering if there is a quick and dirty way to launch any application through python.

Thanks :)

Update--

Ok, I have figured out what I am looking for: Keycodes for QWERTY keyboard is Linux. I have found some tables but they do not seem to be matching with my findings. I will keep experimenting with various numbers.

---

### Post by jeffathehutt on 2010-05-03
If you need the keycode for a specific key, you can use the xev program to find it.  Just run ```
xev
``` from the command line, and hit the key you are interested in.

Output from the 'a' key:
```
KeyRelease event, serial 40, synthetic NO, window 0x2000001,
    root 0x15a, subw 0x0, time 6408995, (-730,104), root:(667,534),
    state 0x0, keycode 38 (keysym 0x61, a), same_screen YES,
    XLookupString gives 1 bytes: (61) "a"
    XFilterEvent returns: False
```

The line you are looking for is "keycode" on line 3 of the output :)

---

### Post by f.sardis on 2010-05-04
I think I am looking for the opposite actually. What I need, is a map of all the keycodes that Ubuntu will understand. If I use xev, I will just see the keycodes of my keyboard. I want my remote to cover functions that my keyboard does not have. 
For example, my keyboard does not have a button to log off or shut down. I would like to find the keycodes for those functions and more. Then I should be able to map almost every button on the remote to the Windows equivalent. I already have set one button to launch the music player. I would like to set another to launch the movie player.

The tricky part is that some functions have a key combination on the keybaord. For example if I want to show the desktop it would be ctrl+alt+D. Is there a specific keycode for button combinations that I can assign to a single key? That would allow me to minimise and restore everything from the remote.

-Update--
I have now found the keycodes to lock session and put the pc on standby. they are 160 and 150 respectively.

---

### Post by jeffathehutt on 2010-05-05
> **f.sardis said:**
> I think I am looking for the opposite actually

I misread your original post, sorry about that.  Unfortunately I don't know how to do what you are trying to do, but I will look around and if I come up with anything I will post back here.

I wonder if the key bindings are controlled by X or if they are controlled by the desktop environment...  The key codes seem to come from X, but the action taken for each code might be controlled by the DE.

---

### Post by soltanis on 2010-05-06
The bindings for hotkeys are usually controlled by hotkeys daemons. These come with desktop environments, but you can also use alternative implementations, like xbindkeys.

---

### Post by f.sardis on 2010-05-06
I figured it out and I got all the functions working. I typed this in the terminal.

 xmodmap -pke > xmodmap.conf

This gave me a list of all the keycodes in my downloads folder.

---

