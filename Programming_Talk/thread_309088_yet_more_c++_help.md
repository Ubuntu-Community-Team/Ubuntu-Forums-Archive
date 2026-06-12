---
title: "yet more c++ help"
date: 2006-11-29
forum: Programming Talk
---

### Post by Choad on 2006-11-29
```
bool LoadLevel(std::string filename)
{
	std::string line;
	std::ifstream levelData(filename.c_str());
	int i, o = 0;
	char block;
	if (levelData.is_open())
	{
		while (!levelData.eof())
		{
			std::getline(levelData, line);
			[B]block = line[i];
			while (!block == NULL)
			{
				if (block == "1")[/B]
				{
					levelLayout[i][o] = true;
				} else
				{
					levelLayout[i][o] = false;
				}
			}
		o += 1;
		}
		levelData.close();
	} else 
	{
		std::cout << "Unable to open file " << filename << std::endl;
		return false;
	}
	return true;
}
```

the bit in bold is the code in question...

```
richard@richard-laptop:~/Desktop$ g++ `sdl-config --cflags --libs` -o maze maze.cpp -lSDL -lSDL_image
maze.cpp: In function ‘bool LoadLevel(std::string)’:
maze.cpp:90: warning: NULL used in arithmetic
maze.cpp:92: error: ISO C++ forbids comparison between pointer and integer

```

pretty self explanatory really.... i just have no idea lol. any help much appreciated.

---

### Post by kinson on 2006-11-29
I'm not very good at this :p

But try:

```
while (block != NULL)
```

Considering "block" is a char, I don't think you can "Not Char".

give it a try and see if it works.

Cheers,
Kinson :)

---

### Post by Choad on 2006-11-29
its not "not"ing a char, its "not"ing the evaluated expresion (ie true or false)

(i tried it and it made no difference :()

---

### Post by kinson on 2006-11-29
<deleted>

Kinson

---

### Post by Gustav on 2006-11-29
Since block is char (and not a pointer) it can never be NULL, you should compare it with the end character of the line (probably '\n').

You should compare block with '1' instead of "1" since "1" is a string (or actually an array (or a pointer to a char)) and '1' is a char

---

### Post by Gustav on 2006-11-29
And you should probably increase i for each loop in the while (!block == NULL) loop. (And read the next char)

---

### Post by kinson on 2006-11-29
> **Gustav said:**
> Since block is char (and not a pointer) it can never be NULL, you should compare it with the end character of the line (probably '\n').


I think the end of the string is "\0" :-k 

[http://cplusplus.com/doc/tutorial/ntcs.html](http://cplusplus.com/doc/tutorial/ntcs.html)

Cheers,
Kinson

---

### Post by Gustav on 2006-11-29
> **kinson said:**
> I think the end of the string is "\0" :-k 

[http://cplusplus.com/doc/tutorial/ntcs.html](http://cplusplus.com/doc/tutorial/ntcs.html)

Cheers,
Kinson

Yes, you might be right (I don't know how std::getline() works :))

---

### Post by kinson on 2006-11-29
> **Gustav said:**
> Yes, you might be right (I don't know how std::getline() works :))

Lol, I've no idea either. My c++ sucks :p

Kinson

---

### Post by Choad on 2006-11-29
thanks all!

---

