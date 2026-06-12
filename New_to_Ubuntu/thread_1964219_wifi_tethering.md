---
title: "wifi tethering"
date: 2012-04-23
forum: New to Ubuntu
---

### Post by sperian on 2012-04-23
Hi,
Ive been trying to find a solution for a while with no luck. I have a Sony Ericsson neo which I use to tether it internet to my computer. I can tether it to my windows computer and too my friends iPhone and a htc desire. I can tether from that iPhone and desire to ubuntu, but for some reason the neo cant tether to ubuntu. If I use wicd it says "bad password". I saw so.e where say to put the password in inverted commas or between brackets, but both with no luck. If I use the standard network connections in ubuntu it will am for the password try connect and then ask just re ask for the password. If I turn the password off on my phone it still says bad password even if I change the settings on wicd and just gets to connect continuously if I use the network connection app that come with ubuntu. Any help will be good.
Cheers

---

### Post by PhantomTurtle on 2012-04-23
Tethering with android can be achieved using easy tether([http://www.mobile-stream.com/easytether/android.html]("http://www.mobile-stream.com/easytether/android.html")). The only thing is that you need to pay to use https websites, but everything else will work. Additionally most carriers charge extra for tethering, so beware of that.

---

### Post by sperian on 2012-04-23
my neo isn't rooted so i cant use easy tether. My carrier also doesnt charge extra for tethering, lucky for me, but i cant seem to use it:( 
Im not sure if the app on the phone is the problem, i can tether it to windows and iphones, but just not to ubuntu. i can tether a unrooted htc desire with no downloaded apps and an iphone to ubuntu.

---

### Post by PhantomTurtle on 2012-04-23
I have never used easy tether but their website says:
> does not require root access

Check this out as well(again no root): [https://play.google.com/store/apps/details?id=com.koushikdutta.tether&hl=en](https://play.google.com/store/apps/details?id=com.koushikdutta.tether&hl=en)

---

### Post by sperian on 2012-04-23
Both of them are only USB tethering only. And some of the easy tethering apps for android r really just shortcuts to the tethering thats part of the Rom.
If u plug tye phone in my comp via USB I recognizes it straight away and I can connect to the internet. It has something to do with the authentication when connecting via wifi.

---

### Post by 3rdalbum on 2012-04-23
The problem seems to be with the wireless driver on Ubuntu.

What wireless card do you have on the computer?

After trying to connect with Network Manager, please give us the last 20 lines of the command 'dmesg'. (so run the dmesg command in Terminal and copy the last few lines into a post here)

Also, what version of Ubuntu? Does wired tethering work?

---

### Post by sperian on 2012-04-24
> **3rdalbum said:**
> The problem seems to be with the wireless driver on Ubuntu.

What wireless card do you have on the computer?

After trying to connect with Network Manager, please give us the last 20 lines of the command 'dmesg'. (so run the dmesg command in Terminal and copy the last few lines into a post here)

Also, what version of Ubuntu? Does wired tethering work?

im using ubuntu 11.10. wired tethering does work, and so does wireless from htc desire running android 2.2 and iphone. i can wireless tether my phone (sony excrisson xperia neo running android 2.3) to windows.

[ 2212.587678] wlan0: direct probe to 8c:64:22:a9:58:6b (try 1/3)
[ 2212.784103] wlan0: direct probe to 8c:64:22:a9:58:6b (try 2/3)
[ 2212.984088] wlan0: direct probe to 8c:64:22:a9:58:6b (try 3/3)
[ 2213.184133] wlan0: direct probe to 8c:64:22:a9:58:6b timed out
[ 2218.879664] wlan0: direct probe to 8c:64:22:a9:58:6b (try 1/3)
[ 2219.076113] wlan0: direct probe to 8c:64:22:a9:58:6b (try 2/3)
[ 2219.276155] wlan0: direct probe to 8c:64:22:a9:58:6b (try 3/3)
[ 2219.476126] wlan0: direct probe to 8c:64:22:a9:58:6b timed out
[ 2225.161394] wlan0: direct probe to 8c:64:22:a9:58:6b (try 1/3)
[ 2225.360196] wlan0: direct probe to 8c:64:22:a9:58:6b (try 2/3)
[ 2225.560128] wlan0: direct probe to 8c:64:22:a9:58:6b (try 3/3)
[ 2225.760092] wlan0: direct probe to 8c:64:22:a9:58:6b timed out
[ 2237.087695] wlan0: direct probe to 8c:64:22:a9:58:6b (try 1/3)
[ 2237.284116] wlan0: direct probe to 8c:64:22:a9:58:6b (try 2/3)
[ 2237.484155] wlan0: direct probe to 8c:64:22:a9:58:6b (try 3/3)
[ 2237.684092] wlan0: direct probe to 8c:64:22:a9:58:6b timed out
[ 2243.361572] wlan0: direct probe to 8c:64:22:a9:58:6b (try 1/3)
[ 2243.560111] wlan0: direct probe to 8c:64:22:a9:58:6b (try 2/3)
[ 2243.760112] wlan0: direct probe to 8c:64:22:a9:58:6b (try 3/3)
[ 2243.960127] wlan0: direct probe to 8c:64:22:a9:58:6b timed out

---

