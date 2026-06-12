---
title: "[SOLVED] Image Management"
date: 2008-04-19
forum: Programming Talk
---

### Post by Zeotronic on 2008-04-19
C++/SDL: I've been working on a game for quite some time... and its all too often I find my lack of foresight catching up with me... this has occurred again. I have decided that my image management system is inadequate.

What I was doing was storing all of my SDL_Surfaces in a structure which I called 'Image_File', along with their file names (so that anything requesting to load loaded images would just use them)... and I had a vector array of 'Image_File' to store all of the images, which are referenced when their needed by their index number (an integer). Anyways, I have decided (and if you have a solution, by all means...) that my system is a poor one... it doesn't allow for me to unload unneeded images, without unloading and reloading everything.

*So*... before I continue in my coding, I just thought I should try and get some help... to make sure that I don't have to go back and re-write this system again. Does anyone have any ideas on how I should implement image management?

---

