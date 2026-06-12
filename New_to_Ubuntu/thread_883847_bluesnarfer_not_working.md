---
title: "bluesnarfer not working"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by 7raTEYdCql on 2008-08-08
I use ubuntu 8.04. Tried bluesnarfer to scan my mobile and this is the error message that i get:

mehrzad@mehrzad-laptop:~$ sudo bluesnarfer -r 1-10 -b 00:1B:EE:93:1B:66
bluesnarfer: hci_read_remote_name failed
bluesnarfer: unable to get device name
bluesnarfer: open /dev/bluetooth/rfcomm/0, No such file or directory
bluesnarfer: bt_rfcomm_config failed
bluesnarfer: unable to create rfcomm connection
bluesnarfer: release rfcomm ok

hcitool scan hci0 works

What must i do?

---

### Post by 7raTEYdCql on 2008-08-08
I use ubuntu 8.04. Tried bluesnarfer to scan my mobile and this is the error message that i get:

mehrzad@mehrzad-laptop:~$ sudo bluesnarfer -r 1-10 -b 00:1B:EE:93:1B:66
bluesnarfer: hci_read_remote_name failed
bluesnarfer: unable to get device name
bluesnarfer: open /dev/bluetooth/rfcomm/0, No such file or directory
bluesnarfer: bt_rfcomm_config failed
bluesnarfer: unable to create rfcomm connection
bluesnarfer: release rfcomm ok

hcitool scan hci0 works

What must i do?

---

### Post by jpeddicord on 2008-08-08
Threads merged. Please don't make duplicates.

---

### Post by 7raTEYdCql on 2008-08-09
didnt understand i am a noob
saw a video and tried to replicate didnt work.

this is what i got

---

### Post by timmo710 on 2008-08-28
hi, i have been using ubuntu for a short amount of time and have found out how to get bluesnarfer to work. read up on this page:

[http://forums.remote-exploit.org/showthread.php?t=8592&highlight=Bluesnarfer](http://forums.remote-exploit.org/showthread.php?t=8592&highlight=Bluesnarfer)

instead of the command:
sdptools browse --tree --l2cap <target MAC>

use:
sdptool browse --tree --l2cap (target MAC) > output
(yes it is sdptool not sdptools)



so the commands to use (in order):

sudo -s
mkdir -p /dev/bluetooth/rfcomm
mknod -m 666 /dev/bluetooth/rfcomm/0 c 216 0

hcitool scan

l2ping (target MAC)
to make sure we can contact it)

sdptool browse --tree --l2cap (target MAC) > output

use gedit to view the file "output"

find the string "channel"
there will be many times it finds the string. you want the lines much like:
Channel/Port (Integer) : 0x1

then you get the last number (in this case "1")
write down each one (unless they end in a letter)

then run bluesnarfer with your switches and add the switch "-C (channel number)

if you cant get in then there is more security then bluesnarfer can bypass.

this worked on one of my phones (sharp hiptop 3) but wouldnt show any contacts. looks empty
and i couldnt get anything working on my other phone (nokia 6085)

above could be completely wrong but yeh this is what i did and hopefully it helps you

---

