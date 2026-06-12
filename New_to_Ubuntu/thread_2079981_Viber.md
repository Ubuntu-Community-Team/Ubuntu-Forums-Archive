---
title: "Viber"
date: 2012-11-02
forum: New to Ubuntu
---

### Post by lizandeen on 2012-11-02
Is Viber available for Ubuntu 12.04?

---

### Post by Linuxisfast on 2012-11-02
Viber is a made for phone app so it currently works on Android and IoS platform.

---

### Post by critin on 2012-11-02
> **lizandeen said:**
> Is Viber available for Ubuntu 12.04?

Some info here.

[https://launchpad.net/ubuntu/+source/viper](https://launchpad.net/ubuntu/+source/viper)

---

### Post by Linuxisfast on 2012-11-03
> **critin said:**
> Some info here.

[https://launchpad.net/ubuntu/+source/viper](https://launchpad.net/ubuntu/+source/viper)

[www.viber.com](www.viber.com)

---

### Post by Viber on 2012-11-11
Hi,

This is a member of the Viber R&D Team!

We are happy to see your interest in our app. :)
Viber at the moment is available only for mobile phone devices, but we have many surprises to come. ;)

Please feel free to let us know your thoughts, questions and comments, we'd be happy to assist.
Thanks,
the Viber Team

---

### Post by resander on 2012-11-11
We have been using Skype with video from UK desk/laptops to keep in touch with friends and family in the East Asian Pacific.

Sometimes the transmission stutters and breaks up and makes communication difficult. Today was such an occasion and someone suggested we try viber from a mobile Android phone instead. Transmission was clear then with no breakups. Would like to have viber on my desktop Ubuntu 12.04 LTS (or 10.04 LTS) too. When will that be available?

---

### Post by Viber on 2012-11-12
> **resander said:**
> We have been using Skype with video from UK desk/laptops to keep in touch with friends and family in the East Asian Pacific.

Sometimes the transmission stutters and breaks up and makes communication difficult. Today was such an occasion and someone suggested we try viber from a mobile Android phone instead. Transmission was clear then with no breakups. Would like to have viber on my desktop Ubuntu 12.04 LTS (or 10.04 LTS) too. When will that be available?

Viber for PC/Mac is something we plan for the future, but we still don't have specific release dates.

Once we have news, we'll make sure to inform our fans out there through our official Facebook page and HelpDesk :)

---

### Post by targetchip on 2013-01-06
[http://youtu.be/YrXL8KrGkm0](http://youtu.be/YrXL8KrGkm0)

you can do it on a pc with the bluestack software but I would also be interested to see if we can do it on ubuntu please.):P

---

### Post by Jydskatomkraft on 2013-03-16
I am also very interested in a ported version for linux!
Integration into Unity Gwibber / Friends will bring completly new use into viber from a workstation :)

---

### Post by gordintoronto on 2013-03-16
> **resander said:**
> We have been using Skype with video from UK desk/laptops to keep in touch with friends and family in the East Asian Pacific.

Sometimes the transmission stutters and breaks up and makes communication difficult. Today was such an occasion and someone suggested we try viber from a mobile Android phone instead. Transmission was clear then with no breakups. Would like to have viber on my desktop Ubuntu 12.04 LTS (or 10.04 LTS) too. When will that be available?

Your transmission problems probably have nothing to do with the program you are using, and everything to do with the data communications or your computer.

When you used Viper on the phone, was it connected by WiFi? If so, your data communications are probably OK.

Skype is a bit of a pig, and likes a fast computer. What CPUs and memory do your computers have? Do you run a temperature monitor?

My wife uses Skype and QQ every day from Toronto to videoconference with friends and family in China, never a problem -- but she's got a really beefy computer.

---

### Post by tellapu on 2013-05-08
Viber for Linux would be great as there is now a Windows & Mac version.

---

### Post by todorakiggg on 2013-05-08
Can Vider be installed with Wine on Ubuntu system?
Did anybody try this?

---

### Post by rhoit on 2013-05-08
viber works for linux! with wine!

---

### Post by mikes-rus on 2013-05-08
yes, it works, but some bugs are peresent.
viber window does not restore after minimize, and sometimes freezes after call transfer

---

### Post by todayalemon on 2013-05-08
i can confirm it works, calls may lag, but i was surprised at how smooth everything works (even things like notification in tray and osd, using gnome). def would be nicer to have a proper version but as temporary solution it's ok!

---

### Post by lukestanley on 2013-05-09
Could anyone say what versions of Wine and Ubuntu it works with? Also if 64 bit or 32 bit?
It fails for me on Ubuntu 11.10 with wine-1.3.28, running XFCE. 
It could be helpful to check the version of the .exe with pev.

You can use this to get version info:
```
cat /etc/issue
wine --version
sudo apt-get install pev
pev ViberSetup.exe

```


When I try installing it it gets a good way through the download then fails with the error shown below:
```
wine ViberSetup.exefixme:wincodecs:JpegDecoder_Frame_GetResolution (0x1adfac,0x31df08,0x31df00): stub
fixme:wincodecs:JpegDecoder_Frame_GetResolution (0x1ae064,0x31df08,0x31df00): stub
fixme:wincodecs:JpegDecoder_Frame_GetResolution (0xc51034,0x31df08,0x31df00): stub
fixme:wininet:InternetCheckConnectionW 
fixme:wininet:InternetCheckConnectionW 
fixme:wininet:InternetCheckConnectionW 
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  53 (X_CreatePixmap)
  Value in failed request:  0x0
  Serial number of failed request:  3290
  Current serial number in output stream:  3302
```

```
pev ViberSetup.exe DOS header:
 Magic number:            0x5a4d (MZ)
 Bytes in last page:        144
 Pages in file:            3
 Relocations:            0
 Size of header in paragraphs:    4
 Minimum extra paragraphs:    0
 Maximum extra paragraphs:    65535
 Initial (relative) SS value:    0
 Initial SP value:        0xb8
 Initial IP value:        0
 Initial (relative) CS value:    0
 Address of relocation table:    0x40
 Overlay number:        0
 OEM identifier:        0
 OEM information:        0
 PE header offset:        0xe0


COFF header:
 Machine:            0x14c - Intel 386 and compatible (32-bits)
 Number of sections:        5
 Date/time stamp:        1270901978 (04/10/2010 at 12:19:38 PM)
 Symbol Table offset:        0
 Number of symbols:        0
 Size of optional header:    0xe0
 Characteristics:        0x103 (00000000000000000000000100000011)
                IMAGE_FILE_RELOCS_STRIPPED
                IMAGE_FILE_EXECUTABLE_IMAGE
                IMAGE_FILE_32BIT_MACHINE


Optional (PE) header:
 Magic number:            0x10b
 Linker major version:        9
 Linker minor version:        0
 Size of CODE section:        0x6800
 Size of DATA section:        0x74000
 Size of BSS section:        0x4200
 Entry point:            0x3415
 Address of CODE section:    0x1000
 Address of DATA section:    0x8000
 Imagebase:            0x400000
 Alignment of sections:        0x1000
 Alignment factor:        512
 Major version of required OS:    5
 Minor version of required OS:    0
 Major version of image:    6
 Minor version of image:    0
 Major version of subsystem:    5
 Minor version of subsystem:    0
 Size of image:            0x302000
 Size of headers:        0x400
 Image file checksum:        0x133f30
 Subsystem required:        0x2
 DLL characteristics:        0x8400
 Size of stack to reserve:    0x100000
 Size of stack to commit:    0x1000
 Size of heap space to reserve:    0x100000
 Size of heap space to commit:    0x1000
 Data-dictionary entries:    16


Sections:
 Name:                .text
 Virtual size:            0x671c
 Virtual address:        0x1000
 Data size:            0x6800
 Data offset:            0x400
 Characteristics:        0x60000020


 Name:                .rdata
 Virtual size:            0x19d6
 Virtual address:        0x8000
 Data size:            0x1a00
 Data offset:            0x6c00
 Characteristics:        0x40000040


 Name:                .data
 Virtual size:            0x7139c
 Virtual address:        0xa000
 Data size:            0x200
 Data offset:            0x8600
 Characteristics:        0xc0000040


 Name:                .ndata
 Virtual size:            0x261000
 Virtual address:        0x7c000
 Data size:            0
 Data offset:            0
 Characteristics:        0xc0000080


 Name:                .rsrc
 Virtual size:            0x243b0
 Virtual address:        0x2dd000
 Data size:            0x24400
 Data offset:            0x8800
 Characteristics:        0x40000040



```

Any thoughts?

Thanks!

---

### Post by Bucky Ball on 2013-05-09
Why not use Skype which is in the repos already and works flawlessly and avoid jumping through Wine hoops? Is there some special feature of Viber which Skype doesn't have or is it just what the people you want to communicate with use right now?

---

### Post by DuckHook on 2013-05-09
> **Bucky Ball said:**
> Why not use Skype which is in the repos already and works flawlessly and avoid jumping through Wine hoops?

Perhaps the more alternatives to Skype, the better. I expect to see MS come out with an "enhancement" any day now that breaks Skype usage on anything but Windows.

---

### Post by Bucky Ball on 2013-05-09
> **DuckHook said:**
>  I expect to see MS come out with an "enhancement" any day now that breaks Skype usage on anything but Windows.

Since when did MS own Skype? Am I missing something?

---

### Post by haqking on 2013-05-09
> **Bucky Ball said:**
> Since when did MS own Skype? Am I missing something?

since 2011, for about $9 billion if i recall

Edit: well 8.5 billion  [http://www.bbc.co.uk/news/business-13343600](http://www.bbc.co.uk/news/business-13343600)

---

### Post by MHK99 on 2013-05-09
In some countries Skype is not allowed but Viber is. Maybe because it will load on iPhone?

---

### Post by Viber on 2013-05-10
Hi all,
I'm an official representative of Viber here in UbuntuForums.

We are planning Viber for Linux! We're working on it these days, but we're not yet sure when exactly it will be released.
When we have news, we'll let you know of course :)

Best regards,
the Viber Team.

---

### Post by Bucky Ball on 2013-05-10
> **lizandeen said:**
> Is Viber available for Ubuntu 12.04?

> **Viber said:**
> Hi all,
I'm an official representative of Viber here in UbuntuForums.

We are planning Viber for Linux! We're working on it these days, but we're not yet sure when exactly it will be released.
When we have news, we'll let you know of course :)

Best regards,
the Viber Team.
 

Thread solved and closed. The question is answered directly by a representative of Viber and nothing more to be said here. Please start a new thread with a descriptive title in the appropriate sub-forum regarding all other problems/issues/questions about Viber or anything else . ;)

---

