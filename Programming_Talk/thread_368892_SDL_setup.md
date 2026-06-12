---
title: "SDL setup"
date: 2007-02-23
forum: Programming Talk
---

### Post by tjtansey on 2007-02-23
Can anyone guide me through the apparent rocket science involved in installing and setting up SDL?  Looking at the library listing is like looking at a parts list for the Space Shuttle.  I only hope the application works better.
Thanks

---

### Post by Mirrorball on 2007-02-23
Why not apt-get install libsdl1.2-dev?

---

### Post by Wybiral on 2007-02-23
Yeah, I got all of mine through synaptic and it was very quick and painless (no rocket science involved)

Just open up synaptic and search for SDL.

---

### Post by tjtansey on 2007-02-24
Thanks guys and forgive me I was caught in a bout of Einstein hair when I asked the question.  Now next idiots(my specialty) question.  If I use a file in the library, do I have to put it in the same directory as my application?

---

### Post by Mirrorball on 2007-02-24
No. They will usually be in /usr/include, but you don't have to worry, the compiler will find them.

---

### Post by tjtansey on 2007-02-24
Ok they're there.   I guess the next question is, is there something I need to do to activate them, because it seems the compiler can't find them.  What sucks about this, is I thought I found something that allowed python to do some really neat things, but every time I try to use it I get an error that such and such can't be opened.  I've gone through every bit of documentation I can find and it seems that all SDL is doing is taking up space on my hard drive. 


 I guees the question is, "what doe SDL do, if anything."

---

### Post by po0f on 2007-02-24
tjtansey,

An exact error message would help better diagnose the problem.  Are you remembering to link to the libraries?  Your compile command should contain at least "-lSDL":

```
[font="Courier New"]$ gcc -Wall -o my_binary my_source.c -lSDL -lSDL_image blar...[/font]
```

---

### Post by Mirrorball on 2007-02-24
> **tjtansey said:**
> What sucks about this, is I thought I found something that allowed python to do some really neat things
If you want to use SDL with python, why don't you install pygame? I assume you must be writing a C module for Python, but you don't need to.

---

### Post by tjtansey on 2007-02-24
> **Mirrorball said:**
> If you want to use SDL with python, why don't you install pygame? 

Funny, that's actually what I've been trying tp do with it, but I haven't been able to figure out how.

---

### Post by Mirrorball on 2007-02-24
```
apt-get install python-pygame
```

---

### Post by tjtansey on 2007-02-24
I have to be wording the question wrong so here's what I've been trying to do.  I'm trying to use some of the tutorials from pygame and here's an example of the code then the error.

tim@tim-laptop:~/Projects/game$ python chimp.py
Cannot load sound: data/whiff.wav
Mix_LoadWAV_RW with NULL src
tim@tim-laptop:~/Projects/game$ 

I guess the question is what am I missing here?

---

### Post by Mirrorball on 2007-02-24
whiff.wav can't be found. Try an absolute path to it.

---

### Post by tjtansey on 2007-02-24
OK I guess the question is where should it be for the code to find it.  I must tell you if you haven't guessed, I'm fairly new to this, so if you think it's obvious, I'll miss it :o

---

### Post by christhemonkey on 2007-02-24
On line 150(-ish) where it says:
>     whiff_sound = load_sound('whiff.wav')
This means it is loading a file 'whiff.wav' it is loading it using an earlier function:
> def load_sound(name):
    class NoneSound:
        def play(self): pass
    if not pygame.mixer or not pygame.mixer.get_init():
        return NoneSound()
    fullname = os.path.join('data', name)
    try:
        sound = pygame.mixer.Sound(fullname)
    except pygame.error, message:
        print 'Cannot load sound:', fullname
        raise SystemExit, message
    return sound 

This means that it is looking for this .wav file in a subdirectory the script was run from called data/

(so if the script is in '/home/tjtansey/Python/' , then this .wav should be in '/home/tjtansey/Python/data/whiff.wav' )

---

### Post by tjtansey on 2007-02-24
AH HA!  So basically you're saying that I need to have any objects I want to call up either in the same directory as the code or in a directory down stream from it?  Much pain and aggravation would have been saved if the tutorials I have been trying to work through would have said, "Oh by the way, you'll need these files to, and here's what to do with them."  GRRR

Thanks for your help guys, and since we are on the subject, were would you recommend finding instructions for this stuff if you haven't been to MIT?  What sucks is I am actually able to follow whats going on in the code, it's just no one mentioned the other stuff.

---

### Post by christhemonkey on 2007-02-24
No idea. Never used pygame, just had a quick glance through that python file.
There are several good python tutorials out there, i would recommend starting with one of them before moving onto pygame.

---

### Post by tjtansey on 2007-02-25
You're right about pygame, I just found the tutorials on pygtk, and boy is it already making a difference.  Anyway guys thanks for your help.

---

