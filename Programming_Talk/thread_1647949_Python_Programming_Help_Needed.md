---
title: "Python Programming Help Needed"
date: 2010-12-18
forum: Programming Talk
---

### Post by Bigmon on 2010-12-18
Hi !
I wonder if any experienced programmers can point me in the right direction with a game I am doing for a python project. 
In the game, a little figure moves across the screen(the_elly) and when it reaches the other end it disappears and a new one is created. Except I want the new one to appear in a different random location. However, the new one always appears in the same location ?
Any help appreciated. (sorry, not sure why the code is all left aligned!)



from livewires import games,color
import random

games.init(screen_width = 640, screen_height = 480, fps = 50)

mum_image = games.load_image("background.jpg", transparent = False)
games.screen.background = mum_image


class Elly(games.Sprite):

    image = games.load_image("Elly.jpg")

    def __init__(self,x = random.randint(2,400),y=20):
        super(Elly,self).__init__(image = Elly.image,
                                  x=x,
                                  y=y,
                                  dx = 0,
                                  dy = 1)

        self.score = games.Text(value = 0,
               size = 60,
               color = color.red,
               x = 550,
               y = 30)
        games.screen.add(self.score)

    


    def update(self):

        if self.bottom > games.screen.height:
            
            self.destroy()
            self.add_new_elly()

    def add_new_elly(self):
            
            new_the_elly = Elly()
            games.screen.add(new_the_elly)
            


class Jake(games.Sprite):

    

    image = games.load_image("jake.jpg")

    def __init__(self,x = 320,y=20):
        super(Jake,self).__init__(image = Jake.image,
                                  x =x,
                                  y =y)

        

    

    def update(self):
        
        self.y = 450
        self.x = games.mouse.x
        if self.left<0:
            self.left = 0

        if self.right > games.screen.width:
            self.right = games.screen.width


def main():

    the_elly = Elly()
    games.screen.add(the_elly)

    the_jake = Jake()
    games.screen.add(the_jake)
    games.mouse.is_visible = False
    games.screen.add(the_jake)
    
    games.screen.mainloop()

main()

---

### Post by juancarlospaco on 2010-12-18
Use [ code]   [ /code]
:(

---

### Post by Bigmon on 2010-12-18
I think that I have found the problem. I inserted a new bit of code:

def add_new_elly(self):
            
            new_the_elly = Elly(x = random.randint(2,400,))
            games.screen.add(new_the_elly)

---

