---
title: "Haskell/SOE graphics library help"
date: 2009-01-06
forum: Programming Talk
---

### Post by stone915 on 2009-01-06
So, I'm running Ubuntu 8.10 on a Macbook 4,1, and I'm having some difficulties getting the SOE graphics library to work correctly with the GHC. I'm trying to run this simple graphics test, and I'm getting this really weird bug. It loads fine, but when I run it, the graphics window pops up and is just full of this random, chaotic assortment of lines and stripes. Here's the catch: Every time I resize it, the window looks exactly like it's supposed to. When I click on it again, it turns back to gibberish. Here's the second catch: I can't take a screenshot of it. I tried to take one using ImageMagick, and the resulting .png looks nothing like what's actually displayed on my screen. If anyone can help me with this I would appreciate it immensely.

(Here's what I'm trying to display. As you can see, it's really simple.)
```
-- After Hudak 3.2 p. 42

module Main where
import SOE

main = runGraphics (
       do w <- openWindow "Graphics Test" (300, 200)
          drawInWindow w (text (50, 100) "Hello, COSC 8 World")
          spaceClose w
       )

spaceClose w = do k <- getKey w
		  if k == ' ' then 
		     closeWindow w
		     else
		     spaceClose w


```

---

### Post by stone915 on 2009-01-06
Alright, so I managed to get some screenshots using scrot. screenshot.png is what the program looks like as soon as it's run. screenshot2.png is what the program looks like after being resized. screenshot3.png is what the program looks like immediately after screenshot2.png was taken. screenshot4.png is interesting. The window has been resized, but if I make the window big enough, I always get the weird "noise" going on in the bottom right corner. If anyone has any idea on what's causing this, whether it's an issue with the SOE library or an issue with Ubuntu, I would be incredibly grateful.

---

### Post by conehead77 on 2009-01-07
Works fine for me. But i had to import Graphics.SOE.Gtk instead of just SOE.
Maybe that will work for you too?

---

### Post by stone915 on 2009-01-07
Hmm, my prof told us that we would only need to use the Gtk package if we were on a Mac, and the regular SOE if we were using Linux. I'll try that though and let you know how it goes. If it doesn't work I might just end up switching to Fedora, because that's what my CS department uses so I can get more support for that.

---

