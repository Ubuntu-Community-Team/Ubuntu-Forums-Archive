---
title: "strings don't match but equal each other"
date: 2012-11-12
forum: Programming Talk
---

### Post by snowlizard31 on 2012-11-12
I made a text box in pygame and I tried run it in my other code but the text box stops all other events and doesn't resume them untill i press enter but only for like a second. And I think this is the cause why I can't match strings 
Textbox code
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
    r = dict(zip(k,k))
    
    message = ''
    while True:
        fonts = fontobject.render("%s"%message,1 , (0, 0, 0))
        for event in pygame.event.get():
            # for loop with if for char input
            for i in r:
                if len(message) >= text_length:
                    pass
                elif event.type == KEYDOWN:
                    if event.key == ord(r[i]):
                        message += i
            
            
            # for all other non char input
            if event.type == KEYDOWN:    
                if event.key == K_BACKSPACE:
                    message = message[:-1]
                elif len(message) >= text_length:
                    pass
                elif event.key == K_SPACE:
                    message += ' '
                elif event.key == K_SEMICOLON:
                    message += ';'
                elif event.key == K_BACKQUOTE:
                    message += '`'
                elif event.key == K_LEFTBRACKET:
                    message += '['
                elif event.key == K_RIGHTBRACKET:
                    message += ']'
                elif event.key == K_COMMA:
                    message += ','
                elif event.key == K_PERIOD:
                    message += '.'
                elif event.key == K_SLASH:
                    message += '/'
                elif event.key == K_MINUS:
                    message += '-'
                elif event.key == K_EQUALS:
                    message += '='
                elif event.key == K_BACKSLASH:
                    message += '\\'                 
                elif event.key == K_QUOTE:
                    message += "'"
                elif event.key == K_ESCAPE:
                    pygame.quit()
                    sys.exit()
                elif event.key == K_RETURN: 
                    return message
            
            
            screen.blit(img, (height,width))
            screen.blit(fonts,(height+4, width+6))
            pygame.display.flip()    


#screen = pygame.display.set_mode((600,680))
#t = print_text(screen, (150,250))

# this works
#if t == 'crazy':
#    print "correct"

```project code
```

# -*- coding: utf-8 -*-
import random, sys, codecs
import pygame
import test

pygame.init()
bck_img = pygame.image.load('background.png')
bck_rect = bck_img.get_rect()
size = (width,height) = bck_img.get_size()
screen = pygame.display.set_mode(size)
pygame.display.set_caption('RTK')
BLACK = (0, 0, 0)

kanji_font = pygame.font.Font('/Library/Fonts/&#21326;&#25991;&#20223;&#23435;.ttf',200)
read_font  = pygame.font.Font('/Library/Fonts/&#21326;&#25991;&#20223;&#23435;.ttf',48)
d_font = pygame.font.Font('/Library/Fonts/Tr2n.ttf', 30)


def main():
    f = codecs.open( "rtk lessons/kanji_set2.txt", "r", encoding = "utf-8")
    kanji, read, english = [], [], []
    
    for ln in f:
        col = ln.split( "|" )
        kanji.append(col[0].strip())   #append column of kanji to kanji variable
        read.append(col[1].strip())    #append column of on readings to read var
        english.append(col[2].strip()) #append english meaning to english var
    correct = 0
                
    
    
    
    while True:
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                sys.exit()
            
        
        rnd   = random.randint(0, len(kanji)-1)
        label_k = kanji_font.render(u"%s"%kanji[rnd],True,BLACK)
        label_r = read_font.render(u"%s"%read[rnd],True,BLACK)
        crt   = d_font.render("Correct: %d"%correct,True, BLACK)
        
        screen.blit(bck_img, bck_rect)
        screen.blit(label_k, (250,100))
        screen.blit(label_r, (280,300))
        screen.blit(crt, (670,15))
        
        # problem h
        text = test.print_text(screen,30, (295,380))
        if test == english[rnd]:
            print 'corect'
        else: 
            correct += 1
        
        pygame.display.flip()
    
main()

```
PS : sorry about the title i couldn't come with anything better

---

### Post by ofnuts on 2012-11-12
```

text = test.print_text(screen,30, (295,380))         
if test == english[rnd]:

```Matching with "test" or with "text"?

---

### Post by snowlizard31 on 2012-11-12
lol I feel stupid I can't believe I missed that haha thank you thought !:)

---

