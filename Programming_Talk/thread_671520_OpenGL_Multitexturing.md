---
title: "OpenGL Multitexturing"
date: 2008-01-18
forum: Programming Talk
---

### Post by Lster on 2008-01-18
Hi all

I've been working a bit more now my exams are done on my game engine (it's still coming slowly). And I've decided to enable multitexturing to do some nice effects. :)

That all went really well and it's working great but I have a few questions that I couldn't find answers for on Google. I have learned how to change coordinates for individual different texture units(?) and enable disable them, but is it possible to change the color associated with a texture unit at a certain vertex? I'm looking for something like glColor4f I think...

Thank you
Lster

---

### Post by Wybiral on 2008-01-18
I'm not 100% certain, but I've never heard of any OpenGL functions that alter the texture space colors. At first I wasn't sure why you would need that, but after thinking about transparent textures, I can see why it might be handy to color each layer separately. Unfortunately, I'm not sure that it's possible. If you can afford a work-around, doing a multipass render would work, as would rebuilding the textures with the colors, but neither of those would be efficient for real time rendering. If you figure it out, definitely post back, I would be interested to see how its possible.

PS: I'm still interested in giving your engine a run!

---

### Post by stroyan on 2008-01-18
Perhaps you want```
glFloat color_array[4] = { 1.0, 1.0, 1.0, 1.0 };
glTexEnvfv(GL_TEXTURE_ENV, GL_TEXTURE_ENV_COLOR, color_array);
glTexEnvi(GL_TEXTURE_ENV, GL_SOURCE0_RGB_EXT, GL_PREVIOUS_EXT);
glTexEnvi(GL_TEXTURE_ENV, GL_OPERAND0_RGB_EXT, GL_SRC_COLOR);

```
You can set up different texture combiner functions and parameters for each texture unit.
I see that used in combination with glActiveTexture in the source for the celestia package.  Look there for a full example.

---

### Post by Lster on 2008-01-19
> **Wybiral]I'm not 100% certain, but I've never heard of any OpenGL functions that alter the texture space colors. At first I wasn't sure why you would need that, but after thinking about transparent textures, I can see why it might be handy to color each layer separately. Unfortunately, I'm not sure that it's possible. If you can afford a work-around, doing a multipass render would work, as would rebuilding the textures with the colors, but neither of those would be efficient for real time rendering. If you figure it out, definitely post back, I would be interested to see how its possible.[/QUOTE]

That is what I was wondering. I can do this with multiple renderings blending stuff together but I hoped multi-texturing would be faster - and easier once I got into it. I can manage I think.  said:**
> PS: I'm still interested in giving your engine a run!

I'd love you to soon, maybe you could review my code then? :) I'm sure you could find a tonne of improvements...

[QUOTE=stroyan]Perhaps you want
Code:

glFloat color_array[4] = { 1.0, 1.0, 1.0, 1.0 };
glTexEnvfv(GL_TEXTURE_ENV, GL_TEXTURE_ENV_COLOR, color_array);
glTexEnvi(GL_TEXTURE_ENV, GL_SOURCE0_RGB_EXT, GL_PREVIOUS_EXT);
glTexEnvi(GL_TEXTURE_ENV, GL_OPERAND0_RGB_EXT, GL_SRC_COLOR);

You can set up different texture combiner functions and parameters for each texture unit.
I see that used in combination with glActiveTexture in the source for the celestia package. Look there for a full example.[/QUOTE]

I played about with that but I couldn't get anything to happen. I think for now I can stick using my custom rendering. Thanks all the same.

---

