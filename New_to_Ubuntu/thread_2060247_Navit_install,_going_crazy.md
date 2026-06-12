---
title: "Navit install, going crazy"
date: 2012-09-19
forum: New to Ubuntu
---

### Post by tdriver on 2012-09-19
Hello I'm a total noob to the Linux world, there that's out in the open. I have some computer skills but nothing to strong. I have an HP Mini 1000, running dual boot Ubuntu Lucid. I have been trying for nearly a week now to install Navit GPS. I've tried all kinds of ways to get it to go with no luck. My last attempt I used the LUCID tar.gz file on this page [http://navit.latouche.info/ubuntu/lucid/](http://navit.latouche.info/ubuntu/lucid/)   


I then used the GNU autotools install instructions from this page: [http://wiki.navit-project.org/index.php/NavIt_on_Linux](http://wiki.navit-project.org/index.php/NavIt_on_Linux)

The install began and stopped here:
vehicle_gpsd.c: In function ‘vehicle_gpsd_open’:
vehicle_gpsd.c:259: warning: implicit declaration of function ‘g_timeout_add’
vehicle_gpsd.c:259: error: ‘GSourceFunc’ undeclared (first use in this function)
vehicle_gpsd.c:259: error: (Each undeclared identifier is reported only once
vehicle_gpsd.c:259: error: for each function it appears in.)
vehicle_gpsd.c:259: error: expected ‘)’ before ‘vehicle_gpsd_try_open’
vehicle_gpsd.c: In function ‘vehicle_gpsd_close’:
vehicle_gpsd.c:271: warning: implicit declaration of function ‘g_source_remove’
make[5]: *** [vehicle_gpsd.lo] Error 1
make[5]: Leaving directory `/home/saul/navit/navit/vehicle/gpsd'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/saul/navit/navit/vehicle'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/saul/navit/navit'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/saul/navit/navit'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/saul/navit'
make: *** [all] Error 2
saul@saul-laptop:~/navit$ 

Is it looking for a GPS receiver here??
 
Unfortunately i do not know what to do now, any and all help will be greatly appreciated, Thank You..

---

### Post by Bashing-om on 2012-09-19
tdriver;

  That package is available in the software repositories .. Is there a reason to attempt to install in a more difficult way ?

[INDENT]hth <==BDQ
 
[/INDENT]

---

### Post by tdriver on 2012-09-20
If you mean package in GPSD, it's already installed. As for an easier way, if there is one i'm all ears..Please do tell how, Thank you,

---

### Post by evilishan on 2012-09-20
I think perhaps they mean adding the Navit repository as a source and then installing Navit via your favourite software installer of choice (apt-get, Ubuntu Software center etc).

Source+ instructions:
 [http://wiki.navit-project.org/index.php/Download_Navit#Ubuntu](http://wiki.navit-project.org/index.php/Download_Navit#Ubuntu)

Good luck and best wishes!
Ishan

---

### Post by Bashing-om on 2012-09-20
tdriver;

  does this package meet you needs:

Car navigation system with routing engine - GTK+ GUI
 
Navit is a car navigation system with routing engine.

Its modular design is capable of using vector maps of various formats for
routing and rendering of the displayed map. It's even possible to use multiple
maps at a time.

The GTK+ or SDL user interfaces are designed to work well with touch screen
displays. Points of Interest of various formats are displayed on the map.

The current vehicle position is either read from gpsd or directly from NMEA
GPS sensors.

The routing engine not only calculates an optimal route to your destination,
but also generates directions and even speaks to you using speech-dispatcher.

This package contains the GTK+ GUI plugin.


[INDENT]try'n to help ==>BDQ

[/INDENT]

---

