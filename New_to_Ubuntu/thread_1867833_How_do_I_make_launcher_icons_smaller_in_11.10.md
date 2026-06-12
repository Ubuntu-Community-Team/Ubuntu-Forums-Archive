---
title: "How do I make launcher icons smaller in 11.10?"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by egkeat on 2011-10-23
Anyone?

---

### Post by haqking on 2011-10-23
> **egkeat said:**
> Anyone?

If you are using Unity 3D, then you can run CCSM and use the Unity plugin to shrink them

---

### Post by egkeat on 2011-10-23
> **haqking said:**
> If you are using Unity 3D, then you can run CCSM and use the Unity plugin to shrink them

I'm using gnome 3.

---

### Post by haqking on 2011-10-23
> **egkeat said:**
> I'm using gnome 3.

So is unity ;-)

You mean you are using Gnome Shell ?

If you are not running defaults in 11.10 then your OP needs to be clearer with more information

---

### Post by egkeat on 2011-10-23
> **haqking said:**
> So is unity ;-)

You mean you are using Gnome Shell ?

If you are not running defaults in 1110 then your OP needs to be clearer with more information

Yes, I am using Gnome Shell. Perhaps I've done so much with trying to personalize,  this whole thing has gone haywire. Anyhow. I don't know how to get to the icons on the launcher that aren't showing up when I go to the bottom. I'm also using docky, and perhaps would like to only use that instead if that's possible.

---

### Post by ProntoAnthony on 2011-10-23
If you are running Unity you can by going into CompizConfig Settings Manager and then choosing the experimental tab of the Ubuntu Unity Plug-in. The smallest setting is 32.

If you are running Unity 2D the icons remain at their biggest setting. This is a known bug in 11.10 and will be fixed by developers eventually.

---

### Post by egkeat on 2011-10-23
> **ProntoAnthony said:**
> If you are running Unity you can by going into CompizConfig Settings Manager and then choosing the experimental tab of the Ubuntu Unity Plug-in. The smallest setting is 32.

If you are running Unity 2D the icons remain at their biggest setting. This is a known bug in 11.10 and will be fixed by developers eventually.

Thanks, I just discovered that after ditching Gnome shell altogether, (a bit difficult that was) and going back to Unity.

---

### Post by Robert Neuron on 2012-05-29
How do I find out if I have Unity 2D or 3D? At least I know that Compiz doesn't change my icons. We're in May 2L012 now, so have they fixed the bug?

---

### Post by TheMTtakeover on 2012-05-29
next time you have a question you should create your own post for it. You can check by logging out and then selecting which one you want or click this link [http://askubuntu.com/questions/62001/am-i-using-unity-or-unity-2d](http://askubuntu.com/questions/62001/am-i-using-unity-or-unity-2d)

It will explain the visual differences to you.

---

### Post by haqking on 2012-05-29
> **Robert Neuron said:**
> How do I find out if I have Unity 2D or 3D? At least I know that Compiz doesn't change my icons. We're in May 2L012 now, so have they fixed the bug?

```
echo $DESKTOP_SESSION
``` if it says Ubuntu then it is 3d, if it says Ubuntu-2d then guess what ;-)

---

