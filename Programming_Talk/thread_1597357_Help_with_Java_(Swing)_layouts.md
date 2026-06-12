---
title: "Help with Java (Swing) layouts"
date: 2010-10-15
forum: Programming Talk
---

### Post by blazemore on 2010-10-15
Hi everyone, for an assignment at uni I have to make a simple game. However, I have a question about the interface.

I need one window that's split vertically into two "panes". The left one needs to be a grid layout, and the right one a normal (flow?) layout.

I'll attach a PDF with the mockup I've made. ([http://concentrationgame.googlecode.com/svn/trunk/myBalsamiqMockup.pdf](http://concentrationgame.googlecode.com/svn/trunk/myBalsamiqMockup.pdf))

Annoyingly, I'd have no problems implementing this with Glade/GTK but have no idea about Swing's syntax and idiosyncrasies.

---

### Post by PaulM1985 on 2010-10-15
I am assuming you are using a JFrame.  You are going to want to add panels for the left and right (have a look at the default layout manager for JFrame.  This should help you sort out this step).  In each of the panels add the appropriate layouts.

I think you are right.  I am fairly sure FlowLayout is normal for a JPanel.

API is really handy for things like this:
[http://download.oracle.com/javase/1.5.0/docs/api/](http://download.oracle.com/javase/1.5.0/docs/api/)

Having a look at your image, I think you probably want to use a different layout to flow for the right hand panel.

Paul

---

### Post by KdotJ on 2010-10-15
Another good source of help is the LayoutManager tutorials from the oracle website:

[LINK HERE]("http://download.oracle.com/javase/tutorial/uiswing/layout/visual.html")

Here there is a visual guide to each one, and they all have their own tutorial(ish) with examples and basic explanation, and even some source files wish you can download and play around with.

In my experience, it's a case of playing around with them and understanding what manager is good for what.

---

### Post by blazemore on 2010-10-18
Ugh I still can't get it to work.

I'm building from an example my lecturer gave me which uses getContentPane() but I can't see the actual panel referenced anywhere?

How can I have two panels side-by-side, each having a different layout, and add widgets to each one independently?

---

### Post by muze4life on 2010-10-18
The link from the first post is broken (404 - not found).
But from your last post it looks like you're trying to do something like this:

```

import java.awt.*;
import javax.swing.*;

public class Main extends JFrame {

    public static void main(String[] args) {
        new Main();
    }

    public Main() {
        setSize(500, 500);
        setDefaultCloseOperation(EXIT_ON_CLOSE);
        JPanel cp = new JPanel();
        cp.setLayout(new BoxLayout(cp, BoxLayout.LINE_AXIS));
        cp.add(createPane1());
        cp.add(createPane2());
        setContentPane(cp);
        setVisible(true);
    }

    private JPanel createPane1() {
        JPanel p = new JPanel(new FlowLayout(FlowLayout.LEFT));
        p.add(new JTextField("Left Pane with a"));
        p.add(new JTextField("flow"));
        p.add(new JTextField("layout"));
        return p;
    }

    private JPanel createPane2() {
        JPanel p = new JPanel(new BorderLayout());
        p.add(BorderLayout.NORTH, new JTextField("Center Pane with a"));
        p.add(BorderLayout.CENTER, new JTextField("Border"));
        p.add(BorderLayout.SOUTH, new JTextField("Layout"));
        return p;
    }
}

```

---

### Post by leg on 2010-10-18
There is a [split pane]("http://download.oracle.com/javase/tutorial/uiswing/components/splitpane.html") component that you could use.

---

### Post by blazemore on 2010-10-18
OK thanks, I'm using a splitpane with divider size 0.

I have a gridlayout in the right-hand column, but **I need the vertical alignment to be top**: by default it is centred.

Is this possible?

I'll attach a screenshot

You can see, the widgets in the panel on the right are spacing out; I need them packed to the top , preferably with a definable gap of, say, 10px.
It's a gridLayout with 1 column.

---

