---
title: "Local time is not using UTC and wrong"
date: 2013-01-31
forum: New to Ubuntu
---

### Post by bonedriven on 2013-01-31
I'm in France. But my time shows +1 than the correct hour.

In terminal I tried to set timezone with  sudo dpkg-reconfigure tzdata

and set it to "Paris"

Now in terminal it shows:
Current default time zone: 'Europe/Paris'
Local time is now:      jeudi 31 janvier 2013, 12:28:01 (UTC+0100).
Universal Time is now:  Thu Jan 31 11:28:01 UTC 2013.

What does "local time" mean? I want to use the UTC time, which is correct. Thanks.

BTW, I'm using a live usb Ubuntu (with persistent file) on a new machine. I didn't have this problem with the previous machine.

---

### Post by furything on 2013-01-31
> What does "local time" mean? Local time should be the displayed time you see on your desktop and is appropriate to the 'local' time of your country/timezone.

UTC universal coordinated time is Standard British time or GMT with NO daylight savings.

If in France then you do want Local Time. the underlying PC time is in UTC so if the local time is wrong you need to click the date time panel and select change/adjust date time. 

Change the time to your local time and ignore utc. For me I am on gmt or utc so my clock shows 11:29 at time of posting

---

### Post by bonedriven on 2013-01-31
> **furything said:**
> Local time should be the displayed time you see on your desktop and is appropriate to the 'local' time of your country/timezone.

UTC universal coordinated time is Standard British time or GMT with NO daylight savings.

If in France then you do want Local Time. the underlying PC time is in UTC so if the local time is wrong you need to click the date time panel and select change/adjust date time. 

Change the time to your local time and ignore utc. For me I am on gmt or utc so my clock shows 11:29 at time of posting

[[IMG]http://img833.imageshack.us/img833/8481/screenshotfrom201301311.png[/IMG]](http://imageshack.us/photo/my-images/833/screenshotfrom201301311.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by furything on 2013-01-31
Using the panel you sent a picture off check manually and set the time correctly.

Apply/close digalogue.

Then reopen it and check back to internet and see if it remains the same or changes.

I know mine time syncs about 7 minutes different to windows so this is the linux time server.

Makes me wonder if you are picking up the correct time server.

try this link
[https://help.ubuntu.com/8.04/serverguide/NTP.html](https://help.ubuntu.com/8.04/serverguide/NTP.html)
to see how to change server and 
this link for ntp servers in france
[http://www.pool.ntp.org/zone/fr](http://www.pool.ntp.org/zone/fr)

---

### Post by Impavidus on 2013-01-31
If you have a dual boot machine there may be a mix-up of local time and UTC. Windows sets the clock in your computer to local time, Linux may interpret it as UTC, causing your UTC to be correct for your local time.

---

### Post by fantab on 2013-01-31
If you are using Ubuntu USB on a Windows machine than the machine time is actually in "Local Time". You just have to tell you Ubuntu to use "Local Time" because it is a bit complicated to set Windows time in UTC.

From terminal:

```
$ sudo gedit /etc/default/rcS
```In the file that opens set UTC=no and save the file and wait for a few minutes, your time will adjust itself correctly if you are online.

(or) do the reverse and see, that is change UTC=yes if it is set to 'no'.

good luck...

---

### Post by permieshane on 2013-04-14
> **fantab said:**
> If you are using Ubuntu USB on a Windows machine than the machine time is actually in "Local Time". You just have to tell you Ubuntu to use "Local Time" because it is a bit complicated to set Windows time in UTC.

From terminal:

```
$ sudo gedit /etc/default/rcS
```In the file that opens set UTC=no and save the file and wait for a few minutes, your time will adjust itself correctly if you are online.

(or) do the reverse and see, that is change UTC=yes if it is set to 'no'.

good luck...

Great this is the fix that sorted my time (finally) in Ubuntu 12.04.  I changed Utc=yes to no.
Thanks so much

---

