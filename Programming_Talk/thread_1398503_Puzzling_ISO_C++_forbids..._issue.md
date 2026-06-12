---
title: "Puzzling ISO C++ forbids... issue"
date: 2010-02-04
forum: Programming Talk
---

### Post by Ravenshade on 2010-02-04
So I've declared the following program and compil it. Now. I get the error 

ISO C++ forbids comparison between pointer and integer

Yet I'm not using any pointers nor am I comparing anything. I simply want to input a character into a char type variable then use that variable to run an if statement. 

Any idea's? I've tried searching but nothing particularly useful via google and the tutorials I'm looking at don't seem to have a problem with the syntax I've used. 

It is specifically the emboldened line that appears to be the problem


```
int main()
{
    char run;    
    cout << "Run Program? ('y' or 'n')\n";
    cin >> run;

   ** if (run==y)** //run what's in the program
    {
        for (int n=0; n<10; n++)
        {
            cout << n << "\n";
        }
        return 0; //Program finished
    }
    else
    {
        return 0; //Program doesn't want to run so Quit
    }
    
    return 0; //Quit!
}
```

---

### Post by doas777 on 2010-02-04
you will have to cast your input as a char. cin specifies a stream iirc so when you eval it, it comes out as a int that is the ascii val for your char. you will also have to wrap the 'y' in single quotes like this, so it knows it's a char.

if(run == 'y')

disclaimer, it's been years and years since i touched c++.

---

### Post by Ravenshade on 2010-02-04
but I want to input a Char, specifically y or n, but anything other single char is allowed. 

cin should be putting that entered value into the variable. The only issue I see is that cin might naturally be trying to put in an integer rather than anything that's used. 

Otherwise I have not a clue what you mean. >.<

Edit!

Genius. Syntax error ^_^ thanks muchly

---

