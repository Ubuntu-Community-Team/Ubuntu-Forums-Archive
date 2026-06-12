---
title: "help with created input text box"
date: 2012-11-07
forum: Programming Talk
---

### Post by snowlizard31 on 2012-11-07
I tried to make my own text box since I couldn't get pgu to work but the text box only gets printed on the screen and doesn't do anything?
```

import pygame, pygame.font, pygame.event, pygame.draw, string
from pygame.locals import *

def print_text(screen, message, height, width):
    pygame.font.init()
    fontobject = pygame.font.Font(None,18)
    img = pygame.image.load('textbox.png')
    

    screen.blit(img, (height,width))
      pygame.display.flip()
    
    if len(message) != 0:
        screen.blit(fontobject.render(message,1 , (0,255,255)),(height+3, width+7))


def text_box():    
    pygame.font.init()
      current_string = []
    
    for key in pygame.key.get_pressed():
        if key == pygame.key.get_pressed() or key == pygame.key.set_repeat():
            current_string.append()
            if key == K_BACKSPACE:
                current_string = current_string[0:-1]
    return string.join(current_string,"")
# how I called it in other file 
text = test.text_box()
test.print_text(screen,text,300,380)


```

---

### Post by snowlizard31 on 2012-11-08
```

import pygame, sys, string
from pygame.locals import *

def print_text(screen, (height, width)):
    pygame.font.init()
    fontobject = pygame.font.Font(None,18)
    img = pygame.image.load('textbox.png')
    message = []
    k = ['a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p',
    'q','r','s','t','u','v','w','x','y','z']
    r = dict(zip(k,k))
    
    screen.blit(img, (height,width))
    
    while True:
        fonts = fontobject.render("%s"%string.join(message,""),1 , (255,255,255))
        for event in pygame.event.get():
            for i in r:
                if event.type == KEYDOWN:
                    if event.key == ord(r[i]):
                        message.append(i)
                        screen.blit(fonts,(height+3, width+7))
                    if event.key == K_SPACE:
                        message.append(" ")
                        screen.blit(fonts,(height+3,width+7))
                    if event.key == K_BACKSPACE:
                        message = message[0:-1]
                    elif event.key == K_ESCAPE:
                        pygame.quit()
                        sys.exit()
                    elif event.key == K_RETURN: 
                        return string.join(message,"")
                        break            
            pygame.display.flip()    
screen = pygame.display.set_mode((600,680))
t = print_text(screen, (150,250))
print t

```
I have almost everything up and working except I can't seems to get it to delete a single char in the list message. ayuda por favor?

---

