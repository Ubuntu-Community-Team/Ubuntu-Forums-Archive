---
title: "Help with mouse event pygame python"
date: 2013-08-29
forum: Programming Talk
---

### Post by snowlizard31 on 2013-08-29
Hi guys I'm trying to make a menu for a program I'm working on and I've seem to hit a road block.
The problem is I don't get any response or inccorrect output from my code; I've tried several ways to get the desired output but can't get it right :(.. the functions are part of class create_menu() that doesn't inherit anything.

```

    def render_text(self,item):
        for entry in item:
            self.text = self.Text.render(entry, 1, (255,255,255))
            self.text_pos = self.text.get_rect(centerx=self.screen.get_width()/2,\
            centery=self.centerY+self.font_size + self.font_space)
            
            self.text_pos_list.append(self.text_pos)
            self.centerY = self.centerY+ self.font_size + self.font_space
            self.screen.blit(self.text, self.text_pos)
        
    # this function does not work need to work on it~!!!
    def check_mouse(self):
        self.text_rect = self.text.get_rect()
        #print self.text_pos_list
        #if self.text_rect.collidepoint(pygame.mouse.get_pos()): #this just keeps printing hello
        #    print 'hello'
        if pygame.mouse.get_pos() == self.text_rect: # does nothing
            print 'hi'

```

So I figured It out I should have used the list  self.text_pos_list instead
I'll leave the answer just in case anyone needs it
```

    def check_mouse(self):
        for rect in self.text_pos_list:
            if rect.collidepoint(pygame.mouse.get_pos()):
                if rect == self.text_pos_list[0]:
                    print "i"
                elif rect == self.text_pos_list[1]:
                    print "e"
        

```

---

