---
title: "Best way to programmatically find serial device based on usb description (bash)"
date: 2024-06-17
forum: Programming Talk
---

### Post by wimsturkenboom on 2024-06-17
Hello everybody

I have the following scenario (it might sound familiar to users of Arduino microcontroller boards).

I have a few USB devices with the same VID/PID but different usb descriptions. I need be able to pick a board based on the usb description using the shell. For those boards *lsusb* only gives the VID and the PID (1b4f:9204) but no usb description; I understand the reason, they are not in /var/lib/usbutils/usb.ids at all and I'm reluctant to modify that file as an update might undo the changes.
```

$ lsusb
Bus 001 Device 009: ID 0925:3881 Lakeview Research Saleae Logic
Bus 001 Device 008: ID 04d9:1503 Holtek Semiconductor, Inc. Keyboard
Bus 001 Device 015: ID 1b4f:9204  
Bus 001 Device 006: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 005: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 001 Device 004: ID 2341:0042 Arduino SA Mega 2560 R3 (CDC ACM)
Bus 001 Device 003: ID 1a86:7523 QinHeng Electronics HL-340 USB-Serial adapter
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1b4f:9204  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

*dmesg* sees the boards, e.g. 
```

[  645.557580] cdc_acm 1-5.4.2:1.0: ttyACM1: USB ACM device
[  661.966126] usb 1-5.4.2: USB disconnect, device number 14
[ 1509.548083] usb 1-5.4.2: new full-speed USB device number 15 using ehci-pci
[ 1509.631344] usb 1-5.4.2: New USB device found, idVendor=1b4f, idProduct=9204
[ 1509.631351] usb 1-5.4.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1509.631355] usb 1-5.4.2: Product: SparkFun Pro Micro22
[ 1509.631359] usb 1-5.4.2: Manufacturer: SparkFun
[ 1509.632074] cdc_acm 1-5.4.2:1.0: ttyACM1: USB ACM device
[ 3460.040120] usb 2-2: new full-speed USB device number 2 using uhci_hcd
[ 3460.208157] usb 2-2: New USB device found, idVendor=1b4f, idProduct=9204
[ 3460.208164] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 3460.208168] usb 2-2: Product: SparkFun Pro Micro
[ 3460.208172] usb 2-2: Manufacturer: SparkFun
[ 3460.210384] cdc_acm 2-2:1.0: ttyACM2: USB ACM device

```

So I need to find a way to find ttyACM1 and ttyACM2 based on *Product: SparkFun Pro Micro22* and *SparkFun Pro Micro* respectively.

Are there shell utilities that provide an easy way to find the serial ports or is filtering (e.g. grep) through dmesg results the only way.

Thanks in advance, WimS

Note:
using antix linux but I think that this is more a generic linux question.

---

### Post by TheFu on 2024-06-18
If the device files are always 'ttyACM?' <---- that's a regex, you can use bash to easily pull the name by using filename globbing and BASH_REMATCH patterns, but really, I'd probably just get the list and use sed or cut.  Those are standard UNIX text processing utils and there are 50+ others.

Of course, you could use python, ruby, perl, too.

OTOH, what's wrong with using 
```
\ls /dev/ttyACM* | egrep -o 'ttyACM[0-9]'
```
Seems pretty simple to me.  

Is there a risk of having other devices with ttyACM in their names? If so, some other filtering would be needed to limit just the specific ones you want.  udev would be where I started, if I had something like this and needed to worry about connections and disconnections post-boot.

---

### Post by wimsturkenboom on 2024-06-22
Thanks for the reply. I think I did not explain the problem correctly.

This is a slightly different dmesg output
```

[14268.944047] usb 1-5.4.2: new full-speed USB device number 19 using ehci-pci
[14269.027261] usb 1-5.4.2: New USB device found, idVendor=1b4f, idProduct=9204
[14269.027267] usb 1-5.4.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[14269.027272] usb 1-5.4.2: Product: SparkFun Pro Micro (1)
[14269.027275] usb 1-5.4.2: Manufacturer: SparkFun
[14269.027954] cdc_acm 1-5.4.2:1.0: ttyACM0: USB ACM device

[14398.800075] usb 2-2: new full-speed USB device number 8 using uhci_hcd
[14398.968999] usb 2-2: New USB device found, idVendor=1b4f, idProduct=9204
[14398.969048] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[14398.969052] usb 2-2: Product: SparkFun Pro Micro (2)
[14398.969067] usb 2-2: Manufacturer: SparkFun
[14398.972206] cdc_acm 2-2:1.0: ttyACM2: USB ACM device

```

From the above dmesg output, I'll need to match "SparkFun Pro Micro (2)" with ttyACM0 or  "SparkFun Pro Micro (1)" with an other ttyACM2. I'm planning to enter e.g. "SparkFun Pro Micro (2)" as an argument to a shell script and the script will further down the line use the associated /dev/ttyACMx to open the device (serial port) for the SparkFun Pro Micro (2).

I hope that that makes it clear.

In the meantime I did find *udevadm* but I'm battling with the grep to match hex characters (e.g. \x20) to ascii.
```

P: /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5.4/1-5.4.2/1-5.4.2:1.0/tty/ttyACM0
N: ttyACM0
S: serial/by-id/usb-SparkFun_SparkFun_Pro_Micro__1_-if00
S: serial/by-path/pci-0000:00:1d.7-usb-0:5.4.2:1.0
E: DEVLINKS=/dev/serial/by-id/usb-SparkFun_SparkFun_Pro_Micro__1_-if00 /dev/serial/by-path/pci-0000:00:1d.7-usb-0:5.4.2:1.0
E: DEVNAME=/dev/ttyACM0
E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5.4/1-5.4.2/1-5.4.2:1.0/tty/ttyACM0
E: ID_BUS=usb
E: ID_MODEL=SparkFun_Pro_Micro__1_
E: ID_MODEL_ENC=SparkFun\x20Pro\x20Micro\x20\x281\x29
E: ID_MODEL_FROM_DATABASE=NM10/ICH7 Family USB2 EHCI Controller
E: ID_MODEL_ID=9204
E: ID_PATH=pci-0000:00:1d.7-usb-0:5.4.2:1.0
E: ID_PATH_TAG=pci-0000_00_1d_7-usb-0_5_4_2_1_0
E: ID_PCI_CLASS_FROM_DATABASE=Serial bus controller
E: ID_PCI_INTERFACE_FROM_DATABASE=EHCI
E: ID_PCI_SUBCLASS_FROM_DATABASE=USB controller
E: ID_REVISION=0100
E: ID_SERIAL=SparkFun_SparkFun_Pro_Micro__1_
E: ID_TYPE=generic
E: ID_USB_CLASS_FROM_DATABASE=Miscellaneous Device
E: ID_USB_DRIVER=cdc_acm
E: ID_USB_INTERFACES=:020200:0a0000:
E: ID_USB_INTERFACE_NUM=00
E: ID_USB_PROTOCOL_FROM_DATABASE=Interface Association
E: ID_VENDOR=SparkFun
E: ID_VENDOR_ENC=SparkFun
E: ID_VENDOR_FROM_DATABASE=Intel Corporation
E: ID_VENDOR_ID=1b4f
E: MAJOR=166
E: MINOR=0
E: SUBSYSTEM=tty
E: USEC_INITIALIZED=14269613903

```
and
```

P: /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/tty/ttyACM2
N: ttyACM2
S: serial/by-id/usb-SparkFun_SparkFun_Pro_Micro__2_-if00
S: serial/by-path/pci-0000:00:1d.0-usb-0:2:1.0
E: DEVLINKS=/dev/serial/by-id/usb-SparkFun_SparkFun_Pro_Micro__2_-if00 /dev/serial/by-path/pci-0000:00:1d.0-usb-0:2:1.0
E: DEVNAME=/dev/ttyACM2
E: DEVPATH=/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/tty/ttyACM2
E: ID_BUS=usb
E: ID_MODEL=SparkFun_Pro_Micro__2_
E: ID_MODEL_ENC=SparkFun\x20Pro\x20Micro\x20\x282\x29
E: ID_MODEL_FROM_DATABASE=NM10/ICH7 Family USB UHCI Controller
E: ID_MODEL_ID=9204
E: ID_PATH=pci-0000:00:1d.0-usb-0:2:1.0
E: ID_PATH_TAG=pci-0000_00_1d_0-usb-0_2_1_0
E: ID_PCI_CLASS_FROM_DATABASE=Serial bus controller
E: ID_PCI_INTERFACE_FROM_DATABASE=UHCI
E: ID_PCI_SUBCLASS_FROM_DATABASE=USB controller
E: ID_REVISION=0100
E: ID_SERIAL=SparkFun_SparkFun_Pro_Micro__2_
E: ID_TYPE=generic
E: ID_USB_CLASS_FROM_DATABASE=Miscellaneous Device
E: ID_USB_DRIVER=cdc_acm
E: ID_USB_INTERFACES=:020200:0a0000:
E: ID_USB_INTERFACE_NUM=00
E: ID_USB_PROTOCOL_FROM_DATABASE=Interface Association
E: ID_VENDOR=SparkFun
E: ID_VENDOR_ENC=SparkFun
E: ID_VENDOR_FROM_DATABASE=Intel Corporation
E: ID_VENDOR_ID=1b4f
E: MAJOR=166
E: MINOR=2
E: SUBSYSTEM=tty
E: USEC_INITIALIZED=14399572873

```

E.g. In "E: ID_MODEL_ENC=SparkFun\x20Pro\x20Micro\x20\x282\x29" I need to replace the \xXX values by their ascii values so the argument for the shell script can be user friendly.

The current shell script (work in progress) runs *udevadm* over the devices and pipes the result through grep.
```

 if [ $# != 1 ]
      2 then
      3   echo "No argument"
      4   exit -1
      5 else
      6   echo $1
      7 fi
      8 
      9 for device in /dev/ttyACM*;
     10 do
     11   echo $device
     12   udevadm info --name $device |grep "$1"
     13 done
     14 
     15 exit 0

```
For this to work I need to enter all those hex values in a unfriendly way
```

$ ./findtty.sh "Pro\\\x20Micro\\\x20\\\x281\\\x29"

```
Result
```

Pro\\x20Micro\\x20\\x281\\x29
/dev/ttyACM0
E: ID_MODEL_ENC=SparkFun\x20Pro\x20Micro\x20\x281\x29
/dev/ttyACM1
/dev/ttyACM2

```
And this is what I would like to achieve
```

$ ./findtty.sh "Pro Micro (1)"

```

---

### Post by TheFu on 2024-06-22
You know, any AI tool can answer simple regex questions.  As much as I find them useless for total solutions, for some specific, small, issues like regex, AI does a good job, usually.   

You can also use a hex to ascii tool, something like **od**.

grep is a weenie version.  May want to use egrep (grep -E), which supports the full regex language.

---

### Post by wimsturkenboom on 2024-06-22
Thanks for the help. I do not think that regular expressions are my problem; shell scripting is more the problem.

I came up with the below solution
```

# check for arguments
if [ $# != 1 ]
then
  echo "No argument"
  exit -1
fi

emptyText=""

# count number of matching devices
count=0
# final port (device) to use
port=""

# loop through all ttyACM devices
for device in /dev/ttyACM*;
do
  # get info for devicesw 
  udevDevice=$(udevadm info --name $device)
  #echo "udevDevice = "
  #echo "$udevDevice"
  # grep what we're looking for
  udevGrep=$(echo -e "$udevDevice" |grep "$1");
  #echo "udevGrep = "
  #echo "$udevGrep"

  # if we have a match
  if [ "$udevGrep" != "$emptyText" ]
  then
    # assign to port
    port=$device
    #echo "$device"
    #echo "$result"
    # update count of matching devices
    ((count++))
  fi
done

# check results
if [[ $count -eq 0 ]]
then
  echo "No matching device found"
  exit -2
else
  if [[ $count -gt 1 ]]
  then
    echo "Multiple devices found"
    echo "$count"
    exit -3
  else
    echo -n "Device '"
    echo -n "$1"
    echo -n "' on port '"
    echo -n "$port"
    echo "'"
  fi
fi

exit 0

```

I might have overlooked scenarios in this (e.g. newline at the end of the regexp) but I can fine tune as I go along.

Output:
```

$ ./findtty.sh "Micro (2)"
Device 'Micro (2)' on port '/dev/ttyACM2'

$ ./findtty.sh "Micro"
Multiple devices found
2

```

---

### Post by TheFu on 2024-06-23
If you are having issues with shell scripting, perhaps if you forced the exact shell you wanted to be used to be used, that would help?  The first line of every shell script should clearly say which interpreter to be used.  That can be sh, ksh, bash, csh, zsh, perl, python, ruby .... whatever.  But we are expected to actually provide that line.

[https://tldp.org/LDP/abs/html/](https://tldp.org/LDP/abs/html/) is the only reference I've needed for bash scripting, but whenever a bash script becomes over 1 terminal page in length, I switch to a real language, since the script is obviously complex enough to need an easier to use language.  Of course, there are exception, like when I cannot be 100% certain a system will have the script interpreter that I'd like already installed or if the bash script is just command after command after command with no real data structures or decision points.

BTW, I was wondering if you could get the list of possible devices, then have a human pick the correct one from the list, that isn't hard in bash.  Just put the possible answers into a bash array, then display those contents with a selection number to choose, then read the selected number and continue processing.  Of course, if only 1 possible answer is found, just use that and continue.  

OTOH, seems like you have a workable solution already.

---

### Post by wimsturkenboom on 2024-06-24
Thanks

I know I should force the shell to use; just a bit lazy (and rusty). It's implemented now.

> 
but whenever a bash script becomes over 1 terminal page in length, I  switch to a real language, since the script is obviously complex enough  to need an easier to use language
...
...
Just put the possible answers into a bash array, then display those contents with a selection number to choose


I do not think it's complex ;) But it will be longer than 1 page.

There should never be a second device with the same USB product description. But I did not tell you that as it was not relevant to the initial question ;) The final code above only contains the first step in a process
[LIST=1]
[*]Detect port (completed)
[*]Reset device
[*]Program device with code specific to the USB description
[/LIST]

Note:
The full script with all three steps is now basically in place; needs a bit of polishing.

---

### Post by ruwolf on 2024-07-05
> **TheFu said:**
> 
grep is a weenie version.  May want to use egrep (grep -E), which supports the full regex language.

grep -P supports almost the full regex language:
[Perl-compatible regular expressions (PCREs)]("https://en.wikipedia.org/wiki/Perl_Compatible_Regular_Expressions"):
> 
PCRE's syntax is much more powerful and flexible than either of the POSIX regular expression flavors (BRE, ERE)&#8230;


---

