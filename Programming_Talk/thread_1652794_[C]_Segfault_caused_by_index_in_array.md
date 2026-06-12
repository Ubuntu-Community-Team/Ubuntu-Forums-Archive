---
title: "[C] Segfault caused by index in array"
date: 2010-12-25
forum: Programming Talk
---

### Post by SpinningAround on 2010-12-25
I'm trying to get the following code to work, but so far have it only caused segfault. Is it something simple that is eluding me?

[PHP]
char *s = "a";
int position(const char c, const char* s){
	int i;
	for(i=0;i<length;i++){
		if(keys[i]==c){
			return i;
		}
	}
	return -1; 
}

void increase(char *s, int pos){
	if(pos==-1){	
		return;
	}else if(s[pos]!='9'){
		int i = position(s[pos],keys);
		s[pos] = keys[++i];
	}else{
		s[pos] = keys[0];
		append(s,'a');
		increase(s,pos-1);
	}
	return;
}
[/PHP]

When stepping through the program do I get this.
```

(gdb) step
increase (s=0x804864f "a", pos=0) at app.c:33
33			s[pos] = keys[++i];
(gdb) step

Program received signal SIGSEGV, Segmentation fault.
0x080484c2 in increase (s=0x804864f "a", pos=0) at app.c:33
33			s[pos] = keys[++i];
(gdb) step

Program terminated with signal SIGSEGV, Segmentation fault.
The program no longer exists.


```

---

### Post by Arndt on 2010-12-25
> **SpinningAround said:**
> I'm trying to get the following code to work, but so far have it only caused segfault. Is it something simple that is eluding me?

[PHP]
char *s = "a";
int position(const char c, const char* s){
	int i;
	for(i=0;i<length;i++){
		if(keys[i]==c){
			return i;
		}
	}
	return -1; 
}

void increase(char *s, int pos){
	if(pos==-1){	
		return;
	}else if(s[pos]!='9'){
		int i = position(s[pos],keys);
		s[pos] = keys[++i];
	}else{
		s[pos] = keys[0];
		append(s,'a');
		increase(s,pos-1);
	}
	return;
}
[/PHP]

When stepping through the program do I get this.
```

(gdb) step
increase (s=0x804864f "a", pos=0) at app.c:33
33			s[pos] = keys[++i];
(gdb) step

Program received signal SIGSEGV, Segmentation fault.
0x080484c2 in increase (s=0x804864f "a", pos=0) at app.c:33
33			s[pos] = keys[++i];
(gdb) step

Program terminated with signal SIGSEGV, Segmentation fault.
The program no longer exists.


```

I think you need to show us more of your program, in particular how 'keys' is declared and initialized.

At the point where it crashes, what is the value of i? And what does 'keys' contain?

---

### Post by Some Penguin on 2010-12-25
's' is pointing to a two-character array in a possibly read-only segment.  Writing to 's', especially while pretending that it points to a larger array, is an error.

---

### Post by SpinningAround on 2010-12-26
Here is the full code
[PHP]
#include <stdio.h>
#include <string.h>

const char *keys = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789";
int length = sizeof(keys)/sizeof(char);

void append(char*, char);
int position(const char, const char*);
void increase(char*, int);

void append(char* string, char c){
	int len = strlen(string);
	string[len] = c;
	string[len+1] = '\0';
}

int position(const char c, const char* s){
	int i;
	for(i=0;i<length;i++){
		if(keys[i]==c){
			return i;
		}
	}
	return -1;
}

void increase(char *s, int pos){
	if(pos==-1){
		return;
	}else if(s[pos]!='9'){
		int i = position(s[pos],keys); 
		s[pos] = keys[++i];
	}else{
		s[pos] = keys[0];
		append(s,'a');
		increase(s,pos-1);
	}
	return;
}

int main(void){
	char *s = "a";
	while(1){
		printf("%s", s);
		increase(s,strlen(s)-1);
	}
}

[/PHP]

---

### Post by Arndt on 2010-12-26
> **SpinningAround said:**
> Here is the full code
[PHP]
#include <stdio.h>
#include <string.h>

const char *keys = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789";
int length = sizeof(keys)/sizeof(char);

void append(char*, char);
int position(const char, const char*);
void increase(char*, int);

void append(char* string, char c){
	int len = strlen(string);
	string[len] = c;
	string[len+1] = '\0';
}

int position(const char c, const char* s){
	int i;
	for(i=0;i<length;i++){
		if(keys[i]==c){
			return i;
		}
	}
	return -1;
}

void increase(char *s, int pos){
	if(pos==-1){
		return;
	}else if(s[pos]!='9'){
		int i = position(s[pos],keys); 
		s[pos] = keys[++i];
	}else{
		s[pos] = keys[0];
		append(s,'a');
		increase(s,pos-1);
	}
	return;
}

int main(void){
	char *s = "a";
	while(1){
		printf("%s", s);
		increase(s,strlen(s)-1);
	}
}

[/PHP]

SomePenguin had the right idea: you are writing to read-only memory in 's'.

---

### Post by worksofcraft on 2010-12-26
If you want to append to a string then you have to make sure there is actually memory allocated for said string.
try replacing
[php]
      char *s = "a";
[/php]
with 
[php]
      char s[100] = "a";
[/php]
IDK what the maximum string length you will need might be... but one way or the other you MUST tell the compiler to reserve that much memory for use by string s.

---

### Post by Barrucadu on 2010-12-26
Or, rather than guesstimate the memory you need, you could of course use malloc and free to get more memory as you need it. However, if you always know the maximum length of the string, and that the string will often reach this maximum length, that might not be the optimal solution.

---

