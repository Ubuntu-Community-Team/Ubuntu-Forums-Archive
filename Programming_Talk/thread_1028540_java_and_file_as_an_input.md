---
title: "java and file as an input"
date: 2009-01-02
forum: Programming Talk
---

### Post by babacan on 2009-01-02
Greetings
I am trying to find the way to read a file line by line and use values of each line as input for the program inside the main method.

For instance lets say I make my own square method such as

```
static int mysqr(int a){
return a*a;
}

```

and say i have input.txt that contains:
```

1
2
3
4
```

so I want to generate output.txt such that each line contains the computed numbers of input.txt such as:
```
1
4
9
16
```

I will be greatful how to achieve such in java.

Best regards.

---

### Post by Delever on 2009-01-02
For example, look here [http://www.javacoffeebreak.com/java103/java103.html](http://www.javacoffeebreak.com/java103/java103.html)

P.S. I entered your thread title into [http://www.google.com](http://www.google.com) search engine.

---

### Post by PaulM1985 on 2009-01-02
You could use the scanner class to read the file, convert the line to an appropriate number type, int, double etc, and output to the file as mentioned from the link in the above post.

You could use 

while(myScanner.hasNextLine())
{
myScanner.readLine();

//code for converting

//code for manipulating the numbers

//and now output

}

remember to close buffers and catch all necessary exceptions when reading/writing files.

Hope this helps

Paul

---

