---
title: "C++: cin.getLine -&gt; not found"
date: 2006-12-19
forum: Programming Talk
---

### Post by Ben Sprinkle on 2006-12-19
Guys, I have a program that uses a string, why won't this work?
```

#include <iostream>

using namespace std;

int main() {
char c[20];
cin.getLine(c, 20, '\n');
}

```
Shouldn't that work? It says getLine not found in cin.

---

### Post by lnostdal on 2006-12-19
> **Goat Spirit said:**
> Guys, I have a program that uses a string, why won't this work?
```

#include <iostream>

using namespace std;

int main() {
char c[20];
cin.getLine(c, 20, '\n');
}

```
Shouldn't that work? It says getLine not found in cin.


```

lars@ibmr52:~$ cat blah.cpp 
#include <iostream>
#include <string>

using namespace std;

int main()
{
        string s;
        getline(cin, s);
        cout << "you typed: " << s << endl;
        return 0;
}
lars@ibmr52:~$ g++ -Wall -g blah.cpp -o blah && ./blah
Hello?
you typed: Hello?

```

---

### Post by Ben Sprinkle on 2006-12-19
Thanks, do you know how to clear cin? cin.clear(); doesn't do it. I need cin to = "".

---

### Post by slavik on 2006-12-19
cin is an istream type ...

---

### Post by Ben Sprinkle on 2006-12-19
What's that mean?
How do I clear it?

---

### Post by slavik on 2006-12-20
cin is an istream, an istream type is for input streams, which is ways to get input ...

cin is defined to be the standard input.

when you do cin>>var; it will check the type of var and read input into it. since you can't really flush the input buffer, after reading a variable, you can read char by char until EOF is returned ...

---

### Post by Ben Sprinkle on 2006-12-20
How?
Give me an example to clear it please. :)

---

### Post by po0f on 2006-12-20
Goat Spirit,

If you're using C++, why aren't you using std::string?  And the following code behaves the way you would expect it to:
```
[FONT="Courier New"]#include <iostream>
#include <string>

int main() {
    std::string s;
    std::cin >> s;

    return 0;
}[/FONT]
```

getline() by default uses '\n' as a delimiter character, but I really don't know if it is taken out of the stream or discarded.  I have always used "std::cin >> variable" to get input, which works.

---

### Post by lnostdal on 2006-12-20
> **po0f said:**
> Goat Spirit,

If you're using C++, why aren't you using std::string?  And the following code behaves the way you would expect it to:
```
[FONT="Courier New"]#include <iostream>
#include <string>

int main() {
    std::string s;
    std::cin >> s;

    return 0;
}[/FONT]
```

getline() by default uses '\n' as a delimiter character, but I really don't know if it is taken out of the stream or discarded.  I have always used "std::cin >> variable" to get input, which works.

Try reading in both your first and surname in one go using cin >> variable.

---

### Post by po0f on 2006-12-20
lnostdal,

Goat Spirit was just trying to read in one variable, so I posted an example that did the same.  I know that after the space, no more input will be read in, if that's your point.

---

### Post by Ben Sprinkle on 2006-12-20
Thanks all.

---

