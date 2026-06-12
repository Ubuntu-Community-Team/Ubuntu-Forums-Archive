---
title: "vector class issue causing segmentation errors"
date: 2009-02-27
forum: Programming Talk
---

### Post by tneva82 on 2009-02-27
I sure seem to be adept at running into those.

Anyway. Code in question is:

```
for (vector<individualSpawn>::iterator it=spawnLocations.begin();it != spawnLocations.end();it++) {
    while(1) { printf("hep"); }
```

I never reach the while loop(put there just to see wether I reach it). While loop BEFORE for statement is reached. SpawnLocations declaration is:

```
  vector<individualSpawn> spawnLocations;
```

Elsewhere in code I add one class type invidualSpawn to spawnLocations. Size shows then 1.

I think I really need to figure this one. I'm affraid lots of other code is going to be faulty as well in similar way...

If I comment out the for loop(which ATM is composed of just the for loop. Rest is commented out as well) everything works fine. If it is uncommented BANG! A crash. Tried also with this for loop but didn't solve:

```
for (int i=0;i<spawnLocations.size();i++) {
```

Also if I hardwire the for loop so that it's i<1 then it works just fine. Why the size() function isn't working?

Edit: Also this:

```
if(spawnLocations[i].isClear) {
```

is causing segmentation errors. Also hardwiring i to 0 isn't changing that one.

What the heck am I screwing up with vectors?

---

### Post by dwhitney67 on 2009-02-27
Ok, to summarize, this is what you are stating:
```

vector<individualSpawn> spawnLocations;

...

for (vector<individualSpawn>::iterator it=spawnLocations.begin();it != spawnLocations.end();it++) {
    while(1) { printf("hep"); }

```

Without the missing code, I haven't a clue how you are populating (adding elements) to the vector.

Before you respond, may I suggest that you tidy up the code a bit by defining a typedef.

```

typedef std::vector<individualSpawn> SpawnLocations;

SpawnLocations spawnLocations;

...

for (SpawnLocations::iterator it = spawnLocations.begin(); it != spawnLocations.end(); it++) {
    ...

```

---

### Post by geirha on 2009-02-27
You are using the vectors the right way, so there's probably something wrong with the individualSpawn class...

---

### Post by Lux Perpetua on 2009-02-27
> **tneva82 said:**
> Elsewhere in code I add one class type invidualSpawn to spawnLocations. Size shows then 1.Please post that code. 

> ```
for (int i=0;i<spawnLocations.size();i++) {
```

Also if I hardwire the for loop so that it's i<1 then it works just fine. What do you mean by "works just fine"? What does the loop do?

> ```
if(spawnLocations[i].isClear) {
```

is causing segmentation errors. Also hardwiring i to 0 isn't changing that one.It sounds like you're operating on an empty vector.

---

### Post by tneva82 on 2009-02-27
Okay so some more code(note I changed vector definition a bit).

```
class individualSpawn {
...data of individual spawn
};

class spawn {
private:
  vector<individualSpawn*> spawnLocations;
  vector<individualSpawn*>::iterator it;
public:
  spawn(char *filename);
  bool checkSpawns(vector<char*> creatureTemplates, idHandler *myIdHandler, vector<creature*> creatureList);
  void creatureKilled(int spawnId);

};

spawn::spawn(char *filename) {

 FILE *pFile=fopen(filename, "r");
  fpos_t pos;
  int c;
  bool done=false;
  char *line=new char[500];
  char *temp;
  
  spawnLocations.resize(MAX_CREATURES);
  spawnLocations.clear();
  while(!done) {
    fgetpos (pFile,&pos);
    c=getc(pFile);
    if(c=='#') {
      while(getc(pFile)!='\n'){}
    } else if(c==EOF) {
	done=true;
    } else {
      fsetpos(pFile, &pos);
      fgets(line, 500, pFile);
      **spawnLocations.push_back(new individualSpawn());**
      temp=strtok(line, ";");
      spawnLocations.back()->id=atoi(temp);
      // continue to fill new individual spawn data
   } 
  }
}
```

And then in function that crashes:

 ```
 for (int i=0;i<spawnLocations.size();i++) {
while(1) { printf("hep"); }
    if(spawnLocations[i]->isClear) {
```

Again if I replace spanLocations.size() with 1 it works just fine and goes to while loop. isClear(which is boolean variable) causes also to crash.

Pretty much all the code related to this. Only missing couple of variable declarations that doesn't come into play here and whole bunch of strtok and atoi calls when I parse string for information.

---

### Post by dwhitney67 on 2009-02-27
I took your idea, simplified it a bit, and came up with the following:
```

#include <vector>
#include <iostream>

struct IndividualSpawn
{
  int value;
};


class Spawn
{
  public:
    typedef std::vector<IndividualSpawn*> SpawnLocations;

    Spawn(const char* filename = 0)
    {
      m_spawnLocations.push_back(new IndividualSpawn);
      m_spawnLocations.back()->value = 10;
    }


    friend std::ostream& operator<<(std::ostream& os, const Spawn& spawn)
    {
      for (SpawnLocations::const_iterator it  = spawn.m_spawnLocations.begin();
                                          it != spawn.m_spawnLocations.end();
                                          ++it)
      {
        os << (*it)->value;
      }

      return os;
    }

  private:
    SpawnLocations m_spawnLocations;
};



int main()
{
  Spawn spawn;
  std::cout << spawn << std::endl;
}

```

As you can see, I skipped most of the stuff that you were doing in the Spawn constructor, merely for test purposes.

Anyhow, hopefully this will help you progress further with your project.

Btw, you really should avoid mixing C library and C++ together; although there is nothing wrong with it, it does look horrible.

In lieu of a char*, use an std::string, or better yet a const std::string&.

In lieu of fopen(), use std::fstream (or std::ofstream).

And the code would look cleaner if you allocated an IndividualSpawn first, perhaps initializing it via its constructor, and then pushing it back onto the vector.

Don't forget to implement your destructor to delete all of the allocated objects.

---

### Post by tneva82 on 2009-02-27
> **Lux Perpetua said:**
> Please post that code. 

What do you mean by "works just fine"? What does the loop do?

It enters the inside of for loop which contains just the while loop.

And as said I printed elsewhere size of the vector and it showed 1 as a size.

---

### Post by tneva82 on 2009-02-27
> **dwhitney67 said:**
> In lieu of a char*, use an std::string, or better yet a const std::string&.

In lieu of fopen(), use std::fstream (or std::ofstream).

Sorry. Never been comfortable with those tripple darned streams. stdio.h has functions that are much more to my liking. Lot less errors this way that atleast I have some sort of idea how to do it.

And the code would look cleaner if you allocated an IndividualSpawn first, perhaps initializing it via its constructor, and then pushing it back onto the vector.

Atleast now by changing how the thing works I MOSTLY managed to get it working. One segmentation error which I can avoid by hardwiring one index which shouldn't be hard and for some reason it seems to INSTANTLY create new creature when it's supposed to wait 5000 milliseconds but atleast it's not crashing.

Edit: THAT segmentation error was easy to fix and wasn't actually even error with code. It was error in scripts :D I had set up this spawn generate creature type 1. Only problem was there was just one creature type which is index 0! Note to self: Put some sort of error checking code in place ASAP!

Edit: WOHOO! It works! It works! Now creature appears when I want him to appear!

Also got rid of stupid class spawn containing vector of individual spawns. Not sure why but I hate that system and already got rid of that for items and creatures so good riddance for this one too! IMO much cleaner to store vector into the main server class rather than main server class containing class spawn which in turn contains individual spawns in vector.

---

### Post by dwhitney67 on 2009-02-27
Out of curiosity, what does your data file look like?  A small snippet is all that is required.

---

### Post by tneva82 on 2009-02-27
> **dwhitney67 said:**
> Out of curiosity, what does your data file look like?  A small snippet is all that is required.

Spawn file:

#id;x;y;z;requirementID for requirement.script;creatureID;spawnTime
#first one creates an creature type 0 to 50, 0, 25 co-ordinates every 2 seconds.
0;50.0;0.0;25.0;0;0;2000
1;25.0;0.0;10.0;0;0;3000
2;15.0;0.0;80.0;0;0;4000
3;35.0;1.0;50.0;0;0;900000

However now I managed to get it all working. Realised also mistake which I have repeated elsewhere(several places) so now off to fix them to avoid MORE segmentation errors once I incorporate more of functions done into the program.

And note that the line gets parsed fine. These parsing functions were pretty much first I did and among them I printed out result just to check they get what I want into the variables.

---

### Post by Lux Perpetua on 2009-02-27
> **tneva82 said:**
> It enters the inside of for loop which contains just the while loop.

And as said I printed elsewhere size of the vector and it showed 1 as a size.
So basically ```
 for (int i=0; i<1; i++) {
    while(1) { printf("hep"); }
}
```Let's just say, if that code never reached the printf statement, you would have a truly serious problem on your hands! Anyway, I'm glad you sorted out your errors.

---

### Post by tneva82 on 2009-02-27
> **Lux Perpetua said:**
> Let's just say, if that code never reached the printf statement, you would have a truly serious problem on your hands! Anyway, I'm glad you sorted out your errors.

That worked when hardwired. When 1 was instead vectors size() function it went haywire. Not quite sure why though. However problem solved and logic went bit cleaner as well in the process(always a nice thing!).

---

