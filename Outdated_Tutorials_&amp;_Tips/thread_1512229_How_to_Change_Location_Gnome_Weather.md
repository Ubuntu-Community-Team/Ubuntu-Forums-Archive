---
title: "How to Change Location Gnome Weather"
date: 2010-06-17
forum: Outdated Tutorials &amp; Tips
---

### Post by Rodney9 on 2010-06-17
If your Gnome Weather Applet does not show your area you may be able to change it.
I live in Brisbane and the forecast is for the general south east, not Brisbane itself, so I copy the IDQ number from [http://www.bom.gov.au/qld/forecasts/brisbane.shtml](http://www.bom.gov.au/qld/forecasts/brisbane.shtml) which is IDQ10095 and I see that the Weather Applet is using IDQ10090.
Download Bless Hex Editor thru the Software Centre and open a terminal and type –

sudo bless /usr/share/libgweather/Locations.xml

I then search for text saying IDQ10090 and change the 0 to a 5 and then save.
Then you close the wearther applet and restart it and it now uses the new code.

For other Locations altogether I found this in the Ubuntu Forum thanks to "psychok7" -

""""""* Get your desire location by using wikimapia.org

    * change the longitude and latitude by using GPS Converter or wikimapia can also convert your longitude and latitude just fine.
    * Open up terminal, and go to folder /usr/share/libgweather/
    * Edit the Location.xml with your Favourite text editor. Please be aware that gedit might not be suitable due to encoding problem. Some editor might hung or crash. My suggestion is to use VIM or nano.
    * Go to nearest location by using the 'find' option.
    * Then add new city by using this template:

<city><name>Your City</name><coordinates>27.990000 101.890989</coordinates></city>

    * Please change the template with your city name and your city coordinates that you got from previous steps.

After finish editing the Location.xml, please select your city listed on Weather Report Preferences by right-clicking the applet icon on your tray. If no data shown on update, just play around with the coordinates. """""

Rodney

---

