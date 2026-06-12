---
title: "Benefits of upgrading graphics card on ubuntu?"
date: 2012-06-15
forum: New to Ubuntu
---

### Post by meathdeath on 2012-06-15
What are some benefits of upgrading my graphics card as far as ubuntu is concerned? Are there really nice fancy visual effects i could apply with a nice graphics card? or are there native games that you can recommend that would look good with a new GPU?

---

### Post by papibe on 2012-06-15
Hi meathdeath.

In general, better desktop effects, like the cube and other effects (check [here]("https://help.ubuntu.com/community/CompositeManager")). 

Also, you'll have better performance on games that uses OpenGL.

However, IMHO, the best benefit is being able to play full HD video.

Just some thoughts.
Regards.

---

### Post by SDX0 on 2012-06-16
Amnesia: The Dark Decent comes to mind as a moderately GPU-heavy game.  Bastion only requires a low-end graphics card, but it benefits from a mid-end card.

Other than those two, games that run natively in Linux tend not to require much graphics processing.  I suppose you could run other games in Wine, but usually games run faster in Windows than they do in Wine.

---

### Post by Paqman on 2012-06-16
You'll also get better performance if you're doing any GPGPU, such as BOINC apps like Seti@Home or Folding@Home.

One point about video playback: to get any benefit from your GPU make sure you're using a VDPAU-enabled player such as XBMC or Smplayer.

---

### Post by 3rdalbum on 2012-06-16
> **Paqman said:**
> You'll also get better performance if you're doing any GPGPU, such as BOINC apps like Seti@Home or Folding@Home.

One point about video playback: to get any benefit from your GPU make sure you're using a VDPAU-enabled player such as XBMC or Smplayer.

And make sure the GPU is made by Nvidia, of course :-)

As modern Linux desktops actually use 3D composited desktop environments, you'll find that the GPU will always be rendering the desktop. So you'll notice that the Dash will open quicker and be more responsive, and windows will appear on the screen in less time than it took with a lower graphics card (or no graphics card).

---

### Post by meathdeath on 2012-06-16
Thank you guys for replying and giving me ideas:) i might upgrade my graphics card to a gt 200 series or so just to have a mid-low card to do the desktop effects and possibly some low end wine gaming.

---

