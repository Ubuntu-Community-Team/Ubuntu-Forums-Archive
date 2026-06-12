---
title: "Convert PNG to GIF in Java"
date: 2009-02-04
forum: Programming Talk
---

### Post by cl333r on 2009-02-04
Hi folks,
how do I convert (say the attached TFT.png image) to a GIF without losing the transparency.
Using Gimp there's no problem doing it, I just go to File->Save as a gif image and I'm done, the result is attached as TFT.gif.

However Java replaces the transparent pixels with black ones when saving to GIF, see image TFT.java.gif

Does anyone know how to solve this issue?

Heres' the code I'm using:
```

...
// File f is a PNG file
FileInputStream fin = new FileInputStream(f);
BufferedImage image = ImageIO.read(fin);
//now the extension becomes .gif
String sPath = f.getPath() + ".gif";
//saving as GIF..
ImageIO.write(image, "GIF", new File(sPath));

```

---

### Post by SushiPad on 2009-06-10
I have exactly the same problem.

Did you find a solution?

---

### Post by Reiger on 2009-06-10
There are multiple kinds of color models for BufferedImage; in particular: those that work with ARGB colors and those that use RGB colors. [Read the API docs]("http://java.sun.com/j2se/1.4.2/docs/api/java/awt/image/BufferedImage.html#BufferedImage(int, int, int)"). ;)

---

### Post by froggyswamp on 2009-06-10
> **Reiger said:**
> There are multiple kinds of color models for BufferedImage; in particular: those that work with ARGB colors and those that use RGB colors. [Read the API docs]("http://java.sun.com/j2se/1.4.2/docs/api/java/awt/image/BufferedImage.html#BufferedImage%28int,%20int,%20int%29"). ;)
There's even more than that, but can anyone actually give a working example?

---

### Post by SushiPad on 2009-06-10
Jepp...i tried it with ARGB right from the beginning...
...but it didn't work.

It seems, that the color i defined for the Text (via GlyphVector) later on in the code is also becoming the background color. I tried several things, but none worked.

...its kinda frustrating

---

### Post by pbrockway2 on 2009-06-10
[http://www.eichberger.de/2007/07/transparent-gifs-in-java.html]("http://www.eichberger.de/2007/07/transparent-gifs-in-java.html") has code and comment on Sun's "support" for gif and IndexColourModel.

---

### Post by froggyswamp on 2009-06-11
Folks, according to my test this bug has been fixed in Java 7, I ran this code:
```

import java.awt.image.BufferedImage;
import java.io.File;
import java.io.FileInputStream;
import javax.imageio.ImageIO;

public class Main {

    public static void main(String[] args) {
        try {
            File f = new File("/home/fox/Desktop/TFT.png");
            FileInputStream fin = new FileInputStream(f);
            BufferedImage image = ImageIO.read(fin);
//now the extension becomes .gif
            String sPath = f.getPath() + ".gif";
//saving as GIF..
            ImageIO.write(image, "GIF", new File(sPath));
            System.out.println("Done saving.");
        } catch (Exception exc) {
            exc.printStackTrace();
        }
    }
}

```And Java 7 (latest build), unlike Java 6, actually yields a transparent gif file as expected, without extra efforts! See attached images for comparison between Java 7 and Java 6 output.

Get latest Java/JDK 7 builds:
[http://download.java.net/jdk7/binaries/](http://download.java.net/jdk7/binaries/)

PS: the "fullscreen" image preview feature on this forum seems to not be able to handle transparent gifs, so save the files and open them to see the difference.

---

### Post by hessiess on 2009-06-11
Why are you using giff anyway? it only supports 1 bit transparency so looks ugly and aliased. If you want a palliated format, use a pelleted png, which dousent suffer from the uglyness caused by one bit transparency.

---

### Post by froggyswamp on 2009-06-11
> **hessiess said:**
> Why are you using giff anyway? it only supports 1 bit transparency so looks ugly and aliased. If you want a palliated format, use a pelleted png, which dousent suffer from the uglyness caused by one bit transparency.

You are absolutely right.
But people need it for example because of Internet Explorer 6, which doesn't support transparent PNGs, thus for such users you can (have to) convert them on the fly (or cache them) as transparent GIFs.
When such bad software like IE6 goes into oblivion we will need this feature (much) less, there are already a few % of web devs who dropped support for IE6, which is good.

PS: also, those JavaScript fixes for IE's transparency issues in my experience don't always work as expected so I have to "fix" it on the server side.

---

### Post by hessiess on 2009-06-11
> **froggyswamp said:**
> You are absolutely right.
But people need it for example because of Internet Explorer 6, which doesn't support transparent PNGs, thus for such users you can (have to) convert them on the fly (or cache them) as transparent GIFs.
When such bad software like IE6 goes into oblivion we will need this feature (much) less, there are already a few % of web devs who dropped support for IE6, which is good.

PS: also, those JavaScript fixes for IE's transparency issues in my experience don't always work as expected so I have to "fix" it on the server side.

Sure, but IE6 is finally going the way of the Dodo, for example [http://www.w3schools.com/browsers/browsers_stats.asp](http://www.w3schools.com/browsers/browsers_stats.asp). And as its such a pain in the *** to develop for, why bother?

---

### Post by froggyswamp on 2009-06-11
> **hessiess said:**
> ... why bother?
The majority considers something not worth supporting as it gets under like 5% or 3% or even lower %.
The IE6 avg is still about 10-30% depending on country (China has like 95% IE usage, unbelievable, they live like we lived in 2001-2005, also their windows usage is like 99%).
Anyway, the industry clearly shows that IE6 still has a fair amount of market share that must be addressed, and yes, in like a year or 2 it will be a (completely) different situation.

---

### Post by SushiPad on 2009-07-03
Sorry for the late response...

In my current project i use (better: i try to) use three different image types: PNG, GIF and JPEG.

...and you are absolutely right, i just want the GIF-support for the IE-users. it's one of the requirements for the projects. But now i think i have to wait till we switched our java version to java7 and try it again.

i keep you posted if and how i was able to get it to work ;-)

greez
SushiPad

---

