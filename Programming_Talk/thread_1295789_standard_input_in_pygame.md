---
title: "standard input in pygame"
date: 2009-10-19
forum: Programming Talk
---

### Post by JDShu on 2009-10-19
Hey, I've been playing with pygame for a couple of days. I'm trying to make a high score table for my program and in order to do so I need some way for the player to input their name on the keyboard. Is there an efficient way to do this in pygame? Thanks in advance.

---

### Post by JDShu on 2009-10-20
impossible/stupid question? :(

---

### Post by lavinog on 2009-10-20
found something here: [http://www.pygame.org/pcr/inputbox/index.php](http://www.pygame.org/pcr/inputbox/index.php)

```

while 1:
    inkey = get_key()
    if inkey == K_BACKSPACE:
      current_string = current_string[0:-1]
    elif inkey == K_RETURN:
      break
    elif inkey == K_MINUS:
      current_string.append("_")
    elif inkey <= 127:
      current_string.append(chr(inkey))
    display_box(screen, question + ": " + string.join(current_string,""))
  return string.join(current_string,"")


```

---

### Post by JDShu on 2009-10-20
Oh wow, thank you so much! The code in the link answers a lot of questions.

---

