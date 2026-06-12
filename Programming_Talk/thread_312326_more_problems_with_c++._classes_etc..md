---
title: "more problems with c++. classes etc."
date: 2006-12-04
forum: Programming Talk
---

### Post by Choad on 2006-12-04
heres the relevant bits of code

```

// global variable
CSprite mySprite();

// classes
class CBlock: public CObject
{
	public:
	  // de/constructor
	CBlock();
	~CBlock();
};

class CSprite
{
	public:
	  // de/constructor
	CSprite();
	~CSprite();
	
	SDL_Surface * block;
};

//class functions 
CBlock::CBlock()
{
	Init();
	**//sprite = mySprite.block;**
}

CBlock::~CBlock()
{
	DeInit();
}

CSprite::CSprite()
{
	block = LoadImage("block.png");
}

CSprite::~CSprite()
{
	SDL_FreeSurface(block);
}

```

if i uncomment that bold code it gives me this error

```

richard@richard-laptop:~/Desktop$ g++ `sdl-config --cflags --libs` -o mygame newproj.cpp -lSDL -lSDL_image
newproj.cpp: In constructor ‘CBlock::CBlock()’:
newproj.cpp:212: error: request for member ‘block’ in ‘mySprite’, which is of non-class type ‘CSprite ()()’

```

any ideas?

---

### Post by Verminox on 2006-12-04
Errrm... maybe because the variable "sprite" is not declared? It has to be of type SDL_Surface*.

---

### Post by Angry on 2006-12-04
offhand, I'm thinking you need to make **CSprite mySprite()** static.

---

### Post by po0f on 2006-12-04
Choad,

To solve your error, just take the parentheses off the mySprite delclaration line.  mySprite will be constructed for you automatically, and will go out of scope and be destroyed at the end of the block.
```
[FONT="Courier New"]CSprite mySprite;[/FONT]
```

If the class CBlock is dependent on another class (CSprite) for some of its information, you should consider making it a member.  This way (if you want), you can better control access to it.
```
[FONT="Courier New"]class CSprite {
public:
  CSprite(const char *file) {
    block = LoadImage(file);
  }
  ~CSprite() {
    SDL_FreeSurface(block);
  }

  SDL_Surface *block;
};

class CBlock : public CObject {
public:
  CBlock() {
    Init();
    sprite = new CSprite("block.png");
  }
  ~CBlock() {
    delete sprite;
    DeInit();
  }
  SDL_Surface *getBlock() const { return sprite->block; }

private:
  CSprite *sprite;
};

int main() {
  CBlock *myBlock = new CBlock();
  myBlock->getBlock();  // get to block

  delete myBlock;
  return 0;
}[/FONT]
```

(Oh yes, I am bored.)

If someone wants to explain it better than me, go ahead.  I'm a bit tipsy right now and can't think so straight.

Choad, if you can't wait for someone more competent, post back and I'll fumble my way through an explanation.  :)

---

### Post by thumper on 2006-12-04
You are attempting to construct a CSprite object called mySprite before the class definition.  You can't do that.  Move it to after the class definition.

---

### Post by Choad on 2006-12-05
i have already swapped the declarations arround


if i remove the parenthises on mySprite declaration i get this error

```
newproj.cpp:55: error: aggregate &#8216;CSprite mySprite&#8217; has incomplete type and cannot be defined

```

---

### Post by duff on 2006-12-05
> **Choad said:**
> i have already swapped the declarations arround


if i remove the parenthises on mySprite declaration i get this error

```
newproj.cpp:55: error: aggregate ‘CSprite mySprite’ has incomplete type and cannot be defined

```

Can you repost what you have now, so we can see exactly what you did.  Also, could you post the result of ```
# nl newproj.cpp
``` before you prune the nonessential code.

---

### Post by Choad on 2006-12-05
```

     1    // includes
     2    ///////////
     3    
     4  #include <stdio.h>
     5  #include <stdlib.h>
     6  #include "SDL/SDL.h"
     7  #include "SDL/SDL_image.h"
     8  #include <string>
     9  #include <fstream>
    10  #include <iostream>
       
    11    // Prototypes
    12    /////////////
       
    13  bool Init();
    14  void DrawScene();
    15  void HandleInput();
    16  SDL_Surface * LoadImage( std::string filename );
       
    17    // Forward Declarations
    18    ///////////////////////
    19    
    20  struct node;
    21  class CObject;
    22  class CBlock;
**    23  class CSprite;**
    24    
    25    // Globals
    26    //////////
    27    
    28    // ID counter. so each object has a unique id
    29  int IDC = 0;
       
    30    // to end the main loop
    31  bool done = false;
       
    32    // pointer to the first and last objects in our linked list of objects.
    33  node * firstObject = NULL;
    34  node * lastObject = NULL;
       
    35    // define the screen
    36  SDL_Surface * screen;
    37  const int SCREEN_WIDTH = 800;
    38  const int SCREEN_HEIGHT = 600;
    39  const int SCREEN_BPP = 32;
       
       
    40    // temporary rect that can be manipulated for drawing
    41  SDL_Rect rectTemp;
       
    42    // for input
    43  SDL_Event event;
       
    44    // for various sprites
**    45  CSprite mySprite;**
       
    46    // Data Structures
    47    //////////////////
    48    
    49  struct node
    50  {
    51          CObject * obj;
    52          node * next;
    53          node * prev;
    54  };
       
    55    // Classes
    56    //////////
    57    
    58  class CObject
    59  {
    60          protected:
    61          int ID;
    62          node * myNode;
    63
    64          public:
    65            // de/constructor
    66          CObject();
    67          ~CObject();
    68
    69            // public functions
    70          void Init();
    71          void DeInit();
    72          void Draw();
    73          void Step();
    74          void KeyDown();
    75          void KeyUp();
    76          int GetID();
    77
    78            // public variables
    79          int x, y;
    80          SDL_Surface * sprite;
    81  };
       
    [B]82  class CSprite
    83  {
    84          public:
    85            // de/constructor
    86          CSprite();
    87          ~CSprite();
    88
    89          SDL_Surface * block;
    90  };[/B]
       
    [B]91  class CBlock: public CObject
    92  {
    93          public:
    94            // de/constructor
    95          CBlock();
    96          ~CBlock();
    97  };[/B]
       
       
       
    98    // Class Functions
    99    //////////////////
   100    
   101  CObject::CObject()
   102  {
   103          Init();
   104  }
       
   105  CObject::~CObject()
   106  {
   107          DeInit();
   108  }
       
   109  void CObject::Init()
   110  {
   111            // add this instance to the global linked list of objects
   112          myNode = new node;
   113          myNode->obj = this;
   114          myNode->next = NULL;
   115          myNode->prev = NULL;
   116
   117          if (lastObject == NULL)
   118          {
   119                  firstObject = myNode;
   120                  lastObject = myNode;
   121          } else
   122          {
   123                  lastObject->next = myNode;
   124                  myNode->prev = lastObject;
   125                  lastObject = myNode;
   126          }
   127
   128            // set other variables
   129          ID = IDC;
   130          IDC++;
   131          x = 0;
   132          y = 0;
   133          sprite = NULL;
   134  }
       
   135  void CObject::DeInit()
   136  {
   137          if (myNode == firstObject)
   138          {
   139                  firstObject = myNode->next;
   140          } 
   141          if (myNode == lastObject)
   142          {
   143                  lastObject = myNode->prev;
   144          }
   145          if (myNode->next != NULL)
   146          {
   147                  myNode->next->prev = myNode->prev;
   148          }
   149          if (myNode->prev != NULL)
   150          {
   151                  myNode->prev->next = myNode->next;
   152          }
   153          if (sprite != NULL)
   154          {
   155                  SDL_FreeSurface(sprite);
   156          }
   157  }
       
   158  int CObject::GetID()
   159  {
   160          return ID;
   161  }
       
   162  void CObject::Draw()
   163  {
   164          if (sprite != NULL)
   165          {
   166                    // draw my sprite
   167                  rectTemp.x = x;
   168                  rectTemp.y = y;
   169                  SDL_BlitSurface(sprite, 
   170                                  NULL, 
   171                                  screen, 
   172                                  &rectTemp);
   173          }
   174  }
       
   175  void CObject::Step()
   176  {
   177  }
       
   178  void CObject::KeyDown()
   179  {
   180  }
       
       
   181  void CObject::KeyUp()
   182  {
   183  }
       
   [B]184  CSprite::CSprite()
   185  {
   186          block = LoadImage("block.png");
   187  }
       
   188  CSprite::~CSprite()
   189  {
   190          SDL_FreeSurface(block);
   191  }[/B]
       
   192  CBlock::CBlock()
   193  {
   194          Init();
   195          //**sprite = mySprite.block;**
   196  }
       
   197  CBlock::~CBlock()
   198  {
   199          DeInit();
   200  }
       
       
   201    // Functions
   202    ////////////
       
   203  bool Init()
   204  {
   205            //Initialize SDL video subsystems
   206          if( SDL_Init( SDL_INIT_VIDEO ) == -1 )    
   207          {
   208                  return false;    
   209          }
   210
   211            // create screen
   212          screen = SDL_SetVideoMode(      SCREEN_WIDTH, 
   213                                          SCREEN_HEIGHT, 
   214                                          SCREEN_BPP, 
   215                                          SDL_SWSURFACE ); 
   216            //Register SDL_Quit() with atexit
   217          atexit(SDL_Quit);
   218
   219          return true;
   220  }
       
   221  void HandleInput()
   222  {
   223            //Using polling to read input
   224          while (SDL_PollEvent(&event)) 
   225          {
   226                  if (event.type == SDL_KEYDOWN) 
   227                  {
   228                          node * temp;
   229                          temp = firstObject;
   230                          while (temp != NULL)
   231                          {
   232                                  temp->obj->KeyDown();
   233                                  temp = temp->next;
   234                          }
   235                            // special case, quit
   236                          if (event.key.keysym.sym == SDLK_ESCAPE)
   237                          {
   238                                  done = true;
   239                          }
   240                  }
   241
   242                  if (event.type == SDL_KEYUP) 
   243                  {
   244                          node * temp;
   245                          temp = firstObject;
   246                          while (temp != NULL)
   247                          {
   248                                  temp->obj->KeyUp();
   249                                  temp = temp->next;
   250                          }
   251                  }
   252
   253
   254                  if (event.type == SDL_QUIT)
   255                  {
   256                          done = true;
   257                  }
   258          }//end while
   259  }
       
   260  void DrawScene()
   261  {
   262          node * temp;
   263          temp = firstObject;
   264            // go through each object
   265          while (temp != NULL)
   266          {
   267                    // execute this objects draw event
   268                  temp->obj->Draw();
   269
   270                    // move to the next object
   271                  temp = temp->next;
   272          }
   273          SDL_Flip(screen);
   274  }
       
   275  SDL_Surface * LoadImage( std::string filename )
   276  {
   277          SDL_Surface * loadedImage = NULL;
   278          SDL_Surface * compatibleImage = NULL;
   279
   280          if(filename.c_str() == NULL) 
   281          { 
   282                  return NULL;
   283          }
       
   284            // load the image
   285          loadedImage = IMG_Load(filename.c_str());
   286
   287          if( loadedImage == NULL )
   288          {
   289                    // if not exit the function
   290                  return NULL;
   291          }
       
   292            // convert image to screen format
   293          compatibleImage = SDL_DisplayFormat( loadedImage );
       
   294          if( compatibleImage != NULL ) 
   295          {
   296                    // set transparrent colour
   297                  Uint32 colorkey = SDL_MapRGB(   compatibleImage->format, 
   298                                                  255, 
   299                                                  0, 
   300                                                  255); // choose pink
       
   301                  SDL_SetColorKey(compatibleImage, 
   302                                  SDL_RLEACCEL | SDL_SRCCOLORKEY, 
   303                                  colorkey);
   304          }
       
   305            // Destroy the old copy
   306          SDL_FreeSurface( loadedImage );
       
   307            // return a pointer to the newly created display compatible image
   308          return compatibleImage;
   309  }
       
   310    // Main
   311    ///////
       
   312  int main()
   313  {
   314          Init();
   315
   316          CObject * myObj1 = new CObject();
   317          CObject * myObj2 = new CObject();
   318
   319          myObj1->sprite = LoadImage("player.png");
   320
   321          while (!done)
   322          {
   323                  DrawScene();
   324                  HandleInput();
   325                  SDL_Delay(20);
   326          }
   327
   328          return 0;
   329  }

```

is that wot u wanted?

---

### Post by duff on 2006-12-05
That helps. You problem is that you are trying to allocate space for a class that hasn't been defined yet.  "class CSprite" isn't enough information to create an instance of a CSprite object (which is what you are trying to do on line 45).  The forward declaration on line 23 is only good enough for a pointer to CSprite.

Move line 45 somewhere past the implementation of class CSprite (past line 90) and you should be ok.

---

### Post by Choad on 2006-12-06
> **duff said:**
> That helps. You problem is that you are trying to allocate space for a class that hasn't been defined yet.  "class CSprite" isn't enough information to create an instance of a CSprite object (which is what you are trying to do on line 45).  The forward declaration on line 23 is only good enough for a pointer to CSprite.

Move line 45 somewhere past the implementation of class CSprite (past line 90) and you should be ok.
thankyou so much! and thanks for the propper explanation too :)

i think i will just make it a pointer in that case. theres no real need for it to *not* be a pointer, as all it does is point to things it's self

---

### Post by Choad on 2006-12-06
> **Choad said:**
> thankyou so much! and thanks for the propper explanation too :)

i think i will just make it a pointer in that case. theres no real need for it to *not* be a pointer, as all it does is point to things it's self
ok now this line

sprite = mySprite->block;

in class CBlock's constructor event causes a segmentation fault (core dumped) error when i run it

it only happens when i create an instance of CBlock.

```


class CObject
{
	protected:
	int ID;
	node * myNode;
	
	public:
	  // de/constructor
	CObject();
	~CObject();
	
	  // public functions
	void Init();
	void DeInit();
	void Draw();
	void Step();
	void KeyDown();
	void KeyUp();
	int GetID();
	
	  // public variables
	int x, y;
**	SDL_Surface * sprite;**
};

class CSprite
{
	public:
	  // de/constructor
	CSprite();
	~CSprite();
	
**	SDL_Surface * block;**
};

class CBlock: public CObject
{
	public:
	  // de/constructor
	CBlock();
	~CBlock();
};

CSprite::CSprite()
{
**	block = LoadImage("block.png");**
}

CBlock::CBlock()
{
	Init();
**	sprite = mySprite->block;**
}

int main()
{
	Init();
	
	CObject * myObj1 = new CObject();
	CObject * myObj2 = new CObject();
**	CBlock * myBlock = new CBlock();**
	//myBlock->x = 100;
	//myBlock->y = 100;
}

```

---

### Post by duff on 2006-12-06
if you changed **mySprite** to a pointer, did you remember to allocate space for it?

---

### Post by Choad on 2006-12-06
> **duff said:**
> if you changed **mySprite** to a pointer, did you remember to allocate space for it?
oh god im getting lost again! :S

ok, i initially just changed it to

CSprite * mySprite;

and it compiled, and thats when i posted the last post.

i then changed it to 

CSprite * mySprite = new CSprite();

thinking thats what you meant by "allocating space" and i now get this wierd error

```

proj.cpp -lSDL -lSDL_image
newproj.cpp:56: error: invalid use of undefined type &#8216;struct CSprite&#8217;
newproj.cpp:27: error: forward declaration of &#8216;struct CSprite&#8217;

```

i have clearly declared it as a CLASS tho!? heeelpppp

i am also verging on the stoned side now... i dont think ill be up to coding much soon lol.

---

### Post by Choad on 2006-12-06
im thinking i might just screw this whole CSprite class and simply store all my sprites as global variables. all this CSprite class is doing is tidying them all away in to a class so i can refer to the loaded images as mySprite->ball or whatever

but i suppose i gotta learn somehow lol. may as well keep plugging away at this damned class

---

### Post by Gustav on 2006-12-08
> **Choad said:**
> oh god im getting lost again! :S

ok, i initially just changed it to

CSprite * mySprite;

and it compiled, and thats when i posted the last post.

i then changed it to 

CSprite * mySprite = new CSprite();

thinking thats what you meant by "allocating space" and i now get this wierd error

```

proj.cpp -lSDL -lSDL_image
newproj.cpp:56: error: invalid use of undefined type ‘struct CSprite’
newproj.cpp:27: error: forward declaration of ‘struct CSprite’

```

i have clearly declared it as a CLASS tho!? heeelpppp

i am also verging on the stoned side now... i dont think ill be up to coding much soon lol.

I think the problem is that you have the line "CSprite * mySprite = new CSprite();" outside main(). 

Keep "CSprite * mySprite" where you have it and have the line "mySprite = new CSprite();" either first in main() or in Init() and it might work :)

---

