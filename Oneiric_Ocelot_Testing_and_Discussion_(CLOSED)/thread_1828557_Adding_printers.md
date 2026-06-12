---
title: "Adding printers"
date: 2011-08-19
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by brazov on 2011-08-19
When OO was in the alpha 1 stage, I succesfully added several printers from the graphical interface System Settings > Printers.

Now it is impossible. When I try, I enter in an infinite loop between two windows, the first one asking for a password of root for localhost, and the second one reporting that the password is wrong. I tried to substitute in that window 'root' with an administrator but it did not work.

Do you also have this problem, or am I doing some mistake?

P.S. also the web interface of cups does not work for network printers.

EDIT: This happens in Unity. In Gnome it is even impossible to click on the button '+' for adding printers.

---

### Post by Framli on 2011-08-19
FWIW, I've just added a network printer using the "Printers" shortcut in the Attached Devices section of the Session Menu. Works well.

---

### Post by terry_gardener on 2011-08-19
i have also done it the same way as Framli did it.
also network printer. 

you have to click file settings and tick the required boxes.

---

### Post by brazov on 2011-08-19
I see that is a problem of mine. Does anybody have a suggestion?

P.S.: After yesterday's updates also Firefox is broken. Freezing on flash content.

---

### Post by Sennaista on 2011-08-30
Trying to add a network printer from System Settings will result in this message:

> FirewallD is not running. Network printer detection needs services mdns, ipp, ipp-client and samba-client enabled on firewall.

Any idea what it means? Do I have to change firewall settings?

---

### Post by kyroupox on 2011-09-06
Same for me !

Oneiric beta 1 + Gnome Shell

---

### Post by soepstad on 2011-09-08
> **kyroupox said:**
> Same for me !

Oneiric beta 1 + Gnome Shell

Exact same issue here.

Edit: Adding printer through browser interface works perfectly.

---

### Post by rbrick49 on 2011-09-08
just go here if your having trouble works for me

[www.ehow.com/how_5107960_add-network-printer-linux.html](www.ehow.com/how_5107960_add-network-printer-linux.html)

---

### Post by zerubbabel on 2011-10-03
> **Sennaista said:**
> Trying to add a network printer from System Settings will result in this message: FirewallD is not running. Network printer detection needs services mdns, ipp, ipp-client and samba-client enabled on firewall. 


Any idea what it means? Do I have to change firewall settings?

Can anyone answer this question? I'm having the same problem. What happened to the simplicity of adding a printer in 11.04? 

When I try using the CUPS browser interface ([http://localhost:631](http://localhost:631)) it asks for a login and then doesn't accept my username/password.

---

### Post by cariboo on 2011-10-03
I have two networked printers, I just logged into [http://localhost:631](http://localhost:631), using my username and password, and was able to administer both printers with no problem. One printer is a Brother HL-5250DN, which has it's own ip static ip address, and the other is an Epson R340 connected to a system running XP, that system has a dynamic ip address, both work without any problems.

---

### Post by zerubbabel on 2011-10-03
> **cariboo907 said:**
> I have two networked printers, I just logged into [http://localhost:631](http://localhost:631), using my username and password, and was able to administer both printers with no problem. One printer is a Brother HL-5250DN, which has it's own ip static ip address, and the other is an Epson R340 connected to a system running XP, that system has a dynamic ip address, both work without any problems.

That doesn't answer the question: Why can't I add a network printer via the Printers applet in System Settings as I could in previous versions of Ubuntu? 

As for the CUPS browser interface, I can't get past the login prompt, as for some reason it won't accept my administrator-level login name and password.

---

### Post by chlorox on 2011-10-03
> **zerubbabel said:**
> That doesn't answer the question: Why can't I add a network printer via the Printers applet in System Settings as I could in previous versions of Ubuntu? 

The ability to manually configure things is slowly eroding in all areas. The responses to my similar questions were along the lines of either:

1. You can still do it, it'll just require you doing it like you did back in RedHat 5.2 via a terminal. (yes, I've been around for awhile)

2. It was causing too many support requests when a user would do it manually, now with the automatic way, there are far fewer requests... probably because the user got disgusted and tried a different distro/OS.


They remove the pretty graphical way because it was giving people the false sense of "knowing what they were doing". Now that sense is only given to those who REALLY know what they are doing.

I know, it doesn't really seem to fit the Ubuntu way, does it?

For you, if you can't use your login credentials to get into the HTTP interface, try editing your /etc/cupsd.conf and removing the need for authentication. Make sure you use sudo to edit the file or you will not be able to change it. Then issue a sudo /etc/init.d/cups restart. You should have no problem setting up a printer.

---

### Post by zerubbabel on 2011-10-03
Thank you very much, but I'm not sure exactly what to change in /etc/cups/cupsd.conf to disable the authentication requirement...

---

### Post by chlorox on 2011-10-03
You need to change DefaultAuthType to none and then restart the cups server. I'll look more into it if that doesn't work for you.

---

### Post by chlorox on 2011-10-03
Oh, one more key thing to keep in mind. If you're going to use authentication, your user needs to be part of the lpadmin group. 

In Ubuntu, you can do this by issuing:

sudo adduser *username* lpadmin .

---

### Post by zerubbabel on 2011-10-03
> **chlorox said:**
> You need to change DefaultAuthType to none and then restart the cups server. I'll look more into it if that doesn't work for you.

Ok, I did that and restarted CUPS, and now when I click Add Printer in the CUPS browser interface, it doesn't ask for a login, but it says: Add Printer Error: Unable to add printer: Unauthorized

---

### Post by zerubbabel on 2011-10-03
> **chlorox said:**
> Oh, one more key thing to keep in mind. If you're going to use authentication, your user needs to be part of the lpadmin group. 

In Ubuntu, you can do this by issuing:

sudo adduser *username* lpadmin .
It says I'm already a member of that group...

---

### Post by zerubbabel on 2011-10-03
Perhaps this is a hint. When it asked for a login, the prompt was: 

A username and password are being requested by [http://localhost:631](http://localhost:631). The site says: "CUPS"

Is there supposed to be a CUPS login?

---

### Post by crdlb on 2011-10-03
> **zerubbabel said:**
> A username and password are being requested by [http://localhost:631](http://localhost:631). The site says: "CUPS"

I get a similar prompt, and I can log in with my user and password.

---

### Post by zerubbabel on 2011-10-03
> **crdlb said:**
> I get a similar prompt, and I can log in with my user and password.

Well that is perplexing. I'm logged in with the same username and password I give in response to that prompt, which is an administrator level account, but it is not accepted at that prompt. I guess I will have to revert to 10.04 in order to get any work done...

---

### Post by bbrg548 on 2011-10-03
> **Sennaista said:**
> Trying to add a network printer from System Settings will result in this message:

> FirewallD is not running. Network printer detection needs services mdns, ipp, ipp-client and samba-client enabled on firewall. 

Any idea what it means? Do I have to change firewall settings?

I'm getting the same thing. I'm stumped. I can't find a "FirewallD" package or process to run or even to install.

I'm not finding anything on Launchpad. Has anyone reported this? I would say it's a definite usability regression, if not an actual bug.

---

### Post by lehjr on 2011-10-09
I found a post on [[COLOR="Blue"]Linux Questions[/COLOR] ]("http://www.linuxquestions.org/questions/linux-hardware-18/network-printer-install-problem-904244/") that points to a [[COLOR="Blue"]Fedora page[/COLOR]]("https://fedoraproject.org/wiki/FirewallD/") and also found a related [[COLOR="Blue"]patch[/COLOR]]("http://mail.gnome.org/archives/commits-list/2011-July/msg09761.html") for Gnome or Gnome Control Center, I'm too tired to read through the whole thing but it looks relevant.

**Edit:** Went back and read the beginning of the patch, and yeah,it's a Gnome patch and that's where this issue started. The way it looks to me is that FirewallD is Fedora specific, and if that's the case, I'm not sure why they thought adding a Fedora-specific requirement to a Desktop Environment used by numerous other distros would be a good idea, but obviously it is something that needs to be addressed. Sure FirewallD could be ported to Ubuntu and other distros, but that doesn't really address the issue of requiring a specific piece of software to be installed and running in order to perform a certain and non-related function.

**Edit2:** I wanted to add that you can still add the printer through the control panel in Unity, but the Gnome version will require FirewallD to add it.

---

