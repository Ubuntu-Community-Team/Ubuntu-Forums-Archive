---
title: "KNOPPIX 6.0 released with LXDE as default."
date: 2009-01-29
forum: Other OS Talk
---

### Post by kagashe on 2009-01-29
Anybody tried KNOPPIX 6.0?

kagashe

---

### Post by binbash on 2009-01-29
I am downloading right now.

---

### Post by Neural oD on 2009-01-29
not yet - but will give it a download later

---

### Post by ibutho on 2009-01-29
I've been tinkering with it for a couple of hours. Seems like a solid release, but if you prefer graphical apps its a bit bare at the moment. Maybe there will be a dvd release later on.

---

### Post by MethodOne on 2009-01-29
The only problem with this release of Knoppix is that it speaks your passwords out loud, like when filling out a Web form or connecting to an SSH server.  Unlike the previous releases, this one tends to be targeted towards blind people.

---

### Post by cardinals_fan on 2009-01-29
That's very interesting.

---

### Post by cmay on 2009-01-29
> **MethodOne said:**
> The only problem with this release of Knoppix is that it speaks your passwords out loud, like when filling out a Web form or connecting to an SSH server.  Unlike the previous releases, this one tends to be targeted towards blind people.
my eyes are operated so i cant see that well. after reading this post of yours i am downloading it for sure. thanks a lot for the infomation.

---

### Post by wolfen69 on 2009-01-29
i just tried it and it looked great and came with some good apps, but when i opened iceweasel (firefox clone), i found it did not render web pages very well, and could not get flash to work after installing it from the repos. let us know if the same thing happens for you. (whoever you may be)

---

### Post by ibutho on 2009-01-29
> **MethodOne said:**
> The only problem with this release of Knoppix is that it speaks your passwords out loud, like when filling out a Web form or connecting to an SSH server.  Unlike the previous releases, this one tends to be targeted towards blind people.

At the boot prompt, enter "knoppix" and you will boot straight into the LXDE and you also won't have the screen reader enabled if it annoys you.

---

### Post by smartboyathome on 2009-01-30
> **wolfen69 said:**
> i just tried it and it looked great and came with some good apps, but when i opened iceweasel (firefox clone), i found it did not render web pages very well, and could not get flash to work after installing it from the repos. let us know if the same thing happens for you. (whoever you may be)

Iceweasel isn't a firefox clone, it is Firefox itself rebranded and stripped of proprietary elements. If it is rendering worse than Firefox itself, it is because the sites you use don't recognise your user agent, and display stuff which doesn't work very well with Firefox.

---

### Post by wolfen69 on 2009-01-30
firefox in ubuntu and other distros work perfect. even iceweasel in lenny was fine. oh well, don't really care, as live cd's are a dime a dozen these days anyway. back in the day, knoppix was the bomb though.

lxde is cool, but overall i think there are better live cd's out there.

---

### Post by kagashe on 2009-01-30
> **smartboyathome said:**
> Iceweasel isn't a firefox clone, it is Firefox itself re-branded and stripped of proprietary elements. If it is rendering worse than Firefox itself, it is because the sites you use don't recognise your user agent, and display stuff which doesn't work very well with Firefox.What is the remedy?

By the way I wrote this thread after starting the download through Torrent. It took me a few hours as the speed of this connection is limited to 256 Kbps. After the download was finished I checked the md5sum and went to sleep. Since this morning I was trying frugal install after copying the iso to a partition but got this error:
> sh: can't access tty: job control turned offI searched and got a solution like:
> # modprobe piix
# exit
but it did not work.

Ultimately I burnt a CD and using the Live CD now after typing 'knoppix' at :boot prompt.

I am impressed with the default COMPIZ over default LXDE. The default settings of COMPIZ are good specially the cube with rotating gears inside and the effect when you close an application (screen-shots attached).

If the rendering in Iceweasel could be improved it will be a nice Live CD to have with following applications:
GnomeMplayer with multimedia codecs (I tried wma and mp3)
GIMP ImageViewer xpdf
CCSM LXRandR
gconf-editor NM_Applet(0.70) PCManFM Synaptic Wavelan Xsceernsaver
elinks Icedove Iceweasel Pidgin Java6_Web_start
Open_Office_3.0.1
Leafpad LXTerminal Orca File_search_utility XArchiver

on LXDE/COMPIZ
with Linux 2.6.28 and Xorg 7.3 (xserver 1.4.2)

kagashe

---

### Post by smartboyathome on 2009-01-30
> **kagashe said:**
> What is the remedy?

Install user agent switcher and create a user agent which emulates Firefox 3. ;)

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

I recommend this site to help you with creating your user agent.
[http://whatsmyuseragent.com/](http://whatsmyuseragent.com/)

Here is my user agent from Firefox 3.0.5 on Puppy Linux:
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.5) Gecko/2008120121 Firefox/3.0.5

---

### Post by Crafty Kisses on 2009-01-31
I really liked Knoppix 4.0, that was a very nice distro, I will give this one a shot later.

---

### Post by Ptero-4 on 2009-02-01
Wow. How they placed compiz over lxde. AFAIK lxde is just a taskbar and openbox doing the menu/launcher stuff, wouldn´t emerald replace openbox leaving the user with no root menu/launchers?

---

### Post by smartboyathome on 2009-02-01
> **Ptero-4 said:**
> Wow. How they placed compiz over lxde. AFAIK lxde is just a taskbar and openbox doing the menu/launcher stuff, wouldn´t emerald replace openbox leaving the user with no root menu/launchers?

The LXDE panel doesn't use the Openbox menu, it uses one compatible with GNOME.

---

### Post by maybeway36 on 2009-02-02
I sort of miss GParted and Konqueror :/
Oh well, at least I have Knoppix 5.3.1.

---

