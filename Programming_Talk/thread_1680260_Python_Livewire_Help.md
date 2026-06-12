---
title: "Python Livewire Help"
date: 2011-02-02
forum: Programming Talk
---

### Post by Bigmon on 2011-02-02
I wonder if anyone can help. I am trying to do a "simon Says" game
in Python using "livewire". When I run the following code I get an error. I am trying to add the first few elements from a list to another list, and then add them to the screen. But it does not seem to work.
Any help appreciated !!!!!



from livewires import games
import random

games.init(screen_width = 640, screen_height = 480, fps = 50)

simon_says_list = ["red.jpg",
                   "green.jpg",
                   "green.jpg",
                   "blue.jpg",
                   "red.jpg",
                   "green.jpg",
                   "blue.jpg"]
random.shuffle(simon_says_list)

first_picture = []
first_picture.append(simon_says_list[0:2])
simon_says = games.Animation(images = first_picture,
                            x = games.screen.width/2,
                            y = games.screen.height/2,
                            n_repeats = 1,
                            repeat_interval = 200)
games.screen.add(simon_says)

games.screen.mainloop()

---

### Post by raydeen on 2011-02-03
What is the error message you're getting? I just tried to run it and couldn't because I don't have Pygame installed. Do you have Pygame installed on your machine?

---

