---
title: "expected : or ; before { token error"
date: 2012-11-20
forum: Programming Talk
---

### Post by hatsoff on 2012-11-20
void enqueue(const string& name, const int age)
    {
        node* newnode = new node(); // at this place
        newnode->set(name, age);
        newnode->setnext(NULL);
        rear->setnext(newnode);
        rear = newnode;
        size++;
    }

---

### Post by dwhitney67 on 2012-11-20
> **hatsoff said:**
> void enqueue(const string& name, const int age)
    {
        node* newnode = new node(); // at this place
        newnode->set(name, age);
        newnode->setnext(NULL);
        rear->setnext(newnode);
        rear = newnode;
        size++;
    }

In C++, if a constructor does not take any parameters, you do not specify the braces; otherwise the declaration (albeit in error) appears as if you are attempting to call 'new' on a function.

Change your statement to be:
```

node* newnode = new node;

```

P.S.  Always post code in CODE tags -- so as to preserve code formatting.

---

### Post by hatsoff on 2012-11-20
it did not solve the problem still getting same error.

---

### Post by spjackson on 2012-11-20
More context is needed. The error lies outside the fragment you have posted.

---

### Post by hatsoff on 2012-11-20
after changes ,it compiled right away but crashing, when i add name

---

### Post by hatsoff on 2012-11-20
i think there is problem with getline function please see this am i doing right?
[HTML] do
            {
                
                cout << "Enter the name of classmate " << endl;
                getline(cin, nameofclassmate);
                cout << "Enter the age " << endl;
                cin >> ageofclassmate;
                queue1.enqueue(nameofclassmate, ageofclassmate);
                cout << "do you want to add more : (y/n)";
                cin >> input;
            } while (input == 'y' || 'Y');
[/HTML]

---

### Post by spjackson on 2012-11-20
In the [previous thread]("http://ubuntuforums.org/showthread.php?t=2085853") dwhitney67 wrote
> 
1. Acquiring raw input from the command line. Don't assume cin will flush input stream of newline characters (ie <Enter> key) that you input. Using getline() is a good choice.

2. Don't assume user will start adding nodes. Check the validity of your queue's pointers before attempting to access them.

You need to pay attention to both of these pieces of advice.

Hint: what is the value of rear when you first do this?
```

rear->setnext(newnode);

```

Note that this loop runs forever:
```

do {
}
while (input == 'y' || 'Y');

```

I'm sure that there are many more mistakes, but you need to do your own homework.

---

