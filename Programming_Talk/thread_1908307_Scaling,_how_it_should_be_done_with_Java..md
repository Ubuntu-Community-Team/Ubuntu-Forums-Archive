---
title: "Scaling, how it should be done with Java."
date: 2012-01-13
forum: Programming Talk
---

### Post by jaho22 on 2012-01-13
If i have an int[], this int[] holds the pixels of an bufferedimage, then what kind of math and calculations i need to learn to make my int[] bytes scalable.

I want to grap pixels from bimage to int[] and then scale this bimage on byte level.

this is java question, i dont want to use awt i want to make my own scale routines for my images, this is, because i want to use cpu not gpu time with my project.

Im building boardgames with java and i dont want to use gpu just cpu.

---

### Post by ofnuts on 2012-01-13
> **jaho22 said:**
> If i have an int[], this int[] holds the pixels of an bufferedimage, then what kind of math and calculations i need to learn to make my int[] bytes scalable.

I want to grap pixels from bimage to int[] and then scale this bimage on byte level.

this is java question, i dont want to use awt i want to make my own scale routines for my images, this is, because i want to use cpu not gpu time with my project.

Im building boardgames with java and i dont want to use gpu just cpu.
There is the AffineTransform class for that: [http://www.javalobby.org/java/forums/t19387.html](http://www.javalobby.org/java/forums/t19387.html)

The problem if you use it on plain numbers is that its gives you plain numbers... and on images you want a bit more than this, you want some intelligent interpolation. This is also provided by Java. I have some old code (dates back to Java 1.2) that does this:
```

   Graphics2D g2;

    g2.setRenderingHint(RenderingHints.KEY_ANTIALIASING,RenderingHints.VALUE_ANTIALIAS_ON);
    g2.setRenderingHint(RenderingHints.KEY_RENDERING,RenderingHints.VALUE_RENDER_QUALITY);
    g2.setRenderingHint(RenderingHints.KEY_DITHERING,RenderingHints.VALUE_DITHER_ENABLE);
  g2.setRenderingHint(RenderingHints.KEY_INTERPOLATION,RenderingHints.VALUE_INTERPOLATION_BICUBIC);

    AffineTransform at;
    if (zoomRatio==100) at=new AffineTransform(); //Identity transform
    else at=AffineTransform.getScaleInstance(zoomRatio/100.,zoomRatio/100.);
    
    AffineTransformOp ato=new AffineTransformOp(at,AffineTransformOp.TYPE_NEAREST_NEIGHBOR);
    
    g2.drawImage(finalImage,ato,x,y);

```

But this produces an image for the screen. Getting the result as another image is left as an exercise for the reader...

---

