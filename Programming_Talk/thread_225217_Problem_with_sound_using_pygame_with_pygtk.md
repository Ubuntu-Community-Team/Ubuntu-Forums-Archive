---
title: "Problem with sound using pygame with pygtk"
date: 2006-07-29
forum: Programming Talk
---

### Post by forrestcupp on 2006-07-29
I am using pygame with pygtk in Python to make a simple letter/number teaching game for my 2 year old. I use pygtk to program the gui, and for this project, the mixer is all I'm using from pygame for the audio. When the program is opened, it is supposed to show the window, then play a wav file using pygame.mixer.Sound. The problem is that even though I have self.window.show_all() (for a gtk window) before the call to play the wav file, it starts playing the wav about 1-2 seconds before the window is displayed. I tried importing time and putting a time.sleep(5) between the self.window.show_all() and the call to play the wav, but that just made it wait 5 seconds before starting the wav, then the 1-2 seconds later the window was displayed. Does anyone know how to solve this? 

Also I have a problem that when a sound is playing if I keep clicking the buttons, the button clicks just queue so that it will just keep playing the sounds that are connected with the buttons that were clicked.  I tried making a method that disconnected all the buttons when a sound is being played and another one that reconnects them afterward, but that didn't change anything.

Anyone have any ideas about these two things?

---

