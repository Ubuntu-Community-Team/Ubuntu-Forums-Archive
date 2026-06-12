---
title: "g++ error I can't figure out"
date: 2007-09-11
forum: Programming Talk
---

### Post by Mardok45 on 2007-09-11
Before I start posting snippets of my code, does anyone happed to know what this error means:

Request for member 'function name' in 'class name', which is of non-class type.

---

### Post by aks44 on 2007-09-11
You tried to call "function name" on an object of type "class name" but you messed up somewhere because "class name" is not a class (is it a builtin-type??).

Better post some code...

---

### Post by Mardok45 on 2007-09-11
This is my OBJLoader header file:

class OBJLoader
{
public:
	OBJLoader();
	~OBJLoader();
	bool load(char *file);
	void render();

private:
	std::fstream file;

	std::vector<face*> faces;
	std::vector<texture*> textures;
	std::vector<vertex*> vertices;

	void readLine(std::string&);

	void readFace(std::string);
	void readVertex(std::string);
	void readTexture(std::string);
};

Now we jump over to my main file:

OBJLoader cube();

int main(int argc, char** argv)
{
     cube.load("cube.obj");//request for member &#8216;load&#8217; in &#8216;cube&#8217;, which is of non-class type &#8216;OBJLoader ()()&#8217;

     return 0;
}

There's like 90 lines of code in my main function and 200+ lines in my OBJLoader defining the functions, which is why I don't want to post my code :\
Plus, I compiled this in Dev-C++ and Visual Studio in Windows and it all compiled fine...

---

### Post by aks44 on 2007-09-11
> **Mardok45 said:**
> OBJLoader cube();

The compiler sees that as a forward-declaration of a function (function *cube* which takes no arguments and returns an instance of *OBJLoader*) rather than a variable definition (variable *cube* of type *OBJLoader* that uses the default constructor).

Since you're using the default constructor, just ditch the parenthesis and you'll be fine:

```
OBJLoader cube;
```


EDIT: Note: this ambiguity doesn't happen with anything else than the default constructor, since the compiler is then able to tell the difference between a function declaration and a variable definition, eg:

OBJLoader cube(TypeName paramName); // forward-declaration of a function, takes 1 param of type *TypeName* and returns an *OBJLoader* instance
OBJLoader cube(TypeName); // same here, since the compiler can resolve *TypeName* to a type name

versus

OBJLoader cube(argument); // variable definition, type *OBJLoader* using a custom constructor (since the compiler can resolve *argument* to some other variable)


EDIT again:
> **Mardok45 said:**
> Plus, I compiled this in Dev-C++ and Visual Studio in Windows and it all compiled fine...
Visual Studio is not a reference when it comes to standards correctness (dunno about Dev-C++, but it seems it made the same error). g++ is right on this one, the C++ standard mandates that behaviour (although I won't bother to search & quote chapter and verse).

---

### Post by gnusci on 2007-09-11
Very funny... ;)

> **aks44 said:**
> You tried to call "function name" on an object of type "class name" but you messed up somewhere because "class name" is not a class (is it a builtin-type??).

Better post some code...

ok here is my answer, you have to pay attention to the important changes I also did some modifications to be able to compile it, here it is:

[PHP]

using namespace std;

class OBJLoader
{
public:
	OBJLoader(){};
	~OBJLoader(){};
	
	bool load(char *file); //<------ file
	void render();
	
private:

	fstream file; //<------ file
	
	vector<face*> faces;
	vector<texture*> textures;
	vector<vertex*> vertices;
	
	void readLine(string&);
	
	void readFace(string);
	void readVertex(string);
	void readTexture(string);
};


OBJLoader cube; //<------ without "()"

int main(int argc, char** argv)
{
	cube.load("cube.obj"); //I get the error here
	return 0;
}
[/PHP]

---

### Post by aks44 on 2007-09-11
@gnusci:

1. good point about the file (argument) vs file (member) name clash. I didn't notice it at first glance. :) I guess it's just another reason to stick to strict naming schemes (as far as I'm concerned, all data members start with **m_** )

2. for once that someone doesn't use **using namespace**, please, I beg you, please don't give him/her bad habits. **using namespace** is one of the very few features (the only one I can think of ATM) that really should be removed from the language, it totally denies the benefits of namespaces...

---

