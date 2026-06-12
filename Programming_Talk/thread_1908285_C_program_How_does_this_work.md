---
title: "C program How does this work?"
date: 2012-01-13
forum: Programming Talk
---

### Post by conradin on 2012-01-13
Hai all, 
I'm in a class where I think we will start writing shells for the kernel in a bit. An example code mentioned in class is shown bellow, which takes the number of arguments including the program name, and lists them in stdout.  here is an example: $ ./a.out cat dog 
0: ./a.out  
1: cat  
2: dog  

great. Thats what I expected. 
So then I got curious about what else I can put in there, and how the arguments get processed, so I put this stuff in and got:
$ ./a.out '' $PWD `touch me` $FOOBAR `touch bobs lies` sluth ~ '"~' 'load' 
0: ./a.out  
1:   
2: /home/j  
3: sluth  
4: /home/j  
5: "~  
6: load

and ended up with the files me, bobs, and lies
So the shell I assume is processing not just whitespace, but other characters.  & sends the program to the background, like it were a shell script, and * lists all sorts of stuff, some of which seems like non-sense. So I get that the shell is processing the program arguments. I get that the white space is how this is getting parsed, and that some arguments arent counting as arguments to the parser. Some of the other output seems just plain strange. Like what happens when I pass the program ./a.out *
similarly, i put $* in the shell and got:
2011.jpg: command not found

whats going on here?
what is the shell doing with these characters?


[http://publications.gbdirect.co.uk/c_book/chapter10/arguments_to_main.html](http://publications.gbdirect.co.uk/c_book/chapter10/arguments_to_main.html)
```
#include <stdlib.h>
#include <stdio.h>
int main( int argc, char ** argv){
	
	int i;
	for (i=0; i<argc; i++) {
		printf("%d: %s  \n", i, argv[i] );
	}

	return 0;
}
```

---

### Post by muteXe on 2012-01-13
This has nothing to do with C.

look here: [http://tldp.org/LDP/abs/html/internalvariables.html](http://tldp.org/LDP/abs/html/internalvariables.html)
Aslo understand the differences of what bash does when you give it "string" or 'string' or string (i.e no speechmarks)

---

### Post by Bachstelze on 2012-01-13
Also `string`.

---

