---
title: "C char array all points to last value"
date: 2009-04-16
forum: Programming Talk
---

### Post by RunnerBri24 on 2009-04-16
I am new to c programming, I have a good knowledge of Java and VB, but don't know c very well. I understand what a pointer is, what I want to know is how can I get a string to stay in an array. Here is a snippet of my code

char** names = new char* [numStocks];

while( fgets(line, linemax, fp) !=NULL){
  token=strtok (line, delimiters);   //name
  names[count] = token;			
  count++;
}

after running this code this for loop returns the last value for all the values:

for (int i=0; i<count; i++){
  printf("%s \n", names[i];
}

so the output looks like this:

wire
wire
wire
...

Is there any way to store the names in this "names" array so that the pointer doesn't go to the last value?

If I run a printf statement in the while loop I can prove that the values are different, I just don't know how to store them correctly.

---

### Post by tneva82 on 2009-04-16
> **RunnerBri24 said:**
>   names[count] = token;	

Try: strcpy(name[count], token). You can't just point pointer to it. You need to copy it with strcpy.

Pretty sure that should fix it.

---

### Post by dwhitney67 on 2009-04-16
Actually, since the OP has declared a pointer to a variable length array of char pointers (ie. char** ), each string in the array will need to be allocated before a strcpy() can be used.

In lieu of the two-step dance, I would recommend usage of strdup().

```

char** names = new char* [numStocks];

while(fgets(line, linemax, fp) !=NULL){
token = strtok(line, delimiters); //name
names[count] = strdup(token);
count++;
}

...

/* free each string in array 'names' */
/* free array 'names' */

```

EDIT:  After posting this response, I started to question why is strtok() being used in the first place?  Is there more data in the 'line' that is of interest?  If not, perhaps the strtok() is not even needed.

EDIT # 2:  I just realized, the OP said he was programming in C, but he is using 'new' to allocate; maybe the OP should decide if he is indeed using C or C++.  The code posted appears to indicate the latter.

---

### Post by RunnerBri24 on 2009-04-16
Thanks dwhitney67, the strdup worked. I thought it was c++ coding too, but my professor keeps referring to it as c. He's a math professor in a CSE course and barley knows any programming. I had tried the strcpy, but it hadn't worked and I forgot to mention that in my post.

---

### Post by nvteighen on 2009-04-16
> **RunnerBri24 said:**
> Thanks dwhitney67, the strdup worked. I thought it was c++ coding too, but my professor keeps referring to it as c. He's a math professor in a CSE course and barley knows any programming. I had tried the strcpy, but it hadn't worked and I forgot to mention that in my post.
Let's leave it in "C-style C++"... or maybe just "C with 'new' allocator", because you're just using C Standard Functions (fgets, str*, etc...)...

---

### Post by lisati on 2009-04-16
Maybe I missed something, but where's count being initialised?

---

### Post by PharmaPhunk on 2009-04-16
What exactly is your program trying to accomplish?

---

### Post by soltanis on 2009-04-17
Looks like C using one C++ keyword. If you are curious about how to do the same thing with C, you should look into the malloc() function.

[man 3 malloc]("http://linux.die.net/man/3/malloc")

---

