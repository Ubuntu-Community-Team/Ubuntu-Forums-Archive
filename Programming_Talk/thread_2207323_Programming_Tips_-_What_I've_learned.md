---
title: "Programming Tips - What I've learned"
date: 2014-02-23
forum: Programming Talk
---

### Post by slooksterpsv on 2014-02-23
I thought, where I've now started to understand and simplify how I'm developing my programs, it'd be good to share my experiences in hopes it'll help someone out with their difficulties and frustrations. Here are my top tips and things I've found (and regularly ignored) when attempting to make programs:

1. Prototype - If you know you're going to have a function for something, make a prototype of it. For example, in a game if I want to throw a rock I may prototype it for later development. e.g.:

```

void ThrowRock()
{
 //Insert code here for how to throw a rock
}

```

I don't have to develop it just yet, but I can put it in there for testing purposes later on. You can even prototype the basics such as:

```

....
case SDLK_space:
 if(player->weapon(rock)) {
  ThrowRock();
 }
...

void ThrowRock() {
 cout << "Throwing rock.";
}

```

2. Layout how your code should work in comments. That way you can break up things that aren't simple and make functions or figure out how to program it easier. Taking the rock example from above:
```

void ThrowRock() {
 //How to throw a rock from the player
 //Check and see if a rock is already thrown - IF statement
 //Get players position on the screen - Pass in players coordinates
 //Place rock depending on direction player is facing - Pass in players direction
 //Set speed for how fast rock will travel - Predetermine speed?
 //Draw the rock - Draw it on the screen
 //Set update method to continue drawing rock until it hits enemy or reaches end of screen - in Update() call Rock drawing method
}

```

Which may ultimately end up as
```

void ThrowRock(int player_x, int player_y, int player_direction) {
 if(!rockIsBeingThrown)
 {
   rockIsBeingThrown = true;
   rock.x = player_x;
   rock.y = player_y;
   rock.direction = player_direction;
   rock.speed = 6;
   DrawRock();
 }
}

...
void Update()
{
  UpdatePlayer();
  if(rockIsBeingThrown){
  UpdateRock();
 }
  ...
}

```

3. Don't create new variables if using the same information. I have a camera class that I'm always referencing for different objects such as my player, map, objects on screen, moving objects, so instead of initializing a camera class in each and updating the information 4 times, I passed in the memory location to access the information:
```


...
Camera main_camera;
...
Camera* cam;
...

void OnInit(Camera* camera)
{
  cam = camera;
}
...

OnInit(&camera_main);

```

4. Vectors are amazing things. std::vector allows me to create a linked-list kind of like object. With it I can push and pop members and it's very useful for Game States, Maps, Object Maps, etc. I can decide what information I want to pass in and push it onto the vector without having to know the size. Research on how you can use these as they are very useful.

5. Recode, recode, recode. Now I don't mean recode your project, but make a few test projects to try different things and program it a few times. This will help with learning functions, members, namespaces, variables, etc. If you need to simplify it such as you don't need every option you get presented, make your own function to pass in the rest, e.g.
```


void SomeBigFunction(int a, int b, int c, float d, float e, float f);

void MyCallToBigFunction(int a, int b)
{
 SomeBigFunction(a, b, 0, 0, 0, 0);
}


```

6. Use descriptive variables (not too extreme). int a or int x tells you nothing and you can spend lots of time searching for what the variables did. In my programming I needed a bounds item to determine collision so instead so I made the following:
```


struct Bounds {
 int top, bottom, left, right;
};

...

int player_x; //makes sense, it's the players x position;
int x; //NO what x, enemies? camera? player? graph?
int player_location_coordinate_on_the_2d_graph_for_x_and_y_axis; //NO that's way overboard
int player_direction; //Awesome!
bool is1; //What's 1 what does 1 mean, why 1
bool isBombActive; //Ok is the bomb active got it.

```

Well I think that's all for now. It's taken me a while to learn and books kept trying to teach me yet I didn't know why, but now I understand and it helps.

---

### Post by ajgreeny on 2014-02-23
> Ubuntu seems cluttered Amazon? Dash plugins for online services? Online  Services search results? Wow, talk about commercialism. I'll stick with  elementary OS =DSo just turn them off if you want to.

Don't forget Canonical is a commercial company, trying to make some profit from Ubuntu so I don't blame it for doing whatever it needs in that manner to help it do so, as long as I don't have to use it if I don't want to!

---

### Post by ofnuts on 2014-02-23
Chalk up another one who has seen the light :)

---

### Post by slooksterpsv on 2014-02-23
@ajgreeny Uhhh... thats my signature and not part of the actual topic.

---

### Post by ajgreeny on 2014-02-23
OK.  There was no way to tell that, apart perhaps from the fact that it was all right down at the bottom of the post.

Perhaps worth your while using a completely different font, if that's possible, just to differentiate it from the rest.

---

### Post by trent.josephsen on 2014-02-23
> **ajgreeny said:**
> OK.  There was no way to tell that, apart perhaps from the fact that it was all right down at the bottom of the post.

Perhaps worth your while using a completely different font, if that's possible, just to differentiate it from the rest.
[HR][/HR]
DISTRO: Xubuntu 12.04-64bit --- [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") --- [Grub2 wiki]("https://wiki.ubuntu.com/Grub2") & [Grub2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275") --- [RootSudo]("https://help.ubuntu.com/community/RootSudo")

Perhaps.

---

### Post by slooksterpsv on 2014-02-24
Yeah, this new forum layout is a bit different, I'm used to the <hr> benig a bit more visible.

---

### Post by Michael_Duchemin on 2014-02-28
Back to the actual topic, #2 can save you a lot of time and unnecessary rework in #5.

---

