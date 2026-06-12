---
title: "[SOLVED] Can Compiz-Fusion work on standard graphics?"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by nuddernuby on 2008-07-21
Does CF require more than the standard onboard graphics capability of AMD or Intel chips?

---

### Post by Vivaldi Gloria on 2008-07-21
> **nuddernuby said:**
> Does CF require more than the standard onboard graphics capability of AMD or Intel chips?

It works with the better onboard ones like the Intel GMA 3100 I have. Ask if you have a particular graphics chip in mind.

---

### Post by Heinzelotto on 2008-07-21
Compiz-Fusion is very customizable (via compizconfig-settings-manager ("ccsm")), so you should be able to find effect-settings fitting your hardware.

edit: do these chips support opengl 3d-acceleration?

---

### Post by dracayr on 2008-07-21
I have a quite old toshiba laptop with an intel chipset, and it works. So the answer is no, it does not require more than the *standard* chips...

dracayr

---

### Post by nuddernuby on 2008-07-21
In this case it's a basic system running an AMD Sempron 2400+ CPU.
Where can one see what graphics chip is installed on the board?

When CCSM is opened, the following message appears:
> GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

Not only can I not find the Graphic chip description, but I can't even find **/apps/compiz/plugins/scale/allscreens/options/initiate_edge**!!!
Any advice would be great, thank you.

---

### Post by Vivaldi Gloria on 2008-07-21
> **nuddernuby said:**
> Where can one see what graphics chip is installed on the board?

I don't know about the compiz error you get. For the graphics chip try the following commands in a terminal:

```
lspci | grep VGA
sudo lshw -class display
sudo hwinfo --gfxcard
```

---

### Post by nuddernuby on 2008-07-21
Thanks V-G. The result shows that it's a Via chipset - VT8378 (S3 Unichrome).
Should that do the CF trick?

---

### Post by Kevbert on 2008-07-21
At present compiz-fusion is not officially supported on Via S3 graphics.

---

### Post by RomeReactor on 2008-07-21
> **nuddernuby said:**
> In this case it's a basic system running an AMD Sempron 2400+ CPU.
Where can one see what graphics chip is installed on the board?

When CCSM is opened, the following message appears:

Not only can I not find the Graphic chip description, but I can't even find **/apps/compiz/plugins/scale/allscreens/options/initiate_edge**!!!
Any advice would be great, thank you.

Hi. Regarding the error, you can clear the option by opening Gconf Editor from the terminal, or by pressing ALT+F2, and pasting:
```
gconf-editor
```
and follow the path the error mentions.

However, as Kevbert points out, it's very unlikely one can enable Compiz using a VIA or Savage integrated video card.

---

### Post by nuddernuby on 2008-07-22
Well, that seems to settle that one. Thank you for your contributions.  Looks like it's time for an upgrade!

---

### Post by 3rdalbum on 2008-07-22
You can pick up a discrete ATI or Nvidia card from your local computer retailer - you could quite happily get something behind the curve, like a 7600, and still get whizzy Compiz effects.

---

### Post by nuddernuby on 2008-08-03
Got an Nvidia card and it all works like a charm! Thanks for all your advice.

---

