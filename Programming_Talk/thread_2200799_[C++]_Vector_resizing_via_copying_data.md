---
title: "[C++] Vector resizing via copying data"
date: 2014-01-21
forum: Programming Talk
---

### Post by slooksterpsv on 2014-01-21
Wow, what a mess I've gotten myself into. Here's the story:

I have a vector that contains about 400+ elements, its for my map for my games, I'm making an editor where I want to resize it, but doing a single coordinate vector is proving difficult. Here's part of my code, and what it's doing (it started to work but if I add too many it overwrites previous elements):

```

void Map::AddColumn()
{
	//OLD: 20
	//NEW: 21
	int temp;
	temp = mapSizeX;
	mapSizeX += 1;
	std::vector<Tiles> tempTiles;
	
	for(int x = 0; x < mapSizeX*mapSizeY; x++)
	{
		Tiles tempTile;
		if(x%mapSizeX == mapSizeX-1)
		{
			tempTile.tileID = 1;
			tempTile.tileType = 1;
		} else
		{
			int tx;
			tx = x - x/temp;
			tempTile.tileID = tiles[tx].tileID;
			tempTile.tileType = tiles[tx].tileType;
			//std::cout << "TX: " << tx << " X: " << x << "TileID: " << tiles[tx].tileID;	
		}
		tempTiles.push_back(tempTile);
	}
	tiles = tempTiles;
	tempTiles.clear();
	std::cout << tiles.size() << mapSizeX*mapSizeY;
}

```

I have a feeling the problem lies with how I'm calculating the math. The trailing end of the vector is what keeps getting screwed up It reads the rest of the area and doesn't overwrite it, but towards the end it takes my last two rows and changes them so example:

[20x25]
11111111111111111111
11111111111111111111
11111111111111111111
11111111111111111111
..imagine more lines
11111111111111111111
21111111111111111111
21111111111111111165

If I add another column it does the same to the last columns:

1111111111111111111111
1111111111111111111111
1111111111111111111111
....
1111111111111111111111
2211111111111111111111
2211111111111111111178

What I'm ultimately doing is I"m trying to keep all the data and generate a new column which may be every 21 elements if I started with 20 (which I have to calculate). Any ideas on what I'm doing wrong.

---

### Post by spjackson on 2014-01-21
Why not make life easy for yourself and represent your 2D vector as... a 2D vector?

std::vector< std::vector<Tiles> >;

By all means, represent it as a single dimension vector if that gives you a much needed performance optimization.

---

### Post by slooksterpsv on 2014-01-21
Figured it out early this morning. My issue was if you take a matrix of:
[1][2][3]
[4][5][6]
[7][8][9]

If you add another column the data would look like
[1][2][3][4]
[5][6][7][8]
[9][10][11][12]

This fixed it:
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

inc += 1; everytime it writes the end of the column;

---

