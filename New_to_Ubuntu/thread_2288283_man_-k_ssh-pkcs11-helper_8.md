---
title: "man -k ssh-pkcs11-helper 8"
date: 2015-07-25
forum: New to Ubuntu
---

### Post by maci2 on 2015-07-25
```
root@Skyggen:~# man -k ssh-pkcs11-helper 8
utf8 (7)             - an ASCII compatible multibyte Unicode encoding
__setfpucw (3)       - set FPU control word on i386 architecture (obsolete)
adduser.conf (5)     - configuration file for adduser(8) and addgroup(8) .
armscii-8 (7)        - Armenian character set encoded in octal, decimal, and hexadecimal
btcflash (8)         - firmware flash utility for BTC DRW1008 DVD+/-RW recorder.
c89 (1)              - ANSI (1989) C compiler
c89-gcc (1)          - ANSI (1989) C compiler

cpuid (4)            - x86 CPUID access device
deluser.conf (5)     - configuration file for deluser(8) and delgroup(8) .
Dpkg::Control::Hash (3) - parse and manipulate a block of RFC822-like fields
Dpkg::Control::HashCore (3) - parse and manipulate a block of RFC822-like fields
drand48 (3)          - generate uniformly distributed pseudo-random numbers
drand48_r (3)        - generate uniformly distributed pseudo-random numbers reentrantly
erand48 (3)          - generate uniformly distributed pseudo-random numbers
erand48_r (3)        - generate uniformly distributed pseudo-random numbers reentrantly
i386 (8)             - change reported architecture in new program environment and set personality flags
i686-linux-gnu-addr2line (1) - convert addresses into file names and line numbers.
i686-linux-gnu-ar (1) - create, modify, and extract from archives
i686-linux-gnu-as (1) - the portable GNU assembler.
i686-linux-gnu-c++filt (1) - Demangle C++ and Java symbols.
i686-linux-gnu-cpp (1) - The C Preprocessor


iso_8859_1 (7)       - ISO 8859-1 character set encoded in octal, decimal, and hexadecimal
l
iso_8859_9 (7)       - ISO 8859-9 character set encoded in octal, decimal, and hexadecimal
jrand48 (3)          - generate uniformly distributed pseudo-random numbers
jrand48_r (3)        - generate uniformly distributed pseudo-random numbers reentrantly
koi8-r (7)           - Russian character set encoded in octal, decimal, and hexadecimal
koi8-u (7)           - Ukrainian character set encoded in octal, decimal, and hexadecimal
koi8rxterm (1)       - X terminal emulator for KOI8-R environments
latin1 (7)           - ISO 8859-1 character set encoded in octal, decimal, and hexadecimal


lrand48_r (3)        - generate uniformly distributed pseudo-random numbers reentrantly
mkmanifest (1)       - makes list of file names and their DOS 8+3 equivalent

mrand48_r (3)        - generate uniformly distributed pseudo-random numbers reentrantly
msr (4)              - x86 CPU MSR access device
Net::grin:NS::RR::EUI48 (3pm) - DNS EUI48 resource record
pkcs8 (1ssl)         - PKCS#8 format private key conversion tool
pppd-radattr (8)     - RADIUS utility plugin for pppd (8)
pppd-radius (8)      - RADIUS authentication plugin for pppd (8)
r128 (4)             - ATI Rage 128 video driver
Regexp::Common::URI::RFC1808 (3pm) - - Definitions from RFC1808;
Regexp::Common::URI::RFC2806 (3pm) - - Definitions from RFC2806;
rpl8 (8)             - Firmware loader for DVD drives
rsyslog.conf (5)     - rsyslogd(8) configuration file
sane-artec_eplus48u (5) - SANE backend for the scanner Artec E+ 48U and re-badged models
sane-genesys (5)     - SANE backend for GL646, GL841, GL843, GL847 and GL124 based USB flatbed scanners
sane-gt68xx (5)      - SANE backend for GT-68XX based USB flatbed scanners
sane-hp3900 (5)      - SANE backend for RTS8822 chipset based scanners
sane-plustek (5)     - SANE backend for LM983[1/2/3] based USB flatbed scanners
sane-rts8891 (5)     - SANE backend for rts8891 based scanners
sane-sm3840 (5)      - SANE backend for Microtek scanners with SCAN08 USB chip
sane-stv680 (5)      - SANE backend for STV680 camera's
seed48_r (3)         - generate uniformly distributed pseudo-random numbers reentrantly
sha384sum (1)        - compute and check SHA384 message digest
sk98lin (4)          - Marvell/SysKonnect Gigabit Ethernet driver v6.21
srand48_r (3)        - generate uniformly distributed pseudo-random numbers reentrantly
ssh-pkcs11-helper (8) - ssh-agent helper program for PKCS#11 support
Text::WrapI18N (3pm) - Line wrapping module with support for multibyte,  fullwidth, and combining characters and languages without whitespaces...
tis-620 (7)          - ISO 8859-11 character set encoded in octal, decimal, and hexadecimal
toshsat1800-irdasetup (1) - IrDA setup utility for Toshiba Satellite 1800
utf-8 (7)            - an ASCII compatible multibyte Unicode encoding
utf8 (1)             - quickly change console font and console mode into UTF-8 encoding
uxterm (1)           - X terminal emulator for Unicode (UTF-8) environments
vm86 (2)             - enter virtual 8086 mode
vm86old (2)          - enter virtual 8086 mode
wish8.6 (1)          - Simple windowing shell
x25 (7)              - ITU-T X.25 / ISO-8208 protocol interface.
root@Skyggen:~# 
```

What realy happend on my toshiba satellite C50-B-14z??????

---

### Post by howefield on 2015-07-25
> **maci2 said:**
> What realy happend on my toshiba satellite C50-B-14z??????

It returned an output to your command.

What exactly are you trying to do ?

---

### Post by maci2 on 2015-07-29
Someboody have control on my computer.  I want to finde about that's true........

---

### Post by Lars Noodén on 2015-07-29
> **maci2 said:**
> ```
root@Skyggen:~# man -k ssh-pkcs11-helper 8
... 
```

What realy happend on my toshiba satellite C50-B-14z??????

You ran [man -k](http://manpages.ubuntu.com/manpages/trusty/en/man1/man.1.html) which is the equivalent of [apropos](http://manpages.ubuntu.com/manpages/trusty/en/man1/apropos.1.html).  That searches the built-in manuals, specifically the manual names ( titles ) and descriptions.

---

