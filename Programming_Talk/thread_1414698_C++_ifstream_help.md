---
title: "C++ ifstream help"
date: 2010-02-23
forum: Programming Talk
---

### Post by chris200x9 on 2010-02-23
I have a function ```
 bool checksudoku()
{
ifstream inData;

inData("out.txt");
int matrix2[9][9];
int counter = 0;
	int i =0;
	while (i < 9)
	{
		while (counter < 9)
		{
			
	 inData >> matrix2[i][counter];
	counter++;
}
//inData >> endl;
counter = 0;
i++;
}
int counter1 = 0;
	int i1 =0;
	while (i < 9)
	{
		while (counter < 9)
		{
			
	 cout << matrix2[i][counter];
	counter++;
}
 cout << endl;
counter1 = 0;
i1++;
}
inData.close();
}
```

that just reads a sudoku from an output file and prints it to check. My question is why do I keep getting the following error: ```
 error: no match for call to ‘(std::ifstream) (const char [8])’
```

---

### Post by Simon17 on 2010-02-23
```

ifstream inData;
inData("out.txt");
```
This is a problem.

Did you mean to do this?

```
ifstream inData("out.txt");
```

Ask if you don't understand the difference.

---

### Post by chris200x9 on 2010-02-23
> **Simon17 said:**
> ```

ifstream inData;
inData("out.txt");
```
This is a problem.

Did you mean to do this?

```
ifstream inData("out.txt");
```

Ask if you don't understand the difference.

I don't understand, this is school work by the way (sorry for not mentioning it earlier) and my way was the way on the powerpoint from my instructor, I also don't get it because ofstream worked when i did it that way. Not trying to be confrontational or "I did it right whatever!" I'm sorry if that how it comes across (because it does a little in my opinion) I'm just theroughly confused, and very greatful.

---

### Post by Simon17 on 2010-02-24
Are you sure you copied it correctly? Are you sure it wasn't something like
```

inData.[COLOR="DarkRed"]open[/COLOR]("out.txt");

```
?

Parenthesis following the variable name in a DECLARATION calls the appropriate constructor. For example
```

int i; // creates an int with an unspecified value
int j(4); // creates an int with the value 4.
i(4); // Error. Doesn't make sense because i is not a function or function object.
// Likewise,
ifstream inData("in.txt"); // creates an ifstream using the constructor ifstream(const char*)
ofstream outData; // creates an ofstream using the default constructor.
outData("out.txt"); // WRONG! 
outData.open("out.txt"); // right!

```

---

### Post by chris200x9 on 2010-02-24
Oh oops, I feel silly, yes I copied it wrong. Thank you so much.

---

