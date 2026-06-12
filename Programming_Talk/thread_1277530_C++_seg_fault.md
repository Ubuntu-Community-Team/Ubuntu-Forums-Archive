---
title: "C++ seg fault"
date: 2009-09-28
forum: Programming Talk
---

### Post by matmatmat on 2009-09-28
I have this code:
```

/* -*- Mode: C; indent-tabs-mode: t; c-basic-offset: 4; tab-width: 4 -*- */
#include <iostream>

using namespace std;

class Person {
	public:
		int request_t[3];
		int name;
		void assign(int s1, int s2, int s3, int n);
};

void Person::assign(int s1, int s2, int s3, int n){
	request_t[0] = s1;
	request_t[1] = s2;
	request_t[2] = s3;
	name = n;
}	

int slots[] = {0,0,0,0,0,0};

void schedule(Person people[], int length){
	int i;
	int i2;
	Person left_over[length];
	Person scheduleA[length];
	for (i=0;i<length;i++){
		if (slots[people[i].request_t[0]] == 0){
			slots[people[i].request_t[0]] = 1;
			scheduleA[people[i].request_t[0]] = people[i];
		}else if (slots[people[i].request_t[1]] == 0){
			slots[people[i].request_t[1]] = 1;
			scheduleA[people[i].request_t[1]] = people[i];
		}else if (slots[people[i].request_t[2]] == 0){
			slots[people[i].request_t[2]] = 1;
			scheduleA[people[i].request_t[2]] = people[i];
		}else{
			**left_over[i2] = people[i];**
			i2++;
		}
	}
	int len = i2;
	i2 = 0;
	for (i=0;i<length && i2 < len;i++){
		if (slots[i] == 0){
			slots[i] = 1;
			scheduleA[i] = left_over[i2];
			i2++;
		}
	}
	
	for (i=0;i<=length;i++){
		cout << scheduleA[i].name << "\n";
	}
}
int main()
{
	Person people[6];
	int i;
	for (i=0;i<6;i++){
		Person person;
		person.assign((i*1234)%6, (i+1*4321)%6, (i+2*3214)%6, i);
		people[i] = person;
	}
	schedule (people, 6);
	return 0;
}


```
it gives a seg fault, according to gdb it is line 56.

---

### Post by lloyd_b on 2009-09-28
> **matmatmat said:**
> I have this code:
```

/* -*- Mode: C; indent-tabs-mode: t; c-basic-offset: 4; tab-width: 4 -*- */
#include <iostream>

using namespace std;

class Person {
	public:
		int request_t[3];
		int name;
		void assign(int s1, int s2, int s3, int n);
};

void Person::assign(int s1, int s2, int s3, int n){
	request_t[0] = s1;
	request_t[1] = s2;
	request_t[2] = s3;
	name = n;
}	

int slots[] = {0,0,0,0,0,0};

void schedule(Person people[], int length){
	int i;
	int i2;
	Person left_over[length];
	Person scheduleA[length];
	for (i=0;i<length;i++){
		if (slots[people[i].request_t[0]] == 0){
			slots[people[i].request_t[0]] = 1;
			scheduleA[people[i].request_t[0]] = people[i];
		}else if (slots[people[i].request_t[1]] == 0){
			slots[people[i].request_t[1]] = 1;
			scheduleA[people[i].request_t[1]] = people[i];
		}else if (slots[people[i].request_t[2]] == 0){
			slots[people[i].request_t[2]] = 1;
			scheduleA[people[i].request_t[2]] = people[i];
		}else{
			**left_over[i2] = people[i];**
			i2++;
		}
	}
	int len = i2;
	i2 = 0;
	for (i=0;i<length && i2 < len;i++){
		if (slots[i] == 0){
			slots[i] = 1;
			scheduleA[i] = left_over[i2];
			i2++;
		}
	}
	
	for (i=0;i<=length;i++){
		cout << scheduleA[i].name << "\n";
	}
}
int main()
{
	Person people[6];
	int i;
	for (i=0;i<6;i++){
		Person person;
		person.assign((i*1234)%6, (i+1*4321)%6, (i+2*3214)%6, i);
		people[i] = person;
	}
	schedule (people, 6);
	return 0;
}


```
it gives a seg fault, according to gdb it is line 56.

Try initializing "i2" to zero: "int i2 = 0;"

Lloyd B.

Edit: Cool - Bean #1000!

---

### Post by matmatmat on 2009-09-28
Thanks!

---

### Post by johnl on 2009-09-28
I just wanted to add that if you were to compile with -Wall [enable all warnings], you might have seen:

```

main.cc: In function 'void schedule(Person*, int)':
main.cc:24: warning: 'i2' may be used uninitialized in this function

```

Which would point you in the right direction.  or, when debugging with GDB, when breaking on line 56, you could do:

```

(gdb) print i
(gdb) print i2
(gdb) print left_over[i2]

```

To see what elements were being accessed in the array & their values

Hope this helps !

---

