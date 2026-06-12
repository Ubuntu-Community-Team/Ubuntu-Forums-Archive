---
title: "CUPS use remotely"
date: 2014-02-22
forum: New to Ubuntu
---

### Post by schmitta on 2014-02-22
I believe a cups printer can be accessed over the web. I have two ubuntu machines ; one with cups and a printer attached through LP1: (?) and another on the same router with currently no cups access to that printer. It would seem that the simplest approach would be to send a file to be printed over the web to the ubuntu machine with the cups printer. How should I go about setting that up? Thank you. Alvin...

---

### Post by pqwoerituytrueiwoq on 2014-02-22
If you want to print over the Internet you will need to enable port forwarding on your router (methods varies from router to router)
if you are trying to  enable it over your local network do this
run
[FONT=courier new]system-config-printer[/FONT]
see attached recording

---

### Post by tgalati4 on 2014-02-23
Set up the printer as normal on your Ubuntu system.  Open port 631 on your router.  Determine your IP address.  Set up a new IPP printer on your remote machine with the correct IP adress.  There are some security risks with leaving port 631 open all of the time, so you can either remap the port to an obscure port number (above 12000) or set up "port knocking".  You would ping a specific port and that would run a script to open port 631 for 10 minutes to allow you to print, then close it up again.

This is an old help link, but the basic steps are the same:  [https://help.ubuntu.com/community/NetworkPrintingFromMacOSX](https://help.ubuntu.com/community/NetworkPrintingFromMacOSX)

---

