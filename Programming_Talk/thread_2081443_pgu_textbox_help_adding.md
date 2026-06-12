---
title: "pgu textbox help adding"
date: 2012-11-06
forum: Programming Talk
---

### Post by snowlizard31 on 2012-11-06
I'm trying to get  a textbox in some code but I can't seem to get a textbox to appear on 
screen 
python pygame extension module pgu
```

# -*- coding: utf-8 -*-
import random, sys, codecs
import pygame
import pgu

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
    f = codecs.open( "kanji_dict.txt", "r", encoding = "utf-8")
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
            #gui.event(event)
        
        rnd   = random.randint(0, len(kanji)-1)
        label_k = kanji_font.render(u"%s"%kanji[rnd],True,BLACK)
        label_r = read_font.render(u"%s"%read[rnd],True,BLACK)
        crt   = d_font.render("Correct: %d"%correct,True, BLACK)
        
        screen.blit(bck_img, bck_rect)
        screen.blit(label_k, (250,100))
        screen.blit(label_r, (280,300))
        screen.blit(crt, (670,15))
        
        

        pygame.display.flip()
    
main()


```I want to be able to make the rnd variable delay and wait for userinput that i get from the created text box

---

