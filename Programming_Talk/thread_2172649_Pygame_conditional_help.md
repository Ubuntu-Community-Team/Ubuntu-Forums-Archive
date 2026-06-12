---
title: "Pygame conditional help"
date: 2013-09-05
forum: Programming Talk
---

### Post by snowlizard31 on 2013-09-05
Hi I'm tyring to check for event in a function in a class I made the only problem is that I don't want to keep writing down each if and elif conditional over and over again for different conditions that I test against a list of rect coords. Is there anyway I could make it so I could just pass a bunch a parameters through list and test against that? How would I ? Heres the function .
```

    def check_mouse(self):
        for rect in self.text_pos_list:
            if rect.collidepoint(pygame.mouse.get_pos()):
                if rect == self.text_pos_list[0]:
                    return self.item[0]
                elif rect == self.text_pos_list[1]:
                    return self.item[1]
                elif rect == self.text_pos_list[2]:
                    return self.item[2]
                else:
                    return False

```

---

### Post by ofnuts on 2013-09-06
> **snowlizard31 said:**
> Hi I'm tyring to check for event in a function in a class I made the only problem is that I don't want to keep writing down each if and elif conditional over and over again for different conditions that I test against a list of rect coords. Is there anyway I could make it so I could just pass a bunch a parameters through list and test against that? How would I ? Heres the function .
```

    def check_mouse(self):
        for rect in self.text_pos_list:
            if rect.collidepoint(pygame.mouse.get_pos()):
                if rect == self.text_pos_list[0]:
                    return self.item[0]
                elif rect == self.text_pos_list[1]:
                    return self.item[1]
                elif rect == self.text_pos_list[2]:
                    return self.item[2]
                else:
                    return False

```

```

    def check_mouse(self):
        for rect in self.text_pos_list:
            if rect.collidepoint(pygame.mouse.get_pos()):
                for i in range(len(self.text_pos_list)):
                   if rect == self.text_pos_list[i]:
                      return self.item[i]
                return False

```

---

### Post by nidzo732 on 2013-09-06
You could insert another for loop to replace if/elif blocks
```

def check_mouse(self):
    for rect in self.text_pos_list:
        if rect.collidepoint(pygame.mouse.get_pos()):
            for listItem in self.text_pos_list[:3]:
                if rect == listItem:
                    return listItem
        return False

```
Thic code would check only the first 3 items just like your if/elif part and if the loop exits it returns False just like your else part

---

### Post by snowlizard31 on 2013-09-06
Sweeeeeet thanks guys! I really appreciate the help!

---

