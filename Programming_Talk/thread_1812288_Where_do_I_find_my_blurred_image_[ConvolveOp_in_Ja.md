---
title: "Where do I find my blurred image? [ConvolveOp in Java]"
date: 2011-07-26
forum: Programming Talk
---

### Post by skytreader on 2011-07-26
Hello. I'm trying out some simple image blurring in Java. I currently have the following code:

```
public class ImageBlurring{
	public static void main(String[] args) throws Exception{
		float[] kernelData = {0.111f, 0.111f, 0.111f,
		                      0.111f, 0.111f, 0.111f,
		                      0.111f, 0.111f, 0.111f};
		ConvolveOp bio = new ConvolveOp(new Kernel(3, 3, kernelData));
		BufferedImage forBlurring = ImageIO.read(new File("testimages/blurtest.JPG"));
		BufferedImage blurred = ImageIO.read(new File("testimages/blurred.JPG"));
		BufferedImage blurOut = bio.filter(forBlurring, blurred);
	}
}
```

Uhmm...I'm really new here so my set-up is like this: blurtest.JPG is the image I want to blur; blurred.JPG is an *exact* copy of blurtest.JPG---I wish it to contain the blurred version of blurtest.JPG but **it is not yet blurred**.

So, I run my little command line program and all seem to go fine. However, I can't find the my blurred image anywhere. blurred.JPG is not blurred and nothing happened to blurtest.JPG as well . So...where do I find it?

P.S. Maybe my image is too textured for me to notice the blur that took place? I'm using an image of a coral. Does the image's texture affect blurring?

---

### Post by PaulM1985 on 2011-07-26
Your code reads in two images, but doesn't write anything out.  If you don't write out, you won't see any changes.

Paul

EDIT:
I usually do:
```

		BufferedImage blurred = bio.filter(forBlurring, null);

```
so it is clear that we have created "blurred" from "forBlurring".  After doing this, you want to write out the "blurred" variable.

---

### Post by skytreader on 2011-07-26
> **PaulM1985 said:**
> 
I usually do:
```

		BufferedImage blurred = bio.filter(forBlurring, null);

```


That's was my first attempt, seeing that filter throws an Exception if src is null but not when dst is null :D. However, when nothing happened, I wrote it as I posted above, following the tutorial I'm working on.

But...uhmmm...how do you write out an image? All I found on the web was [http://download.oracle.com/javase/tutorial/2d/images/saveimage.html](http://download.oracle.com/javase/tutorial/2d/images/saveimage.html) which needs a RenderedImage object (with the note that BufferedImage implements RenderedImage). What RenderedImage do I instantiate? The example uses BufferedImage, instantiated by call to a method getMyImage() which, as far as I can tell, is more of a pseudo-method than an actual API call.

Thanks!

---

### Post by PaulM1985 on 2011-07-26
> **skytreader said:**
> That's was my first attempt, seeing that filter throws an Exception if src is null but not when dst is null :D. However, when nothing happened, I wrote it as I posted above, following the tutorial I'm working on.

But...uhmmm...how do you write out an image? All I found on the web was [http://download.oracle.com/javase/tutorial/2d/images/saveimage.html](http://download.oracle.com/javase/tutorial/2d/images/saveimage.html) which needs a RenderedImage object (with the note that BufferedImage implements RenderedImage). What RenderedImage do I instantiate? The example uses BufferedImage, instantiated by call to a method getMyImage() which, as far as I can tell, is more of a pseudo-method than an actual API call.

Thanks!

```

    ImageIO.write(bi, "png", outputfile);

```

This line from your link is saving a buffered image "bi" to an output file "outputFile".  In your original code, you have both a buffered image and an output file.
```

BufferedImage blurred = bio.filter(forBlurring, null);
ImageIO.write(blurred, "png", (new File("testimages/blurred.JPG"));

```

---

