---
title: "pygame rotate line"
date: 2009-09-03
forum: Programming Talk
---

### Post by nipunreddevil on 2009-09-03
I wish to do a fairly simple task in pygame ,just to rotate a line,have been unable to do so.Website talks about rotating images,same methods didnt work for me for line.Here is my code```
import pygame,time

width = 640
height = 400

screen = pygame.display.set_mode((width, height))
a=pygame.draw.rect(screen,(100,100,100), (100,100,100,100),1)
pygame.transform.rotate(screen,45)
pygame.display.flip()
time.sleep(2)


```

---

### Post by nipunreddevil on 2009-09-06
Does anyone have an idea for rotating line in pygame or shall i use elementary techniques like vector multiplication and transformation.I am not clear regarding that too.Please could anyone throw some light .

---

