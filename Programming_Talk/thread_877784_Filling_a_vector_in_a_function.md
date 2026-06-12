---
title: "Filling a vector in a function"
date: 2008-08-02
forum: Programming Talk
---

### Post by thelamb on 2008-08-02
Hello all,

I have been looking through dozens of forums to find my answer, found alot, tried it but it never worked for me so I decided to make my own thread.

First off, I am trying to fill a vector with objects, two functions are of importance:

```
void startServerScreens(vector<CGame*>& retVal)
{
	vector<CGame*> v;
        v.push_back(new CGame(&serversh, &game_id));

	(retVal).swap(v);
        (*retVal.at(0)).readLog(); (1)
}

int main(int argc, char *argv[])
{
	vector<CGame*> v;
	startServerScreens(v);
        (*v.at(0)).readLog(); (2)
}
```

serversh and game_id are set in startServerScreens aswell but I left them out to make things more readable.
readLog is part of the CGame class, it reads a logfile and outputs something.

When I run the program, line (1) is executed properly, I get the result that I expect from readLog();
However, line (2) gives no errors but no output from readLog() aswell.

So for some reason, the value-pointed-by retVal is destroyed when the startServerScreens function ends.

If I am right, the retVal.swap(v) is doing something, otherwise I would get a segmentation fault in line (2) wouldn't I?

Also, I do not fully understand this:
void startServerScreens(vector<CGame*>& retVal)

If I remove the & from this line I get no compile error so I am kind of in the dark on what the point is.

As far as I know, the idea of what it should do is:
1 - Create vector<CGame*> v
2 - Pass the address of v to startServerScreens()
3 - Fill another vector<CGame*> v
4 - Swap v with retVal
5 - v in startServerScreens is destroyed

Any push in the right direction is much appreciated.

I got the above solution from here [http://ubuntuforums.org/showthread.php?t=643484](http://ubuntuforums.org/showthread.php?t=643484)

---

### Post by jbrackett on 2008-08-02
I've tried to recreate your problem with the code below, but this code works.  Maybe the problem lies elsewhere in the code?

The reason we need to pass a reference is because the parameter we are passing is what we want filled.  If we just passed by value then v in main will never be changed.

```
#include <vector>
#include <iostream>

#include "myclass.h"

int stuff;
MyClass::MyClass(int i) {
	stuff = i;
}
void MyClass::print() {
	std::cout << (stuff);
}

void swapIt(std::vector<MyClass*>& vRef)
{
  std::vector<MyClass*> vLocal;
  vLocal.push_back(new MyClass(1));

  vRef.swap(vLocal);
  (*vRef.at(0)).print();
}

int main(int argc, char *argv[])
{
  std::vector<MyClass*> v;
  swapIt(v);
  (*v.at(0)).print();
}
```

---

### Post by Jessehk on 2008-08-02
Some may argue with me, but I think passing in a reference to the vector is premature optimization. Feel free to return it from the function. Yes, there will be a copy made, but I don't think it will affect speed too much.

The swap nonsense looks completely unnecessary.
Also, is there a particular reason you're storing pointers instead of objects?
```

#include <vector>

std::vector<CGame> startServerScreens() {
    std::vector<CGame> v;

    v.push_back( CGame( &serverh, &game_id ) );
    v[0].readLog();
    return v;
}

int main() {
    std::vector<CGame> v = startServerScreens();
    v[0].readLog();
}

```

---

### Post by thelamb on 2008-08-02
You are right jbrackett, the problem lies in my class.
I created a new function print(); in  my class that just prints "Hello". If I call this function from the main, everything works fine.

So the problem lies in readLog(), and something has changed.. I get a segmentation error now when I try to call readLog() from the main.

Here is the readlog:

> 
	// Logfile variables
	string logpath = "/home/GVSites/org.gv.ucon/serverfiles/" + *CGame::game_id + "/" + *CGame::serversh + ".log"; (1)
	cout << logpath << endl;
	ifstream fplog(logpath.c_str());
	string buffer;

	// Offsets for string searching
	size_t offset, offset_slot, offset_1, offset_2, offset_len;

	// Violation variables
	string violExclude, violGameid, violPeriod, violType, violNum;

	// Player info variables
	string playGuid, playSlot, playName, playIp, md5_filename;
	
	// Command to send to gameserver
	string strCmd;
	string* pstrCmd;
	pstrCmd = &strCmd;

	string searchStr[3] = { "GUID Computed", ") MD5Tool Mismatch:", "| VIOLATION (" }; // Strings that we are searching for in the logs
	
	while( getline(fplog, buffer) ) // Read the logfile and dump it in buffer
	{
		for( int i=0; i<=1; i++)
		{
                  // In here I search the buffer for some stuff, but the segmentation fault is before this line
		}
	}
	return buffer;
}

The segmentation error occurs at line (1), if I remove the CGame::serversh and CGame::game_id then everything works.

Now, I don't understand why ;).

Remember my startServerScreens() function, filled the vector with 'new CGame' - so here the object is created and its constructor is called, the constructor is this:

> CGame::CGame(string* serversh, string* game_id)
{
	sleep(1);
	CGame::serversh = serversh;
	CGame::game_id = game_id;
}

And the CGame::serversh variable is declared as:

> class CGame
{
private:
	string* serversh;
	string* game_id;
etc.


So when the constructor is called it saves the serversh and game_id. But after we leave the function startServerScreens() these are destroyed? 

I might be completely noob here but I thought this was the correct way ;), apparently not so.

I was just thinking, is it because the variables are private? So only the scope of these variables is startServerScreens() ?

@Jessehk :
I have no idea about the size of this vector yet. It will have about 400 objects now but this will grow in time. 

EDIT: Guess I wasnt right about the private part.. still segmentation fault when I make them public

---

### Post by dwhitney67 on 2008-08-02
[PHP]void startServerScreens(vector<CGame*>& retVal)
{
	vector<CGame*> v;
        v.push_back(new CGame(&serversh, &game_id));

	(retVal).swap(v);
        (*retVal.at(0)).readLog(); (1)
}[/PHP]

Looking at the code above, I can only conclude that you are a newbie to C++.  I also think that this snippet of code can lead to memory leaks.

I agree with the post from Jessehk, minus the comment concerning "premature optimization" wrt passing the vector by reference.

Here's a cleaned up version, although I am not certain if you need the retVal vector cleared out, and I am not certain as to the point of calling readLog().
[PHP]void startServerScreens(vector<CGame>& retVal)
{
  retVal.clear();  // if this is called, then retVal will have at most one
                   // element (which is inserted next)

  retVal.push_back( CGame( &serverSh, &game_id ) );

  retVal.at(0).readLog();  // And the point of this is...???
}[/PHP]

Your original code will leave a memory leak when you swap one vector for the other.  Even clearing the vector (as I have shown above) would not free the memory that you show being allocated.  You would have needed to iterate over the locally declared vector, 'v', after the swap(), in order to deallocate the memory properly.

If you really want to write better C++ code, avoid using global variables, such as serverSh and game_id.  It also confuses me why you are passing them via their address.  Why not pass them by reference?

P.S.  Btw, here's the definition of the std::vector's swap method:
```
Swap content

Exchanges the content of the vector by the content of vec, which is another vector of the same type. Sizes may differ.

After the call to this member function, the elements in this container are those which were in vec before the call, and the elements of vec are those which were in this. All iterators, references and pointers remain valid for the swapped vectors.

Notice that a global algorithm function exists with this same name, swap, and the same behavior.
```

P.S.S.  I have no idea what functionality is being performed by the CGame() constructor.  If it is allocating memory, then be sure to deallocate it in the destructor.

---

### Post by dwhitney67 on 2008-08-02
Ah, I just read the OP's last post more carefully.  Wrt to CGame, try this:
[PHP]class CGame
{
  public:
    CGame( const std::string &serversh, const std::string &gameID );

    // etc...

  private:
    const std::string & m_serversh;
    const std::string & m_gameID;
    // etc...
};

CGame::CGame( const std::string &serversh, const std::string &gameID )
  : m_serversh( serversh ),
    m_gameID( gameID )
{
  // etc.  (if anything)
}
[/PHP]

---

### Post by thelamb on 2008-08-02
> **dwhitney67 said:**
> 
Looking at the code above, I can only conclude that you are a newbie to C++.

You are quite right with your conclusion ;).

It has been on my todo list for a while now to read up on memory management in C++, I guess this would be a good time to actually do it. I don't study anything related to programming, just like doing it as a hobby and untill now I never really bothered what happens to allocated memory, but that will change. 

Thank you all for your help.

---

