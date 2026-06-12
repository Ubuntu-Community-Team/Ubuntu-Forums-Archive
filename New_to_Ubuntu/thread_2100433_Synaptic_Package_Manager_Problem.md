---
title: "Synaptic Package Manager Problem"
date: 2013-01-01
forum: New to Ubuntu
---

### Post by mikeymike11 on 2013-01-01
Hi, I'm a newbi and don't do terminal commands to install software. Only Synaptic.

How do I install tor via synaptic?
thanks

---

### Post by ubudog on 2013-01-01
This is a good guide to follow, by bodhi.zazen: 
[http://bodhizazen.net/Tutorials/TOR](http://bodhizazen.net/Tutorials/TOR)

The package should be called 'tor'.

---

### Post by Cheesehead on 2013-01-01
Which part of installing Tor via Synaptic are you having trouble with?

---

### Post by ibjsb4 on 2013-01-01
Look here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by mikeymike11 on 2013-01-02
> **ibjsb4 said:**
> Look here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en)

As one article [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto) says  "The only function that is somewhat lacking with the new Synaptic frontend is application installation. There is a new program called gnome-app-install that shows a simple list of common GNOME programs with a checkbox for installation or removal. gnome-app-install will list every package that provides a .desktop icon in the GNOME application menu. In other words, basically every major gui program will be listed."  tried gnome-app-install but the link led to nothing.  so in Synaptic, when i right click the tor package, i get the idea that tor is in the etc folder, so when i go there i find a tor subfolder, where i expected to find a tor icon to click and launch, but no such luck. there were just 2 files there: torrc and a conf file.  questions are, is tor actually installed? how to get the icon onto the application menu?   thanks

---

### Post by mikeymike11 on 2013-01-02
> **Cheesehead said:**
> Which part of installing Tor via Synaptic are you having trouble with?

 tor packages are installed, cant get to launch tor - cant find the program icon to click on!

---

### Post by mikeymike11 on 2013-01-02
> **mikeymike11 said:**
> tor packages are installed, cant get to launch tor - cant find the program icon to click on!

same issue for clamav: installed via synaptic, cant find an icon to launch it

---

### Post by mikeymike11 on 2013-01-02
> **mikeymike11 said:**
> same issue for clamav: installed via synaptic, cant find an icon to launch it

 well bless me, I did another search in SPM for clamav and happened on clamtk: graphical front end for clamav.  I installed that and hey presto! there is an clamav icon in my applications manager!!!!!!!!!!!!!!  Why isnt clamtk included with the clamav packages?   Should I install all packages that are returned when i search clamav?  Now i'm gonna search for a tor icon package....

---

### Post by mikeymike11 on 2013-01-02
> **mikeymike11 said:**
> well tie me up with butchers twine and call me a turkey, I did another search in SPM for clamav and happened on clamtk: graphical front end for clamav.  I installed that and hey presto! there is an clamav icon in my applications manager!!!!!!!!!!!!!!  Why isnt clamtk included with the clamav packages?   Should I install all packages that are returned when i search clamav?  Now i'm gonna search for a tor icon package....

 this is getting better and better. I remember vidalia had something to do with tor. searched for vidalia in SPM and its desc is "GUI for tor". yeehaw, its installing right now.   question is: how are you supposed to know to instal vidalia when you've installed tor? (when you're only using SPM and won't use the terminal commands)

---

### Post by Bucky Ball on 2013-01-02
Because both of these can be used from the command line and the GUI is secondary, kind of an add-on. They don't come automatically as part of the install because some people don't need, or want them. ;)

Please mark as 'Solved' from 'Thread Tools' to help others when you feel it is.

---

### Post by mikeymike11 on 2013-01-02
> **Bucky Ball said:**
> Because both of these can be used from the command line and the GUI is secondary, kind of an add-on. They don't come default as part of the install because some people don't need and/or want them. ;)

Please mark as 'Solved' from 'Thread Tools' to help others when you feel it is.

 I know this is a little off topic, but if ubuntu is going to take off as an alternative to windows, GUI has to be considered as primary and command line is secondary!

---

### Post by Paqman on 2013-01-02
> **mikeymike11 said:**
> I know this is a little off topic, but if ubuntu is going to take off as an alternative to windows, GUI has to be considered as primary and command line is secondary!

Clamav is primarily a server package, it's of very little use on a desktop, since it scans for Windows viruses. Normally you'd install it on a Linux server in order to protect Windows clients connecting to it. Servers very rarely have a GUI.

Tor is a service, it works in the background like a proxy server. To use it you simply point whatever application you're using (such as a browser) to it instead of directly to the internet.

So no, for some stuff having a GUI isn't a sensible default option.

If you want a nice bundled TOR+browser solution, TOR do provide a download that bundles TOR, Vidalia and Firefox. You can get it from their site. Download, extract and click, nice and easy.

---

### Post by mikeymike11 on 2013-01-02
> **mikeymike11 said:**
> I know this is a little off topic, but if ubuntu is going to take off as an alternative to windows, GUI has to be considered as primary and command line is secondary!

 The partial answer can be found when you right-click the package and under dependencies you have 'recommends' and 'suggests'. It is there that the GUI package should be mentioned. Unfortunately the tor package does not mention vidalia in these sections. I will suggest it to tor.

---

### Post by Cheesehead on 2013-01-02
> **mikeymike11 said:**
> I know this is a little off topic, but if ubuntu is going to take off as an alternative to windows, GUI has to be considered as primary and command line is secondary!

In the Free Software ecosystem, any user is welcome to collaborate with a developer and write a needed frontend...or add a frontend module to an existing service (like Network Manager)...and contribute those usability enhancements back to Ubuntu.

You're not a customer, and Ubuntu or Canonical is not your vendor. You're a participant in a collaborative project.

---

### Post by Bucky Ball on 2013-01-02
> **cheesehead said:**
> in the free software ecosystem, any user is welcome to collaborate with a developer and write a needed frontend...or add a frontend module to an existing service (like network manager)...and contribute those usability enhancements back to ubuntu.

You're not a customer, and ubuntu or canonical is not your vendor. You're a participant in a collaborative project.

+1

---

