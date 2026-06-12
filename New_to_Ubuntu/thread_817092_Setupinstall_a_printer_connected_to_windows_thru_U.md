---
title: "Setup/install a printer connected to windows thru USB on network"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by shuttleworthwannabe on 2008-06-03
Hi there,

simply this is the setup right now:
Printer connected to Windows XP desktop via usb; I have the IP address of the desktop and have the printer in sharing mode. Windows machine logs onto a domain (windows domain). This desktop is always on and there are no firewalls.

I wish to use my Ubuntu laptop that is also hooked up to the network (but not login via domain) to print on the Windows desktop that is connected to the printer via a USB cable.

How do I use Ubuntu printer setup to connect to this USB printer on windows desktop on network.

Many thanks
S:confused:

---

### Post by superprash2003 on 2008-06-03
hope this helps [https://help.ubuntu.com/community/WindowsXPPrinter](https://help.ubuntu.com/community/WindowsXPPrinter)

---

### Post by NikoC on 2008-06-03
System > Administration > Printing > New printer

Windows Printer Via Samba

Just fill out the ip of the Samba machine (your windows pc) and the printer share name. Finally enter your username and pass and verify...

It worked out of the box for my Desktop Xp Pc and HP deskjet 1010 printer...

Cheers

---

### Post by shuttleworthwannabe on 2008-06-03
thanks both of you; am away from the network right now, but will try as soon as I get back to work.

---

### Post by shuttleworthwannabe on 2008-06-04
Hi there; I am using Windows Printer with SAMBA. I get error "Print share is not accessible". I know the machine is on and I am logged in. Printer is also on.

Any suggestions?

---

### Post by NikoC on 2008-06-05
A couple of issues that I had when installing the Samba printer (though this was on a previous ubuntu release, running Hardy now) :

- keep the printer's share name short (< 9 characters and no spaces)
- no spaces in you username and or pass

---

### Post by lisati on 2008-06-05
> **NikoC said:**
> A couple of issues that I had when installing the Samba printer (though this was on a previous ubuntu release, running Hardy now) :

- keep the printer's share name short (< 9 characters and no spaces)
- no spaces in you username and or pass

And don't forget to make sure that printer sharing is enabled on the Windows end.

---

### Post by shuttleworthwannabe on 2008-06-06
The thing is is I dual boot on this remote laptop and when I setup the printer that is connected to the desktop via network using Windows XP on my laptop, it sees the printer on the IP and configures it correctly. So surprized that Ubuntu Hardy using SAMBA not seeing the printer or even able to configure it.

BTW, I have made sure the printer is in share mode and user/pass are appropriate. thanks for that.
S

---

### Post by halitech on 2008-06-10
try it using the IP address of the windows computer. Also, verify the username and password is correct (I forgot I had a different username on my windows box). I used the IP and made sure my username was right and now its working for me.

---

### Post by geezerone on 2008-06-14
I am trying to get printing to XP shared printer to work but unable to do so yet. 

I add my Samsung ml1210 and browse ok for it but do I need the user/password or not. I have tried XP user account name and password but says print share is inaccesible when I click 'verify'?

---

### Post by halitech on 2008-06-14
You probably do need the XP username and password. is the sharing set up on the printer to allow the user to do things? Also, try Guest and leave the password blank.

---

### Post by geezerone on 2008-06-14
Tried my XP account name (lower case as shown) and the login password to no avail. I checked and XP printer is shared.

I take it that the exact username and password is what is typed and not the path too (/HOME/PC/...) etc?

---

### Post by halitech on 2008-06-14
correct, it should be the same as what you use to log into the computer. If that doesn't work, try Administrator and what ever the admin password is.

---

### Post by geezerone on 2008-06-14
No joy, still no authentication.

---

### Post by shuttleworthwannabe on 2008-06-16
just to let you also know that I have not been successful at al; stalled at unable to verify and not accessible...

Will try and get my network admin comeby to help me understand this and setup, till then...

---

### Post by cariboo on 2008-06-16
You shouldn't need a password if you have your printer shareed on XP so everyone can use it.

JIm

---

### Post by shuttleworthwannabe on 2008-06-17
ok, I got it to work. for some reason GNOME print manager did not setup correctly. I have installed kcontrol (with kdeprint), and used the GUI there to setp up the SMB printer and worked like a charm. BTW the user/psswd is required.

Thanks you all.
S

---

### Post by bk60544 on 2011-03-14
Shuttle, please explain with MORE DETAIL. I am a newbie, and cannot connect the USB printer to connect using SAMBA.

---

### Post by bk60544 on 2011-03-14
Using "Windows Printer with SAMBA", rather than Browse- I entered the IP address of the Windows machine, and Shared name of the printer.  xxx.xxx.xxx.xxx/printer.  Now it works!

---

### Post by Revjohn on 2011-05-04
> **NikoC said:**
> 

- keep the printer's share name short (< 9 characters and no spaces)

Just wanted to let you know that this piece of wisdom solved a couple of hours of head-ache for me.  Thank you!

John

---

