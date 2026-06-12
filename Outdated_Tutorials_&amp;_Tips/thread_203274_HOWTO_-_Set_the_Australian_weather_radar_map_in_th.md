---
title: "HOWTO - Set the Australian weather radar map in the panel applet"
date: 2006-06-25
forum: Outdated Tutorials &amp; Tips
---

### Post by dcstar on 2006-06-25
The Gnome "Weather Report" panel applet has the facility for a radar map of a selected locality which may be automatically set in some regions, but in Australia you have to manually set a map URL for your region (if it is available), here are the steps (using Firefox) to set this for the official Australian Bureau of Meteorology maps:

[LIST=1]
[*]Navigate to the B.O.M. site: [http://www.bom.gov.au/](http://www.bom.gov.au/)
[*]Select your State
[*]Select the "**Radar Images**" link
[*]Select either the **128 km **or **256 km** map for your region (if available)
[*]Right-click the image and select "**Copy Image Location**"
[*]Right-click the Weather applet icon in your taskbar (you have already installed it, haven't you.....) and select "**Preferences**"
[*]Select "**Enable Radar Map**"
[*]Select "**Use custom address for radar map**"
[*]Paste the address into the "**Address**" field (the map URL should be put there)
[*]**Close** the Weather Preferences box
[/LIST]
Now you should see the latest weather radar map when you select the Weather applet on your taskbar and then select the Radar Map tab.

This procedure should also be able to be used for any other location where map URLs are not put in automatically by selecting the Weather applet Location (and if there are local radar maps available on-line).

---

### Post by aaamos on 2008-10-04
Useful post, thanks dcstar :)

Just a quick addition, since the thread is a couple of years old by now... the instructions are still pretty much the same, except you should insert:

**3b. Select the "Single Images" tab (by default, it will take you to the "Loops" tab, copying the address of which won't work)**

Oh, and selecting "Copy Image Address" in Opera will of course also work in Step 5.

---

### Post by k3lt01 on 2009-01-14
> **dcstar said:**
> [*]Right-click the image and select "**Copy Image Location**"I know this is very old but I thought I'd let you know that it doesn't seem to work this way anymore. My copy of FireFox3 doesn't have the "Copy Image Location" option when I right click.
> **aaamos said:**
> **3b. Select the "Single Images" tab (by default, it will take you to the "Loops" tab, copying the address of which won't work)**That fixed it.

---

### Post by divinequran on 2009-01-14
Is it is the same procedure to add in all Linux based system link Redhat, debian linux e.t.c

---

### Post by k3lt01 on 2009-01-14
> **divinequran said:**
> Is it is the same procedure to add in all Linux based system link Redhat, debian linux e.t.cIf they used Gnome I would imagine it would be the same.

---

### Post by Herman on 2009-01-15
:) Thank you for the useful thread, dcstar and all who contributed, and k3lt01 for letting me know. :)

---

### Post by charonred on 2009-06-15
did as per above instructions, and single image loads; but how do I get it to display a loop animation?

---

### Post by Rodney9 on 2009-11-03
The Gnome weather report still uses the airport weather details.
The airport here in Brisbane is 30 km's away on the coast, the weather there is much differant than in the city.
Temperatures can vary 5 degrees and the wind can be from a totally different direction, the airport might have a storm or fog when Brisbane is clear. 
So this panel add-on is useless, it has been the same for several years, with this latest version I hoped they fixed it.

Are there any other widgets or something for local weather here in Brisbane Australia ?

Rodney

---

### Post by k3lt01 on 2009-11-04
> **Rodney9 said:**
> The Gnome weather report still uses the airport weather details.
The airport here in Brisbane is 30 km's away on the coast, the weather there is much differant than in the city.
Temperatures can vary 5 degrees and the wind can be from a totally different direction, the airport might have a storm or fog when Brisbane is clear. 
So this panel add-on is useless, it has been the same for several years, with this latest version I hoped they fixed it.

Are there any other widgets or something for local weather here in Brisbane Australia ?

Rodney
It may be useless for you but for others, like me, it is useful.

Check sites like Elders weather or even just Google Australian Weather stations that may help give you some answers.

---

### Post by dcstar on 2010-12-03
> **charonred said:**
> did as per above instructions, and single image loads; but how do I get it to display a loop animation?

You can't, the "loop" is a series of individual jpegs displayed in the BOM webpage courtesy of javascript.

The Gnome display can only display a single image, so the latest available is the best choice.

---

### Post by Rodney9 on 2010-12-03
Well now the forecast in Gnome Weather Applet is broken after BOM changed their format.

---

### Post by kyphi on 2011-02-21
Yes, it is broken for the capital cities because the BoM changed their forecast codes.

It still works very well for rural areas and towns.

The address for the radar map can be obtained by right clicking the "Single Image" and selecting "View Image Info" from the drop down menu.  That will give you a long radar location address which has to be entered into the "weather preferences" radar location box.

I have altered my weather locations listing to include Williamtown, NSW.
See:  [https://wiki.ubuntu.com/WeatherIndicator/NewLocation](https://wiki.ubuntu.com/WeatherIndicator/NewLocation)

---

### Post by AldenIsZen on 2011-07-18
Most current thread I've found on the Weather Report applet and mentioning Radar Map. For NOAA, you can view the page source, and search for ".gif". I found the Southeast Loop, so I knew that is what I wanted. Since it was at location /Loop/southeast_loop.gif in the page source, I knew I had to add the loop and the rest after where I was at, which was of course a .php page at the [http://radar.weather.gov/Conus/](http://radar.weather.gov/Conus/) directory. The below was the end result, and I have animated waether radar map, after years of wanting this... hope this helps with this explanation.

[http://radar.weather.gov/Conus/Loop/southeast_loop.gif](http://radar.weather.gov/Conus/Loop/southeast_loop.gif)

---

