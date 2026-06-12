---
title: "pygame event handling multiple scripts"
date: 2013-01-17
forum: Programming Talk
---

### Post by snowlizard31 on 2013-01-17
I was wondering how I can have two scripts both with pygame events work at the same time with one of the scripts being the main script where it's events are read first and then the other scripts events are read. I've tried making functions in both where the take the event parameter but it doesn't work it just freezes the app.

---

### Post by Tony Flury on 2013-01-23
> **snowlizard31 said:**
> I was wondering how I can have two scripts both with pygame events work at the same time with one of the scripts being the main script where it's events are read first and then the other scripts events are read. I've tried making functions in both where the take the event parameter but it doesn't work it just freezes the app.

A better way to do things would be to have your main loop in one script - That script also imports a 2nd script which defines functions/classes/methods for dealing with your events. In fact you could have a whole range of imported scripts, which deal with different events in different ways.

Your main loop just needs to call the right function for the right event.

---

### Post by snowlizard31 on 2013-01-24
Thank you that helped me out a lot. If its not to much trouble would happen to know how I can make pygame wait for a function to return something in my case a variable. This is still part of the two scripts

---

### Post by Tony Flury on 2013-01-27
Unless you are using threads (which I doubt you are) python ( and therefore pygame) will always wait for your functions to return a value before executing the next instruction.

```

... Code section a
.... Functional call
.... Code section b

```

You can guarantee in a non threaded program that code section b will execute only after the function has completed and returned whatever values it should.  Even in threaded programs you can rely on this behaviour unless the function call for instance starts a new thread but does not wait for completion. 

Do you have an example of code where you think it isn't doing that ?

---

### Post by snowlizard31 on 2013-01-28
```

while True:            
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
        
        
        if event == pygame.QUIT:
            pygame.quit()
            sys.exit()
        # line 52 it just iterates and keeps adding 1 to the incorrect variable
        text = test.print_text(screen,34,(230,510))
        if text == english[rnd]:#and if i press escape to quit it just resets    
            correct += 1       #incorrect to 0 clicking escapes does nothing
        else: 
            incorrect += 1    
        pygame.display.flip()
    


event = pygame.event.get()
main(event)


```
If I try pressing key it only displays the key on screen for a fraction of a second and keeps iterating

---

