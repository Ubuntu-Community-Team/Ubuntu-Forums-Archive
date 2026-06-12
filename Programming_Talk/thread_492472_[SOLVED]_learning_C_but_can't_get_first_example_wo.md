---
title: "[SOLVED] learning C but can't get first example working"
date: 2007-07-04
forum: Programming Talk
---

### Post by scragar on 2007-07-04
hey I'm using a really bad tutorial to try and learn C, with the basic premise that  since I already know PHP and javascript and the syntax is virtually identical that it would be easy, anyway my problem is this, the tutorial says to put this into a text file and compile it:
```
main(){
		printf("Hello World");
}
```so I followed the exact instructions, yet gcc tells me:```
/home/scragar/Desktop/meap.c: In function ‘main’:
/home/scragar/Desktop/meap.c:2: warning: incompatible implicit declaration of built-in function ‘printf’
```
anyone got any advice or clues as to the problem?

---

### Post by Modred on 2007-07-04
I suggest you find a better tutorial.  Also, try including stdio.h.

And while we're at it, add return types to your main function.
```
int main() {
...
return 0;
}
```

You can usually get away with a main with a void return type, but some compilers will choke on it.

---

### Post by scragar on 2007-07-04
thanks that fixed it, can you recommend a tutorial then?

---

### Post by AlexThomson_NZ on 2007-07-04
Check the sticky ;)

// On a more productive note:

1) [http://www.crasseux.com/books/ctutorial/](http://www.crasseux.com/books/ctutorial/)
2) [http://www.cprogramming.com/tutorial.html#ctutorial](http://www.cprogramming.com/tutorial.html#ctutorial) (Mind the zealotry, don't be fooled by the C++ evangelists)
3) [http://members.cox.net/midian/articles/ansic1.htm](http://members.cox.net/midian/articles/ansic1.htm)

Try some examples: [http://www.paulgriffiths.net/program/c/](http://www.paulgriffiths.net/program/c/)

---

