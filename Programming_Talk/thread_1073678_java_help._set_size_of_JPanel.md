---
title: "java help. set size of JPanel"
date: 2009-02-18
forum: Programming Talk
---

### Post by Choad on 2009-02-18
this is a direct copy-paste from another forum... got no replies :(

ok something funky was going on with the size of my game window, and i realised that it was because calling the main JFrame's setSize( w, h ) method takes in to account window borders.

so i googled, and apparently i need to use the pack() method of my JFrame to size it for the widgets contained within.

so i commented out the setSize method and replaced it with a pack but that made the window tiny, because the only thing the JFrame contains is a JPanel which has no size as it's a container.

so i tried setting the JPanel's size by calling it's setSize method... and nothing happened.

does anyone know how i can go about this?

in a nut shell:
i have a JFrame that contains 1 JPanel, and i need to set the dimensions to a specific size not counting the window borders.

edit: just tried

super.setPreferredSize( new Dimension( Main.SCREEN_WIDTH, Main.SCREEN_HEIGHT ));

which worked... except it decided to ignore my suggestion for a size and make up a size of it's own. urgh. why does nothing do what i expect it to today?

ok here's the relevant code if it helps. love and rep to the person who figures this out before me!

```

public Main() {
        board = new Board();
        add(board);
        pack();
        loadMainMenu();
        setDefaultCloseOperation(EXIT_ON_CLOSE);
        //setSize(SCREEN_WIDTH, SCREEN_HEIGHT);
        setLocationRelativeTo(null);
        setVisible(true);
        setResizable(false);
        setTitle("Platformy Game");     
    }

public Board() {
        super.setPreferredSize( new Dimension( Main.SCREEN_WIDTH, Main.SCREEN_HEIGHT ));
        addKeyListener(new InputHandler());
        setFocusable(true);
        setBackground(Color.WHITE);
        setDoubleBuffered(true);
        clearAll();
        timer = new Timer( 25, this );
        timer.start();
    }

```


this forum doesn't do rep so you'll have to settle for the love :)

---

### Post by kavon89 on 2009-02-18
Try moving the pack() to the very bottom the Main constructor, or actually just removing it. When you want an exact resolution, you shouldn't use pack.

---

### Post by Choad on 2009-02-18
tried but to no avail. this is really bugging me now. i could carry on and ignore the odd window size but i hate letting my computer get the better of me.

would you mind downloading it and seeing if you can get it to work?

it's a netbeans project, and it's attached :)

---

### Post by kavon89 on 2009-02-18
Seems to work for me. All I did was modify the screen sizes and it seemed fine.

---

### Post by Zugzwang on 2009-02-19
Did you try setting the *minimum size* and the *maximum size* and then calling pack()? "pack" might resize your elements.

---

### Post by Choad on 2009-02-19
> **kavon89 said:**
> Seems to work for me. All I did was modify the screen sizes and it seemed fine.
if that's all you did then i'm stumped.

i'm using ubuntu 8.10, openjdk 1.6 (according to netbeans java platform manager), compiz, and err... netbeans 6.1

i've tried with metacity and got the same results

is your setup different from mine?

---

### Post by kavon89 on 2009-02-19
Only difference is I'm using Sun's JDK 1.6 and a newer NetBeans (Which should have nothing to do with it).


One thing I noticed is if I were to change the resolution values and just hit Run in NetBeans, it wouldn't change it properly. Hit Clean & Build, then Run and it should be fine.

Edit: oh yea cute little game you've got going (I'm assuming the block with a smiley face is a testing sprite, but hes cool ;D ), the jumping motion is pretty smooth.

---

### Post by Choad on 2009-02-19
> **kavon89 said:**
> Only difference is I'm using Sun's JDK 1.6 and a newer NetBeans (Which should have nothing to do with it).


One thing I noticed is if I were to change the resolution values and just hit Run in NetBeans, it wouldn't change it properly. Hit Clean & Build, then Run and it should be fine.

Edit: oh yea cute little game you've got going (I'm assuming the block with a smiley face is a testing sprite, but hes cool ;D ), the jumping motion is pretty smooth.
cool i'll see if that has anything to do with it.

and thx :D i know a thing or two more about programming 2d games than i do about java. my introduction to programming was a wicked little thing called game maker - i spent years making games like this

---

### Post by Choad on 2009-02-20
> **kavon89 said:**
> Only difference is I'm using Sun's JDK 1.6 and a newer NetBeans (Which should have nothing to do with it).


One thing I noticed is if I were to change the resolution values and just hit Run in NetBeans, it wouldn't change it properly. Hit Clean & Build, then Run and it should be fine.

Edit: oh yea cute little game you've got going (I'm assuming the block with a smiley face is a testing sprite, but hes cool ;D ), the jumping motion is pretty smooth.

just tried it on windows and i still see that bug, just much smaller. down the bottom and right there is a white border

---

