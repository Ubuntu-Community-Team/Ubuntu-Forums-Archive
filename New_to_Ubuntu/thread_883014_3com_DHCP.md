---
title: "3com DHCP"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by waterrr on 2008-08-07
Hi,
I currently have a cisco router and a 3com router and when I run any wired connection from the cisco onto any of the pc's/platforms they can achieve a IP from the DHCP successfully, but when connecting a port from the cisco to the 3com and a port from the 3com to a pc/platform, the pc/platform fails to achieve a IP from the DHCP when I run a ```
sudo ifup eth0
``` commandline - what am I doing wrong?

The reason I have 2 routers is for the sole purpose of providing more ports

---

### Post by bab1 on 2008-08-07
Quick answer:  DHCP requests do not pass through routers without dhcp helper being used.

You do not need a router "to add more ports".  You should use a switch for that purpose.

Edit:  The switch can be a simple one.  No config -- just plug it in to a port on the original router and that port is replicated to all the ports on the switch.

---

### Post by waterrr on 2008-08-07
Okay, but is what I'm doing not going to give me internet access?

I also consider the 3com to be more a switch than a router

---

### Post by bab1 on 2008-08-07
If you use 2 routers then you will have to do some exotic config.  There is no sorta -- either you have a switch or you don't.

---

### Post by waterrr on 2008-08-07
the 3com is a switch - the cisco is a router - when i conect one port of the router to the switch port of the 3com and a port of the 3com to a pc/platform i get no internet

---

### Post by waterrr on 2008-08-07
i know that since its a switch, it should just automatically just give the internet...but this switch was configured before for a different environment i think and i have no idea on how to restart this switch so it can just be on default settings - i think that may be the problem

---

### Post by bab1 on 2008-08-07
If it truly is a switch, then dhcp should pass through and the internet should be available.

---

### Post by bab1 on 2008-08-07
Unless this is a switch that is "managed" then there is no config.  It is just is installed and works.

---

### Post by waterrr on 2008-08-07
What do you mean "managed" - From what I've been told, this 3com was configured for a different environment/setting but I don't see how...I thought all switches just automatically give the internet

---

### Post by bab1 on 2008-08-07
Like I said -- there is no config.  Managed switches do not involve "environmet"  They set up VLAN's and filter by MAC addresses.

---

### Post by waterrr on 2008-08-07
So is that prohibiting the ability to give me internet? - if so what can I do to fix this?

---

### Post by fwre01 on 2008-08-07
what model 3com and cisco are you using?

---

### Post by waterrr on 2008-08-07
cisco 2960 and 3com switch 4500

---

### Post by fwre01 on 2008-08-07
Ok, thats a managed switch, it sounds astho someone has configured some vlans or dhcp snooping. you need to reset the config and all should be well

---

### Post by waterrr on 2008-08-07
Ok, but how do I reset it is what I'm asking, I have no idea...

---

### Post by fwre01 on 2008-08-07
you may need to logon via console to switch (unless you can logon via telnet, if you know its IP address) using a serial port. then issue the clear config command which will be in this manual (along with how to connect via console)

[http://www.3com.hu/download/switch_4500_family_configuration_guide.pdf/switch_4500_family_configuration_guide.pdf](http://www.3com.hu/download/switch_4500_family_configuration_guide.pdf/switch_4500_family_configuration_guide.pdf)

---

### Post by waterrr on 2008-08-07
I can't seem to find the clear config command...

and I do not understand on how to connect it via console to switch for this Ubuntu

Such as the instructions on the bottom of page 17 where it says to go to a Terminal or Hyperterminal for windows 3x or 9x

---

### Post by fwre01 on 2008-08-07
This is the command you need.

```
 reset saved-configuration 
```

To console onto the switch you need something like minicom installed in ubuntu

---

### Post by waterrr on 2008-08-07
Ok ive installed minicom and configured it - but I don't know how to type the command reset saved-configuration...do you happen to know how to use minicom?

---

### Post by fwre01 on 2008-08-07
once minicom is configured to use your serial port, just connect to the switch using the correct cable, then type minicom from a terminal, you may have to hit <CR> a few times to initiliaze the connection. then you will be at the command prompt of the switch, then issue that command.

---

### Post by waterrr on 2008-08-07
i typed sudo minicom and i just get this minicom menu, so am i just suppose to type minicom?

it brings up the same menu actually and im not able to type, just use ctrl+a z for help

hit <CR> ? what's <CR>

---

### Post by bab1 on 2008-08-07
I believe minicom is the comand.  Try ```
man minicom
``` for useage.  The term <CR> is for "carridge return", roughly;...the "enter" key ;-)

I would make sure minicom is configured correctly.  I believe the baud rate is: 9600, 8, N, 1

Edit: the baud rate is: 19200  [COLOR="Red"]NOT[/COLOR] as stated above.
See page 17 of the [[COLOR="SandyBrown"]manual[/COLOR]]("http://www.3com.hu/download/switch_4500_family_configuration_guide.pdf/switch_4500_family_configuration_guide.pdf")

---

### Post by cgkades on 2008-08-07
I think you have to configure minicom to use ttys0 or something like that. they give an example in the help file. what ever one they used for the example is what i used


oh and do you have port on your switch labled con or console? if so do you have a console cable, know what one is, or know how to make one?

---

### Post by bab1 on 2008-08-07
You bring up a good point [COLOR="Blue"]cgkades[/COLOR].  I have never had a need to use a USB/DB9  serial cable. I wonder how hard it is to get one. Most boxes don't have a serial port on the backplane anymore.

---

### Post by fwre01 on 2008-08-10
waterrr, how did u get on with this? did u get it working?

---

