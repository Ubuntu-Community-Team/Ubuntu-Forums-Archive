---
title: "C++ - checking bool return value gives 255 instead of 0 or 1 ????"
date: 2014-02-26
forum: Programming Talk
---

### Post by slooksterpsv on 2014-02-26
I'm lost on this here's what happened:

I had a variable named checkLoadMap that was boolean in a private member field of a class.
I had a public function CheckLoadMap() that was a return type of boolean in public member field of the same class.

When I'd try to get the bool state, it would return 255, not 0, not 1. Any explanation? I'm trying to fix regressions and memory leaks, but this is just really strange.

---

### Post by The Cog on 2014-02-26
I think there's something wrong with your type handling. It should be returning a bool (true or false). It would not surprise me if internally C++ used a byte value of FF or 0 to represent true or false (may even be specified in the standard) but if you want to treat a bool as an int then you need to look up the conversion rules.

Edit: I did a quick search, and it seems that true should convert to an int value of 1. Odd.

---

### Post by trent.josephsen on 2014-02-26
In C (C99 and later), the conversion from bool to int is well-defined: true is 1, false is 0. Conversion to bool from int (or any other integer type) is also well-defined: zero becomes false, non-zero becomes true. I'd be surprised if C++ permits these assumptions to not hold (but lots of stuff about C++ does surprise me).

What you're likely dealing with is a failure to initialize the variable, in which case you can't assume that it will automatically take a value that makes sense for its declared type. There might be other corner cases in which bool can take other values, and which correct code will avoid. But without seeing the code it's impossible to say, besides which I don't know how much of this applies to C++.

---

### Post by slooksterpsv on 2014-02-26
Oddly  here's the fix

I renamed the bool variable to a name other than checkLoadMap and it works. Where it was named almost the same as CheckLoadMap function it was returning 255. So the code was like this:

```

class Map
{
public:
...
bool CheckMapLoad();
private:
...
bool checkMapLoad;
};
...
bool Map::CheckMapLoad()
{
return checkMapLoad;
}
...

//In the OnInit function

checkMapLoad = false;

//calling from game

std::cout << map->CheckMapLoad() << std::endl; //this would return 255

```

---

### Post by slooksterpsv on 2014-02-26
Just for kicks, here's the entire code of my Map and partial of my Playstate:

```

//Map.h
#ifndef __MAP_H_
#define __MAP_H_

#include <SDL2/SDL.h>
#include <iostream>
#include <vector>
#include "imagehandler.h"
#include "globals.h"
#include "tiles.h"
#include "warp.h"
#include "collision.h"

class Collision;
class Tiles;
class Warp;

class Map {
	public:
		void OnInit();
		void OnDraw(SDL_Renderer* ren, SDL_Rect mapRect);
		void LoadMap(SDL_Renderer* ren, std::string mapName);
		void LoadTileset(SDL_Renderer* ren, std::string tilesetFile);
		
		int GetMapWidth();
		int GetMapHeight();
		
		void ReplaceTile(int tileNum, int tileID);
		void AddColumn();
		void AddRow();
		
		std::string GetTilesetName();
		std::vector<Tiles> GetTiles();
		
		Tiles* GetTile(int X, int Y);
		
		bool drawTileNum;
		void DrawTileNum(bool draw);
		
		void ReplaceTileType(int ID, int tileType);
		
		void CreateNewMap(int map_width, int map_height);
		
		void CheckWarpCollision(SDL_Renderer* ren, Bounds player);
		void LoadNextMap(SDL_Renderer* ren);
		bool CheckLoadMap();
		
		std::string GetWarpTileType();
		
		void OnCleanUp();
	private:
		int mapSizeX, mapSizeY;
		int tilesetWidth, tilesetHeight;
		bool isLoadMap;
		SDL_Texture* tileset;
		SDL_Texture* tilesetNum;
		std::vector<Tiles> tiles;
		std::string tilesetName;
		std::vector<Warp> warp;
		int warpID;
		
};

#endif

```

```

//Map.cpp
#include "map.h"

void Map::OnInit()
{
	tileset = NULL;
	tilesetNum = NULL;
	tiles.clear();
	warp.clear();
	mapSizeX = 0;
	mapSizeY = 0;
	drawTileNum = false;
	std::cout << "Map Init: " << CheckLoadMap() << " " << false;
	isLoadMap = false;
	std::cout << "\nMap Init2: " << CheckLoadMap() << " " << false;
	warpID = -1;
}

void Map::OnDraw(SDL_Renderer* ren, SDL_Rect camRect)
{
	if(tileset == NULL) return;

    int ID = 0;

	bool temp = false;

    for(int y = 0; y < mapSizeY; y++){
        for(int x = 0; x < mapSizeX; x++) {
        	//TileID Type CHANGED**********************************
            if(tiles[ID].tileType == 0) {
                ID++;
                continue;
            }

            int tx = (x * TILE_SIZE);
            int ty = (y * TILE_SIZE);

            int tilesetX = (tiles[ID].tileID % (tilesetWidth)) * TILE_SIZE;
            int tilesetY = (tiles[ID].tileID / (tilesetWidth)) * TILE_SIZE;
            
            if(tx >= camRect.x + WIN_SIZE_X + TILE_SIZE)
            {
            	ID++;
            	continue;
            }
            
            if(tx <= camRect.x - (TILE_SIZE*2))
            {
            	ID++;
            	continue;
            }
            
			if(ty >= camRect.y + WIN_SIZE_Y + TILE_SIZE)
            {
            	ID++;
            	continue;
            }
            
            if(ty <= camRect.y - (TILE_SIZE*2))
            {
            	ID++;
            	continue;
            }

            SDL_Rect DestR;
            DestR.x = tx - camRect.x;
            DestR.y = ty - camRect.y;
            //DestR.x = tx;
            //DestR.y = ty;
            DestR.w = TILE_SIZE;
            DestR.h = TILE_SIZE;

            SDL_Rect src;
            src.x = tilesetX;
            src.y = tilesetY;
            src.w = 32;
            src.h = 32;

            SDL_RenderCopy(ren, tileset, &src, &DestR);
            
            if(drawTileNum)
            {
            	SDL_Rect srcC;
            	srcC.x = TILE_SIZE*(tiles[ID].tileType - 1);
            	srcC.y = 0;
            	srcC.w = 32;
            	srcC.h = 32;
            	SDL_RenderCopy(ren, tilesetNum, &srcC, &DestR);
            }
            
            ID++;
        }
    }
}

void Map::LoadMap(SDL_Renderer* ren, std::string mapName)
{
	std::cout << mapName << std::endl;
	if(strlen(mapName.c_str()) < 3)
	{
		std::cout << "ERROR LOADING " << mapName;
		return;
	}
	int mX, mY;
	char tset[80];
	std::string tSetStr;
	tiles.clear();
	warp.clear();
	FILE* fMap = fopen(mapName.c_str(), "r");
	if(fMap == NULL)
	{
		std::cout << "ERROR LOADING MAP " << mapName.c_str();
	}
	fscanf(fMap, "%s\n", tset);
	fscanf(fMap, "%d:%d\n", &mX, &mY);
	
	mapSizeX = mX;
	mapSizeY = mY;
	
	for(int y = 0; y < mY; y++) {
        for(int x = 0; x < mX; x++) {
            Tiles tempTile;
            fscanf(fMap, "%d:%d ", &tempTile.tileID, &tempTile.tileType);
            //cout << tempTile.tileID << ":" << tempTile.tileType << " ";

            tiles.push_back(tempTile);        
        }
        fscanf(fMap, "\n");
    }
    
    //TEST CODE FOR LOADING WARP POINTS
    char wp[2] = "";
    int lx = 0, ly = 0;
    char fn[255] = "";
	while(fscanf(fMap, "TDAT:%2s:%d:%d:%s\n", wp, &lx, &ly, fn) > 0) {
	    Warp tempWarp;
	    tempWarp.tile_type = wp;
	    tempWarp.tile_x = lx;
	    tempWarp.tile_y = ly;
	    tempWarp.map_name = fn;
	    warp.push_back(tempWarp);
	    std::cout << fn;
    }
    
    std::cout << "Warp Points: " << warp.size();
    
    fclose(fMap);

	tilesetName = tset;
	LoadTileset(ren, tilesetName);
	std::cout << "\nLoaded Tileset" << std::endl;
}

void Map::LoadTileset(SDL_Renderer* ren, std::string tilesetFile)
{
	SDL_Surface *sTile;
	sTile = ImageHandler::LoadImage(tilesetFile);
	tileset = SDL_CreateTextureFromSurface(ren, sTile);
	SDL_FreeSurface(sTile);
	
	SDL_QueryTexture(tileset, NULL, NULL, &tilesetWidth, &tilesetHeight);
	tilesetWidth /= 32;
	tilesetHeight /= 32;
	
	if(tilesetNum == NULL)
	{
		SDL_Surface *nTile;
		nTile = ImageHandler::LoadImageTransparency("tilesetnum.png", 255, 0, 255);
		tilesetNum = SDL_CreateTextureFromSurface(ren, nTile);
		SDL_FreeSurface(nTile);
		if(tilesetNum == NULL)
			std::cout << "ERROR";
	}
}

void Map::OnCleanUp()
{
	tiles.clear();
	warp.clear();
	SDL_DestroyTexture(tileset);
}

int Map::GetMapHeight()
{
	return mapSizeY * TILE_SIZE;
}

int Map::GetMapWidth()
{
	return mapSizeX * TILE_SIZE;
}

void Map::CheckWarpCollision(SDL_Renderer* ren, Bounds player)
{
	if(warp.size() > 0){
	
		for(int check = 0; check < warp.size(); check++)
		{
			//std::cout << strcmp("eb", warp[check].tile_type.c_str());
			int max_t, max_l;

			Bounds temp;
			
			if(strcmp("wp", warp[check].tile_type.c_str()) == 0)
			{
				temp.top = warp[check].tile_y * 32;
				temp.left = warp[check].tile_x * 32;
				temp.bottom = temp.top + 32;
				temp.right = temp.left + 32;
			}
			
			if(strcmp("el", warp[check].tile_type.c_str()) == 0)
			{
				temp.top = 0;
				temp.left = 0;
				temp.bottom = 480;
				temp.right = 16;
			}
			
			if(strcmp("er", warp[check].tile_type.c_str()) == 0)
			{
				temp.top = 0;
				temp.left = 624;
				temp.bottom = 480;
				temp.right = 640;
			}
			
			if(strcmp("et", warp[check].tile_type.c_str()) == 0)
			{
				temp.top = 0;
				temp.left = 0;
				temp.bottom = 16;
				temp.right = 640;
			}
			
			if(strcmp("eb", warp[check].tile_type.c_str()) == 0)
			{
				temp.top = 464;
				temp.left = 0;
				temp.bottom = 480;
				temp.right = 640;
				//std::cout << player.bottom << " " << temp.top << " " << std::endl;
				
			}
			

			if(Collision::BoundsCollision(player, temp))
			{
				isLoadMap = true;
				warpID = check;
			}
		}
	}
}

bool Map::CheckLoadMap()
{
	return isLoadMap;
}

void Map::LoadNextMap(SDL_Renderer *ren)
{
	OnCleanUp();
	
	if(warpID < 0)
	{
		std::cout << "Critical Error occured loading next map!!! ID CODE: " << warpID;
		return;
	}
	
	std::cout << "Called load map to load: " << warp[warpID].map_name;	
	LoadMap(ren, warp[warpID].map_name);

	isLoadMap = false;
	warpID = -1;

}

std::string Map::GetWarpTileType()
{
	if(warpID >= 0)
		return warp[warpID].tile_type;
	std::cout << "ERROR!!! " << warpID << "=warpID";
	return 0;
}

void Map::ReplaceTile(int tileNum, int tileID)
{
	tiles[tileNum].tileID = tileID;
}

void Map::ReplaceTileType(int ID, int tileType)
{
	tiles[ID].tileType = tileType;
}

std::vector<Tiles> Map::GetTiles(){
	return tiles;
}

void Map::AddColumn()
{
	//OLD: 20
	//NEW: 21
	int temp;
	int inc = 0;
	temp = mapSizeX;
	mapSizeX += 1;
	std::vector<Tiles> tempTiles;
	
	for(int x = 0; x < mapSizeX*mapSizeY; x++)
	{
		Tiles tempTile;
		if(x % mapSizeX == temp)
		{
			std::cout << x << std::endl;
			tempTile.tileID = 1;
			tempTile.tileType = 1;
			inc += 1;
		} else
		{
			int tx;
			tx = x - (x%temp/temp) - inc;
			tempTile.tileID = tiles[tx].tileID;
			tempTile.tileType = tiles[tx].tileType;	
		}
		tempTiles.push_back(tempTile);
	}
	tiles = tempTiles;
	tempTiles.clear();
	std::cout << tiles.size() << mapSizeX*mapSizeY;
}

std::string Map::GetTilesetName()
{
	return tilesetName;
}

Tiles* Map::GetTile(int X, int Y)
{
	int ID = 0;
	ID = X / TILE_SIZE;
	ID = ID + ((mapSizeX) * (Y / TILE_SIZE));
	if(ID < 0 || ID >= tiles.size()) {
		return NULL;
	}
	return &tiles[ID];
}

void Map::DrawTileNum(bool draw)
{
	drawTileNum = draw;
}

void Map::CreateNewMap(int map_width, int map_height)
{
	tiles.clear();
	for(int x = 0; x < map_width; x++)
	{
		for(int y = 0; y < map_height; y++)
		{
			Tiles tempTile;
			tempTile.tileID = 240;
			tempTile.tileType = 1;
			tiles.push_back(tempTile);
		}
	}
	mapSizeX = map_width;
	mapSizeY = map_height;
}

```

```

//Playstate.cpp
#include "playstate.h"

PlayState PlayState::PlayGameState;

void PlayState::OnInit(Game* game)
{
	//Load everything from the map, player, enemies, objects
	//Setup camera, hud, etc.
	map = new Map();
	map->OnInit();
	map->LoadMap(game->ren, "map.f1");
	player = new Player(&cam);
	player->SetLife(25);
	cam.SetWidthAndHeight(map->GetMapWidth(), map->GetMapHeight());
	player->OnInit(game->ren);
	objectList = new Object(&cam);
	objectList->LoadObjectList(game->ren, "obj.f1");
	enemy = new Enemy(&cam);
	enemy->OnInit(game->ren);
	hud.OnInit(game->ren);
	weapon = new Weapon(&cam);
	weapon->OnInit(game->ren);
	std::cout << "map: " << map->CheckLoadMap();
}

void PlayState::OnCleanUp()
{
	//Cleanup objects and free memory
	map->OnCleanUp();
	player->OnCleanUp();
	enemy->OnCleanUp();
	hud.OnCleanUp();
}
		
void PlayState::OnDraw(Game* game)
{
	//std::cout << "Going to clear my screen" << std::endl;
	//Clear Screen
	SDL_RenderClear(game->ren);
	
	//Draw elements
	map->OnDraw(game->ren, cam.GetCameraRect());
	
	objectList->OnDraw(game->ren);
	
	player->OnDraw(game->ren);
	
	if(weapon->IsActive())
	{
		weapon->OnDraw(game->ren);
		weapon->OnUpdate(game->ren);
		if(objectList->CheckCollision(weapon->GetBounds()))
		{
			weapon->SetActive(false);
			//Get Collision Object
			//remove collision object
			objectList->RemoveAt(objectList->GetCollisionObject(weapon->GetBounds()));
		}
		if(enemy->CheckCollision(weapon->GetBounds()))
		{
			enemy->SetLife(enemy->GetLife()-1);
			weapon->SetActive(false);
		}
	}
	
	enemy->OnDraw(game->ren);
	
	hud.OnDraw(game->ren, player);
	
	SDL_RenderPresent(game->ren);
}

void PlayState::OnUpdate(Game* game)
{
	if(map->CheckLoadMap())
	{
		std::string temp;
		temp = map->GetWarpTileType();
		map->LoadNextMap(game->ren);
		cam.SetWidthAndHeight(map->GetMapWidth(), map->GetMapHeight());
		player->ChangeMap(temp, map->GetMapWidth(), map->GetMapHeight());
		weapon->SetActive(false);
	}
	map->CheckWarpCollision(game->ren, player->GetBounds());
	enemy->CheckCollision(player->GetBounds());
	enemy->Move();
	HandleInput(game);
	
}

void PlayState::OnEvent(Game* game)
{
	//Handle keyboard Events
	SDL_Event event;
	if (SDL_PollEvent(&event)) {
		switch (event.type) {
			case SDL_QUIT:
				game->PopState();
				break;

			case SDL_KEYDOWN:
				switch (event.key.keysym.sym) {
					case SDLK_ESCAPE:
						game->PopState();
						break;
					case SDLK_m:
						if(!weapon->IsActive())
						{
							weapon->SetStartPosition(player->GetPositionX() + cam.GetX(), player->GetPositionY() + cam.GetY(), player->GetDirection());
							weapon->SetActive();
						}
						break;
					case SDLK_RETURN:
						objectList->RemoveAt(3);
						break;
					default:
						break;
				}
				break;
			case SDL_KEYUP:
				player->SetAnimate(false);
				break;
		}
	}
}

void PlayState::HandleInput(Game* game)
{
	const Uint8* keystate = SDL_GetKeyboardState(NULL);

    if(keystate[SDL_SCANCODE_LEFT])
    {
    	if(objectList->CheckCollision(player->GetBounds(1)))
    	{
    		player->SetPositionX(player->GetPositionX()+4);
    	}
    	if(enemy->CheckCollision(player->GetBounds()))
    	{
    		if(!player->GetFlicker())
			{
    			player->SetPositionX(player->GetPositionX()+32);
    			player->SetLife(player->GetLife()-1);
    			player->SetFlicker(true);
    			adjustment = 1;
    		}else {
    			//player->SetPositionX(player->GetPositionX()+4);
    		}
    		
    	}
		if(!player->CheckCollision(map->GetTile(player->GetRelX()+8, player->GetRelY()+48)->tileType)){
			if(cam.NearBounds(P_MOVE_LEFT, player->GetPositionX(), player->GetPositionY()))
			{
				player->SetSpeed(4);
			}else
			{
				player->SetSpeed(0);
	    		cam.SetCameraLocation(cam.GetX()-4, cam.GetY());
			}
		} else {
			player->SetSpeed(0);
		}
		player->Move(P_MOVE_LEFT);
		
		/*if(player->GetPositionX() <= -4)
		{
			std::cout << "\n\nMAP DIMENSIONS: " << map->GetMapWidth() <<  "x" << map->GetMapHeight() << std::endl;
			map->LoadMap(game->ren, "test.f1");
			std::cout << "\n\nMAP DIMENSIONS: " << map->GetMapWidth() <<  "x" << map->GetMapHeight() << std::endl;
			std::cout << "Player X: " << player->GetPositionX() << " Map Width: " << map->GetMapWidth() << std::endl;
			cam.SetWidthAndHeight(map->GetMapWidth(), map->GetMapHeight());
			cam.SetCameraLocation(cam.GetX()+map->GetMapWidth(), cam.GetY());
			player->SetPositionX(584);
		}*/
    }
    if(keystate[SDL_SCANCODE_RIGHT])
    {
    	if(objectList->CheckCollision(player->GetBounds(3)))
    	{
    		player->SetPositionX(player->GetPositionX()-4);
    	}
    	if(enemy->CheckCollision(player->GetBounds()))
    	{
    		if(!player->GetFlicker())
			{
    			player->SetPositionX(player->GetPositionX()-32);
    			player->SetLife(player->GetLife()-1);
    			player->SetFlicker(true);
    			adjustment = 1;
    		}else {
    			//player->SetPositionX(player->GetPositionX()-4);
    		}
    		
    	}
		if(!player->CheckCollision(map->GetTile(player->GetRelX()+40, player->GetRelY()+48)->tileType)){
        	if(cam.NearBounds(P_MOVE_RIGHT, player->GetPositionX(), player->GetPositionY()))
			{
				player->SetSpeed(4);
			}    
   		    else{
        		player->SetSpeed(0);
           		cam.SetCameraLocation(cam.GetX()+4, cam.GetY());
        	}
    	}else{
    		player->SetSpeed(0);
    	}
    	player->Move(P_MOVE_RIGHT);
    	/*if(player->GetPositionX() >= map->GetMapWidth()-cam.GetX()-48)
		{
			map->LoadMap(game->ren, "map.f1");
			objectList->OnCleanUp();
			objectList->LoadObjectList(game->ren, "obj.f1");
			cam.SetWidthAndHeight(map->GetMapWidth(), map->GetMapHeight());
			cam.SetCameraLocation(cam.GetX()-map->GetMapWidth(), cam.GetY());
			player->SetPositionX(4);
		}*/
    }
    if(keystate[SDL_SCANCODE_UP])
    {
    	if(objectList->CheckCollision(player->GetBounds(0)))
    	{
    		player->SetPositionY(player->GetPositionY()+4);
    	}
    	if(enemy->CheckCollision(player->GetBounds()))
    	{
    		if(!player->GetFlicker())
			{
    			player->SetPositionY(player->GetPositionY()+32);
    			player->SetLife(player->GetLife()-1);
    			player->SetFlicker(true);
    			adjustment = 1;
    		}else {
    			//player->SetPositionY(player->GetPositionY()+4);
    		}
    		
    	}
    	if(!player->CheckCollision(map->GetTile(player->GetRelX()+24, player->GetRelY()+44)->tileType)){
    		if(cam.NearBounds(P_MOVE_UP, player->GetPositionX(), player->GetPositionY()))
    		{
    			player->SetSpeed(4);
    		}else
    		{
    			player->SetSpeed(0);
    			cam.SetCameraLocation(cam.GetX(), cam.GetY()-4);
    		}
	    }else {
	    	player->SetSpeed(0);
	    }
    	player->Move(P_MOVE_UP);
    }
    if(keystate[SDL_SCANCODE_DOWN])
    {
    	if(objectList->CheckCollision(player->GetBounds(2)))
    	{
    		player->SetPositionY(player->GetPositionY()-4);
    	}
    	if(enemy->CheckCollision(player->GetBounds())){
	    	if(!player->GetFlicker())
			{
    			player->SetPositionY(player->GetPositionY()-32);
    			player->SetLife(player->GetLife()-1);
	    		player->SetFlicker(true);
    			adjustment = 1;
    		}else {
    			//player->SetPositionY(player->GetPositionY()-4);
    		}
    	}
    	if(!player->CheckCollision(map->GetTile(player->GetRelX()+24, player->GetRelY()+56)->tileType)){
	    	if(cam.NearBounds(P_MOVE_DOWN, player->GetPositionX(), player->GetPositionY()))
    		{
    			player->SetSpeed(4);
   	 		}else{
    			player->SetSpeed(0);
				cam.SetCameraLocation(cam.GetX(), cam.GetY()+4);
    		}
   		}else {
   			player->SetSpeed(0);
   		}
    	player->Move(P_MOVE_DOWN);
    }
    ticks += adjustment;
    if(ticks >= 75)
    {
    	ticks = 0;
    	adjustment = 0;
    	player->SetFlicker(false);
    }
}

```

```

//Playstate.h
#ifndef __PLAYSTATE__H_
#define __PLAYSTATE__H_

#include <SDL2/SDL.h>
#include <SDL2/SDL_image.h>
#include "globals.h"
#include "imagehandler.h"
#include "gamestates.h"
#include "hud.h"
#include "map.h"
#include "camera.h"
#include "object.h"
#include "enemy.h"
#include "weapon.h"

class Hud;
class GameStates;
class Map;
class Camera;
class Object;
class Enemy;
class Weapon;

class PlayState:public GameStates {
	public:
		void OnInit(Game* game);
		void OnCleanUp();
		
		void OnDraw(Game* game);
		void OnUpdate(Game* game);
		void OnEvent(Game* game);
		
		void HandleInput(Game* game);
		
		static PlayState* Instance() {
			return &PlayGameState;
		}
		
	private:
		static PlayState PlayGameState;
		Hud hud;
		Player* player;
		Map* map;
		Object* tree;
		Object* objectList;
		Camera cam;
		Enemy* enemy;
		int ticks, adjustment;
		Weapon* weapon;
};

#endif

```

---

### Post by slooksterpsv on 2014-02-27
Here's what the issue was:

1. The name was similar to a function - not sure if this is an error with gcc 4.7.1 or if it's with how Dev-C++ allows compiling to happen.
2. The main cause was probably this: there were some errors in the program which were overwriting the buffers and other memory areas within the program. This has been since resolved and a new version has been created. The errors came from reading files like so:

fscanf(file, "%s", &tset);

Instead a mandatory length for what is being read in the file will follow this structure:

fscanf(file, "%10s", tset);

And for any other string obtaining function:

fscanf(file, "%d:%d:%10s", &lx, &ly, map_name);

This fixed numerous issues that were replicating in the program such as - maps not showing up correctly, random crashes during program execution, crashes when changing maps in the game, etc.

Thanks!

---

### Post by dwhitney67 on 2014-02-28
fscanf()?!!!  And I thought this was a C++ thread.  Now where can I find that dusty ol' C programming book to help this chap?

---

