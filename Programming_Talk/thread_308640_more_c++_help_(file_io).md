---
title: "more c++ help (file io)"
date: 2006-11-28
forum: Programming Talk
---

### Post by Choad on 2006-11-28
```

bool LoadLevel(std::string filename)
{
	std::string line;
	std::ifstream levelData(filename);
	/*if (levelData.is_open())
	{
		while (!levelData.eof())
		{
			std::getline(levelData, line);
			printf(line);
		}
		levelData.close();
	} else 
	{
		printf("Unable to open file " + filename);
		return false;
	}*/
	return true;
}

```

that is not compiling. most of the code is commented out to narrow it down. anyone tell me why?

i have #included fstream and iostream

```

richard@richard-laptop:~/Desktop$ g++ `sdl-config --cflags --libs` -o maze maze.cpp -lSDL -lSDL_image
maze.cpp: In function ‘bool LoadLevel(std::string)’:
maze.cpp:80: error: no matching function for call to ‘std::basic_ifstream<char, std::char_traits<char> >::basic_ifstream(std::string&)’
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/fstream:442: note: candidates are: std::basic_ifstream<_CharT, _Traits>::basic_ifstream(const char*, std::_Ios_Openmode) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/fstream:428: note:                 std::basic_ifstream<_CharT, _Traits>::basic_ifstream() [with _CharT = char, _Traits = std::char_traits<char>]
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/iosfwd:89: note:                 std::basic_ifstream<char, std::char_traits<char> >::basic_ifstream(const std::basic_ifstream<char, std::char_traits<char> >&)

```

---

### Post by civilian on 2006-11-28
look for examples of an ifstream declaration, and make sure you read the man page for it, its always useful. Sorry if its not helpful at all, I'm usually better at this but I'm having a blank.

---

### Post by Choad on 2006-11-28
i am following a tutorial

the only difference is it used namespace std instead of std::

```

using namespace std;

int main () {
  string line;
  ifstream myfile ("example.txt");
  if (myfile.is_open())
  {
    while (! myfile.eof() )
    {
      getline (myfile,line);
      cout << line << endl;
    }
    myfile.close();
  }

  else cout << "Unable to open file"; 

  return 0;
}

```

that compiles fine

---

### Post by hod139 on 2006-11-28
> **Choad said:**
> ```

bool LoadLevel(std::string filename)
{
    std::string line;
    std::ifstream levelData(filename);

    /* snip */
}

```that is not compiling. most of the code is commented out to narrow it down. anyone tell me why?

i have #included fstream and iostream

```

You need to change
[code] std::ifstream levelData(filename);
```
to 
```
std::ifstream levelData(filename.c_str());
```

Also, you should consider passing the filename string as a const reference
```

bool LoadLevel(const std::string &filename)

```

---

### Post by Choad on 2006-11-28
> **hod139 said:**
> You need to change
```
 std::ifstream levelData(filename);
```
to 
```
std::ifstream levelData(filename.c_str());
```

Also, you should consider passing the filename string as a const reference
```

bool LoadLevel(const std::string &filename)

```
thankyou!

may i ask why i should do the second thing you mentioned? (must absorb all c++ knowledge lol)

---

### Post by hod139 on 2006-11-28
> **Choad said:**
> may i ask why i should do the second thing you mentioned? (must absorb all c++ knowledge lol)

The second thing I mentioned consists of two parts: 
 1) pass by reference versus pass by value 
 2) const-correctness
First the difference between pass by reference and pass by value.  
     ```

     bool LoadLevel(std::string filename) // You wrote pass by value

```and
```

bool LoadLevel(const std::string &filename) // This is pass by reference (note the &) 
```In pass by value, a temporary copy of the object is created, and the temporary is passed to the function.  Any changes you make to the function parameter (filename in this case) only persist during that function call.  With pass by reference, you are actually passing a pointer of the object to the function.   Now any changes you make to the argument will persist after the function exists, which brings me to part 2) const-correctness.

Since you don't want any changes to occur to filename, I added the keyword const, which tells the compiler to throw an error if anything tries to change the value of the variable.

Why pass by const reference instead of passing by value, speed.  Pass by const reference requires passing 4 bytes (the size of a pointer in a 32 bit machine) instead of creating a temporary copy of the object (which could be a large class etc) and passing the copy.

---

### Post by civilian on 2006-11-28
Yes thats what it is, I tend to complicate my life when I don't see the "using namespace std;" statement and then think its some very complicated code, sorry I didnt get it before.

---

### Post by Choad on 2006-11-28
> **hod139 said:**
> The second thing I mentioned consists of two parts: 
 1) pass by reference versus pass by value 
 2) const-correctness
First the difference between pass by reference and pass by value.  
     ```

     bool LoadLevel(std::string filename) // You wrote pass by value

```and
```

bool LoadLevel(const std::string &filename) // This is pass by reference (note the &) 
```In pass by value, a temporary copy of the object is created, and the temporary is passed to the function.  Any changes you make to the function parameter (filename in this case) only persist during that function call.  With pass by reference, you are actually passing a pointer of the object to the function.   Now any changes you make to the argument will persist after the function exists, which brings me to part 2) const-correctness.

Since you don't want any changes to occur to filename, I added the keyword const, which tells the compiler to throw an error if anything tries to change the value of the variable.

Why pass by const reference instead of passing by value, speed.  Pass by const reference requires passing 4 bytes (the size of a pointer in a 32 bit machine) instead of creating a temporary copy of the object (which could be a large class etc) and passing the copy.
thanks! that makes alot of sense! even tho im drunk i still understand lol

---

