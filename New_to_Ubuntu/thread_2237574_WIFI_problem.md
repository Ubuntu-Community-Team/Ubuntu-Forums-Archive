---
title: "WIFI problem"
date: 2014-08-02
forum: New to Ubuntu
---

### Post by Val87 on 2014-08-02
During Skype video call i noticed that the connection - internet access disappears but the wifi icon says connected.
Maybe it happens on other occasions, but of course when call drops you notice it more. 
Funny thing i thought this was the router problem, but no, if at the same time i open a page on my smarpthone connected to same wifi, internet is there.
Anyone any ideas, as to why it is the issue?

---

### Post by NM5TF on 2014-08-02
need a little more info to be of any help..

does this happen JUST with Skype or does it happen connected to the 'net in general ?? 

is this a OLD symptom or has it happened since an update/upgrade ??

what distro are you using ???

tommy

---

### Post by Val87 on 2014-08-02
Hey Tommy,
Thank you.
Well i installed Ubuntu 14.04 after ditching windows maybe 4 days ago, but hell broke out today evening.
It is a 64 bit instllation. 
Whenever i try to talk vide on skype with my girlfriend, after sometime and maybe a little later, the call cuts off and drops.
I go to browser try to open a window, but there is no internet to open it, for like 3-4 minutes, the internet comes back.
If i would try the video call again, it would drop.
If i look at any time at the status bar of WIFI connection, it says it is always connected. It is like it is still connected to WIFI signal but there is no internet.
I go that moment to my smartphone, and i have internet there, whil on ubuntu none for few minutes, i ended up making the calls from my smartphone :)

---

### Post by Val87 on 2014-08-02
UPDATE:
Now skype was just running in the background. No video call. Internet went out for a few minutes again... this is driving me insane IT is an ASPIRE 5750 with a Broadcom wifi adapter.
And no on 13.10 or 13.04 or Win 7 i never had this problem.

---

### Post by Val87 on 2014-08-02
UPDATE been about 15 minutes, skype has been off completely no distruption, skype version 4.3

---

### Post by Val87 on 2014-08-02
UPDATE Skype 4.3 not active, no distruption.

---

### Post by Bucky Ball on 2014-08-02
Did you install Skype via the repositories? 4.3 has only recently been available via a regular update/upgrade.

---

### Post by Val87 on 2014-08-02
Took the .deb the 12.04 multiarch from the website, doubleclick on it and it installed in software centre then...

---

### Post by Val87 on 2014-08-02
Did this:

sudo dpkg --add-architecture i386
sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) $(lsb_release -sc) partner"
sudo apt-get update && sudo apt-get install skype

This should have brought the latest up to date version, right?
Well it downloaded something and installed, if it was up to date, it would not have done that?

Don not know if it is going to fix the issue. Have no one to videocall at this late hour. :D

So the .deb from skype website is not the newest version then?


UPDATE no calls made, but its running in the backround and has been no distruption in internet, well see how it goes with a video call tomorrow.
Can a certain software really affect that much the system?

---

### Post by Rrory on 2014-08-02
Hi; I am having a problem also connecting to wi-fi since Friday afternoon after the previous update. I took my Toshiba laptop (which never had a problem connecting and only runs Ubuntu) into the same room with my chromebook. The chromebook connects instantly via wi-fi, the laptop keeps searching for the signal. My skype also doesn't work.

---

### Post by Val87 on 2014-08-02
> **Rrory said:**
> Hi; I am having a problem also connecting to wi-fi since Friday afternoon after the previous update. I took my Toshiba laptop (which never had a problem connecting and only runs Ubuntu) into the same room with my chromebook. The chromebook connects instantly via wi-fi, the laptop keeps searching for the signal. My skype also doesn't work.

Yours can be a driver issue, or firmwire, or even the adapter itself....
Mine is what seemed to be a application specific issue.

---

### Post by Rrory on 2014-08-02
Hmm, all I know is I took out my dying Asus with un-updated Trusty Tahr and it connects to the internet easily in the same room(s) that my updated Toshiba won't.

---

### Post by Val87 on 2014-08-02
UPDATE: After running it with no video call, no issue with internet after updating 4.3 via terminal. Performed Skype tesst call, no video but no distruption in connection.

---

### Post by NM5TF on 2014-08-02
> **Val87 said:**
> UPDATE:
Now skype was just running in the background. No video call. Internet went out for a few minutes again... this is driving me insane IT is an ASPIRE 5750 with a Broadcom wifi adapter.
And no on 13.10 or 13.04 or Win 7 i never had this problem.

there seems to some problem with Broadcom adapters under Ubuntu or Mint...don't if your adapter is the bcm4311 or not...

to find out what adapter you have try this:

```
sudo lshw -c network
```

if it is the bcm4311, several people have had some success going here & following the instructions:

[http://linuxg.net/how-to-fix-broadcom-bcm4311-wireless-driver-on-ubuntu-and-linux-mint/](http://linuxg.net/how-to-fix-broadcom-bcm4311-wireless-driver-on-ubuntu-and-linux-mint/)


tommy

---

### Post by Bucky Ball on 2014-08-03
> **NM5TF said:**
> there seems to some problem with Broadcom adapters under Ubuntu or Mint...don't if your adapter is the bcm4311 or not...

FUD. The 4311 is old and extremely well supported, as are the majority of Broadcom cards now thanks to B43. Please check your sources. Sounds like they are old.

See here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access)

You will find the instructions to get the 4311, and many other Broadcom cards, up in a jiffy. The 4311 uses the wl driver.

---

### Post by Val87 on 2014-08-03
[ATTACH=CONFIG]255222[/ATTACH]

That is the adapter info. So far no distruptions. I think the 4.3 from Skype website is not newews another update required through terminal.
Ill keep u guys posted.

---

### Post by Val87 on 2014-08-03
UPDATE: Tried a video call with my Girlfriend.... Wifi went ...about minute in to call

---

### Post by oldrocker99 on 2014-08-03
I recently tried to connevct with Skype, and it failed the test call. I then connected using Google, and the call proceeded with no dropouts, and we could both hear and see each other.

---

### Post by Rrory on 2014-08-03
My problem solved itself with a simple reboot. Connected again:)

---

### Post by dave131 on 2014-08-03
> **Val87 said:**
> UPDATE: Tried a video call with my Girlfriend.... Wifi went ...about minute in to call

So......if you do the call without video, does the call stay up?

It sounds like a problem with actually using your webcam with Skype.  I haven't used Skype in what seems like eons (well, a year so  - can't get my elderly parents used to the idea of "press this button when you see this" so I can't video call with them ;) ), but I'll take a look and see if I can find a setting, etc..  I seem to remember, if this might be wrong, something about Skype starting support of HD video a year or so ago - I don't know for sure, but maybe this has something to do with it as well.

---

