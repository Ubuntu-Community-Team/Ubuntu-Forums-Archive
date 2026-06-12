---
title: "[Python+PyGame] Change window size"
date: 2010-06-23
forum: Programming Talk
---

### Post by Asday on 2010-06-23
Ok, so, I'm trying to fanny about with PyGame to use as an interface, for two reasons, which I won't go into, 'cause I just realised that's not what this thread is about.

This thread is about changing the window's size, after it's been created, and stuff's happened on it.  I tried this:

```
>>> while i<100:
	for event in pygame.event.get():
		if event.type == pygame.KEYDOWN:
			pygame.display.quit()
			pygame.display.init()
			screen=pygame.display.set_mode((900,900))
			pygame.display.flip()
		elif event.type == pygame.KEYUP:
			pygame.display.quit()
			pygame.display.init()
			screen=pygame.display.set_mode((468,60))
			pygame.display.flip()
		elif event.type == pygame.QUIT:
			sys.exit()
	pygame.time.delay(100)
	i+=1
```

Which works.  Kinda.  I figured it was hacky, and it was confirmed when when the window was activated, it flashed RAPIDLY between the two resolutions for a while, then worked almost as intended.  (Holding in a key seemed to toggle between the two resolutions after the key repeat delay.)

Thanks for your time.

---

