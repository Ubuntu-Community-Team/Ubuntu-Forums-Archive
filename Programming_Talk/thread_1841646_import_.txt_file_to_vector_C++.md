---
title: "import .txt file to vector C++"
date: 2011-09-09
forum: Programming Talk
---

### Post by misaeltovar on 2011-09-09
ok guys i have a .txt file that has to be imported into a vector, the file looks like this

12 30 50 50
02 02 20 40
33 33 02 02
00 00 15 15
99 99 01 00

and this is my code, i would like to know what do you guys think and if im right or not bc im not sure..


#include <fstream>
#include <iostream>
#include <vector>
using namespace std;

int main() {

	// Import File & Check if read
	ifstream myfile("project2.txt",ios::in);

	if (!myfile)
	{
		cerr << "File not Read"<< endl;
		exit( 1 );
	}

	//Creating Variables & Vector
	vector<int> vec(20); 			// 20 elements

	int num;

	// Import .txt into Vector

	while(myfile){
		myfile >> num;
		vec.push_back(num);
	}


	//end
	return 0;
}

---

### Post by misaeltovar on 2011-09-09
when i go and print the number if elements in the vector it tells me theres 41.. but why 41?

cout << vec.size();

---

### Post by dwhitney67 on 2011-09-09
Here you are inserting 20 items into the vector:
```

vector<int> vec(20); 			// 20 elements

```

Now you are adding more:
```

vec.push_back(num);

```
The condition in the while loop is not appropriate because it will be true even after the 20th number has been read in.  Only when an attempt to read past the EOF occurs, does the file stream report an error, and thus you exit the while-loop.  Unfortunately, this adds a 21st entry into your vector.  So, 20 + 20 + 1 = 41.... with that +1 occurring after the final read fails.

Try something like:
```

std::vector<int> vec;

while (myfile >> num)
{
   vec.push_back(num);
}

```


P.S.  In cases where you definitely know how many items will be stored in a vector, the type of constructor that you used to initialize the number of items is ok.  But when actually adding the numbers, do not use push_back(); either use the operator[] method, or use at().  Both of these methods require that you provide an index for the offset into the vector.

---

### Post by misaeltovar on 2011-09-09
thank you soo much man!

---

### Post by Senesence on 2011-09-09
It's fine to ask questions, but I think this was one of those cases where a little bit of testing would essentially bring you to the same answer.

Using the size() method to get the element count was a good first step. The next step would be to actually print out the elements themselves.

In doing this, you would be able to see that there are exactly 20 elements in the vector before the file sequence, and it doesn't take a big jump from there to figure out that 'vec(20)' is responsible for that.

---

