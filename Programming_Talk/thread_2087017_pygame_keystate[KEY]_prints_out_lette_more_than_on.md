---
title: "pygame keystate[KEY] prints out lette more than once"
date: 2012-11-22
forum: Programming Talk
---

### Post by snowlizard31 on 2012-11-22
The keystate (keystate = pygame.key.get_pressed()) isn't working the way I want it to work instead of print out one character on key pressed it prints out 4 characters can some one help me fix this please?
```

import pygame, sys, string
from pygame.locals import *

def print_text(screen,text_length, (height, width)):
    pygame.font.init()
    fontobject = pygame.font.Font('Fonts/Times New Roman.ttf',18)
    img = pygame.image.load('textbox.png')
    screen.blit(img, (height,width))
    pygame.display.flip()
    k = ['a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p',
    'q','r','s','t','u','v','w','x','y','z']
    K = ['A','B','C','D','E','F','G','H','I','J','K','L','M','N','O','P'
    ,'Q','R','S','T','U','V','W','X','Y','Z']
    
    r = dict(zip(k,k))
    R = dict(zip(k,K))
    
    message = ''
    while True:
        fonts = fontobject.render("%s"%message,1 , (0, 0, 0))
        keystate = pygame.key.get_pressed()
        for event in pygame.event.get():
            if event == pygame.QUIT:
                pygame.quit()
                sys.exit()
                
            # for loop with if for char input
            for i in r:
                if len(message) >= text_length:
                    pass
                elif event.type == KEYDOWN:
                    if event.key == ord(r[i]):
                        message += i
        
        if keystate[K_BACKSPACE]:
            message = message[:-1]
        elif len(message) >= text_length:
            pass
        elif keystate[K_SPACE]:
            message += ' '
        elif keystate[K_SEMICOLON]:
            message += ';'
        elif keystate[K_BACKQUOTE]:
            message += '`'
        elif keystate[K_LEFTBRACKET]:
            message += '['
        elif keystate[K_RIGHTBRACKET]:
            message += ']'
        elif keystate[K_COMMA]:
            message += ','
        elif keystate[K_PERIOD]:
            message += '.'
        elif keystate[K_SLASH]:
            message += '/'
        elif keystate[K_MINUS]:
            message += '-'
        elif keystate[K_EQUALS]:
            message += '='
        elif keystate[K_BACKSLASH]:
            message += '\\'                 
        elif keystate[K_QUOTE]:
            message += "'"
        elif keystate[K_ESCAPE]:
            pygame.quit()
            sys.exit()
        elif keystate[K_RETURN]: 
            return message
            
            
        screen.blit(img, (height,width))
        screen.blit(fonts,(height+4, width+6))
        pygame.display.flip()    


```

---

