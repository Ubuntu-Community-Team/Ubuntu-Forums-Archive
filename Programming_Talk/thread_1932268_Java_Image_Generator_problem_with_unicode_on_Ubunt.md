---
title: "Java Image Generator problem with unicode on Ubuntu Server"
date: 2012-02-27
forum: Programming Talk
---

### Post by phichidev on 2012-02-27
Why my image generator problem with java font in Ubuntu Server?

Ubuntu Desktop:
[IMG]http://ni1.upanh.com/b4.s24.d1/84a063dea3b407345053ee3d24114291_41396531.imageubuntudesktop.png[/IMG]
Ubuntu Server: (problem with **unicode characters**)
[IMG]http://ni6.upanh.com/b3.s24.d1/da066f245798e35233dbde0c510c2318_41396546.imageubuntuserver.png[/IMG]

OS: Ubuntu Server 11.10
Java: java version "1.6.0_23"
OpenJDK Runtime Environment (IcedTea6 1.11pre) (6b23~pre11-0ubuntu1.11.10.2)
OpenJDK 64-Bit Server VM (build 20.0-b11, mixed mode)

**My Code:**
```
import java.awt.*;
import java.awt.image.BufferedImage;
import java.io.File;
import javax.imageio.ImageIO;

public class Main {

    public static void main(String[] args) throws Exception {
        BufferedImage bufferedImage = new BufferedImage(200, 20, BufferedImage.TYPE_INT_ARGB);
        Graphics2D g2d = bufferedImage.createGraphics();
        g2d.setRenderingHint(RenderingHints.KEY_TEXT_ANTIALIASING, RenderingHints.VALUE_TEXT_ANTIALIAS_ON);
        g2d.setRenderingHint(RenderingHints.KEY_ANTIALIASING, RenderingHints.VALUE_ANTIALIAS_ON);
        g2d.setRenderingHint(RenderingHints.KEY_TEXT_ANTIALIASING, RenderingHints.VALUE_TEXT_ANTIALIAS_ON);
        g2d.setBackground(Color.WHITE);
        g2d.fillRect(0, 0, bufferedImage.getWidth(), bufferedImage.getHeight());
        g2d.setColor(Color.BLACK);
        g2d.drawString("&#9734;°&#12290;&#12290;&#9734;°&#12290;&#12290;°&#9734;", 5, 15);
        ImageIO.write(bufferedImage, "PNG", new File("image.png"));
    }
}

```

---

### Post by ofnuts on 2012-02-27
[COLOR=Black]Are the same fonts installed on both?
[/COLOR]
[LIST]
[*][COLOR=Black] The first character is "White star" in group "[/COLOR] [COLOR=Black][Miscellaneous Symbols]("http://www.fileformat.info/info/unicode/block/miscellaneous_symbols/index.htm")".[/COLOR]
[*][COLOR=Black] While the dots are "ideographic full stop'" from group "[CJK Symbols and Punctuation" (ie, ideographic languages).]("http://www.fileformat.info/info/unicode/block/cjk_symbols_and_punctuation/index.htm")[/COLOR]
[/LIST]
 So the dots likely require some ideographic font.

---

### Post by Some Penguin on 2012-02-27
Don't embed multibyte characters like that.  Use the \u#### method as that's actually likely to work even on systems that make silly assumptions about character encoding and so forth.

---

### Post by ofnuts on 2012-02-27
> **Some Penguin said:**
> Don't embed multibyte characters like that.  Use the \u#### method as that's actually likely to work even on systems that make silly assumptions about character encoding and so forth.Java source code(*) can have any encoding (this is an option to the compiler, which uses the default platform encoding). The benefits of using the local characters directly (try to write regular expressions using escaped unicode....) more than offset the added complexity, and most people end up quickly with a properly set up tool chain.

(*) unlike properties, that must be in ISO-8859-1

---

