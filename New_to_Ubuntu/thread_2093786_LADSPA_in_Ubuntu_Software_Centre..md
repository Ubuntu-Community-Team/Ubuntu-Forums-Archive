---
title: "LADSPA in Ubuntu Software Centre."
date: 2012-12-11
forum: New to Ubuntu
---

### Post by Lapsang Souchong on 2012-12-11
Good Evening All,

First off, thanks to Ubuntu and the entire Linux community for being there when I decided to start making the switch from Windows.  I tried a few distributions (Fedora, Mint and Ubuntu, several flavours of each) but came back to Ubuntu (LTS version, wasn't overly keen on the Amazon thing in 12.10) again and again.  

I'll confess that I've not yet switched over completely (currently running two computers next to each other and punching up tutorials on the Windows machine whilst carrying them out on the Ubuntu Machine) but give it time. I'm definitely spending more time on the Ubuntu machine.

Anyway, I have a question. I've used Audacity for a while but was surprised when I loaded it up from the Software centre to find that there was no GVerb in the effects.  Now over the last few days of distro hopping I've seen that there were some LADSPA plugins available on at least one of the software centres, and that one (Steve Harris if I recall correctly) had all the reverbs and that it just slotted in to Audacity, although that may have been on the Linux Mint centre), however I thought I'd seen it in Ubuntu also.

This time, I install Ubuntu and find that there are no reverb LADSPAs in the software centre and the only way that it seems possible to get the plugins is via Steve Harris' website as a tarball.

Now I've come some of the way in the short time of experimenting with Linux but I still find installing a tarball a tad intimidating (am only a baby Linux user as yet afterall).

Can anyone tell me either; 

a: How do I download and install the tarball so that it will integrate nicely with Audacity (please use baby instructions).

b: If I've done something wrong that I can't see the LADSPA plugins in the software centre and how to rectify this.

Many apologies for the short essay and thank you all yet again.

):P

Cheers,

Lapsang.

---

### Post by vasa1 on 2012-12-11
A search for ladspa via Synaptic gave me **swh-plugins** aka "Steve Harris's LADSPA plugins" version 0.4.15+1-6 and a whole lot of other ladspa related stuff. No idea which one will be the one you want.

One thing re. the USC (from when I last used it): there's a button or option near the bottom left to show technical items. You may need to turn that  on.

---

### Post by Lapsang Souchong on 2012-12-12
> **vasa1 said:**
> A search for ladspa via Synaptic gave me **swh-plugins** aka "Steve Harris's LADSPA plugins" version 0.4.15+1-6 and a whole lot of other ladspa related stuff. No idea which one will be the one you want.

One thing re. the USC (from when I last used it): there's a button or option near the bottom left to show technical items. You may need to turn that  on.

Hi Vasa1,

Thank you for that.  Perfect!  I'm now happily able to add more effects to my meagre musical efforts.:guitar:  It was exactly where you said.

Can't believe that I spent all that time trying to remember Command Terminal stuff and forgot to use my eyes.

Many thanks again,

Lapsang.

---

### Post by andrew.46 on 2012-12-12
> **Lapsang Souchong said:**
> Can't believe that I spent all that time trying to remember Command Terminal stuff and forgot to use my eyes.

From the commandline:

```

andrew@corinth:~$ **[COLOR="Red"]apt-cache search ladspa | grep -i harris[/COLOR]**
swh-plugins - Steve Harris's LADSPA plugins

```

and a simple:

```
apt-cache search ladspa
```

reveals a pretty impressive listing of ladspa related packages.

---

### Post by Lapsang Souchong on 2012-12-13
> **andrew.46 said:**
> From the commandline:

```

andrew@corinth:~$ **[COLOR="Red"]apt-cache search ladspa | grep -i harris[/COLOR]**
swh-plugins - Steve Harris's LADSPA plugins

```

and a simple:

```
apt-cache search ladspa
```

reveals a pretty impressive listing of ladspa related packages.

Hi Andrew,

Fantastic.  Thanks for that too.

Cheers,

Lapsang.

---

