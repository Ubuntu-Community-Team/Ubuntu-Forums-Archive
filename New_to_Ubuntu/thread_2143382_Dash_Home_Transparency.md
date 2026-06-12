---
title: "Dash Home Transparency"
date: 2013-05-08
forum: New to Ubuntu
---

### Post by GUZZLR on 2013-05-08
Hello All,
One thing I havent figured out yet:
When I open the applications area from the dash home, the window where all my applications are stored, is transparent so my desktop background shows through, making it difficult to see the applications. Is there a way to make the tranparency solid?
Thanks for the help

---

### Post by papibe on 2013-05-08
Hi GUZZLR.

You may try installing Ubuntu Tweak and play with the Dash color, opacity, and blur style. Take a look at this [tutorial]("http://www.howtogeek.com/112974/how-to-customize-ubuntu-with-ubuntu-tweak/").

Regards.

---

### Post by GUZZLR on 2013-05-09
Well, I tried this, and i do like the functionality of it, but i still have transperency when the dash home opens.  Thanks for the help

---

### Post by fantab on 2013-05-09
Install 'compiz-config-settings-manager'. And you will be able to 'control' transparency. See the screenshot:



[ATTACH=CONFIG]242411[/ATTACH]

---

### Post by GUZZLR on 2013-05-10
I installed this, and clicked on Ubuntu Unity Plugin. But my tabs do not resemble yours.  My tabs on top say: Behaviour, Switcher, Experimental.  Also, what does <Super> mean?
Thanks

---

### Post by fantab on 2013-05-10
<Super> generally means the 'windows' key (or the key with windows logo) on the keyboard.

Are you using 12.04? I am on "Saucy". Don't worry you have the same feature under 'experimental', I think, if not look around it will be there.

---

### Post by GUZZLR on 2013-05-11
[QUOTE=fantab;12642691]<Super> generally means the 'windows' key (or the key with windows logo) on the keyboard.

This is what I thought: Super = Windows Key.  I have converted chromebook to Ubuntu 12.10, which is why I was having difficulty.  I've been playing with it for sometime now, and I'm starting to believe there is no adjustment for what I'm looking for...which is adjusting the opacity for the menu window which pops up from the launcher icons.  so far all I've been able to find for opacity adjustment is the "Launcher" and the "Panel" (panel is the thin bar at the top of the screen, with battery, network connection, sound,etc...
Maybe this should be an area of concern for future releases of Unbuntu
I'm using Ubuntu 12.10 on a converted Chromebook

---

### Post by fantab on 2013-05-11
Well, I have no issue adjusting my DASH opacity. But then I can confirm on Precise, Raring and Saucy... 12.10 Quantal I cannot as I don't have it.

---

### Post by grahammechanical on 2013-05-11
In 12.04 and 12.10 we can use CCSM to set the top panel opacity to zero = transparent. I like it like that but In 13.04 & Saucy it is not enough. The Dash background shows across the top panel preventing from being truely transparent. The solution? Use CCSM to set the Dask background to 2. Then the top panel becomes transparent but so does the Dash. Sadly.

So, in CCSM>Ubuntu Unity Plugin>General tab (on 13.04) click Background color and you can adjust the level opacity for the background. Or rest it to default level by clicking the x tab. But you will loose top panel transparency on 13.04 but not (I think) on 12.04.

Regards.

---

### Post by mc4man on 2013-05-11
> **GUZZLR said:**
> 

I'm starting to believe there is no adjustment for what I'm looking for...which is adjusting the opacity for the menu window which pops up from the launcher icons.  so far all I've been able to find for opacity adjustment is the "Launcher" and the "Panel" (panel is the thin bar at the top of the screen, with battery, network connection, sound,etc...
Maybe this should be an area of concern for future releases of Unbuntu
I'm using Ubuntu 12.10 on a converted Chromebook

The opacity of the Dash (opens from top icon in launcher) is adjustable as described thru setting opacity level in 'Background Color'

The opacity of the quicklists, (r. click on any launcher icon) is non user adjustable

As far as  concern for future Ubuntu releases, I doubt it matters to Ubuntu/Canonical

---

### Post by GUZZLR on 2013-05-11
Well, I suppose I can do this:  Use my "Ubuntu Tweak" tool and just click on the Apps tab, which brings up all my apps in the U. Tweak window which has a solid white background...Maybe I'm just being a pain, but it's annoying to me to try and look at icons with the background showing through...thanks for everybody's help

---

### Post by mc4man on 2013-05-11
> **GUZZLR said:**
> Well, I suppose I can do this:  Use my "Ubuntu Tweak" tool and just click on the Apps tab, which brings up all my apps in the U. Tweak window which has a solid white background...Maybe I'm just being a pain, but it's annoying to me to try and look at icons with the background showing through...thanks for everybody's help

Then I guess you do mean the Dash - 
If you want it opaque then open the unity plugin settings as in screen 1
Under the experimental tab click on "Background Color",, raise the opacity level to a high value, 255 will be completely opaque  - screens 2 & 3
Leave the color @ #000000 for black, looks best

---

### Post by GUZZLR on 2013-05-11
yeah...I've been messing around with it for a while.  Making a super dark color and really bumping up the opacity all the way is probably the best way...it just makes the launcher super dark, so I loose the color I really liked. But I can see the icons much better.
I can live with it, especially considering it's so very much better than Microsoft.  I keep forgetting how nice it is to have an alternative to Microsoft with open source...
Thanks for everybody's help

---

### Post by fantab on 2013-05-11
> **GUZZLR said:**
> yeah...I've been messing around with it for a while.  Making a super dark color and really bumping up the opacity all the way is probably the best way...it just makes the launcher super dark, so I loose the color I really liked. But I can see the icons much better.
I can live with it, especially considering it's so very much better than Microsoft.  I keep forgetting how nice it is to have an alternative to Microsoft with open source...
Thanks for everybody's help

If you really like any color, then set that color in a lighter shade and make it opaque.

As an aside suggestion, you can install 'Cinnamon' desktop as an alternate to Unity. And to use it you have select it from Login Menu by clicking the Ubuntu icon next to your username. Cinnamon offers much more themeing than Unity.

To install cinnamon:
sudo apt-get install cinnamon

---

### Post by mc4man on 2013-05-11
They should have had a separate opacity level for the Dash itself so one didn't have to use a custom color to increase it.
(not an issue here as #000000 is fine.

Or just made the dash opaque, never understood the point of seeing thru it, who cares, when the Dash is open that's what one is using..

---

### Post by fantab on 2013-05-11
> **mc4man said:**
> They should have had a separate opacity level for the Dash itself so one didn't have to use a custom color to increase it.
(not an issue here as #000000 is fine.

Or just made the dash opaque, never understood the point of seeing thru it, who cares, when the Dash is open that's what one is using..

I like transparency effects. :D And I guess many of us do.

---

### Post by mc4man on 2013-05-12
> **fantab said:**
> I like transparency effects. :D And I guess many of us do.

Whether most people like or dislike for whatever reasons doesn't much matter, was/is the default of Design  in an experiment that is over.  (unity/compiz

---

### Post by GUZZLR on 2013-05-12
To install cinnamon:
sudo apt-get install cinnamon[/QUOTE]

so I tried the cinnamon install but it did not work, is there any steps beforehand for install?

---

### Post by arpanaut on 2013-05-12
I believe that on 12.04 you need to install through a PPA,
Not sure though???

[http://www.googlubuntu.com/](http://www.googlubuntu.com/)
should help.

---

### Post by fantab on 2013-05-12
If you are using 12.04 then:

```
sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
sudo apt-get update
sudo apt-get install cinnamon
```

---

