---
title: "Beginner : Java and drawimage and etc.."
date: 2012-02-02
forum: Programming Talk
---

### Post by jaho22 on 2012-02-02
Im newbie with Java,

I have set on linux and mac computers "-Dsun.java2d.opengl=true" and on windows computers "-Dsun.java2d.d3d=true".

My question is as i am now using java2d, when i use drawimage and fillrect, then are thouse lines where drawimage or fillrect are, are they blocking lines or will all images be flushed later to screen when i use strategy.show();

---

### Post by Zugzwang on 2012-02-02
> **jaho22 said:**
> My question is as i am now using java2d, when i use drawimage and fillrect, then are thouse lines where drawimage or fillrect are, are they blocking lines or will all images be flushed later to screen when i use strategy.show();

Can you reformulate your question? It is extremely hard to understand.

For example, where do the lines come from "where drawimage or fillrect are"? How can drawimage or fillrect be anywhere?

Then, what are blocking lines? Google didn't reveal anything. And what type is "strategy" of?

---

### Post by jaho22 on 2012-02-02
im asking,

about java graphics2d command "drawimage",
is this command blocking when i have set hardware acceleration on, or are images drawn to screen then later with bufferstrategy.show().

---

### Post by muteXe on 2012-02-02
Any use?:
[http://stackoverflow.com/questions/658059/graphics-drawimage-in-java-is-extremely-slow-on-some-computers-yet-much-faster](http://stackoverflow.com/questions/658059/graphics-drawimage-in-java-is-extremely-slow-on-some-computers-yet-much-faster)

---

### Post by jaho22 on 2012-02-03
This is not an performance question, i am asking by the reason of how to build my sleep() calls on my game code.

it is important to me to know if drawimage() is blocking the code until it is fully drawn to screen or will it be later flushed with all other bufferedimages by bufferstrategy.show().

---

### Post by PaulM1985 on 2012-02-03
Have you got any code examples so we can look at what you are doing?

Are you asking if every "drawImage" call actually draws to screen straight away?  If this is the case I think the answer is no in most cases.  Java JPanels have an option of double buffered which is enabled to true by default.  This means that in the paint(Graphics g) method, all of the things that are drawn are drawn to a buffer and once the paint method ends, the whole buffer is drawn to the panel.

Does this make sense?  Does it answer your question?

Paul

EDIT:
As for sleep calls in your game code, you will usually want a loop like this:

```

long totalGameLoopTime = X;

Date lastSleep = new Date();
while (!gameEnded) {
   readUserInput();   // read input from keyboard, mouse, game pad etc
   updateGameState(); // update the positions of your game objects (balls, soldiers, leaves in the wind etc)
   repaint();         // draw everything

                      // Now sleep
   try
   {
      Date now = new Date();
      long timeFromLastSleep = now.getTime() - lastSleep.getTime();

      // Having a total game loop time means that slower PCs and faster PCs 
      // spend the same amount of time in each iteration of the game loop
      Thread.sleep(totalGameLoopTime - timeFromLastSleep); 
      lastSleep = now;
   }
   catch (InterruptedException e) {}
}

```

---

