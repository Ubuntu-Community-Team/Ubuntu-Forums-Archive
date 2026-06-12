---
title: "Making a printer driver for Lexmark X1190"
date: 2015-02-25
forum: Programming Talk
---

### Post by pc_magas on 2015-02-25
Hello I have an Lexmark X1190 printer and I am thninking to write my own cups driver for it.

As I read in [http://www.linuxfoundation.org/collaborate/workgroups/openprinting/writingandpackagingprinterdrivers](http://www.linuxfoundation.org/collaborate/workgroups/openprinting/writingandpackagingprinterdrivers) actually a cups driver is a program that translates a poscript/pdf/ into printer commands. Also it should bridge The SANE with the embeded scanner. All the required information should be into a ppd file.

So I would to know:
[LIST=1]
[*]How I am gonna find the correct commands to send into the printer, in other words how I am gonna reverse engineer the connection between printer and computer in order to find out what data iand in what form should I send to (By using it through Windows); (Note lsusb shows that the kernel recognises the printer it just cups doesn't know what to send)
[*]How should I make the .ppd file;
[*]How I gonna find how to open the connection between computer and the printer. Is it just easy as Opening a serial Connection with Arduino, that is just like opening a serial terminal or needs a specific configuration, how I gonna find that?
[/LIST]

---

