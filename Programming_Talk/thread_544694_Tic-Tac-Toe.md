---
title: "Tic-Tac-Toe"
date: 2007-09-06
forum: Programming Talk
---

### Post by yman on 2007-09-06
Hello all.

I'm making a tic tac toe game in Java (later in C++ with KDE) and being a beginner in programing, I thought I could use some help. I'm also not used to writing documentation, so it's probably lacking. I already wrote most or nearly all the code, but I find the GUI part confusing, so I didn't do that, and had to use some placeholder code in some places. The documentation that exists isn't 100% what I implemented, but it's close enough.

This is meant as a practice project. next on my list are Connect 4, Checkers, Chess , Shogi (Japanese Chess, I really like it, and the only computer version I found, XShogi, crashes immediately upon startup). These are all intended as practice projects, after which I will try implementing my own ideas for original games. One of these is "Melting Ice", in which you play as a penguin on a melting Iceberg. You can move forward, backward, left and right (overhead view). Each tile of ice that is near water would crack each time you make a move, And cracked ice would melt. You lose if you are surrounded on all 4 sides by water, win if you reach dry land.

Anyway, back to tic-tac-toe:

Obviously, It's intended to be open and free by all means and meanings. If you got to attribute a license to it then consider it GNU GPL v.2, since thats the only FLOSS license I ever read.

Any help will be appreciated, although I expect to succeed on this on my own.

A tarball of the entire eclipse project can be found [Here.]("http://www.orangejew.com/programing/tic-tac-toe.tar.gz")

---

### Post by pmasiar on 2007-09-06
Is Java strict requirement? Python and Pygames might be simpler to learn (especially for self-learning beginner) and more fun. Of course I know nothing about your skill level and interest, it is just average guess :-/

---

### Post by Tomosaur on 2007-09-06
> **pmasiar said:**
> Is Java strict requirement? Python and Pygames might be simpler to learn (especially for self-learning beginner) and more fun. Of course I know nothing about your skill level and interest, it is just average guess :-/
^^ It's pretty much finished in Java :P

Looks pretty decent, although since it isn't playable yet I don't know if it works. From the brief glance I've taken it looks like you shouldn't have any trouble finishing it off.

If you're not yet comfortable with building a GUI purely through hand-coding, then you should check out Netbeans - it has a visual development tool for GUI building so you can pretty much just drag and drop. However, depending on how you want to implement your game board, you might find it's easier to just hand-code, because I expect you will need to extend a few classes here and there.

Good luck!

---

### Post by yman on 2007-09-07
> **pmasiar said:**
> Is Java strict requirement? Python and Pygames might be simpler to learn (especially for self-learning beginner) and more fun. Of course I know nothing about your skill level and interest, it is just average guess :-/

I always get lazy and give up fast when trying to learn a new language. as for python specifically, I didn't like the tutorial for a reason I can't remember.

I guess if what I read about it is true then it would be easier, but I still want to get a good head start in Java for when I take programing courses in college. I also know it already so I can't get stuck on the learning stage. I learned it on my own, then had an AP course in high school that covered just about one for one all that I learned from "Java all in one desk reference for dummies", and I quite that book somewhere in the middle, out of laziness.

what do you mean by "requirement"? I just happened to use it. if you want to code along in Python, be my guest, but the goal is that this works, and more important, that ***_I_*** fully understand it so I can go on to more advanced things.

BTW: while writing this, I'm installing Ubuntu 7.04 in the background. writing this post took more time than the installation :-)

I'll finally have an IDE that doesn't take 5 minutes to load cause the processor is 486 MHz!

> **Tomosaur said:**
> ^^ It's pretty much finished in Java :P

Looks pretty decent, although since it isn't playable yet I don't know if it works. From the brief glance I've taken it looks like you shouldn't have any trouble finishing it off.

If you're not yet comfortable with building a GUI purely through hand-coding, then you should check out Netbeans - it has a visual development tool for GUI building so you can pretty much just drag and drop. However, depending on how you want to implement your game board, you might find it's easier to just hand-code, because I expect you will need to extend a few classes here and there.

Good luck!

I'm even less comfortable doing it visually. The problem is I'm too used to HTML (in notepad/gedit, no graphical tools for me!), so even the easy GUI building in Java intimidates me. and I know it's easy and I played around with it, but I still feel scared. I guess I'll just have to hope right into the freezing hot water (or however you say it).

the problem is, I haven't done much about the graphical side in the design stage except right down that I need to do *something*. well, maybe I'll get to it on Monday.

anyhow, it's nice to get some positive comments. it's not like I really invested a lot of effort in this, but non the less, it feels good. hopefully I finish on schedule,

---

### Post by fct on 2007-09-07
I programmed Connect 4 in Java for an AI exercise.

If you're having problems with the GUI, I guess it's the same part that confused me at first: the canvas to draw on and the mouse input. Specially the canvas, since until Java 7 comes out, you shouldn't mix the AWT canvas with Swing containers.

For the canvas, you create a class that inherits from a JPanel and overrides the PaintComponent function. Then you add functions to handle mouse input. Like this:

```

public class GameCanvas extends javax.swing.JPanel implements MouseListener{
	public GameCanvas (){
		super();
		addMouseListener(this);
		...
	}


	// Here you can use ev.getX() and ev.getY() to get the coordinates of
	// the mouse inside the canvas.
	public void mouseEntered(MouseEvent ev){
	...
	}
	public void mouseExited(MouseEvent ev){
	...
	}
	public void mousePressed(MouseEvent ev){
	...
	}
	public void mouseReleased(MouseEvent ev){
	...
	}
	public void mouseClicked(MouseEvent ev){
	...
	}

	// And here the methods of g (setColor(), draw*, fill*, etc.) are what
	// you'll use to draw in the canvas
	@Override public void paintComponent(Graphics g) {
	        super.paintComponent(g);
		...
	}
}

```

For your tic-tac-toe game, you'll probably just need the functions "g.setColor(), "g.drawLine()" and "g.fillCircle()".

Remember to call paintComponent() whenever there is a change in the state of the game. That function only gets called automatically during some window operations like resizing, if I remember correctly.

---

### Post by Wybiral on 2007-09-07
> **yman said:**
> I always get lazy and give up fast when trying to learn a new language. as for python specifically, I didn't like the tutorial for a reason I can't remember.

I guess if what I read about it is true then it would be easier, but I still want to get a good head start in Java for when I take programing courses in college. I also know it already so I can't get stuck on the learning stage.

Learning new languages will get easier and easier as you go (most of them have a lot in common). If you really enjoy Java after learning a few other languages, then keep using it. But learning new languages will open you up to more opportunities... Programming languages are tools, it's best you have as many as you can under your belt.

When a job comes along that's best suited for that tool, you'll have it and you wont have to waste the time trying to hack it together with the wrong language.

---

