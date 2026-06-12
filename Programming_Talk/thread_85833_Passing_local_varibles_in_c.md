---
title: "Passing local varibles in c"
date: 2005-11-03
forum: Programming Talk
---

### Post by rock freak on 2005-11-03
Hi there ive been trying to do this for hours upon end now but i just cant get it right.

I am trying ot pass a local varible from one function so that it can be called by the main function to print it later on.  I no i have to have the main point to it in the local varible (correct me if im wrong) but yeah im stuck.

Any help would be very well appreciated!!!

Cheers in advanced 

Ollie

---

### Post by toojays on 2005-11-03
Declare the variable in the main function, then pass its address to the other function. Something like:```
void sum(int * total, int a, int b) {
  *total = a + b;
}

int main(){
  int foo;
  ...
  sum(&foo, 1, 2);
  ...
  printf("foo is %d", foo)
  ...
}
```

There are a couple of other ways to get what you want (declare the variable in the function with static storage or allocate it with malloc) but this way is the simplest.

---

### Post by rock freak on 2005-11-03
Right i have got this:

> //start of get name
char getname(char *name){

	//define varibles
	

	//ask for name
	printf("Hello, please type your name: ");
	
	//get name
	fgets(*name, sizeof(*name), stdin);

	return();
}


//start of main
void main(){
	
	char name[50];

	getname(*name);

}

any ideas???

im probs just missing a little thing or a big major one hehe

---

### Post by toojays on 2005-11-03
That shouldn't compile, because your arguments to fgets have the wrong type. In the getname function, the variable "name" has type "char *", so you can just pass it directly to fgets. Also your sizeof(*name) doesn't do what you want, and the correct version sizeof(name) still wont work because that function has no way to know what size name will be at compile time.

Try just "fgets(name, 50, stdin)" and see how you go.

---

### Post by rock freak on 2005-11-03
excellent thanks alot :D

at last i dont have to use the evil global varibles!!!!

Cheers again

---

### Post by rock freak on 2005-11-03
would it also be the same if i had to do the same with a int???

---

### Post by rock freak on 2005-11-03
aha! not to worry i looke din your first example and managed to figure it out cheers :D


Ollie

---

