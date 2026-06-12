---
title: "Unity weather app?"
date: 2011-09-24
forum: New to Ubuntu
---

### Post by stalkier on 2011-09-24
Ok not a huge issue. I have been using 11.04 for a while now but have been using the Classic Interface. I decided to go head on into Unity and I miss my weather next to my time. I'm wondering if there is an option for showing weather on the taskbar. If so, how do I enable it. Thanks so much.

---

### Post by wildmanne39 on 2011-09-24
Hi, here is a link to install it and several others if you would like.
[http://askubuntu.com/questions/30334/list-of-application-indicators](http://askubuntu.com/questions/30334/list-of-application-indicators)
Thank you

---

### Post by HuaiDan on 2011-09-24
You can try My-Weather-Indicator, which is a taskbar applet. There's a PPA you need add to your software sources in order to get it:  'ppa:atareao/atareao'.

Another option would be to go to your login settings and re-enable Gnome classic.


Hope that helps.

---

### Post by papibe on 2011-09-24
I love the weather thingy!

Unity works with a new weather indicator, you can install the default:
```
$ sudo apt-get install indicator-weather
```
But I think this version is a bit better (recommended [here]("http://askubuntu.com/questions/30334/list-of-application-indicators")):
```
$ sudo add-apt-repository ppa:weather-indicator-team/ppa
$ sudo apt-get update
$ sudo apt-get install indicator-weather
```
Sometimes the installation didn't start the application. If you don't see the indicator running right after the install just running it manual from dash.

I really like the new forecast feature.

One con is that it's not placed right besides the time, but you get used to it.

Hope it helps,
Regards.

---

### Post by stalkier on 2011-09-24
Thanks for all the help guys.

---

### Post by wildmanne39 on 2011-09-24
Hi, your welcome!

---

### Post by nualaor on 2011-12-25
I thank everyone, esp papibe.
My choice is indicator-multiload

---

