---
title: "pygame event not checked?"
date: 2012-12-02
forum: Programming Talk
---

### Post by snowlizard31 on 2012-12-02
when I run this code I can never get the if event == pygame.QUIT: to work 
```


# -*- coding: utf-8 -*-
import random, sys, codecs
import pygame
import test, py


pygame.init()
#pygame.mixer.init()
#load sound
c = pygame.mixer.Sound('sounds/corrent.wav')
ic = pygame.mixer.Sound('sounds/incorrect.mp3')
# load image
bck_img = pygame.image.load('images/background.png')
bck_rect = bck_img.get_rect()
size = (width,height) = bck_img.get_size()
screen = pygame.display.set_mode(size)
pygame.display.set_caption('RTK')
BLACK = (0, 0, 0)
#fonts
kanji_font = pygame.font.Font('Fonts/&#21326;&#25991;&#20223;&#23435;.ttf',200)
read_font  = pygame.font.Font('Fonts/&#21326;&#25991;&#20223;&#23435;.ttf',48)
d_font = pygame.font.Font('Fonts/Tr2n.ttf', 30)

def main():
    f = codecs.open( "rtk lessons/kanji_set2.txt", "r", encoding = "utf-8")
    kanji, read, english = [], [], []
    
    for ln in f:
        col = ln.split( "|" )
        kanji.append(col[0].strip())   
        read.append(col[1].strip())    
        english.append(col[2].strip()) 
    correct = 0
    incorrect = 0
                
    while True:
        for event in pygame.event.get():
            if event == pygame.QUIT:    
                pygame.quit()
                sys.exit()
            
        rnd   = random.randint(0, len(kanji)-1)
        label_k = kanji_font.render(u"%s"%kanji[rnd],True,BLACK)
        label_r = read_font.render(u"%s"%read[rnd],True,BLACK)
        crt   = d_font.render("Correct: %d"%correct,True, BLACK)
        incrt =    d_font.render("InCorrect: %d"%incorrect,True, BLACK)
        
        screen.blit(bck_img, bck_rect)
        screen.blit(label_k, (250,100))
        screen.blit(label_r, (280,300))
        screen.blit(crt, (670,19))
        screen.blit(incrt,(660,50))

        text = test.print_text(screen,30, (250,410))
        
        if text == english[rnd]:
            correct += 1
            c.play()
            
        else: 
            ic.play()
            incorrect += 1
            
        pygame.display.flip()
    
main()


```
thanks for the help!

---

### Post by kostkon on 2012-12-03
Just replace the line
```
if event == pygame.QUIT:
```
to
```
if event.type == pygame.QUIT:
```
:P

---

### Post by snowlizard31 on 2012-12-03
Thank you ;D

---

