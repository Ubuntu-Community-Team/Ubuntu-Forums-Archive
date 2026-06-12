---
title: "control gnuchessx in c"
date: 2008-08-05
forum: Programming Talk
---

### Post by montamer on 2008-08-05
hi im trying to control the input to gnuchessx through a c program but it doesn't seem to work. here is my code.
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>

int main(void){
	FILE *gnuchess_inputstream;
	char line[100];

	strcpy(line,"");
	gnuchess_inputstream=popen("gnuchessx ","w");

	fprintf(gnuchess_inputstream,"c2c4 ");
	sleep(10);
	fprintf(gnuchess_inputstream,"a2a4 ");
	pclose(gnuchess_inputstream);
	return 0;
}

```

here is wht i get the output
```
Chess
1. c2c4
1. ... e7e5
My move is: e7e5
Illegal move: $&#65533;

```

as for the program first it has to input c2c4 and then a2a4; but i dont know why its not working; can someone explain me where im making mistake?

thanx.

---

