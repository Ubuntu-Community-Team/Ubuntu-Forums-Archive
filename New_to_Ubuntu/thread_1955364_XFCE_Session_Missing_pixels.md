---
title: "XFCE Session Missing pixels"
date: 2012-04-09
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2012-04-09
My screen has a strange problem. The words & other objects appearing on the screen are missing pixels. For instance the Title of this post: XFCE Session Missing pixels, has pixels missing from the XFC (but not the E), the ssio of Session and the M ss fo Missing and the els of pixels. Not all the pixels are missing. The words are easily readable, but something is wrong.

When I first saw this, I rebooted (warm boot) thinking that could fix this. Not working that way.

I also have Windows 7 on this hard drive. Nothing is amiss there. Well, it's Windows what could go wrong?

---

### Post by ajgreeny on 2012-04-09
If this is only on text, I suspect it is related to the system font rendering or lack of antialiasing.  Have a good search for how you can change that in xubuntu, as I am not using it at the moment, but am on lubuntu with lxde, and I can't remember how it's done in xfce.

Font rendering is fine on this system with lubuntu, though I have not changed any of the font configuration on this machine, so far as I can remember.  However, if I do turn of antialiasing in the font configuration, text looks dreadful.

---

### Post by kazztan0325 on 2012-04-10
Hi Mark_in_Hollywood,

You would be able to enable anti-aliasing on XFCE Session as below.

1. Open **"Settings Manager"**.
( Menu > Settings > Settings Manager )

2. Click on **'Appearance'** icon, and then click on **'Fonts'** tab.

3. You will find **'Rendering'** option there.

4. Tick ON against the item **"Enable anti-aliasing"**.

5. As for **'Hinting'** and **'Sub-pixel order'** option, I myself also be not sure, sorry. At least for LCD screen of my notebook PC, it seems to be good to choose **Slight** as Hinting and to choose **RGB** as Sub-pixel order.

Hope this helps.

---

### Post by Mark_in_Hollywood on 2012-04-10
I have dropped XFCE and am in a Gnome (no effects) session. I use Chrome as a browser.

I've wanted to attach a screenshot of part of this problem I'm having. I doubt it has to do with anti-aliasing, but I'll log into XFCE and look at the config settings.

Bizarrely I took a screenshot of this post, while the artifact was visible. I went to edit the screenshot and the artifact was gone. The artifact was a box about 2 inches square covering the upper right hand side of this page. Where I see: **Thread: [ubuntu]** [COLOR="Red"]XFCE Session Missing pixels[/COLOR] - That is where the object is or was, I'm way too confused. I think it may have come via Facebook. Is this a Flash or Java problem??

---

### Post by Mark_in_Hollywood on 2012-04-10
> **kazztan0325 said:**
> Hi Mark_in_Hollywood,

You would be able to enable anti-aliasing on XFCE Session as below.

1. Open **"Settings Manager"**.
( Menu > Settings > Settings Manager )

2. Click on **'Appearance'** icon, and then click on **'Fonts'** tab.

3. You will find **'Rendering'** option there.

4. Tick ON against the item **"Enable anti-aliasing"**.

5. As for **'Hinting'** and **'Sub-pixel order'** option, I myself also be not sure, sorry. At least for LCD screen of my notebook PC, it seems to be good to choose **Slight** as Hinting and to choose **RGB** as Sub-pixel order.

Hope this helps.

[COLOR="Red"]**I find that anti-aliasing is checked.**[/COLOR]

---

### Post by kazztan0325 on 2012-04-10
> **Mark_in_Hollywood said:**
> [COLOR="Red"]**I find that anti-aliasing is checked.**[/COLOR]

Oh, really?

Then I cannot guess why ever does your screen look missing pixels at present, sorry.

---

