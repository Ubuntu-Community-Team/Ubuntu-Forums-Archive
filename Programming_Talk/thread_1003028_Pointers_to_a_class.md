---
title: "Pointers to a class:"
date: 2008-12-05
forum: Programming Talk
---

### Post by WitchCraft on 2008-12-05
Hi, I have a problem with pointers in a class in C++...

the following situation:

I need a pointer to a member function, within the same class:



```

#include <iostream>

//using namespace std;

class Testpm {
public:
	Testpm();
	~Testpm();

   void m_func1() 
   {
      std::cout << "m_func1\n"; 
   }
   int m_num;

   //void (*pmfn)() ;
};

Testpm::Testpm()
{
	pmfn = &m_func1;
}

Testpm::~Testpm()
{}

// Define derived types pmfn and pmd.
// These types are pointers to members m_func1() and
// m_num, respectively.
//void (Testpm::*pmfn)() = &Testpm::m_func1;
//int Testpm::*pmd = &Testpm::m_num;

int main() {
   Testpm ATestpm;
   Testpm *pTestpm = new Testpm;

   delete pTestpm;
}

```

I have an array of function pointers:

modSupport_t temporary_modTable[] =

{

// char name[64], weapons, numweap, playerinfo, unlagged, deadflag, clientinfo_distortion, VerifyTarget, AddGlowShell, AddTarget, DrawEsp

		 { "baseq3"    , weapons_BQ3, 10,  0, 0, EF_DEAD,  0,  &VerifyTarget_BQ3 , &AddGlowShell_BQ3 , &AddTarget_BQ3 ,  &DrawEsp_BQ3  },


Now I added the functions VerifyTarget_BQ3 , AddGlowShell_BQ3 , AddTarget_BQ3 ,  DrawEsp_BQ3 to a class.

And the modSupport_t array of function pointers is also in this class.
The compiler won't compile it, because it says it can't assign a member function to the function pointer...


Now I really don't want to move the functionpointers or member functions outside the class...


I wanted to add a member function function pointer to the class, and then assign the function pointer address in the constructor, but nothing seems to work.


i need something like:

```

class Testpm {
public:
	Testpm();
	~Testpm();
       void memberfunction_no_1()
       {
           //do something
           return ;
       }
       // memberfunction no 2 & 3, etc

       void (*functionpointer_no_1)() ;
       void (*functionpointer_no_2)() ;
       void (*functionpointer_no_3)() ;
       // etc.
       modSupport_t modTable[20] ; /()/ this is the array containing the functionpointers

};

Testpm::Testpm()
{
	functionpointer_no_1 = &memberfunction_no_1;
        // the above line is is what doesn't work
	//functionpointer_no_1 = &(this->memberfunction_no_1);
        // i think it should probably be something like the above, 
        // i can't initialize it by creating the class object in main, and then passing some king of pointer, because i am going to use it in another class...


modSupport_t temporary_modTable[20] ;

	modTableSize = 
		 { "baseq3"    , weapons_BQ3, 10,  0, 0, EF_DEAD,  0, MOfunctionpointer_no_1, functionpointer_no_2, functionpointer_no_3, etc  },
                 // etc.
		 //{ "cpma"      , weapons_BQ3, 10,  0, 0, EF_DEAD,  0, MOD_FUNCS(BQ3)  },

		 //{ "q3ut4"     , weapons_UT4, 15,  0, 1, EF_DEAD, -4, MOD_FUNCS(FRZ)  },

		 //{ "freeze"    , weapons_BQ3, 10,  0, 0, EF_DEAD,  0, MOD_FUNCS(FRZ)  },

		 //{ "ufreeze"   , weapons_BQ3, 10,  0, 1,   0x100,  0, MOD_FUNCS(FRZ)  },

		 //{ "arena"     , weapons_BQ3, 10,  0, 0, EF_DEAD,  0, MOD_FUNCS(FRZ)  },

		 //{ "threewave" , weapons_BQ3, 12, 17, 0, EF_DEAD,  0, MOD_FUNCS(FRZ)  }
}

sizeof(temporary_modTable)/sizeof(temporary_modTable[0]) ;
	memcpy(&modTable, &temporary_modTable, sizeof(modSupport_t) * modTableSize) ;

}

Testpm::~Testpm()
{}

```

Can anybody help?

---

### Post by dexter on 2008-12-05
If you need pointers to member functions of a class, you'll need to declare those functions static. 
- Non-static functions always belong to an instantiation of a class and have full access to all class members.
- Static functions can be used without an instantiation be they don't have access to non-static members of the class, since those members only belong to an instantiation of a class.

---

### Post by WitchCraft on 2008-12-05
> **dexter said:**
> If you need pointers to member functions of a class, you'll need to declare those functions static. 
- Non-static functions always belong to an instantiation of a class and have full access to all class members.
- Static functions can be used without an instantiation be they don't have access to non-static members of the class, since those members only belong to an instantiation of a class.

static functions in a class don't compile

---

### Post by dwhitney67 on 2008-12-05
In an effort to up my post count, I just wanted to weigh in.....

What are you trying to accomplish by keeping a pointer of a method of a class, within the same class????

Statically declared methods, while doable, may not be the appropriate solution to your problem.

I see too many queries on these forums along the line... I'm trying to do something, but it doesn't work... how do I fix it?  But not once is the **real** requirement presented.  It's analogous to the countless climbers that have died going up the wrong side of the mountain.  Yep, they are climbing upwards, but...

---

### Post by WitchCraft on 2008-12-05
OK, i further simplified and identified the problem:


if you comment out the 2 lines with DOESN'T WORK, you can compile it...
```

#include <iostream>
using namespace std;

class X {
public:
  X();
  ~X();
  int a;
  void f(int b) 
  {
    cout << "The value of b is "<< b << endl;
  }

  static void g(int b) 
  {
    cout << "The value of b is "<< b << endl;
  }

  void h(int b) 
  {
    cout << "The value of b is "<< b << endl;
  }

  int* pa ;
  void (X::*fuptr)(int b) ;
};

X::X()
{
	printf("Calling constructor\n");
	a = 5;
	pa = &a ;
        fuptr = &X::h ;
        (this->*fuptr)(99);
	printf("a=%d\n", *pa);
	printf("Leaving constructor\n");
}

X::~X()
{
	printf("Calling destructor\n");
	printf("Leaving destructor\n");
}

int main() {

  // declare pointer to data member
  int X::*ptiptr = &X::a;

  // declare a pointer to member function
  void (X::* ptfptr) (int) = &X::f;

  // create an object of class type X
	printf("\n\ninstantation\n\n");
  X xobject;

  // initialize data member
  xobject.*ptiptr = 10;

  cout << "The value of a is " << xobject.*ptiptr << endl;
  printf("a = %d\n", (xobject.a));  // works
  printf("a as pointer = %d\n", (xobject.*pa)); // DOESN'T WORK
  // call member function
  (xobject.*ptfptr) (20);
  (xobject.*fuptr)(199); // DOESN'T WORK
}

```
Why do i get this:
g++ source.cpp -o source
source.cpp:62: error: &#8216;pa&#8217; was not declared in this scope
source.cpp:65: error: &#8216;fuptr&#8217; was not declared in this scope

I don't get it, why not declared? They are declared in the class. 
It works in the constructor. But then?
How can they possibly disappear???
If they are not initialized, or have wrong values - which they don't - i should get a segmentation fault, not a compile error...

---

### Post by CptPicard on 2008-12-06
> **dwhitney67 said:**
> 
I see too many queries on these forums along the line... I'm trying to do something, but it doesn't work... how do I fix it?  But not once is the **real** requirement presented.

Yup. Not only that, but sometimes you even get a fairly non-grateful "just shut up and answer the exact question" reaction when trying to point this out...

---

### Post by dribeas on 2008-12-06
Member functions are different than free functions and static functions, and they work in a different manner. The idea is that for a free or static function no implicit object (this pointer) is required, but for member functions the function applies to a particular instance of the class and that information must be handed into the member method.

As you have already found out, there are operators to get and use member pointers, whether they are to an attribute or a method. Now, you are getting the compiler error because you are trying to use a member that is a pointer with the syntax of pointers-to-members, which are different things.

The syntax object.*ptr is valid for accessing the data pointed to by a local member pointer called ptr, not for accessing the data pointed by ptr (which is itself a member of object). For the latter you will need to use *(object.ptr). The dereference operator applied to the result of accessing to the member ptr.

That is, in the scope of main, neither pa nor fuptr are defined. They are defined in the class scope and you must access them through a class instance.  Change the lines in main to:
```

62:  printf("a as pointer = %d\n", *(xobject.pa));
65:  (xobject.*(xobject.fuptr))(199);

```

Then again, the important question is what is the rationale that has lead you into trying to write this overly complex solution. If you provide a small description of what you are trying to achieve I am sure others can comment on better more simpler designs. Unless, of course, what you want to achieve is understanding of member to pointers.

---

### Post by WitchCraft on 2008-12-06
> **dribeas said:**
> 

That is, in the scope of main, neither pa nor fuptr are defined. They are defined in the class scope and you must access them through a class instance.  Change the lines in main to:
```

62:  printf("a as pointer = %d\n", *(xobject.pa));
65:  (xobject.*(xobject.fuptr))(199);

```

Then again, the important question is what is the rationale that has lead you into trying to write this overly complex solution. If you provide a small description of what you are trying to achieve I am sure others can comment on better more simpler designs. Unless, of course, what you want to achieve is understanding of member to pointers.


First: many thanks for this perfect answer. That was very very useful.

62:  printf("a as pointer = %d\n", *(xobject.pa));
I think i understand line 62, that's my fault, i guess - stupid one, i confused the simple pointer with the member function pointer.


65:  (xobject.*(xobject.fuptr))(199);
Now with line 65 I have some difficulties. I guessed it was something like this, but why again the xobject??? in the constructor i can call the pointer via (this->*fuptr), which is what i would expect. Why do i suddenly need a this->*(this->fuptr)? I did not create a class in a class, or did I?

Well, I think I'm not sure about the syntax rules, because i also had a problem with:
```
 
void (X::*fuptr)(int b) ;

```
Why does it need a X::? I'd have assumed that i just need a void (*fuptr)(int b);  since it is in the class declaration, not the implementation outside the declaration...
I'd have assumed that it is like when you define functions.
In the class X you don't write void X::function(int argument), that you write in the implementation outside the class declaration, but inside???




As to the rest: i posted before i saw dwitney's post. Well, I'd certainly like to see whether i did it overly complex, so I'll explain what I'm doing:

I'm reimplementing OGC in C++, in a way that it doesn't need function detours.
Now that's a really interesting thing, because instead of detouring functions (overwriting them in RAM), you can instead use threads that work across platform, and then modify some quake/openarena/CoD/EnemyTerritory pointers to direct the program execution to your shared library ;-)) (=cheating)

now there are various mods/extensions of quake3, like openarena, enemy territory and urban terror (and many more).

Now, to support all these mods in one hack, you first need to know what game/mod is running, and then use your hack's functions to cheat.

Now, unfortunately not all engines work the same, so you need adapt some functions to one mod specifically. 

So you implement, for example:
void AimAtPlayersHead_Quake3(int clientID)
void AimAtPlayersHead_OpenArena(int clientID)
void AimAtPlayersHead_UrbanTerror(int clientID)
void AimAtPlayersHead_CoD(int clientID)
void AimAtPlayersHead_ET(int clientID)
 

Now instead of writing 5 programs for each game, you write one program for all games. The way you do that, is you set a functionpointer in your bot, which you set to the appropriate function for the appropriate mod.

Then, another thing to know is that there are most probably more than one function which is different in each game, and also the weapons, their speed, names and accuracy can vary...

So you load all the mod specific data in one struct, from which you take the mod specific data.

So you can do the following:
determine the mod at startup, get a number for it:
int MOD = identify_Mod(); // returns a number, for exampel 2 if openarena
then later
functionpointer_for_aimatplayershead = modTable[MOD].AimAtPlayersHead
with modTable being an array of ogcMod_t.


typedef struct ogcWeapon_s
{
	char name[32] ;
	float speed   ;
	vec3_t v      ;
} ogcWeapon_t     ;





typedef struct ogcMod_s
{
	char name[64]             ;
	ogcWeapon_t* weapons      ;
	int numweapons            ;
	int playerinfo            ;
	int unlagged              ;
	int deadflag              ;
	int clientinfo_distortion ;
	int  (*VerifyTarget)(centity_t* ent)   ;
	void (*AddGlowShell)(refEntity_t* ent) ;
	int  (*AddTarget)(centity_t* targ, centity_t* ent)        ;
	int  (*DrawEsp)(centity_t* ent, float *color, int* force) ;
} ogcMod_t ;





Now the first problem is, OGC was programmed in C.


Now one statement in C is:

ogcWeapon_t weapons_UT4[20]=
{
	// char name[32] float speed       vec3_t v
	{"NONE"         ,     0.0f,	{ 0.0f, 0.0f, 0.0f	}  },
	{"KNIFE"        ,     0.0f,	{ 4.0f,	0.0f, 26.0f	}  },
	{"BERETTA"      ,     0.0f,	{ 4.0f, 0.0f, 26.0f	}  },
	{"DESERT EAGLE" ,     0.0f,	{ 4.0f, 0.0f, 26.0f	}  },
	{"SPAS-12"      ,     0.0f,	{ 0.0f,	0.0f,  5.0f	}  },
	{"MPK5"         ,     0.0f,	{ 4.0f,	0.0f, 26.0f	}  },
	{"UMP-45"       ,     0.0f,	{ 4.0f,	0.0f, 26.0f	}  },
	{"HK-69"        ,  1000.0f,	{ 0.0f,	0.0f, 30.0f	}  },
	{"LR-300"       ,     0.0f,	{ 4.0f,	0.0f, 26.0f	}  },
	{"G-36"         ,     0.0f,	{ 4.0f,	0.0f, 26.0f	}  },
	{"PSG-1"        ,     0.0f,	{ 4.0f,	0.0f, 26.0f	}  },
	{"GRENADE"      ,   500.0f,	{ 0.0f,	0.0f, 30.0f	}  },
	{"FLASH"        ,   500.0f,	{ 0.0f,	0.0f, 30.0f	}  },
	{"SMOKE"        ,   500.0f,	{ 0.0f,	0.0f, 30.0f	}  },
	{"SR-8"         ,     0.0f,	{ 0.0f,	0.0f,  5.0f	}  },
	{"AK-103"       ,     0.0f,	{ 4.0f,	0.0f, 26.0f	}  },
	{"UNKNOWN"      ,     0.0f,	{ 4.0f,	0.0f, 26.0f	}  },
	{"NEGEV"        ,     0.0f,	{ 4.0f,	0.0f, 26.0f	}  },
	{"UNKNOWN"      ,     0.0f,	{ 4.0f,	0.0f, 26.0f	}  },
	{"M4"           ,	  0.0f,	{ 4.0f,	0.0f, 26.0f	}  }
};



Now in C++ i have classes, and I made one class for MOD.
There I put all mod specific things, for example the table with the weapons data above.


class Cmods
{
    public:
        Cmods() ;
        ~Cmods() ;
	int VerifyTarget_BQ3(centity_t *ent) ;
	void AddGlowShell_BQ3(refEntity_t *ref) ;
	int AddTarget_BQ3(centity_t *targ,centity_t * cent) ;
	int DrawEsp_BQ3(centity_t *ent,float *color,int *force) ;
	int VerifyTarget_FRZ(centity_t * ent) ;
	void AddGlowShell_FRZ(refEntity_t * ref) ;
	int AddTarget_FRZ(centity_t * targ, centity_t * cent) ;
	int DrawEsp_FRZ(centity_t * ent, float *color, int *force) ;


	typedef struct modWeapon_s

	{

		char name[32] ;

		float speed   ;

		vec3_t v      ;

	} modWeapon_t     ;


	typedef struct modSupport_s
	{
		char name[64]             ;
		modWeapon_t* weapons      ;
		int numweapons            ;
		int playerinfo            ;
		int unlagged              ;
		int deadflag              ;
		int clientinfo_distortion ;
		int  (*VerifyTarget)(centity_t* ent)   ;
		void (*AddGlowShell)(refEntity_t* ent) ;
		int  (*AddTarget)(centity_t* targ, centity_t* ent)        ;
		int  (*DrawEsp)(centity_t* ent, float *color, int* force) ;
	} modSupport_t ;



	modWeapon_t weapons_UT4[] =
{
	// char name[32] float speed       vec3_t v
	{"NONE"         ,     0.0f,	{ 0.0f, 0.0f, 0.0f	}  },
	{"KNIFE"        ,     0.0f,	{ 4.0f,	0.0f, 26.0f	}  },
	{"BERETTA"      ,     0.0f,	{ 4.0f, 0.0f, 26.0f	}  },
	{"DESERT EAGLE" ,     0.0f,	{ 4.0f, 0.0f, 26.0f	}  },
	{"SPAS-12"      ,     0.0f,	{ 0.0f,	0.0f,  5.0f	}  },
	{"MPK5"         ,     0.0f,	{ 4.0f,	0.0f, 26.0f	}  },
	{"UMP-45"       ,     0.0f,	{ 4.0f,	0.0f, 26.0f	}  },
	{"HK-69"        ,  1000.0f,	{ 0.0f,	0.0f, 30.0f	}  },
	{"LR-300"       ,     0.0f,	{ 4.0f,	0.0f, 26.0f	}  },
	{"G-36"         ,     0.0f,	{ 4.0f,	0.0f, 26.0f	}  },
	{"PSG-1"        ,     0.0f,	{ 4.0f,	0.0f, 26.0f	}  },
	{"GRENADE"      ,   500.0f,	{ 0.0f,	0.0f, 30.0f	}  },
	{"FLASH"        ,   500.0f,	{ 0.0f,	0.0f, 30.0f	}  },
	{"SMOKE"        ,   500.0f,	{ 0.0f,	0.0f, 30.0f	}  },
	{"SR-8"         ,     0.0f,	{ 0.0f,	0.0f,  5.0f	}  },
	{"AK-103"       ,     0.0f,	{ 4.0f,	0.0f, 26.0f	}  },
	{"UNKNOWN"      ,     0.0f,	{ 4.0f,	0.0f, 26.0f	}  },
	{"NEGEV"        ,     0.0f,	{ 4.0f,	0.0f, 26.0f	}  },
	{"UNKNOWN"      ,     0.0f,	{ 4.0f,	0.0f, 26.0f	}  },
	{"M4"           ,	  0.0f,	{ 4.0f,	0.0f, 26.0f	}  }
};


Now the problem is that this doesn't compile, since you cannot initialize data that is in a class....

so i thougt, OK, well, if I cannot initialize it in the declaration, then OK, I'm gonna initialize it in the constructor.

But the bad thing is, i cannot initialize this table in the constructor with a simple =, when i initialized the data in the in the class header...

so what i do is I create a new variable in the constructor, and then memcopy it's contents to the variable in the class...
which works perfectly...

I define a too large array in the class header, so i can grow my array in the constructor without having to adapt the header.
Therefore in the header i write:
#define UT4_MAX_WEAPONS 30
#define BQ3_MAX_WEAPONS 20
	modWeapon_t weapons_UT4[UT4_MAX_WEAPONS] ;
	modWeapon_t weapons_BQ3[BQ3_MAX_WEAPONS] ;

then in the constructor i do:
```



	// f*** C++ ISO forbidds allocating this in class declaration
	modWeapon_t temporary_weapons_UT4[UT4_MAX_WEAPONS] = 
	{
	// char name[32] float speed       vec3_t v
	{"NONE"         ,     0.0f,	{ 0.0f, 0.0f, 0.0f	}  },
	{"KNIFE"        ,     0.0f,	{ 4.0f,	0.0f, 26.0f	}  },
	{"BERETTA"      ,     0.0f,	{ 4.0f, 0.0f, 26.0f	}  },
	{"DESERT EAGLE" ,     0.0f,	{ 4.0f, 0.0f, 26.0f	}  },
	{"SPAS-12"      ,     0.0f,	{ 0.0f,	0.0f,  5.0f	}  },
	{"MPK5"         ,     0.0f,	{ 4.0f,	0.0f, 26.0f	}  },
	{"UMP-45"       ,     0.0f,	{ 4.0f,	0.0f, 26.0f	}  },
	{"HK-69"        ,  1000.0f,	{ 0.0f,	0.0f, 30.0f	}  },
	{"LR-300"       ,     0.0f,	{ 4.0f,	0.0f, 26.0f	}  },
	{"G-36"         ,     0.0f,	{ 4.0f,	0.0f, 26.0f	}  },
	{"PSG-1"        ,     0.0f,	{ 4.0f,	0.0f, 26.0f	}  },
	{"GRENADE"      ,   500.0f,	{ 0.0f,	0.0f, 30.0f	}  },
	{"FLASH"        ,   500.0f,	{ 0.0f,	0.0f, 30.0f	}  },
	{"SMOKE"        ,   500.0f,	{ 0.0f,	0.0f, 30.0f	}  },
	{"SR-8"         ,     0.0f,	{ 0.0f,	0.0f,  5.0f	}  },
	{"AK-103"       ,     0.0f,	{ 4.0f,	0.0f, 26.0f	}  },
	{"UNKNOWN"      ,     0.0f,	{ 4.0f,	0.0f, 26.0f	}  },
	{"NEGEV"        ,     0.0f,	{ 4.0f,	0.0f, 26.0f	}  },
	{"UNKNOWN"      ,     0.0f,	{ 4.0f,	0.0f, 26.0f	}  },
	{"M4"           ,     0.0f,	{ 4.0f,	0.0f, 26.0f	}  }
	};
	memcpy(&weapons_UT4, &temporary_weapons_UT4, sizeof(modWeapon_t) * UT4_MAX_WEAPONS) ;
	
	modWeapon_t temporary_weapons_BQ3[BQ3_MAX_WEAPONS] =
	{
		{"none"     ,	   0.0f,  { 0.0f, 0.0f,	  0.0f }  },
		{"gauntlet" ,      0.0f,  { 0.0f, 0.0f,	  0.0f }  },
		{"machine"  ,	   0.0f,  { 0.0f, 0.0f,	  0.0f }  },
		{"shotgun"  ,	   0.0f,  { 0.0f, 0.0f,	  0.0f }  },
		{"grenade"  ,	 700.0f,  { 0.0f, 0.0f,  20.0f }  },
		{"rocket"  ,	 900.0f,  { 0.0f, 0.0f, -20.0f }  },
		{"light"    ,	   0.0f,  { 0.0f, 0.0f,   0.0f }  },
		{"railgun"  ,	   0.0f,  { 0.0f, 0.0f,   0.0f }  },
		{"plasma"   ,	2000.0f,  { 0.0f, 0.0f,   0.0f }  },
		{"bfg"      ,	2000.0f,  { 0.0f, 0.0f, -20.0f }  },
		{""         ,      0.0f,  { 0.0f, 0.0f,   0.0f }  },
		{"grapple"  ,	   0.0f,  { 0.0f, 0.0f,   0.0f }  }
	};
	memcpy(&weapons_BQ3, &temporary_weapons_BQ3, sizeof(modWeapon_t) * BQ3_MAX_WEAPONS) ;

```


Then i thought here i'm gonna do just the same with the modtable

#define MOD_FUNCS(MOD) VerifyTarget_##MOD , AddGlowShell_##MOD , AddTarget_##MOD , DrawEsp_##MOD

	modSupport_t temporary_modTable[] =
	{
		 //{ "baseq3"    , weapons_BQ3, 10,  0, 0, EF_DEAD,  0, MOD_FUNCS(BQ3)  },
		 //{ "cpma"      , weapons_BQ3, 10,  0, 0, EF_DEAD,  0, MOD_FUNCS(BQ3)  },
		 //{ "q3ut4"     , weapons_UT4, 15,  0, 1, EF_DEAD, -4, MOD_FUNCS(FRZ)  },
		 //{ "freeze"    , weapons_BQ3, 10,  0, 0, EF_DEAD,  0, MOD_FUNCS(FRZ)  },
		 //{ "ufreeze"   , weapons_BQ3, 10,  0, 1,   0x100,  0, MOD_FUNCS(FRZ)  },
		 //{ "arena"     , weapons_BQ3, 10,  0, 0, EF_DEAD,  0, MOD_FUNCS(FRZ)  },
		 //{ "threewave" , weapons_BQ3, 12, 17, 0, EF_DEAD,  0, MOD_FUNCS(FRZ)  }
	};
	modTableSize = sizeof(temporary_modTable)/sizeof(temporary_modTable[0]) ;
	memcpy(&modTable, &temporary_modTable, sizeof(modSupport_t) * modTableSize) ;
	

Now of course, since I putted data and functions in my mod class, the functions VerifyTarget, AddGlowShell, AddTarget, DrawEsp
have become member functions... aaaaaaaaaaaaaargh
well, i don't want to put them in a extern "C"{} of course, since I want it in proper C++...


You understand now? Probably not too god. 
I'm gonna attach the sourcecode for the entire bot.
Compilation is broken at the moment, since it requries the mod data in some other classes, but i haven't yet finished implementing my mod class...

But you can read the source and critique it ;-)

---

### Post by dribeas on 2008-12-06
> **WitchCraft said:**
> 
65:  (xobject.*(xobject.fuptr))(199);
Now with line 65 I have some difficulties. I guessed it was something like this, but why again the xobject??? in the constructor i can call the pointer via (this->*fuptr), which is what i would expect. Why do i suddenly need a this->*(this->fuptr)? I did not create a class in a class, or did I?


The thing is that fuptr is a member variable of your class. That means that you can refer to it as this->fuptr, or for simplicity skip the this-> part whenever you are inside the class scope. Once you are out (as in main) you will have to go step by step: first xobject.fuptr that will return a member pointer, and then apply the ::* or ::-> operator on that member pointer. The inner xobject is used to access the member, and the outer xobject to dereference it with that particular instance. It might be easier to see with an example with the member pointer being outside of your class:

```

struct X {
  void f( int x );
};
int main()
{
   void (X::*the_ptr)( int ) = &X::f; // Define the member function pointer
   X x;
   (x.*the_ptr)( 5 ); // call x.f(5)
}

```

In this example, the member pointer is a local variable in the main method. From here on, if the member function were not to be a local variable, but a member variable of x, then you need to access it through the standard way: object.member_attribute.

> **WitchCraft said:**
> 
Well, I think I'm not sure about the syntax rules, because i also had a problem with:
```
 
void (X::*fuptr)(int b) ;

```
Why does it need a X::? I'd have assumed that i just need a void (*fuptr)(int b);  since it is in the class declaration, not the implementation outside the declaration...
I'd have assumed that it is like when you define functions.
In the class X you don't write void X::function(int argument), that you write in the implementation outside the class declaration, but inside???


Well, member functions are not normal function pointers. You are creating a pointer to a method inside a class, not a free function. The member function has an implicit this pointer to the instance of the class that it is being called on. If the function uses internally any data member of the object, the compiler must know what particular instance data is being read/written.

With static member functions that is not a problem. Static member functions don't have an implicit member function as they don't execute with any particular object but with all the class.

Now on your original problem. After reading your post (not really going through the code, and I must admit not really understanding all parts), I believe that it sounds like you could use a Factory / Abstract Factory. 

Once you need to implement n-different versions of the methods, you can just go ahead and do it in their own class. Provide a base class with virtual functions and then implement in different classes your particular game version details. Add in a factory method that will check the game and instead of changing function pointers as you are doing, just instantiate the class for the particular implementation.

On the initialization of your data. Is your data specific to each of the bots that you will instantiate or is it shared by all. My guess is that many of it (weapon definitions for example) are not really instance data, but should better be static data (shared by all instances of the class). If that is the case, you can use the same initialization code that C uses in your static member definition:

```

struct X // I doubt it will work if X has constructors defined, I don't remember the standard requirements for this to work
{
   int x, y, z;

  static X static_X;
};
int X::static_X = { 1, 2, 3 }; // initializes x=1, y=2, z=3

```

You are not able to use that syntax for member attributes, as you posted, though. Also note that this is performed in the place of the real definition, which in most cases will be a .cpp file. I am not sure on what the standard has to say about it, but I have seen it written in the .h some times so it might be allowed (g++ 4.0 allows it). At any rate, it must not be defined both in the class declaration and in the static variable definition.

---

### Post by WitchCraft on 2008-12-07
> **dribeas said:**
> 

Once you need to implement n-different versions of the methods, you can just go ahead and do it in their own class. Provide a base class with virtual functions and then implement in different classes your particular game version details. Add in a factory method that will check the game and instead of changing function pointers as you are doing, just instantiate the class for the particular implementation.

On the initialization of your data. Is your data specific to each of the bots that you will instantiate or is it shared by all. My guess is that many of it (weapon definitions for example) are not really instance data, but should better be static data (shared by all instances of the class). If that is the case, you can use the same initialization code that C uses in your static member definition:



Good idea, should have been mine ;-)) .

For now, added revised edition with member function pointers.

---

