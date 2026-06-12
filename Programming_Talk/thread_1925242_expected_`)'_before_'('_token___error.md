---
title: "expected `)' before '(' token   error"
date: 2012-02-14
forum: Programming Talk
---

### Post by zolax on 2012-02-14
Who can help me with this code [[img]http://i.tibia.tv/th/27/pTEfs0sdasdas.JPG[/img]](http://i.tibia.tv/27/pTEfs0sdasdas.JPG)

---

### Post by Tony Flury on 2012-02-14
Try actually posting the code (as in cut and paste of the text), rather than posting a screen shot. ALso - you will need to use the code tags (click the # in the toolbar when composing your post.

The most likely problem is that you are missing a ")" i a previous line (or you have another type of bracket where a ")" should be).

You should be able to see that the same error occurs at line 99 in your code (according to you screen shot) - you might find that fixing that one makes the others go-away.

---

### Post by zolax on 2012-02-14
```
[HIGHLIGHT=cpp]#ifdef JD_DEATH_LIST
		if (attackedplayer && attacker)
			attackedplayer->addDeath(attacker->getName(), attackedplayer->level, time(0));
#endif //JD_DEATH_LIST
		unsigned char stackpos = tile->getThingStackPos(attackedCreature);[/HIGHLIGHT]

dodaj:

[HIGHLIGHT=cpp]//tasksys									
							    	Player* attackingplayer = dynamic_cast<Player*>(attacker);                                     
									if (attackingplayer && (attackedCreature->getName() == attackingplayer->task_monster) && !(attackingplayer->task_count == attackingplayer->task_max))
                                    {
                                                                                 
                                       attackingplayer->task_count++;
                                       std::stringstream info;       
                                       std::string mons = attackingplayer->task_monster;
                                       std::transform(mons.begin(), mons.end(), mons.begin(), (int(*)(int))tolower);   
									   info << "You have killed " <<attackingplayer->task_count<< " out of " <<attackingplayer->task_max<< " " <<mons<< "s.";
									   attackingplayer->sendTextMessage(MSG_BLUE_TEXT, info.str().c_str());
									
                                    }
		//tasksys[/HIGHLIGHT]

w **ioplayerxml.cpp** pod:

[HIGHLIGHT=cpp]nodeValue = (char*)xmlGetProp(root, (const xmlChar *) "lastlogin");
		if(nodeValue){
			player->lastLoginSaved = atoi(nodeValue);
			xmlFreeOTSERV(nodeValue);
		}
		else{
			player->lastLoginSaved = 0;
		}
[/HIGHLIGHT]
dodaj:

[HIGHLIGHT=cpp]//tasksys
		nodeValue = (char*)xmlGetProp(root, (const xmlChar *) "task_monster");
        if(nodeValue){
            player->task_monster = nodeValue;
            xmlFreeOTSERV(nodeValue);
        }
        else
             isLoaded = false;

        nodeValue = (char*)xmlGetProp(root, (const xmlChar *) "task_count");
		if(nodeValue) {
			player->task_count=atoi(nodeValue);
			xmlFreeOTSERV(nodeValue);
		}
		else
			isLoaded = false;
            
            nodeValue = (char*)xmlGetProp(root, (const xmlChar *) "task_max");
        if(nodeValue){
            player->task_max = atoi(nodeValue);
            xmlFreeOTSERV(nodeValue);
        }
        else
             isLoaded = false;
            
            //tasksys[/HIGHLIGHT]

w **ioplayer.cpp** pod:

[HIGHLIGHT=cpp]sb << (long)player->lastlogin;	        xmlSetProp(root, (const xmlChar*) "lastlogin", (const xmlChar*)sb.str().c_str());  sb.str("");[/HIGHLIGHT]

dodaj:

	[HIGHLIGHT=cpp]//tasksys
	sb << player->task_monster;         xmlSetProp(root, (const xmlChar*) "task_monster", (const xmlChar*)sb.str().c_str());  sb.str("");
	sb << player->task_count;         xmlSetProp(root, (const xmlChar*) "task_count", (const xmlChar*)sb.str().c_str());  sb.str("");
	sb << player->task_max;         xmlSetProp(root, (const xmlChar*) "task_max", (const xmlChar*)sb.str().c_str());  sb.str("");
	//tasksys[/HIGHLIGHT]

w **npc.h** pod:

[HIGHLIGHT=cpp]#ifdef YUR_ROOKGARD
	lua_register(luaState, "setPlayerVocation", NpcScript::luaSetPlayerVocation);
#endif //YUR_ROOKGARD[/HIGHLIGHT]

dodaj:

[HIGHLIGHT=cpp]//tasksys
lua_register(luaState, "setPlayerTaskMonster", NpcScript::luaSetPlayerTaskMonster);
lua_register(luaState, "setPlayerTaskMax", NpcScript::luaSetPlayerTaskMax);
lua_register(luaState, "setPlayerTaskCount", NpcScript::luaSetPlayerTaskCount);
lua_register(luaState, "getPlayerTaskMonster", NpcScript::luaGetPlayerTaskMonster);
lua_register(luaState, "getPlayerTaskCount", NpcScript::luaGetPlayerTaskCount);
lua_register(luaState, "getPlayerTaskMax", NpcScript::luaGetPlayerTaskMax);
lua_register(luaState, "AddRewards", NpcScript::luaAddRewards);
lua_register(luaState, "getItemName", NpcScript::luaGetItemName);
//tasksys[/HIGHLIGHT]

w **npc.cpp** pod:

[HIGHLIGHT=cpp]int NpcScript::luaLearnSpell(lua_State *L)
{
	int cid = (int)lua_tonumber(L, -3);
	const char* words = lua_tostring(L, -2);
	int cost = (int)lua_tonumber(L, -1); 
	lua_pop(L,3);

	Npc* mynpc = getNpc(L);
	Creature* creature = mynpc->game->getCreatureByID(cid);
	Player *player = creature? dynamic_cast<Player*>(creature) : NULL;

	if (player)
	{
		if (player->knowsSpell(words))
		{
			mynpc->doSay("You already know this spell.");
		}
		else if (player->getCoins(cost)) 
		{
			if (player->removeCoins(cost)) // double check
			{
				player->learnSpell(words);
				player->sendMagicEffect(player->pos, NM_ME_MAGIC_ENERGIE);
				mynpc->doSay((std::string("To use it say: ") + std::string(words) + ".").c_str());
			}
			else
				mynpc->doSay("Sorry, you do not have enough money.");
		}
		else
			mynpc->doSay("Sorry, you do not have enough money.");
	}

	return 0;
}
#endif //YUR_LEARN_SPELLS[/HIGHLIGHT]

dodaj:


[HIGHLIGHT=cpp]//tasksys
int NpcScript::luaGetPlayerTaskMonster(lua_State* L)
{
	int id = (int)lua_tonumber(L, -1);
	lua_pop(L, 1);

	Npc* mynpc = getNpc(L);
	Creature* creature = mynpc->game->getCreatureByID(id);
	Player* player = creature? dynamic_cast<Player*>(creature) : NULL;

	if (player)
		lua_pushstring(L, player->task_monster.c_str());
	else
		lua_pushnumber(L, -1);

	return 1;
}

int NpcScript::luaGetPlayerTaskCount(lua_State* L)
{
	int id = (int)lua_tonumber(L, -1);
	lua_pop(L, 1);

	Npc* mynpc = getNpc(L);
	Creature* creature = mynpc->game->getCreatureByID(id);
	Player* player = creature? dynamic_cast<Player*>(creature) : NULL;

	if (player)
		lua_pushnumber(L, player->task_count);
	else
		lua_pushnumber(L, -1);

	return 1;
}

int NpcScript::luaGetPlayerTaskMax(lua_State* L)
{
	int id = (int)lua_tonumber(L, -1);
	lua_pop(L, 1);

	Npc* mynpc = getNpc(L);
	Creature* creature = mynpc->game->getCreatureByID(id);
	Player* player = creature? dynamic_cast<Player*>(creature) : NULL;

	if (player)
		lua_pushnumber(L, player->task_max);
	else
		lua_pushnumber(L, -1);

	return 1;
}

int NpcScript::luaSetPlayerTaskMonster(lua_State* L)
{
	int id = (int)lua_tonumber(L, -2);
	std::string monster = lua_tostring(L, -1);
	lua_pop(L, 2);

	Npc* mynpc = getNpc(L);
	Creature* creature = mynpc->game->getCreatureByID(id);
	Player* player = creature? dynamic_cast<Player*>(creature) : NULL;

	if (player)       
		player->task_monster = monster;

	return 0;
}

int NpcScript::luaSetPlayerTaskMax(lua_State* L)
{
	int id = (int)lua_tonumber(L, -2);
	int max = (int)lua_tonumber(L, -1);
	lua_pop(L, 2);

	Npc* mynpc = getNpc(L);
	Creature* creature = mynpc->game->getCreatureByID(id);
	Player* player = creature? dynamic_cast<Player*>(creature) : NULL;

	if (player)       
		player->task_max = max;

	return 0;
}

int NpcScript::luaSetPlayerTaskCount(lua_State* L)
{
	int id = (int)lua_tonumber(L, -2);
	int count = (int)lua_tonumber(L, -1);
	lua_pop(L, 2);

	Npc* mynpc = getNpc(L);
	Creature* creature = mynpc->game->getCreatureByID(id);
	Player* player = creature? dynamic_cast<Player*>(creature) : NULL;

	if (player)       
		player->task_count = count;

	return 0;
}

int NpcScript::luaAddRewards(lua_State *L)
{
    
    int itemcnt = (int)lua_tonumber(L, -1);
    int itemid = (int)lua_tonumber(L, -2);
	int money = (int)lua_tonumber(L, -3);
	int exp = (int)lua_tonumber(L, -4);

	int cid = (int)lua_tonumber(L, -5);
	lua_pop(L,5);

	Npc* mynpc = getNpc(L);
	Creature* creature = mynpc->game->getCreatureByID(cid);
	Player* player = creature? dynamic_cast<Player*>(creature) : NULL;

	if (player)
	{
		
		
                if (itemcnt > 0) 
                player->TLMaddItem(itemid, itemcnt);
				player->payBack(money);
				player->addExp(exp);
				std::stringstream expp;
				expp << exp;
				player->sendAnimatedText(player->pos, 215, expp.str());
				
			
			
	}

	return 0;
}

int NpcScript::luaGetItemName(lua_State *L)
{
	int id = (int)lua_tonumber(L, -1);
	lua_pop(L, 1);
	lua_pushstring(L, Item::items[id].name.c_str());
	return 1;
}
//tasksys[/HIGHLIGHT]


w **npc.h** pod:

[HIGHLIGHT=cpp]#ifdef YUR_LEARN_SPELLS
	static int luaGetPlayerVocation(lua_State *L);
	static int luaLearnSpell(lua_State* L);
#endif //YUR_LEARN_SPELLS[/HIGHLIGHT]

dodaj:

[HIGHLIGHT=cpp]//tasksys
static int luaGetPlayerTaskMonster(lua_State *L);
static int luaGetPlayerTaskCount(lua_State *L);
static int luaGetPlayerTaskMax(lua_State *L);
static int luaSetPlayerTaskMonster(lua_State* L);
static int luaSetPlayerTaskMax(lua_State* L);
static int luaSetPlayerTaskCount(lua_State* L);
static int luaAddRewards(lua_State *L);
static int luaGetItemName(lua_State *L);
//tasksys[/HIGHLIGHT]

w **player.h** pod:

[HIGHLIGHT=cpp]class Player : public Creature
{
public:[/HIGHLIGHT]

dodaj:

[HIGHLIGHT=cpp]//tasksys
       std::string task_monster;
       int task_count;
       int task_max;
//tasksys[/HIGHLIGHT]


```


ITS TUTORIAL

---

### Post by ofnuts on 2012-02-14
As it says on the box, look for a missing parenthesis earlier in the code. But since you have #ifdef's, this can be a lot earlier in the code if all the #ifdef sections are skipped.

Otherwise, use the good o'l dichotomic approach and pinpoint the culprit line by commenting/uncommenting code.

---

### Post by zolax on 2012-02-14
Can you tell me where is the problem ;/

---

### Post by SeijiSensei on 2012-02-14
> **zolax said:**
> Can you tell me where is the problem ;/

I don't know if anyone here has the persistence to examine all that code.  

I recommend you use an editor with good syntax highlighting and parenthesis matching functions like [gedit]("https://help.ubuntu.com/community/gedit#Syntax_Highlighting").

I use the text-mode editor called **jed**, which defaults to being an **emacs** clone.  Either of these will count parentheses and brackets and make it clear when they are unmatched.

---

### Post by drmrgd on 2012-02-14
Heh!  I actually tried, but between the badly formatted output (please in future post your code using the code tags!) and my faint memories of C++ coding, I couldn't find it.  I think a better programming editor like was proposed might be beneficial to you.

---

### Post by nebukadnezzar on 2012-02-17
The error is that you are using the wrong syntax for the class member function pointers.

The correct syntax would be:

```
lua_register(luaState, "whatever", &ClassName::MemberName);
```

---

