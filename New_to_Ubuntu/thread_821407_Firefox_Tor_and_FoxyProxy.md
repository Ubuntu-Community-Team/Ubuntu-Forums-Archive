---
title: "Firefox Tor and FoxyProxy"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by perito on 2008-06-07
I'm running Ubuntu Hardy with FireFox 3 Beta 5
I installed tor using
sudo apt-get install tor
sudo apt-get install Privoxy
Changed the config file to
[https://wiki.torproject.org/noreply/.../PrivoxyConfig](https://wiki.torproject.org/noreply/.../PrivoxyConfig)

and restarted

the next step is to install the tor button:
[https://addons.mozilla.org/firefox/2275/](https://addons.mozilla.org/firefox/2275/)
but Firefox is not allowing me (This add-on is for older versions of Firefox)

so I'm stuck, I have two options and I don't know what to pick:
1) I can install torbutton from here:
[http://torbutton.torproject.org/dev/](http://torbutton.torproject.org/dev/)
2) I can install FoxyProxy... but is it as good as tor ?
will it cover my IP address from different websites ? and if I do install this, I can remove tor and privoxy right?

Thanks for your help.

---

### Post by Heinzelotto on 2008-06-07
you don't necessarily need TorButton, you can set your preferences by hand to use Tor, just go to the proxy-settings and enter the adress and port of privoxy (localhost:9119 i can't remember it exactly). This will have the disadvantage though that you wont be able to switch between tor and non-tor as quickly as you can with torButton.

Update:
found something: [http://flim.cc/index.php/2008/05/11/torbutton-firefox-3-plugin/](http://flim.cc/index.php/2008/05/11/torbutton-firefox-3-plugin/)

---

### Post by perito on 2008-06-07
so you dont suggest for use torbutton (force the plugin) and you also dont suggest to use FoxyProxy ?

---

### Post by muteXe on 2008-06-09
How about reinstalling FF2?

---

### Post by perito on 2008-06-09
eh downgrade ... ? Is that a good option ? 

anywayz, I did install tor and FoxyProxy and it works great until now, although it slows the loading of the website alot and the more annoying thing is, at random times, it wont load the website at all, instead I'll recieve :
> Empty server or forwarder response.
The connection has been closed but Privoxy didn't receive any data.

does anyone know why/when it does that? and how to aviod it?

---

### Post by El Rogueo on 2008-06-12
> **Heinzelotto said:**
> you don't necessarily need TorButton, you can set your preferences by hand to use Tor, just go to the proxy-settings and enter the adress and port of privoxy (localhost:9119 i can't remember it exactly). This will have the disadvantage though that you wont be able to switch between tor and non-tor as quickly as you can with torButton.

Update:
found something: [http://flim.cc/index.php/2008/05/11/torbutton-firefox-3-plugin/](http://flim.cc/index.php/2008/05/11/torbutton-firefox-3-plugin/)

Clarification:

[https://torbutton.torproject.org/dev/](https://torbutton.torproject.org/dev/)

"There is currently one known unfixed security issue with Torbutton: it is possible to unmask the javascript hooks that wrap the Date object to conceal your timezone. We are working with the Firefox team to fix one of Bug 399274 or Bug 419598 to address this. In the meantime, it is possible to set the TZ environment variable to UTC to cause the browser to use UTC as your timezone. Under Linux, you can add an export TZ=UTC to the /usr/bin/firefox script, or edit your system bashrc to do the same."

If you must use torbutton, your best option is to edit that script ajd install the alpha from the above source.

Or, the simplest method is to use Foxyproxy; with luck the auto configuration will be all you need to do.

---

