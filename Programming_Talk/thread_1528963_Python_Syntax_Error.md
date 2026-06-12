---
title: "Python Syntax Error"
date: 2010-07-11
forum: Programming Talk
---

### Post by skaarr on 2010-07-11
Running from the command line I get this error. The thing is, the program I'm running is 33 lines long. When I try to run it in IDLE, it gives the same error and highlights the last space after the text on the last line of the program. Thanks for any help in advance.


The error:
```
:~$ python v.py
  File "v.py", line 34
    
                                  ^
SyntaxError: invalid syntax
```

---

### Post by Tony Flury on 2010-07-11
Try posting the code - in code tags - so we can actually help.

It could be something simple like a missing bracket.

---

### Post by skaarr on 2010-07-11
Here's the code:
```
import pygame
import os.path, sys

pygame.init()
mixer = pygame.mixer

main_dir = os.path.split(os.path.abspath(__file__))[0]

def main(file_path=None):

    if file_path is None:
        file_path = os.path.join(main_dir,
                                 'data',
                                 'mp3.ogg')
    mixer.init(11025) #raises exception on fail   
    sound = mixer.Sound(file_path)
    print ('Playing Sound...')
    channel = sound.play()
    playing = True
    while playing:
        track_length = sound.get_length()
        w = 300
        h = 70
    rect_w = 50
        screen = pygame.display.set_mode((w,h))
        pygame.draw.rect(screen, (0, 255, 0), (10, 10, track_length, rect_w))
        drawing = True
    time_passed = pygame.time.get_ticks()
    pygame.draw.rect(screen, (225, 0, 0), (15, 15, time_passed, (rect_w - 5))


if __name__ == '__main__':
    if len(sys.argv) > 1:
        main(sys.argv[1])
    else:
        main()
```

To add to what I wrote earlier, IDLE takes issue with the colon after '__main__'  but if I remove the last section of code entirely then the issue I described above begins to happen. Thanks for any help, I'm teaching myself python and this is just an experiment I wanted to try (so if you spot any poor coding practices etc feel free to point them out :) ). Also, the number of lines is different here because I removed the comments.

---

### Post by wmcbrine on 2010-07-11
The indentation of the "rect_w = 50" line is wrong, assuming that it's meant to be part of the "while playing" loop. Either way, that line is then followed by three indented lines, which are orphans (presumably meant to be in the "while playing" block).

You're also missing a closing parens on the last "pygame.draw.rect" line. I think that's the source of the error (although the other thing is also an error).

---

### Post by skaarr on 2010-07-11
Thanks! That fixed it.

You were right, the missing parenthesis were the problem (so many brackets!)
Feel a bit silly missing the formatting error at 'rect_w' but it seems it was due to using the tab key to indent that line which is why I never saw it, but then that's an even sillier mistake... Oh well :P

Thanks very much for your help.

---

### Post by Tony Flury on 2010-07-11
> **skaarr said:**
> Thanks! That fixed it.
Feel a bit silly missing the formatting error at 'rect_w' but it seems it was due to using the tab key to indent that line which is why I never saw it, but then that's an even sillier mistake... Oh well :P

Thanks very much for your help.

Which ever editor you are using configure it to convert Tabs to spaces - that way you can still use the Tab key but the indentation still works.

---

