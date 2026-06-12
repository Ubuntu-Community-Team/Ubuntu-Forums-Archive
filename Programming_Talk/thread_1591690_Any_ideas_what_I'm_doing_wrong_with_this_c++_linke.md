---
title: "Any ideas what I'm doing wrong with this c++ linked list"
date: 2010-10-09
forum: Programming Talk
---

### Post by SavantStrike on 2010-10-09
Right now I'm working on an assignment where I have to create a linked list from a class that the prof has provided. I'm having trouble implementing his overloaded methods, especially the + and = methods. Any tips would be appreciated as I'm pretty stumped.

main:
```

int main ()
{
IntList a;
cout << a;
a= a +10;
a = a + 5;
cout << a;
a[0]=a[1];
cout << a;
return 0;
}

```

Header provided for another project, but I know the prof wants us to modify it for use with this main. Note that there was no default destructor, and that there was no default constructor that would convert an integer into a class object, those I added. I haven't finished them yet and right now I would be satisfied if I could get it to add a single value and work.

Header
```

#define TRUE 1
#define FALSE 0

struct NodeType{
int value;
NodeType *next;
};

class IntList{

friend ostream &operator<<( ostream&, const IntList & );
friend istream &operator>>( istream&, IntList & );

public:
IntList(); //default constructor
IntList(const int &); //conversion constructor to create IntList object when passed int
~IntList();//is this needed?

const IntList &operator=( const IntList & );
const IntList &operator+( const IntList & );

int &operator[](int); //returns left hand operand
const int &operator[](int) const; //returns right hand operand


private:
NodeType *ptr;

};

```

Here is the code I have so far. I'm not sure my + method works, let alone the rest of them.. It runs without error, but if I try to print values inside of it it causes a segmentation fault.

```

ostream &operator<<(ostream &output, const IntList &ls ){

	if (ls.ptr == NULL ){
		output << "Linked list is empty, nothing to print" << endl;
	}
	else{
		int tmpSize = 0; //used to save the size of ls
		NodeType *currTemp = ls.ptr;

		//list was populated from the tail, so values should be removed from the head
		while(currTemp->next != NULL  ){
			currTemp = (currTemp->next);
			output << (currTemp->value) << " ";
		}//size is now known, time to print list

		}
			output << endl;
			return output;

}


IntList::IntList(){
	ptr = NULL;
}

IntList::~IntList(){
	ptr = NULL;
}

IntList::IntList(const int &cs){
	NodeType *tmp;
	tmp = new NodeType;

	tmp->value = cs;
	tmp->next = NULL;

	ptr = tmp;
}


const IntList &IntList::operator+(const IntList &right){

	//start of commands to get int value
	NodeType *currTemp;
	currTemp = right.ptr;

	int tmpInt;
	tmpInt = currTemp->value;
	//end of get int value

	//create a new node
	NodeType *newNode = new NodeType;

	//init values in new node
	newNode->value = tmpInt;
	newNode->next = NULL;

	if (this->ptr == NULL){//then linked list is empty
		this->ptr = newNode;
		}
	//increase size of left hand operand
	this->size = ((this->size) + 1);

	return *this;
}


const IntList &IntList::operator=(const IntList &right){

	NodeType *lTemp = this->ptr;
	NodeType *rTemp = right.ptr;
	NodeType *Last;

	if(&right != this){//check for self assignment

		//values were inserted at tail of list, so the copy should go from head to tail;

		if (this->size < right.size ){ //then the rvalue is larger than the lvalue
			Last = right.ptr;

			while(rTemp->next != NULL){
				Last = rTemp; //Last is one node before rTemp
				lTemp->value = Last->value;
				lTemp->next = Last->next;
				rTemp = rTemp->next;
			}
				lTemp->next = NULL;

		}

		if (this->size > right.size){ //then rvalue is smaller than lvalue
			Last = this->ptr;

			while(rTemp->next != NULL){
				Last = rTemp;
				lTemp->value = Last->value;
				lTemp->next = Last->next;
				rTemp = rTemp->next;
			}
				lTemp->next = NULL;
		}
	}


	return *this;
}

```

---

### Post by Some Penguin on 2010-10-09
Things that catch my eye:

* Your operator<< method looks like it skips the first node.
* tmpSize is unused
* A linked list's destructor would normally deallocate the list's dynamically allocated structures rather than leak memory.
* operator+ will segfault if the passed-in list is empty
* operator+ looks like it's just trying to add a single node, regardless of length of passed-in list
* operator= not clear why you care about sizes; isn't it supposed to just replace the list, not concatenate them or anything?

---

### Post by dwhitney67 on 2010-10-10
> **SavantStrike said:**
> ...It runs without error, but if I try to print values inside of it it causes a segmentation fault.

Are you sure?  I cannot fathom how you were able to compile to code.  Where is "size" declared within the class?  Even if it were declared, do you ever initialize this value to zero?

In your operator<<() method, you should output the node value *before* moving on to the next pointer.  You should also remove the endl that you output; put that in your main() function.
```

int main()
{
   ...

   cout << a << endl;

   ...
}

```

In your operator+() method, you should be accepting an int value, not an IntList.  The value should be appended to the end of the list.
```

IntList& operator+(const int value)
{
   // append value (as a node) to the list
   ...

   return *this;
}

```

I refrain from commenting further until I see concrete evidence that you actually have a compilable program.

---

### Post by SavantStrike on 2010-10-10
> **dwhitney67 said:**
> Are you sure?  I cannot fathom how you were able to compile to code.  Where is "size" declared within the class?  Even if it were declared, do you ever initialize this value to zero?

In your operator<<() method, you should output the node value *before* moving on to the next pointer.  You should also remove the endl that you output; put that in your main() function.
```

int main()
{
   ...

   cout << a << endl;

   ...
}

```



Size wasn't initialized properly in that code, I initialized it in the no argument default constructor and it now works. 

I also fixed the order of the statements in the << method so that it prints the current node value. If I only try to feed the linked list one value, it compiles and runs fine. If I feed it more than one value, seg fault, even after I modified the + operator to allow adding a second node.

I'm not sure I'm allowed to add the endl statements in main. All of the functions the prof has provided usually do the carriage return inside the function. My hands are further tied with the + operator. 

> 
In your operator+() method, you should be accepting an int value, not an IntList.  The value should be appended to the end of the list.
```

IntList& operator+(const int value)
{
   // append value (as a node) to the list
   ...

   return *this;
}

```

I refrain from commenting further until I see concrete evidence that you actually have a compilable program.

Agreed! I want to pass an int, but cannot since I can only feed it an object or enumerated type (int throws an error). I'm pretty sure the prof wants the overloaded + function to be a member function. I would say the heck with it and feed it two parameters (so it would be a non member function) and then just make it a friend, but it may come back to haunt me in the next question. In the next question, I have to take the solution from this problem and put it in a template. I did that on the last project (array lists) and had to befriend another template to make the + function work since it was a non member function. The prof didn't like my solution. 

That leaves me with a function that I can only pass a class object or enumerated type to. I could have a "createInt" class, but that would change the syntax in main since I would be calling createInt(10). I couldn't find a way to convert an int into a class object other than a default constructor which takes an int parameter. It's a poor workaround though as it means the statement a=a+10+5 will not work unless the + operator function is a friend, and then it's not going to work because the
+ operator function is a friend...

I may be going at this the wrong way. I'm going to start on the next problem and see if I get an error passing a template object to a member function. If I don't, then the solutions to this problem and the next problem can be completely different. I can make the overloaded + operator function a non member in this problem, and a member function in the template problem.

---

### Post by SavantStrike on 2010-10-10
> **SavantStrike said:**
> Size wasn't initialized properly in that code, I initialized it in the no argument default constructor and it now works. 

I also fixed the order of the statements in the << method so that it prints the current node value. If I only try to feed the linked list one value, it compiles and runs fine. If I feed it more than one value, seg fault, even after I modified the + operator to allow adding a second node.

I'm not sure I'm allowed to add the endl statements in main. All of the functions the prof has provided usually do the carriage return inside the function. My hands are further tied with the + operator. 



Agreed! I want to pass an int, but cannot since I can only feed it an object or enumerated type (int throws an error). I'm pretty sure the prof wants the overloaded + function to be a member function. I would say the heck with it and feed it two parameters (so it would be a non member function) and then just make it a friend, but it may come back to haunt me in the next question. In the next question, I have to take the solution from this problem and put it in a template. I did that on the last project (array lists) and had to befriend another template to make the + function work since it was a non member function. The prof didn't like my solution. 

That leaves me with a function that I can only pass a class object or enumerated type to. I could have a "createInt" class, but that would change the syntax in main since I would be calling createInt(10). I couldn't find a way to convert an int into a class object other than a default constructor which takes an int parameter. It's a poor workaround though as it means the statement a=a+10+5 will not work unless the + operator function is a friend, and then it's not going to work because the
+ operator function is a friend...

I may be going at this the wrong way. I'm going to start on the next problem and see if I get an error passing a template object to a member function. If I don't, then the solutions to this problem and the next problem can be completely different. I can make the overloaded + operator function a non member in this problem, and a member function in the template problem.

Unless of course, I tried passing the int by value instead of by reference...

I tried one more time before I moved on to the next problem. I made an add constructor that took an int rather than int &something, and it worked.

That's a bunch of hours wasted. I kept reading and re reading all kinds of material trying to fit a square peg in a round hole.

I'm not sure why I tried to pass an integer as a pointer... that was dumb. 

Thanks for all the help!

---

