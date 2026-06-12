---
title: "Purple colour calibration problems (Maybe gamma correction)"
date: 2014-06-19
forum: New to Ubuntu
---

### Post by icelechi2 on 2014-06-19
Hi,

I have a problem with images and videos in Ubuntu with purple colours.
They seem oversaturated.

I don't know if it's a gamma correction issue but it really bugs me.

Does anyone else have this problem?

Does anyone have a solution?

Thanks.

---

### Post by tgalati4 on 2014-06-20
What is your monitor?  Is it a laptop or a desktop?  Normally colors are corrected with a color profile using ICC files.

Quick overview:

[https://help.ubuntu.com/community/UbuntuStudioPreparation#Color_management](https://help.ubuntu.com/community/UbuntuStudioPreparation#Color_management)

Gnome Color Manager:

[http://askubuntu.com/questions/334636/how-to-use-gnome-color-manager-in-ubuntu-12-04](http://askubuntu.com/questions/334636/how-to-use-gnome-color-manager-in-ubuntu-12-04)

```
apropos color
man colormgr
```

---

### Post by icelechi2 on 2014-06-20
Sorry about that. I'm a bit of a beginner.

**Laptop:** HP Pavilion TouchSmart 15-n065sa
**OS:** Ubuntu Gnome 14.04
**Processor:** Intel Core i5 4200u
**RAM:** 8GB
**HDD:** 750GB HDD
**Graphics:** Intel HD Graphics 4600
**Monitor:** HD WLED BrightView Touchscreen

Thanks

---

### Post by icelechi2 on 2014-06-29
Ok, I think I found a solution.

I went into the settings and selected **Device Colour Profiles** 

I then selected **Add Profile** 

Then I selected **D65**

This seems to have addressed the problem

I'll update if there are any changes. Thanks for all the input.

---

### Post by tgalati4 on 2014-06-29
D65 is a setting used to simulate Daylight with 6500 degrees Kelvin.  Some light sources and camera equipment are calibrated to D50 or D55, which is 5000 or 5500 degrees Kelvin.  6500K is similar to northern skylight with a bluish cast, 5000K is similar to direct sunlight with a pure white cast.  If you research your display, you can discover what its color profile was designed to be.  sRGB is an Adobe standard from years ago that works with many VGA monitors, but newer LED displays will have a different color profile than phosphor-based, cathode-ray tubes--old style monitors.

If you need more tweaking than D65, then you can set a custom color profile by shooting a color card (like a MacBeth Color Checker) and hold it up to your display and tweaking the color settings so that they look the same in the light of your workspace.  Because a laptop moves around, this is not very helpful.  Your laptop display will change depending on what light you are under--natural daylight versus flourescent indoor light.  The color of the light from your display does not change, but your perception of color changes under different lighting conditions.

---

