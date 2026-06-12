---
title: "Linked list, calculator (20 base) print"
date: 2012-04-23
forum: Programming Talk
---

### Post by tcebak on 2012-04-23
so i'm making a vigesimal calculator (20 base number system)
I am having trouble with the ```
LList::Menu()
``` when it uses the ```
print()
``` method.
I want the program to start with the current number to be displayed and it should be "0"

but when i have print() in the menu function it does not compile. if you substute ```
print()
``` with ```
answer
``` it will compile.

any suggestions, program is still in early stages

```
#include <iostream>
using namespace std;

#undef NULL		//undefines anything from a class that already has
			//the same name


typedef int element;
const int NULL=0;
const char SENTINEL ='#' ;

class listnode{
	public:
		element data;
		listnode* next;
		listnode();	
		~listnode();

	};			// no private data

class LList{
	private:
		listnode* head;
		listnode* tail;
	
	public:
		LList();
		~LList();
		void ReadBackwards();
		void Clean();		
		void Menu();
		char Read_element();
		void Vigesimalinput();
		void AddVigesimal();
		void MultiplyVigesimal();
		void HelpMenu();
		void Print();				
	
	};

int main(){
	//main function, everthing will be executed from top to bottom
	LList A;
	
	cout<<"\n""Vigesimal Calculator, Version 1.0" <<endl;
	cout<<"(c) 2012, Tony Cebak"<<endl;
	cout<<endl;

		A.Menu();
		
	}
	
LList::LList(){
	//This is the constructor, LList will live!
	//Pre:None
	//Post: The N.O is valid
	head=NULL;
	}
		
LList::~LList(){
	//This is the destructor, it will give LList a clean death
	//Pre: The N.O. is valid
	//Post: The N.O. is valid and empty and all borrowed system
	//	resources have been given back
	Clean();
	}

listnode::listnode(){
        //This is the constructor, Listnode will live
        //I hope to make listnode more intelligent so it starts with a
        // zero value
        //
        // Pre: none
        //Post: The N.O. is valid!
	data=0;
        }

listnode::~listnode(){
        //This is the destructor, it will clean and kill the listnode
        //Pre: The N.O. is valid
        //Post: the N.O. is valid and empty and all borrowed system 
        //      resources have been give back
        delete next;
        }



void LList::Clean(){
	//This will basically "proprley" delete objects LList
	//Pre: the N.O. LList is valid
	//Post: The N.O. is now empty, and all of it's previous listnodes
	//	have been given to the system memory pool ("heap")
	listnode* temp;
	while(head != NULL){
		temp=head;
		head=head -> next;
		delete temp;
		}
	}

void LList::ReadBackwards(){
	//This will put the user input into a linked list backwards
	//Pre: The N.O LList is valid
	//Post: the N.O. LList is now valid, filled with data provided 
	//	by the user in backwards order
	
	char userval;
	listnode* temp;
	
	Clean();
	cout<<"Enter elements, "<<SENTINEL<<" to stop";
	userval=Read_element();
	while(userval != SENTINEL){
		temp= new listnode;
		temp -> data=userval;
		temp -> next = head;
		if (head == NULL)
			tail=temp;
		else
			;
		head=temp;
		userval=Read_element();
		}	
	}

char LList::Read_element(){
	//Perfors my data type checking validation like a true player
	char val;
	cin >> val;
	while(!cin.good()){
		cout<<"Invalid response, should be a number 0-9 or a";
		cout<<" letter A-J, try again: ";
		cin.clear();
		cin.ignore(80, '\n');
		cin >>val;
		}
	return val;
	}

void LList::Menu(){
	//This displays the vigesimal number that is current. then ask
	//for a user input.

	char useranswer;
	int answer;
	
	answer=0;
	
	
	cout<<"Current vigesmial number is:   "<<Print()<<endl;
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

void LList::Vigesimalinput(){
	ReadBackwards();
	
	}

void LList::AddVigesimal(){
	}

void LList::MultiplyVigesimal(){
	}
	
void LList::HelpMenu(){
	//This will display the commands for the user! power to the user!
	
	cout<<"\n"<<"Valid commands are:"<<endl;
	cout<<"   e   enter     enter the current vigesimal number"
		<<"from the keyboard"<<endl;
	cout<<"   a   add       add a new vigesimal number to the"
		<<"current vig. number"<<endl;
	cout<<"   m   multiply  multiply a new vigesimal number by"
		<<"the current vig. number"<<endl;
	cout<<"   h   help      show the help menu"<<endl;
	cout<<"   q   quit      quit the program""\n"<<endl;

	Menu();
	}

void LList::Print(){
	//Pre; The N.O LList is valid
	//Post: the N.O LList is unchaged and its elements have been
	//	displayed 

	listnode* temp;
	temp=head;
	
	while(temp != NULL){
		cout<<temp -> data<< endl;
		temp=temp -> next;		//pointer increament
		}	
	}

```

---

### Post by Bachstelze on 2012-04-23
I don't know a lot of C++, but I think what you want is

```
	
	cout<<"Current vigesmial number is:   "<<endl;
        Print();
```

---

### Post by tcebak on 2012-04-23
wow, that worked. not sure why since i can put a variable in that spot and it works. 
A huge thanks though!!!!

---

### Post by tcebak on 2012-04-23
WOW, that worked, not sure why. since i can change print() to a variable and it works.

A HUGE thanks!!!

---

### Post by Bachstelze on 2012-04-23
Print() returns void, apparently C++ doesn't like when you try to print a void value  like that...

---

### Post by tcebak on 2012-04-23
that makes sense!

---

