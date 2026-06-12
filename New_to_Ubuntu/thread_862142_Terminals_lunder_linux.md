---
title: "Terminals lunder linux??"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by ra2008 on 2008-07-17
hi, do u know any terminal programs work for linux except cutecom and minicom?
thanks

---

### Post by hyper_ch on 2008-07-17
termina program for ....?

---

### Post by nowshining on 2008-07-17
linux comes with a terminal already - applications - accessories I believe and u also got the ttys in ctrl+alt+f1-f7 - f7 or so is the GUI, ie: to come back to the GUI from a tty. :)

---

### Post by ra2008 on 2008-07-17
> **hyper_ch said:**
> termina program for ....?
I mean anything equivalent to Hyperterminal in windows?

---

### Post by sisco311 on 2008-07-17
gtkterm?
>  aptitude show gtkterm 
Package: gtkterm
State: not installed
Version: 0.99.5-1ubuntu2
Priority: optional
Section: universe/comm
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 266k
Depends: libatk1.0-0 (>= 1.13.1), libc6 (>= 2.5-0ubuntu1), libcairo2 (>= 1.4.0),
         libfontconfig1 (>= 2.4.0), libglib2.0-0 (>= 2.12.9), libgtk2.0-0 (>=
         2.10.3), libpango1.0-0 (>= 1.16.1), libvte9 (>= 1:0.16.0), libx11-6,
         libxcursor1 (> 1.1.2), libxext6, libxfixes3 (>= 1:4.0.1), libxft2 (>
         2.1.1), libxi6, libxinerama1, libxrandr2 (>= 2:1.2.0), libxrender1
Description: A simple GTK+ serial port terminal
 gtkterm is a simple GTK+ terminal used to communicate with the serial port. 
 
 Its features : 
 
 * Serial port terminal window 
 * Serial port setup (speed, parity, bits, stopbits, flow control) 
 * Using the termios API 
 * Possible to send a file (only RAW data, no protocol) 
 * End of line delay while sending a file 
 * Special character wait before next line while sending a file 
 * Possible to toggle control lines manually (DTR, CTS) 
 * Also reads the state of control lines (RTS, CD, DSR, RI) 
   
 Author:   Julien Schmitt <julien@jls-info.com>
 Homepage: [http://www.jls-info.com/julien/linux/](http://www.jls-info.com/julien/linux/)


seyon
> aptitude show seyon 
Package: seyon
State: not installed
Version: 2.20c-27
Priority: extra
Section: universe/comm
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 397k
Depends: libc6 (>= 2.6.1-1), libice6 (>= 1:1.0.0), libsm6, libx11-6, libxaw7,
         libxext6, libxmu6, libxpm4, libxt6, xterm | x-terminal-emulator,
         debconf (>= 1.2.9) | debconf-2.0
Suggests: lrzsz, ckermit
Description: Full-featured native X11 communications program
 Seyon is a complete full-featured modem communications package for the X Window
 System. Some of its features are: 
 * dialing directory 
 * terminal emulation (DEC VT02, Tektronix 4014 and ANSI) 
 * script language 
 * Zmodem


---

### Post by oldos2er on 2008-07-17
I know nothing of "Hyperterminal," but zsh is a nice replacement for bash (if that's what you're asking).

---

### Post by stchman on 2008-07-17
> **ra2008 said:**
> I mean anything equivalent to Hyperterminal in windows?

So you want to communicate with the serial ports?  The package gtkterm or minicom may do what you want.

---

