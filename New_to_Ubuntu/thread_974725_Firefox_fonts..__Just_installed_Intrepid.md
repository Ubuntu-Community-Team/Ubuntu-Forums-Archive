---
title: "Firefox fonts..  Just installed Intrepid"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by neurostu on 2008-11-07
I just upgraded to Intrepid and fonts look totally different under Intrepid then they did in Hardy. I've checked all my settings and they are the same but the fonts are different...

What could be causing this?

---

### Post by ciscosurfer on 2008-11-07
Check your rendering. Also, maybe you had the msttcorefonts package installed before?

---

### Post by neurostu on 2008-11-07
So its not msttcorefonts, I've tried that package several times and everytime I feel like it makes thing more ugly so I've tried avoiding it as much as possible.

I'm pretty sure its a firefox issue because fonts everywhere else in the system look fine.

---

### Post by ciscosurfer on 2008-11-07
Could you post a screenshot of what you're seeing?

---

### Post by OrangeCrate on 2008-11-07
> **neurostu said:**
> I just upgraded to Intrepid and fonts look totally different under Intrepid then they did in Hardy. I've checked all my settings and they are the same but the fonts are different...

**What could be causing this?**

I assume you have this covered, but is "ubuntu-restricted-extras" installed? 

[http://packages.ubuntu.com/intrepid/ubuntu-restricted-extras](http://packages.ubuntu.com/intrepid/ubuntu-restricted-extras)

And, your font settings are the same in both Hardy and Intrepid?

Edit > Preferences > Content > Fonts & Colors

If all of this is the same, as suggested above, please let us see a screenshot, and maybe we can help you figure it out.

As a point of reference, Firefox renders the same on both of my computers after moving from Hardy to Intrepid.

---

### Post by bjtuna on 2008-11-08
I got smooth fonts working in Firefox under Intrepid. On my system, I've got some LCD smoothing set in Preferences->Appearance->Fonts. I created a ~/.fonts.conf file that used the available values from [http://www.fontconfig.org/fontconfig-user.html](http://www.fontconfig.org/fontconfig-user.html) to replicate the settings in Appearance->Fonts. This is what I put in ~/.fonts.conf:

```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="autohint" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="lcdfilter" >
   <const>lcddefault</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>false</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintslight</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>


```

Then, restart Firefox.

---

### Post by chanders on 2008-11-11
Beautiful. Simply beautiful.

---

