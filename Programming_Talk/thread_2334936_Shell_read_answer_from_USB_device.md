---
title: "Shell read answer from USB device"
date: 2016-08-24
forum: Programming Talk
---

### Post by electronico_nc on 2016-08-24
Hi all,
I need to read answer from an USB device after I've sent it a command.
I can send the wanted code to /dev/ttyUSB0 using the following script:
```
#! /bin/bash

# launch with ./program.sh filename
# file has to be in HEX mode, exemple:
# \x02\x33\x07
# but file contents looks like:
# 02 03 07

# init serial port for USB device
stty -F /dev/ttyUSB0 38400 cs8 parenb

# replace all occurences of space by \x in file passed as argument
sed -i 's| |\\x|g' "$1"

# remove empty lines in file passed as argument
sed -i '/^$/d' "$1"

# send each line to serial port, pause between each line
while read -r line
do
    # add \x for the 1st hex code and send line to USB device
    echo -ne '\x'"$line" >/dev/ttyUSB0
    # let's pause as we can't read answer from device
    sleep 0.18
done < "$1"
```and the following file:```
02 31 06 00 35 31 41 0a 52 45 53 45 41 55 20 52 41 49 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 a9
02 31 06 40 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 77
02 31 06 80 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 b7
02 31 06 c0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 f7
```The thing is that the device anwers either 0x03 for OK or 0x04 for KO after each line.
Instead of making a stupid pause (and because the file will be really bigger than this test one), I'd like to wait for the device answer before sending the next line.
Up to now, I've tried (nothing displayed)```
cat -v < /dev/ttyUSB0
```Tried in a 2nd terminal (nothing displayed)```
#! /bin/sh
while true
do
    cat -v < /dev/ttyUSB0
done
```Tried screen without success (nothing displayed)
I can well see the answer from the device using usbmon/vusn-analyzer or wireshark.
How to watch for this in shell ?
Thanks in advance for your thoughts.
Nicolas

---

### Post by steeldriver on 2016-08-24
I'd try something like

```

read -N1 < /dev/ttyUSB0
printf '%#x\n' "$rtn"

```

In fact, I'd get rid of all the seddery and use read and printf to get the bytes in the format you want - something like

```

#!/bin/bash

# init serial port for USB device
stty -F /dev/ttyUSB0 38400 cs8 parenb

# send each line to serial port, check response between each line
while read -r line
do
  if [ -z "$line" ]; then
    continue;
  fi
  read -a bytes <<< "$line"
  printf '\\x%s' "${bytes[@]}" > /dev/ttyUSB0
  read -N1 rtn < /dev/ttyUSB0
  printf '%#x\n' "$rtn"
done < "$1"

```

Actually you can probably skip the explicit empty line check, since read -a will result in a zero-length array which printf will skip conversion of

```

#!/bin/bash

# init serial port for USB device
stty -F /dev/ttyUSB0 38400 cs8 parenb

# send each line to serial port, check response between each line
while read -ra bytes
do
  printf '\\x%s' "${bytes[@]}" > /dev/ttyUSB0
  read -N1 rtn < /dev/ttyUSB0
  printf '%#x\n' "$rtn"
done < "$1"

```

---

### Post by electronico_nc on 2016-08-25
Hello & thanks for your answer (and sorry for the long delay reply) !
HEX codes are well displayed using :```
printf '\\x%s' "${bytes[@]}" 
```But /dev/ttyUSB0 doesn't receive anything using:```
printf '\\x%s' "${bytes[@]}" > /dev/ttyUSB0
```So I'll continue to use the original code as it works to send the datas and try to receive answer from device.
Running the read USB part in a 2nd terminal like this allow to well have the 0a03 (End of text ETX) or 0a04 (End of transmission EOT) after each line.
```
#! /bin/bash
while true
do
    read -N1 rtn < /dev/ttyUSB0
    timestamp=$(date +%s.%3N)
    echo $timestamp
    echo "$rtn" | hexdump | cut -c 9- # YES displays 0a03 or 0a04
done
```Here a bad code is sent on 1st file line to show OK and KO codes. It displays in terminal:```
1472127471.444
0a04                                   

1472127472.180
0a03                                   

1472127472.703
0a03
```
I don't understand why this code always displays 0a30 value in logfile:```
logfile='log.txt'
while read -r line
do
    # send data to device
    echo -en '\x'"$line" >/dev/ttyUSB0
    
    # log data sent to file (timestamp with milliseconds)
    timestamp=$(date +%s.%3N)
    log='-> '$timestamp' \x'"$line"
    echo $log >> $logfile

    # wait for 1st bytes from serial port
    rtn=0
    while [ -z $rtn ]
    do
        read -N1 "$rtn" < /dev/ttyUSB0  
    done

    # convert received data to HEX
    rtn_hex=`echo $rtn | hexdump | cut -c 9-`

    # log response to file
    timestamp=$(date +%s.%3N)
    log='<- '$timestamp' '$rtn_hex
    echo $log >> $logfile
    echo '' >> $logfile

    # let's pause
    sleep 0.25
done < "$1"
```
displays:```
-> 1472127471.325 \x02\x31\x06\x00\x35\x31\x41\x0a\x52\x45\x53\x45\x41\x55\x20\x52\x41\x49\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\xa9
<- 1472127471.332 0a30

-> 1472127471.587 \x02\x31\x06\x40\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x77
<- 1472127471.591 0a30

-> 1472127471.847 \x02\x31\x06\x80\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\xb7
<- 1472127471.853 0a30
```Thanks again for your help.
Nicolas

---

### Post by steeldriver on 2016-08-25
I don't see how your code works at all

```

    # wait for 1st bytes from serial port
    rtn=0
    while [ -z $rtn ]
    do
        read -N1 "$rtn" < /dev/ttyUSB0  
    done

```


[LIST]
[*][ -z $rtn ] tests whether $rtn is *empty*, not whether it is zero. It isn't empty (you just assigned a value to it) so the while loop never executes
[*]read -N1 "$rtn" needs to be read -N1 rtn (the name of the variable, not its value)
[/LIST]

---

### Post by electronico_nc on 2016-08-30
Thanks a lot for your answer : I well had to review my shell scripting syntax :neutral:
Because the read function from ttyUSB0 never ends, I had to launch a second script that read /dev/ttyUSB0 in infinite loop and writes device answer to a log file.
read_ttyusb0.sh:```
#! /bin/bash
logfile='/path/to/log.txt'

while true
do
    read -N1 rtn < /dev/ttyUSB0
    rtn_hex=`echo "$rtn" | hexdump | cut -c 9-` # 0a03 or 0a04
    log=$rtn_hex
    echo $log >> $logfile
done
```
Then program the device : launch a screen session read_ttyusb0 and detach it, send data to device, read last log file line (device answer) and proceed to next line.
program.sh:```
#! /bin/bash

# Make sure only root can run our script
if [[ $EUID -ne 0 ]]; then
    echo "This script must be run as root. Launch it with sudo" 1>&2
    exit 1
fi

# launch with ./program.sh filename
# file has to be in HEX mode, exemple:
# \x02\x33\x07
# but contents looks like:
# 02 03 07

# reset the USB port (set it manually waiting for its detection code)
/home/nico/reset dev/bus/usb/008/003

# allow read and write access to /dev/ttyUSB0 (not sure if required)
chmod o+rw /dev/ttyUSB0

# init serial port for device
stty -F /dev/ttyUSB0 38400 cs8 parenb

# launch the read_ttyusb0.sh script in a screen session and detach it
while true;
do
    if ! screen -list | grep -q "read_ttyusb0"; then
        screen -S read_ttyusb0 -d -m su - root /path/to/read_ttyusb0.sh
        break
    else
        echo 'screen session read_ttyusb0 still running. killing.'
        PROCESS=$(screen -ls |grep read_ttyusb0)
        kill $(echo $PROCESS |cut -f1 -d'.')
        continue
    fi

    # check that screen session is well running
    if screen -list | grep -q "read_ttyusb0"; then
        echo 'screen session read_ttyusb0 running OK'
        break
    else
        echo 'screen session read_ttyusb0 NOT running. exit'
        exit 0
    fi
done


# set log file
logfile='/path/to/log.txt'
#echo ''>$logfile

# replace all occurences of space by \x in file passed as argument
sed -i 's| |\\x|g' "$1"

# remove empty lines in file passed as argument
sed -i '/^$/d' "$1"

# send each line to serial port
l=1 # init line counter
while read -r line
do
    # echo -en => 
    # -n     do not output the trailing newline
    # -e     enable interpretation of backslash escapes
    # \xHH   byte with hexadecimal value HH (1 to 2 digits)
    # add \x for the 1st hex code and send line to USB device
    echo -en '\x'"$line" > /dev/ttyUSB0
    
    log='\x'"$line"
    echo $log >> $logfile # write to logfile

    s=0 # init sleep counter
    while true; # wait for device answer (read logfile last line)
    do
        last_line=$(tac $logfile | egrep -m 1 .)
        
        if [[ "$last_line" == "0a03" ]]; then # OK received : exit reading logfile
            break
        elif [[ "$last_line" == "0a04" ]]; then # KO received : exit program
            echo 'error line '$l
            echo '' >> $logfile
            exit 0
        fi

        sleep 0.1
        s=$(( $s + 1 )) # increment sleep counter
        
        if [ "$s" -ge 10 ]; then # if 1 sec without answer : timeout error
            echo 'error timeout line '$l
            echo '' >> $logfile
            exit 0
        fi
    done

if [ "$l" -eq 1 ]; then # waiting at least 0.5s after the first line (required)
    sleep 0.55
fi

l=$(( $l + 1 )) # increment line counter
done < "$1"
echo '' >> $logfile # add empty line to logfile for reading
echo 'ok' # everything went OK

# kill the running screen session
if screen -list | grep -q "read_ttyusb0"; then
    PROCESS=$(screen -ls |grep read_ttyusb0)
    kill $(echo $PROCESS |cut -f1 -d'.')
fi
```
I'm aware this is not fully well coded, but it works. Thanks again a lot for your answers !
Nicolas

---

