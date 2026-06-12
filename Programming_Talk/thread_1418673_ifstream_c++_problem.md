---
title: "ifstream c++ problem"
date: 2010-02-28
forum: Programming Talk
---

### Post by chris200x9 on 2010-02-28
My ifstream is broken plain and simple. I've followed many tutorials, I've even posted here and everything looks right. I'm begging someone find what's wrong with this:
```
 #include <iostream>
#include <fstream>
using namespace std;
int main(int argc, char** argv)
{
	ifstream inData;
	inData.open("out.txt");
int matrix2[9][9];
int counter = 0;
	int i =0;
	while(!inData.eof())
	{
	while (i < 9)
	{
		while (counter < 9)
		{
			
	 inData >> matrix2[i][counter];
	counter++;
}
counter = 0;
i++;
}
}
inData.close();
	cout << matrix2[0][0];
	
	return 0;
}

```

here is the contents of out:
```
 0 3 0 9 0 2 0 4 0
6 0 0 0 0 0 0 0 5
0 0 0 0 1 0 0 0 0
8 0 0 2 0 3 0 0 7
0 0 4 0 5 0 6 0 0
9 0 0 7 0 8 0 0 2
0 0 0 0 9 0 0 0 0
7 0 0 0 0 0 0 0 1
0 5 0 6 0 4 0 9 0
``` 
When I run the program nothing happens, I have to hit control c.

---

### Post by chris200x9 on 2010-02-28
I have found a workaround of just reading the file into an array, but I still don't know exactly why the above does not work.

---

### Post by MindSz on 2010-02-28
I believe you need to reset i

```
#include <iostream>
#include <fstream>

using namespace std;

int main(int argc, char** argv)
{
  ifstream inData;
  inData.open("out.txt");
  int matrix2[9][9];
  int counter = 0;
  int i =0;

  while(!inData.eof()) {
    while (i < 9) {
      while ((!inData.eof())&&(counter < 9)) {
	inData >> matrix2[i][counter];
	counter++;
      }
      counter = 0;
      i++;
    }
    i = 0;
  }

  inData.close();
  cout << matrix2[0][0];
  
  return 0;
}

```

---

### Post by chris200x9 on 2010-02-28
> **MindSz said:**
> I believe you need to reset i

```
#include <iostream>
#include <fstream>

using namespace std;

int main(int argc, char** argv)
{
  ifstream inData;
  inData.open("out.txt");
  int matrix2[9][9];
  int counter = 0;
  int i =0;

  while(!inData.eof()) {
    while (i < 9) {
      while ((!inData.eof())&&(counter < 9)) {
	inData >> matrix2[i][counter];
	counter++;
      }
      counter = 0;
      i++;
    }
    i = 0;
  }

  inData.close();
  cout << matrix2[0][0];
  
  return 0;
}

```

ah thanks!

---

