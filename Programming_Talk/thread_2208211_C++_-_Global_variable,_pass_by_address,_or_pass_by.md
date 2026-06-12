---
title: "C++ - Global variable, pass by address, or pass by reference?"
date: 2014-02-27
forum: Programming Talk
---

### Post by slooksterpsv on 2014-02-27
I've found a few bugs in my game as I've been working on it, and something is hammering into my mind that it's my camera class causing the corruption (and it may not be in any shape or form).

Here's what I'm doing:

I have a bunch of classes and a few select ones depend on my camera interface for things such as:
Player
Collision
Enemy
Objects
Weapons
etc.

Now here's what I'm doing:
Each of those classes have a pointer called:
Camera* cam;

Each of those functions when initialized take a pointer to camera via: 
OnInit(Camera* camera)

Each of those classes assign cam the following way:
cam = camera;

Each of those classes are invoked via:

Player* player = new Player();
player->OnInit(&cam);
Weapon* weapon = new Weapon();
weapon->OnInit(&cam);

etc.

Is that the best way? Should I make it a global variable? Could it be something else causing memory corruption? Now when my game first loads, the map is skewed. The last things I did were:
Fixed bug where I was storing strings like so (from a file):
Changed the following from:
char tset[80];
fscanf(map, "%s", &tset);

To:
char tset[80];
fscanf(map, "%s", tset);

I'm about to upload my entire project just to seek help finding these issues, but it's very very undocumented code.

---

### Post by slooksterpsv on 2014-02-27
```

void Map::LoadMap(SDL_Renderer* ren, std::string mapName)
{
	std::cout << mapName << std::endl;
	if(strlen(mapName.c_str()) < 3)
	{
		std::cout << "ERROR LOADING " << mapName;
		return;
	}
	int mX = 0;
	int mY = 0;
	char tset[20];
	std::string tSetStr;
	tiles.clear();
	warp.clear();
	FILE* fMap = fopen(mapName.c_str(), "r");
	if(fMap == NULL)
	{
		std::cout << "ERROR LOADING MAP " << mapName.c_str();
	}
	fscanf(fMap, "%s\n", tset);
**	fscanf(fMap, "%d:%d\n", &mX, &mY); **

```

It keeps crashing on that line in debug mode:
fscanf(fMap, "%d:%d\n", &mX, &mY);

Why though?

EDIT:
Hmm... so I did:
int mX = int(malloc(sizeof(int)));
int mY = int(malloc(sizeof(int)));

and it doesn't crash in debug now...

EDIT2:
Well it does not, an issue with one of my vectors... gah!!! Lol I'm pulling my hair ou.

---

### Post by trent.josephsen on 2014-02-27
Just a guess, but using fscanf in that way is unsafe. Make sure you don't overwrite any buffers like that or by using gets(), carelessly with scanf() or any of the other functions that may walk off the end of a buffer.

```
fscanf(fMap, "**%19s**\n", tset)
```

I won't offer help debugging because (as I mentioned in your other thread) I'm not familiar with C++, but if you can't nail down your mistake, you might want to post your entire program (perhaps using a pastebin-like site) and the misbehaving input files. The program is almost certainly corrupting memory somewhere, and that means the actual bug could be far, far away from the code that crashes.

Also, I'm not sure what you were thinking this does --
```
int mX = int(malloc(sizeof(int)));
```
-- but it probably doesn't do that. (In particular, it doesn't make mX dynamically allocated.)

---

### Post by slooksterpsv on 2014-02-27
I changed the code instead of reading it in directly, using specific lengths and standards to copy it to variables.

---

