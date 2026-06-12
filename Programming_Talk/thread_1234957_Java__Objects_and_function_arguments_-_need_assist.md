---
title: "Java / Objects and function arguments - need assistance."
date: 2009-08-08
forum: Programming Talk
---

### Post by credobyte on 2009-08-08
Why I'm not allowed to create an object and pass an argument as it's name ?


**Error:**
```
Game.java:9: alias is already defined in MakeBot(java.lang.String,java.lang.String)
        GameBot alias = new GameBot(name);
                ^
1 error
```**Game.java**
```
public class Game {

    public static void main(String args[]) {
        MakeBot("bot1", "Computer #1");
        MakeBot("bot2", "Computer #2");
    }
    
    static void MakeBot(String alias, String name) {
        GameBot alias = new GameBot(name);
    }
    
}

class GameBot {

    String name;
    int health, strength, defense;
    
    public GameBot(String iName) {
        name = iName;
        health = 60;
        strength = 18;
        defense = 10;
    }
    
}

```

---

### Post by Enk on 2009-08-08
"alias" is already defined as a the function parametre.

Oh, I see what you are trying. You cannot use the passed String as a name for an object!


You should rather just save your bots in an array/list, and maybe make alias an member attribute (if you need it). 

```

GameBot[] bots = new GameBot[MAX_BOTS];
int numBots = 0;
...
static void MakeBot(String name) {
  bots[numBots++] = new GameBot(name);
}

...
static GameBot getBotByName(String name) {
    for(GameBot bot : bots) {
        if(bot.getName().equals(name)) return bot;
    }

    return null;
}

```

Or something. You could probably use a hashmap too, but an array is desirable in games (for performance). It is generally better to use the bot's position in the array as an ID, rather than using names for the bots tho.

---

### Post by credobyte on 2009-08-08
> **Enk said:**
> "alias" is already defined as a the function parametre.

Oh, I see what you are trying. You cannot use the passed String as a name for an object!

Sad to hear that :( Any workarounds ? Is it even possible to create an object from a predefined string ?

---

### Post by Enk on 2009-08-08
I do not understand why you want to be able to do that? 

Create a GameBotManager-class which controlls all the gamebots. 

```

class GameBotManager {
    private GameBot bots[];
    private int maxNumBots;
    private int numBots;

    public GameBotManager(int maxNumBots) {
        this.maxNumBots = maxNumBots;
        bots = new GameBot[maxNumBots];
    }

    ...

    public void newBot(String name) {
        bots[numBots] = new GameBot(name);
        numBots++;
    }

    ...
  
    public GameBot getBot(int id) {
        // Maybe make sure id < maxNumBots
        return bots[id];
    }

    public GameBot getBot(String name) {
        for(GameBot bot : bots) {
            if(bot.getName().equals(name)) return bot;
        }
        
        return null;
    }

    ...

    public void updateBots() {
        for(GameBot bot : bots) {
            if(bot != null) {
                bot.update();
            }
        }
    }

    public void render() {
          // just as update
    }

    ... etc

}

```

This is just an example of how I would have done it (so not perfect). But it is easy and it works.

This is not optimal for dynamically removing/adding bots, but this can also be done easily (e.g. when creating a new bot loop through the bots-array till you find an empty spot = bot is null). Using ArrayLists may seem more elegant but it can give awful performance-issues.

---

### Post by credobyte on 2009-08-08
> **Enk said:**
> I do not understand why you want to be able to do that? 

Create a GameBotManager-class which controlls all the gamebots. 

[COLOR=Gray][code][/COLOR]

This is just an example of how I would have done it (so not perfect). But it is easy and it works.

This is not optimal for dynamically removing/adding bots, but this can also be done easily (e.g. when creating a new bot loop through the bots-array till you find an empty spot = bot is null). Using ArrayLists may seem more elegant but it can give awful performance-issues.

Thank you :) The reason why I wanted to do this was .. I'm really new in Java world ( have done only a few "Goodbye, cruel world!" type tutorials ).

---

