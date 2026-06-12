---
title: "pygame doesn't read events in scripts"
date: 2012-12-06
forum: Programming Talk
---

### Post by snowlizard31 on 2012-12-06
I have two files  that use pygame's event handling but if I using it in both cause's one of the scripts events not to be read, so I tried passing event as an parameter in one but that still doesn't work.
script 1 the main script 
```

for event in pygame.event.get():
            text = test.print_text(screen,35,event,(250,410))
            if event == pygame.QUIT:
                pygame.quit()
                sys.exit()

```
script 2
```

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

```

---

