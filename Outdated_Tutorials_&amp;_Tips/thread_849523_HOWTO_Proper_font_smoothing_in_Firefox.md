---
title: "HOWTO: Proper font smoothing in Firefox"
date: 2008-07-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Mazza558 on 2008-07-04
For some reason, font smoothing isn't enabled in Firefox 3. Applying this tweak will force it to use the same smoothing as your gtk settings.

**Step 1 - Open firefox settings page**

- Open a new window or tab and paste this into the address bar...

```
about:config
```


**Step 2 - Find and change the setting**

- After clicking the "I'll be careful" button, type "gfx" into the Filter bar.

- The bottom option, called 

```
gfx.use_text_smoothing_setting
```

is the one you want. Double-click to enable it, then restart Firefox.


**Step 3 - Test it!**

- Is your font quality better than before? Some fonts don't have any difference, whilst others (e.g ones downloaded yourself) do.

---

### Post by kerry_s on 2008-07-04
hmm, that's a "OS X" setting.

[http://kb.mozillazine.org/Gfx.use_text_smoothing_setting](http://kb.mozillazine.org/Gfx.use_text_smoothing_setting)

---

### Post by Mazza558 on 2008-07-04
> **kerry_s said:**
> hmm, that's a "OS X" setting.

[http://kb.mozillazine.org/Gfx.use_text_smoothing_setting](http://kb.mozillazine.org/Gfx.use_text_smoothing_setting)

I could have sworn it made a difference for me...

---

### Post by kerry_s on 2008-07-04
> **Mazza558 said:**
> I could have sworn it made a difference for me...

it might, it sounds like it just makes the browser respect system settings. linux and os x use different smoothing engines, but it might be close enough to give a little help.

any which way, i see no harm in leaving it on.

---

### Post by kerry_s on 2008-07-04
there is one you might want to try:
[http://kb.mozillazine.org/Browser.display.auto_quality_min_font_size](http://kb.mozillazine.org/Browser.display.auto_quality_min_font_size)

it's a quality over speed thing, so only you can decide what you prefer.

---

### Post by chucky chuckaluck on 2008-07-04
ouch! looks horrible for the font i use (urw palladio l), but it'll probably help some other fonts. good to know.

---

### Post by deejross on 2008-10-24
I don't mean to resurrect a dead thread, but I just installed Intrepid and tried this trick and it totally works! I'm using the Liberation fonts from Red Hat and Firefox looks awesome now....thanks for this!

---

### Post by Mazza558 on 2008-10-25
Glad to know it worked for someone else :)

---

### Post by K.Mandla on 2008-10-25
Moved to Tutorials and Tips.

---

### Post by Tomosaur on 2008-10-25
This definitely worked for me - thanks! I always hated how my fonts looked in Firefox on Ubuntu compared to Firefox on Windows, now they're pretty much the same!

---

### Post by nucleuskore on 2008-10-25
On your Ubuntu Desktop, click on System->Administration->Synaptic

In Synaptic click on settings->Repositories,and in that make sure all are ticked as shown below, especially the one which is highlighted

[[IMG]http://img66.imageshack.us/img66/3870/ubuntulib1xm5.th.png[/IMG]](http://img66.imageshack.us/my.php?image=ubuntulib1xm5.png)

Click close and click the Reload button in synaptic

After everything is refreshed, click Search and look for liberation, you will get a package named ttf-liberation, mark that for installation by clicking on it and click the Apply button. Liberation fonts will get downloaded and installed on to your system.

Now close synaptic, and click on System->Preferences->Appearance

[[IMG]http://img148.imageshack.us/img148/266/ubuntulib2vg0.th.png[/IMG]](http://img148.imageshack.us/my.php?image=ubuntulib2vg0.png)

In the dialog box that opens click on the fonts tab

[[IMG]http://img356.imageshack.us/img356/95/ubuntulib3mg5.th.png[/IMG]](http://img356.imageshack.us/my.php?image=ubuntulib3mg5.png) [[IMG]http://img236.imageshack.us/img236/2668/ubuntulib4rh0.th.png[/IMG]](http://img236.imageshack.us/my.php?image=ubuntulib4rh0.png)

Now in that you will see fonts for various purposes, application, desktop etc. Change each one to the liberation equivalent by clicking on it. So change sans to liberation sans, mono to liberation mono, sans bold to liberation sans, and in that select bold.

Open Firefox
Click on Edit->Preferences->Content
Change as follows

[[IMG]http://img143.imageshack.us/img143/3303/ubuntulib5qf4.th.png[/IMG]](http://img143.imageshack.us/my.php?image=ubuntulib5qf4.png)

Click on Advanced and change as follows

[[IMG]http://img143.imageshack.us/img143/5906/ubuntulib6bp6.th.png[/IMG]](http://img143.imageshack.us/my.php?image=ubuntulib6bp6.png)

**Also uncheck allow pages to choose their own fonts**

Now see the difference.

---

### Post by chele on 2009-02-12
I set **browser.display.auto_quality_min_font_size** to 8. The default is to use fast but ugly fonts for anything below 20, which is pretty much everything.

---

### Post by steveneddy on 2009-02-12
I think it helped mine, too.

---

### Post by SilverWave on 2010-01-29
> **kerry_s said:**
> there is one you might want to try:
[http://kb.mozillazine.org/Browser.display.auto_quality_min_font_size](http://kb.mozillazine.org/Browser.display.auto_quality_min_font_size)

it's a quality over speed thing, so only you can decide what you prefer.

**This setting is key** by default(20) its almost never used.

As I wanted text to be **optimized for display quality** I set ```
browser.display.auto_quality_min_font_size = 0

```**Much Much better!**

> **Possible values and their effects**

 A non-negative integer, specifying device pixels. Text rendered at  this size or larger is optimized for display quality rather than display  speed. Default is 20. 
**Caveats**

 
[LIST]
[*] Text in chrome (the UI) is always rendered with the  high-quality path.
[*] Web pages can override the effects of this preference by  specifying the text-rendering CSS property.
[/LIST]
  **Recommended settings**

 To use the highest quality display and legibility settings for all  rendered text, set this preference to 0. Conversely, setting this  preference to a very high number will cause Mozilla to use the fastest  rendering methods for all text. 
I don't think **gfx.use_text_smoothing_setting** makes any difference on Linux... but it would be useful if others could confirm.

---

### Post by gareththomasnz on 2010-06-09
Gos I wish I hadn't just done that - its smooth but looks horrible

---

