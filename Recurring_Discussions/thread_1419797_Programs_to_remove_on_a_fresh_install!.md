---
title: "Programs to remove on a fresh install!"
date: 2010-03-02
forum: Recurring Discussions
---

### Post by Rytron on 2010-03-02
Hi.
While I love using Ubuntu. There are a few programs that I never use or don't particularly like. On a fresh Ubuntu install I remove these: Empathy, Evolution, F-Spot & Tomboy

[LIST]
[*]I use Sunbird instead of Evolution (I only need a calendar function)
[*]I use gthumb instead of F-Spot
[*]I use Pidgin instead of Empathy
[/LIST]
What programs do you never use and remove?

---

### Post by snowpine on 2010-03-02
I do not remove programs I do not use, as I have ample hard disk space.

---

### Post by k@e on 2010-03-02
Quite a bunch, this is my purge list:

```
evolution-common evolution-data-server evolution-webcal gnome-games* gwibber human-theme humanity-icon-theme mono-runtime onboard pitivi rhythmbox software-center ^telepathy-* ubiquity-slideshow-ubuntu ubufox ubuntu-wallpapers ubuntu-xsplash-artwork ubuntuone* xcursor-themes xscreensaver-gl
```

---

### Post by Rytron on 2010-03-02
> **k@e said:**
> Quite a bunch, this is my purge list:

```
evolution-common evolution-data-server evolution-webcal gnome-games* gwibber human-theme humanity-icon-theme mono-runtime onboard pitivi rhythmbox software-center ^telepathy-* ubiquity-slideshow-ubuntu ubufox ubuntu-wallpapers ubuntu-xsplash-artwork ubuntuone* xcursor-themes xscreensaver-gl
```

Thats very comprehensive k@e. ;)

---

### Post by J_Stanton on 2010-03-02
removing apps doesnt make anything faster so i just leave everything and add others.

---

### Post by cariboo on 2010-03-02
This is not a T&E thread, moved to recurring, as it has been brought up so often.

---

### Post by Tibuda on 2010-03-02
I don't use Ubuntu anymore, but the last time I installed it, I used the minimal disk, so there were nothing for me to remove...

When I used standard Ubuntu, I replaced Rhythmbox for QuodLibet or Sonata. Pidgin was still the default, but I would replace Empathy in karmic.

---

### Post by unknownPoster on 2010-03-02
If you're going to remove lots of packages to begin with, you're better off just installing from the minimal disk or just installing one of the several minimalist distributions out there.

---

### Post by lisati on 2010-03-02
I didn't bother with a GUI on my old machine. For one thing, not enough RAM and it's probably getting too old and tired to mess around updating/upgrading it too much. Plus with the monitor being a bit unreliable, it's a good excuse to start expanding my horizons by using something like SSH.

---

### Post by juancarlospaco on 2010-03-02
[lol]
I use a minimal minimal kernel, and thinking on remove GNU userland toolkit because is bloated, but i removed the "rm" command with "shred"
[/lol]

---

### Post by Rytron on 2010-03-02
> **k@e said:**
> Quite a bunch, this is my purge list:

```
evolution-common evolution-data-server evolution-webcal gnome-games* gwibber human-theme humanity-icon-theme mono-runtime onboard pitivi rhythmbox software-center ^telepathy-* ubiquity-slideshow-ubuntu ubufox ubuntu-wallpapers ubuntu-xsplash-artwork ubuntuone* xcursor-themes xscreensaver-gl
```

Just curious. What does [COLOR="Indigo"]^telepathy-*[/COLOR] mean?

---

### Post by Tibuda on 2010-03-02
> **Rytron said:**
> Just curious. What does [COLOR="Indigo"]^telepathy-*[/COLOR] mean?

telepathy is the libraries/framework behind empathy.

---

### Post by Rytron on 2010-03-02
> **danielrmt said:**
> telepathy is the libraries/framework behind empathy.

Yes but what does the **[COLOR="Purple"]^[/COLOR]** symbol in front of it do?

---

### Post by Tibuda on 2010-03-02
> **Rytron said:**
> Yes but what does the **[COLOR="Purple"]^[/COLOR]** symbol in front of it do?

In regular expressions syntax, it means something starting with the expression. I don't see much sense in using this on a purge list, perhaps it is not a regex.

---

### Post by oldos2er on 2010-03-02
Let's see. I usually remove tracker, avahi, all the bluetooth software, samba, ntfs support, brltty and all the 'assistive technologies,' gdm (only in Karmic), laptop-tools, and other things I can't recall right--basically everything I know I'm never going to require.

---

### Post by juancarlospaco on 2010-03-02
Change the APT to use FTP because is faster, 
Change the APT to use Network/YourCountry Mirror because is faster,
Change the APT to use IP if mirror has Fixed IP because is faster.
:)

---

### Post by uRock on 2010-03-03
I just did an install where I uninstalled ubuntu-desktop and installed ubuntu-netbook. The minimal installer wouldn't work, neither would the server install, so I used desktop to get it installed. Of coarse the easiest way was unavailable. The UNR iso had no seeders.

---

### Post by k@e on 2010-03-03
> **Rytron said:**
> Just curious. What does [COLOR="Indigo"]^telepathy-*[/COLOR] mean?

It is a regular expression, meaning when given to apt-get it shall select any package starting with "telepathy-" and followed by anything else. This is because I do use pidgin in place of empathy but removing empathy would leave the telepathy framework behind. However, some libtelepathy-* should not be selected because some apps seem to depend on it.

In fact, I use this list to build my own customized Ubuntu live CD, where space matters a lot.

---

### Post by DubyBreaks on 2010-03-03
I add more than I remove, but mainly:  Rhythmbox (for G-que), Transmission (for Deluge), I don't uninstall but I do remove Movie Player from my menu and associations (for VLC), and all games except Mahjongg and gnometris.

---

### Post by Rytron on 2010-03-03
> **juancarlospaco said:**
> Change the APT to use FTP because is faster, 
Change the APT to use Network/YourCountry Mirror because is faster,
Change the APT to use IP if mirror has Fixed IP because is faster.
:)

Hi juancarlospaco.
Could you explain in detail?

---

### Post by juancarlospaco on 2010-03-03
> **Rytron said:**
> Hi juancarlospaco.
Could you explain in detail?

What do you dont understand...?
[I]FTP=Faster
Network Mirror=100Mb/s updates
IP Mirror=dont need to resolve namez[/I]

---

### Post by Rytron on 2010-03-03
I understand the words. I mean how do I implement it? Would this be done through 'Software Sources'?

---

### Post by juancarlospaco on 2010-03-03
> **Rytron said:**
> I understand the words. I mean how do I implement it? Would this be done through 'Software Sources'?

Yes, or manual editing your sources list.

Random example:
deb [ftp://192.168.0.1/ubuntu/](ftp://192.168.0.1/ubuntu/) karmic main restricted

deb [ftp://127.0.0.1/ubuntu/](ftp://127.0.0.1/ubuntu/) karmic main restricted

---

### Post by MelDJ on 2010-03-03
empathy, evolution, rhytmbox and computer janitor

---

### Post by DexterP17 on 2010-03-04
I don't like to remove the programs that come with the operating system. if the program has been replaced with a better one and the old application is still there then that's when i will remove the software. i learn to use the applications that come to the system.

---

