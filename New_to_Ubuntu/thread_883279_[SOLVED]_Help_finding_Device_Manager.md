---
title: "[SOLVED] Help finding Device Manager"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by Doversole on 2008-08-07
Hello all, I am new here and to Ubuntu.  I installed Ubuntu last night on an old laptop to try it out. It is a Dell Inspiron 2650. When I inserted my wireless card (D-link Air 650)not much happened.  I went to the online (on a different computer) Documentation site to read about connecting to the Internet.

I was told told to go to Network Manager and select my wireless connection.  Well there were none showing.  A note in the documentation said that if no connections are showing, then see the Troubleshooting section.

In troubleshooting, I was told to go to the Device Manager (System > Prefereces > Hardware Informaton)to determine that the system recognizes my wireless card.  When I follow these steps there is no menu item for "hardware information" shown.

What I am doing wrong?

---

### Post by spiderbatdad on 2008-08-07
System>>Administration>>Hardware Drivers?

---

### Post by drs305 on 2008-08-07
Device manager is no longer installed by default in hardy.

```
sudo aptitude install gnome-device-manager
```

Accessed via System Tools, Device Manager.

---

### Post by Doversole on 2008-08-07
Below is a cut and paste from the documentation.

[COLOR="Red"]Check for device recognition

1)Open Device Manager (System &#8594; Preferences &#8594; Hardware Information).

2)Check to see the hardware is recognised if it is then the section called “Check for driver”

3)If your device is not displayed then there may be a hardware problem. Ensure if it is PCMCIA or PCI that it is inserted correctly.[/COLOR]

I am at step #1 trying to make sure my hardware is recognized. As I read the documentation, if I can determine that it is recognized, then I would go to check drivers as you suggested with a question.

Where is the Device Manager?

---

### Post by spiderbatdad on 2008-08-07
also running the command```
sudo lshw
```would show you a list of recognized pci and pcmcia connected hardware...or```
lspci
```This too would show you whether the device is recognized and assigned a driver...though drs305 suggests a gui tool, much more user friendly.

---

### Post by Doversole on 2008-08-07
I went to "Terminal" and ran the command line (sudo aptitude install gnome-device-manager) that drs305 suggested.  It appeared to execute fine.

Now where do I find "System Tools" to access the Device Manager?

---

### Post by drs305 on 2008-08-07
> **Doversole said:**
> I went to "Terminal" and ran the command line (sudo aptitude install gnome-device-manager) that drs305 suggested.  It appeared to execute fine.

Now where do I find "System Tools" to access the Device Manager?

Probably you have an ubuntu symbol at the top left of the top panel. Click on that and it opens the main menu. Under that you will find "System Tools". 

You can also type in terminal:
```
gnome-device-manager
```

---

### Post by Doversole on 2008-08-07
> **drs305 said:**
> Probably you have an ubuntu symbol at the top left of the top panel. Click on that and it opens the main menu. Under that you will find "System Tools". 

You can also type in terminal:
```
gnome-device-manager
```

Clicking on the symbol results in the "Applications" menu dropping down.  I can find nothing such as system tools in the Applications.

---

### Post by spiderbatdad on 2008-08-07
system>>preferences>>main menu

highlight applications on the left, check system tools on the right.
Also highlight system tools on the left, check your application on the right.

---

### Post by drs305 on 2008-08-07
> **Doversole said:**
> Clicking on the symbol results in the "Applications" menu dropping down.  I can find nothing such as system tools in the Applications.

Sorry, I may have rearranged my menu. Other than the method mentioned in the  prior post, you can run terminal commands with ALT-F2 and entering the command - in this case "gnome-device-manager".

---

### Post by Doversole on 2008-08-07
> **spiderbatdad said:**
> system>>preferences>>main menu

highlight applications on the left, check system tools on the right.
Also highlight system tools on the left, check your application on the right.

When I go to Main Menu, and check the box next to System tools, the check disapears within a few seconds.  When I click on System tools on the left side a list of six items appears, but Device Manager is not one of them.

Does this mean the command (sudo aptitude install gnome-device-manager) that I ran earlier did not work?

---

### Post by spiderbatdad on 2008-08-07
seems weird. did you try sudo lshw or lspci? If your device is connected and you run the command, we can easily see if the device is recognized...then you can move on to step two.:)

---

### Post by spiderbatdad on 2008-08-07
Also could you link the guide you are following?

---

### Post by Doversole on 2008-08-07
> **drs305 said:**
> Sorry, I must have rearranged my menu. Other than the method mentioned in the  prior post, you can run terminal commands with ALT-F2 and entering the command - in this case "gnome-device-manager".

OK, first I wish to thank you and drs305 for your helpful advice.

I re-ran the command that drs305 gave to install device manager with the screen expanded so I could see all of the execution results.  I notice that there was a problem connecting to the internet for some information.

Remember I began this because I could not get my wireless to work.  Well I cabled to the router and ran it again.  The results appear to have worked much better.  I now see the device manager.

So I am one step closer (please do not remind me that this was all step one).

Thanks again.

---

### Post by drs305 on 2008-08-07
> **Doversole said:**
> So I am one step closer (please do not remind me that this was all step one).


If you can still keep your humor after all this so can we ;-)

---

### Post by Doversole on 2008-08-07
> **drs305 said:**
> Sorry, I may have rearranged my menu. Other than the method mentioned in the  prior post, you can run terminal commands with ALT-F2 and entering the command - in this case "gnome-device-manager".

I have device manager now.  during the install there is a need for internet access.  Since I was working on a wireless problem, I did not have internet and therefore the install did not work properly.  I cabled to the router and re-ran the install command it it worked fine.

Thanks to both you and drs305.

---

