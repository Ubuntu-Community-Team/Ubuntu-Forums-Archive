---
title: "Need help debugging Lua scripts for GMod10"
date: 2008-03-25
forum: Programming Talk
---

### Post by chumchum on 2008-03-25
Hello all
I've been trying to create a mod for GMod 10, you can see the original idea/post [here]("http://forum.moddb.com/thread/23950/?page=2").(only the last post is relavent, to this thread)
AS you can see the thread died an no one there can help me, so I turned to you guys =D.
Anyway, my problem is...well I don't know the problem, which is why I want to debug my code in source with dev console and have tried to do somaking a command for each of my functions that returns text to see if code is working.
I tried this at first (yeah it's all in the thread) and my commands didn't return anything(even for working code), so I wanted to know if my code for creating console commands was even working, so I wrote this script 


> function testfunction()
player.GetByID( 1 ):PrintMessage( HUD_PRINTCENTER, "LOLZ" )
end

concommand.Add("laugh", testfunction()) 

Alas, this didn't work.
Does anyone know what I got wrong and could they please tell me how to fix it.
Any help and suggestions will be appreciated :D

Oh, and you'll probably need this since any Lua scripters out there won't necesserally be familiar with GMod 10 functions ;)
[http://www.garrysmod.com/wiki/?title=Server_Function_Dump](http://www.garrysmod.com/wiki/?title=Server_Function_Dump)
[http://www.garrysmod.com/wiki/?title=Client_Function_Dump](http://www.garrysmod.com/wiki/?title=Client_Function_Dump)
[http://www.garrysmod.com/wiki/?title=Global_Functions](http://www.garrysmod.com/wiki/?title=Global_Functions)

---

### Post by PaulFr on 2008-03-26
Not knowing Lua and not having GMOD, I highly doubt I can help :-) But then rushing to tread where ... and all that, I would suggest you try the example function in **[http://www.garrysmod.com/wiki/?title=Common_Code_Snippets#Adding_a_console_command](http://www.garrysmod.com/wiki/?title=Common_Code_Snippets#Adding_a_console_command)** first. That seems straightforward enough to me.

BTW, when I say use the example function, use it exactly as is to see whether it works. Do not add or subtract anything (especially the function parameters).

*Update*: AFAICS, the first parameter in that example function is the player object **ply** and so if the example above works, you can try changing the body of the function to > [COLOR=#0000dd]**[local]("http://www.garrysmod.com/wiki/?title=local")**[/COLOR] playerName = ply:[GetName]("http://www.garrysmod.com/wiki/?title=.GetName")[COLOR=#000000]**(**[/COLOR][COLOR=#000000][B])
[/B][/COLOR]ply:[PrintMessage]("http://www.garrysmod.com/wiki/?title=Player.PrintMessage")[COLOR=#000000]**(**[/COLOR] HUD_PRINTTALK, [COLOR=#222222]"This is a message from "[/COLOR] .. playerName [COLOR=#000000]**)**[/COLOR]

---

### Post by chumchum on 2008-03-26
OK thank you for that =D (didn't know there was a list of code snippets :oops:)

---

