---
title: "SDL + (2 by 2) TileMap = SLOW?"
date: 2010-02-28
forum: Programming Talk
---

### Post by EnigmaticCoder on 2010-02-28
I'm making a game where the player can dig tunnels through dirt. I've got the multi-layered level drawn without slowdown, but now that I've added a 2x2 tile tunnel map on top of the rest of the level, the game runs very slowly. A 16 X 16 tile tunnel map makes the game run at a passable speed, but then the tunnels aren't precise enough! (Note: I'm only drawing what's on screen)

Is this the fault of SDL?
Could switching to OpenGL fix my problem?
What about SDL + OpenGL?
Is SDL antiquated?

I'll post code if necessary.

---

### Post by mike_g on 2010-03-01
> Is this the fault of SDL?
Probably not.
> Is SDL antiquated?
Its not hardware accelerated, but it should be fine for most 2D games, unless it has really flashy graphics. After all, games were written with SDL for hardware that was around in 1997.

Code would be helpful. Otherwise people would just be guessing, and I'd guess that if you are using Python then it would slow down loads as its very slow when dealing with big loops. 

One way to optimise it would be to keep a masked buffer storing image data for the tunnel shown on-screen. Then you would only be drawing one image per loop instead of hundreds, the only thing you would then draw to this image would be the change of state in the tunnel from last time it was drawn.

Another option (in C) would be to write your own inlined drawing function for the tunnel. This would remove function overhead and allow you to draw to you image buffer more efficiently, EG: only incrementing the pointer of the pixel you are drawing to instead of jumping around all over the image all the time. But that would be more work.

---

### Post by EnigmaticCoder on 2010-03-01
I added code to skip transparent pixels, and that speeds it up quite a bit until a lot of tunnels are drawn.

> Code would be helpful
I'm slightly embarrassed to show my least modular function, but here it goes:

```
void Renderer::drawScreen(ScreenState &screenState, const Level &level, const Map &map, const Map &tunnelMap,
        const std::vector<Sprite> &sprites, const Player &player,
        const std::map<std::string, Image> &images, const Cursor &cursor,
        double cameraX, double cameraY)
{
    //Ensure proper initial conditions
    if (cameraX < 0)
        cameraX = 0;
    if (cameraY < 0)
        cameraY = 0;

    int screenWidth;
    int screenHeight;
    screenState.getDimensions(screenWidth, screenHeight);

    int levelWidth;
    int levelHeight;
    level.getDimensions(levelWidth, levelHeight);

    int levelRow;
    int levelCol;
    int endLevelRow;
    int endLevelCol;

    int tunnelLevelRow;
    int tunnelLevelCol;
    int tunnelEndLevelRow;
    int tunnelEndLevelCol;

    double modifiedX = -map.tileSize - fmod(cameraX, map.tileSize); //The actual screen coordinates of the first tile, not the camera coordinates
    double modifiedY = -map.tileSize - fmod(cameraY, map.tileSize);

    double modifiedTunnelX = -tunnelMap.tileSize - fmod(cameraX, tunnelMap.tileSize);
    double modifiedTunnelY = -tunnelMap.tileSize - fmod(cameraY, tunnelMap.tileSize);

    getStartIndexes(map, cameraX, cameraY, levelRow, levelCol);
    getEndIndexes(map, screenState, levelRow, levelCol, endLevelRow, endLevelCol);

    getStartIndexes(tunnelMap, cameraX, cameraY, tunnelLevelRow, tunnelLevelCol);
    getEndIndexes(tunnelMap, screenState, tunnelLevelRow, tunnelLevelCol, tunnelEndLevelRow, tunnelEndLevelCol);

    //Tiles
    //Start at the current row, which is an index in the map array
    // contiue with the number of tiles that fit within the screen
    // i.e. row = 0, i < (row * (screenHeight = 640 / tileSize = 16))
    // 40 tiles total will be displayed
    for (int layer = 0; layer < map.indexOfLastBackgroundLayer; ++layer)
    {
        for (int i = levelRow; i < endLevelRow; ++i)
        {
            for (int j = levelCol; j < endLevelCol; ++j)
            {
                drawLayer(map, layer, i, j, levelRow, levelCol, modifiedX, modifiedY);
            }
        }
    }

    //TunnelTiles
    for (int layer = 0; layer < tunnelMap.indexOfLastBackgroundLayer; ++layer)
    {
        for (int i = tunnelLevelRow; i < tunnelEndLevelRow; ++i)
        {
            for (int j = tunnelLevelCol; j < tunnelEndLevelCol; ++j)
            {
                drawLayer(tunnelMap, layer, i, j, tunnelLevelRow, tunnelLevelCol, modifiedTunnelX, modifiedTunnelY);
            }
        }
    }

    for (int layer = map.indexOfLastBackgroundLayer; layer < map.layers; ++layer)
    {
        for (int i = levelRow; i < endLevelRow; ++i)
        {
            for (int j = levelCol; j < endLevelCol; ++j)
            {
                drawLayer(map, layer, i, j, levelRow, levelCol, modifiedX, modifiedY);
            }
        }
    }

    //Draw all the sprites in the spriteList
    for (unsigned int i = 0; i < sprites.size(); ++i)
    {
        if (!spriteOnScreen(sprites[i], 0, 0, levelWidth, levelHeight))
            continue;

        double drawPositionX = 0;
        double drawPositionY = 0;

        getSpriteOnScreenCoordinates(sprites[i], cameraX, cameraY,
                drawPositionX, drawPositionY);
        drawSprite(sprites[i], drawPositionX, drawPositionY);
    }

    //For the player too
    if (spriteOnScreen((Sprite) player, 0, 0, levelWidth, levelHeight))
    {
        double drawPositionX = 0;
        double drawPositionY = 0;

        getSpriteOnScreenCoordinates((Sprite) player, cameraX, cameraY,
                drawPositionX, drawPositionY);
        drawSprite((Sprite) player, drawPositionX, drawPositionY);
    }    

    double cursorX = 0;
    double cursorY = 0;
    cursor.getCoordinates(cursorX, cursorY);

    int currentZ = -1;

    while (getNextLowest(currentZ, images) == true)
    {
        for (std::map<std::string, Sheet>::iterator it = this->images.begin();
                it != this->images.end(); ++it)
        {
            if (images.find(it->first)->second.getZ() == currentZ && images.find(it->first)->second.getShowing())
                drawImage(it->first, images.find(it->first)->second.getX(), images.find(it->first)->second.getY());
        }
    }

    drawCursor(cursor, cursorX, cursorY);
    drawScreen();
}
```

```
void Renderer::getStartIndexes(const Map &map, double x, double y, int &rowIndex, int &colIndex)
{
    rowIndex = ((int) y) / map.tileSize - NUM_BORDER_TILES;
    colIndex = ((int) x) / map.tileSize - NUM_BORDER_TILES;
}
```

```
void Renderer::getEndIndexes(const Map &map, ScreenState screenState, int levelRow, int levelCol, int &endLevelRow, int &endLevelCol)
{
    int screenWidth;
    int screenHeight;
    screenState.getDimensions(screenWidth, screenHeight);

    endLevelRow = levelRow + screenHeight / map.tileSize + NUM_BORDER_TILES * 2; //*2 because we must make up for the left border and ADD the right border too
    endLevelCol = levelCol + screenWidth / map.tileSize + NUM_BORDER_TILES * 2;
}
```

```
void Renderer::drawLayer(const Map &map, int layer, int row, int col, int levelRow,
        int levelCol, double modifiedX, double modifiedY)
{
    double curY = modifiedY + (row - levelRow) * map.tileSize;
    double curX = modifiedX + (col - levelCol) * map.tileSize;

    Tile curTile = {0, 0, map.filePath};

    //Returns true if tile is not XXX
    // XXX means that the entire tile is transparent/non-existent and should not be drawn
    if (!validateBoundaries(map, row, col))
        return;

    getSheetCoordinates(map, map.mapData[layer][row][col], curTile.row, curTile.col);

    if (curTile.row == TILE_TRANSPARENT && curTile.col == TILE_TRANSPARENT)
        return;
    
    drawTile(curTile, curX, curY);
}

```

```
bool Renderer::spriteOnScreen(Sprite sprite, double topLeftX, double topLeftY, int screenWidth,
        int screenHeight)
{
    double spriteX = 0;
    double spriteY = 0;

    sprite.getCoordinates(spriteX, spriteY);

    if (spriteX < topLeftX || spriteX > topLeftX + screenWidth ||
            spriteY < topLeftY || spriteY > topLeftY + screenHeight)
        return false;

    return true;
}
```

```
void Renderer::getSpriteOnScreenCoordinates(Sprite sprite, double topLeftX, double topLeftY,
        double &drawPositionX, double &drawPositionY)
{
    double spriteX = 0;
    double spriteY = 0;

    sprite.getCoordinates(spriteX, spriteY);

    drawPositionX = spriteX - topLeftX;
    drawPositionY = spriteY - topLeftY;
}
```

```
bool Renderer::getNextLowest(int &currentZ, const std::map<std::string, Image> &images)
{
    const bool FOUND_NEXT = true;
    int lastZ = currentZ;
    int nextZ = INT_MAX;

    for (std::map<std::string, Sheet>::iterator it = this->images.begin();
            it != this->images.end(); ++it)
    {
        if (images.find(it->first)->second.getZ() > lastZ &&
                images.find(it->first)->second.getZ() < nextZ)
        {
            currentZ = images.find(it->first)->second.getZ();
            nextZ = currentZ;
        }
    }

    if (lastZ != currentZ)
        return FOUND_NEXT;

    return !FOUND_NEXT;
}
```

```
void Renderer::getSheetCoordinates(const Map &map, int tileNum, int &rowIndex, int &colIndex)
{
    rowIndex = tileNum / map.numOfTilesHigh;
    colIndex = tileNum % map.numOfTilesWide;
}
```

```
void Renderer::drawScreen()
{
    if (SDL_Flip(screen) == -1)
        exit(EXIT_FAILURE);
}
```

```
bool Renderer::validateBoundaries(const Map &map, int row, int col)
{
    const int LBOUND_ROW = 0;
    const int LBOUND_COL = 0;
    const int UBOUND_ROW = map.mapDataHeight - ARRAY_OFFSET;
    const int UBOUND_COL = map.mapDataWidth - ARRAY_OFFSET;

    if (row < LBOUND_ROW || row > UBOUND_ROW || col < LBOUND_COL || col > UBOUND_COL)
        return false;

    return true;
}
```

---

### Post by cb951303 on 2010-03-01
I didn't check the code but, do you draw every layer and sprite every frame? if so, you should probably draw everything once and then update the changing parts. it should really speed up things.

---

### Post by EnigmaticCoder on 2010-03-01
> **cb951303 said:**
> I didn't check the code but, do you draw every layer and sprite every frame? if so, you should probably draw everything once and then update the changing parts. it should really speed up things.

I've started to implement your solution, but I've got this nagging question: If there are many sprites on screen, won't it be slow again? I could avoid this by not having many sprites on screen, but I'm worried about being limited in that way.

If worse comes to worse, I could implement your solution *and* use OpenGL. We'll see.

---

### Post by EnigmaticCoder on 2010-03-01
Now that I've started to implemented it, drawing only what's changed doesn't seem like it'd work because most of the screen changes when the game scrolls. Hmmm...

---

### Post by cb951303 on 2010-03-01
> **EnigmaticCoder said:**
> I've started to implement your solution, but I've got this nagging question: If there are many sprites on screen, won't it be slow again? I could avoid this by not having many sprites on screen, but I'm worried about being limited in that way.

If worse comes to worse, I could implement your solution *and* use OpenGL. We'll see.

yes but I've seen pure SDL applications with more than hundred a sprites on the screen moving without any hint of slowing down.

keep in mind that, when you need to do collision detection on too many sprites it's very inefficient to check them all for collisions. if it ever comes to it, read about scene management. more specifically "grids" or "quadtrees".

also, SDL is more than enough for a wide variety of 2D games. you shouldn't resort to using OpenGL every time something is slow :) check your code first, do some basic profiling (it's very easy with gprof) to see which part of the code takes the most time and find a way to optimize it or even write it from scratch. you will see that most of the time there is a better way.

note that hardware acceleration is needed if you need real-time matrix transformations such as rotating/zooming a sprite. also I' must add I use OpenGL for 2D too but mostly for real-time transformations, shaders and some cool lighting.

cheers

---

