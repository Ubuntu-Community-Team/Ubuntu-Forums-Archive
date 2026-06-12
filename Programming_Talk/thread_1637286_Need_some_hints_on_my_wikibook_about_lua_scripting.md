---
title: "Need some hints on my wikibook about lua scripting"
date: 2010-12-04
forum: Programming Talk
---

### Post by Pithikos on 2010-12-04
I am writing a book in wikibooks about the Spring engine if someone have heard of(maybe Total Annihilation rings a bell). :redface:

Anyway I have a page with reference for functions from the engine that can be used with scripting. Check the [link]("http://en.wikibooks.org/wiki/Lua_in_SpringRTS/Callouts").
There is a table with each row keeping a bit information about each function like **function name, description, arguments, return values**. Here is an example of my [COLOR=Red]first method[/COLOR]:
```

Spring.KillTeam     |     Will declare a team to be dead. New in version 0.83.x     |     teamID     |     nil

```Then I have a second page explaining each argument name. For example you wouldn't be able to interpret what teamID is and what type of data it is. That's why in this page there is the bellow table: 
```

_Name_____________Type________________________________Description____________________________________________
teamID     |     integer     |     Each team in the game has a unique ID. Players with the same team ID share their units.

```Before doing my reference this way it used to be in the form([COLOR=Red]second method[/COLOR]):
```

Spring.KillTeam     |     Will declare a team to be dead. New in version 0.83.x     |     number teamID     |     nil

```My question now. If you were reading a programming book which methology would you find easiest to follow? The first method makes it look cleaner when there are many arguments. You got some hints?

---

