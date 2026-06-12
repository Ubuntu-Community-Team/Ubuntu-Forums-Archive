---
title: "ASCII linked list conversion"
date: 2012-04-24
forum: Programming Talk
---

### Post by tcebak on 2012-04-24
so i have the user input a char and then convert it to ASCII (int=char) and run commands on the int value
example
```
void LList::Menu(){
        //This displays the vigesimal number that is current. then ask
        //for a user input.

        char useranswer;
        int answer;

        answer=0;


        cout<<"Current vigesmial number is:   ";
        Print();
        cout<<endl;

        cout<<endl;
        cout<<"Command (h for help) : ";
        useranswer=Read_element();
        answer=useranswer;


        if ((answer == 101) || (answer == 69))
                Vigesimalinput();
        else if ((answer == 97) || (answer == 65 ))
                AddVigesimal();
        else if ((answer == 109) || (answer == 77 ))
                MultiplyVigesimal();
        else if ((answer == 104) || (answer == 72))
                HelpMenu();
        else if ((answer == 113) || (answer == 81))
                Menu();
        else
                cout<<"Invalid menu option (h for help)""\n"<<endl;
                Menu();
        }

```

and then i will want to display them but as the original char value
```
void LList::Print(){
        //Pre; The N.O LList is valid
        //Post: the N.O LList is unchaged and its elements have been
        //      displayed 

        char letter;
        int val;
        listnode* temp;

        temp=head;

        while(temp != NULL){
                temp -> data=letter;

                cout<<temp -> data;
                temp=temp -> next;              //pointer increament
                }

```

as you can tell it's not right
i'm writing a calculator for a 20 base number system (0-9 and a-j)
any insight?

---

### Post by ofnuts on 2012-04-24
1) Your code would be much more readable using a switch statement (and you don't need to convert the char to int):
```

switch (useranswer)
{
    case 'I':
    case 'i':
        Vigesimalinput();
        break;

/// other cases left as an exercise

    default:
        cout<<"Invalid menu option (h for help)""\n"<<endl; 
}

```

2) You don't show what your list looks like, what it contains, and how you build it, which could be the source of your problems. 
3) You can iterate your list in a much more readable fashion using a for loop:
```

for (ListNode current=head;current != NULL; current=current->next) {
   cout << current -> data
}

```

- use meaningful variable names (avoid "temp")
- Capitalize class/type names: ListNode
- Don't add variables just to change types, many type conversions are implicit, other can be handled with a "cast"

---

