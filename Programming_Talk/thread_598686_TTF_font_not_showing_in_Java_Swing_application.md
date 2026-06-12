---
title: "TTF font not showing in Java Swing application"
date: 2007-10-31
forum: Programming Talk
---

### Post by sambitbasu on 2007-10-31
I hope I am posting in the right forum.

I am writing a Java Swing application which loads a non-english TTF font in the JEditorPane. I installed the font as System font under /usr/share/fonts/truetye/. I can see the font in nautilus with ctrl l -> "fonts://". I can view the font in OpenOffice. I can see documents using the same font on Firefox. But my swing application do not show the font.

Debugger returns a non-null Font object when "new Font(FONTNAME ...) is called.

This, I think, is Ubuntu issue since the same bytecode (compiled on Ubuntu) shows the fonts properly on CentOS 4.5.

I am running Java 5 (1.5.0_13) from Sun on Ubuntu 7.04.

Thanks.
Sambit


Update: Forgot to mention, when I tried to set the font in JEditorPane via Netbeans 6's form designer, the font didn't show up in Netbean's font dialog either

---

### Post by sambitbasu on 2007-11-01
I downloaded Java 6 (1.6.0_03) and tried the same binary. It worked like a charm. Previously, I Java 1.4 (1.4.2_16) but that also didn't work.

I tried to print out the font names that JVM sees by the following code. under Java 1.4 and 5 it did not print the font I was looking for, under 6 it did. 

```

import javax.swing.*;
import java.awt.*;

public class ListFonts extends JFrame
{
    public static void main(String[] args)
    {
        for (String fontName : GraphicsEnvironment.getLocalGraphicsEnvironment().getAvailableFontFamilyNames())
        {
            System.out.println(fontName);
        }
    }
}

```


- Sambit

---

