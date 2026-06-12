---
title: "Gnome-Shell got HUP stdin error ...."
date: 2011-07-22
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by 23dornot23d on 2011-07-22
Everytime I have tried to update and run Gnome-Shell in here I get the same error ....
was on the 32 bit before though ..... similar on 64bit ....

**Does no one else see this** ..... maybe its just relative to my Acer Aspire Laptop ...... who knows .....
I have reported the HUP error before on Launchpad ........

keithg@keith-Aspire-7730ZG:~/Documents$ uname -a
Linux keith-Aspire-7730ZG 3.0.0-6-generic #7-Ubuntu SMP Wed Jul 20 13:53:04 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux



Wish I knew what to do to fix it ...... what is the telepathy Client for anyway ?

> 
@keith-Aspire-7730ZG:~$ gnome-shell --replace
    JS ERROR: !!!   Exception was: TypeError: this._tpClient.set_delegated_channels_callback is not a function
    JS ERROR: !!!     lineNumber = '97'
    JS ERROR: !!!     fileName = '/usr/share/gnome-shell/js/ui/telepathyClient.js'
    JS ERROR: !!!     stack = '()@/usr/share/gnome-shell/js/ui/telepathyClient.js:97
Client()@/usr/share/gnome-shell/js/ui/telepathyClient.js:70
start()@/usr/share/gnome-shell/js/ui/main.js:148
@<main>:1
'
    JS ERROR: !!!     message = 'this._tpClient.set_delegated_channels_callback is not a function'
Window manager warning: Log level 32: Execution of main.js threw  exception: TypeError: this._tpClient.set_delegated_channels_callback is  not a function
keithg@keith-Aspire-7730ZG:~$ gnome-shell-calendar-server[2552]: Got HUP on stdin - exiting
Somewhere around here ...... so is it empathy !!! ..... will look see if any later upgrades ....
```

        // Allow other clients (such as Empathy) to pre-empt our channels if
        // needed
        this._tpClient.set_delegated_channels_callback(
            Lang.bind(this, this._delegatedChannelsCb));

        try {
            this._tpClient.register();
        } catch (e) {
            throw new Error('Couldn\'t register Telepathy client. Error: \n' + e);
        }
    },

```Well everything looks upto date ..... all the Empathy packages are loaded and uptodate
and the telepathy file I added too in case it was that ......


Fixed it ..... 17 more packages that were relative to telepathy ,,,, one of them must have done it ....
( Note - I only chose to upgrade the ones already marked in Synaptic ,,,,, not the others )

---

