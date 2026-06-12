---
title: "paint brush in opengl"
date: 2010-03-30
forum: Programming Talk
---

### Post by oedipuss on 2010-03-30
Hello

I'd like to simulate something close to how gimp handles a standard brush in opengl. The general idea is to have a brush texture, with only one channel indicating the shape of the brush, and the opacity of each pixel, and paint with it in another texture using quads. Now, the paint to texture part and the calculation of the general shape of the stroke are ok, and simple enough, plus I don't have to keep all the generated quads. After they're painted to the target texture, they get discarded. 

The problem is I can't in no way figure out how to simulate the way gimp handles self intersecting brush-strokes in no way whatsoever.. OpenGL blend modes make me stupid :(

The gist of it is the brush should alter the destination opacity only over less opacity than itself replacing the destination opacity, and alter the destination color, according to its opacity, everywhere, blending normally. 
Like that when in one stroke a brush with 0.4 opacity intersects itself, the intersection remains at 0.5, and the other way around, the final opacity would again be 0.5 .
And when a brush with varying color A to B (as in pressure controlled) intersects itself when colored A on top of color B the colors should blend normally, altering alpha only if the stroke on top is more opaque. 

Two different strokes would blend normally.

The problems are that I don't know what blending to use for this, everything I've tried either doesn't work correctly, or leaves borders around the brush. The closest I've come is with GL_MAX as a blending equation, which is pretty much how I want the alpha channel to behave.
I've no idea how to use a shader for this particular purpose, which would allow for a more controlled blending. The only possible blending with a shader I could come up with is to render both source and destination in two textures, and then render a multitextured quad with the shader activated. That can't work with a brush, however, as it has to intersect with itself as it's painted. Unless I use the texture on which the brush is rendered, as a second texture when I'm drawing the brush itself to that texture, like rendering it onto itself, but that doesn't seem right at all...

Any ideas, or suggestions? Or the right way to do this ?

Semi-noob by the way, only doing this for fun. Please don't make fun of my general ignorance :P

---

### Post by Herve van Baren on 2010-04-19
Hi,
I'm answering your post only now because I'm having the same problem since yesterday. 
 
As stated in the openGL red book, I'm using GL_SRC_ALPHA and GL_ONE_MINUS_SRC_ALPHA for the blending function. The result is an edge around my brush, at each stroke. This is explained by a simple example :
- source color : red, alpha = 0.5 (typical of the brush edge)
- dest. color : red, alpha = 1.0 (already opaque red at that pixel)
the resulting color is of course red, but the blending equation gives :
alpha = 0.5*0.5 + (1-0.5)*1 = 0.75
Which means that the brush "paints" its transparency to the opaque layer. What's not so cool is the source alpha multiplying itself, I think.
 
I think a shader won't help in this case, because all a fragment shader does is send a color (RGBA) to some kind of buffer, and it doesn't have access to what's already painted there. To blend, there's no way around the blending function. You could imagine complex feedback but that's certainly not the best solution. I'm thinking about a 2-pass rendering instead : the first pass uses the classical setting described above, but limits painting to the 3 color channels with glColormask- the alpha is unchanged. The second pass writes only to the alpha, this time with an additive function, and limits writing to the alpha channel. Haven't tested this yet.

---

### Post by Herve van Baren on 2010-04-19
OK, I finally found it : google for **[FONT=Courier New]glBlendFuncSeparate.[/FONT]**

---

