---
title: "Weird JButton behaviour is weird"
date: 2010-05-24
forum: Programming Talk
---

### Post by nmccrina on 2010-05-24
Hi all,

I'm doing this GUI thing with Swing, and I have encountered a mystifying problem. I'm trying to display a JButton that says "prev", but instead it displays "pr...", like there is no space for the text. It's FlowLayout so theoretically it should be able to grow and accommodate the text anyway, but it wasn't doing that.

But then here's the catch: I tried making it say "next" (same number of characters) and it displayed perfectly! "prev " (with a space at the end), "prew", and "nexte" were also fine. However, "nexv" was displayed as "n...". So I'm thinking this is either some kind of bug involving JButton texts that end in 'v', or something esoteric that's beyond my current understanding. What do you guys think?

I'm using the default openjdk JDK that comes with Lucid, BTW.

---

### Post by dwhitney67 on 2010-05-24
I'm using Sun-Java; the following works fine for me:
```

import java.awt.*;
import javax.swing.*;


class Foo extends JFrame
{
   public Foo()
   {
      super("Foo");

      Dimension size = getToolkit().getScreenSize();
      int       xLoc = size.width  / 4;
      int       yLoc = size.height / 3;

      setLocation(xLoc, yLoc);

      setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

      JPanel panel = new JPanel();
      panel.add(new JButton("prev"));
      panel.add(new JButton("next"));
      panel.add(new JButton("prew"));
      panel.add(new JButton("nexte"));

      getContentPane().setLayout(new FlowLayout());
      getContentPane().add(panel);
   }

   public void display()
   {
      pack();
      setVisible(true);
   }

   public static void main(String[] args)
   {
      Foo f = new Foo();
      f.display();
   }
}

```
What other operations with the buttons and/or layout are you doing in your code?

---

### Post by nmccrina on 2010-05-24
I compiled your code, and the result was:

[IMG]http://i757.photobucket.com/albums/xx219/nmccrina/Random/Screenshot-Foo.png[/IMG]

???

Should I file some kind of bug report on this?

---

### Post by dwhitney67 on 2010-05-25
I guess you should file a bug report, or perhaps wait for other feedback from someone who actually uses the OpenJDK package.  Like I stated earlier, I do not.

---

### Post by eluminBe on 2010-05-25
File a bug report - regardless of the version you are currently trying to use, it's not a normal behaviour.

---

### Post by KdotJ on 2010-05-25
Just to confirm, I too use the openJDK and compiled dwhitney67's code. 

I also got "pr..." displayed on the prev button

---

### Post by twistedCT on 2011-02-20
Hey all.
Total newbie here to both Ubuntu and Java programming.
I know this thread is 9 months old, but I had the same issue with the text label on a JButton showing up as "..." . I searched all over for a solution and this thread is the only one that I found that even addressed the issue.
Anyway, after trying different character sets and using Sun Java instead openJDK with no luck, I ended up asking my Java programmer friend about it. He took one look at the output and knew the answer. He resized the JFrame larger which in turn resized the JButtons and there it was, the proper text for the JButton labels. He said that's a Java thing. If the characters are "to big" for the box, it will replace it with "..." (which really doesn't make sense since I was only trying to have a single character for the label).
I'm sure after 9 months the OP may have already figured out how to fix his issue, but for anyone else that may come across this problem and find this thread, try resizing the JFrame larger. It worked for me.

---

