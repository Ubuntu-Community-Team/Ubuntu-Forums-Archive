---
title: "streaming of internet radio"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by beswatcher on 2008-11-06
Hello everybody, I am an occasional user of a Knoppix live CD and a "sick of BSOD" person who just loaded Ubuntu 8.04. I seem to have most everything working, including java and flash, but I'm having trouble setting up live streaming of internet radio. I like to listen to BBC news while on the net. As an example, I was able to listen to and watch Mr. Obama's thank you speech on the BBC site, but still unable to stream the "Live" radio broadcast later in the evening. 
What package should I install, and how? Help!!!

---

### Post by mapes12 on 2008-11-07
The BBC use iPlayer for streaming radio but this doesn't work for Ubuntu versions 8.04 and below. However, I have read that Ubuntu 8.10 is configured to work with it.

---

### Post by beswatcher on 2008-11-08
Thank you, mapes12. I may try to upgrade tomorrow when the local bandwidth is not so crowded. Through all of this, I downloaded RealPlayer 11 and can't even get it installed. I've tried everything I can but nothing seems to run in terminal. What am I doing wrong?

Real player 11

installation Instructions

- Ensure that the .bin file you downloaded is executable. You can make the .bin file executable by running the "chmod a+x RealPlayer11GOLD.bin" command from a terminal window. 

- Run the .bin file by typing "./RealPlayer11GOLD.bin". Follow the prompts provided to finish installing the player.

- When you launch the player for the first time, a set-up assistant will take you through configuring your player. 

- Enjoy your RealPlayer11 for Linux!


Thanks again

---

### Post by FreewheelinFrank on 2008-11-08
The BBC now uses Flash for streaming radio. It worked fine for me in 8.04, and works in 8.10. It would help if you could post the link you're trying to listen to so we can check if it works for us.

For example, if you right-click on the Radio 4 Listen Live link, this is the address:

[http://www.bbc.co.uk/radio/aod/radio4.shtml?fm](http://www.bbc.co.uk/radio/aod/radio4.shtml?fm)

Realpayer is in the repositories, although I never had any luck with it. The MPlayer Mozilla plug-in plays Realplayer stuff anyway.

---

### Post by mapes12 on 2008-11-08
> The BBC now uses Flash for streaming radio. It worked fine for me in 8.04, and works in 8.10. It would help if you could post the link you're trying to listen to so we can check if it works for us.

For example, if you right-click on the Radio 4 Listen Live link, this is the address:

[http://www.bbc.co.uk/radio/aod/radio4.shtml?fm](http://www.bbc.co.uk/radio/aod/radio4.shtml?fm)

I clicked on the Radio 4 link you gave and nothing happens? I've attached a screenshot. Do I need any add ons for Firefox for it to work?

---

### Post by gandaran on 2008-11-08
> **mapes12 said:**
> I clicked on the Radio 4 link you gave and nothing happens? I've attached a screenshot. Do I need any add ons for Firefox for it to work?

what you need is to remove the totem plugin and install the mozilla mplayer plugin, which is compatible with real audio and video play
and install the w32codecs from medibuntu repo [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by philinux on 2008-11-08
Post the contents of ```
about:plugins
```

Upgrading has caused problems with flash symlinks. A clean install is the way to go with home on it's own partition.

---

### Post by beswatcher on 2008-11-08
[img]http://www.smiliegenerator.de/s36/smilies-2524.png[/img]
The mplayer plugin seems to have worked!:D

---

### Post by FreewheelinFrank on 2008-11-08
> **mapes12 said:**
> I clicked on the Radio 4 link you gave and nothing happens? I've attached a screenshot. Do I need any add ons for Firefox for it to work?

Did the advice given by other posters help? Hope so.

---

### Post by mapes12 on 2008-11-08
Philinux,

This is what I get to the command you posted:

> mark@ubuntu-laptop:~$ about:plugins
bash: about:plugins: command not found
mark@ubuntu-laptop:~$ 

and I am lost about removing a Totem plugin and installing a mozilla mplayer plugin? Where do I find these please?

The smiley face has come up where the ":" was posted

---

### Post by FreewheelinFrank on 2008-11-08
> **mapes12 said:**
> Philinux,

This is what I get to the command you posted:



and I am lost about removing a Totem plugin and installing a mozilla mplayer plugin? Where do I find these please?

The smiley face has come up where the ":" was posted

about:plugins needs to be entered into the browser address bar, just like a web address.

The Totem and mozilla-mplayer plugins are found in System>Administration>Synaptic.

---

### Post by gandaran on 2008-11-08
> **philinux said:**
> Post the contents of ```
about:plugins
```

Upgrading has caused problems with flash symlinks. A clean install is the way to go with home on it's own partition.
philinux
can you explain how to type about:plugins on forum post's without the smilies getting in the middle?

---

### Post by FreewheelinFrank on 2008-11-08
Wrap in code tags:

```
about:plugins
```

[CO DE]about:plugins[/CO DE]

:p

---

### Post by mapes12 on 2008-11-09
> The Totem and mozilla-mplayer plugins are found in System>Administration>Synaptic.

Found them an did as you suggested. Thanks. Then went to the previously posted web link. A window popped up asking to search for required codecs. I OK'd it. It then said it wanted to install the Gstreamer package. I OK'd it. It installed and voila I can now listen to streaming BBC radio! :guitar:

---

