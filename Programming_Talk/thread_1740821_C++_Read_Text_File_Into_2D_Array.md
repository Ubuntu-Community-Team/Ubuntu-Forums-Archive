---
title: "C++ Read Text File Into 2D Array"
date: 2011-04-27
forum: Programming Talk
---

### Post by KAISER91 on 2011-04-27
I'm absolutely stumped on how to do this. 

Basically, I'm supposed to write a function that reads a file ("Sample.txt") into a 2D array and determines the number of entries(rows). The number of entries must be less than or equal to 200. 


For a 2D array will this be a correct header to use?

```
int readfile(double xy[][200], char filename[])
```


```
int main()

	
{
	
	fstream file("Sample.txt", ios::in);

	int row = 0;
	int col = 0;

	file >> row >> col;

	cout << "row = " << row << ", col = " << col << endl;

	return 0;
}
```



The "Sample.txt" file reads something like this;


1	  3
2	  4
3	  5
4	  8
5	  11


Help will be appreciated.

---

### Post by dwhitney67 on 2011-04-27
A 2-D array of int values looks like this:
```

const size_t MAX = 200;

int array[MAX][MAX];

```
Please complete your homework on your own using the hint above.

---

