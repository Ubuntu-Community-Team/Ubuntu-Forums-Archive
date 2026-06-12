---
title: "SDL loop problem"
date: 2011-01-27
forum: Programming Talk
---

### Post by gufide on 2011-01-27
Hi, I get start to make my first project excluding tutorial. I want to copy the old game [chip's challenge]("http://takegame.ru/arcade/gam/chipschallenge.zip"). I know this is a bit hard to start, but it's almost finished, but I got a problem in my main sdl loop. At the beginning of my project, I put the wait event and I enable the key repeat with SDL_EnableKeyRepeat(int delay, int interval), I put 10 and 200. But I had to refresh a least 30 frame/sec. and not only when I press a key. So, I put pollEvent. That is the problem. when I put pollEvent, but the key is repeated each time it restart the loop, and I can't put SDL_Delay because I have to refresh and verify actions! No one can help me?

LEFT RIGHT UP DOWN is an enumeration
this is my mais sdl loop:
```
while (continue)
    {
        if ( SDL_GetTicks() - chipper.getTimeStartWait() > 750)
        {
            chipper.setDirection(DOWN);
            chipper.setTimeStartWait(SDL_GetTicks());
        }
        for(i = 0 ; i<lvl.getHeight() ; i++)
        {
            for(j = 0 ; j<lvl.getWidth() ; j++)
            {
                    gameActions.doGameEvent(lvl, i, j);   //do some actions
            }
        }
        mainWin.redrawlvl(chipper, lvl);        //refresh
        gameActions.doCharacterEvent(chipper, lvl);     //do character actions
        SDL_PollEvent(&pollev);
        switch(pollev.type)
        {
            case SDL_QUIT:
                continue = false;
                break;

            case SDL_KEYDOWN:
                switch(pollev.key.keysym.sym)
                {
                    default:
                        break;

                    case SDLK_UP:
                            gameActions.addToMoveList(UP);
                        break;

                    case SDLK_DOWN:
                            gameActions.addToMoveList(DOWN);
                        break;

                    case SDLK_LEFT:
                            gameActions.addToMoveList(LEFT);
                        break;

                    case SDLK_RIGHT:
                            gameActions.addToMoveList(RIGHT);
                        break;
                }
        }
    }
```

---

### Post by gufide on 2011-01-28
no one can help me?

---

### Post by Zugzwang on 2011-01-29
> **gufide said:**
> no one can help me?

It's a little bit tricky to help you because you have already chosen to do down a path which is very uncommon - namely using "SDL_EnableKeyRepeat". Since apparently noone here has experience with that, I can only suggest you to reconsider using that function altogether and instead have a look at [this tutorial]("http://lazyfoo.net/SDL_tutorials/lesson32/index.php") - the way to get framerate-independent movement described there is hassle-free. If you have any questions with that, you can come back and ask questions about that one. Then, you'll probably get more answers as this is more or less the "standard" way.

---

### Post by gufide on 2011-01-29
mh... It's not exacly this. The problem is each time it make the loop, if a key is pressed, it will call gameAction.addToMoveList(). But not each time I press the key. So, my character will move again and again... But I just want to call this function each 200 ms if the key is pressed

---

