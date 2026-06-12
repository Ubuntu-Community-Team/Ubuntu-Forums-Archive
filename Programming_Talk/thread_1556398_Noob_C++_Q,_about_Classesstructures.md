---
title: "Noob C++ Q, about Classes/structures"
date: 2010-08-19
forum: Programming Talk
---

### Post by cthulhu_54 on 2010-08-19
I have two classes, one that defines the x,y,z direction (of a particle) and one that defines left, right. Now I want to put them together to give:
```
object.x = 1
object.x.l = 4.5 //(for left)
object.x.r = 32
```
As I understand it this will not work. So I've written the following program in C++, but it will not compile:

[PHP]using namespace std;

class Direction{
public:
  Direction(void);
  double r;  //right
  double l;  //left
};

class Particle{
public:
  Particle(void);
  int x;
  int y;
  int z;
  
  Direction dir;
};

int main(){
  
  Particle test;
  test.x = 5;
  test.y = 11;
  test.z = 3;      //OK, works

  Direction temp;    
  temp.r = 1;
  temp.l = 5.3;     //OK, works

  test.x.dir = temp;  //AARRGHHH!
  test.x.dir.r = 32;  //AARRGHHH!
  
  return 0;
}[/PHP]

And I get the error:
```
 request for member ‘dir’ in ‘test.Particle::x’, which is of non-class type ‘int’
```
for the two last lines. 
I've googled it (omitting the specifics in my error message above), and the first 30-40 hits are all about mixing up the -> with . operator, or declaring things like Particle() test, or Particle test(), but that can't be the case here can it? 

What did I do wrong? Any clue would be greatly appreciated!

---

### Post by GeneralZod on 2010-08-19
The error message is pretty much exactly right: test.x is of type int, so test.x.dir does not make sense - an "int" is not a class/ struct, and doesn't have a "dir" as a member :)

I think there's a fundamental problem with the way you're trying to model this, but I don't understand the "real-life" domain well enough to work out what it is: what do the x,y and z members of a particle represent? From your code, it looks like co-ordinates, but from your description, it sounds like they are supposed to represent a direction, which makes the inclusion of a further "dir" field confusion.  

Why does a Direction have a "left" component and a "right" component? Do they cancel out, or ... ?

---

### Post by endotherm on 2010-08-19
as zod mentions, change this:
```

...
[COLOR=#000000][COLOR=#0000bb]test[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]x[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]dir [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]temp[/COLOR][COLOR=#007700];  [/COLOR][COLOR=#ff8000]//AARRGHHH! 
  [/COLOR][COLOR=#0000bb]test[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]x[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]dir[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]r [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]32[/COLOR][COLOR=#007700];  [/COLOR][COLOR=#ff8000]//AARRGHHH! [/COLOR][/COLOR]
...

```to```

...
[COLOR=#000000][COLOR=#0000bb]test[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]dir [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]temp[/COLOR][COLOR=#007700];  [/COLOR][COLOR=#ff8000]//AARRGHHH! 
  [/COLOR][COLOR=#0000bb]test[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]dir[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]r [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000bb]32[/COLOR][COLOR=#007700];  [/COLOR][COLOR=#ff8000]//AARRGHHH! [/COLOR][/COLOR]
...

```

do you see why?

---

### Post by cthulhu_54 on 2010-08-19
Yes, I've never tried to do anything like this before, but Each Particle has a position x,y,z and in each direction (six in total) they can have a certain probability to move. Hmm, perhaps this is a bad implementation? 

I got this idea from the last section here ("Nesting structures")
[http://www.cplusplus.com/doc/tutorial/structures/](http://www.cplusplus.com/doc/tutorial/structures/)
where they have:
[PHP]struct movies_t {
  string title;
  int year;
};

struct friends_t {
  string name;
  string email;
  movies_t favorite_movie;
  } charlie, maria;

friends_t * pfriends = &charlie;

//the following is valid:
charlie.name
maria.favorite_movie.title
charlie.favorite_movie.year[/PHP]
(I was thinking I could replace the movies with left/right, and the names by x,y,z)

Perhaps I'm starting to see that this was a bad way of doing it. But I'd like to be able to bundle up these six different values (for the speed in each direction) plus the three coordinates in some nice way. (other than having nine variables: int x,y,z; double speedXright, speedXleft, speedYright... )

**EDIT:** AHHH-ha! Now that you spell it out for me endotherm, yes, now I see. Thank you so much, both of you.

---

