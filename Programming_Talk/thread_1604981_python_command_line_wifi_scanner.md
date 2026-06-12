---
title: "python command line wifi scanner"
date: 2010-10-24
forum: Programming Talk
---

### Post by Crazedpsyc on 2010-10-24
I am making a simple wifi scanner program for the command line (basically a wardriver) and I want it to get the info from os.popen("iwlist %s scanning" % interface) and print it in a format such as 
```
> scan wlan0 1 # 1 being the number of seconds to wait between scanning
Scanning for networks on wlan0...
No networks found, retrying in 1 second...
Found: MYNET (strength: 25/70)
Found: OtherNet (strength: 14/50)
No networks found, retrying in 1 second...
No networks found, retrying in 1 second...
```

So I have everything except parsing the output of iwlist down. That's what I need. If I could get it into dictionary form that would be great, but I don't know how. for those of you who don't know what the output of iwlist wlan0 scanning looks like, here it is:
```
wlan0     Scan completed :
          Cell 01 - Address: MA:CA:DD:RE:SS
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:off
                    ESSID:"MYNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000028e7163467
                    Extra: Last beacon: 3370ms ago
                    IE: Unknown: 0004484F4D45
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEC010FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4300000000
                    IE: Unknown: DD1E00904C33EC010FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401000400000000000000000000000000000000000000

```
If there is another way of getting the available networks quickly, That would be great too! Thanks!

---

### Post by Crazedpsyc on 2010-10-25
nothing? bump

---

### Post by johnl on 2010-10-25
This is probably not the best way to do this, but take a look:

```

#!/usr/bin/env python
import subprocess
import re

class line_matcher:
    def __init__(self, regexp, handler):
        self.regexp  = re.compile(regexp)
        self.handler = handler


def handle_new_network(line, result, networks):
    # group(1) is the mac address
    networks.append({})
    networks[-1]['Address'] = result.group(1)

def handle_essid(line, result, networks):
    # group(1) is the essid name
    networks[-1]['ESSID'] = result.group(1)

def handle_quality(line, result, networks):
    # group(1) is the quality value
    # group(2) is probably always 100
    networks[-1]['Quality'] = result.group(1) + '/' + result.group(2)

def handle_unknown(line, result, networks):
    # group(1) is the key, group(2) is the rest of the line
    networks[-1][result.group(1)] = result.group(2)

if __name__ == '__main__':
    proc = subprocess.Popen(['/sbin/iwlist', 'wlan0', 'scan'],
                            stdout=subprocess.PIPE)
    stdout, stderr =  proc.communicate()

    lines = stdout.split('\n')

    networks = []
    matchers = []

    # catch the line 'Cell ## - Address: XX:YY:ZZ:AA:BB:CC'
    matchers.append(line_matcher(r'\s+Cell \d+ - Address: (\S+)',
                                 handle_new_network))
    
    # catch the line 'ESSID:"network name"
    matchers.append(line_matcher(r'\s+ESSID:"([^"]+)"', 
                                 handle_essid))

    # catch the line 'Quality:X/Y Signal level:X dBm Noise level:Y dBm'
    matchers.append(line_matcher(r'\s+Quality:(\d+)/(\d+)',
                                 handle_quality))

    # catch any other line that looks like this:
    # Key:value
    matchers.append(line_matcher(r'\s+([^:]+):(.+)',
                                 handle_unknown))

    # read each line of output, testing against the matches above
    # in that order (so that the key:value matcher will be tried last)
    for line in lines:
        for m in matchers:
            result = m.regexp.match(line)
            if result:
                m.handler(line, result, networks)
                break

    for n in networks:
        print 'Found network', n['ESSID'], 'Quality', n['Quality']
        # to see the whole dictionary:
        # print n

```

The dictionary you get for each network will look something like this:

```

{
  'Pairwise Ciphers (1) ': ' TKIP',
  'Protocol': 'IEEE 802.11g',
  'Extra': 'atim=0',
  'Encryption key': 'on',
  'Bit Rates': '1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s',
  'Frequency': '5.055 GHz',
  'Mode': 'Managed',
  'IE': ' WPA Version 1',
  'Address': '00:1A:2B:66:7B:69',
  'Authentication Suites (1) ': ' PSK',
  'Group Cipher ': ' TKIP',
  'Quality': '4/100',
  'ESSID': 'BEACHHOUSE'
}

```

---

### Post by mo.reina on 2010-10-25
dude wait at least 24 hours before bumping a thread....

anyway are you familiar with regular expressions?  you can use python's re module to parse the output, otherwise, since you're using shell tools anyway, you can use awk to parse the output of iwlist.

```
>>> import re
>>> astring = "ESSID:my network"
>>> re.search(r'ESSID:(.*$)', astring).groups()
('my network',)

```

---

### Post by Crazedpsyc on 2010-10-27
Thanks johnl! that was exactly what I was looking for. I also made a quick bash shell script that just greps for the essid and quality, but printing from that is slow and poorly organized, so I will use your python script (with a few minor modifications) for now

---

