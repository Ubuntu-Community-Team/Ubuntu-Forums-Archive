---
title: "my weather indicator doesn't work 12.04"
date: 2012-12-20
forum: New to Ubuntu
---

### Post by doja on 2012-12-20
Hi,

yesterday I updated my Ubuntu  12.04 (unity). One of the listed updates was also for
my-weather-indicator (but there were also others).

After the update the icons from my-weater-indicator disappeared at first.
Pc restarted the my-weater-indicator didn't even make a autostart.
Then I tried to start this indicator via DASH. The icon in Launcher appeared for short while (so the application try to start) but then disappear again.

I also tried de- and reinstall the application, but without result.

Starting via terminal I get the message:

bash: /usr/bin/my-weather-indicator: /usr/bin/python3: bad interpreter: No such file or directory

Can anybody help? 
thanks

---

### Post by lokijuhz on 2012-12-20
Hi,

I had the same problem today.

I solved it by installing python3, python3-gi, python3-dbus and python3-cairo.

Hope this helps.

---

### Post by doja on 2012-12-20
it works,  thanks

my only connection to the bad world outside has been restored.

I don't understand it, is it because they rewrote the program in new language that is not included in 12.04?

---

### Post by doja on 2012-12-20
after this last update for my-weather-indicator
the time for sunrise and sunset has been at last
corrected and shows now the right values.

---

### Post by lokijuhz on 2012-12-20
Without looking into the source code, I think the dependency has been changed to python3 and support has been dropped for python 2.

---

### Post by jcottier on 2012-12-21
According to Synaptic, the dependancy for my-weather is python 2.7. So even on a fresh install it wont work. It seems the update to my-weather has not been packaged correctly.

---

### Post by superDave972 on 2012-12-21
I had the same problem. I will try this fix and hopefully it works on my machine as well!

---

### Post by rburkartjo on 2012-12-21
lok thanks for the info fixed my weather indicator and i am using xubuntu 12.10. i was missing python3-cairo.

---

### Post by miguelpires on 2012-12-21
For me it don't work. I can launch the aplication, but can't select my citty or any citty. This is the errors

miguel@miguel-M14xR1:~$ my-weather-indicator
<gettext.GNUTranslations object at 0x2071510>
#####################################################
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.1 LTS
Release:    12.04
Codename:    precise
Version:    x86_64
#####################################################

My-Weather-Indicator version: 0.6.0.0
#####################################################
Traceback (most recent call last):
  File "/usr/share/my-weather-indicator/preferences.py", line 428, in search_location
    cm1 = WhereAmI(self,location = self.entry11.get_text(),latitude = self.latitude,longitude = self.longitude)
  File "/usr/share/my-weather-indicator/whereami.py", line 142, in __init__
    self.on_button1_clicked(None)
  File "/usr/share/my-weather-indicator/whereami.py", line 169, in on_button1_clicked
    direction = geocodeapi.get_direction(search_string)
  File "/usr/share/my-weather-indicator/geocodeapi.py", line 100, in get_direction
    directions = get_directions(search_string)
  File "/usr/share/my-weather-indicator/geocodeapi.py", line 107, in get_directions
    response = read_from_url(url)
  File "/usr/share/my-weather-indicator/comun.py", line 171, in read_from_url
    f = urllib.request.urlopen(request)
  File "/usr/lib/python3.2/urllib/request.py", line 138, in urlopen
    return opener.open(url, data, timeout)
  File "/usr/lib/python3.2/urllib/request.py", line 369, in open
    response = self._open(req, data)
  File "/usr/lib/python3.2/urllib/request.py", line 387, in _open
    '_open', req)
  File "/usr/lib/python3.2/urllib/request.py", line 347, in _call_chain
    result = func(*args)
  File "/usr/lib/python3.2/urllib/request.py", line 1155, in http_open
    return self.do_open(http.client.HTTPConnection, req)
  File "/usr/lib/python3.2/urllib/request.py", line 1135, in do_open
    h.request(req.get_method(), req.selector, req.data, headers)
  File "/usr/lib/python3.2/http/client.py", line 967, in request
    self._send_request(method, url, body, headers)
  File "/usr/lib/python3.2/http/client.py", line 995, in _send_request
    self.putrequest(method, url, **skips)
  File "/usr/lib/python3.2/http/client.py", line 859, in putrequest
    self._output(request.encode('ascii'))
UnicodeEncodeError: 'ascii' codec can't encode character '\xe3' in position 38: ordinal not in range(128)
'utf-8' codec can't decode byte 0xe3 in position 255: invalid continuation byte
'NoneType' object is not subscriptable
Traceback (most recent call last):
  File "/usr/bin/my-weather-indicator", line 45, in <module>
    mwi=MWI()
  File "/usr/share/my-weather-indicator/myweatherindicator.py", line 113, in __init__
    cm.save_preferences()
  File "/usr/share/my-weather-indicator/preferences.py", line 497, in save_preferences
    self.location = geocodeapi.get_inv_direction(self.latitude,self.longitude)['locality'] 
TypeError: 'NoneType' object is not subscriptable
miguel@miguel-M14xR1:~$

---

### Post by superDave972 on 2012-12-21
I finally tried it and I installed all of the packages listed above. My Weather Indicator still doesn't work. Same error is occurring as before. Everything seems to work fine up until the point when I click "APPLY" The app just freezes at that point and doesn't respond.

Any thoughts?

---

### Post by hearthie on 2012-12-22
I had the same problem. I followed the lokijuhz instructions that solved it. Thx lokijuhz!

---

### Post by ronbrooks on 2012-12-23
I am having the same problem and I have added the files but it still will not work at all.  This is what I get from the terminial.

ronald@ronald-GA-78LMT-S2:~$ my-weather-indicator
<gettext.GNUTranslations instance at 0x86ce38c>
No LSB modules are available.
#####################################################
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise
Version:	i686
#####################################################

My-Weather-Indicator version: 0.6.0.2.precise.1
#####################################################

Can anyone help with this?

---

### Post by doja on 2013-01-08
Today 8.1.2013  I  get a new updates for Ubuntu and one of the packages was again for my-weather-indicator (3.1 MB). I think they get the bug(s) corrected.  :-)

But I can not tell because my weather app was already running.

---

### Post by meteorrock on 2013-02-08
This should not be marked solved. On my Gnome 3+ shell with ubuntu I can get this app up but can not get into the preferences on this app. Please help. Using ubuntu 12.10.

---

### Post by cstambaugh on 2013-02-10
I Aslo have the same issue and cant get it to work. When I search for the python stuff it tells me it cannot install them. The  weather indicator just errors out when I try to add my location. 
Is there commands I can try in the Terminal?

---

### Post by kurt18947 on 2013-02-10
> **meteorrock said:**
> This should not be marked solved. On my Gnome 3+ shell with ubuntu I can get this app up but can not get into the preferences on this app. Please help. Using ubuntu 12.10.

I don't know about Unity, don't have it installed in 12.10.  12.10 gnome remix is working very well with Neroth's extension, including on 13.04 so far.  I used this:

[http://www.webupd8.org/2012/06/alternative-gnome-shell-weather.html](http://www.webupd8.org/2012/06/alternative-gnome-shell-weather.html)

After installing, this must be activated with tweak tool.  It also doesn't like Google as a weather source, Yahoo seems to work okay.  If there's no weather data immediately after startup, left-click the display then left-click 'Reload Weather Information".  You should be in business.

---

### Post by cstambaugh on 2013-02-10
I found this worked well, just stumbled upon it tonight..

[http://ubuntuguide.net/weather-indicator-in-ubuntu-12-04-unity#comment-13079](http://ubuntuguide.net/weather-indicator-in-ubuntu-12-04-unity#comment-13079)

Good luck
Chris

---

### Post by t3chn0k on 2013-05-19
I use 12.04 LTS and it was working fine, but after I changed the weather service to Yahoo, I couldn't click on "Preferences" anymore, and after closing the app, I couldn't open it anymore.

**Edit:** I solved this by deleting the configuration file in ***~/.config/my-weather-indicator*** and restarting the application.

For everyone who can't open the app, I recommend trying this solution.

---

### Post by OrangeVixen on 2013-05-31
That does not fix every problem, and it seems that everyone is having different problems... which means that there are a lot of problems with the weather applet :(

For me, the "Set up weather" dialog has the Ok button always insensitive (gray'ed out). So I can never set it up.

---

### Post by Cherukuri_Raviteja on 2013-09-10
Thank u. I deleted that file and restarted the app.. Now it is working.. But the forecast of upcoming days is shown as not available.. Can you help me out of this please...

---

### Post by MrAli on 2013-09-10
i think it is better to report this problem as a bug in projects page.

---

### Post by twoey on 2014-02-05
> **lokijuhz said:**
> Hi,

I had the same problem today.

I solved it by installing python3, python3-gi, python3-dbus and python3-cairo.

Hope this helps.

As I read this I was wondering if it would give me any problems since I'm reading *Learning Python the Hard Way 3rd Ed.* and it says **not** to use python 3. If I was to install python3, would I run into any trouble as to trying to learn python with python 2.7?

---

