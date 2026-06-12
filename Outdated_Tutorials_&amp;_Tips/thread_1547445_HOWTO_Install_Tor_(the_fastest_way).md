---
title: "HOWTO: Install Tor (the fastest way)"
date: 2010-08-06
forum: Outdated Tutorials &amp; Tips
---

### Post by zerwas on 2010-08-06
[COLOR="DimGray"][SIZE="1"]Preface: Tor is a software to anonymize your activities (your IP address). Please note that not all of your internet traffic will be anonymous magically. Instead you need to understand what Tor does and [what it does not]("https://www.torproject.org/download#Warning").[/SIZE][/COLOR]

[CENTER][FONT="Arial Black"][SIZE="5"]= How to install and set up Tor in Ubuntu =[/SIZE][/FONT]
[IMG]http://upload.wikimedia.org/wikipedia/commons/f/ff/Tor_logo0.png[/IMG][/CENTER]
[SIZE="3"][LIST=1]
[*]To install and setup Tor, copy and paste the content from the box below and paste it into a terminal window (which you can find in [FONT="Courier New"]Applications[/FONT] -> [FONT="Courier New"]Accessories[/FONT] -> [FONT="Courier New"]Terminal[/FONT]). You can copy&paste the content of the whole box at once if you want to.

```
gksudo 'apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 886DDD89'
sudo add-apt-repository "deb http://deb.torproject.org/torproject.org $(lsb_release -s -c) main"
sudo apt-get update
sudo apt-get -y install tor-geoipdb polipo
sudo cp /etc/polipo/config /etc/polipo/config.bak
sudo wget -O /etc/polipo/config http://gitweb.torproject.org/torbrowser.git/blob_plain/HEAD:/build-scripts/config/polipo.conf
sudo service polipo restart
```That's it, you are done. Note, that every application (like Instant Messaging, Mail Client etc.) needs to be set up separately in order to use Tor: See step 2.

[*]Now it depends on which part of your Internet traffic you want to be anonymized; If you just want to browse the web anonymized, you need to install [Torbutton]("https://addons.mozilla.org/de/firefox/addon/2275/") for Firefox and click on the button in the bottom right corner in Firefox. To see if everything worked as it should, check [this website]("https://check.torproject.org/") from Tor Project. Enjoy your anonymity.
[/list][/SIZE]


[CENTER]= [SIZE="3"]Appendix[/SIZE] =[/center]

> [CENTER]What are all these cryptic commands?[/CENTER]

[SIZE="1"]
The "ubuntu way" (to use graphical tools whereever possible) of doing things isn't the most comfortable in this case. Instead, it is useful to use the [terminal]("https://help.ubuntu.com/community/UsingTheTerminal").

For those who are interested i will explain what these commands do:
[LIST]
[*]apt-key downloads the public key for the Tor repository and adds it to the keychain.
[*]add-apt-repository adds the Tor repository where the Tor package comes from.
[*]apt-get update updates the package database, apt-get install installs Tor itself and Polipo, a proxy that is needed.
[*]cp creates a backup of the Polipo configuration file.
[*]wget downloads a new configuration file and saves it in the correct place.
[*]service restarts the Polipo service so the changes can take effect without reboot.
[/LIST]
[/SIZE]

---

### Post by bodhi.zazen on 2010-08-08
Second fastest, the fastest is the TOR Portable bundle, which is quite nice :twisted:

It is available for both Linux and Windows:

[http://www.torproject.org/torbrowser/](http://www.torproject.org/torbrowser/)

runs out of the box and, IMO, comes with a very nice set of graphical configuration tools.

Also, I prefer privoxy to polipo, privosy adds adblocking (no need to slow down tor with adds, IMO).

---

### Post by bodhi.zazen on 2010-08-08
As a side note, you can run tor without a proxy (you do not need privoxy or polipo) and the utility of these proxies may be limited if you are behind a router.

---

### Post by zerwas on 2010-08-08
Thank you very much for your comments, wise bodhi.zazen.

> **bodhi.zazen said:**
> Second fastest, the fastest is the TOR Portable bundle, which is quite nice :twisted:
Right, but i am not sure about the fact that they say "the Tor Browser Bundle is under development and not yet complete.". But i removed the "(the fastest way)" ;-).
I am also unsure about if Tor, Polipo and portable Firefox will get security updates when available. The Fx version in the bundle is 3.5.10pre. If you simply use all applications out of the repository you always are on the safe side.

And with the bundle Tor gets shut down when portable Firefox is closed. Which may not be what some people want.
> Also, I prefer privoxy to polipo, privosy adds adblocking (no need to slow down tor with adds, IMO).
But Polipo is slim, fast and always worked for me and my friends. I sometimes had problems with Privoxy in the past, so i chose Polipo. Besides, the Browser Bundle also includes Polipo and you will find that Torproject.org also suggests using Polipo.
> you can run tor without a proxy (you do not need privoxy or polipo)Of course other applications can be torified without a proxy, but if you want to use a webbrowser with Tor you need a proxy, right?

I will expand the HOWTO in the future and hope i will be able to keep it updated.

---

### Post by bodhi.zazen on 2010-08-08
> **zerwas said:**
> Of course other applications can be torified without a proxy, but if you want to use a webbrowser with Tor you need a proxy, right?

No, that is a common misunderstanding. You can use the TOR network without a proxy. Proxies improve privacy is all (by cleansing your headers) but they are not necessary.

I understand why you may prefer polipo, and there is nothing wrong with that proxy. I was merely adding that that is not the only option. I will admit it takes a while to learn to configure privoxy, but for the most part privoxy works just fine and as I indicated, blocks adds (no need for additional extensions in firefox and no need to tunnel advertisements over TOR, so IMO is a wash in terms of speed, depending of course where you browse). 

The TOR bundle is, IMO, both very simple to use and very nice. I have not had a problem with them (even though they are in "Beta"). Why would you not want to shut down polipo and TOR if you are not using them ? I also like the portability, put the linux and windows versions on a flash drive and you are good to go =)

---

### Post by zerwas on 2010-08-08
> **bodhi.zazen said:**
> No, that is a common misunderstanding. You can use the TOR network without a proxy. Proxies improve privacy is all (by cleansing your headers) but they are not necessary.
I didn't know that. Could you explain how to torify a webbrowser without a proxy? Tor itself is a socks proxy, but a browser needs a HTTP proxy; that's why you will get this message when you configure your browser to use 127.0.0.1:9050 as proxy:
> Tor is not an HTTP Proxy

It appears you have configured your web browser to use Tor as an HTTP proxy. This is not correct: Tor is a SOCKS proxy, not an HTTP proxy. Please configure your client accordingly.

See [https://www.torproject.org/documentation.html](https://www.torproject.org/documentation.html) for more information. 

I understand why you may prefer polipo, and there is nothing wrong with that proxy. I was merely adding that that is not the only option. I will admit it takes a while to learn to configure privoxy, but for the most part privoxy works just fine and as I indicated, blocks adds (no need for additional extensions in firefox and no need to tunnel advertisements over TOR, so IMO is a wash in terms of speed, depending of course where you browse). 

> Why would you not want to shut down polipo and TOR if you are not using them ?
Because i still might have a torified Pidgin running at that moment. I also want to emphasize that it looks like the user won't get any security updates for Polipo, Tor and Firefox if he uses this bundle.

Thank you for mentioning Privoxy and the bundle, those are definitely alternate options. But to keep my HOWTO as simple as possible i won't let the user choose the proxy and stick with Polipo, just like the Tor people do in the documentation.

---

### Post by bodhi.zazen on 2010-08-08
> **zerwas said:**
> I didn't know that. Could you explain how to torify a webbrowser without a proxy? Tor itself is a socks proxy, but a browser needs a HTTP proxy; that's why you will get this message when you configure your browser to use 127.0.0.1:9050 as proxy:

You need to configure firefox to use a socks prosy.

See:

[http://vectrosecurity.com/content/view/68/](http://vectrosecurity.com/content/view/68/)

(I could not find a ow to with screen shots).
 

> Because i still might have a torified Pidgin running at that moment. I also want to emphasize that it looks like the user won't get any security updates for Polipo, Tor and Firefox if he uses this bundle.

Well, that is not exactly true, it is up to the user to track updates, but I understand your point.

> Thank you for mentioning Privoxy and the bundle, those are definitely alternate options. But to keep my HOWTO as simple as possible i won't let the user choose the proxy and stick with Polipo, just like the Tor people do in the documentation.

I was just enhancing you how to is all, if you had used privoxy, I would have suggested the other options (polipo and direct socks).

---

### Post by Gyoja on 2010-12-25
zerwas -

the location of the configuration file for polipo has changed:

[https://gitwehttps://gitweb.torproject.org/torbrowser.git/blob_plain/HEAD:/build-scripts/config/polipo.confb.torproject.org/torbrowser.git/blob_plain/HEAD:/build-scripts/config/polipo.conf](https://gitwehttps://gitweb.torproject.org/torbrowser.git/blob_plain/HEAD:/build-scripts/config/polipo.confb.torproject.org/torbrowser.git/blob_plain/HEAD:/build-scripts/config/polipo.conf)

other than that your series of commands worked like a charm.

thanks.

---

### Post by zerwas on 2010-12-25
> **Gyoja said:**
> 
the location of the configuration file for polipo has changed:

You are right. Thank you very much.

---

### Post by bodhi.zazen on 2010-12-25
> **Gyoja said:**
> zerwas -

the location of the configuration file for polipo has changed:

[https://gitwehttps://gitweb.torproject.org/torbrowser.git/blob_plain/HEAD:/build-scripts/config/polipo.confb.torproject.org/torbrowser.git/blob_plain/HEAD:/build-scripts/config/polipo.conf](https://gitwehttps://gitweb.torproject.org/torbrowser.git/blob_plain/HEAD:/build-scripts/config/polipo.confb.torproject.org/torbrowser.git/blob_plain/HEAD:/build-scripts/config/polipo.conf)

other than that your series of commands worked like a charm.

thanks.

Thank you for that information from me as well.

---

### Post by Sina_RJ on 2011-03-15
I hope you see this,cause this thread is for about a year ago!
I'm using ubuntu 10.10 and when i copy pasted what you said at first post here it says at last,what should i do?
code:

/etc/polipo/config: No such file or directory
moeen@Moeen:~$ sudo service polipo restart
polipo: unrecognized service

---

### Post by bodhi.zazen on 2011-03-16
> **Sina_RJ said:**
> I hope you see this,cause this thread is for about a year ago!
I'm using ubuntu 10.10 and when i copy pasted what you said at first post here it says at last,what should i do?
code:

/etc/polipo/config: No such file or directory
moeen@Moeen:~$ sudo service polipo restart
polipo: unrecognized service

Did you install polipo ?

---

