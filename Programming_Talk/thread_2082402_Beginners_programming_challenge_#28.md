---
title: "Beginners programming challenge #28"
date: 2012-11-09
forum: Programming Talk
---

### Post by Bachstelze on 2012-11-09
Seeing as challenge #27 is now over 4 months old with no #28 in sight, and that I have (what I think is) an interesting idea for a new challenge, I have taken the liberty of creating it myself. As you will see, it will help you develop a somewhat different (but no less important) set of skills than most previous challenges. So without further ado...

_[SIZE=4][COLOR=Red]Welcome to the 28th Beginners programming challenge.[/COLOR][/SIZE]_
Most previous challenges asked you to work with text or numeric data. By contrast, this one will ask you to work with binary data. I also wanted to make it relevant, so you will work with real-world data. Namely, you will implement an **ARP packet analyser**. Don't worry, it's less scary than it sounds. ;) First, some background.


_**Background: The ARP Protocol**_

(To simplify the discussion, we only consider two machines that are in the same LAN segment, meaning they can communicate directly, without any router between them.)

Most people know that machines on a network are identified by an IP address. A bit less known is that machines are also identified by a hardware (or MAC) address. You can see it for example with the command [font=monospace]ifconfig[/font]:

```

firas@aoba ~ % ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:25:00:48:09:8c  
          inet addr:192.168.1.19  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:ff:fe48:98c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:93066 errors:0 dropped:0 overruns:0 frame:38438
          TX packets:50786 errors:19 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:130634360 (130.6 MB)  TX bytes:4352298 (4.3 MB)
          Interrupt:23 

```

Here the IP address of my machine is [font=monospace]192.168.1.19[/font], and its hardware address is [font=monospace]00:25:00:48:09:8c[/font]. Generally, when a user wants to use the network, they specify only the IP address of the machine they want to communicate with. I am not going to dwelve into the reason for having two addresses (IP and hardware) in the first place, but the fact is that in order to communicate with another machine on the network using the IP protocol, a machine needs to know both its IP and hardware addresses. The IP address is specified by the user, but the hardware address is not, so how does a machine obtain the hardware address of the machine it wants to communicate with? This is where the ARP (Address Resolution Protocol) protocol kicks in.

Remember that my machine has IP address [font=monospace]192.168.1.19[/font] and hardware address [font=monospace]00:25:00:48:09:8c[/font], let's call it machine A. Suppose I want to send an IP packet to the machine with IP address [font=monospace]192.168.1.1[/font], let's call it machine B. First, machine A needs to acquire the hardware address of machine B. In order to do that, it simply sends a packet to *every* other machine on the network, saying in effect: "Hi, I am [font=monospace]00:25:00:48:09:8c[/font], I have IP address [font=monospace]192.168.1.19[/font], and I would like to know who here has IP address [font=monospace]192.168.1.1[/font]." Assuming there actually is a machine on the network that has IP address [font=monospace]192.168.1.1[/font], it will reply with a packet stating its hardware address, saying in effect: "Hi, I am [font=monospace]38:46:08:d1:83:97[/font], and it is I who has IP address [font=monospace]192.168.1.1[/font]." Then machine A has all the information it needs in order to send an IP packet to machine B. Also, it will store the hardware address of machine B in its *ARP table*, so as to not perform an ARP lookup every time. You can see your machine's ARP table with the aptly named [font=monospace]arp[/font] command:

```
firas@aoba ~ % arp -n
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.1.1              ether   38:46:08:d1:83:97   C                     eth1

```


The format of an ARP packet is defined in several RFCs, but the [Wikipedia article](http://en.wikipedia.org/wiki/Address_Resolution_Protocol) (especially section 2, *Packet structure*) will be sufficient for this task. ARP packets are encapsulated in Ethernet frames, so you will also need the [Ethernet frame](http://en.wikipedia.org/wiki/Ethernet_frame) Wikipedia article.


_**Task**_

Your task is simply to write a program that will read a copy of an ARP packet, and print the information it contains, such as whether the packet is a request or reply packet, and the addresses of the two machines involved. Sample request and reply packets are available in the attached archive. The files [font=monospace]request.bin[/font] and [font=monospace]reply.bin[/font] are the raw request and reply packets, that your program will take as input. The files suffixed [font=monospace].hexdump[/font] are hexadecimal dumps of the corresponding packets in text format, for easier visualisation. (If you would like to capture packets yourself, see post #4 below.)

Before you start coding, you should get familiar with the structure of an ARP packet (and of an Ethernet frame that contains one). To that end you can simply look at the hexdumps in your favourite text editor, or, even better, open them in Wireshark. Wireshark is available in the Ubuntu repositories (package [font=monospace]wireshark[/font]), simply run it, cick File > Import, and open the hexdump file of your choice, keeping all the other options at their default values. Examining the packets in Wireshark will let you see exactly where in the packet each piece of information is stored, for example:

[[IMG]http://imageshack.us/a/img842/6445/wireshark.th.png[/IMG]](http://imageshack.us/a/img842/6445/wireshark.png)

You can assume that all input packets are correctly formatted. Also, I have included the encapsulating Ethernet frame only to make opening the packets in Wireshark easier, you can just skip over the Ethernet data in your program.


_**Cookie points**_

Cookie points will be awarded for the following extras:

[LIST=1]
[*] Drop the assumption that all packets are correctly formatted, and handle incorrect packets gracefully.
[*] Also print the information contained in the Ethernet frames.
[*] Make your program support both input formats (raw and hexdump in the same format as in the provided archive).
[/LIST]


_**Disqualified Entries**_

Any overly obfuscated code will be immediately disqualified without     account for programmers skill. Please remember that these challenges are for beginners and therefore the code should be easily readable and well commented.

Any non-beginner entries will not be judged. Please use common sense when posting code examples. Please do not give beginners a copy paste solution before they have had a chance to try this for themselves.


_**Assistance**_

If you require any help with this challenge please do not hesitate to come and chat to the development focus group. We have a channel on irc.freenode.net #ubuntu-beginners-dev
Or you can pm me

Have fun,
Happy coding

Bachstelze

---

### Post by nathan.the.sane on 2012-11-09
[http://goo.gl/0UDto](http://goo.gl/0UDto) (the code)

A sample run with the example packets:
```
nfm@FX6840:~/dev/arp$ gcc -Wall -o arp main.c 
nfm@FX6840:~/dev/arp$ ./arp 
ETHERNET HEADER
--------------------
Destination MAC Address: ff:ff:ff:ff:ff:ff
Source MAC Address: ca:01:33:65:00:08
Ethertype: 0x0806

ARP PACKET
------------------
Hardware Type: 1
Protocol Type: 0x0800
Packet Type: REQUEST
Sender MAC Address: ca:01:33:65:00:08
Sender Protocol Address: 192.168.1.1
Target MAC Address: 00:00:00:00:00:00
Target Protocol Address: 192.168.1.2
nfm@FX6840:~/dev/arp$ rm packet.bin 
nfm@FX6840:~/dev/arp$ cp reply.bin packet.bin
nfm@FX6840:~/dev/arp$ ./arp 
ETHERNET HEADER
--------------------
Destination MAC Address: ca:01:33:65:00:08
Source MAC Address: cc:03:33:76:00:00
Ethertype: 0x0806

ARP PACKET
------------------
Hardware Type: 1
Protocol Type: 0x0800
Packet Type: REPLY
Sender MAC Address: cc:03:33:76:00:00
Sender Protocol Address: 192.168.1.2
Target MAC Address: ca:01:33:65:00:08
Target Protocol Address: 192.168.1.1
```I think it could be improved, but I'm getting lazy. Also I'm trying to learn Dvorak typing at the same time so typing the code is frustrating.  What do you think? I can handle criticism :p

---

### Post by Bachstelze on 2012-11-10
On lines 45 and 46 you have a semicolon that should not be there, I assume it's a typo.

Compiling with all warnings enabled gives:

```
firas@ichiyoh arp % gcc -std=c99 -pedantic -Wall -Wextra -o arptool arptool.c 
arptool.c:31: warning: unused parameter 'argc'
arptool.c:31: warning: unused parameter 'argv'
arptool.c: In function 'getData':
arptool.c:81: warning: comparison is always false due to limited range of data type
arptool.c:91: warning: comparison is always false due to limited range of data type

```

This is a common mistake: fgetc() returns an int, you need to check that it is not EOF *before* storing it in a variable of type unsigned char.

Also, hardcoding the input file path is not really good practice, you should take it as a command-line argument. And you need to check that the input file was opened successfully, otherwise your program will segfault.

---

### Post by Bachstelze on 2012-11-10
For those interested, here's how to capture ARP (and other) packets for yourself with Wireshark:

1. Install Wireshark if you haven't installed it already. By default, only root can capture traffic, which is inconvenient, so it is better to allow yourself to do it (I assume Debian/Ubuntu, see [here](http://wiki.wireshark.org/CaptureSetup/CapturePrivileges) for other OSes). Run

```
sudo dpkg-reconfigure wireshark-common
```

and choose "Yes". Add yourself to the [font=monospace]wireshark[/font] group, then log out and log back in.

2. Find a machine on your LAN that is not in your ARP table. If there is none, delete an entry from it with

```
sudo arp -d <IP_ADDRESS>
```

3. Run Wireshark. In the "Interface List" panel, click the interface you want to capture on.

[[IMG]http://imageshack.us/a/img688/8418/wireshark1.th.png[/IMG]](http://imageshack.us/a/img688/8418/wireshark1.png)

Then try to send an IP packet to the other machine, with e.g. [font=monospace]ping[/font]:

[[IMG]http://imageshack.us/a/img820/4953/wireshark2.th.png[/IMG]](http://imageshack.us/a/img820/4953/wireshark2.png)

4. To save a packet in binary form (to use in your program), select a packet and click the "Frame" header so that all the bytes of the packet are selected:

[[IMG]http://imageshack.us/a/img31/5363/wireshark3.th.png[/IMG]](http://imageshack.us/a/img31/5363/wireshark3.png)

Then click File > Export > Selected packet bytes.

5. To create a hexdump of your packet in a format similar to the ones I provided, open a terminal and do:

```
od -Ax -tx1 -v packet.bin > packet.bin.hexdump
```

---

### Post by nathan.the.sane on 2012-11-10
> **Bachstelze said:**
> On lines 45 and 46 you have a semicolon that should not be there, I assume it's a typo.


Hmm, it's not there in my original file, must have been a copypasta glitch. :confused:

Thanks for the feedback! I would never have thought about the EOF thing.

---

### Post by Bachstelze on 2012-11-12
356 views and only one entry, I thought it would be more popular than that...

---

### Post by Odexios on 2012-11-12
> **Bachstelze said:**
> 356 views and only one entry, I thought it would be more popular than that...
I'm not having a lot of free time, but the challenge is really interesting and seems pretty doable. I'll surely try it if I can; I'm trying to learn Caml these days, might give it a shot with that.

Even if I don't I've learned something new about ARP today, so, well, thank you for the input anyway.

---

### Post by Odexios on 2012-11-12
I have a question about the Ethernet Frame. It's the first time I look at this kind of subjects, so it might be a dumb question.

As far as I can understand, the endiannes is the way a binary number is represented. A big endian representation has the most significant digit coming first (or left), and a little endian last (or right). The usual notation for a binary number written by hand is big endian.

The ethernet frame is, as far as I discovered, big endian on the bytes, and little endian on the bits; does that mean that the decimal number 270 would be represented as 0x80 0x70, instead of 0x01 0x0e?

If so, is the payload represented in the same way? I mean, if in the payload all I wanted to send was 0x01 0x0e, would it be represented as 0x80 0x70?

---

### Post by Bachstelze on 2012-11-12
Bit-endianness does not matter here because we read entire bytes, not bits, so you can consider that the Ethernet frame is just an array of bytes, that appear in the same order and have the same value that what you see when you do a hexdump. Ethernet frames are only transmitted bit-little-endian "on the wire", at each end the bytes are reconstructed and bit-endianness ceases to matter.

---

### Post by Odexios on 2012-11-12
> **Bachstelze said:**
> Bit-endianness does not matter here because we read entire bytes, not bits, so you can consider that the Ethernet frame is just an array of bytes, that appear in the same order and have the same value that what you see when you do a hexdump. Ethernet frames are only transmitted bit-little-endian "on the wire", at each end the bytes are reconstructed and bit-endianness ceases to matter.Perfect. Thanks!

---

### Post by Tony Flury on 2012-11-17
I have an idea for a data driven protocol interpreter in python, but I wont post any code since strictly speaking I don't feel i am a beginner.

---

### Post by kevinharper on 2012-11-17
Great challenge Bachstelze.

I don't have any free time at the moment but am hoping that this will change in a few weeks. I think I'll do the programming challenges over winter. Hopefully I'll get to yours before school starts back up in January. :)

---

### Post by fdrake on 2012-12-23
just asking why the old Programming Challenges are closed. some ppl weren't around at the time and the challenges are a good way to keep ppl motivated in trying .. or you expect a begginer to start from challenge 28?

---

### Post by Bachstelze on 2012-12-23
> **fdrake said:**
> just asking why the old Programming Challenges are closed. some ppl weren't around at the time and the challenges are a good way to keep ppl motivated in trying .. or you expect a begginer to start from challenge 28?

The old challenges are closed in the sense that a winner has already been chosen. However, the threads are not closed, you are welcome to try them and post your solution in the corresponding thread if you want comments. :)

---

### Post by fdrake on 2012-12-23
> **Bachstelze said:**
> The old challenges are closed in the sense that a winner has already been chosen. However, the threads are not closed, you are welcome to try them and post your solution in the corresponding thread if you want scomments. :)

gotcha ya!

---

### Post by fdrake on 2012-12-23
> **fdrake said:**
> gotcha ya!

actually some threads are closed since I cannot post on them. like #1 . that's fine I'll look for the open ones.

---

### Post by Bachstelze on 2012-12-23
Oh yes, #1 is closed. You can use the report button to ask for a reopen, or post [here](http://ubuntuforums.org/forumdisplay.php?f=123).

---

### Post by CoyleTrydan on 2013-01-04
Thanks for putting together this challenge, I'm learning a lot! I'm afraid I'm in way over my head though, and was hoping somebody could point me in the right direction.

I feel like I have a decent handle now on the structure of the packets - I've looked at them both in wireshark and the hexdump in a text editor. I have a plan for how to process and display the information once I get it into my program (this part of the program is not written yet).

Where I'm running into trouble is actually getting the contents of the raw .bin files into my program. I'm not even sure what information they have in them, so I'm not certain how to proceed. I do notice that I can use "readlines()" to get a string of the hex octets, but "read()" and "readline()" both give unprintable characters. I haven't been able to make sense of why this is, although I imagine it has something to do with the information that lays out the numbering of the packet structure (on the far left of the hexdump file in gedit/wireshark)?

This is the hex string I'm getting:
```

['\xff\xff\xff\xff\xff\xff\xca\x013e\x00\x08\x08\x06\x00\x01\x08\x00\x06\x04\x00\x01\xca\x013e\x00\x08\xc0\xa8\x01\x01\x00\x00\x00\x00\x00\x00\xc0\xa8\x01\x02\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00']

```I realize this corresponds to the octets in the packet, although I'm not certain why I'm getting "x013e" which appears to correspond to "01 33 65".

Also, even getting the hex string, I can't seem to process it in any way. I'm trying to take the hex and display it in decimal, but keep getting errors. I've commented out my two latest attempts, one of which includes the struct method. I've read the docs for that over and over, and am starting to grasp a bit of it, but it's way over my head. Am I even heading down the right path with struct?

I've attached my program so far, it's far from complete, I'm just trying to print the contents of the packet file right now. I'm very new to Python, so I appreciate any other pointers on my code as well. I know I have a lot of questions, but if someone could just point me in the right direction, I'm not afraid of doing some more searching/reading. :) Thanks!

[php]
#!/usr/bin/python
from __future__ import print_function
from struct import *
import sys

def getFile():
    #I bet there's a cleaner way to do this? Pass file path after "-f "
    file = sys.argv[(sys.argv.index("-f")) + 1]
    return(file)

def getBits(file):
    f = open(file, "r")
    data = str(f.readlines())
    #Why does only readlines work here? What is the other "gibberish" in the file?
    f.close()
    #decData = unpack('30H', data)
    #decData = int(data, 0)
    return(decData)

def main():
    file = getFile()
    data = getBits(file)
    print(data)

main()
[/php]

---

### Post by debd on 2013-01-07
@Bachstelze Very interesting challenge. I'll code it tonight and make a post tomorrow possibly. And, btw, winner of #27 hasn't been announced yet.. although there's only two entries (probably)

====

I've got a question, Is the arp packet capsuled in the ethernet frame as a payload or is it a stand alone packet?

---

### Post by CoyleTrydan on 2013-01-28
Alright, it took long enough, but I think I've got it. :) It isn't the most elegant solution perhaps (especially formatting the MAC and IP addresses...) but it seems to work.

I'd appreciate any feedback! I've learned a lot through this exercise, and I'm sure I can learn plenty more from critiques on how I did it.

[php]
#!/usr/bin/python
from __future__ import print_function
import argparse
import binascii


def getBits(file):
    packet = open(file, "r")
    data = binascii.hexlify(packet.read())    
    packet.close()
    return(data)

def processPacket(data):
    #First 14 octets of ethernet frame are ethernet header
    #Realized that Preamble and Start of Frame Delimiter aren't seen on OSI Level 2
    ether0x = data[0:28]

    macDest = ether0x[0:12]
    macSrc = ether0x[12:24]
    type = ether0x[24:28]

    macDestination = str(macDest[0:2]) + ':' + str(macDest[2:4]) + ':' + str(macDest[4:6]) + ':' + str(macDest[6:8]) + ':' + str(macDest[8:10]) + ':' +  str(macDest[10:12])
    macSource = str(macSrc[0:2]) + ':' + str(macSrc[2:4]) + ':' + str(macSrc[4:6]) + ':' + str(macSrc[6:8]) + ':' + str(macSrc[8:10]) + ':' +  str(macSrc[10:12])

    print()
    print("[+] Ethernet Header")
    print(" * Destination MAC Address: " + str(macDestination))
    print(" * Source MAC Address: " + str(macSource))
    print(" * EtherType: 0x" + str(type))

    #Next is the ARP packet, 28 octets
    arp0x = data[28:84]

    htype = arp0x[0:4]
    ptype = arp0x[4:8]
    hlen = arp0x[8:10]
    plen = arp0x[10:12]
    oper = arp0x[12:16]
    sha = arp0x[16:28]
    spa = arp0x[28:36]
    tha = arp0x[36:48]
    tpa = arp0x[48:56]

    if int(oper, 16) == 1:
        oper = "REQUEST"
    elif int(oper, 16) == 2:
        oper = "REPLY"

    senderProtocol = str(int(spa[0:2], 16)) + '.' + str(int(spa[2:4], 16)) + '.' + str(int(spa[4:6], 16)) + '.' + str(int(spa[6:8], 16))
    targetProtocol = str(int(tpa[0:2], 16)) + '.' + str(int(tpa[2:4], 16)) + '.' + str(int(tpa[4:6], 16)) + '.' + str(int(tpa[6:8], 16))

    senderHardware = str(sha[0:2]) + ':' + str(sha[2:4]) + ':' + str(sha[4:6]) + ':' + str(sha[6:8]) + ':' + str(sha[8:10]) + ':' +  str(sha[10:12])
    targetHardware = str(tha[0:2]) + ':' + str(tha[2:4]) + ':' + str(tha[4:6]) + ':' + str(tha[6:8]) + ':' + str(tha[8:10]) + ':' +  str(tha[10:12])
    
    print()
    print("[+] ARP Packet")
    print(" * Hardware Type: " + str(int((htype), 16)))
    print(" * Protocol Type: 0x" + str(ptype))
    print(" * Hardware Length: " + str(int((hlen), 16)))
    print(" * Protocol Length: " + str(int((plen), 16)))
    print(" * Operation: " + str(oper))
    print(" * Sender Hardware Address: " + str(senderHardware))
    print(" * Sender Protocol Address: " + str(senderProtocol))
    print(" * Target Hardware Address: " + str(targetHardware))
    print(" * Target Protocol Address: " + str(targetProtocol))

    return

def main():
    parser = argparse.ArgumentParser()
    parser.add_argument("file", help="Path to packet file")
    args = parser.parse_args()

    file = args.file
    data = getBits(file)
    processPacket(data)

main()
[/php]

---

### Post by Bachstelze on 2013-01-29
> **debd said:**
> 
I've got a question, Is the arp packet capsuled in the ethernet frame as a payload or is it a stand alone packet?

What do you mean by "payload"?

---

### Post by CoyleTrydan on 2013-01-29
> **Bachstelze said:**
> What do you mean by "payload"?

The table showing the structure of an Ethernet frame includes a "payload" section, where in this case the ARP packet would be. 

To the initial question: Yes the provided example files include the Ethernet frame as well as the ARP packet payload.

---

### Post by Bachstelze on 2013-01-29
> **CoyleTrydan said:**
> The table showing the structure of an Ethernet frame includes a "payload" section, where in this case the ARP packet would be. 

To the initial question: Yes the provided example files include the Ethernet frame as well as the ARP packet payload.

The initial question doesn't mention the example files, why do you think I asked for clarification? Also, I can read, thank you very much.

---

### Post by CoyleTrydan on 2013-01-29
:???: Just trying to help answer a question. Didn't mean to step on any toes...

---

### Post by Bachstelze on 2013-01-29
> **CoyleTrydan said:**
> :???: Just trying to help answer a question. Didn't mean to step on any toes...

With an implication that I hadn't read the Wikipedia page I myself gave a link to... Anyway, what debd meant may or may not be what you assumed it to be, so let's wait for him to clarify, shall we?

---

### Post by Bachstelze on 2013-01-29
And about your program, Python is not my forte, but it looks very good. One odd thing, instead of importing __future__, why not use Python 3 altogether?

One thing you could do to improve address formatting is to make separate functions that take the "raw" address as argument and return it as a formatted string.

> **CoyleTrydan said:**
> Alright, it took long enough, but I think I've got it. :) It isn't the most elegant solution perhaps (especially formatting the MAC and IP addresses...) but it seems to work.

I'd appreciate any feedback! I've learned a lot through this exercise, and I'm sure I can learn plenty more from critiques on how I did it.

[php]
#!/usr/bin/python
from __future__ import print_function
import argparse
import binascii


def getBits(file):
    packet = open(file, "r")
    data = binascii.hexlify(packet.read())    
    packet.close()
    return(data)

def processPacket(data):
    #First 14 octets of ethernet frame are ethernet header
    #Realized that Preamble and Start of Frame Delimiter aren't seen on OSI Level 2
    ether0x = data[0:28]

    macDest = ether0x[0:12]
    macSrc = ether0x[12:24]
    type = ether0x[24:28]

    macDestination = str(macDest[0:2]) + ':' + str(macDest[2:4]) + ':' + str(macDest[4:6]) + ':' + str(macDest[6:8]) + ':' + str(macDest[8:10]) + ':' +  str(macDest[10:12])
    macSource = str(macSrc[0:2]) + ':' + str(macSrc[2:4]) + ':' + str(macSrc[4:6]) + ':' + str(macSrc[6:8]) + ':' + str(macSrc[8:10]) + ':' +  str(macSrc[10:12])

    print()
    print("[+] Ethernet Header")
    print(" * Destination MAC Address: " + str(macDestination))
    print(" * Source MAC Address: " + str(macSource))
    print(" * EtherType: 0x" + str(type))

    #Next is the ARP packet, 28 octets
    arp0x = data[28:84]

    htype = arp0x[0:4]
    ptype = arp0x[4:8]
    hlen = arp0x[8:10]
    plen = arp0x[10:12]
    oper = arp0x[12:16]
    sha = arp0x[16:28]
    spa = arp0x[28:36]
    tha = arp0x[36:48]
    tpa = arp0x[48:56]

    if int(oper, 16) == 1:
        oper = "REQUEST"
    elif int(oper, 16) == 2:
        oper = "REPLY"

    senderProtocol = str(int(spa[0:2], 16)) + '.' + str(int(spa[2:4], 16)) + '.' + str(int(spa[4:6], 16)) + '.' + str(int(spa[6:8], 16))
    targetProtocol = str(int(tpa[0:2], 16)) + '.' + str(int(tpa[2:4], 16)) + '.' + str(int(tpa[4:6], 16)) + '.' + str(int(tpa[6:8], 16))

    senderHardware = str(sha[0:2]) + ':' + str(sha[2:4]) + ':' + str(sha[4:6]) + ':' + str(sha[6:8]) + ':' + str(sha[8:10]) + ':' +  str(sha[10:12])
    targetHardware = str(tha[0:2]) + ':' + str(tha[2:4]) + ':' + str(tha[4:6]) + ':' + str(tha[6:8]) + ':' + str(tha[8:10]) + ':' +  str(tha[10:12])
    
    print()
    print("[+] ARP Packet")
    print(" * Hardware Type: " + str(int((htype), 16)))
    print(" * Protocol Type: 0x" + str(ptype))
    print(" * Hardware Length: " + str(int((hlen), 16)))
    print(" * Protocol Length: " + str(int((plen), 16)))
    print(" * Operation: " + str(oper))
    print(" * Sender Hardware Address: " + str(senderHardware))
    print(" * Sender Protocol Address: " + str(senderProtocol))
    print(" * Target Hardware Address: " + str(targetHardware))
    print(" * Target Protocol Address: " + str(targetProtocol))

    return

def main():
    parser = argparse.ArgumentParser()
    parser.add_argument("file", help="Path to packet file")
    args = parser.parse_args()

    file = args.file
    data = getBits(file)
    processPacket(data)

main()
[/php]

---

### Post by CoyleTrydan on 2013-01-29
Can we back up here please? I really didn't mean to imply that you hadn't read anything, I'm sorry if it came across that way.  I had wondered the same thing (regarding the Ethernet frame) at first myself, so I thought I'd be able to help debd out. 
It really isn't necessary to be so harsh with me, I'm new to the community and trying to be helpful in the tiny ways I'm able - I don't see how my post was offensive. However, your response has really discouraged me from offering input.

Thanks for the feedback about my program, I appreciate it. Yes, I'm planning on making the jump to Python 3 before long, the reason I don't is I'm so new to the language, and most tutorials and discussions so far seem to still use 2.6 or 2.7. I have heard one of the biggest annoyances when switching over to 3 is the print_function, so I figured I'd go ahead and learn it with that in place. I'm not familiar with all the changes though, so I don't want to make the jump and then have tutorials not work.

Functions to format the addresses is a good idea, I may change that. Are there any overarching programming philosophies regarding when a job is too small to warrant its own function, or is that more of a stylistic decision?

---

### Post by horizons187 on 2013-02-01
> **CoyleTrydan said:**
> Can we back up here please? I really didn't mean to imply that you hadn't read anything, I'm sorry if it came across that way.  I had wondered the same thing (regarding the Ethernet frame) at first myself, so I thought I'd be able to help debd out. 
It really isn't necessary to be so harsh with me, I'm new to the community and trying to be helpful in the tiny ways I'm able - I don't see how my post was offensive. However, your response has really discouraged me from offering input.

Thanks for the feedback about my program, I appreciate it. Yes, I'm planning on making the jump to Python 3 before long, the reason I don't is I'm so new to the language, and most tutorials and discussions so far seem to still use 2.6 or 2.7. I have heard one of the biggest annoyances when switching over to 3 is the print_function, so I figured I'd go ahead and learn it with that in place. I'm not familiar with all the changes though, so I don't want to make the jump and then have tutorials not work.

Functions to format the addresses is a good idea, I may change that. Are there any overarching programming philosophies regarding when a job is too small to warrant its own function, or is that more of a stylistic decision?

From what I can tell it's almost always better to use a function unless you're writing a program that literally does one thing. (i.e. the beer song example from challenge 1)

---

### Post by Bachstelze on 2013-02-01
> **CoyleTrydan said:**
> 
Functions to format the addresses is a good idea, I may change that. Are there any overarching programming philosophies regarding when a job is too small to warrant its own function, or is that more of a stylistic decision?

A good rule of thumb is: if you have to write the same code more than once in your program, make a function for it. Writing the same code several times is called "code duplication", and the reasons why it's a bad thing are amply documented (just Google it).

---

### Post by trent.josephsen on 2013-02-01
Another good rule of thumb is that most functions should fit in a screenful of text. If you have to page back and forth multiple times to view the entire function, you very easily lose track of the big picture. Breaking a small chunk of code off into its own subroutine is cheap; maintaining a function that's 1000 lines long is not.

---

### Post by r-senior on 2013-02-01
Not a beginner submission, but they seem few and far between now so here's a little Java solution. Functions you say? Functions (or methods) aplenty here!

I've left all classes in the default package to make compiling it easier without a Java IDE. I suppose I could have used java.net.InetAddress to format the IP address but I was writing the MAC address formatter anyway. Note the .bin filenames need to be passed on the command line -- it doesn't check and display a usage message. :oops:

Here's a compile and test run:
```
$ ls
ARPPacket.java  Driver.java  EthernetFrame.java  NetDump.java  reply.bin  request.bin
$ javac *.java
$ java Driver request.bin
request.bin

Ethernet Header
---------------
Source MAC Address: ca:01:33:65:00:08
Destination MAC Address: ff:ff:ff:ff:ff:ff
Ethernet Frame Type: 0x0806

ARP Packet
----------
Hardware Type: 0x0001
Protocol Type: 0x0800
Hardware Size: 0x06
Protocol Size: 0x04
Opcode: 0x0001
Sender MAC Address: ca:01:33:65:00:08
Sender IP Address: 192.168.1.1
Target MAC Address: 00:00:00:00:00:00
Target IP Address: 192.168.1.2
```

---

### Post by Bodsda on 2013-04-14
Morning all, it's great to see people stepping in to keep these challenges going. Now, we haven't had a reply to this thread for quite a while, and I've been unable to get in touch with Bachstelze. We also only had 1 beginner entry, which kind of makes judging relatively easy :)
Despite this, the entry in question displayed good use of functions, readable code and although the comments were a bit thin they were used correctly; by that I mean they were used to tell the reader why something was being done, not how something was being done.

The winner is. 
.
.
.
***[CoyleTrydan]("http://ubuntuforums.org/member.php?u=1438480")***

Congratultations, I look froward to seeing the next challenge.

Good work from everyone,
Happy coding!
Bodsda,
Ubuntu Beginners Team

---

### Post by Bachstelze on 2013-04-14
> **Bodsda said:**
> and I've been unable to get in touch with Bachstelze.

Oh, sorry about that, I'm not visiting the forum much these days, and I don't get email notifications when I have a PM...

---

### Post by CoyleTrydan on 2013-04-14
Cool! Thanks Bachstelze for putting this challenge together. Though I struggled at times to figure some parts out,  it really taught me some useful stuff, and I enjoyed it a great deal. Thank you Bodsda for your kind words about my entry. :)

I'm not sure I'm really qualified to put together the next challenge, but I'll give it a bit of thought and talk with Bodsda some privately.

---

