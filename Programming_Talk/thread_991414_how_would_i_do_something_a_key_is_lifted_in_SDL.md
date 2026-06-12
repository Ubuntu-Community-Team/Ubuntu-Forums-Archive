---
title: "how would i do something a key is lifted in SDL?"
date: 2008-11-23
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-11-23
tell me if you want my source but lets say i read the key input and then go to a switch statement where i read the event and then do something per key...how would i do something until that key is lifted...

---

### Post by Lux Perpetua on 2008-11-23
The relevant information is here: 

[http://www.libsdl.org/cgi/docwiki.cgi/Introduction_to_Events](http://www.libsdl.org/cgi/docwiki.cgi/Introduction_to_Events)
[http://www.libsdl.org/cgi/docwiki.cgi/SDL_KeyboardEvent](http://www.libsdl.org/cgi/docwiki.cgi/SDL_KeyboardEvent)

You can check for SDL_KEYUP to figure out if the key has been lifted. 

By the way, SDL has great documentation:

[http://www.libsdl.org/cgi/docwiki.cgi/SDL_API](http://www.libsdl.org/cgi/docwiki.cgi/SDL_API)

---

### Post by jimi_hendrix on 2008-11-23
thanks

---

### Post by jimi_hendrix on 2008-11-23
ok that stuff didnt really help but why is this code wrong [php]void handleInput()
    {
        bool keepGoing = true;
        while (keepGoing == true)
        {
            keepGoing = false;

            //get the keystate and begin checking for keydowns
            Uint8* Keys = SDL_GetKeyState(NULL);

            if(Keys[SDLK_LEFT])
            {
                x -= velX;
                keepGoing = true;
            }

            if(Keys[SDLK_RIGHT])
            {
                x += velX;
                keepGoing = true;
            }
        }
    }
[/php]

---

### Post by jimi_hendrix on 2008-11-23
it just hangs

---

### Post by jimi_hendrix on 2008-11-24
bump

---

### Post by raf_kig on 2008-11-24
> SDL_GetKeyState:
Gets a snapshot of the current keyboard state. The current state is returned as a pointer to an array. The size of this array is stored in numkeys. The array is indexed by the SDLK_* symbols (see SDLKey). A value of 1 means that the key is pressed and a value of 0 means that it is not. **The pointer returned is a pointer to an internal SDL array. It will be valid for the whole lifetime of the application and should not be freed by the caller.**

Note: **Use SDL_PumpEvents to update the state array.**
I suggest reading [http://www.libsdl.org/cgi/docwiki.cgi/SDL_GetKeyState](http://www.libsdl.org/cgi/docwiki.cgi/SDL_GetKeyState) before using the function ;-)

Regards

raf

---

### Post by jimi_hendrix on 2008-11-24
ill try it later and tell if it works

---

### Post by slavik on 2008-11-24
oldie but goodie? those were the days ...

[http://ubuntuforums.org/showthread.php?t=490914](http://ubuntuforums.org/showthread.php?t=490914)

---

### Post by jimi_hendrix on 2008-11-24
looked at the code where you handled input and couldnt figure out how you did it...but i have a break coming up so i will have plenty of time to figure this out

---

### Post by slavik on 2008-11-24
yeah, that's the bad part of the code :(

the idea is that the keysym returns an array where 1 is the key is pressed and 0 the key being unpressed (the key is an index in the array). what you want to do is act while the key is pressed. grabbing the keysym happens every iteration.

---

### Post by jimi_hendrix on 2008-11-24
right...i can make my ship move when the player hits a key...but if they hold the key down it stands still until they pick their finger up and press the key again...i want it to keep on moving

---

### Post by slavik on 2008-11-24
my code does that, compile it ;)
look carefully at the bodies of the if statements.

---

### Post by jimi_hendrix on 2008-11-24
i know...im trying to figure out how it does that ;)

---

